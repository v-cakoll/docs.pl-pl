---
ms.openlocfilehash: 0d29407896145bc3b2ed8284c839ae8f2f0521b2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602951"
---

<span data-ttu-id="2b3a8-101">[Skrypty programu dotnet-Install](../../tools/dotnet-install-script.md) są używane na potrzeby automatyzacji i instalacji nienależących do administratora **zestawu SDK**.</span><span class="sxs-lookup"><span data-stu-id="2b3a8-101">The [dotnet-install scripts](../../tools/dotnet-install-script.md) are used for automation and non-admin installs of the **SDK**.</span></span> <span data-ttu-id="2b3a8-102">Skrypt można pobrać z programu <https://dot.net/v1/dotnet-install.sh> .</span><span class="sxs-lookup"><span data-stu-id="2b3a8-102">You can download the script from <https://dot.net/v1/dotnet-install.sh>.</span></span>

<span data-ttu-id="2b3a8-103">Skrypt domyślnie instaluje najnowszą [LTS](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) wersję, która jest platformą .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="2b3a8-103">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="2b3a8-104">Aby zainstalować bieżącą wersję, która nie może być wersją (LTS), użyj `-c Current` parametru.</span><span class="sxs-lookup"><span data-stu-id="2b3a8-104">To install the current release, which may not be an (LTS) version, use the `-c Current` parameter.</span></span>

```bash
./dotnet-install.sh -c Current
```

<span data-ttu-id="2b3a8-105">Aby zainstalować środowisko uruchomieniowe platformy .NET Core zamiast zestawu SDK, użyj `--runtime` parametru.</span><span class="sxs-lookup"><span data-stu-id="2b3a8-105">To install .NET Core Runtime instead of the SDK, use the `--runtime` parameter.</span></span>

```bash
./dotnet-install.sh -c Current --runtime
```

<span data-ttu-id="2b3a8-106">Określoną wersję można zainstalować, zmieniając `-c` parametr w celu wskazania określonej wersji.</span><span class="sxs-lookup"><span data-stu-id="2b3a8-106">You can install a specific version by altering the `-c` parameter to indicate the specific version.</span></span> <span data-ttu-id="2b3a8-107">Następujące polecenie instaluje zestaw .NET Core SDK 3,1.</span><span class="sxs-lookup"><span data-stu-id="2b3a8-107">The following command installs .NET Core SDK 3.1.</span></span>

```bash
./dotnet-install.sh -c 3.1
```

<span data-ttu-id="2b3a8-108">Aby uzyskać więcej informacji, zobacz temat informacje o [skryptach dotnet-Install](../../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="2b3a8-108">For more information, see [dotnet-install scripts reference](../../tools/dotnet-install-script.md).</span></span>
