---
ms.openlocfilehash: db89539982c1afe0df374027d54826f3265f0fee
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84603014"
---

### <a name="install-the-sdk"></a><span data-ttu-id="24ffb-101">Instalacja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="24ffb-101">Install the SDK</span></span>

<span data-ttu-id="24ffb-102">Zestaw .NET Core SDK pozwala na tworzenie aplikacji przy użyciu platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="24ffb-102">The .NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="24ffb-103">Aby zainstalować zestaw .NET Core SDK, uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="24ffb-103">To install the .NET Core SDK, run the following commands.</span></span>

```bash
sudo zypper install dotnet-sdk-3.1
```

### <a name="install-the-runtime"></a><span data-ttu-id="24ffb-104">Instalowanie środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="24ffb-104">Install the runtime</span></span>

<span data-ttu-id="24ffb-105">Środowisko uruchomieniowe programu .NET Core umożliwia uruchamianie aplikacji, które zostały wykonane przy użyciu platformy .NET Core, które nie zawierały środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="24ffb-105">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="24ffb-106">Poniższe polecenia instalują środowisko uruchomieniowe ASP.NET Core, które jest najbardziej zgodnym środowiskiem uruchomieniowym dla platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="24ffb-106">The commands below install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="24ffb-107">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="24ffb-107">In your terminal, run the following commands.</span></span>

```bash
sudo zypper install aspnetcore-runtime-3.1
```

<span data-ttu-id="24ffb-108">Jako alternatywę dla środowiska uruchomieniowego ASP.NET Core można zainstalować środowisko uruchomieniowe programu .NET Core, które nie obejmuje ASP.NET Core Support: Zastąp `aspnetcore-runtime-2.1` w powyższym poleceniu poleceniem `dotnet-runtime-3.1` .</span><span class="sxs-lookup"><span data-stu-id="24ffb-108">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime that doesn't include ASP.NET Core support: replace `aspnetcore-runtime-2.1` in the command above with `dotnet-runtime-3.1`.</span></span>

```bash
sudo zypper install dotnet-runtime-3.1
```
