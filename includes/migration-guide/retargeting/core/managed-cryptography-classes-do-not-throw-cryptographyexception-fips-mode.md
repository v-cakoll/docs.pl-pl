---
ms.openlocfilehash: 0b62eff8d70873293aafa539f40bf032672df57a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616289"
---
### <a name="managed-cryptography-classes-do-not-throw-a-cryptographyexception-in-fips-mode"></a>Zarządzane klasy kryptograficzne nie zgłaszają wyjątku kryptografii w trybie FIPS

#### <a name="details"></a>Szczegóły

W .NET Framework 4.7.2 i starszych wersjach zarządzane klasy dostawcy usług kryptograficznych, takie jak <xref:System.Security.Cryptography.SHA256Managed> throw, <xref:System.Security.Cryptography.CryptographicException> gdy systemowe biblioteki kryptograficzne są skonfigurowane w trybie FIPS. Te wyjątki są zgłaszane, ponieważ zarządzane wersje nie zostały poddane FIPS (Federal Information Processing Standards) 140-2 certyfikacji, a także do blokowania algorytmów kryptograficznych, które nie zostały uznane za zatwierdzone na podstawie reguł FIPS.  Ponieważ kilku deweloperów ma swoje komputery deweloperskie w trybie FIPS, te wyjątki są często zgłaszane tylko w systemach produkcyjnych. Aplikacje przeznaczone dla .NET Framework 4,8 i nowszych wersji automatycznie przełączają się do nowszej, swobodnej zasady, tak aby <xref:System.Security.Cryptography.CryptographicException> nie było już zgłaszane domyślnie w takich przypadkach. Zamiast tego zarządzane klasy kryptograficzne przekierowują operacje kryptograficzne do biblioteki kryptografii systemu. Ta zmiana zasad skutecznie usuwa potencjalne różnice między środowiskami deweloperskimi i środowiskami produkcyjnymi, dzięki czemu składniki macierzyste i zarządzane składniki działają w ramach tych samych zasad kryptograficznych.

#### <a name="suggestion"></a>Sugestia

Jeśli takie zachowanie jest niepożądane, można zrezygnować z niego i przywrócić poprzednie zachowanie, tak aby <xref:System.Security.Cryptography.CryptographicException> w trybie FIPS było zgłaszane, dodając następujące ustawienie konfiguracji [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcji pliku konfiguracyjnego aplikacji:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.UseLegacyFipsThrow=true" />
</runtime>
```

Jeśli aplikacja jest przeznaczona .NET Framework 4.7.2 lub wcześniejsza, możesz również przystąpić do tej zmiany, dodając następujące ustawienia konfiguracji [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcji pliku konfiguracyjnego aplikacji:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.UseLegacyFipsThrow=false" />
</runtime>
```

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Brzeg        |
| Wersja | 4,8         |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Security.Cryptography.AesManaged?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.MD5Cng?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.MD5CryptoServiceProvider?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RC2CryptoServiceProvider?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RijndaelManaged?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RIPEMD160Managed?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.SHA1Managed?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.SHA256Managed?displayProperty=nameWithType>
