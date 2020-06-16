---
ms.openlocfilehash: fb78e1439a680a8dbb9fc0eb8afdeee3efef7ead
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768403"
---

<span data-ttu-id="b1678-101">[Skrypty dotnet-Install](../../tools/dotnet-install-script.md) są używane na potrzeby automatyzacji i nieadministracyjnych instalacji **zestawu SDK** i **środowiska uruchomieniowego**.</span><span class="sxs-lookup"><span data-stu-id="b1678-101">The [dotnet-install scripts](../../tools/dotnet-install-script.md) are used for automation and non-admin installs of the **SDK** and **Runtime**.</span></span> <span data-ttu-id="b1678-102">Skrypt można pobrać z programu <https://dot.net/v1/dotnet-install.sh> .</span><span class="sxs-lookup"><span data-stu-id="b1678-102">You can download the script from <https://dot.net/v1/dotnet-install.sh>.</span></span>

<span data-ttu-id="b1678-103">Skrypt domyślnie instaluje najnowszą wersję programu [obsługi długoterminowej (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) zestawu SDK, która jest .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="b1678-103">The script defaults to installing the latest SDK [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="b1678-104">Aby zainstalować bieżącą wersję, która nie może być wersją (LTS), użyj `-c Current` parametru.</span><span class="sxs-lookup"><span data-stu-id="b1678-104">To install the current release, which may not be an (LTS) version, use the `-c Current` parameter.</span></span>

```bash
./dotnet-install.sh -c Current
```

<span data-ttu-id="b1678-105">Aby zainstalować środowisko uruchomieniowe platformy .NET Core zamiast zestawu SDK, użyj `--runtime` parametru.</span><span class="sxs-lookup"><span data-stu-id="b1678-105">To install .NET Core Runtime instead of the SDK, use the `--runtime` parameter.</span></span>

```bash
./dotnet-install.sh -c Current --runtime aspnetcore
```

<span data-ttu-id="b1678-106">Określoną wersję można zainstalować, zmieniając `-c` parametr w celu wskazania określonej wersji.</span><span class="sxs-lookup"><span data-stu-id="b1678-106">You can install a specific version by altering the `-c` parameter to indicate the specific version.</span></span> <span data-ttu-id="b1678-107">Następujące polecenie instaluje zestaw .NET Core SDK 3,1.</span><span class="sxs-lookup"><span data-stu-id="b1678-107">The following command installs .NET Core SDK 3.1.</span></span>

```bash
./dotnet-install.sh -c 3.1
```

<span data-ttu-id="b1678-108">Aby uzyskać więcej informacji, zobacz temat informacje o [skryptach dotnet-Install](../../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="b1678-108">For more information, see [dotnet-install scripts reference](../../tools/dotnet-install-script.md).</span></span>
