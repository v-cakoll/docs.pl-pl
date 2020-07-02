---
ms.openlocfilehash: 3e4a5936bbac4e77efc5f7e68b55ddf49bae5d43
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614718"
---
### <a name="path-colon-checks-are-stricter"></a>Sprawdzanie dwukropek ścieżki jest bardziej rygorystyczne

#### <a name="details"></a>Szczegóły

W .NET Framework 4.6.2 wprowadzono wiele zmian do obsługi wcześniej nieobsługiwanych ścieżek (zarówno w formacie długości, jak i formatu). Sprawdza, czy składnia separatora dysku (dwukropek) była bardziej poprawna, co spowodowało zablokowanie niektórych ścieżek identyfikatorów URI w kilku interfejsach API do wybierania ścieżek, gdzie są one używane do tolerowania.

#### <a name="suggestion"></a>Sugestia

W przypadku przekazywania identyfikatora URI do odpowiednich interfejsów API należy najpierw zmodyfikować ciąg tak, aby był on ścieżką prawną.<ul><li>Ręcznie usuń schemat z adresów URL (np. Usuń `file://` z adresów URL)

- Przekaż identyfikator URI do <xref:System.Uri> klasy i Użyj<xref:System.Uri.LocalPath>

Alternatywnie można zrezygnować z nowej normalizacji ścieżki, ustawiając `Switch.System.IO.UseLegacyPathHandling` przełącznik AppContext na true.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Brzeg        |
| Wersja | 4.6.2       |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.IO.Path.GetDirectoryName(System.String)?displayProperty=nameWithType>
- <xref:System.IO.Path.GetPathRoot(System.String)?displayProperty=nameWithType>
