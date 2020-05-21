---
title: Opcje konfiguracji czasu wykonywania
description: Dowiedz się, jak skonfigurować aplikacje platformy .NET Core za pomocą ustawień konfiguracji czasu wykonywania.
ms.date: 01/21/2020
ms.openlocfilehash: 68690689fd4f936e3af76ab647f0b58d8ec6ca27
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761957"
---
# <a name="net-core-run-time-configuration-settings"></a>Ustawienia konfiguracji środowiska uruchomieniowego .NET Core

Platforma .NET Core obsługuje używanie plików konfiguracji i zmiennych środowiskowych w celu skonfigurowania zachowania aplikacji .NET Core w czasie wykonywania. Konfiguracja czasu wykonywania jest atrakcyjną opcją, jeśli:

- Nie jesteś własnością ani nie kontrolujesz kodu źródłowego dla aplikacji, dlatego nie można programowo skonfigurować go.

- Wiele wystąpień aplikacji jest wykonywanych w tym samym czasie w pojedynczym systemie i chcesz skonfigurować każdą z nich w celu uzyskania optymalnej wydajności.

> [!NOTE]
> Ta dokumentacja jest w toku. Jeśli zauważysz, że informacje przedstawione w tym miejscu są niekompletne lub niedokładne, należy [otworzyć problem](https://github.com/dotnet/docs/issues) , aby poinformować nas o tym lub [przesłać żądanie ściągnięcia](https://github.com/dotnet/docs/pulls) w celu rozwiązania problemu. Informacje o przesyłaniu żądań ściągnięcia dla repozytorium dotnet/docs można znaleźć w [przewodniku współautora](https://docs.microsoft.com/contribute/dotnet/dotnet-contribute).

Platforma .NET Core udostępnia następujące mechanizmy konfigurowania zachowania aplikacji w czasie wykonywania:

- [Plik runtimeconfig. JSON](#runtimeconfigjson)

- [Właściwości programu MSBuild](#msbuild-properties)

- [Zmienne środowiskowe](#environment-variables)

> [!TIP]
> Skonfigurowanie opcji czasu wykonywania przy użyciu zmiennej środowiskowej stosuje ustawienie do wszystkich aplikacji platformy .NET Core. Skonfigurowanie opcji czasu wykonywania w pliku *runtimeconfig. JSON* lub projektu powoduje zastosowanie ustawienia tylko do tej aplikacji.

Niektóre wartości konfiguracji można również ustawić programowo, wywołując <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> metodę.

Artykuły w tej sekcji dokumentacji są zorganizowane według kategorii, na przykład [debugowania](debugging-profiling.md) i [wyrzucania elementów bezużytecznych](garbage-collector.md). W stosownych przypadkach opcje konfiguracji są wyświetlane dla plików *runtimeconfig. JSON* , właściwości programu MSBuild, zmiennych środowiskowych i, w przypadku plików z odsyłaczem, *pliku App. config* dla projektów .NET Framework.

## <a name="runtimeconfigjson"></a>runtimeconfig. JSON

Po [skompilowaniu](../tools/dotnet-build.md)projektu w katalogu wyjściowym zostanie wygenerowany plik *[nazwa_aplikacji]. runtimeconfig. JSON* . Jeśli plik *runtimeconfig. Template. JSON* istnieje w tym samym folderze co plik projektu, wszystkie opcje konfiguracji, które zawiera, są scalane w pliku *[nazwa_aplikacji]. runtimeconfig. JSON* . Jeśli tworzysz aplikację samodzielnie, umieść wszystkie opcje konfiguracji w pliku *runtimeconfig. Template. JSON* . Jeśli właśnie uruchamiasz aplikację, Wstaw ją bezpośrednio do pliku *[nazwa_aplikacji]. runtimeconfig. JSON* .

> [!NOTE]
> Plik *[nazwa_aplikacji]. runtimeconfig. JSON* zostanie nadpisany po kolejnych kompilacjach.

Określ opcje konfiguracji czasu wykonywania w sekcji **configProperties** plików *runtimeconfig. JSON* . Ta sekcja ma postać:

```json
"configProperties": {
  "config-property-name1": "config-value1",
  "config-property-name2": "config-value2"
}
```

### <a name="example-appnameruntimeconfigjson-file"></a>Przykład [nazwa_aplikacji]. runtimeconfig. JSON

Jeśli umieszczasz opcje w wyjściowym pliku JSON, zastąp je `runtimeOptions` właściwością.

```json
{
  "runtimeOptions": {
    "tfm": "netcoreapp3.1",
    "framework": {
      "name": "Microsoft.NETCore.App",
      "version": "3.1.0"
    },
    "configProperties": {
      "System.GC.Concurrent": false,
      "System.Threading.ThreadPool.MinThreads": 4,
      "System.Threading.ThreadPool.MaxThreads": 25
    }
  }
}
```

### <a name="example-runtimeconfigtemplatejson-file"></a>Przykład pliku runtimeconfig. Template. JSON

Jeśli umieszczasz opcje w pliku JSON szablonu, Pomiń `runtimeOptions` Właściwość.

```json
{
  "configProperties": {
    "System.GC.Concurrent": false,
    "System.Threading.ThreadPool.MinThreads": "4",
    "System.Threading.ThreadPool.MaxThreads": "25"
  }
}
```

## <a name="msbuild-properties"></a>właściwości programu MSBuild

Niektóre opcje konfiguracji czasu wykonywania można ustawić przy użyciu właściwości programu MSBuild w pliku *. csproj* lub *. vbproj* projektów .NET Core w stylu zestawu SDK. Właściwości programu MSBuild mają pierwszeństwo przed opcjami ustawionymi w pliku *runtimeconfig. Template. JSON* . Zastąpią także wszystkie opcje ustawione w pliku *[nazwa_aplikacji]. runtimeconfig. JSON* w czasie kompilacji.

Oto przykładowy plik projektu w stylu zestawu SDK z właściwościami MSBuild służący do konfigurowania zachowania w czasie wykonywania:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
    <ThreadPoolMaxThreads>25</ThreadPoolMaxThreads>
  </PropertyGroup>

</Project>
```

Właściwości programu MSBuild służące do konfigurowania zachowania w czasie wykonywania są zanotowane w poszczególnych artykułach dla każdego obszaru, na przykład na [wyrzucaniu elementów bezużytecznych](garbage-collector.md). Są one również wymienione w sekcji [Konfiguracja czasu wykonywania](../project-sdk/msbuild-props.md#run-time-configuration-properties) w temacie Informacje o właściwościach programu MSBuild dla projektów w stylu zestawu SDK.

## <a name="environment-variables"></a>Zmienne środowiskowe

Zmienne środowiskowe mogą służyć do dostarczania niektórych informacji o konfiguracji czasu wykonywania. Skonfigurowanie opcji czasu wykonywania przy użyciu zmiennej środowiskowej stosuje ustawienie do wszystkich aplikacji platformy .NET Core. Pokrętła konfiguracji określone jako zmienne środowiskowe zwykle mają prefiks **COMPlus_**.

Zmienne środowiskowe można definiować w panelu sterowania systemu Windows, w wierszu polecenia lub programowo poprzez wywołanie <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> metody w systemach Windows i UNIX.

W poniższych przykładach pokazano, jak ustawić zmienną środowiskową w wierszu polecenia:

```shell
# Windows
set COMPlus_GCRetainVM=1

# Powershell
$env:COMPlus_GCRetainVM="1"

# Unix
export COMPlus_GCRetainVM=1
```
