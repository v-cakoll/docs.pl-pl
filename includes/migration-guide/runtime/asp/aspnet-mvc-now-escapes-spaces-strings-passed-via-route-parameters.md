---
ms.openlocfilehash: c53fe57f3278741a927a2f00b11af6e26dafce66
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620149"
---
### <a name="aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a>ASP.NET MVC teraz wyprowadza spacje w ciągach przesyłanych za pośrednictwem parametrów trasy

#### <a name="details"></a>Szczegóły

Aby zapewnić zgodność ze standardem RFC 2396, w przypadku wypełniania parametrów akcji z trasy są teraz zmieniane spacje w ścieżkach tras. W związku z tym, w <code>/controller/action/some data</code> <code>/controller/action/{data}</code> przeciwieństwie do trasy i podania <code>some data</code> jako parametru danych, będzie ona teraz dostarczana <code>some%20data</code> .

#### <a name="suggestion"></a>Sugestia

Kod powinien zostać zaktualizowany do nieucieczki parametrów ciągu z trasy. Jeśli oryginalny identyfikator URI jest wymagany, dostęp do niego można uzyskać za pomocą <xref:System.Net.HttpWebRequest.RequestUri> . Interfejs API OriginalString.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Mały|
|Wersja|4.5.2|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Web.Mvc.RouteAttribute.%23ctor(System.String)></li></ul>|
