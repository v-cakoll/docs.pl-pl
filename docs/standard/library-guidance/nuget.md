---
title: Biblioteki NuGet i .NET
description: Najlepsze zalecenia dotyczące pakowania za pomocą biblioteki NuGet dla .NET.
ms.date: 01/15/2019
ms.openlocfilehash: f1e8d39fe2988f11ce7fd351a4d6bee6d322f2b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400520"
---
# <a name="nuget"></a>NuGet

NuGet jest menedżerem pakietów dla ekosystemu .NET i jest podstawowym sposobem deweloperzy odnajdować i nabywać .NET bibliotek open source. [NuGet.org](https://www.nuget.org/), bezpłatna usługa świadczona przez firmę Microsoft do obsługi pakietów NuGet, jest głównym hostem dla publicznych pakietów NuGet, ale można publikować w niestandardowych usługach NuGet, takich jak [MyGet](https://www.myget.org/) i [Artefakty platformy Azure](https://azure.microsoft.com/services/devops/artifacts/).

![NuGet](./media/nuget/nuget-logo.png "NuGet")

## <a name="create-a-nuget-package"></a>Tworzenie pakietu NuGet

Pakiet NuGet`*.nupkg`( ) jest plikiem zip, który zawiera zestawy .NET i skojarzone metadane.

Istnieją dwa główne sposoby tworzenia pakietu NuGet. Nowszym i zalecanym sposobem jest utworzenie pakietu z projektu w stylu zestawu SDK (pliku projektu, którego zawartość zaczyna się od `<Project Sdk="Microsoft.NET.Sdk">`). Zestawy i obiekty docelowe są automatycznie dodawane do pakietu, a pozostałe metadane są dodawane do pliku MSBuild, takie jak nazwa pakietu i numer wersji. Kompilowanie za [`dotnet pack`](../../core/tools/dotnet-pack.md) pomocą polecenia `*.nupkg` wyprowadza plik zamiast zestawów.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
    <AssemblyName>Contoso.Api</AssemblyName>
    <PackageVersion>1.1.0</PackageVersion>
    <Authors>John Doe</Authors>
  </PropertyGroup>
</Project>
```

Starszy sposób tworzenia pakietu NuGet jest `*.nuspec` z `nuget.exe` pliku i narzędzia wiersza polecenia. Nuspec plik daje doskonałą kontrolę, ale należy dokładnie określić, jakie zestawy i obiekty docelowe do uwzględnienia w ostatnim pakiecie NuGet. Łatwo jest popełnić błąd lub aby ktoś zapomniał zaktualizować nuspec podczas wprowadzania zmian. Zaletą nuspec jest można go używać tworzenie pakietów NuGet dla struktur, które nie obsługują jeszcze pliku projektu w stylu SDK.

✔️ ZASTANÓW SIĘ przy użyciu pliku projektu w stylu zestawu SDK do utworzenia pakietu NuGet.

## <a name="package-dependencies"></a>Zależności pakietów

Zależności pakietów NuGet są szczegółowo omówione w [artykule Zależności.](./dependencies.md)

## <a name="important-nuget-package-metadata"></a>Ważne metadane pakietu NuGet

Pakiet NuGet obsługuje wiele [właściwości metadanych](/nuget/reference/nuspec). Poniższa tabela zawiera podstawowe metadane, które każdy pakiet na NuGet.org powinien zapewnić:

| Nazwa właściwości MSBuild              | Nazwa Nuspec              | Opis  |
| ---------------------------------- | ------------------------ | ------------ |
| `PackageId`                        | `id`                       | Identyfikator pakietu. Prefiks z identyfikatora można zarezerwować, jeśli spełnia [kryteria](/nuget/reference/id-prefix-reservation). |
| `PackageVersion`                   | `version`                  | NuGet wersji pakietu. Aby uzyskać więcej informacji, zobacz [NuGet wersji pakietu](./versioning.md#nuget-package-version).             |
| `Title`                            | `title`                    | Przyjazny dla człowieka tytuł pakietu. Domyślnie jest `PackageId`to plik .             |
| `Description`                      | `description`              | Długi opis pakietu wyświetlanego w ui.             |
| `Authors`                          | `authors`                  | Oddzielona przecinkami lista autorów pakietów, odpowiadająca nazwom profilów w nuget.org.             |
| `PackageTags`                      | `tags`                     | Lista znaczników i słów kluczowych z rozdzielaniem miejsca, które opisują pakiet. Tagi są używane podczas wyszukiwania pakietów.             |
| `PackageIconUrl`                   | `iconUrl`                  | Adres URL obrazu, który ma być używany jako ikona pakietu. Adres URL powinien być HTTPS, a obraz powinien mieć 64x64 i mieć przezroczyste tło.             |
| `PackageProjectUrl`                | `projectUrl`               | Adres URL strony głównej projektu lub repozytorium źródeł.             |
| `PackageLicenseExpression`         | `license`                  | [Identyfikator SPDX](https://spdx.org/licenses/)licencji projektu . Identyfikatormoże używać tylko licencji zatwierdzonych przez OSI i FSF. Inne licencje `PackageLicenseFile`powinny być używane . Dowiedz się więcej o [ `license` metadanych](/nuget/reference/nuspec#license). |

> [!IMPORTANT]
> Projekt bez licencji domyślnie [wyłączne prawa autorskie,](https://choosealicense.com/no-permission/)co prawnie niemożliwe dla innych osób do korzystania.

✔️ ROZWAŻ wybranie nazwy pakietu NuGet z prefiksem, który spełnia [kryteria](/nuget/reference/id-prefix-reservation)rezerwacji prefiksu NuGet.

✔️ użyj https href do ikony pakietu.

> Witryny takie jak NuGet.org uruchamiane z włączoną funkcją HTTPS i wyświetlające obraz bez protokołu HTTPS utworzą ostrzeżenie o zawartości mieszanej.

✔️ DO użyj obrazu ikony pakietu, który jest 64x64 i ma przezroczyste tło dla najlepszych wyników wyświetlania.

✔️ ROZWAŻ skonfigurowanie [łącza źródłowego,](./sourcelink.md) aby dodać metadane kontroli źródła do zestawów i pakietu NuGet.

> Łącze źródłowe `RepositoryUrl` automatycznie `RepositoryType` dodaje i metadane do pakietu NuGet. Łącze źródłowe dodaje również informacje o dokładnym kodzie źródłowym, z powodu który został utworzony pakiet. Na przykład pakiet utworzony z repozytorium Git będzie miał skrót zatwierdzania dodany jako metadane.

## <a name="pre-release-packages"></a>Pakiety w wersji wstępnej

Pakiety NuGet z sufiksem wersji są uważane za [wersja wwersji wstępnej](/nuget/create-packages/prerelease-packages). Domyślnie nuget menedżera pakietów interfejsu użytkownika pokazuje stabilne wersje, chyba że użytkownik wyraża zgodę na pakiety wersji wstępnej, dzięki czemu pakiety wersji wstępnej idealne dla ograniczonych testów użytkowników.

```xml
<PackageVersion>1.0.1-beta1</PackageVersion>
```

> [!NOTE]
> Stabilny pakiet nie może zależeć od pakietu w wersji wstępnej. Musisz albo spopuścić własny pakiet w wersji wstępnej, albo polegać na starszej stabilnej wersji.

![Zależność pakietu pre-release NuGet](./media/nuget/nuget-prerelease-package.png "Zależność pakietu pre-release NuGet")

✔️ publikują pakiet w wersji wstępnej podczas testowania, wyświetlania podglądu lub eksperymentowania.

✔️ czy opublikować stabilny pakiet, gdy jest gotowy, więc inne stabilne pakiety mogą odwoływać się do niego.

## <a name="symbol-packages"></a>Pakiety symboli

Pliki symboli (`*.pdb`) są tworzone przez kompilator .NET wraz z zestawami. Pliki symboli mapują lokalizacje wykonywania do oryginalnego kodu źródłowego, dzięki czemu można przejść przez kod źródłowy, jak jest uruchomiony przy użyciu debugera. NuGet obsługuje [generowanie oddzielnego`*.snupkg`pakietu symboli ( )](/nuget/create-packages/symbol-packages-snupkg) zawierającego pliki symboli wraz z głównym pakietem zawierającym zestawy .NET. Ideą pakietów symboli jest to, że są one hostowane na serwerze symboli i są pobierane tylko przez narzędzie, takie jak Visual Studio na żądanie.

NuGet.org hostuje własne [repozytorium serwerów symboli](/nuget/create-packages/symbol-packages-snupkg#nugetorg-symbol-server). Deweloperzy mogą używać symboli opublikowanych na `https://symbols.nuget.org/download/symbols` serwerze symboli NuGet.org, dodając do swoich [źródeł symboli w programie Visual Studio](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger).

> [!IMPORTANT]
> Serwer symboli NuGet.org obsługuje tylko nowe`*.pdb` [przenośne pliki symboli](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) ( ) utworzone przez projekty w stylu SDK.
>
> Aby podczas debugowania biblioteki .NET programiści mogli używać serwera symboli NuGet.org podczas debugowania biblioteki .NET, deweloperzy muszą mieć program Visual Studio 2017 w wersji 15.9 lub nowszej.

Alternatywą dla tworzenia pakietu symboljest osadzanie plików symboli w głównym pakiecie NuGet. Główny pakiet NuGet będzie większy, ale osadzone pliki symboli oznaczają, że deweloperzy nie muszą konfigurować serwera symboli NuGet.org. Jeśli tworzysz pakiet NuGet przy użyciu projektu w stylu zestawu SDK, `AllowedOutputExtensionsInPackageBuildOutputFolder` możesz osadzić pliki symboli, ustawiając właściwość:

```xml
<Project Sdk="Microsoft.NET.Sdk">
 <PropertyGroup>
    <!-- Include symbol files (*.pdb) in the built .nupkg -->
    <AllowedOutputExtensionsInPackageBuildOutputFolder>$(AllowedOutputExtensionsInPackageBuildOutputFolder);.pdb</AllowedOutputExtensionsInPackageBuildOutputFolder>
  </PropertyGroup>
</Project>
```

Wadą osadzania plików symboli jest zwiększenie rozmiaru pakietu o około 30% dla bibliotek .NET skompilowanych przy użyciu projektów w stylu Zestawu SDK. Jeśli rozmiar pakietu jest problemem, należy zamiast tego opublikować symbole w pakiecie symboli.

✔️ ROZWAŻ publikowanie symboli`*.snupkg`jako pakietu symboli ( ) do NuGet.org

> Pakiety symboli (`*.snupkg`) zapewniają deweloperom dobre środowisko debugowania na żądanie bez wzdęcia rozmiaru głównego pakietu i wpływu na wydajność przywracania dla tych, którzy nie zamierzają debugować pakietu NuGet.
>
> Zastrzeżeniem jest to, że użytkownicy mogą być konieczne, aby znaleźć i skonfigurować serwer symboli NuGet w ich IDE (jako jednorazowa konfiguracja), aby uzyskać pliki symboli. Program Visual Studio 2019 w wersji 16.1 dodał serwer symboli NuGet.org do listy domyślnych serwerów symboli.

>[!div class="step-by-step"]
>[Poprzedni](strong-naming.md)
>[następny](dependencies.md)
