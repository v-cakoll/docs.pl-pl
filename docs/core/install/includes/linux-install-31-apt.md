---
ms.openlocfilehash: b6f2af7af77398d5e902aae995590b5dde4cf76a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602909"
---

### <a name="install-the-sdk"></a><span data-ttu-id="ff6e0-101">Instalacja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="ff6e0-101">Install the SDK</span></span>

<span data-ttu-id="ff6e0-102">Zestaw .NET Core SDK umożliwia tworzenie aplikacji przy użyciu platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-102">.NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="ff6e0-103">W przypadku zainstalowania zestaw .NET Core SDK nie trzeba instalować odpowiedniego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-103">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="ff6e0-104">Aby zainstalować zestaw .NET Core SDK, uruchom następujące polecenia:</span><span class="sxs-lookup"><span data-stu-id="ff6e0-104">To install .NET Core SDK, run the following commands:</span></span>

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y dotnet-sdk-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="ff6e0-105">Jeśli zostanie wyświetlony komunikat o błędzie podobny do sytuacji, w której **nie można znaleźć pakietu dotnet-SDK-3,1**, zobacz sekcję [Rozwiązywanie problemów z apt](#apt-troubleshooting) .</span><span class="sxs-lookup"><span data-stu-id="ff6e0-105">If you receive an error message similar to **Unable to locate package dotnet-sdk-3.1**, see the [APT troubleshooting](#apt-troubleshooting) section.</span></span>

### <a name="install-the-runtime"></a><span data-ttu-id="ff6e0-106">Instalowanie środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="ff6e0-106">Install the runtime</span></span>

<span data-ttu-id="ff6e0-107">Środowisko uruchomieniowe programu .NET Core umożliwia uruchamianie aplikacji, które zostały wykonane przy użyciu platformy .NET Core, które nie zawierały środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-107">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="ff6e0-108">Poniższe polecenia instalują środowisko uruchomieniowe ASP.NET Core, które jest najbardziej zgodnym środowiskiem uruchomieniowym dla platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-108">The commands below install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="ff6e0-109">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-109">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="ff6e0-110">Jeśli zostanie wyświetlony komunikat o błędzie podobny do sytuacji, w której **nie można znaleźć pakietu aspnetcore-Runtime-3,1**, zobacz sekcję [Rozwiązywanie problemów z apt](#apt-troubleshooting) .</span><span class="sxs-lookup"><span data-stu-id="ff6e0-110">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-3.1**, see the [APT troubleshooting](#apt-troubleshooting) section.</span></span>

<span data-ttu-id="ff6e0-111">Jako alternatywę dla środowiska uruchomieniowego ASP.NET Core można zainstalować środowisko uruchomieniowe programu .NET Core, które nie obejmuje ASP.NET Core Support: Zastąp `aspnetcore-runtime-3.1` w powyższym poleceniu poleceniem `dotnet-runtime-3.1` .</span><span class="sxs-lookup"><span data-stu-id="ff6e0-111">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime that doesn't include ASP.NET Core support: replace `aspnetcore-runtime-3.1` in the command above with `dotnet-runtime-3.1`.</span></span>

```bash
sudo apt-get install -y dotnet-runtime-3.1
```
