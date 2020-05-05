---
ms.openlocfilehash: e5355387d5cb6d9e6de89f5b85e64bc100b32ae1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522655"
---
### <a name="spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger"></a>Aplikacji jednostronicowych: SpaServices i NodeServices nie są już z powrotem do rejestratora konsoli

<xref:Microsoft.AspNetCore.SpaServices?displayProperty=nameWithType>nie <xref:Microsoft.AspNetCore.NodeServices?displayProperty=nameWithType> będą wyświetlane dzienniki konsoli, chyba że skonfigurowano rejestrowanie.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

`Microsoft.AspNetCore.SpaServices`służy `Microsoft.AspNetCore.NodeServices` do automatycznego tworzenia rejestratora konsoli, gdy rejestrowanie nie jest skonfigurowane.

#### <a name="new-behavior"></a>Nowe zachowanie

`Microsoft.AspNetCore.SpaServices`nie `Microsoft.AspNetCore.NodeServices` będą wyświetlane dzienniki konsoli, chyba że skonfigurowano rejestrowanie.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Istnieje potrzeba dopasowania metody rejestrowania w innych pakietach ASP.NET Core.

#### <a name="recommended-action"></a>Zalecana akcja

Jeśli stare zachowanie jest wymagane, aby skonfigurować rejestrowanie konsoli, Dodaj `services.AddLogging(builder => builder.AddConsole())` do `Setup.ConfigureServices` metody.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak

<!--

#### Affected APIs

Not detectable via API analysis

-->
