---
title: Instalowanie dodatkowych zależności ML.NET
description: Dowiedz się, jak zainstalować wszystkie biblioteki macierzyste, od których ML.NET pakiety są zależne, ale nie są instalowane z pakietami NuGet
ms.date: 04/02/2020
author: natke
ms.author: nakersha
ms.custom: how-to
ms.openlocfilehash: 0b870542706c065295d48205b7780e568e267ab6
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888303"
---
# <a name="install-extra-mlnet-dependencies"></a><span data-ttu-id="a802a-103">Instalowanie dodatkowych zależności ML.NET</span><span class="sxs-lookup"><span data-stu-id="a802a-103">Install extra ML.NET dependencies</span></span>

<span data-ttu-id="a802a-104">W większości przypadków we wszystkich systemach operacyjnych instalowanie ML.NET jest tak proste, jak odwoływanie się do odpowiedniego pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="a802a-104">In most cases, on all operating systems, installing ML.NET is as simple as referencing the appropriate NuGet package.</span></span>

```bash
dotnet add package Microsoft.ML
```

<span data-ttu-id="a802a-105">W niektórych przypadkach istnieją jednak dodatkowe wymagania dotyczące instalacji, szczególnie gdy wymagane są składniki macierzyste.</span><span class="sxs-lookup"><span data-stu-id="a802a-105">In some cases though, there are additional installation requirements, particularly when native components are required.</span></span> <span data-ttu-id="a802a-106">W tym dokumencie opisano wymagania dotyczące instalacji w tych przypadkach.</span><span class="sxs-lookup"><span data-stu-id="a802a-106">This document describes the installation requirements for those cases.</span></span> <span data-ttu-id="a802a-107">Sekcje są podzielone według `Microsoft.ML.*` określonego pakietu NuGet, który ma dodatkową zależność.</span><span class="sxs-lookup"><span data-stu-id="a802a-107">The sections are broken down by the specific `Microsoft.ML.*` NuGet package that has the additional dependency.</span></span>

## <a name="microsoftmltimeseries-microsoftmlautoml"></a><span data-ttu-id="a802a-108">Microsoft.ML.TimeSeries, Microsoft.ML.AutoML</span><span class="sxs-lookup"><span data-stu-id="a802a-108">Microsoft.ML.TimeSeries, Microsoft.ML.AutoML</span></span>

<span data-ttu-id="a802a-109">Oba te pakiety mają `Microsoft.ML.MKL.Redist`zależność od , `libiomp`który ma zależność od .</span><span class="sxs-lookup"><span data-stu-id="a802a-109">Both of these packages have a dependency on `Microsoft.ML.MKL.Redist`, which has a dependency on `libiomp`.</span></span>

### <a name="windows"></a><span data-ttu-id="a802a-110">Windows</span><span class="sxs-lookup"><span data-stu-id="a802a-110">Windows</span></span>

<span data-ttu-id="a802a-111">Nie są wymagane żadne dodatkowe czynności instalacyjne.</span><span class="sxs-lookup"><span data-stu-id="a802a-111">No extra installation steps required.</span></span> <span data-ttu-id="a802a-112">Biblioteka jest instalowana po dodaniu pakietu NuGet do projektu.</span><span class="sxs-lookup"><span data-stu-id="a802a-112">The library is installed when the NuGet package is added to the project.</span></span>

### <a name="linux"></a><span data-ttu-id="a802a-113">Linux</span><span class="sxs-lookup"><span data-stu-id="a802a-113">Linux</span></span>

1. <span data-ttu-id="a802a-114">Instalowanie klucza GPG dla repozytorium</span><span class="sxs-lookup"><span data-stu-id="a802a-114">Install the GPG key for the repository</span></span>

    ```bash
    sudo bash
    # <type your user password when prompted.  this will put you in a root shell>
    # cd to /tmp where this shell has write permission
    cd /tmp
    # now get the key:
    wget https://apt.repos.intel.com/intel-gpg-keys/GPG-PUB-KEY-INTEL-SW-PRODUCTS-2019.PUB
    # now install that key
    apt-key add GPG-PUB-KEY-INTEL-SW-PRODUCTS-2019.PUB
    # now remove the public key file exit the root shell
    rm GPG-PUB-KEY-INTEL-SW-PRODUCTS-2019.PUB
    exit
    ```

2. <span data-ttu-id="a802a-115">Dodaj repozytorium APT dla MKL</span><span class="sxs-lookup"><span data-stu-id="a802a-115">Add the APT Repository for MKL</span></span>

    ```bash
    sudo sh -c 'echo deb https://apt.repos.intel.com/mkl all main > /etc/apt/sources.list.d/intel-mkl.list'
    ```

3. <span data-ttu-id="a802a-116">Aktualizuj pakiety</span><span class="sxs-lookup"><span data-stu-id="a802a-116">Update packages</span></span>

    ```bash
    sudo apt-get update
    ```

4. <span data-ttu-id="a802a-117">Instalowanie programu MKL</span><span class="sxs-lookup"><span data-stu-id="a802a-117">Install MKL</span></span>

    ```bash
    sudo apt-get install <COMPONENT>-<VERSION>.<UPDATE>-<BUILD_NUMBER>
    ```

    <span data-ttu-id="a802a-118">Przykład:</span><span class="sxs-lookup"><span data-stu-id="a802a-118">For example:</span></span>

    ```bash
    sudo apt-get install intel-mkl-64bit-2020.0-088
    ```

    <span data-ttu-id="a802a-119">Określić lokalizację`libiomp.so`</span><span class="sxs-lookup"><span data-stu-id="a802a-119">Determine the location of `libiomp.so`</span></span>

    ```bash
    find /opt -name "libiomp5.so"
    ```

    <span data-ttu-id="a802a-120">Przykład:</span><span class="sxs-lookup"><span data-stu-id="a802a-120">For example:</span></span>

    ```output
    /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_lin/libiomp5.so
    ```

5. <span data-ttu-id="a802a-121">Dodaj tę lokalizację do ścieżki biblioteki obciążenia:</span><span class="sxs-lookup"><span data-stu-id="a802a-121">Add this location to the load library path:</span></span>

    ```bash
    sudo ldconfig /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_li
    ```

### <a name="mac"></a><span data-ttu-id="a802a-122">Mac</span><span class="sxs-lookup"><span data-stu-id="a802a-122">Mac</span></span>

1. <span data-ttu-id="a802a-123">Zainstaluj bibliotekę za pomocą`Homebrew`</span><span class="sxs-lookup"><span data-stu-id="a802a-123">Install the library with `Homebrew`</span></span>

    ```bash
    brew update && brew install https://raw.githubusercontent.com/Homebrew/homebrew-core/f5b1ac99a7fba27c19cee0bc4f036775c889b359/Formula/libomp.rb && brew link libomp --force
    ```
