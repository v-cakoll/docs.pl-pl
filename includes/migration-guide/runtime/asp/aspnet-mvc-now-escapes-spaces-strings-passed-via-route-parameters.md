---
ms.openlocfilehash: 2278d82d5362fe217ca4bce02a052d4b440843c2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803232"
---
### <a name="aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a>ASP.NET MVC teraz ucieka przestrzenie w ciągach przekazywane za pośrednictwem parametrów trasy

|   |   |
|---|---|
|Szczegóły|Aby zapewnić zgodność z rfc 2396, miejsca w ścieżkach trasy są teraz wysuwają się podczas wypełniania parametrów akcji z trasy. Tak, podczas <code>/controller/action/some data</code> gdy wcześniej dopasować <code>/controller/action/{data}</code> <code>some data</code> trasę i podać jako parametr <code>some%20data</code> danych, będzie teraz zapewnić zamiast tego.|
|Sugestia|Kod powinien zostać zaktualizowany do parametrów ciągu unescape z trasy. Jeśli wymagany jest oryginalny identyfikator URI, można <xref:System.Net.HttpWebRequest.RequestUri>uzyskać do niego dostęp za pomocą pliku . Interfejs API originalstring.|
|Zakres|Mały|
|Wersja|4.5.2|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Web.Mvc.RouteAttribute.%23ctor(System.String)?displayProperty=nameWithType></li></ul>|
