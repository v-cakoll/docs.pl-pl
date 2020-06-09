---
ms.openlocfilehash: 7d398df060c031ae891218b82a2712d74f4c33b7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602986"
---

<span data-ttu-id="e899b-101">Jeśli zostanie wyświetlony komunikat o błędzie podobny do następującego: **nie można zlokalizować pakietu {servicecore-Package}**, uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="e899b-101">If you receive an error message similar to **Unable to locate package {netcore-package}**, run the following commands.</span></span>

<span data-ttu-id="e899b-102">W poniższym zestawie poleceń znajdują się dwa symbole zastępcze.</span><span class="sxs-lookup"><span data-stu-id="e899b-102">There are two placeholders in the following set of commands.</span></span>

- `{dotnet-package}`\
<span data-ttu-id="e899b-103">Reprezentuje pakiet .NET Core, który instalujesz, na przykład `aspnetcore-runtime-3.1` .</span><span class="sxs-lookup"><span data-stu-id="e899b-103">This represents the .NET Core package you're installing, such as `aspnetcore-runtime-3.1`.</span></span> <span data-ttu-id="e899b-104">Ta wartość jest używana w `sudo apt-get install` poniższym poleceniu.</span><span class="sxs-lookup"><span data-stu-id="e899b-104">This is used in the `sudo apt-get install` command below.</span></span>

- `{os-version}`\
<span data-ttu-id="e899b-105">Oznacza to, że wersja systemu Linux jest włączona.</span><span class="sxs-lookup"><span data-stu-id="e899b-105">This represents the Linux version you are on.</span></span> <span data-ttu-id="e899b-106">Ta wartość jest używana w `wget` poniższym poleceniu.</span><span class="sxs-lookup"><span data-stu-id="e899b-106">This is used in the `wget` command below.</span></span>

<span data-ttu-id="e899b-107">Spróbuj wyczyszczenie listy pakietów:</span><span class="sxs-lookup"><span data-stu-id="e899b-107">Try purging the package list:</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {dotnet-package}
```

<span data-ttu-id="e899b-108">Jeśli to nie zadziała, można uruchomić instalację ręczną przy użyciu następujących poleceń:</span><span class="sxs-lookup"><span data-stu-id="e899b-108">If that doesn't work, you can run a manual install with the following commands:</span></span>
