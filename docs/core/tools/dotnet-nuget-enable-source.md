---
title: dotnet nuget enable source, polecenie
description: Polecenie dotnet nuget enable source umożliwia istniejące źródło w plikach konfiguracyjnych NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: 1f18e7db6a6c8631bb432676dd97dabfad5b0ab8
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80148562"
---
# <a name="dotnet-nuget-enable-source"></a><span data-ttu-id="f12c5-103">dotnet nuget włączyć źródło</span><span class="sxs-lookup"><span data-stu-id="f12c5-103">dotnet nuget enable source</span></span>

<span data-ttu-id="f12c5-104">**Ten artykuł dotyczy:** ✔️.NET Core 3.1.200 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="f12c5-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="f12c5-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="f12c5-105">Name</span></span>

<span data-ttu-id="f12c5-106">`dotnet nuget enable source`- Włącz źródło NuGet.</span><span class="sxs-lookup"><span data-stu-id="f12c5-106">`dotnet nuget enable source` - Enable a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f12c5-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="f12c5-107">Synopsis</span></span>

```dotnetcli
dotnet nuget enable source <NAME> [--configfile]
dotnet nuget enable source [-h|--help]
```

## <a name="description"></a><span data-ttu-id="f12c5-108">Opis</span><span class="sxs-lookup"><span data-stu-id="f12c5-108">Description</span></span>

<span data-ttu-id="f12c5-109">Polecenie `dotnet nuget enable source` włącza istniejące źródło w plikach konfiguracyjnych NuGet.</span><span class="sxs-lookup"><span data-stu-id="f12c5-109">The `dotnet nuget enable source` command enables an existing source in your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="f12c5-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="f12c5-110">Arguments</span></span>

- **`NAME`**

  <span data-ttu-id="f12c5-111">Nazwa źródła.</span><span class="sxs-lookup"><span data-stu-id="f12c5-111">Name of the source.</span></span>

## <a name="options"></a><span data-ttu-id="f12c5-112">Opcje</span><span class="sxs-lookup"><span data-stu-id="f12c5-112">Options</span></span>

- **`--configfile`**

  <span data-ttu-id="f12c5-113">Plik konfiguracyjny NuGet.</span><span class="sxs-lookup"><span data-stu-id="f12c5-113">The NuGet configuration file.</span></span> <span data-ttu-id="f12c5-114">Jeśli zostanie określony, będą używane tylko ustawienia z tego pliku.</span><span class="sxs-lookup"><span data-stu-id="f12c5-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="f12c5-115">Jeśli nie zostanie określona, zostanie użyta hierarchia plików konfiguracyjnych z bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="f12c5-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="f12c5-116">Aby uzyskać więcej informacji, zobacz [typowe konfiguracje NuGet](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="f12c5-116">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

## <a name="examples"></a><span data-ttu-id="f12c5-117">Przykłady</span><span class="sxs-lookup"><span data-stu-id="f12c5-117">Examples</span></span>

- <span data-ttu-id="f12c5-118">Włącz źródło o `mySource`nazwie :</span><span class="sxs-lookup"><span data-stu-id="f12c5-118">Enable a source with name of `mySource`:</span></span>

  ```dotnetcli
  dotnet nuget enable source mySource
  ```

## <a name="see-also"></a><span data-ttu-id="f12c5-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f12c5-119">See also</span></span>

- [<span data-ttu-id="f12c5-120">Sekcje źródła pakietów w plikach NuGet.config</span><span class="sxs-lookup"><span data-stu-id="f12c5-120">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="f12c5-121">sources, polecenie (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="f12c5-121">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
