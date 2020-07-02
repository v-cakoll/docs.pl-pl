---
ms.openlocfilehash: ea2883912907843e4b6d65db5ba186af43f27aaa
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85805845"
---

<!-- Note, this content is copied in ../macos.md. Any fixes should be applied there too, though content may be different -->

Jako alternatywę dla menedżerów pakietów można pobrać i ręcznie zainstalować zestaw SDK i środowisko uruchomieniowe. Instalacja ręczna jest zwykle wykonywana w ramach testowania ciągłej integracji lub nieobsługiwanej dystrybucji systemu Linux. W przypadku deweloperów lub użytkowników zazwyczaj lepiej jest używać Menedżera pakietów.

W przypadku zainstalowania zestaw .NET Core SDK nie trzeba instalować odpowiedniego środowiska uruchomieniowego. Najpierw pobierz wydanie **binarne** dla zestawu SDK lub środowiska uruchomieniowego z jednej z następujących lokacji:

- ✔️ [pobierania wersji zapoznawczej programu .net 5,0](https://dotnet.microsoft.com/download/dotnet/5.0)
- [pliki do pobrania ✔️ .NET Core 3,1](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [pliki do pobrania ✔️ .NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1)
- [Wszystkie pliki do pobrania z platformy .NET Core](https://dotnet.microsoft.com/download/dotnet-core)

Następnie wyodrębnij pobrany plik i użyj polecenia, `export` Aby ustawić zmienne używane przez platformę .NET Core, a następnie upewnij się, że program .NET Core znajduje się w ścieżce.

Aby wyodrębnić środowisko uruchomieniowe i udostępnić interfejs wiersza polecenia platformy .NET Core polecenia w terminalu, należy najpierw pobrać wydanie binarne platformy .NET Core. Następnie otwórz Terminal i uruchom następujące polecenia z katalogu, w którym zapisano plik. Nazwa pliku archiwum może się różnić w zależności od pobranych informacji.

**Aby wyodrębnić środowisko uruchomieniowe, użyj następującego polecenia**:

```bash
mkdir -p "$HOME/dotnet" && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

**Użyj następującego polecenia, aby wyodrębnić zestaw SDK**:

```bash
mkdir -p "$HOME/dotnet" && tar zxf dotnet-sdk-3.1.301-linux-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> Powyższe `export` polecenia sprawiają, że polecenia interfejs wiersza polecenia platformy .NET Core są dostępne tylko dla sesji terminalu, w której została uruchomiona.
>
> Możesz edytować profil powłoki, aby trwale dodać polecenia. Istnieje wiele różnych powłok dostępnych dla systemu Linux, a każdy z nich ma inny profil. Przykład:
>
> - **Bash Shell**: *~/. bash_profile*, *~/.bashrc.*
> - **Powłoka Korn**: *~/.KSHRC* lub *. profile*
> - **Powłoka Z**: *~/.zshrc* lub *. zprofile*
>
> Edytuj odpowiedni plik źródłowy dla powłoki i Dodaj `:$HOME/dotnet` na końcu istniejącej `PATH` instrukcji. Jeśli `PATH` instrukcja nie jest uwzględniona, Dodaj nowy wiersz za pomocą `export PATH=$PATH:$HOME/dotnet` .
>
> Ponadto Dodaj `export DOTNET_ROOT=$HOME/dotnet` na końcu pliku.

Takie podejście umożliwia zainstalowanie różnych wersji w oddzielnych lokalizacjach i wybór jawny, który ma być używany przez aplikację.
