---
ms.openlocfilehash: a70aca33d0830f3b23ff985f17c469cb7c4ff35c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234811"
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
