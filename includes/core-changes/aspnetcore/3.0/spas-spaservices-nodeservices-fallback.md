---
ms.openlocfilehash: e5355387d5cb6d9e6de89f5b85e64bc100b32ae1
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522655"
---
### <a name="spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger"></a>Aplikacji jednostronicowych: SpaServices i NodeServices nie są już z powrotem do rejestratora konsoli

<xref:Microsoft.AspNetCore.SpaServices?displayProperty=nameWithType> i <xref:Microsoft.AspNetCore.NodeServices?displayProperty=nameWithType> nie będą wyświetlane dzienniki konsoli, chyba że rejestrowanie jest skonfigurowane.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

`Microsoft.AspNetCore.SpaServices` i `Microsoft.AspNetCore.NodeServices` używane do automatycznego tworzenia rejestratora konsoli, gdy rejestrowanie nie jest skonfigurowane.

#### <a name="new-behavior"></a>Nowe zachowanie

`Microsoft.AspNetCore.SpaServices` i `Microsoft.AspNetCore.NodeServices` nie będą wyświetlane dzienniki konsoli, chyba że rejestrowanie jest skonfigurowane.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Istnieje potrzeba dopasowania metody rejestrowania w innych pakietach ASP.NET Core.

#### <a name="recommended-action"></a>Zalecana akcja

Jeśli jest wymagane stare zachowanie, aby skonfigurować rejestrowanie konsoli, Dodaj `services.AddLogging(builder => builder.AddConsole())` do metody `Setup.ConfigureServices`.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak

<!--

#### Affected APIs

Not detectable via API analysis

-->
