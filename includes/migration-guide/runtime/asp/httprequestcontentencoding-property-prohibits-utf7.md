---
ms.openlocfilehash: 668d047d3247d64cb1400d4a9ea6887795fa0d44
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235429"
---
### <a name="httprequestcontentencoding-property-prohibits-utf7"></a>HttpRequest.ContentEncoding property prohibits UTF7

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.5, kodowanie UTF-7 jest zabronione w <xref:System.Web.HttpRequest?displayProperty=name>s' treści. Dane dla aplikacji, które zależą od danych przychodzących w formacie UTF-7, nie będą poprawnie dekodowane w niektórych przypadkach.|
|Sugestia|W idealnym przypadku aplikacji powinien zostać zaktualizowany w taki sposób, aby nie używać kodowania w UTF-7 <xref:System.Web.HttpRequest?displayProperty=name>s. Alternatywnie, można przywrócić starsze zachowanie za pomocą <code>aspnet:AllowUtf7RequestContentEncoding</code> atrybutu [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) elementu.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType></li></ul>|
