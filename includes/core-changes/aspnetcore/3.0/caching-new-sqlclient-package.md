---
ms.openlocfilehash: 32c7f4e9e4736145f9275b74f34c04404e7c770a
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394044"
---
### <a name="caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package"></a>Buforowanie: Microsoft. Extensions. buforowanie. SqlServer używa nowego pakietu SqlClient

Pakiet `Microsoft.Extensions.Caching.SqlServer` będzie używać nowego pakietu `Microsoft.Data.SqlClient` zamiast pakietu `System.Data.SqlClient`. Ta zmiana może spowodować drobne zmiany zachowań. Aby uzyskać więcej informacji, zobacz [wprowadzenie do nowego elementu Microsoft. Data. SqlClient](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Pakiet `Microsoft.Extensions.Caching.SqlServer` używał pakietu `System.Data.SqlClient`.

#### <a name="new-behavior"></a>Nowe zachowanie

`Microsoft.Extensions.Caching.SqlServer` używa teraz pakietu `Microsoft.Data.SqlClient`.

#### <a name="reason-for-change"></a>Przyczyna zmiany

`Microsoft.Data.SqlClient` to nowy pakiet, który jest zbudowany z `System.Data.SqlClient`. Jest to miejsce, w którym wszystkie nowe funkcje będą wykonywane od teraz.

#### <a name="recommended-action"></a>Zalecana akcja

Klienci nie muszą martwić się o tę zmianę, chyba że używali typów zwracanych przez pakiet `Microsoft.Extensions.Caching.SqlServer` i rzutowania ich do typów `System.Data.SqlClient`. Na przykład jeśli ktoś wyrzutuje `DbConnection` do [starego typu SqlConnection](xref:System.Data.SqlClient.SqlConnection), musi zmienić rzutowanie na nowy typ `Microsoft.Data.SqlClient.SqlConnection`. 

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
