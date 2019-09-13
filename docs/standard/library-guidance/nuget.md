---
title: Biblioteki NuGet i .NET
description: Zalecenia dotyczące najlepszych rozwiązań związanych z pakietem NuGet dla bibliotek programu .NET.
author: jamesnk
ms.author: mairaw
ms.date: 01/15/2019
ms.openlocfilehash: 9cf30fa41af2d31e416bae1d75d8880ece7dde3e
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895211"
---
# <a name="nuget"></a>NuGet

NuGet jest menedżerem pakietów dla ekosystemu .NET i jest głównym sposobem, aby deweloperzy odkrywali i nabywali biblioteki typu open-source platformy .NET. [NuGet.org](https://www.nuget.org/), bezpłatna usługa oferowana przez firmę Microsoft do hostowania pakietów NuGet, jest głównym hostem dla publicznych pakietów NuGet, ale możesz publikować w niestandardowych usługach NuGet, takich jak [MyGet](https://www.myget.org/) i [Azure Artifacts](https://azure.microsoft.com/services/devops/artifacts/).

Pakiet ![NuGet] Pakiet (./media/nuget/nuget-logo.png "NuGet")

## <a name="create-a-nuget-package"></a>Tworzenie pakietu NuGet

Pakiet NuGet (`*.nupkg`) to plik zip, który zawiera zestawy .NET i skojarzone metadane.

Istnieją dwa podstawowe sposoby tworzenia pakietu NuGet. Nowszym i zalecanym sposobem jest utworzenie pakietu z projektu w stylu zestawu SDK (plik projektu, którego zawartość zaczyna się `<Project Sdk="Microsoft.NET.Sdk">`od). Zestawy i cele są automatycznie dodawane do pakietu, a pozostałe metadane są dodawane do pliku programu MSBuild, takiego jak nazwa pakietu i numer wersji. Kompilowanie za [`dotnet pack`](../../core/tools/dotnet-pack.md) pomocą polecenia `*.nupkg` wyprowadza plik zamiast zestawów.

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

Starszym sposobem tworzenia pakietu NuGet jest `*.nuspec` plik `nuget.exe` i narzędzie wiersza polecenia. Plik NUSPEC daje doskonałą kontrolę, ale należy starannie określić, które zestawy i elementy docelowe mają być uwzględnione w końcowym pakiecie NuGet. W przypadku wprowadzania zmian łatwo jest wprowadzić błąd lub ktoś zapomni, aby zaktualizować nuspec. Zaletą nuspec jest możliwość tworzenia pakietów NuGet dla struktur, które nie obsługują jeszcze pliku projektu w stylu zestawu SDK.

**✔️ rozważyć** użycie pliku projektu w stylu zestawu SDK, aby utworzyć pakiet NuGet.

## <a name="package-dependencies"></a>Zależności pakietów

Zależności pakietów NuGet zostały szczegółowo omówione w artykule [zależności](./dependencies.md) .

## <a name="important-nuget-package-metadata"></a>Ważne metadane pakietu NuGet

Pakiet NuGet obsługuje wiele [właściwości metadanych](/nuget/reference/nuspec). Poniższa tabela zawiera podstawowe metadane, które każdy pakiet w NuGet.org powinien udostępnić:

| Nazwa właściwości programu MSBuild              | Nazwa nuspec              | Opis  |
| ---------------------------------- | ------------------------ | ------------ |
| `PackageId`                        | `id`                       | Identyfikator pakietu. Prefiks z identyfikatora może być zarezerwowany, jeśli spełnia [kryteria](/nuget/reference/id-prefix-reservation). |
| `PackageVersion`                   | `version`                  | Wersja pakietu NuGet. Aby uzyskać więcej informacji, zobacz [wersja pakietu NuGet](./versioning.md#nuget-package-version).             |
| `Title`                            | `title`                    | Przyjazny dla człowieka tytuł pakietu. Domyślnie jest to `PackageId`.             |
| `Description`                      | `description`              | Długi opis pakietu wyświetlanego w interfejsie użytkownika.             |
| `Authors`                          | `authors`                  | Rozdzielana przecinkami lista autorów pakietów pasujących do nazw profilów w nuget.org.             |
| `PackageTags`                      | `tags`                     | Rozdzielana spacjami Lista tagów i słów kluczowych, które opisują pakiet. Tagi są używane podczas wyszukiwania pakietów.             |
| `PackageIconUrl`                   | `iconUrl`                  | Adres URL obrazu, który będzie używany jako ikona pakietu. Adres URL powinien być adresem HTTPS, a obraz powinien być 64x64 i mieć przezroczyste tło.             |
| `PackageProjectUrl`                | `projectUrl`               | Adres URL dla strony głównej projektu lub repozytorium źródłowego.             |
| `PackageLicenseExpression`         | `license`                  | [Identyfikator SPDX](https://spdx.org/licenses/)licencji projektu. Tylko zatwierdzone licencje OSI i FSF mogą używać identyfikatora. Inne licencje powinny być `PackageLicenseFile`używane. Przeczytaj więcej na temat [ `license` metadanych](/nuget/reference/nuspec#license). |

> [!IMPORTANT]
> Projekt bez licencji jest domyślnie nieuprawniony do korzystania z [praw autorskich](https://choosealicense.com/no-permission/).

**✔️ rozważyć** wybranie nazwy pakietu NuGet z prefiksem spełniającym [kryteria](/nuget/reference/id-prefix-reservation)rezerwacji prefiksu NuGet.

**✔️** Użyj odwołania https href do ikony pakietu.

> Lokacje, takie jak NuGet.org, działają z włączonym protokołem HTTPS i wyświetlanie obrazu innego niż HTTPS spowoduje utworzenie ostrzeżenia o zawartości mieszanej.

**✔️** używać obrazu ikony pakietu 64x64 i ma przezroczyste tło w celu uzyskania najlepszych wyników wyświetlania.

**✔️ rozważyć** skonfigurowanie [linku źródłowego](./sourcelink.md) w celu dodania metadanych kontroli źródła do zestawów i pakietu NuGet.

> Link źródłowy automatycznie dodaje `RepositoryUrl` i `RepositoryType` metadanych do pakietu NuGet. Link źródłowy dodaje również informacje o dokładnym kodzie źródłowym, z którego został skompilowany pakiet. Na przykład pakiet utworzony na podstawie repozytorium Git będzie miał skrót Zatwierdź dodany jako metadane.

## <a name="pre-release-packages"></a>Pakiety wersji wstępnej

Pakiety NuGet z sufiksem wersji są uważane za [wersję wstępną](/nuget/create-packages/prerelease-packages). Domyślnie interfejs użytkownika Menedżera pakietów NuGet pokazuje stabilne wersje, chyba że użytkownik zdecyduje się na pakiety wersji wstępnej, dzięki czemu pakiety wersji wstępnej są idealnym rozwiązaniem w przypadku ograniczonej liczby testów użytkownika.

```xml
<PackageVersion>1.0.1-beta1</PackageVersion>
```

> [!NOTE]
> Pakiet stabilny nie może zależeć od pakietu w wersji wstępnej. Musisz albo wprowadzić własny pakiet w wersji wstępnej, albo zależeć od starszej stabilnej wersji.

![Zależność pakietu NuGet w wersji wstępnej](./media/nuget/nuget-prerelease-package.png "Zależność pakietu NuGet w wersji wstępnej")

**✔️** opublikować pakiet w wersji wstępnej podczas testowania, podglądu lub eksperymentowania.

**✔️** opublikować pakiet stabilny, gdy gotowe do niego inne pakiety stabilne.

## <a name="symbol-packages"></a>Pakiety symboli

Pliki symboli (`*.pdb`) są generowane przez kompilator .NET obok zestawów. Pliki symboli mapują lokalizacje wykonywania na oryginalny kod źródłowy, dzięki czemu można przechodzić przez kod źródłowy, ponieważ jest on uruchamiany przy użyciu debugera. Pakiet NuGet obsługuje [generowanie oddzielnego pakietu symboli`*.snupkg`()](/nuget/create-packages/symbol-packages-snupkg) zawierającego pliki symboli obok głównego pakietu zawierającego zestawy .NET. Pomysł dotyczący pakietów symboli jest hostowany na serwerze symboli i pobierany tylko przez narzędzie, takie jak Visual Studio na żądanie.

NuGet.org hostuje własne [repozytorium serwerów symboli](/nuget/create-packages/symbol-packages-snupkg#nugetorg-symbol-server). Deweloperzy mogą używać symboli opublikowanych na serwerze symboli NuGet.org przez dodanie `https://symbols.nuget.org/download/symbols` ich do [źródeł symboli w programie Visual Studio](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger).

> [!IMPORTANT]
> Serwer symboli NuGet.org obsługuje tylko nowe [pliki symboli przenośnych](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) (`*.pdb`) utworzone przez projekty w stylu zestawu SDK.
>
> Aby użyć serwera symboli NuGet.org podczas debugowania biblioteki .NET, deweloperzy muszą mieć program Visual Studio 2017 15,9 lub nowszy.

Alternatywą dla tworzenia pakietu symboli jest osadzanie plików symboli w głównym pakiecie NuGet. Główny pakiet NuGet będzie większy, ale osadzone pliki symboli oznaczają, że deweloperzy nie muszą konfigurować serwera symboli NuGet.org. Jeśli tworzysz pakiet NuGet przy użyciu projektu w stylu zestawu SDK, możesz osadzić pliki symboli, ustawiając `AllowedOutputExtensionsInPackageBuildOutputFolder` Właściwość:

```xml
<Project Sdk="Microsoft.NET.Sdk">
 <PropertyGroup>
    <!-- Include symbol files (*.pdb) in the built .nupkg -->
    <AllowedOutputExtensionsInPackageBuildOutputFolder>$(AllowedOutputExtensionsInPackageBuildOutputFolder);.pdb</AllowedOutputExtensionsInPackageBuildOutputFolder>
  </PropertyGroup>
</Project>
```

Minusem osadzania plików symboli polega na tym, że zwiększają rozmiar pakietu o około 30% dla bibliotek .NET skompilowanych za pomocą projektów w stylu zestawu SDK. Jeśli rozmiar pakietu jest istotny, należy zamiast tego opublikować symbole w pakiecie symboli.

**✔️ rozważyć** opublikowanie symboli jako pakietu symboli (`*.snupkg`) do NuGet.org

> Pakiety symboli (`*.snupkg`) zapewniają deweloperom dobry komfort debugowania na żądanie, bez przeładowania głównego rozmiaru pakietu i wpływając na wydajność przywracania dla tych, którzy nie będą mogli debugować pakietu NuGet.
>
> Zastrzeżenie polega na tym, że użytkownicy mogą potrzebować znaleźć i skonfigurować serwer symboli NuGet w swoim środowisku IDE (jako jednorazową konfigurację), aby uzyskać pliki symboli. Program Visual Studio 2019 w wersji 16,1 dodał NuGet. serwer symboli organizacji do listy domyślnych serwerów symboli.

>[!div class="step-by-step"]
>[Poprzedni](strong-naming.md)Następny
>[](dependencies.md)
