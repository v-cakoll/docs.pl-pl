---
ms.openlocfilehash: 82103d82a6f68c62f3532608718bc71b0ba126bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901582"
---
### <a name="hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle"></a>Hosting: AspNetCoreModule V1 został usunięty z pakietu hostingu systemu Windows

Począwszy od ASP.NET Core 3,0, pakiet hostingu systemu Windows nie będzie zawierał AspNetCoreModule (ANCM) v1.

ANCM v2 jest zgodna z poprzednimi wersjami ANCM OutOfProcess i jest zalecane do użycia z aplikacjami ASP.NET Core 3,0.

Aby zapoznać się z omówieniem, zobacz [dotnet/aspnetcore # 7095](https://github.com/dotnet/aspnetcore/issues/7095).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

ANCM v1 jest zawarta w pakiecie hostingu systemu Windows.

#### <a name="new-behavior"></a>Nowe zachowanie

ANCM V1 nie jest uwzględniony w pakiecie hostingu systemu Windows.

#### <a name="reason-for-change"></a>Przyczyna zmiany

ANCM v2 jest zgodna z poprzednimi wersjami ANCM OutOfProcess i jest zalecane do użycia z aplikacjami ASP.NET Core 3,0.

#### <a name="recommended-action"></a>Zalecana akcja

Używaj ANCM v2 z aplikacjami ASP.NET Core 3,0.

Jeśli ANCM v1 jest wymagany, można go zainstalować przy użyciu pakietu hostingu systemu Windows w ASP.NET Core 2,1 lub 2,2.

Ta zmiana spowoduje przerwanie ASP.NET Core aplikacji 3,0, które:

- Jawnie wybrane do użycia ANCM V1 z `<AspNetCoreModuleName>AspNetCoreModule</AspNetCoreModuleName>`.
- Mieć niestandardowy plik *Web. config* z `<add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />`.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
