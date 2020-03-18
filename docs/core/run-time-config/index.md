---
title: Opcje konfiguracji w czasie wykonywania
description: Dowiedz się, jak skonfigurować aplikacje .NET Core przy użyciu ustawień konfiguracji w czasie wykonywania.
ms.date: 01/21/2020
ms.openlocfilehash: ddf68c30e620a06856f65e71bd050e1b77618f20
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399162"
---
# <a name="net-core-run-time-configuration-settings"></a>Ustawienia konfiguracji środowiska .NET Core w czasie wykonywania

Program .NET Core obsługuje używanie plików konfiguracyjnych i zmiennych środowiskowych w celu skonfigurowania zachowania aplikacji .NET Core w czasie wykonywania. Konfiguracja w czasie wykonywania jest atrakcyjną opcją, jeśli:

- Nie jesteś właścicielem lub kontrolować kod źródłowy dla aplikacji i dlatego nie można skonfigurować go programowo.

- Wiele wystąpień aplikacji uruchamia się w tym samym czasie w jednym systemie i chcesz skonfigurować każdy dla optymalnej wydajności.

> [!NOTE]
> Ta dokumentacja jest w toku. Jeśli zauważysz, że przedstawione tutaj informacje są niekompletne lub niedokładne, [otwórz problem,](https://github.com/dotnet/docs/issues) aby poinformować nas o tym, albo [prześlij żądanie ściągnięcia,](https://github.com/dotnet/docs/pulls) aby rozwiązać problem. Aby uzyskać informacje na temat przesyłania żądań ściągnięcia dla repozytorium dotnet/docs, zobacz [przewodnik współautora](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).

Program .NET Core udostępnia następujące mechanizmy konfigurowania zachowania aplikacji w czasie wykonywania:

- [Plik runtimeconfig.json](#runtimeconfigjson)

- [MsBuild właściwości](#msbuild-properties)

- [Zmienne środowiskowe](#environment-variables)

Niektóre wartości konfiguracji można również ustawić programowo, wywołując <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> metodę.

Artykuły w tej sekcji dokumentacji są zorganizowane według kategorii, na przykład [debugowania](debugging-profiling.md) i [wyrzucania elementów bezużytecznych](garbage-collector.md). W stosownych przypadkach opcje konfiguracji są wyświetlane dla plików *runtimeconfig.json,* właściwości MSBuild, zmiennych środowiskowych i, dla odsyłacza, plików *app.config* dla projektów .NET Framework.

## <a name="runtimeconfigjson"></a>runtimeconfig.json

Po [skonstruowaniu](../tools/dotnet-build.md)projektu w katalogu wyjściowym generowany jest plik *[nazwa_aplikacji].runtimeconfig.json.* Jeśli plik *runtimeconfig.template.json* istnieje w tym samym folderze co plik projektu, wszystkie opcje konfiguracji, które zawiera, są scalane z *plikiem [nazwa_aplikacji].runtimeconfig.json.* Jeśli samodzielnie budujesz aplikację, umieść dowolne opcje konfiguracji w pliku *runtimeconfig.template.json.* Jeśli po prostu używasz aplikacji, wstaw je bezpośrednio do pliku *[nazwa aplikacji].runtimeconfig.json.*

> [!NOTE]
> Plik *[nazwa aplikacji].runtimeconfig.json* zostanie zastąpiony na kolejnych kompilacjach.

Określ opcje konfiguracji w czasie wykonywania w sekcji **configProperties** plików *runtimeconfig.json.* Ta sekcja ma formularz:

```json
"configProperties": {
  "config-property-name1": "config-value1",
  "config-property-name2": "config-value2"
}
```

### <a name="example-appnameruntimeconfigjson-file"></a>Przykładowy plik [nazwa aplikacji].runtimeconfig.json file

Jeśli umieszczasz opcje w wyjściowym pliku JSON, `runtimeOptions` zagnieździć je pod właściwością.

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

### <a name="example-runtimeconfigtemplatejson-file"></a>Przykładowy plik runtimeconfig.template.json

Jeśli umieszczasz opcje w pliku JSON szablonu, pomiń właściwość. `runtimeOptions`

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

Niektóre opcje konfiguracji w czasie wykonywania można ustawić przy użyciu właściwości MSBuild w pliku *csproj* lub *.vbproj* projektów .NET Core w stylu zestawu SDK. Właściwości MSBuild mają pierwszeństwo przed opcjami ustawionymi w pliku *runtimeconfig.template.json.* Zastępują one również wszystkie opcje ustawione w pliku *[nazwa_aplikacji].runtimeconfig.json* w czasie kompilacji.

Oto przykładowy plik projektu w stylu SDK z właściwościami MSBuild do konfigurowania zachowania w czasie wykonywania:

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

MsBuild właściwości do konfigurowania zachowania w czasie wykonywania są odnotowane w poszczególnych artykułów dla każdego obszaru, na przykład [wyrzucania elementów bezużytecznych](garbage-collector.md).

## <a name="environment-variables"></a>Zmienne środowiskowe

Zmiennych środowiskowych może służyć do dostarczania niektórych informacji o konfiguracji w czasie wykonywania. Pokrętła konfiguracji określone jako zmienne środowiskowe mają zazwyczaj prefiks **COMPlus_**.

Zmienne środowiskowe można definiować z Panelu sterowania systemu Windows, w <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> wierszu polecenia lub programowo, wywołując metodę zarówno w systemach Windows, jak i Unix.

W poniższych przykładach przedstawiono sposób ustawiania zmiennej środowiskowej w wierszu polecenia:

```shell
# Windows
set COMPlus_GCRetainVM=1

# Powershell
$env:COMPlus_GCRetainVM="1"

# Unix
export COMPlus_GCRetainVM=1
```
