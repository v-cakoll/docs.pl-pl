---
title: Tworzenie bibliotek za pomocą narzędzi międzyplatformowych
description: Dowiedz się, jak tworzyć biblioteki dla platformy .NET przy użyciu narzędzi interfejsu wiersza polecenia platformy .NET Core.
author: cartermp
ms.author: mairaw
ms.date: 05/01/2017
ms.openlocfilehash: a6db7a15c484122600afd54814d19ea11bd1abc1
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2018
ms.locfileid: "43256199"
---
# <a name="developing-libraries-with-cross-platform-tools"></a>Tworzenie bibliotek za pomocą narzędzi międzyplatformowych

W tym artykule opisano sposób pisania biblioteki dla platformy .NET przy użyciu narzędzi interfejsu wiersza polecenia dla wielu platform. Interfejs wiersza polecenia zawiera interfejs wydajne i niskiego poziomu, który współdziała dowolnego obsługiwanego systemu operacyjnego. Możesz nadal tworzyć biblioteki za pomocą programu Visual Studio, i jeśli jest preferowany środowisko [można znaleźć w podręczniku programu Visual Studio](libraries-with-vs.md).

## <a name="prerequisites"></a>Wymagania wstępne

Potrzebujesz [zestawu .NET Core SDK i interfejsu wiersza polecenia](https://www.microsoft.com/net/core) zainstalowana na tym komputerze.

W przypadku części tego dokumentu zajmowanie się wersje programu .NET Framework, należy [.NET Framework](http://getdotnet.azurewebsites.net/) zainstalowane na komputerze Windows.

Ponadto, jeśli chcesz obsługiwać starsze cele .NET Framework, należy zainstalować pakiety przeznaczone dla deweloperów w przypadku starszych wersji framework z [strony platformy docelowej .NET](http://getdotnet.azurewebsites.net/target-dotnet-platforms.html). Zapoznaj się z tej tabeli:

| Wersja programu .NET Framework | Co do pobrania                                       |
| ---------------------- | ------------------------------------------------------ |
| 4.6.1                  | .NET framework 4.6.1 Targeting Pack                    |
| 4.6                    | .NET framework 4.6 Targeting Pack                      |
| 4.5.2                  | .NET framework 4.5.2 Developer Pack                    |
| 4.5.1                  | .NET framework 4.5.1 Developer Pack                    |
| 4.5                    | Zestaw Windows Software Development Kit dla systemu Windows 8         |
| 4.0                    | Windows SDK for Windows 7 i platformy .NET Framework 4         |
| w wersji 2.0, 3.0 i 3.5      | Środowisko uruchomieniowe platformy .NET framework 3.5 z dodatkiem SP1 (lub wersji systemu Windows 8 i nowsze) |

## <a name="how-to-target-the-net-standard"></a>Jak do obiektu docelowego .NET Standard

Jeśli nie znasz jeszcze przy użyciu platformy .NET Standard, zapoznaj się [.NET Standard](../../standard/net-standard.md) Aby dowiedzieć się więcej.

W tym artykule raporcie uwzględniona jest tabela mapujący wersji .NET Standard do różnych implementacji:

[!INCLUDE [net-standard-table](~/includes/net-standard-table.md)]

Oto, co oznacza tej tabeli na potrzeby tworzenia biblioteki:

Wersja programu .NET Standard możesz wybrać będzie zależność między dostęp do najnowszych interfejsów API i pozwalają objąć więcej implementacje platformy .NET i .NET Standard wersji. Kontrolowanie zakresu targetable platformy i wersje, wprost wybierając wersję `netstandardX.X` (gdzie `X.X` jest numer wersji) i dodanie go do pliku projektu (`.csproj` lub `.fsproj`).

Masz trzy podstawowe opcje podczas przeznaczonych dla platformy .NET Standard, w zależności od potrzeb.

1. Można użyć domyślnej wersji dostarczonych przez Szablony — .NET Standard `netstandard1.4` — które zapewnia dostęp do większości interfejsów API .NET Standard przy zachowaniu zgodny z platformy uniwersalnej systemu Windows, platformy .NET Framework 4.6.1 i nadchodzących .NET Standard 2.0.

    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <TargetFramework>netstandard1.4</TargetFramework>
      </PropertyGroup>
    </Project>
    ```

2. Można użyć mniejsze lub większe wersji programu .NET Standard, zmieniając wartość w `TargetFramework` węzła pliku projektu.
    
    Wersje .NET standard są zgodne z poprzednimi wersjami. Oznacza to, że `netstandard1.0` systemem bibliotek `netstandard1.1` platform lub nowszy. Jednak nie ma żadnych zgodność z nowszymi wersjami — niższy platformy .NET Standard nie może odwoływać się tymi wyższy. Oznacza to, że `netstandard1.0` bibliotek nie odniesienia bibliotek przeznaczonych dla `netstandard1.1` lub nowszej. Wybierz pozycję standardowa wersja, która zawiera odpowiedniej kombinacji obsługę interfejsów API i platform do własnych potrzeb. Firma Microsoft zaleca `netstandard1.4` teraz.
    
3. Jeśli chcesz przeanalizować wersje programu .NET Framework 4.0 lub starszej, lub chcesz użyć interfejsu API, które są dostępne w .NET Framework, ale nie w programie .NET Standard (na przykład `System.Drawing`), powinien przeczytać poniższe sekcje i Dowiedz się, jak multitarget.

## <a name="how-to-target-the-net-framework"></a>Instrukcje dla środowiska .NET Framework

> [!NOTE]
> W instrukcjach przyjęto założenie, że masz zainstalowany na komputerze w programie .NET Framework. Zapoznaj się [wymagania wstępne](#prerequisites) uzyskać zależności zainstalowane.

Należy pamiętać, że niektóre wersje programu .NET Framework, w tym miejscu użyć nie są już objęte wsparciem. Zapoznaj się [.NET Framework pomocy technicznej cyklu życia zasad — często zadawane pytania](https://support.microsoft.com/gp/framework_faq/en-us) o wersjach nieobsługiwany.

Jeśli chcesz osiągnąć maksymalną liczbę deweloperów i projektów, należy użyć programu .NET Framework 4.0 jako docelowej linii bazowej. Pod kątem programu .NET Framework, należy rozpocząć od użycia poprawne Target Framework krótkiej nazwy (elementu TFM) odpowiadający wersji .NET Framework, którą chcesz obsługiwać.

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

Następnie Wstaw tego elementu TFM do `TargetFramework` sekcji w pliku projektu. Na przykład Oto jak możesz napisać bibliotekę, która jest przeznaczony dla .NET Framework 4.0:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net40</TargetFramework>
  </PropertyGroup>
</Project>
```

I to wszystko! Mimo że to skompilowany tylko dla programu .NET Framework 4, przy użyciu biblioteki na nowsze wersje programu .NET Framework.

## <a name="how-to-multitarget"></a>Jak Multitarget

> [!NOTE]
> Zgodnie z poniższymi instrukcjami przyjęto założenie, że masz zainstalowany na komputerze w programie .NET Framework. Zapoznaj się [wymagania wstępne](#prerequisites) sekcji, aby dowiedzieć się, które zależności, należy zainstalować i gdzie można je pobrać z.

Może być konieczne docelowe starsze wersje programu .NET Framework, gdy projekt obsługuje .NET Framework i .NET Core. W tym scenariuszu, jeśli chcesz użyć nowszych interfejsów API i konstrukcji językowych dla nowszej elementów docelowych, użyj `#if` dyrektywy w kodzie. Należy także dodawać różne pakiety i zależności dla wszystkich platform, które zostaną objęci do uwzględnienia różnych interfejsów API potrzebne w każdym przypadku.

Załóżmy na przykład, że masz bibliotekę, która wykonuje operacje sieciowe za pośrednictwem protokołu HTTP. .NET Standard i .NET Framework w wersji 4.5 lub nowszej, można użyć `HttpClient` klasy z `System.Net.Http` przestrzeni nazw. Wcześniejszych wersjach programu .NET Framework nie mają jednak `HttpClient` klasy, dzięki czemu można używać `WebClient` klasy z `System.Net` przestrzeni nazw dla osób, zamiast tego.

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

Można zauważyć trzy duże zmiany w tym miejscu:

1. `TargetFramework` Węzeł został zastąpiony przez `TargetFrameworks`, i trzech krótkich nazw są wyrażone w.
1. Brak `<ItemGroup>` węzeł `net40 ` docelowej ściąganie w jedno odwołanie do .NET Framework.
1. Brak `<ItemGroup>` węzeł `net45` docelowej ściąganie spowoduje dwa odwołania do .NET Framework.

System kompilacji ma informacje o następujących symboli preprocesora używane w `#if` dyrektywy:

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

Poniżej przedstawiono przykładowe zastosowanie wprowadzania kompilacji warunkowej dla elementu docelowego:

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

Każdy z nich zawiera `.dll` plików dla każdego obiektu docelowego.

## <a name="how-to-test-libraries-on-net-core"></a>Jak przetestować bibliotek na platformie .NET Core

Jest ważne można było przetestować na wielu platformach. Można użyć dowolnego [xUnit](http://xunit.github.io/) lub MSTest gotowe. Zarówno nadają się idealnie do biblioteki, na platformie .NET Core testów jednostkowych. Jak skonfigurować rozwiązanie z projektami testowymi będzie zależeć od [struktury rozwiązania](#structuring-a-solution). W poniższym przykładzie założono, że katalogi testu i źródła na żywo w tym samym katalogu najwyższego poziomu.

> [!NOTE]
> Ta metoda korzysta z niektórych [poleceń interfejsu wiersza polecenia platformy .NET Core](../tools/index.md). Zobacz [dotnet nowe](../tools/dotnet-new.md) i [dotnet sln](../tools/dotnet-sln.md) Aby uzyskać więcej informacji.

1. Konfigurowanie rozwiązania programu. Można to zrobić za pomocą następujących poleceń:

   ```bash
   mkdir SolutionWithSrcAndTest
   cd SolutionWithSrcAndTest
   dotnet new sln
   dotnet new classlib -o MyProject
   dotnet new xunit -o MyProject.Test
   dotnet sln add MyProject/MyProject.csproj
   dotnet sln add MyProject.Test/MyProject.Test.csproj
   ```

   Spowoduje to utworzenie projektów i połączyć je w ramach rozwiązania. W katalogu `SolutionWithSrcAndTest` powinien wyglądać następująco:

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

1. Przywróć pakiety i kompilacji projektów:

   ```bash
   dotnet restore
   dotnet build
   ```

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

1. Sprawdź, że xUnit działa, wykonując `dotnet test` polecenia. Jeśli została wybrana opcja używania MSTest, modułu uruchamiającego MSTest konsoli należy uruchomić zamiast tego.
    
I to wszystko! Teraz możesz przetestować biblioteki, na wszystkich platformach przy użyciu narzędzia wiersza polecenia. Aby kontynuować testowanie Skoro masz wszystko, czego należy skonfigurować, testowanie biblioteki jest bardzo prosta:

1. Wprowadź zmiany w bibliotece.
1. Uruchom testy z wiersza polecenia, w katalogu testu za pomocą `dotnet test` polecenia.

Twój kod będzie automatycznie odbudować po wywołaniu `dotnet test` polecenia.

## <a name="how-to-use-multiple-projects"></a>Jak używać wielu projektów

Potrzebują większych biblioteki jest umieszczenie funkcji w różnych projektach.

Załóżmy, że chcieliby Tworzenie biblioteki, w którym można korzystać w idiomatyczną C# i F #. Oznacza to, że konsumenci biblioteki korzystania z nich w sposób naturalny C# lub F #. Na przykład w języku C# może używać biblioteki następująco:

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

Scenariusze użycia, np. oznacza to, że interfejsy API, do którego uzyskiwany jest dostęp, trzeba mieć różną strukturę języka C# i F #.  Typowym podejściem do realizacji tego zadania jest wziąć pod uwagę całą logikę biblioteki do projektu core, w projektach C# i F # Definiowanie warstwy interfejsu API, odwołujące się do tego projektu core.  Pozostała część sekcji użyje następujących nazw:

* **AwesomeLibrary.Core** -projekt core, która zawiera całą logikę dla biblioteki
* **AwesomeLibrary.CSharp** -projektu przy użyciu publicznych interfejsów API przeznaczonych do użycia w języku C#
* **AwesomeLibrary.FSharp** -projektu przy użyciu publicznych interfejsów API przeznaczonych do użycia w języku F #

W terminalu, aby utworzyć tę samą strukturę jako tego przewodnika, można uruchomić następujące polecenia:

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

Spowoduje to dodanie trzy projekty powyżej i plik rozwiązania, które łączy je razem. Utworzenie pliku rozwiązania i połączenie projekty będzie można przywrócić i kompilacji projektów z najwyższego poziomu.

### <a name="project-to-project-referencing"></a>Odwołanie do projektu do projektu

Jest najlepszym sposobem, aby odwoływać się do projektu Dodaj odwołanie do projektu przy użyciu interfejsu wiersza polecenia platformy .NET Core. Z **AwesomeLibrary.CSharp** i **AwesomeLibrary.FSharp** katalogi projektu, można uruchomić następujące polecenie:

```console
$ dotnet add reference ../AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
```

Pliki projektu dla obu **AwesomeLibrary.CSharp** i **AwesomeLibrary.FSharp** będzie teraz odwołanie **AwesomeLibrary.Core** jako `ProjectReference` docelowej.  Można to sprawdzić, przeprowadzanie inspekcji plików projektu i sprawdzając następujące informacje w nich:

```xml
<ItemGroup>
  <ProjectReference Include="..\AwesomeLibrary.Core\AwesomeLibrary.Core.csproj" />
</ItemGroup>
```

Możesz dodać w tej sekcji do każdego pliku projektu ręcznie, jeśli nie chcesz używać interfejsu wiersza polecenia platformy .NET Core.

### <a name="structuring-a-solution"></a>Tworzenie struktury rozwiązania

Innym ważnym aspektem rozwiązań dotyczących wielu projektów jest ustanowienie dobre ogólna struktura projektu. Można organizować kod, możesz dowolnie i tak długo, jak połączyć każdego projektu do pliku rozwiązania przy użyciu `dotnet sln add`, będzie można uruchomić `dotnet restore` i `dotnet build` na poziomie rozwiązania.
