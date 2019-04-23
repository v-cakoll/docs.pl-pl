---
ms.openlocfilehash: dfc1a0d05142861ff1c1b7391126d86e09fa71c0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804771"
---
### <a name="webutilityhtmldecode-no-longer-decodes-invalid-input-sequences"></a>WebUtility.HtmlDecode dekoduje już nieprawidłowych sekwencji wejściowych

|   |   |
|---|---|
|Szczegóły|Domyślnie metody dekodowania nie dekodują już nieprawidłowych sekwencji wejściowych na nieprawidłowy ciąg UTF-16. Zamiast tego zwracają oryginalne dane wejściowe.|
|Sugestia|Zmiana w danych wyjściowych dekodera powinna mieć znaczenie tylko wtedy, gdy w ciągach zamiast danych UTF-16 są przechowywane dane binarne. Aby jawnie kontrolować to zachowanie, ustaw <code>aspnet:AllowRelaxedUnicodeDecoding</code> atrybutu [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/index.md) elementu <code>true</code> Aby włączyć starsze zachowanie lub <code>false</code> włączyć bieżące zachowanie.|
|Zakres|Mały|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Net.WebUtility.HtmlDecode(System.String)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.HtmlDecode(System.String,System.IO.TextWriter)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.UrlDecode(System.String)?displayProperty=nameWithType></li></ul>|
