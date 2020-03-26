---
title: polecenie źródło listy dotnet nuget
description: Polecenie źródło listy nuget dotnet zawiera listę wszystkich istniejących źródeł z plików konfiguracyjnych NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: 4d7bc3dbd3ab5eb14c1ebf592044b685d28355cd
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80148576"
---
# <a name="dotnet-nuget-list-source"></a><span data-ttu-id="c751f-103">źródło listy dotnet nuget</span><span class="sxs-lookup"><span data-stu-id="c751f-103">dotnet nuget list source</span></span>

<span data-ttu-id="c751f-104">**Ten artykuł dotyczy:** ✔️.NET Core 3.1.200 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="c751f-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="c751f-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="c751f-105">Name</span></span>

<span data-ttu-id="c751f-106">`dotnet nuget list source`- Wyświetla listę wszystkich skonfigurowanych źródeł NuGet.</span><span class="sxs-lookup"><span data-stu-id="c751f-106">`dotnet nuget list source` - Lists all configured NuGet sources.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c751f-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="c751f-107">Synopsis</span></span>

```dotnetcli
dotnet nuget list source [--format] [--configfile]
dotnet nuget list source [-h|--help]
```

## <a name="description"></a><span data-ttu-id="c751f-108">Opis</span><span class="sxs-lookup"><span data-stu-id="c751f-108">Description</span></span>

<span data-ttu-id="c751f-109">Polecenie `dotnet nuget list source` zawiera listę wszystkich istniejących źródeł z plików konfiguracyjnych NuGet.</span><span class="sxs-lookup"><span data-stu-id="c751f-109">The `dotnet nuget list source` command lists all existing sources from your NuGet configuration files.</span></span>

## <a name="options"></a><span data-ttu-id="c751f-110">Opcje</span><span class="sxs-lookup"><span data-stu-id="c751f-110">Options</span></span>

- **`--configfile`**

  <span data-ttu-id="c751f-111">Plik konfiguracyjny NuGet.</span><span class="sxs-lookup"><span data-stu-id="c751f-111">The NuGet configuration file.</span></span> <span data-ttu-id="c751f-112">Jeśli zostanie określony, będą używane tylko ustawienia z tego pliku.</span><span class="sxs-lookup"><span data-stu-id="c751f-112">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="c751f-113">Jeśli nie zostanie określona, zostanie użyta hierarchia plików konfiguracyjnych z bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="c751f-113">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="c751f-114">Aby uzyskać więcej informacji, zobacz [typowe konfiguracje NuGet](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="c751f-114">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

- **`--format`**

  <span data-ttu-id="c751f-115">Format wyjścia polecenia listy: `Detailed` (domyślny) `Short`i .</span><span class="sxs-lookup"><span data-stu-id="c751f-115">The format of the list command output: `Detailed` (the default) and `Short`.</span></span>

## <a name="examples"></a><span data-ttu-id="c751f-116">Przykłady</span><span class="sxs-lookup"><span data-stu-id="c751f-116">Examples</span></span>

- <span data-ttu-id="c751f-117">Lista skonfigurowanych źródeł z bieżącego katalogu:</span><span class="sxs-lookup"><span data-stu-id="c751f-117">List configured sources from the current directory:</span></span>

  ```dotnetcli
  dotnet nuget list source
  ```

## <a name="see-also"></a><span data-ttu-id="c751f-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c751f-118">See also</span></span>

- [<span data-ttu-id="c751f-119">Sekcje źródła pakietów w plikach NuGet.config</span><span class="sxs-lookup"><span data-stu-id="c751f-119">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="c751f-120">sources, polecenie (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="c751f-120">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
