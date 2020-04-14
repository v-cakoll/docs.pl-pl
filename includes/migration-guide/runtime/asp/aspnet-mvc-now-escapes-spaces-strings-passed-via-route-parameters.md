---
ms.openlocfilehash: 7444ddbdd4a7c5f731fba8528ee2334374fc254e
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275098"
---
### <a name="aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a>ASP.NET MVC teraz ucieka przestrzenie w ciągach przekazywane za pośrednictwem parametrów trasy

|   |   |
|---|---|
|Szczegóły|Aby zapewnić zgodność z rfc 2396, miejsca w ścieżkach trasy są teraz wysuwają się podczas wypełniania parametrów akcji z trasy. Tak, podczas <code>/controller/action/some data</code> gdy wcześniej dopasować <code>/controller/action/{data}</code> <code>some data</code> trasę i podać jako parametr <code>some%20data</code> danych, będzie teraz zapewnić zamiast tego.|
|Sugestia|Kod powinien zostać zaktualizowany do parametrów ciągu unescape z trasy. Jeśli wymagany jest oryginalny identyfikator URI, można <xref:System.Net.HttpWebRequest.RequestUri>uzyskać do niego dostęp za pomocą pliku . Interfejs API originalstring.|
|Zakres|Mały|
|Wersja|4.5.2|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Web.Mvc.RouteAttribute.%23ctor(System.String)></li></ul>|
