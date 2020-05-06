---
ms.openlocfilehash: 771238c53dc97f4cf4068968f3c68500ba9f87da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73198530"
---
### <a name="caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package"></a>Buforowanie: Microsoft. Extensions. buforowanie. SqlServer używa nowego pakietu SqlClient

`Microsoft.Extensions.Caching.SqlServer` Pakiet będzie używać nowego `Microsoft.Data.SqlClient` pakietu zamiast `System.Data.SqlClient` pakietu. Ta zmiana może spowodować drobne zmiany zachowań. Aby uzyskać więcej informacji, zobacz [wprowadzenie do nowego elementu Microsoft. Data. SqlClient](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

`Microsoft.Extensions.Caching.SqlServer` Pakiet użył `System.Data.SqlClient` pakietu.

#### <a name="new-behavior"></a>Nowe zachowanie

`Microsoft.Extensions.Caching.SqlServer`Program korzysta teraz z `Microsoft.Data.SqlClient` pakietu.

#### <a name="reason-for-change"></a>Przyczyna zmiany

`Microsoft.Data.SqlClient`jest nowym pakietem, który jest zbudowany z `System.Data.SqlClient`. Jest to miejsce, w którym wszystkie nowe funkcje będą wykonywane od teraz.

#### <a name="recommended-action"></a>Zalecana akcja

Klienci nie muszą martwić się o tę zmianę, chyba że używali typów zwracanych `Microsoft.Extensions.Caching.SqlServer` przez pakiet i rzutowania `System.Data.SqlClient` ich na typy. Na przykład jeśli ktoś wyrzutuje `DbConnection` do [starego typu SqlConnection](xref:System.Data.SqlClient.SqlConnection), musi zmienić rzutowanie na nowy `Microsoft.Data.SqlClient.SqlConnection` typ.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
