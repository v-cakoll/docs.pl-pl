---
title: polecenie źródło listy dotnet nuget
description: Polecenie źródło listy nuget dotnet zawiera listę wszystkich istniejących źródeł z plików konfiguracyjnych NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: 8b14413949bd60ddeed977d19eec9bb99982da70
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463543"
---
# <a name="dotnet-nuget-list-source"></a><span data-ttu-id="83740-103">dotnet nuget list source</span><span class="sxs-lookup"><span data-stu-id="83740-103">dotnet nuget list source</span></span>

<span data-ttu-id="83740-104">**Ten artykuł dotyczy:** ✔️.NET Core 3.1.200 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="83740-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="83740-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="83740-105">Name</span></span>

<span data-ttu-id="83740-106">`dotnet nuget list source`- Wyświetla listę wszystkich skonfigurowanych źródeł NuGet.</span><span class="sxs-lookup"><span data-stu-id="83740-106">`dotnet nuget list source` - Lists all configured NuGet sources.</span></span>

## <a name="synopsis"></a><span data-ttu-id="83740-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="83740-107">Synopsis</span></span>

```dotnetcli
dotnet nuget list source [--format [Detailed|Short]] [--configfile <FILE>]

dotnet nuget list source -h|--help
```

## <a name="description"></a><span data-ttu-id="83740-108">Opis</span><span class="sxs-lookup"><span data-stu-id="83740-108">Description</span></span>

<span data-ttu-id="83740-109">Polecenie `dotnet nuget list source` zawiera listę wszystkich istniejących źródeł z plików konfiguracyjnych NuGet.</span><span class="sxs-lookup"><span data-stu-id="83740-109">The `dotnet nuget list source` command lists all existing sources from your NuGet configuration files.</span></span>

## <a name="options"></a><span data-ttu-id="83740-110">Opcje</span><span class="sxs-lookup"><span data-stu-id="83740-110">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="83740-111">Plik konfiguracyjny NuGet.</span><span class="sxs-lookup"><span data-stu-id="83740-111">The NuGet configuration file.</span></span> <span data-ttu-id="83740-112">Jeśli zostanie określony, będą używane tylko ustawienia z tego pliku.</span><span class="sxs-lookup"><span data-stu-id="83740-112">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="83740-113">Jeśli nie zostanie określona, zostanie użyta hierarchia plików konfiguracyjnych z bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="83740-113">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="83740-114">Aby uzyskać więcej informacji, zobacz [typowe konfiguracje NuGet](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="83740-114">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

- **`--format [Detailed|Short]`**

  <span data-ttu-id="83740-115">Format wyjścia polecenia listy: `Detailed` (domyślny) `Short`i .</span><span class="sxs-lookup"><span data-stu-id="83740-115">The format of the list command output: `Detailed` (the default) and `Short`.</span></span>

## <a name="examples"></a><span data-ttu-id="83740-116">Przykłady</span><span class="sxs-lookup"><span data-stu-id="83740-116">Examples</span></span>

- <span data-ttu-id="83740-117">Lista skonfigurowanych źródeł z bieżącego katalogu:</span><span class="sxs-lookup"><span data-stu-id="83740-117">List configured sources from the current directory:</span></span>

  ```dotnetcli
  dotnet nuget list source
  ```

## <a name="see-also"></a><span data-ttu-id="83740-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="83740-118">See also</span></span>

- [<span data-ttu-id="83740-119">Sekcje źródła pakietów w plikach NuGet.config</span><span class="sxs-lookup"><span data-stu-id="83740-119">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="83740-120">sources, polecenie (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="83740-120">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
