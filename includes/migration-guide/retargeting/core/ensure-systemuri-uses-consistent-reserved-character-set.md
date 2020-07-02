---
ms.openlocfilehash: 21921156295d89aad04f3197fef9fa322f3c8c87
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614663"
---
### <a name="ensure-systemuri-uses-a-consistent-reserved-character-set"></a>Upewnij się, że system. URI używa spójnego zestawu znaków zarezerwowanych

#### <a name="details"></a>Szczegóły

W programie <xref:System.Uri?displayProperty=fullName> niektóre znaki zakodowane w procentach, które były czasami zdekodowane, są teraz spójne z kodowaniem. Dzieje się tak we właściwościach i metodach, które uzyskują dostęp do składników Path, Query, fragment lub UserInfo identyfikatora URI. Zachowanie zmieni się tylko wtedy, gdy oba poniższe warunki są spełnione:

- Identyfikator URI zawiera zakodowaną postać dowolnego z następujących znaków zarezerwowanych: `:` , `'` ,, `(` `)` `!` lub `*` .
- Identyfikator URI zawiera znak Unicode lub zakodowany zastrzeżony. Jeśli obie powyższe wartości mają wartość true, zakodowane zarezerwowane znaki są zaszyfrowane. W poprzednich wersjach .NET Framework są one zdekodowane.

#### <a name="suggestion"></a>Sugestia

W przypadku aplikacji przeznaczonych dla wersji .NET Framework zaczynających się od 4.7.2 nowe zachowanie dekodowania jest domyślnie włączone. Jeśli ta zmiana jest niepożądana, można ją wyłączyć, dodając następujący przełącznik [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do `<runtime>` sekcji pliku konfiguracyjnego aplikacji:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets=true" />
</runtime>
```

W przypadku aplikacji przeznaczonych dla wcześniejszych wersji .NET Framework, które są uruchamiane w ramach wersji zaczynających się od .NET Framework 4.7.2, nowe zachowanie dekodowania jest domyślnie wyłączone. Można ją włączyć, dodając następujący przełącznik [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do `<runtime>` sekcji pliku konfiguracyjnego aplikacji:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets=false" />
</runtime>
```

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Mały       |
| Wersja | 4.7.2       |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Uri?displayProperty=nameWithType>
