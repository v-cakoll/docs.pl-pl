---
ms.openlocfilehash: 7723892a33bf7dd8e475b2f696db5d9ab287e182
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602993"
---

Pakiety dodane do źródeł Menedżera pakietów są nazywane w formacie włamywania: `{product}-{type}-{version}` .

- **iloczyn**\
Typ produktu .NET do zainstalowania. Prawidłowe opcje to:

  - dotnet
  - aspnetcore

- **Wprowadź**\
Wybiera zestaw SDK lub środowisko uruchomieniowe. Prawidłowe opcje to:

  - sdk
  - środowisko uruchomieniowe

- **Wersja**\
Wersja zestawu SDK lub środowiska uruchomieniowego do zainstalowania. Ten artykuł będzie zawsze zawierać instrukcje dotyczące najnowszej obsługiwanej wersji. Prawidłowe opcje to wszystkie wydane wersje, takie jak:

  - 3,1
  - 3.0
  - 2.1

  Możliwe, że zestaw SDK/środowisko uruchomieniowe, które próbujesz pobrać, nie jest dostępny dla dystrybucji systemu Linux. Aby zapoznać się z listą obsługiwanych dystrybucji, zobacz temat [zależności i wymagania dotyczące platformy .NET Core](../linux.md).

### <a name="examples"></a>Przykłady

- Zainstaluj środowisko uruchomieniowe ASP.NET Core 3,1:`aspnetcore-runtime-3.1`
- Zainstaluj środowisko uruchomieniowe programu .NET Core 2,1:`dotnet-runtime-2.1`
- Zainstaluj zestaw SDK platformy .NET Core 3,1:`dotnet-sdk-3.1`

### <a name="package-missing"></a>Brak pakietu

Jeśli kombinacja pakiet-wersja nie działa, jest niedostępna. Na przykład nie istnieje zestaw ASP.NET Core SDK, składniki zestawu SDK są dołączone do zestaw .NET Core SDK. Wartość `aspnetcore-sdk-2.2` jest niepoprawna i powinna być `dotnet-sdk-2.2` . Aby uzyskać listę dystrybucji systemu Linux obsługiwanych przez platformę .NET Core, zobacz [zależności i wymagania dotyczące platformy .NET Core](../linux.md).
