---
ms.openlocfilehash: a51738fa75ba2dd4574549fce2570df8231c4cae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859247"
---
### <a name="path-colon-checks-are-stricter"></a>Kontrole dwukropek ścieżki są bardziej rygorystyczne

|   |   |
|---|---|
|Szczegóły|W .NET Framework 4.6.2 wprowadzono szereg zmian w celu obsługi wcześniej nieobsługiconych ścieżek (zarówno pod względem długości, jak i formatu). Sprawdzanie prawidłowej składni separatora dysku (dwukropek) było bardziej poprawne, co miało efekt uboczny blokowania niektórych ścieżek URI w kilku wybranych interfejsach API ścieżki, w których były tolerowane.|
|Sugestia|Jeśli przekazywanie identyfikatora URI do interfejsów API, których dotyczy problem, należy najpierw zmodyfikować ciąg jako ścieżkę prawną.<ul><li>Ręczne usuwanie schematu z adresów <code>file://</code> URL (np. usuwanie z adresów URL)</li><li>Przekaż identyfikator URI <xref:System.Uri> do klasy i użyj<xref:System.Uri.LocalPath></li></ul>Alternatywnie można zrezygnować z normalizacji nowej ścieżki, <code>Switch.System.IO.UseLegacyPathHandling</code> ustawiając appcontext przełącznik do true.|
|Zakres|Brzeg|
|Wersja|4.6.2|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.IO.Path.GetDirectoryName(System.String)?displayProperty=nameWithType></li><li><xref:System.IO.Path.GetPathRoot(System.String)?displayProperty=nameWithType></li></ul>|
