---
ms.openlocfilehash: ea2883912907843e4b6d65db5ba186af43f27aaa
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85805845"
---

<!-- Note, this content is copied in ../macos.md. Any fixes should be applied there too, though content may be different -->

<span data-ttu-id="33b52-101">Jako alternatywę dla menedżerów pakietów można pobrać i ręcznie zainstalować zestaw SDK i środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="33b52-101">As an alternative to the package managers, you can download and manually install the SDK and runtime.</span></span> <span data-ttu-id="33b52-102">Instalacja ręczna jest zwykle wykonywana w ramach testowania ciągłej integracji lub nieobsługiwanej dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="33b52-102">Manual install is usually performed as part of continuous integration testing or on an unsupported Linux distribution.</span></span> <span data-ttu-id="33b52-103">W przypadku deweloperów lub użytkowników zazwyczaj lepiej jest używać Menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="33b52-103">For a developer or user, it's generally better to use a package manager.</span></span>

<span data-ttu-id="33b52-104">W przypadku zainstalowania zestaw .NET Core SDK nie trzeba instalować odpowiedniego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="33b52-104">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="33b52-105">Najpierw pobierz wydanie **binarne** dla zestawu SDK lub środowiska uruchomieniowego z jednej z następujących lokacji:</span><span class="sxs-lookup"><span data-stu-id="33b52-105">First, download a **binary** release for either the SDK or the runtime from one of the following sites:</span></span>

- <span data-ttu-id="33b52-106">✔️ [pobierania wersji zapoznawczej programu .net 5,0](https://dotnet.microsoft.com/download/dotnet/5.0)</span><span class="sxs-lookup"><span data-stu-id="33b52-106">✔️ [.NET 5.0 preview downloads](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>
- <span data-ttu-id="33b52-107">[pliki do pobrania ✔️ .NET Core 3,1](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span><span class="sxs-lookup"><span data-stu-id="33b52-107">✔️ [.NET Core 3.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span></span>
- <span data-ttu-id="33b52-108">[pliki do pobrania ✔️ .NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span><span class="sxs-lookup"><span data-stu-id="33b52-108">✔️ [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span></span>
- [<span data-ttu-id="33b52-109">Wszystkie pliki do pobrania z platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="33b52-109">All .NET Core downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

<span data-ttu-id="33b52-110">Następnie wyodrębnij pobrany plik i użyj polecenia, `export` Aby ustawić zmienne używane przez platformę .NET Core, a następnie upewnij się, że program .NET Core znajduje się w ścieżce.</span><span class="sxs-lookup"><span data-stu-id="33b52-110">Next, extract the downloaded file and use the `export` command to set variables used by .NET Core and then ensure .NET Core is in PATH.</span></span>

<span data-ttu-id="33b52-111">Aby wyodrębnić środowisko uruchomieniowe i udostępnić interfejs wiersza polecenia platformy .NET Core polecenia w terminalu, należy najpierw pobrać wydanie binarne platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="33b52-111">To extract the runtime and make the .NET Core CLI commands available at the terminal, first download a .NET Core binary release.</span></span> <span data-ttu-id="33b52-112">Następnie otwórz Terminal i uruchom następujące polecenia z katalogu, w którym zapisano plik.</span><span class="sxs-lookup"><span data-stu-id="33b52-112">Then, open a terminal and run the following commands from the directory where the file was saved.</span></span> <span data-ttu-id="33b52-113">Nazwa pliku archiwum może się różnić w zależności od pobranych informacji.</span><span class="sxs-lookup"><span data-stu-id="33b52-113">The archive file name may be different depending on what you downloaded.</span></span>

<span data-ttu-id="33b52-114">**Aby wyodrębnić środowisko uruchomieniowe, użyj następującego polecenia**:</span><span class="sxs-lookup"><span data-stu-id="33b52-114">**Use the following command to extract the runtime**:</span></span>

```bash
mkdir -p "$HOME/dotnet" && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

<span data-ttu-id="33b52-115">**Użyj następującego polecenia, aby wyodrębnić zestaw SDK**:</span><span class="sxs-lookup"><span data-stu-id="33b52-115">**Use the following command to extract the SDK**:</span></span>

```bash
mkdir -p "$HOME/dotnet" && tar zxf dotnet-sdk-3.1.301-linux-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="33b52-116">Powyższe `export` polecenia sprawiają, że polecenia interfejs wiersza polecenia platformy .NET Core są dostępne tylko dla sesji terminalu, w której została uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="33b52-116">The preceding `export` commands only make the .NET Core CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="33b52-117">Możesz edytować profil powłoki, aby trwale dodać polecenia.</span><span class="sxs-lookup"><span data-stu-id="33b52-117">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="33b52-118">Istnieje wiele różnych powłok dostępnych dla systemu Linux, a każdy z nich ma inny profil.</span><span class="sxs-lookup"><span data-stu-id="33b52-118">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="33b52-119">Przykład:</span><span class="sxs-lookup"><span data-stu-id="33b52-119">For example:</span></span>
>
> - <span data-ttu-id="33b52-120">**Bash Shell**: *~/. bash_profile*, *~/.bashrc.*</span><span class="sxs-lookup"><span data-stu-id="33b52-120">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="33b52-121">**Powłoka Korn**: *~/.KSHRC* lub *. profile*</span><span class="sxs-lookup"><span data-stu-id="33b52-121">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="33b52-122">**Powłoka Z**: *~/.zshrc* lub *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="33b52-122">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="33b52-123">Edytuj odpowiedni plik źródłowy dla powłoki i Dodaj `:$HOME/dotnet` na końcu istniejącej `PATH` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="33b52-123">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="33b52-124">Jeśli `PATH` instrukcja nie jest uwzględniona, Dodaj nowy wiersz za pomocą `export PATH=$PATH:$HOME/dotnet` .</span><span class="sxs-lookup"><span data-stu-id="33b52-124">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="33b52-125">Ponadto Dodaj `export DOTNET_ROOT=$HOME/dotnet` na końcu pliku.</span><span class="sxs-lookup"><span data-stu-id="33b52-125">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

<span data-ttu-id="33b52-126">Takie podejście umożliwia zainstalowanie różnych wersji w oddzielnych lokalizacjach i wybór jawny, który ma być używany przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="33b52-126">This approach lets you install different versions into separate locations and choose explicitly which one to use by which application.</span></span>
