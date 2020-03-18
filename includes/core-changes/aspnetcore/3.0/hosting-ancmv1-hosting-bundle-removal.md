---
ms.openlocfilehash: 82103d82a6f68c62f3532608718bc71b0ba126bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901582"
---
### <a name="hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle"></a>Hosting: AspNetCoreModule V1 usunięty z pakietu hostingowego systemu Windows

Począwszy od ASP.NET Core 3.0, pakiet hostingowy systemu Windows nie będzie zawierał aspNetCoreModule (ANCM) V1.

ANCM V2 jest wstecznie kompatybilny z ANCM OutOfProcess i jest zalecany do użytku z aplikacjami ASP.NET Core 3.0.

Aby uzyskać do dyskusji, zobacz [dotnet/aspnetcore#7095](https://github.com/dotnet/aspnetcore/issues/7095).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

ANCM V1 znajduje się w pakiecie hostingowym systemu Windows.

#### <a name="new-behavior"></a>Nowe zachowanie

Ancm V1 nie jest uwzględniony w pakiecie hostingu systemu Windows.

#### <a name="reason-for-change"></a>Przyczyna zmiany

ANCM V2 jest wstecznie kompatybilny z ANCM OutOfProcess i jest zalecany do użytku z aplikacjami ASP.NET Core 3.0.

#### <a name="recommended-action"></a>Zalecana akcja

Użyj ANCM V2 z ASP.NET aplikacjami Core 3.0.

Jeśli wymagany jest ancm V1, można go zainstalować za pomocą pakietu hostingowego ASP.NET Core 2.1 lub 2.2 Windows Hosting Bundle.

Ta zmiana spowoduje przerwanie ASP.NET aplikacji Core 3.0, które:

- Wyraźnie zdecydował się na korzystanie z `<AspNetCoreModuleName>AspNetCoreModule</AspNetCoreModuleName>`ANCM V1 z .
- Mieć niestandardowy plik *web.config* z . `<add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />`

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
