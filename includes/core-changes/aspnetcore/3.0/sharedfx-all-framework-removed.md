---
ms.openlocfilehash: 959f3959c28c7d0159be7a213986345e2865b9a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394440"
---
### <a name="shared-framework-removed-microsoftaspnetcoreall"></a>Struktura udostępniona: usunięto microsoft.aspNetcore.All

Począwszy od ASP.NET Core `Microsoft.AspNetCore.All` 3.0, `Microsoft.AspNetCore.All` metapackage i pasujące udostępnione juz nie są już produkowane. Ten pakiet jest dostępny w ASP.NET Core 2.2 i będzie nadal otrzymywać aktualizacje obsługi w ASP.NET Core 2.1.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Aplikacje mogą `Microsoft.AspNetCore.All` używać metapakietu `Microsoft.AspNetCore.All` do kierowania udostępnionej struktury na .NET Core.

#### <a name="new-behavior"></a>Nowe zachowanie

.NET Core 3.0 nie `Microsoft.AspNetCore.All` zawiera udostępnionej struktury.

#### <a name="reason-for-change"></a>Przyczyna zmiany

`Microsoft.AspNetCore.All` Metapakiet zawiera dużą liczbę zależności zewnętrznych.

#### <a name="recommended-action"></a>Zalecana akcja

Migracja projektu do korzystania `Microsoft.AspNetCore.App` z platformy. Składniki, które były `Microsoft.AspNetCore.All` wcześniej dostępne w są nadal dostępne na NuGet. Te składniki są teraz wdrażane z aplikacją, a nie są uwzględniane w udostępnionej strukturze.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
