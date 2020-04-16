---
title: dotnet nuget enable source, polecenie
description: Polecenie dotnet nuget enable source umożliwia istniejące źródło w plikach konfiguracyjnych NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: 38fb5917361bd7952fef9c31ed897fb81f005155
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463559"
---
# <a name="dotnet-nuget-enable-source"></a><span data-ttu-id="54e98-103">dotnet nuget enable source</span><span class="sxs-lookup"><span data-stu-id="54e98-103">dotnet nuget enable source</span></span>

<span data-ttu-id="54e98-104">**Ten artykuł dotyczy:** ✔️.NET Core 3.1.200 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="54e98-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="54e98-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="54e98-105">Name</span></span>

<span data-ttu-id="54e98-106">`dotnet nuget enable source`- Włącz źródło NuGet.</span><span class="sxs-lookup"><span data-stu-id="54e98-106">`dotnet nuget enable source` - Enable a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="54e98-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="54e98-107">Synopsis</span></span>

```dotnetcli
dotnet nuget enable source <NAME> [--configfile <FILE>]

dotnet nuget enable source -h|--help
```

## <a name="description"></a><span data-ttu-id="54e98-108">Opis</span><span class="sxs-lookup"><span data-stu-id="54e98-108">Description</span></span>

<span data-ttu-id="54e98-109">Polecenie `dotnet nuget enable source` włącza istniejące źródło w plikach konfiguracyjnych NuGet.</span><span class="sxs-lookup"><span data-stu-id="54e98-109">The `dotnet nuget enable source` command enables an existing source in your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="54e98-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="54e98-110">Arguments</span></span>

- **`NAME`**

  <span data-ttu-id="54e98-111">Nazwa źródła.</span><span class="sxs-lookup"><span data-stu-id="54e98-111">Name of the source.</span></span>

## <a name="options"></a><span data-ttu-id="54e98-112">Opcje</span><span class="sxs-lookup"><span data-stu-id="54e98-112">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="54e98-113">Plik konfiguracyjny NuGet.</span><span class="sxs-lookup"><span data-stu-id="54e98-113">The NuGet configuration file.</span></span> <span data-ttu-id="54e98-114">Jeśli zostanie określony, będą używane tylko ustawienia z tego pliku.</span><span class="sxs-lookup"><span data-stu-id="54e98-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="54e98-115">Jeśli nie zostanie określona, zostanie użyta hierarchia plików konfiguracyjnych z bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="54e98-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="54e98-116">Aby uzyskać więcej informacji, zobacz [typowe konfiguracje NuGet](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="54e98-116">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

## <a name="examples"></a><span data-ttu-id="54e98-117">Przykłady</span><span class="sxs-lookup"><span data-stu-id="54e98-117">Examples</span></span>

- <span data-ttu-id="54e98-118">Włącz źródło o `mySource`nazwie :</span><span class="sxs-lookup"><span data-stu-id="54e98-118">Enable a source with name of `mySource`:</span></span>

  ```dotnetcli
  dotnet nuget enable source mySource
  ```

## <a name="see-also"></a><span data-ttu-id="54e98-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="54e98-119">See also</span></span>

- [<span data-ttu-id="54e98-120">Sekcje źródła pakietów w plikach NuGet.config</span><span class="sxs-lookup"><span data-stu-id="54e98-120">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="54e98-121">sources, polecenie (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="54e98-121">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
