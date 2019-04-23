---
ms.openlocfilehash: a51738fa75ba2dd4574549fce2570df8231c4cae
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59234973"
---
### <a name="path-colon-checks-are-stricter"></a>Ścieżka dwukropek kontrole są bardziej restrykcyjne

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.6.2 Liczba zmian dokonano obsługuje wcześniej nieobsługiwanych ścieżek (zarówno format i długości). Sprawdza, czy składnia separatora (dwukropek) odpowiedniego dysku wprowadzono bardziej poprawny, który ma efekt uboczny blokujących niektóre ścieżki identyfikatora URI kilka wybierz ścieżkę interfejsów API gdzie one używane do tolerowane.|
|Sugestia|Jeśli przekazywanie adresu URI, do których to dotyczy interfejsów API, należy zmodyfikować ciągu jako ścieżka.<ul><li>Ręcznie usuń schemat z adresów URL (np. Usuń <code>file://</code> z adresów URL)</li><li>Przekaż identyfikator URI do <xref:System.Uri> klasy i użyć <xref:System.Uri.LocalPath></li></ul>Alternatywnie można zrezygnować z nowych normalizacji ścieżki, ustawiając <code>Switch.System.IO.UseLegacyPathHandling</code> AppContext przełącznik na wartość true.|
|Zakres|Krawędź|
|Wersja|4.6.2|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.IO.Path.GetDirectoryName(System.String)?displayProperty=nameWithType></li><li><xref:System.IO.Path.GetPathRoot(System.String)?displayProperty=nameWithType></li></ul>|
