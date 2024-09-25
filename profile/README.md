
# Spely CO

## React Native Structure

React Native ve TypeScript kullanırken, bileşenleri isimlendirme ve dışa aktarma konusunda en iyi uygulamaları takip etmek önemlidir. İşte önerilen yaklaşım:

```tsx
import React from 'react'
import { TouchableOpacity, Text, StyleSheet } from 'react-native'

type LoginButtonProps = {
  onPress: () => void
  label: string
}

export function LoginButton ({ onPress, label }: LoginButtonProps): JSX.Element {
  return (
    <TouchableOpacity style={styles.button} onPress={onPress}>
      <Text style={styles.text}>{label}</Text>
    </TouchableOpacity>
  )
}

const styles = StyleSheet.create({
  button: {
    backgroundColor: 'blue',
    padding: 10,
    borderRadius: 5
  },
  text: {
    color: 'white',
    textAlign: 'center'
  }
})
```

 1. Bileşen İsimlendirme:
	 - PascalCase kullanın (örn. LoginButton, UserProfile)
	 - Kebab-case kullanmayın
 2. Dışa Aktarma:
	 - Genellikle named export kullanın
	 - Default export'u sadece özel durumlarda kullanın (örneğin, dinamik import ile lazy loading yapılacaksa)
 3. Dosya İsimlendirme:
	 - Kebab-case kullanın (örn. login-button.tsx, user-profile.tsx)

```
my-expo-project/
├── app/
│   ├── (auth)/
│   │   ├── login.tsx
│   │   ├── register.tsx
│   │   └── forgot-password.tsx
│   ├── (tabs)/
│   │   ├── home.tsx
│   │   ├── profile.tsx
│   │   └── settings.tsx
│   ├── _layout.tsx
│   └── index.tsx
├── modules/
|   ├── auth/
|   |   ├── login/
|   |   |   ├── components/
|   |   |   |   ├── name.tsx
|   |   |   ├── containers/
|   |   |   |   ├── name.tsx
|   |   |   ├── hooks/
|   |   |   |   ├── name.ts
|   |   |   ├── containers/
|   |   |   |   ├── name.tsx
|   |   |   ├── index.tsx
|   ├── app/
|   |   ├── home/
|   |   |   ├── components/
|   |   |   |   ├── name.tsx
|   |   |   ├── containers/
|   |   |   |   ├── name.tsx
|   |   |   ├── hooks/
|   |   |   |   ├── name.ts
|   |   |   ├── containers/
|   |   |   |   ├── name.tsx
|   |   |   ├── index.tsx
├── components/
│   ├── ui/
│   │   ├── button.tsx
│   │   ├── input.tsx
│   │   └── card.tsx
│   ├── forms/
│   │   ├── login-form.tsx
│   │   └── register-form.tsx
│   └── shared/
│       ├── header.tsx
│       └── footer.tsx
├── hooks/
│   ├── use-auth.ts
│   └── use-theme.ts
├── services/
│   ├── api.ts
│   └── storage.ts
├── stores/
│   ├── auth-store.ts
│   └── theme-store.ts
├── utils/
│   ├── validation.ts
│   └── formatting.ts
├── constants/
│   ├── colors.ts
│   └── config.ts
├── assets/
│   ├── images/
│   └── fonts/
├── types/
│   └── index.ts
├── app.json
├── babel.config.js
├── package.json
└── tsconfig.json
```

Özetle:

-   Bileşen isimleri: **PascalCase**
-   Dosya isimleri: **kebab-case**
-   Export yöntemi: **Genellikle named export**
-   Prop tipleri: **Interface veya type alias kullanarak tanımlayın**
 
Bu yaklaşım, kodunuzun tutarlı, okunabilir ve bakımı kolay olmasını sağlayacaktır.
