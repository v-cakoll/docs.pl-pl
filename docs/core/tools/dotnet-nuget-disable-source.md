---
title: dotnet nuget wyłącz polecenie source
description: Polecenie dotnet nuget disable source wyłącza istniejące źródło w plikach konfiguracyjnych NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: 54acb40b1944eaff347107e8f3439578ec8e0f3c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463565"
---
# <a name="dotnet-nuget-disable-source"></a><span data-ttu-id="0566b-103">dotnet nuget disable source</span><span class="sxs-lookup"><span data-stu-id="0566b-103">dotnet nuget disable source</span></span>

<span data-ttu-id="0566b-104">**Ten artykuł dotyczy:** ✔️.NET Core 3.1.200 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="0566b-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="0566b-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="0566b-105">Name</span></span>

<span data-ttu-id="0566b-106">`dotnet nuget disable source`- Wyłącz źródło NuGet.</span><span class="sxs-lookup"><span data-stu-id="0566b-106">`dotnet nuget disable source` - Disable a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0566b-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="0566b-107">Synopsis</span></span>

```dotnetcli
dotnet nuget disable source <NAME> [--configfile <FILE>]

dotnet nuget disable source -h|--help
```

## <a name="description"></a><span data-ttu-id="0566b-108">Opis</span><span class="sxs-lookup"><span data-stu-id="0566b-108">Description</span></span>

<span data-ttu-id="0566b-109">Polecenie `dotnet nuget disable source` wyłącza istniejące źródło w plikach konfiguracyjnych NuGet.</span><span class="sxs-lookup"><span data-stu-id="0566b-109">The `dotnet nuget disable source` command disables an existing source in your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="0566b-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="0566b-110">Arguments</span></span>

- **`NAME`**

  <span data-ttu-id="0566b-111">Nazwa źródła.</span><span class="sxs-lookup"><span data-stu-id="0566b-111">Name of the source.</span></span>

## <a name="options"></a><span data-ttu-id="0566b-112">Opcje</span><span class="sxs-lookup"><span data-stu-id="0566b-112">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="0566b-113">Plik konfiguracyjny NuGet.</span><span class="sxs-lookup"><span data-stu-id="0566b-113">The NuGet configuration file.</span></span> <span data-ttu-id="0566b-114">Jeśli zostanie określony, będą używane tylko ustawienia z tego pliku.</span><span class="sxs-lookup"><span data-stu-id="0566b-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="0566b-115">Jeśli nie zostanie określona, zostanie użyta hierarchia plików konfiguracyjnych z bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="0566b-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="0566b-116">Aby uzyskać więcej informacji, zobacz [typowe konfiguracje NuGet](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="0566b-116">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

## <a name="examples"></a><span data-ttu-id="0566b-117">Przykłady</span><span class="sxs-lookup"><span data-stu-id="0566b-117">Examples</span></span>

- <span data-ttu-id="0566b-118">Wyłącz źródło o `mySource`nazwie :</span><span class="sxs-lookup"><span data-stu-id="0566b-118">Disable a source with name of `mySource`:</span></span>

  ```dotnetcli
  dotnet nuget disable source mySource
  ```

## <a name="see-also"></a><span data-ttu-id="0566b-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0566b-119">See also</span></span>

- [<span data-ttu-id="0566b-120">Sekcje źródła pakietów w plikach NuGet.config</span><span class="sxs-lookup"><span data-stu-id="0566b-120">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="0566b-121">sources, polecenie (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="0566b-121">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
