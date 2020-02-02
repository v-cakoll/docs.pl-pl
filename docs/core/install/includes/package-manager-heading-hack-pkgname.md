---
ms.openlocfilehash: ef3e4f9f8145677732b9d2e66d416be277697f55
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920634"
---

Pakiety dodane do kanałów informacyjnych Menedżera pakietów są nazywane w formacie włamywania: `{product}-{type}-{version}`.

- \ **produktu**
Typ produktu .NET do zainstalowania. Prawidłowe opcje to:

  - dotnet
  - aspnetcore

- **typ**\
Wybiera zestaw SDK lub środowisko uruchomieniowe. Prawidłowe opcje to:

  - sdk
  - środowisko uruchomieniowe

- \ **wersji**
Wersja zestawu SDK lub środowiska uruchomieniowego do zainstalowania. Ten artykuł będzie zawsze zawierać instrukcje dotyczące najnowszej obsługiwanej wersji. Prawidłowe opcje to wszystkie wydane wersje, takie jak:

  - 3.0
  - 2.2
  - 2.1

### <a name="examples"></a>Przykłady

- Zainstaluj zestaw SDK platformy .NET Core 2,2: `dotnet-sdk-2.2`
- Zainstaluj środowisko uruchomieniowe ASP.NET Core 3,1: `aspnetcore-runtime-3.1`
- Zainstaluj środowisko uruchomieniowe programu .NET Core 2,1: `dotnet-runtime-2.1`

### <a name="package-missing"></a>Brak pakietu

Jeśli kombinacja pakiet-wersja nie działa, jest niedostępna. Na przykład nie istnieje zestaw ASP.NET Core SDK, składniki zestawu SDK są dołączone do zestaw .NET Core SDK. Wartość `aspnetcore-sdk-2.2` jest niepoprawna i powinna być `dotnet-sdk-2.2`.
