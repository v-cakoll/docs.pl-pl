---
title: Kompilacja platformy .NET Core ze źródła
description: Dowiedz się, jak utworzyć platformę .NET Core i interfejs wiersza polecenia platformy .NET Core z kodu źródłowego.
author: bleroy
ms.date: 06/28/2017
ms.openlocfilehash: fe5431667d861d830c2ec56252e6e3e2ca08a866
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740919"
---
# <a name="build-net-core-from-source"></a>Kompilacja platformy .NET Core ze źródła

Możliwość tworzenia programu .NET Core z jego kodu źródłowego jest ważna na wiele sposobów: ułatwia to przenoszenie platformy .NET Core na nowe platformy, umożliwia wprowadzanie wkładów i poprawek do produktu, a także umożliwia tworzenie niestandardowych wersji platformy .NET.
Ten artykuł zawiera wskazówki dla deweloperów, którzy chcą kompilować i rozpowszechniać własne wersje platformy .NET Core.

## <a name="build-the-clr-from-source"></a>Kompiluj środowisko CLR ze źródła

Kod źródłowy dla programu .NET CoreCLR można znaleźć w repozytorium [dotnet/Runtime](https://github.com/dotnet/runtime/) w witrynie GitHub.

Kompilacja zależy obecnie od następujących wymagań wstępnych:

- [Git](https://git-scm.com/)
- [CMake](https://cmake.org/)
- [Python](https://www.python.org/)
- C++ kompilator.

Po zainstalowaniu tych wymagań wstępnych można skompilować środowisko CLR, wywołując skrypt kompilacji (`build.cmd` w systemie Windows lub `build.sh` w systemie Linux i macOS) na podstawie bazy repozytorium [dotnet/Runtime](https://github.com/dotnet/runtime/) .

Instalowanie składników różni się w zależności od systemu operacyjnego. Zobacz instrukcje dotyczące kompilacji dla konkretnego systemu operacyjnego:

- [Windows](https://github.com/dotnet/coreclr/blob/master/Documentation/building/windows-instructions.md)
- [Linux](https://github.com/dotnet/coreclr/blob/master/Documentation/building/linux-instructions.md)
- [macOS](https://github.com/dotnet/coreclr/blob/master/Documentation/building/osx-instructions.md)
- [FreeBSD](https://github.com/dotnet/coreclr/blob/master/Documentation/building/freebsd-instructions.md)
- [NetBSD](https://github.com/dotnet/coreclr/blob/master/Documentation/building/netbsd-instructions.md)

W systemie operacyjnym nie ma między różnymi kompilacjami (tylko w przypadku platformy ARM, która jest oparta na architekturze x64).  
Musisz mieć na konkretną platformę, aby skompilować tę platformę.  

Kompilacja ma dwa główne `buildTypes`:

- Debuguj (domyślnie) — kompiluje środowisko uruchomieniowe z minimalnymi optymalizacjami i dodatkowymi sprawdzeniami w czasie wykonywania (potwierdzenia). To zmniejszenie poziomu optymalizacji i dodatkowych sprawdzeń w czasie wykonywania, ale są cenne dla debugowania. Jest to zalecane ustawienie dla środowisk deweloperskich i testowych.
- Wydanie — kompiluje środowisko uruchomieniowe z pełną optymalizacją i bez dodatkowych kontroli środowiska uruchomieniowego. Spowoduje to przyspieszenie wydajności w czasie wykonywania, ale może to trochę potrwać i może być trudne do debugowania. Przekaż `release` do skryptu kompilacji, aby wybrać ten typ kompilacji.

Ponadto domyślnie kompilacja nie tylko tworzy pliki wykonywalne środowiska uruchomieniowego, ale również kompiluje wszystkie testy.
Istnieje kilka testów, które nie są potrzebne, jeśli chcesz tylko eksperymentować ze zmianami.
Możesz pominąć kompilacje testów, dodając argument `skiptests` do skryptu kompilacji, jak w poniższym przykładzie (Zastąp `.\build` `./build.sh` na komputerach z systemem UNIX):

```bat
    .\build skiptests
```

W poprzednim przykładzie pokazano, jak utworzyć `Debug` wersja, która ma włączone sprawdzanie czasu projektowania (potwierdzenia), a optymalizacja została wyłączona. Aby skompilować wersję wydania (Pełna szybkość), wykonaj następujące czynności:

```bat
    .\build release skiptests
```

Możesz znaleźć więcej opcji kompilacji z kompilacją, korzystając z-? lub kwalifikator pomocy.

### <a name="using-your-build"></a>Korzystanie z kompilacji

Kompilacja umieszcza wszystkie wygenerowane pliki w katalogu `bin` w bazie repozytorium.
Istnieje katalog *bin\Log* , który zawiera pliki dziennika wygenerowane podczas kompilacji (najbardziej przydatne, gdy kompilacja zakończy się niepowodzeniem).
Rzeczywista wartość wyjściowa jest umieszczana w *bin\Product\[platformę]. [Architektura procesora]. [typ kompilacji]* Katalog, taki jak *bin\product\ Windows_NT. x64. Release*.

Chociaż nieprzetworzone dane wyjściowe kompilacji są czasami przydatne, zazwyczaj interesuje się tylko pakiety NuGet, które są umieszczane w podkatalogu `.nuget\pkg` poprzedniego katalogu wyjściowego.

Istnieją dwie podstawowe techniki korzystania z nowego środowiska uruchomieniowego:

 1. **Użyj programu dotnet. exe i NuGet, aby utworzyć aplikację**.
    Zapoznaj się z instrukcjami dotyczącymi tworzenia [programu korzystającego](https://github.com/dotnet/runtime/blob/master/docs/workflow/testing/using-your-build.md) z nowego środowiska uruchomieniowego przy użyciu utworzonej przez siebie pakietów NuGet i interfejsu wiersza polecenia "dotnet" (CLI). Ta technika jest oczekiwanym sposobem, w jaki deweloperzy niebędący środowiskiem uruchomieniowym mogą korzystać z nowego środowiska uruchomieniowego.

 2. **Użyj narzędzia do ponownego uruchomienia. exe, aby uruchomić aplikację przy użyciu nieopakowanych bibliotek DLL**.
    To repozytorium definiuje również prostego hosta o nazwie współdziałanie. exe, który nie przyjmuje żadnej zależności od NuGet.
    Musisz poinformować hosta, na którym mają zostać pobrane wymagane biblioteki DLL, i musisz ręcznie zebrać je razem.
    Ta technika jest używana przez wszystkie testy w repozytorium [dotnet/Runtime](https://github.com/dotnet/runtime) i jest przydatna w przypadku szybkiej lokalnej pętli "Edit-Compile-debug", takiej jak wstępne testy jednostkowe.
    Aby uzyskać szczegółowe informacje na temat korzystania z tej techniki, zobacz [wykonywanie aplikacji platformy .NET Core za pomocą narzędzia do ponownego uruchomienia. exe](https://github.com/dotnet/runtime/blob/master/docs/workflow/testing/using-corerun.md) .

## <a name="build-the-cli-from-source"></a>Kompilowanie interfejsu wiersza polecenia ze źródła

Kod źródłowy interfejs wiersza polecenia platformy .NET Core można znaleźć w repozytorium [dotnet/CLI](https://github.com/dotnet/cli/) w serwisie GitHub.

Aby można było skompilować interfejs wiersza polecenia platformy .NET Core, potrzebne są następujące elementy zainstalowane na komputerze.

- System Windows & Linux:
  - Git na ścieżce
- macOS:
  - Git na ścieżce
  - Xcode
  - Openssl

W celu kompilowania, uruchamiania `build.cmd` w systemie Windows lub `build.sh` w systemie Linux i macOS z poziomu katalogu głównego. Jeśli nie chcesz wykonywać testów, uruchom `build.cmd -t:Compile` lub `./build.sh -t:Compile`. Aby skompilować interfejs wiersza polecenia w macOS Sierra, należy ustawić zmienną środowiskową DOTNET_RUNTIME_ID, uruchamiając polecenie `export DOTNET_RUNTIME_ID=osx.10.11-x64`.

### <a name="using-your-build"></a>Korzystanie z kompilacji

Użyj `dotnet` pliku wykonywalnego z *artefaktów/{OS}-{Arch}/STAGE2* , aby wypróbować nowo utworzony interfejs wiersza polecenia. Jeśli chcesz użyć danych wyjściowych kompilacji podczas wywoływania `dotnet` z bieżącej konsoli, możesz również dodać *artefakty/{OS}-{Arch}/STAGE2* do ścieżki.

## <a name="see-also"></a>Zobacz także

- [Środowisko uruchomieniowe platformy .NET](https://github.com/dotnet/runtime/blob/master/README.md)
- [Przewodnik dla deweloperów interfejs wiersza polecenia platformy .NET Core](https://github.com/dotnet/cli/blob/master/Documentation/project-docs/developer-guide.md)
- [Tworzenie pakietów dystrybucji platformy .NET Core](./distribution-packaging.md)
