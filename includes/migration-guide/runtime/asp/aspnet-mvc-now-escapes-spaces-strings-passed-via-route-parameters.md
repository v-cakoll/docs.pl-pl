---
ms.openlocfilehash: 8d058d3297471e67459164f18358b1d143465712
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803232"
---
### <a name="aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a>ASP.NET MVC teraz specjalne spacje w ciągach przekazaną za pomocą parametrów trasy

|   |   |
|---|---|
|Szczegóły|Aby można było zgodne z RFC 2396, miejsca do magazynowania w ścieżkach trasy są teraz poprzedzone znakiem zmiany znaczenia podczas wypełniania parametry akcji z trasy. Tak podczas gdy <code>/controller/action/some data</code> wcześniej będzie odpowiadać trasy <code>/controller/action/{data}</code> i podaj <code>some data</code> jako parametr danych, będzie teraz zapewniać <code>some%20data</code> zamiast tego.|
|Sugestia|Kod powinien zostać zaktualizowany do unescape parametry ciągu z trasy. W razie potrzeby oryginalnego identyfikatora URI jest dostępny za pomocą <xref:System.Net.HttpWebRequest.RequestUri>. OriginalString interfejsu API.|
|Scope|Mały|
|Wersja|4.5.2|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Web.Mvc.RouteAttribute.%23ctor(System.String)?displayProperty=nameWithType></li></ul>|

