---
ms.openlocfilehash: 51b3c1b3e3d61b23a0511ca807afef0269ac9ee4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77465978"
---

Pakiety dodane do kanałów menedżera pakietów są nazwane `{product}-{type}-{version}`w formacie hackable: .

- **Produktu**\
Typ produktu .NET do zainstalowania. Prawidłowe opcje to:

  - dotnet
  - aspnetcore (polski)

- **Typu**\
Wybiera zestaw SDK lub czas wykonywania. Prawidłowe opcje to:

  - sdk
  - środowisko uruchomieniowe

- **Wersja**\
Wersja sdk lub czas wykonywania do zainstalowania. W tym artykule zawsze zostaną opublikowane instrukcje dotyczące najnowszej obsługiwanej wersji. Prawidłowe opcje to dowolna wydana wersja, taka jak:

  - 3.1
  - 3.0
  - 2.1

  Możliwe, że zestaw SDK/runtime, który próbujesz pobrać, nie jest dostępny dla twojej dystrybucji systemu Linux. Aby uzyskać listę obsługiwanych dystrybucji, zobacz [zależności i wymagania programu .NET Core](../dependencies.md?pivots=os-linux).

### <a name="examples"></a>Przykłady

- Zainstaluj ASP.NET core 3.1:`aspnetcore-runtime-3.1`
- Zainstaluj czas uruchomieniowy .NET Core 2.1:`dotnet-runtime-2.1`
- Zainstaluj zestaw SDK .NET Core 3.0:`dotnet-sdk-3.0`

### <a name="package-missing"></a>Brakuje pakietu

Jeśli kombinacja wersji pakietu nie działa, nie jest dostępna. Na przykład nie ma ASP.NET Core SDK, składniki sdk są dołączone do .NET Core SDK. Wartość `aspnetcore-sdk-2.2` jest niepoprawna `dotnet-sdk-2.2`i powinna być . Aby uzyskać listę dystrybucji systemu Linux obsługiwanych przez program .NET Core, zobacz [zależności i wymagania programu .NET Core](../dependencies.md?pivots=os-linux).
