---
ms.openlocfilehash: 4d99d0b6e99a7a9b976cf11832b33ad3bdc6d299
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901616"
---
### <a name="hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies"></a>Hosting: ObjectPoolProvider usunięte z zależności WebHostBuilder

W ramach wprowadzania ASP.NET Core więcej opłat za odtwarzanie, `ObjectPoolProvider` został usunięty z głównego zestawu zależności. Poszczególne składniki opierają się na `ObjectPoolProvider` teraz dodają sam siebie.

Aby zapoznać się z omówieniem, zobacz [dotnet/aspnetcore # 5944](https://github.com/dotnet/aspnetcore/issues/5944).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

`WebHostBuilder` zapewnia `ObjectPoolProvider` domyślnie w kontenerze DI.

#### <a name="new-behavior"></a>Nowe zachowanie

`WebHostBuilder` nie zapewnia już `ObjectPoolProvider` domyślnie w kontenerze DI.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Ta zmiana została wprowadzona, aby ASP.NET Core więcej opłat za odtwarzanie.

#### <a name="recommended-action"></a>Zalecane działanie

Jeśli składnik wymaga `ObjectPoolProvider`, należy dodać go do swoich zależności za pośrednictwem `IServiceCollection`.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
