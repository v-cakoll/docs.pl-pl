---
ms.openlocfilehash: 7d3568fef933758c40e47cefa86c24d31d4119fc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620134"
---
### <a name="httprequestcontentencoding-property-prohibits-utf7"></a>Właściwość HttpRequest. ContentEncoding zabrania UTF7

#### <a name="details"></a>Szczegóły

Począwszy od .NET Framework 4,5, kodowanie UTF-7 jest zabronione w <xref:System.Web.HttpRequest?displayProperty=fullName> treści "s". Dane dla aplikacji, które zależą od danych przychodzących w formacie UTF-7, nie będą poprawnie dekodowane w niektórych przypadkach.

#### <a name="suggestion"></a>Sugestia

W idealnym przypadku aplikacje należy zaktualizować tak, aby nie korzystały z kodowania UTF-7 w <xref:System.Web.HttpRequest?displayProperty=fullName> s. Alternatywnie można przywrócić starsze zachowanie przy użyciu <code>aspnet:AllowUtf7RequestContentEncoding</code> atrybutu [AppSettings](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) elementu.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType></li></ul>|
