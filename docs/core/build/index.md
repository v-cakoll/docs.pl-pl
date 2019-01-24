---
title: Kompilacja platformy .NET Core ze źródła
description: 'Dowiedz się, jak tworzyć oprogramowanie .NET Core i .NET Core interfejsu wiersza polecenia z kodu źródłowego.'
author: bleroy
ms.date: 06/28/2017
ms.custom: seodec18
---

# <a name="build-net-core-from-source"></a>Kompilacja platformy .NET Core ze źródła

Kompilacja platformy .NET Core z jego kod źródłowy jest ważne na wiele sposobów: ułatwia port platformy .NET Core do nowych platform, umożliwia wkładu i poprawek dotyczących produktu, i umożliwia tworzenie niestandardowych wersji platformy .NET.
Ten artykuł zawiera wskazówki dla deweloperów, którzy chcą dystrybucję własnych wersji platformy .NET Core.

## <a name="build-the-clr-from-source"></a>Tworzenie środowiska CLR ze źródła

Kod źródłowy w programie CoreCLR .NET można znaleźć w [dotnet/coreclr](https://github.com/dotnet/coreclr/) repozytorium w witrynie GitHub.

Kompilacja obecnie zależy od następujących wymagań wstępnych:

* [Usługa Git](https://git-scm.com/)
* [Narzędzia CMake](https://cmake.org/)
* [Python](https://www.python.org/)
* kompilator języka C++.

Po zainstalowaniu wymagań wstępnych, można tworzyć środowiska CLR, wywołując skrypt kompilacji (`build.cmd` na Windows, lub `build.sh` w systemie Linux i macOS) u dołu [dotnet/coreclr](https://github.com/dotnet/coreclr/) repozytorium.

Instalowanie składników różnią się zależnie od systemu operacyjnego (OS). Zapoznaj się z instrukcjami kompilacji dla swojego określonego systemu operacyjnego:

* [Windows](https://github.com/dotnet/coreclr/blob/master/Documentation/building/windows-instructions.md)
* [Linux](https://github.com/dotnet/coreclr/blob/master/Documentation/building/linux-instructions.md)
* [macOS](https://github.com/dotnet/coreclr/blob/master/Documentation/building/osx-instructions.md)
* [FreeBSD](https://github.com/dotnet/coreclr/blob/master/Documentation/building/freebsd-instructions.md)
* [NetBSD](https://github.com/dotnet/coreclr/blob/master/Documentation/building/netbsd-instructions.md)

Nie ma żadnych tworzenie wielu różnych systemów operacyjnych (tylko dla ARM, która jest oparta na X64).  
Muszą znajdować się na konkretnej platformie do tworzenia tej platformy.  

Kompilacja ma dwa główne `buildTypes`:

* Debugowanie (ustawienie domyślne) — kompiluje środowiska uruchomieniowego przy użyciu minimalnego optymalizacje i kontrole dodatkowe środowiska uruchomieniowego (potwierdza). Takie zmniejszenie poziom optymalizacji i dodatkowe kontrole spowolnić wykonywanie środowiska uruchomieniowego, ale są przydatne do debugowania. To ustawienie zalecane dla środowisk programowania i testowania.
* Release — kompiluje środowiska uruchomieniowego za pomocą pełnego optymalizacje i bez testy dodatkowe środowiska uruchomieniowego. Umożliwia to uzyskanie wydajności znacznie szybciej czas wykonywania, ale może trwać nieco dłużej, tworzyć i może być trudne do debugowania. Przekaż `release` do kompilacji skrypt, aby wybrać tę opcję, typ kompilacji.

Ponadto domyślnie kompilacji tworzy nie tylko pliki wykonywalne środowiska uruchomieniowego, ale sprzyja wytwarzaniu wszystkie testy.
Istnieje kilka testów, biorąc znaczną ilość czasu, który nie jest konieczne, jeśli chcesz, aby eksperymentować z zmiany.
Możesz pominąć kompilacje testów przez dodanie `skiptests` argument skrypt kompilacji, jak pokazano w poniższym przykładzie (Zastąp `.\build` z `./build.sh` na komputerach z systemem Unix):

```bat
    .\build skiptests
```

W poprzednim przykładzie pokazano sposób tworzenia `Debug` smak ma sprawdzania w trakcie rozwoju (potwierdza) włączone i wyłączone optymalizacje. Aby skompilować wersję (z pełną prędkością) wersji, wykonaj następujące czynności:

```bat
    .\build release skiptests
```

Można znaleźć więcej kompilacji opcje kompilacji przy użyciu? lub - help kwalifikator.

### <a name="using-your-build"></a>Za pomocą kompilacji

Kompilacja umieszcza wszystkich wygenerowanych plików w obszarze `bin` katalogu z podstawową repozytorium.
Brak *bin\Log* katalog zawierający pliki dziennika generowane podczas kompilacji (najbardziej przydatne w przypadku niepowodzenia kompilacji).
Rzeczywiste wyniki są umieszczane w *bin\Product\[platformy]. [ Architektura Procesora]. [typ kompilacji]*  katalogu, takie jak *bin\Product\Windows_NT.x64.Release*.

Chociaż czasami przydaje "raw" dane wyjściowe kompilacji, zwykle interesuje Cię tylko pakiety NuGet, które są umieszczane w `.nuget\pkg` podkatalogu poprzedniego katalogu wyjściowego.

Istnieją dwie podstawowe metody za pomocą Twojego nowego środowiska uruchomieniowego:

 1. **Tworzenie aplikacji za pomocą dotnet.exe i NuGet**.
    Zobacz [przy użyciu kompilacji](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingYourBuild.md) instrukcje dotyczące tworzenia program, który używa Twojego nowego środowiska uruchomieniowego przy użyciu pakietu NuGet pakietów właśnie utworzony i interfejsu wiersza polecenia "dotnet" (CLI). Ta technika jest oczekiwany sposób deweloperzy innych środowiska uruchomieniowego są mogących korzystać z nowego środowiska uruchomieniowego.

 2. **Użyj corerun.exe, aby uruchomić aplikację przy użyciu biblioteki DLL rozpakowanych**.
    To repozytorium definiuje również proste hosta o nazwie corerun.exe który nie ma żadnych zależności dla narzędzia NuGet.
    Należy przekazać do uzyskania wymaganych bibliotek DLL faktycznie używać hosta i musisz ręcznie zebrać je ze sobą.
    Ta technika jest używany przez wszystkie testy w [dotnet/coreclr](https://github.com/dotnet/coreclr) repozytorium i jest przydatne w przypadku pętli szybkiego lokalnego "Edycja kompilacji debug" takich jak testy jednostkowe wstępnego.
    Zobacz [wykonywania aplikacji programu .NET Core za pomocą CoreRun.exe](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingCoreRun.md) Aby uzyskać szczegółowe informacje na temat korzystania z tej techniki.

## <a name="build-the-cli-from-source"></a>Tworzenie interfejsu wiersza polecenia ze źródła

Kod źródłowy dla platformy .NET Core interfejsu wiersza polecenia można znaleźć w [interfejsu wiersza poleceniadotnet/](https://github.com/dotnet/cli/) repozytorium w witrynie GitHub.

Aby można było utworzyć interfejsu wiersza polecenia platformy .NET Core, potrzebne będą zainstalowane na tym komputerze.

* Windows i Linux:
  * git na ŚCIEŻCE
* macOS:
  * git na ŚCIEŻCE
  * Xcode
  * Openssl

Aby skompilować, uruchom `build.cmd` na Windows, lub `build.sh` w systemie Linux i macOS z katalogu głównego. Jeśli nie chcesz wykonać testy, należy uruchomić `build.cmd -t:Compile` lub `./build.sh -t:Compile`. Aby utworzyć interfejs wiersza polecenia w systemie macOS Sierra, musisz ustawić zmienną środowiskową DOTNET_RUNTIME_ID, uruchamiając `export DOTNET_RUNTIME_ID=osx.10.11-x64`.

### <a name="using-your-build"></a>Za pomocą kompilacji

Użyj `dotnet` z *artefaktów / {os}-{arch} / stage2* do wypróbowania nowo zbudowany interfejs wiersza polecenia. Jeśli chcesz używać dane wyjściowe podczas wywoływania kompilacji `dotnet` z bieżącą konsolę, można również dodać *artefaktów / {os}-{arch} / stage2* do ścieżki.

## <a name="see-also"></a>Zobacz także

- [.NET core środowiska uruchomieniowego języka wspólnego (CoreCLR)](https://github.com/dotnet/coreclr/blob/master/README.md)
- [Przewodnik dewelopera programu .NET core interfejsu wiersza polecenia](https://github.com/dotnet/cli/blob/master/Documentation/project-docs/developer-guide.md)
- [Tworzenie pakietów dystrybucji platformy .NET Core](./distribution-packaging.md)
