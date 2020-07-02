---
ms.openlocfilehash: 9c3c0bf7fbd8d45eba84eaa8634fd2d834195702
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617210"
---
### <a name="systemuri-parsing-adheres-to-rfc-3987"></a>Analizowanie elementu System. URI jest zgodne ze specyfikacją RFC 3987

#### <a name="details"></a>Szczegóły

Analiza identyfikatorów URI została zmieniona na kilka sposobów w .NET Framework 4,5. Należy jednak pamiętać, że te zmiany mają wpływ tylko na kod docelowy .NET Framework 4,5. W przypadku elementów binarnych .NET Framework 4,0 zostanie zaobserwowane stare zachowanie. Zmiany w analizie identyfikatora URI w .NET Framework 4,5 obejmują:

- Analiza identyfikatora URI będzie wykonywała normalizację i sprawdzanie znaków zgodnie z najnowszymi regułami IRI w dokumencie RFC 3987.
- Formularz normalizacji Unicode C zostanie wykonany tylko na części hosta identyfikatora URI.
- Nieprawidłowe identyfikatory URI:
- Końcowe kropki na końcu segmentu ścieżki są teraz zachowywane.
- `file://`Identyfikatory URI nie mają znaku ucieczki `?` .
- Znaki kontrolne `U+0080` Unicode `U+009F` nie są obsługiwane.
- Znaki przecinki `,` lub `%2c` nie są automatycznie wyprowadzane.

#### <a name="suggestion"></a>Sugestia

Jeśli stara składnia analizowania składni identyfikatorów URI .NET Framework 4,0 jest niezbędna (często nie są), mogą one być używane przez kierowanie .NET Framework 4,0. Można to osiągnąć przy użyciu <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> na zestawie lub za pośrednictwem interfejsu użytkownika systemu projektu programu Visual Studio na stronie właściwości projektu.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Duży       |
| Wersja | 4.5         |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Uri.%23ctor(System.String)>
- <xref:System.Uri.%23ctor(System.String,System.Boolean)>
- <xref:System.Uri.%23ctor(System.String,System.UriKind)>
- <xref:System.Uri.%23ctor(System.Uri,System.String)>
- <xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType>
- <xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType>
- <xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType>
