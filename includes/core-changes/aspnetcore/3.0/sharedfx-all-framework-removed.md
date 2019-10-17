---
ms.openlocfilehash: 959f3959c28c7d0159be7a213986345e2865b9a2
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394440"
---
### <a name="shared-framework-removed-microsoftaspnetcoreall"></a>Udostępnione środowisko: Usunięto Microsoft. AspNetCore. All

Począwszy od ASP.NET Core 3,0, pakiet "`Microsoft.AspNetCore.All`" oraz zgodna struktura współdzielona `Microsoft.AspNetCore.All` nie są już generowane. Ten pakiet jest dostępny w ASP.NET Core 2,2 i nadal będzie otrzymywać aktualizacje obsługi w programie ASP.NET Core 2,1.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Aplikacje mogą korzystać z pakietu "`Microsoft.AspNetCore.All`" jako docelowej platformy współdzielonej `Microsoft.AspNetCore.All` na platformie .NET Core.

#### <a name="new-behavior"></a>Nowe zachowanie

Platforma .NET Core 3,0 nie obejmuje współdzielonej platformy `Microsoft.AspNetCore.All`.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Pakiet "`Microsoft.AspNetCore.All`" zawiera dużą liczbę zależności zewnętrznych.

#### <a name="recommended-action"></a>Zalecana akcja

Migruj projekt, aby użyć platformy `Microsoft.AspNetCore.App`. Składniki, które wcześniej były dostępne w `Microsoft.AspNetCore.All`, są nadal dostępne w programie NuGet. Te składniki są teraz wdrażane wraz z aplikacją, a nie uwzględniane w strukturze udostępnionej.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
