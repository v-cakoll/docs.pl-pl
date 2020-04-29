---
ms.openlocfilehash: c4e7864262a11aafa4b7f1f4bdf632fbf084c560
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507098"
---
### <a name="http-kestrel-and-iis-badhttprequestexception-types-marked-obsolete-and-replaced"></a>HTTP: Kestrel i IIS BadHttpRequestException typy oznaczone jako przestarzałe i zastąpione

`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`i `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` zostały oznaczone jako przestarzałe i zmienione na pochodne `Microsoft.AspNetCore.Http.BadHttpRequestException`od. Serwery Kestrel i IIS nadal generują stare typy wyjątków w celu zapewnienia zgodności z poprzednimi wersjami. Przestarzałe typy zostaną usunięte w przyszłej wersji.

Aby zapoznać się z omówieniem, zobacz [dotnet/aspnetcore # 20614](https://github.com/dotnet/aspnetcore/issues/20614).

#### <a name="version-introduced"></a>Wprowadzona wersja

5,0 wersja zapoznawcza 4

#### <a name="old-behavior"></a>Stare zachowanie

`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`i `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` pochodzące od <xref:System.IO.IOException?displayProperty=nameWithType>.

#### <a name="new-behavior"></a>Nowe zachowanie

`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`i `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` są przestarzałe. Typy pochodzą z `Microsoft.AspNetCore.Http.BadHttpRequestException`, które pochodzą z `System.IO.IOException`.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Wprowadzono zmianę w:

* Konsolidowanie zduplikowanych typów.
* Ujednolicenie zachowania między implementacjami serwera.

Aplikacja może teraz przechwycić wyjątek `Microsoft.AspNetCore.Http.BadHttpRequestException` podstawowy podczas korzystania z usługi Kestrel lub IIS.

#### <a name="recommended-action"></a>Zalecana akcja

Zamień Użycie elementów `Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` i `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` na. `Microsoft.AspNetCore.Http.BadHttpRequestException`

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- [Microsoft. AspNetCore. Server. IIS. BadHttpRequestException](/dotnet/api/microsoft.aspnetcore.server.iis.badhttprequestexception?view=aspnetcore-3.1)
- [Microsoft. AspNetCore. Server. Kestrel. BadHttpRequestException](/dotnet/api/microsoft.aspnetcore.server.kestrel.badhttprequestexception?view=aspnetcore-1.1)

<!--

#### Affected APIs

- `T:Microsoft.AspNetCore.Server.IIS.BadHttpRequestException`
- `T:Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`

-->
