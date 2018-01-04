---
title: "Kompilacji platformy .NET Core ze źródła"
description: "Informacje o sposobie tworzenia .NET Core i .NET Core interfejsu wiersza polecenia z kodu źródłowego."
keywords: "Źródło .NET i .NET core, kompilacji"
author: bleroy
ms.author: mairaw
ms.date: 06/28/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 8b49079c-6ede-429a-92d7-ecd2fda1ab0e
ms.workload: dotnetcore
ms.openlocfilehash: 6aa5abd071355b1c1a367b35e9521e6b1af9c945
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="build-net-core-from-source"></a>Kompilacji platformy .NET Core ze źródła

Możliwość kompilacji platformy .NET Core z jego kod źródłowy jest ważne na wiele sposobów: ułatwi do portu .NET Core do nowych platform, umożliwia wkładów i poprawki produktu oraz umożliwia tworzenie niestandardowych wersji platformy .NET.
Ten artykuł zawiera wskazówki dla deweloperów chcących do tworzenia i rozpowszechniania własnych wersji platformy .NET Core.

## <a name="build-the-clr-from-source"></a>Tworzenie środowiska CLR ze źródła

Kod źródłowy środowisko CoreCLR .NET można znaleźć w [ `dotnet/coreclr` repozytorium w usłudze GitHub](https://github.com/dotnet/coreclr/).

Kompilacja zależy obecnie następujące wymagania wstępne:
* [Git](https://git-scm.com/)
* [CMake](https://cmake.org/)
* [Python](https://www.python.org/)
* kompilator języka C++.

Po zainstalowaniu wymagań wstępnych są zainstalowane, CLR można tworzyć za pomocą skryptu kompilacji (`build.cmd` w systemie Windows, lub `build.sh` w systemie Linux i macOS) u dołu [repozytorium środowisko CoreCLR](https://github.com/dotnet/coreclr/).

Instalowanie składników różnią się w zależności od systemu operacyjnego (systemu operacyjnego). Zapoznaj się z instrukcjami kompilacji dla określonej system operacyjny:

 * [Windows](https://github.com/dotnet/coreclr/blob/master/Documentation/building/windows-instructions.md)
 * [Linux](https://github.com/dotnet/coreclr/blob/master/Documentation/building/linux-instructions.md)
 * [System macOS](https://github.com/dotnet/coreclr/blob/master/Documentation/building/osx-instructions.md)
 * [FreeBSD](https://github.com/dotnet/coreclr/blob/master/Documentation/building/freebsd-instructions.md) 
 * [NetBSD](https://github.com/dotnet/coreclr/blob/master/Documentation/building/netbsd-instructions.md)

Nie ma żadnych budowania między przez system operacyjny (tylko dla ARM, który jest oparty na X64).  
Muszą znajdować się w szczególności platformę do tworzenia tej platformy.  

Kompilacja ma dwa główne `buildTypes`:

 * Debugowania (domyślnie) — kompiluje obsługi z minimalnym optymalizacji i Sprawdzanie czasu wykonania dodatkowych (potwierdzeń). Zmniejszenie poziomu optymalizacji i dodatkowe kontrole powolna wykonywania środowiska uruchomieniowego, ale są przydatne do debugowania. To ustawienie zalecane dla środowisk projektowych i testowych.
 * Release — kompiluje środowiska uruchomieniowego z pełną optymalizacji i bez kontroli dodatkowe środowiska wykonawczego. Umożliwia to uzyskanie wydajności znacznie szybciej czas wykonywania, ale może zająć nieco dłużej i może być trudne do debugowania. Przekaż `release` do kompilacji skrypt, aby wybrać tę opcję, typ kompilacji.

Ponadto domyślnie kompilacji nie tylko tworzy pliki wykonywalne środowiska uruchomieniowego, ale również tworzy wszystkie testy.
Istnieje kilka testy, biorąc znaczną ilość czasu, który nie jest konieczne, jeśli chcesz, aby wypróbować zmiany.
Kompilacje testów można pominąć, dodając `skiptests` argument skryptu kompilacji, takich jak w poniższym przykładzie (Zastąp `.\build` z `./build.sh` na komputerach Unix):

```bat
    .\build skiptests 
```

W poprzednim przykładzie pokazano sposób tworzenia `Debug` podtyp, którego rozwój sprawdzanie w trakcie wykonywania (potwierdzeń) włączone i wyłączone optymalizacje. Tworzenie wersji podtyp (pełnej szybkości), wykonaj następujące czynności:

```bat 
    .\build release skiptests
```

Można znaleźć opcje więcej kompilacji z kompilacją przy użyciu? lub - help kwalifikatora.   

### <a name="using-your-build"></a>Za pomocą kompilacji

Kompilacja umieszcza wszystkie jego pliki generowane w obszarze `bin` katalogu u podstawy repozytorium.
Brak *bin\Log* katalog zawierający pliki dziennika wygenerowanych podczas kompilacji (najbardziej przydatne w przypadku niepowodzenia kompilacji).
Rzeczywiste wyniki są umieszczane w *bin\Product\[platformy]. [ Architektura Procesora]. [typ kompilacji]*  katalogu, takie jak *bin\Product\Windows_NT.x64.Release*.

Podczas gdy "raw" dane wyjściowe kompilacji czasami jest przydatne, zwykle interesuje Cię tylko pakietów NuGet, które są umieszczane w `.nuget\pkg` podkatalogu poprzedniej katalogu wyjściowego.

Istnieją dwie podstawowe metody przy użyciu Twoje nowe środowisko uruchomieniowe:

 1. **Umożliwia utworzenie aplikacji dotnet.exe i NuGet**.
    Zobacz [przy użyciu Your kompilacji](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingYourBuild.md) instrukcje dotyczące tworzenia program, który używa Twoje nowe środowisko uruchomieniowe przy użyciu pakietów NuGet właśnie utworzony i "dotnet" interfejsu wiersza polecenia (CLI). Ta technika jest najprawdopodobniej Twoje nowe środowisko uruchomieniowe to deweloperom runtime z systemem innym niż oczekiwany sposób.    

 2. **Użyj corerun.exe, aby uruchomić aplikację przy użyciu bibliotek DLL rozpakowanych**.
    To repozytorium definiuje również proste hosta o nazwie corerun.exe, który nie przyjmuje żadnych zależności NuGet.
    Należy określić hosta do uzyskania wymaganych bibliotek DLL rzeczywiście używane i musisz ręcznie zebrać je razem.
    Ta technika jest używany przez wszystkie testy w [repozytorium środowisko CoreCLR](https://github.com/dotnet/coreclr)i ułatwia szybkie lokalnego "Edycja kompilacji debugowania" pętli takich jak wstępnego testowania jednostek.
    Zobacz [wykonywania aplikacji programu .NET Core z CoreRun.exe](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingCoreRun.md) szczegółowe informacje na temat używania tej metody.

## <a name="build-the-cli-from-source"></a>Tworzenie interfejsu wiersza polecenia ze źródła

Kod źródłowy dla platformy .NET Core interfejsu wiersza polecenia można znaleźć w [ `dotnet/cli` repozytorium w usłudze GitHub](https://github.com/dotnet/cli/).

Aby można było skompilować .NET Core interfejsu wiersza polecenia, należy spełnić następujące zainstalowane na tym komputerze.

* System Windows i Linux:
    - git w ŚCIEŻCE
* System macOS:
    - git w ŚCIEŻCE
    - Xcode
    - Openssl

Aby można było skompilować, uruchom `build.cmd` w systemie Windows, lub `build.sh` w systemie Linux i macOS z katalogu głównego. Jeśli nie chcesz wykonywać testy, uruchom `build.cmd /t:Compile` lub `./build.sh /t:Compile`. Aby utworzyć interfejsu wiersza polecenia w macOS Sierra, należy ustawić zmienną środowiskową DOTNET_RUNTIME_ID, uruchamiając `export DOTNET_RUNTIME_ID=osx.10.11-x64`.

### <a name="using-your-build"></a>Za pomocą kompilacji

Użyj `dotnet` pliku wykonywalnego z *artefakty / {os}-{arch} / stage2* wypróbowanie nowo zbudowany interfejsu wiersza polecenia. Jeśli chcesz użyć kompilacji dane wyjściowe w przypadku wywoływania `dotnet` z bieżącą konsolę, można również dodać *artefakty / {os}-{arch} / stage2* do ścieżki.

## <a name="see-also"></a>Zobacz także

* [.NET core środowisko uruchomieniowe języka wspólnego (środowisko CoreCLR)](https://github.com/dotnet/coreclr/blob/master/README.md)
* [Przewodnik dewelopera po .NET core interfejsu wiersza polecenia](https://github.com/dotnet/cli/blob/master/Documentation/project-docs/developer-guide.md)
* [Tworzenie pakietów dystrybucji platformy .NET Core](./distribution-packaging.md)
