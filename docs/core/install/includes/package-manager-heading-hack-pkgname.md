---
ms.openlocfilehash: 4340ed7444681b4601dea50c93926b0ee0c07eec
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134109"
---

Pakiety dodane do kanałów menedżera pakietów są `{product}-{type}-{version}`nazwane w formacie hackable: .

- **Produktu**\
Typ produktu .NET do zainstalowania. Prawidłowe opcje to:

  - dotnet
  - aspnetcore

- **Typu**\
Wybiera SDK lub środowisko wykonawcze. Prawidłowe opcje to:

  - sdk
  - środowisko uruchomieniowe

- **Wersja**\
Wersja pakietu SDK lub środowiska wykonawczego do zainstalowania. W tym artykule zawsze będzie instrukcje dotyczące najnowszej obsługiwanej wersji. Prawidłowe opcje to każda wydana wersja, taka jak:

  - 3.1
  - 3.0
  - 2.1

  Jest możliwe, że SDK/runtime próbujesz pobrać nie jest dostępny dla twojej dystrybucji Linuksa. Aby uzyskać listę obsługiwanych dystrybucji, zobacz [.NET Core zależności i wymagania](../dependencies.md?pivots=os-linux).

### <a name="examples"></a>Przykłady

- Zainstaluj środowisko wykonawcze ASP.NET Core 3.1:`aspnetcore-runtime-3.1`
- Zainstaluj środowisko uruchomieniowe .NET Core 2.1:`dotnet-runtime-2.1`
- Zainstaluj pakiet .NET Core 3.1 SDK:`dotnet-sdk-3.1`

### <a name="package-missing"></a>Brak pakietu

Jeśli kombinacja wersji pakietu nie działa, nie jest dostępna. Na przykład nie ma ASP.NET core SDK, składniki SDK są dołączone do .NET Core SDK. Wartość `aspnetcore-sdk-2.2` jest niepoprawna `dotnet-sdk-2.2`i powinna być . Aby uzyskać listę dystrybucji systemu Linux obsługiwanych przez program .NET Core, zobacz [.NET Core zależności i wymagania](../dependencies.md?pivots=os-linux).
