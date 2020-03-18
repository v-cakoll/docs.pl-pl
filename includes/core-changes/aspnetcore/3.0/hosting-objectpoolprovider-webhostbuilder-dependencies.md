---
ms.openlocfilehash: 4d99d0b6e99a7a9b976cf11832b33ad3bdc6d299
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901616"
---
### <a name="hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies"></a>Hosting: ObjectPoolProvider usunięty z zależności WebHostBuilder

W ramach dokonywania ASP.NET Core więcej `ObjectPoolProvider` zapłacić za grę, został usunięty z głównego zestawu zależności. Konkretne składniki, `ObjectPoolProvider` na których polegasz, teraz same je dodają.

Aby uzyskać do dyskusji, zobacz [dotnet/aspnetcore#5944](https://github.com/dotnet/aspnetcore/issues/5944).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

`WebHostBuilder``ObjectPoolProvider` domyślnie w kontenerze DI.

#### <a name="new-behavior"></a>Nowe zachowanie

`WebHostBuilder`nie jest `ObjectPoolProvider` już domyślnie udostępnia w kontenerze DI.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Ta zmiana została winna, aby ASP.NET Core więcej płacić za grę.

#### <a name="recommended-action"></a>Zalecana akcja

Jeśli składnik `ObjectPoolProvider`wymaga, musi zostać dodany do `IServiceCollection`zależności za pośrednictwem pliku .

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
