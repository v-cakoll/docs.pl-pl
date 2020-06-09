---
ms.openlocfilehash: e7d35045892c62f759aad5067962ac5c15a9fb8b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602930"
---

Zarówno zestaw .NET Core SDK, jak i środowisko uruchomieniowe platformy .NET Core można zainstalować ręcznie po pobraniu. W przypadku zainstalowania zestaw .NET Core SDK nie trzeba instalować odpowiedniego środowiska uruchomieniowego. Najpierw pobierz wydanie binarne dla zestawu SDK lub środowiska uruchomieniowego z jednej z następujących lokacji:

- ✔️ [pobierania wersji zapoznawczej programu .net 5,0](https://dotnet.microsoft.com/download/dotnet/5.0)
- [pliki do pobrania ✔️ .NET Core 3,1](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- ❌[Pliki do pobrania w programie .NET Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- ❌[Pliki do pobrania w programie .NET Core 2,2](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [pliki do pobrania ✔️ .NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1)

Następnie wyodrębnij pobrany plik i użyj polecenia, `export` Aby ustawić zmienne używane przez platformę .NET Core, a następnie upewnij się, że program .NET Core znajduje się w ścieżce.

Aby wyodrębnić środowisko uruchomieniowe i udostępnić interfejs wiersza polecenia platformy .NET Core polecenia w terminalu, należy najpierw pobrać wydanie binarne platformy .NET Core. Następnie otwórz Terminal i uruchom następujące polecenia z katalogu, w którym zapisano plik.

```bash
mkdir -p "$HOME/dotnet" && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C "$HOME/dotnet"
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
