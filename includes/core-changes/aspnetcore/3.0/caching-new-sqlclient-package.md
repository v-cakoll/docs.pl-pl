---
ms.openlocfilehash: 771238c53dc97f4cf4068968f3c68500ba9f87da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73198530"
---
### <a name="caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package"></a>Buforowanie: Program Microsoft.Extensions.Caching.SqlServer używa nowego pakietu SqlClient

Pakiet `Microsoft.Extensions.Caching.SqlServer` użyje nowego `Microsoft.Data.SqlClient` pakietu `System.Data.SqlClient` zamiast pakietu. Ta zmiana może spowodować niewielkie zmiany zachowań łamanie. Aby uzyskać więcej informacji, zobacz [Wprowadzenie do nowego klienta Microsoft.Data.SqlClient](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Pakiet `Microsoft.Extensions.Caching.SqlServer` użył `System.Data.SqlClient` pakietu.

#### <a name="new-behavior"></a>Nowe zachowanie

`Microsoft.Extensions.Caching.SqlServer`używa teraz `Microsoft.Data.SqlClient` pakietu.

#### <a name="reason-for-change"></a>Przyczyna zmiany

`Microsoft.Data.SqlClient`to nowy pakiet, który `System.Data.SqlClient`jest zbudowany z . To miejsce, w którym wszystkie nowe funkcje będą wykonywane od teraz.

#### <a name="recommended-action"></a>Zalecana akcja

Klienci nie powinni się martwić o tę przełomową zmianę, `Microsoft.Extensions.Caching.SqlServer` chyba że używali `System.Data.SqlClient` typów zwracanych przez pakiet i przesyłania ich do typów. Na przykład jeśli ktoś `DbConnection` był rzutowanie do [starego typu SqlConnection](xref:System.Data.SqlClient.SqlConnection), musieliby zmienić rzutowania na nowy `Microsoft.Data.SqlClient.SqlConnection` typ.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
