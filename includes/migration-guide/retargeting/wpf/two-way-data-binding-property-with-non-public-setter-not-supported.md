---
ms.openlocfilehash: a70aca33d0830f3b23ff985f17c469cb7c4ff35c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774496"
---
### <a name="two-way-data-binding-to-a-property-with-a-non-public-setter-is-not-supported"></a>Dwukierunkowe powiązanie danych z właściwością setter niepublicznych nie jest obsługiwane.

|   |   |
|---|---|
|Szczegóły|Podjęto próbę powiązanie danych z właściwością bez publicznej metody ustawiającej nigdy nie było to obsługiwany scenariusz. Począwszy od programu .NET Framework 4.5.1, w tym scenariuszu będzie zgłaszać wyjątek <xref:System.InvalidOperationException?displayProperty=name>. Należy pamiętać, że ten nowy wyjątek zostanie zgłoszony tylko dla aplikacji, które są specjalnie przeznaczone dla .NET Framework 4.5.1. Jeśli aplikacja jest przeznaczony dla .NET Framework 4.5, będą miały wywołania. Jeśli aplikacja nie wskazuje elementu docelowego konkretnej wersji .NET Framework, powiązanie będzie traktowane jak jednokierunkowe.|
|Sugestia|Aplikacja powinien zostać zaktualizowany do Użyj powiązania jednokierunkowe lub publicznie ujawniać metoda ustawiająca właściwości. Alternatywnie przeznaczone dla .NET Framework 4.5 spowoduje, że aplikacja stare zachowują się.|
|Zakres|Mały|
|Wersja|4.5.1|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType></li></ul>|
