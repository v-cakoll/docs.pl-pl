---
ms.openlocfilehash: e5355387d5cb6d9e6de89f5b85e64bc100b32ae1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522655"
---
### <a name="spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger"></a>Umowy O SPA: SpaServices i NodeServices nie wracają już do rejestratora konsoli

<xref:Microsoft.AspNetCore.SpaServices?displayProperty=nameWithType>i <xref:Microsoft.AspNetCore.NodeServices?displayProperty=nameWithType> nie będą wyświetlać dzienników konsoli, chyba że rejestrowanie jest skonfigurowane.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

`Microsoft.AspNetCore.SpaServices`i `Microsoft.AspNetCore.NodeServices` służy do automatycznego tworzenia rejestratora konsoli, gdy rejestrowanie nie jest skonfigurowane.

#### <a name="new-behavior"></a>Nowe zachowanie

`Microsoft.AspNetCore.SpaServices`i `Microsoft.AspNetCore.NodeServices` nie będą wyświetlać dzienników konsoli, chyba że rejestrowanie jest skonfigurowane.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Istnieje potrzeba dostosowania do sposobu, w jaki inne ASP.NET pakiety Core implementują rejestrowanie.

#### <a name="recommended-action"></a>Zalecana akcja

Jeśli wymagane jest stare zachowanie, aby skonfigurować `services.AddLogging(builder => builder.AddConsole())` rejestrowanie konsoli, dodaj do metody. `Setup.ConfigureServices`

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak

<!--

#### Affected APIs

Not detectable via API analysis

-->
