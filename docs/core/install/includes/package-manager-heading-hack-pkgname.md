---
ms.openlocfilehash: 47e8e15a64236d8ade2febb1add81fa4e5c030d9
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116149"
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

### <a name="troubleshoot"></a>Rozwiązywanie problemów

Jeśli kombinacja pakietów nie działa, jest niedostępna. Na przykład nie istnieje zestaw ASP.NET Core SDK, składniki zestawu SDK są dołączone do zestaw .NET Core SDK. Wartość `aspnetcore-sdk-2.2` jest niepoprawna i powinna być `dotnet-sdk-2.2`
