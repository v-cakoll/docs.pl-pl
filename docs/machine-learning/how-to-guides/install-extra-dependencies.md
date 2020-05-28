---
title: Instalowanie dodatkowych zależności ML.NET
description: Dowiedz się, jak zainstalować wszystkie biblioteki natywne, od których są zależne pakiety ML.NET, ale nie są instalowane z pakietami NuGet
ms.date: 04/02/2020
author: natke
ms.author: nakersha
ms.custom: how-to
ms.openlocfilehash: c744b42b4b95681de7b0cbeaef338cc890708fd8
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008433"
---
# <a name="install-extra-mlnet-dependencies"></a><span data-ttu-id="711ee-103">Instalowanie dodatkowych zależności ML.NET</span><span class="sxs-lookup"><span data-stu-id="711ee-103">Install extra ML.NET dependencies</span></span>

<span data-ttu-id="711ee-104">W większości przypadków w przypadku wszystkich systemów operacyjnych Instalowanie ML.NET jest proste, ponieważ odwołuje się do odpowiedniego pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="711ee-104">In most cases, on all operating systems, installing ML.NET is as simple as referencing the appropriate NuGet package.</span></span>

```dotnetcli
dotnet add package Microsoft.ML
```

<span data-ttu-id="711ee-105">W niektórych przypadkach istnieją dodatkowe wymagania dotyczące instalacji, zwłaszcza w przypadku, gdy wymagane są składniki natywne.</span><span class="sxs-lookup"><span data-stu-id="711ee-105">In some cases though, there are additional installation requirements, particularly when native components are required.</span></span> <span data-ttu-id="711ee-106">W tym dokumencie opisano wymagania dotyczące instalacji tych przypadków.</span><span class="sxs-lookup"><span data-stu-id="711ee-106">This document describes the installation requirements for those cases.</span></span> <span data-ttu-id="711ee-107">Sekcje są podzielone według określonego `Microsoft.ML.*` pakietu NuGet, który ma dodatkową zależność.</span><span class="sxs-lookup"><span data-stu-id="711ee-107">The sections are broken down by the specific `Microsoft.ML.*` NuGet package that has the additional dependency.</span></span>

## <a name="microsoftmltimeseries-microsoftmlautoml"></a><span data-ttu-id="711ee-108">Microsoft. ML. szeregów czasowych, Microsoft. ML. AutoML</span><span class="sxs-lookup"><span data-stu-id="711ee-108">Microsoft.ML.TimeSeries, Microsoft.ML.AutoML</span></span>

<span data-ttu-id="711ee-109">Oba te pakiety mają zależność od `Microsoft.ML.MKL.Redist` , która ma zależność od `libiomp` .</span><span class="sxs-lookup"><span data-stu-id="711ee-109">Both of these packages have a dependency on `Microsoft.ML.MKL.Redist`, which has a dependency on `libiomp`.</span></span>

### <a name="windows"></a><span data-ttu-id="711ee-110">Windows</span><span class="sxs-lookup"><span data-stu-id="711ee-110">Windows</span></span>

<span data-ttu-id="711ee-111">Nie są wymagane żadne dodatkowe kroki instalacji.</span><span class="sxs-lookup"><span data-stu-id="711ee-111">No extra installation steps required.</span></span> <span data-ttu-id="711ee-112">Biblioteka jest instalowana, gdy pakiet NuGet zostanie dodany do projektu.</span><span class="sxs-lookup"><span data-stu-id="711ee-112">The library is installed when the NuGet package is added to the project.</span></span>

### <a name="linux"></a><span data-ttu-id="711ee-113">Linux</span><span class="sxs-lookup"><span data-stu-id="711ee-113">Linux</span></span>

1. <span data-ttu-id="711ee-114">Instalowanie klucza GPG dla repozytorium</span><span class="sxs-lookup"><span data-stu-id="711ee-114">Install the GPG key for the repository</span></span>

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

2. <span data-ttu-id="711ee-115">Dodawanie repozytorium APT dla MKL</span><span class="sxs-lookup"><span data-stu-id="711ee-115">Add the APT Repository for MKL</span></span>

    ```bash
    sudo sh -c 'echo deb https://apt.repos.intel.com/mkl all main > /etc/apt/sources.list.d/intel-mkl.list'
    ```

3. <span data-ttu-id="711ee-116">Pakiety aktualizacji</span><span class="sxs-lookup"><span data-stu-id="711ee-116">Update packages</span></span>

    ```bash
    sudo apt-get update
    ```

4. <span data-ttu-id="711ee-117">Zainstaluj MKL</span><span class="sxs-lookup"><span data-stu-id="711ee-117">Install MKL</span></span>

    ```bash
    sudo apt-get install <COMPONENT>-<VERSION>.<UPDATE>-<BUILD_NUMBER>
    ```

    <span data-ttu-id="711ee-118">Przykład:</span><span class="sxs-lookup"><span data-stu-id="711ee-118">For example:</span></span>

    ```bash
    sudo apt-get install intel-mkl-64bit-2020.0-088
    ```

    <span data-ttu-id="711ee-119">Określ lokalizację`libiomp.so`</span><span class="sxs-lookup"><span data-stu-id="711ee-119">Determine the location of `libiomp.so`</span></span>

    ```bash
    find /opt -name "libiomp5.so"
    ```

    <span data-ttu-id="711ee-120">Przykład:</span><span class="sxs-lookup"><span data-stu-id="711ee-120">For example:</span></span>

    ```output
    /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_lin/libiomp5.so
    ```

5. <span data-ttu-id="711ee-121">Dodaj tę lokalizację do ścieżki biblioteki ładowania:</span><span class="sxs-lookup"><span data-stu-id="711ee-121">Add this location to the load library path:</span></span>

    ```bash
    sudo ldconfig /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_lin
    ```

### <a name="mac"></a><span data-ttu-id="711ee-122">Mac</span><span class="sxs-lookup"><span data-stu-id="711ee-122">Mac</span></span>

1. <span data-ttu-id="711ee-123">Zainstaluj bibliotekę z`Homebrew`</span><span class="sxs-lookup"><span data-stu-id="711ee-123">Install the library with `Homebrew`</span></span>

    ```bash
    brew update && brew install https://raw.githubusercontent.com/Homebrew/homebrew-core/f5b1ac99a7fba27c19cee0bc4f036775c889b359/Formula/libomp.rb && brew link libomp --force
    ```
