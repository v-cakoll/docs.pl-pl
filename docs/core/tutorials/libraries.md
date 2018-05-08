---
title: Tworzenie bibliotek z wielu narzędzi platformy
description: Dowiedz się, jak utworzyć biblioteki dla platformy .NET przy użyciu narzędzi interfejsu wiersza polecenia platformy .NET Core.
author: cartermp
ms.author: mairaw
ms.date: 05/01/2017
ms.openlocfilehash: a6db7a15c484122600afd54814d19ea11bd1abc1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="developing-libraries-with-cross-platform-tools"></a>Tworzenie bibliotek z wielu narzędzi platformy

W tym artykule omówiono sposób zapisania biblioteki dla platformy .NET przy użyciu narzędzi interfejsu wiersza polecenia i platform. Interfejsu wiersza polecenia zapewnia wydajne i niskiego poziomu, który działa z dowolnym obsługiwany system operacyjny. Można nadal tworzyć bibliotek w programie Visual Studio i jeśli jest to preferowany środowiska [można znaleźć w podręczniku programu Visual Studio](libraries-with-vs.md).

## <a name="prerequisites"></a>Wymagania wstępne

Należy [.NET Core SDK i interfejsu wiersza polecenia](https://www.microsoft.com/net/core) zainstalowana na tym komputerze.

Dla sekcji tego dokumentu dotyczącej wersji systemu .NET Framework należy [.NET Framework](http://getdotnet.azurewebsites.net/) zainstalowany na komputerze z systemem Windows.

Ponadto, jeśli chcesz obsługiwać starszych docelowych .NET Framework należy zainstalować pakiety przeznaczonych dla deweloperów dla starszych wersji framework z [strony platformy docelowej .NET](http://getdotnet.azurewebsites.net/target-dotnet-platforms.html). Można skorzystać z tej tabeli:

| Wersja programu .NET Framework | Co do pobrania                                       |
| ---------------------- | ------------------------------------------------------ |
| 4.6.1                  | .NET framework 4.6.1 Targeting Pack                    |
| 4.6                    | .NET framework 4.6 Targeting Pack                      |
| 4.5.2                  | .NET framework 4.5.2 Developer Pack                    |
| 4.5.1                  | .NET framework 4.5.1 Developer Pack                    |
| 4.5                    | Zestaw Windows Software Development Kit dla systemu Windows 8         |
| 4.0                    | Zestaw Windows SDK dla systemu Windows 7 i .NET Framework 4         |
| 2.0, 3.0 i 3.5      | Środowisko uruchomieniowe platformy .NET framework 3.5 z dodatkiem SP1 (lub wersji systemu Windows 8 +) |

## <a name="how-to-target-the-net-standard"></a>Jak docelowy .NET Standard

Jeśli nie znasz jeszcze przy użyciu platformy .NET Standard, zapoznaj się [.NET Standard](../../standard/net-standard.md) Aby dowiedzieć się więcej.

W tym artykule nie istnieje tabela, który mapuje wersje .NET Standard na różnych implementacji:

[!INCLUDE [net-standard-table](~/includes/net-standard-table.md)]

Oto tej tabeli oznacza na potrzeby tworzenia biblioteki:

Wersja programu .NET Standard możesz wybrać będzie zależności między dostęp do najnowszych interfejsów API oraz możliwość docelowego więcej implementacje .NET oraz wersji platformy .NET Standard. Kontrolowanie zakresu targetable platform i wersje wybierając wersję `netstandardX.X` (gdzie `X.X` jest numer wersji) i dodanie go do pliku projektu (`.csproj` lub `.fsproj`).

Dostępne są trzy opcje podstawowego przeznaczonych dla platformy .NET Standard, w zależności od potrzeb.

1. Korzystając z domyślną wersją .NET Standard dostarczonych przez szablony — `netstandard1.4` — która zapewnia dostęp do większości interfejsów API platformy .NET Standard przy zachowaniu zgodny z platformy uniwersalnej systemu Windows, .NET Framework 4.6.1 i nadchodzącego .NET Standard w wersji 2.0.

    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <TargetFramework>netstandard1.4</TargetFramework>
      </PropertyGroup>
    </Project>
    ```

2. Można użyć niższych lub nowszej wersji programu .NET Standard przez zmodyfikowanie wartości w `TargetFramework` węzła pliku projektu.
    
    Wersje .NET standard są zgodne z poprzednimi wersjami. Oznacza to, że `netstandard1.0` biblioteki Uruchom na `netstandard1.1` platform i wyższych. Jednak nie istnieje żadne zgodność z nowszymi wersjami — niższe platformy .NET Standard nie może odwoływać się wyższym z nich. Oznacza to, że `netstandard1.0` bibliotek nie odwołanie bibliotek przeznaczonych `netstandard1.1` lub nowszej. Wybierz wersję Standard z odpowiedniej kombinacji obsługę interfejsów API i platforma do potrzeb. Firma Microsoft zaleca `netstandard1.4` teraz.
    
3. Jeśli chcesz korzystać z wersji .NET Framework 4.0 lub poniżej, lub chcesz użyć interfejsu API, które są dostępne w programie .NET Framework, ale nie w .NET Standard (na przykład `System.Drawing`), powinien przeczytać poniższe sekcje i Dowiedz się, jak multitarget.

## <a name="how-to-target-the-net-framework"></a>Jak docelowej platformy .NET Framework

> [!NOTE]
> W instrukcjach przyjęto założenie, że ma programu .NET Framework na komputerze jest zainstalowany. Zapoznaj się [wymagania wstępne](#prerequisites) uzyskać zależności zainstalowane.

Należy pamiętać, że niektóre wersje programu .NET Framework, używane w tym miejscu nie są już w obsłudze. Zapoznaj się [.NET Framework wsparcia technicznego](https://support.microsoft.com/gp/framework_faq/en-us) o nieobsługiwanej wersji.

Aby osiągnąć maksymalną liczbę deweloperów i projekty, należy użyć programu .NET Framework 4.0 jako urządzenie docelowe linii bazowej. Docelowy .NET Framework, należy rozpocząć przy użyciu poprawny docelowy Framework Moniker (TFM) umożliwiająca wersja architektury .NET Framework, które chcesz obsługiwać.

```
.NET Framework 2.0   --> net20
.NET Framework 3.0   --> net30
.NET Framework 3.5   --> net35
.NET Framework 4.0   --> net40
.NET Framework 4.5   --> net45
.NET Framework 4.5.1 --> net451
.NET Framework 4.5.2 --> net452
.NET Framework 4.6   --> net46
.NET Framework 4.6.1 --> net461
.NET Framework 4.6.2 --> net462
.NET Framework 4.7   --> net47
```

Następnie wstaw ten TFM do `TargetFramework` sekcji w pliku projektu. Na przykład poniżej przedstawiono sposób piszesz bibliotekę, która jest przeznaczony dla programu .NET Framework 4.0:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net40</TargetFramework>
  </PropertyGroup>
</Project>
```

I to już wszystko! Mimo że to skompilowany tylko dla programu .NET Framework 4, biblioteki można używać w nowszej wersji programu .NET Framework.

## <a name="how-to-multitarget"></a>Jak Multitarget

> [!NOTE]
> Poniższe instrukcje założono, że na komputerze jest zainstalowany w programie .NET Framework. Zapoznaj się [wymagania wstępne](#prerequisites) sekcji, aby dowiedzieć się zależności, które należy zainstalować i skąd pobrać je z.

Konieczne może być celem starsze wersje programu .NET Framework, gdy projekt obsługuje program .NET Framework i .NET Core. W tym scenariuszu, jeśli chcesz użyć nowszej interfejsów API i konstrukcji języka dla nowszej celów, użyj `#if` dyrektywy w kodzie. Należy również dodać różnych pakietów i zależności dla poszczególnych platform docelowych do uwzględnienia różnych interfejsów API potrzebne w każdym przypadku.

Załóżmy na przykład, że biblioteka, która wykonuje operacje sieciowe za pośrednictwem protokołu HTTP. W przypadku standardowych .NET i .NET Framework w wersji 4.5 lub nowszej, można użyć `HttpClient` klasę z `System.Net.Http` przestrzeni nazw. Jednak nie ma wcześniejszych wersji programu .NET Framework `HttpClient` klasy, aby można było używać `WebClient` klasę z `System.Net` przestrzeń nazw dla tych zamiast tego.

Plik projektu może wyglądać następująco:

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

Można zauważyć trzy istotne zmiany w tym miejscu:

1. `TargetFramework` Węzeł został zastąpiony przez `TargetFrameworks`, i trzy TFMs są wyrażane w.
1. Brak `<ItemGroup>` węzeł `net40 ` docelowej ściąganie w jedno odwołanie .NET Framework.
1. Brak `<ItemGroup>` węzeł `net45` docelowej ściąganie w dwóch odwołań platformy .NET.

System kompilacji jest pamiętać o następujących symboli preprocesora używane w `#if` dyrektywy:

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

Oto przykład korzystające z kompilacji warunkowej na docelowym:

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
            string url = "http://www.dotnetfoundation.org/";

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
            string url = "http://www.dotnetfoundation.org/";

            // HttpClient is thread-safe, so no need to explicitly lock here
            var result = await _client.GetStringAsync(url);

            int dotNetCount = Regex.Matches(result, ".NET").Count;

            return $"dotnetfoundation.org mentions .NET {dotNetCount} times in its HTML!";
        }
#endif
    }
}
```

W przypadku tworzenia tego projektu z `dotnet build`, można zauważyć trzy katalogi w ramach `bin/` folderu:

```
net40/
net45/
netstandard1.4/
```

Każdy z tych zawierać `.dll` plików dla każdego obiektu docelowego.

## <a name="how-to-test-libraries-on-net-core"></a>Jak przetestować bibliotek .NET Core

Jest ważne można było przetestować na różnych platformach. Możesz użyć dowolnej [xUnit](http://xunit.github.io/) lub MSTest poza pole. Oba są doskonale nadające się do biblioteki programu .NET Core testowania jednostek. Sposób konfigurowania rozwiązania z projekty testowe będzie zależeć od [struktury rozwiązania](#structuring-a-solution). W poniższym przykładzie założono, że katalogi testu oraz źródła na żywo w tym samym katalogu najwyższego poziomu.

> [!NOTE]
> Niektóre używa [polecenia interfejsu wiersza polecenia platformy .NET Core](../tools/index.md). Zobacz [dotnet nowe](../tools/dotnet-new.md) i [dotnet sln](../tools/dotnet-sln.md) Aby uzyskać więcej informacji.

1. Konfigurowanie rozwiązania. Możesz to zrobić za pomocą następujących poleceń:

   ```bash
   mkdir SolutionWithSrcAndTest
   cd SolutionWithSrcAndTest
   dotnet new sln
   dotnet new classlib -o MyProject
   dotnet new xunit -o MyProject.Test
   dotnet sln add MyProject/MyProject.csproj
   dotnet sln add MyProject.Test/MyProject.Test.csproj
   ```

   Spowoduje to utworzenie projektów i połączyć je w rozwiązaniu. W katalogu `SolutionWithSrcAndTest` powinna wyglądać następująco:

   ```
   /SolutionWithSrcAndTest
   |__SolutionWithSrcAndTest.sln
   |__MyProject/
   |__MyProject.Test/
   ```

1. Przejdź do katalogu projektu testowego i Dodaj odwołanie do `MyProject.Test` z `MyProject`.

   ```bash
   cd MyProject.Test
   dotnet add reference ../MyProject/MyProject.csproj
   ```

1. Przywracanie pakietów i kompilacji projektów:

   ```bash
   dotnet restore
   dotnet build
   ```

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

1. Sprawdź, że xUnit działa, wykonując `dotnet test` polecenia. Jeśli chcesz użyć przełącznika MSTest konsoli MSTest modułu uruchamiającego testy należy uruchomić zamiast tego.
    
I to już wszystko! Teraz możesz przetestować biblioteki na wszystkich platformach za pomocą narzędzia wiersza polecenia. Aby kontynuować testowanie teraz, gdy masz wszystkie elementy skonfigurować, testowanie biblioteki jest bardzo prosty:

1. Wprowadzanie zmian do biblioteki.
1. Uruchom testy z wiersza polecenia w katalogu testu z `dotnet test` polecenia.

Kod zostanie automatycznie odbudować po wywołaniu `dotnet test` polecenia.

## <a name="how-to-use-multiple-projects"></a>Jak używać wielu projektów

Potrzebują większych biblioteki jest umieścić funkcji w różnych projektów.

Załóżmy, że zamierza utworzyć bibliotekę, która może być używana w idiomatyczne C# i F #. Oznacza to, że konsumenci biblioteki mogły ich używać w sposób fizyczne do języka C# lub języka F #. Na przykład w języku C# mogą używać biblioteki następująco:

```csharp
using AwesomeLibrary.CSharp;

public Task DoThings(Data data)
{
    var convertResult = await AwesomeLibrary.ConvertAsync(data);
    var result = AwesomeLibrary.Process(convertResult);
    // do something with result
}
```

W języku F # może wyglądać następująco:

```fsharp
open AwesomeLibrary.FSharp

let doWork data = async {
    let! result = AwesomeLibrary.AsyncConvert data // Uses an F# async function rather than C# async method
    // do something with result
}
```

Scenariusze użycia, takich jak ta oznaczają, że dostęp do interfejsów API muszą mieć inną strukturę języka C# i F #.  Typowym podejściem do realizacji tego zadania jest uwzględnić wszystkie logiki biblioteki projektu podstawowych, z projektami C# i F # Definiowanie warstwy interfejsu API, które wywołują projektu core.  Pozostała część sekcji użyjemy następujące nazwy:

* **AwesomeLibrary.Core** -projektu core, która zawiera całą logikę biblioteki
* **AwesomeLibrary.CSharp** -projekt o publiczne interfejsy API przeznaczonych do użycia w języku C#
* **AwesomeLibrary.FSharp** -projekt o publiczne interfejsy API przeznaczonych do użycia w języku F #

W terminalu, aby utworzyć taką samą strukturę jak w tym przewodniku można uruchomić następujące polecenia:

```console
mkdir AwesomeLibrary && cd AwesomeLibrary
dotnet new sln
mkdir AwesomeLibrary.Core && cd AwesomeLibrary.Core && dotnet new classlib
cd ..
mkdir AwesomeLibrary.CSharp && cd AwesomeLibrary.CSharp && dotnet new classlib
cd ..
mkdir AwesomeLibrary.FSharp && cd AwesomeLibrary.FSharp && dotnet new classlib -lang F#
cd ..
dotnet sln add AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
dotnet sln add AwesomeLibrary.CSharp/AwesomeLibrary.CSharp.csproj
dotnet sln add AwesomeLibrary.FSharp/AwesomeLibrary.FSharp.fsproj
```

Spowoduje to dodanie trzy projekty powyżej i plik rozwiązania, który łączy je razem. Tworzenie pliku rozwiązania, a następnie połączenie projektów pozwoli przywracania oraz tworzenie projektów z typem najwyższego poziomu.

### <a name="project-to-project-referencing"></a>Odwołanie do projektu do projektu

Najlepszym sposobem odwoływać się do projektu jest dodać odwołanie do projektu za pomocą interfejsu wiersza polecenia platformy .NET Core. Z **AwesomeLibrary.CSharp** i **AwesomeLibrary.FSharp** katalogu projektu można uruchomić następujące polecenie:

```console
$ dotnet add reference ../AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
```

Pliki projektu dla obu **AwesomeLibrary.CSharp** i **AwesomeLibrary.FSharp** będzie teraz odwołanie **AwesomeLibrary.Core** jako `ProjectReference` docelowej.  Można to sprawdzić, przeprowadzanie inspekcji plików projektu i sprawdzając następujące w nich:

```xml
<ItemGroup>
  <ProjectReference Include="..\AwesomeLibrary.Core\AwesomeLibrary.Core.csproj" />
</ItemGroup>
```

Można dodać tej sekcji do każdego pliku projektu ręcznie, jeśli nie chcesz korzystać z interfejsu wiersza polecenia platformy .NET Core.

### <a name="structuring-a-solution"></a>Tworzenie struktury rozwiązania

Innym ważnym aspektem rozwiązań dotyczących wielu projektów jest ustanowienie dobrej ogólnej struktury projektu. Kod można organizować w dowolny sposób oraz tak długo, jak połączyć każdego projektu w pliku rozwiązania z `dotnet sln add`, będzie można uruchomić `dotnet restore` i `dotnet build` na poziomie rozwiązania.
