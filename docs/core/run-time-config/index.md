---
title: Konfiguracja czasu wykonywania
description: Dowiedz się, jak skonfigurować aplikacje platformy .NET Core za pomocą ustawień konfiguracji czasu wykonywania.
ms.date: 11/13/2019
ms.openlocfilehash: e3922f6df81198b5e122f16d5cfc4b6d15cbb4ae
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567387"
---
# <a name="net-core-run-time-configuration-settings"></a>Ustawienia konfiguracji środowiska uruchomieniowego .NET Core

Platforma .NET Core obsługuje używanie plików konfiguracji i zmiennych środowiskowych w celu skonfigurowania zachowania aplikacji .NET Core w czasie wykonywania. Konfiguracja czasu wykonywania jest atrakcyjną opcją, jeśli:

- Nie jesteś własnością ani nie kontrolujesz kodu źródłowego dla aplikacji, dlatego nie można programowo skonfigurować go.

- Wiele wystąpień aplikacji jest wykonywanych w tym samym czasie w pojedynczym systemie i chcesz skonfigurować każdą z nich w celu uzyskania optymalnej wydajności.

> [!NOTE]
> Ta dokumentacja jest w toku. Jeśli zauważysz, że informacje przedstawione w tym miejscu są niekompletne lub niedokładne, należy [otworzyć problem](https://github.com/dotnet/docs/issues) , aby poinformować nas o tym lub [przesłać żądanie ściągnięcia](https://github.com/dotnet/docs/pulls) w celu rozwiązania problemu. Informacje dotyczące przesyłania żądań ściągnięcia dla repozytorium dotnet/docs można znaleźć w [przewodniku współautora](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).

Platforma .NET Core udostępnia następujące mechanizmy konfigurowania aplikacji w czasie wykonywania:

- [Plik runtimeconfig. JSON](#runtimeconfigjson)

- [Zmienne środowiskowe](#environment-variables)

Artykuły w tej sekcji dokumentacji obejmują elementy uporządkowane według kategorii, na przykład debugowania i wyrzucania elementów bezużytecznych. Dostępne opcje konfiguracji są wyświetlane dla *runtimeconfig. JSON* (tylko dla platformy .NET Core), *App. config* (tylko .NET Framework) i zmiennych środowiskowych.

## <a name="runtimeconfigjson"></a>runtimeconfig. JSON

Określ opcje konfiguracji czasu wykonywania w sekcji **configProperties** pliku *runtimeconfig. JSON* . Ta sekcja ma postać:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "config-property-name1": "config-value1",
         "config-property-name2": "config-value2"
      }
   }
}
```

Oto przykładowy plik:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": true,
         "System.GC.RetainVM": true,
         "System.Threading.ThreadPool.MinThreads": "4",
         "System.Threading.ThreadPool.MaxThreads": "25"
      }
   }
}
```

Plik *runtimeconfig. JSON* jest tworzony automatycznie w katalogu kompilacji przez polecenie [kompilacji dotnet](../tools/dotnet-build.md) . Jest również tworzony w przypadku wybrania opcji menu **kompilacja** w programie Visual Studio. Następnie można edytować plik po jego utworzeniu.

Niektóre wartości konfiguracji można również ustawić programowo, wywołując metodę <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType>.

## <a name="environment-variables"></a>Zmienne środowiskowe

Zmienne środowiskowe mogą służyć do dostarczania niektórych informacji o konfiguracji czasu wykonywania. Pokrętła konfiguracji określone jako zmienne środowiskowe zwykle mają prefiks **COMPlus_** .

Zmienne środowiskowe można definiować w panelu sterowania systemu Windows, w wierszu polecenia lub programowo, wywołując metodę <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> w systemach Windows i UNIX.

W poniższych przykładach pokazano, jak ustawić zmienną środowiskową w wierszu polecenia:

```shell
# Windows
set COMPlus_GCRetainVM=1

# Powershell
$env:COMPlus_GCRetainVM="1"

# Unix
export COMPlus_GCRetainVM=1
```
