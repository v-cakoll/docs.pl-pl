---
title: Tworzenie bibliotek za pomocą cli .NET Core
description: Dowiedz się, jak tworzyć biblioteki .NET Core przy użyciu.NET Core CLI. Utworzysz bibliotekę, która obsługuje wiele struktur.
author: cartermp
ms.date: 05/01/2017
ms.openlocfilehash: c23c1f027b4d6d09c50eb2257d34f72ec56302f4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503505"
---
# <a name="develop-libraries-with-the-net-core-cli"></a>Tworzenie bibliotek za pomocą cli .NET Core

W tym artykule omówiono sposób pisania bibliotek dla programu .NET przy użyciu cli.NET Core. CLI zapewnia wydajne i niskiego poziomu środowiska, który działa w każdym obsługiwanym środowisku operacyjnym. Nadal można tworzyć biblioteki za pomocą programu Visual Studio, a jeśli jest to preferowane środowisko [odnoszą się do przewodnika programu Visual Studio](library-with-visual-studio.md).

## <a name="prerequisites"></a>Wymagania wstępne

Potrzebujesz [.NET Core SDK i CLI](https://dotnet.microsoft.com/download) zainstalowane na komputerze.

W przypadku sekcji tego dokumentu dotyczących wersji .NET Framework potrzebna jest zainstalowana platforma [.NET Framework](https://dotnet.microsoft.com) na komputerze z systemem Windows.

Ponadto jeśli chcesz obsługiwać starsze obiekty docelowe .NET Framework, musisz zainstalować pakiety docelowe lub pakiety deweloperskie ze [strony archiwum pobierania .NET](https://dotnet.microsoft.com/download/archives). Zapoznaj się z poniższą tabelą:

| Wersja programu .NET Framework | Co pobrać                                       |
| ---------------------- | ------------------------------------------------------ |
| 4.6.1                  | Pakiet kierowania .NET Framework 4.6.1                    |
| 4.6                    | Pakiet targetowania .NET Framework 4.6                      |
| 4.5.2                  | Pakiet deweloperski .NET Framework 4.5.2                    |
| 4.5.1                  | Pakiet deweloperski .NET Framework 4.5.1                    |
| 4.5                    | Zestaw Windows Software Development Kit dla systemu Windows 8         |
| 4.0                    | Zestaw Windows SDK dla systemów Windows 7 i .NET Framework 4         |
| 2,0, 3,0 i 3,5      | Środowisko uruchomieniowe programu .NET Framework 3.5 z dodatkiem SP1 (lub wersja systemu Windows 8+) |

## <a name="how-to-target-the-net-standard"></a>Jak kierować reklamy na standard .NET

Jeśli nie znasz standardu .NET, zapoznaj się z [.NET Standard,](../../standard/net-standard.md) aby dowiedzieć się więcej.

W tym artykule znajduje się tabela, która mapuje wersje .NET Standard do różnych implementacji:

[!INCLUDE [net-standard-table](../../../includes/net-standard-table.md)]

Oto, co ta tabela oznacza dla celów tworzenia biblioteki:

Wersja .NET Standard, którą wybierzesz, będzie kompromisem między dostępem do najnowszych interfejsów API a możliwością kierowania większej liczby implementacji .NET i wersji .NET Standard. Możesz kontrolować zakres platform docelowych i wersji, `netstandardX.X` wybierając `X.X` wersję (gdzie jest numer wersji)`.csproj` i `.fsproj`dodając ją do pliku projektu (lub ).

Podczas kierowania na standard .NET są dostępne trzy opcje podstawowe, w zależności od potrzeb.

1. Można użyć domyślnej wersji .NET Standard dostarczonej `netstandard1.4`przez szablony, która zapewnia dostęp do większości interfejsów API w standardzie .NET, a jednocześnie jest zgodna z platformą UWP, .NET Framework 4.6.1 i .NET Standard 2.0.

    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <TargetFramework>netstandard1.4</TargetFramework>
      </PropertyGroup>
    </Project>
    ```

2. Można użyć niższej lub wyższej wersji programu .NET Standard, `TargetFramework` modyfikując wartość w węźle pliku projektu.

    Wersje .NET Standard są wstecznie kompatybilne. Oznacza to, że `netstandard1.0` `netstandard1.1` biblioteki działają na platformach i wyższe. Jednak nie ma zgodności z przyszłością. Niższe platformy .NET Standard nie mogą odwoływać się do wyższych. Oznacza to, że `netstandard1.0` biblioteki nie `netstandard1.1` mogą odwoływać się do bibliotek przeznaczonych do pracy lub wyższych. Wybierz wersję standardową, która ma odpowiednią kombinację interfejsów API i obsługi platform y dla Twoich potrzeb. Polecamy `netstandard1.4` na razie.

3. Jeśli chcesz kierować .NET Framework w wersji 4.0 lub poniżej lub chcesz użyć interfejsu API dostępnego w `System.Drawing`.NET Framework, ale nie w .NET Standard (na przykład), przeczytaj poniższe sekcje i dowiedz się, jak kierować wiele.

## <a name="how-to-target-net-framework"></a>Jak kierować reklamy do programu .NET Framework

> [!NOTE]
> W tych instrukcjach założono, że na komputerze jest zainstalowana platforma .NET Framework. Zapoznaj się z [wymaganiami wstępnymi,](#prerequisites) aby zainstalować zależności.

Należy pamiętać, że niektóre wersje .NET Framework używane w tym miejscu nie są już obsługiwane. Zapoznaj się z często [zadawanymi pytaniami](https://support.microsoft.com/gp/framework_faq/en-us) dotyczącymi zasad cyklu pomocy technicznej programu .NET Framework dotyczące nieobsługiwanych wersji.

Jeśli chcesz osiągnąć maksymalną liczbę deweloperów i projektów, użyj .NET Framework 4.0 jako cel linii bazowej. Aby kierować .NET Framework, rozpocząć przy użyciu poprawnego moniker struktury docelowej (TFM), który odpowiada .NET Framework wersji, które mają być obsługiwane.

| Wersja programu .NET Framework | Tfm      |
| ---------------------- | -------- |
| .NET Framework 2.0     | `net20`  |
| .NET Framework 3.0     | `net30`  |
| Program .NET Framework 3,5     | `net35`  |
| .NET Framework 4.0     | `net40`  |
| .NET Framework 4.5     | `net45`  |
| .NET Framework 4.5.1   | `net451` |
| .NET Framework 4.5.2   | `net452` |
| Program .NET Framework 4.6     | `net46`  |
| .NET Framework 4.6.1   | `net461` |
| .NET Framework 4.6.2   | `net462` |
| .NET Framework 4.7     | `net47`  |
|  .NET Framework 4.8     | `net48`  |

Następnie wstaw ten TFM do `TargetFramework` sekcji pliku projektu. Na przykład oto jak można napisać bibliotekę, która jest przeznaczona dla .NET Framework 4.0:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net40</TargetFramework>
  </PropertyGroup>
</Project>
```

I to wszystko. Mimo że jest to skompilowane tylko dla .NET Framework 4, można użyć biblioteki w nowszych wersjach .NET Framework.

## <a name="how-to-multitarget"></a>Jak wielocelowe

> [!NOTE]
> W poniższych instrukcjach przyjęto założenie, że na komputerze jest zainstalowana platforma .NET Framework. Zapoznaj się z sekcją [Wymagania wstępne,](#prerequisites) aby dowiedzieć się, z których zależności należy zainstalować i skąd je pobrać.

Może być konieczne kierowanie starszych wersji programu .NET Framework, gdy projekt obsługuje zarówno .NET Framework, jak i .NET Core. W tym scenariuszu, jeśli chcesz użyć nowszych interfejsów API `#if` i konstrukcji języka dla nowszych obiektów docelowych, użyj dyrektyw w kodzie. Może być również konieczne dodanie różnych pakietów i zależności dla każdej platformy, na którą kierujesz reklamy, aby uwzględnić różne interfejsy API potrzebne dla każdego przypadku.

Załóżmy na przykład, że masz bibliotekę, która wykonuje operacje sieciowe za pośrednictwem protokołu HTTP. W przypadku standardu .NET i wersji .NET Framework w `HttpClient` wersji `System.Net.Http` 4.5 lub nowszej można użyć tej klasy z obszaru nazw. Jednak wcześniejsze wersje .NET Framework nie mają `HttpClient` klasy, więc można `WebClient` użyć `System.Net` klasy z obszaru nazw dla tych zamiast.

Plik projektu może wyglądać tak:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netstandard1.4;net40;net45</TargetFrameworks>
  </PropertyGroup>

  <!-- Need to conditionally bring in references for the .NET Framework 4.0 target -->
  <ItemGroup Condition="'$(TargetFramework)' == 'net40'">
    <Reference Include="System.Net" />
  </ItemGroup>

  <!-- Need to conditionally bring in references for the .NET Framework 4.5 target -->
  <ItemGroup Condition="'$(TargetFramework)' == 'net45'">
    <Reference Include="System.Net.Http" />
    <Reference Include="System.Threading.Tasks" />
  </ItemGroup>
</Project>
```

Tutaj zauważasz trzy główne zmiany:

1. Węzeł `TargetFramework` został zastąpiony przez `TargetFrameworks`, a trzy TFM są wyrażone wewnątrz.
1. Istnieje `<ItemGroup>` węzeł dla `net40` obiektu docelowego ściągając w jednym .NET Framework odwołania.
1. Istnieje `<ItemGroup>` węzeł dla `net45` obiektu docelowego ciągnąc w dwóch odwołaniach .NET Framework.

System kompilacji jest świadomy następujących symboli `#if` preprocesora używanych w dyrektywach:

[!INCLUDE [Preprocessor symbols](../../../includes/preprocessor-symbols.md)]

Oto przykład korzystania z kompilacji warunkowej na miejsce docelowe:

```csharp
using System;
using System.Text.RegularExpressions;
#if NET40
// This only compiles for the .NET Framework 4 targets
using System.Net;
#else
 // This compiles for all other targets
using System.Net.Http;
using System.Threading.Tasks;
#endif

namespace MultitargetLib
{
    public class Library
    {
#if NET40
        private readonly WebClient _client = new WebClient();
        private readonly object _locker = new object();
#else
        private readonly HttpClient _client = new HttpClient();
#endif

#if NET40
        // .NET Framework 4.0 does not have async/await
        public string GetDotNetCount()
        {
            string url = "https://www.dotnetfoundation.org/";

            var uri = new Uri(url);

            string result = "";

            // Lock here to provide thread-safety.
            lock(_locker)
            {
                result = _client.DownloadString(uri);
            }

            int dotNetCount = Regex.Matches(result, ".NET").Count;

            return $"Dotnet Foundation mentions .NET {dotNetCount} times!";
        }
#else
        // .NET 4.5+ can use async/await!
        public async Task<string> GetDotNetCountAsync()
        {
            string url = "https://www.dotnetfoundation.org/";

            // HttpClient is thread-safe, so no need to explicitly lock here
            var result = await _client.GetStringAsync(url);

            int dotNetCount = Regex.Matches(result, ".NET").Count;

            return $"dotnetfoundation.org mentions .NET {dotNetCount} times in its HTML!";
        }
#endif
    }
}
```

Jeśli stworzysz `dotnet build`ten projekt z , zauważysz trzy katalogi w folderze: `bin/`

```
net40/
net45/
netstandard1.4/
```

Każdy z nich `.dll` zawiera pliki dla każdego obiektu docelowego.

## <a name="how-to-test-libraries-on-net-core"></a>Jak testować biblioteki w usiułm.NET Core

Ważne jest, aby móc testować na różnych platformach. Można użyć [xUnit](https://xunit.github.io/) lub MSTest po wyjęciu z pudełka. Oba są idealnie odpowiednie do testowania jednostkowego biblioteki na .NET Core. Sposób konfigurowania rozwiązania w projektach testowych zależy od [struktury rozwiązania.](#structuring-a-solution) W poniższym przykładzie przyjęto założenie, że katalogi testowe i źródłowe są aktywne w tym samym katalogu najwyższego poziomu.

> [!NOTE]
> Używa niektórych poleceń [cli programu .NET Core.](../tools/index.md) Zobacz [dotnet nowy](../tools/dotnet-new.md) i [dotnet sln](../tools/dotnet-sln.md) aby uzyskać więcej informacji.

1. Skonfiguruj rozwiązanie. Można to zrobić za pomocą następujących poleceń:

   ```dotnetcli
   mkdir SolutionWithSrcAndTest
   cd SolutionWithSrcAndTest
   dotnet new sln
   dotnet new classlib -o MyProject
   dotnet new xunit -o MyProject.Test
   dotnet sln add MyProject/MyProject.csproj
   dotnet sln add MyProject.Test/MyProject.Test.csproj
   ```

   Spowoduje to utworzenie projektów i połączenie ich w rozwiązaniu. Twój katalog `SolutionWithSrcAndTest` powinien wyglądać tak:

   ```
   /SolutionWithSrcAndTest
   |__SolutionWithSrcAndTest.sln
   |__MyProject/
   |__MyProject.Test/
   ```

1. Przejdź do katalogu projektu testowego i `MyProject.Test` dodaj `MyProject`odwołanie do z .

   ```dotnetcli
   cd MyProject.Test
   dotnet add reference ../MyProject/MyProject.csproj
   ```

1. Przywracanie pakietów i tworzenie projektów:

   ```dotnetcli
   dotnet restore
   dotnet build
   ```

   [!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

1. Sprawdź, czy xUnit działa, wykonując `dotnet test` polecenie. Jeśli wybrano użycie narzędzia MSTest, zamiast tego powinien zostać uruchomiony program uruchamiany konsoli MSTest.

I to wszystko. Teraz można przetestować bibliotekę na wszystkich platformach za pomocą narzędzi wiersza polecenia. Aby kontynuować testowanie teraz, gdy wszystko jest skonfigurowane, testowanie biblioteki jest bardzo proste:

1. Wprowadzanie zmian w bibliotece.
1. Uruchom testy z wiersza polecenia, w `dotnet test` katalogu testowym, za pomocą polecenia.

Kod zostanie automatycznie przebudowany podczas wywoływania `dotnet test` polecenia.

## <a name="how-to-use-multiple-projects"></a>Jak korzystać z wielu projektów

Częstą potrzebą większych bibliotek jest umieszczenie funkcji w różnych projektach.

Wyobraź sobie, że chcesz utworzyć bibliotekę, która może być zużywana w idiomatycznych językach C# i F#. Oznaczałoby to, że konsumenci biblioteki zużywają go w sposób, który jest naturalny dla Języka C# lub F#. Na przykład w języku C# można użyć biblioteki w ten sposób:

```csharp
using AwesomeLibrary.CSharp;

public Task DoThings(Data data)
{
    var convertResult = await AwesomeLibrary.ConvertAsync(data);
    var result = AwesomeLibrary.Process(convertResult);
    // do something with result
}
```

W F#, może to wyglądać tak:

```fsharp
open AwesomeLibrary.FSharp

let doWork data = async {
    let! result = AwesomeLibrary.AsyncConvert data // Uses an F# async function rather than C# async method
    // do something with result
}
```

Scenariusze zużycia, takie jak to oznacza, że interfejsy API, do których uzyskuje się dostęp, muszą mieć inną strukturę dla języka C# i F#.  Wspólne podejście do osiągnięcia tego jest uwzględnienie wszystkich logiki biblioteki do projektu podstawowego, z C# i F# projektów definiujących warstwy interfejsu API, które wywołują do tego projektu podstawowego.  W pozostałej części sekcji będą używane następujące nazwy:

* **AwesomeLibrary.Core** - podstawowy projekt, który zawiera całą logikę dla biblioteki
* **AwesomeLibrary.CSharp** — projekt z publicznymi interfejsami API przeznaczony do użycia w c #
* **AwesomeLibrary.FSharp** — projekt z publicznymi interfejsami API przeznaczony do użycia w F #

W terminalu można uruchomić następujące polecenia, aby utworzyć tę samą strukturę, co ten przewodnik:

```dotnetcli
mkdir AwesomeLibrary && cd AwesomeLibrary
dotnet new sln
mkdir AwesomeLibrary.Core && cd AwesomeLibrary.Core && dotnet new classlib
cd ..
mkdir AwesomeLibrary.CSharp && cd AwesomeLibrary.CSharp && dotnet new classlib
cd ..
mkdir AwesomeLibrary.FSharp && cd AwesomeLibrary.FSharp && dotnet new classlib -lang "F#"
cd ..
dotnet sln add AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
dotnet sln add AwesomeLibrary.CSharp/AwesomeLibrary.CSharp.csproj
dotnet sln add AwesomeLibrary.FSharp/AwesomeLibrary.FSharp.fsproj
```

Spowoduje to dodanie trzech powyższych projektów i pliku rozwiązania, który łączy je ze sobą. Tworzenie pliku rozwiązania i łączenie projektów pozwoli przywrócić i zbudować projekty z najwyższego poziomu.

### <a name="project-to-project-referencing"></a>Odwoływanie się do projektu

Najlepszym sposobem odwoływania się do projektu jest użycie cli .NET Core, aby dodać odwołanie do projektu. Z **awesomelibrary.CSharp** i **AwesomeLibrary.FSharp** katalogów projektu, można uruchomić następujące polecenie:

```dotnetcli
dotnet add reference ../AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
```

Pliki projektu dla **awesomelibrary.CSharp** i **AwesomeLibrary.FSharp** będzie teraz odwoływać **AwesomeLibrary.Core** jako `ProjectReference` miejsce docelowe.  Można to sprawdzić, sprawdzając pliki projektu i wyświetlając w nich następujące informacje:

```xml
<ItemGroup>
  <ProjectReference Include="..\AwesomeLibrary.Core\AwesomeLibrary.Core.csproj" />
</ItemGroup>
```

Tę sekcję można dodać do każdego pliku projektu ręcznie, jeśli nie chcesz używać.NET Core CLI.

### <a name="structuring-a-solution"></a>Strukturyzacja rozwiązania

Innym ważnym aspektem rozwiązań wieloprojektowych jest stworzenie dobrej ogólnej struktury projektu. Możesz zorganizować kod, jak chcesz, i tak długo, jak `dotnet sln add`połączyć każdy projekt do `dotnet restore` `dotnet build` pliku rozwiązania z , będzie można uruchomić i na poziomie rozwiązania.
