---
ms.openlocfilehash: 4b5c886ad35afbbf0a68e03b3174ab9ea1f5524f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614766"
---
### <a name="cspparametersparentwindowhandle-now-expects-hwnd-value"></a>CspParameters. ParentWindowHandle teraz oczekuje wartości HWND

#### <a name="details"></a>Szczegóły

<xref:System.Security.Cryptography.CspParameters.ParentWindowHandle>Wartość wprowadzona w .NET Framework 2,0 umożliwia aplikacji zarejestrowanie wartości uchwytu okna nadrzędnego w taki sposób, że każdy interfejs użytkownika wymagany do uzyskania dostępu do klucza (na przykład monitu o podanie numeru PIN lub okna dialogowego zgody) otwiera się jako modalny element podrzędny do określonego okna. Począwszy od aplikacji przeznaczonych dla .NET Framework 4,7, aplikacja Windows Forms może ustawić <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle> Właściwość z kodem podobnym do poniższego:

```csharp
cspParameters.ParentWindowHandle = form.Handle;
```

W poprzednich wersjach .NET Framework oczekiwano, że wartość będzie <xref:System.IntPtr?displayProperty=fullName> reprezentować lokalizację w pamięci, w której znajduje się wartość [HWND](https://docs.microsoft.com/windows/desktop/WinProg/windows-data-types#HWND) . Ustawianie właściwości na postać. Obsługa w systemie Windows 7 i starszych wersjach nie miała znaczenia, ale w systemie Windows 8 i nowszych wersjach jego wynikiem jest &quot; <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> : parametr jest nieprawidłowy.&quot;

#### <a name="suggestion"></a>Sugestia

W przypadku aplikacji przeznaczonych dla .NET Framework 4,7 lub wyższych chcemy zarejestrowanie relacji między oknem nadrzędnym zaleca się użycie formy uproszczonej:

```csharp
cspParameters.ParentWindowHandle = form.Handle;
```

Użytkownicy, którzy zidentyfikowali, że poprawna wartość jest adresem lokalizacji pamięci, która posiadała wartość, `form.Handle` może zrezygnować z zmiany zachowania, ustawiając przełącznik AppContext `Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle` na `true` :

- Przez programowe ustawianie przełączników zgodności w AppContext, jak wyjaśniono [tutaj](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46).
- Dodając następujący wiersz do `<runtime>` sekcji pliku app.config:

```xml
<runtime>
 <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle=true"/>
</runtime>
```

W przypadku użytkowników, którzy chcą zrezygnować z nowego zachowania w środowisku uruchomieniowym .NET Framework 4,7, gdy aplikacja jest ładowana w starszej wersji .NET Framework, można ustawić przełącznik AppContext na `false` .

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Mały       |
| Wersja | 4,7         |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle?displayProperty=nameWithType>
