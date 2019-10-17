---
ms.openlocfilehash: 16b9fde49f513643a37f65f3e926a34fc991c55a
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393928"
---
### <a name="hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies"></a>Hosting: ObjectPoolProvider usunięte z zależności WebHostBuilder

W ramach wprowadzania ASP.NET Core więcej opłat za odtwarzanie, `ObjectPoolProvider` został usunięty z głównego zestawu zależności. Określone składniki polegające na `ObjectPoolProvider` teraz dodają go.

W przypadku dyskusji zobacz [ASPNET/AspNetCore # 5944](https://github.com/aspnet/AspNetCore/issues/5944).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

`WebHostBuilder` domyślnie zapewnia `ObjectPoolProvider` w kontenerze DI.

#### <a name="new-behavior"></a>Nowe zachowanie

`WebHostBuilder` nie zapewnia już domyślnie `ObjectPoolProvider` w kontenerze DI.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Ta zmiana została wprowadzona, aby ASP.NET Core więcej opłat za odtwarzanie.

#### <a name="recommended-action"></a>Zalecana akcja

Jeśli składnik wymaga `ObjectPoolProvider`, należy go dodać do zależności za pośrednictwem `IServiceCollection`.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
