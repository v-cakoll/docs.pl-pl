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
# <a name="install-extra-mlnet-dependencies"></a>Instalowanie dodatkowych zależności ML.NET

W większości przypadków we wszystkich systemach operacyjnych instalowanie ML.NET jest tak proste, jak odwoływanie się do odpowiedniego pakietu NuGet.

```bash
dotnet add package Microsoft.ML
```

W niektórych przypadkach istnieją jednak dodatkowe wymagania dotyczące instalacji, szczególnie gdy wymagane są składniki macierzyste. W tym dokumencie opisano wymagania dotyczące instalacji w tych przypadkach. Sekcje są podzielone według `Microsoft.ML.*` określonego pakietu NuGet, który ma dodatkową zależność.

## <a name="microsoftmltimeseries-microsoftmlautoml"></a>Microsoft.ML.TimeSeries, Microsoft.ML.AutoML

Oba te pakiety mają `Microsoft.ML.MKL.Redist`zależność od , `libiomp`który ma zależność od .

### <a name="windows"></a>Windows

Nie są wymagane żadne dodatkowe czynności instalacyjne. Biblioteka jest instalowana po dodaniu pakietu NuGet do projektu.

### <a name="linux"></a>Linux

1. Instalowanie klucza GPG dla repozytorium

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

2. Dodaj repozytorium APT dla MKL

    ```bash
    sudo sh -c 'echo deb https://apt.repos.intel.com/mkl all main > /etc/apt/sources.list.d/intel-mkl.list'
    ```

3. Aktualizuj pakiety

    ```bash
    sudo apt-get update
    ```

4. Instalowanie programu MKL

    ```bash
    sudo apt-get install <COMPONENT>-<VERSION>.<UPDATE>-<BUILD_NUMBER>
    ```

    Przykład:

    ```bash
    sudo apt-get install intel-mkl-64bit-2020.0-088
    ```

    Określić lokalizację`libiomp.so`

    ```bash
    find /opt -name "libiomp5.so"
    ```

    Przykład:

    ```output
    /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_lin/libiomp5.so
    ```

5. Dodaj tę lokalizację do ścieżki biblioteki obciążenia:

    ```bash
    sudo ldconfig /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_li
    ```

### <a name="mac"></a>Mac

1. Zainstaluj bibliotekę za pomocą`Homebrew`

    ```bash
    brew update && brew install https://raw.githubusercontent.com/Homebrew/homebrew-core/f5b1ac99a7fba27c19cee0bc4f036775c889b359/Formula/libomp.rb && brew link libomp --force
    ```
