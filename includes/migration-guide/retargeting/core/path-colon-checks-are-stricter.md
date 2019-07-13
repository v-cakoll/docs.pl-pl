---
ms.openlocfilehash: 7f551fbc194d2da2fdae6bcc7025c20b03aadda2
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859247"
---
### <a name="path-colon-checks-are-stricter"></a>Ścieżka dwukropek kontrole są bardziej restrykcyjne

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.6.2 Liczba zmian dokonano obsługuje wcześniej nieobsługiwanych ścieżek (zarówno format i długości). Sprawdza, czy składnia separatora (dwukropek) odpowiedniego dysku wprowadzono bardziej poprawny, który ma efekt uboczny blokujących niektóre ścieżki identyfikatora URI kilka wybierz ścieżkę interfejsów API gdzie one używane do tolerowane.|
|Sugestia|Jeśli przekazywanie adresu URI, do których to dotyczy interfejsów API, należy zmodyfikować ciągu jako ścieżka.<ul><li>Ręcznie usuń schemat z adresów URL (np. Usuń <code>file://</code> z adresów URL)</li><li>Przekaż identyfikator URI do <xref:System.Uri> klasy i użyć <xref:System.Uri.LocalPath></li></ul>Alternatywnie można zrezygnować z nowych normalizacji ścieżki, ustawiając <code>Switch.System.IO.UseLegacyPathHandling</code> AppContext przełącznik na wartość true.|
|Scope|Krawędź|
|Wersja|4.6.2|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.IO.Path.GetDirectoryName(System.String)?displayProperty=nameWithType></li><li><xref:System.IO.Path.GetPathRoot(System.String)?displayProperty=nameWithType></li></ul>|

