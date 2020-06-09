---
ms.openlocfilehash: 5e77b7bd73c09e061a94a29703cf5286814d1ebb
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602916"
---

[<span data-ttu-id="ab838-101">Program .NET Core jest dostępny w magazynie Snap.</span><span class="sxs-lookup"><span data-stu-id="ab838-101">.NET Core is available from the Snap Store.</span></span>](https://snapcraft.io/dotnet-sdk)

<span data-ttu-id="ab838-102">Przyciąganie to pakiet aplikacji i jej zależności, które działają bez modyfikacji dla wielu różnych dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="ab838-102">A snap is a bundle of an app and its dependencies that works without modification across many different Linux distributions.</span></span> <span data-ttu-id="ab838-103">Przyciąganie jest wykrywalne i instalowane z magazynu Snap.</span><span class="sxs-lookup"><span data-stu-id="ab838-103">Snaps are discoverable and installable from the Snap Store.</span></span> <span data-ttu-id="ab838-104">Aby uzyskać więcej informacji na temat przyciągania, zobacz [wprowadzenie do przyciągania](https://snapcraft.io/docs/getting-started).</span><span class="sxs-lookup"><span data-stu-id="ab838-104">For more information about Snap, see [Getting started with Snap](https://snapcraft.io/docs/getting-started).</span></span>

<span data-ttu-id="ab838-105">Tylko obsługiwane wersje programu .NET Core są dostępne za poorednictwem przyciągania.</span><span class="sxs-lookup"><span data-stu-id="ab838-105">Only supported versions of .NET Core are available through Snap.</span></span>

### <a name="install-the-sdk"></a><span data-ttu-id="ab838-106">Instalacja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="ab838-106">Install the SDK</span></span>

<span data-ttu-id="ab838-107">Pakiety przyciągania dla zestaw .NET Core SDK są publikowane w ramach tego samego identyfikatora: `dotnet-sdk` .</span><span class="sxs-lookup"><span data-stu-id="ab838-107">Snap packages for .NET Core SDK are all published under the same identifier: `dotnet-sdk`.</span></span> <span data-ttu-id="ab838-108">Określoną wersję zestawu SDK można zainstalować, określając kanał.</span><span class="sxs-lookup"><span data-stu-id="ab838-108">A specific version of the SDK can be installed by specifying the channel.</span></span> <span data-ttu-id="ab838-109">Zestaw SDK obejmuje środowisko uruchomieniowe współreagujące.</span><span class="sxs-lookup"><span data-stu-id="ab838-109">The SDK includes the coresponding runtime.</span></span> <span data-ttu-id="ab838-110">W poniższej tabeli wymieniono kanały:</span><span class="sxs-lookup"><span data-stu-id="ab838-110">The following table list the channels:</span></span>

| <span data-ttu-id="ab838-111">Wersja platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="ab838-111">.NET Core version</span></span> | <span data-ttu-id="ab838-112">Pakiet przyciągania</span><span class="sxs-lookup"><span data-stu-id="ab838-112">Snap package</span></span>             |
|-------------------|--------------------------|
| <span data-ttu-id="ab838-113">3,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="ab838-113">3.1 (LTS)</span></span>         | <span data-ttu-id="ab838-114">`3.1` lub `latest/stable`</span><span class="sxs-lookup"><span data-stu-id="ab838-114">`3.1` or `latest/stable`</span></span> |
| <span data-ttu-id="ab838-115">2,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="ab838-115">2.1 (LTS)</span></span>         | `2.1`                    |
| <span data-ttu-id="ab838-116">.NET 5,0 — wersja zapoznawcza</span><span class="sxs-lookup"><span data-stu-id="ab838-116">.NET 5.0 preview</span></span>  | `5.0/beta`               |

<span data-ttu-id="ab838-117">Użyj `snap install` polecenia, aby zainstalować pakiet przyciągania zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="ab838-117">Use the `snap install` command to install a .NET Core SDK snap package.</span></span> <span data-ttu-id="ab838-118">Użyj `--channel` parametru, aby wskazać wersję do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="ab838-118">Use the `--channel` parameter to indicate which version to install.</span></span> <span data-ttu-id="ab838-119">Jeśli ten parametr zostanie pominięty, `latest/stable` jest używany.</span><span class="sxs-lookup"><span data-stu-id="ab838-119">If this parameter is omitted, `latest/stable` is used.</span></span> <span data-ttu-id="ab838-120">W tym przykładzie `3.1` określono:</span><span class="sxs-lookup"><span data-stu-id="ab838-120">In this example, `3.1` is specified:</span></span>

```bash
sudo snap install dotnet-sdk --classic --channel=3.1
```

<span data-ttu-id="ab838-121">Następnie zarejestruj `dotnet` polecenie dla systemu przy użyciu `snap alias` polecenia:</span><span class="sxs-lookup"><span data-stu-id="ab838-121">Next, register the `dotnet` command for the system with the `snap alias` command:</span></span>

```bash
sudo snap alias dotnet-sdk.dotnet dotnet
```

<span data-ttu-id="ab838-122">To polecenie jest sformatowane jako: `sudo snap alias {package}.{command} {alias}` .</span><span class="sxs-lookup"><span data-stu-id="ab838-122">This command is formatted as: `sudo snap alias {package}.{command} {alias}`.</span></span> <span data-ttu-id="ab838-123">Możesz wybrać dowolną `{alias}` nazwę.</span><span class="sxs-lookup"><span data-stu-id="ab838-123">You can choose any `{alias}` name you would like.</span></span> <span data-ttu-id="ab838-124">Można na przykład nazwać polecenie po zainstalowaniu określonej wersji przez przyciąganie: `sudo snap alias dotnet-sdk.dotnet dotnet31` .</span><span class="sxs-lookup"><span data-stu-id="ab838-124">For example, you could name the command after the specific version installed by snap: `sudo snap alias dotnet-sdk.dotnet dotnet31`.</span></span> <span data-ttu-id="ab838-125">Korzystając z polecenia `dotnet31` , należy wywołać tę konkretną wersję platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="ab838-125">When you use the command `dotnet31`, you'll invoke this specific version of .NET.</span></span> <span data-ttu-id="ab838-126">Ale jest to niezgodne z większością samouczków i przykładów, ponieważ oczekuje, że `dotnet` polecenie jest dostępne.</span><span class="sxs-lookup"><span data-stu-id="ab838-126">But this is incompatible with most tutorials and examples as they expect a `dotnet` command to be available.</span></span>

### <a name="install-the-runtime"></a><span data-ttu-id="ab838-127">Instalowanie środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="ab838-127">Install the runtime</span></span>

<span data-ttu-id="ab838-128">Pakiety przyciągania dla środowiska uruchomieniowego .NET Core są publikowane w ramach własnego identyfikatora pakietu.</span><span class="sxs-lookup"><span data-stu-id="ab838-128">Snap packages for .NET Core Runtime are each published under their own package identifier.</span></span> <span data-ttu-id="ab838-129">W poniższej tabeli wymieniono identyfikatory pakietów:</span><span class="sxs-lookup"><span data-stu-id="ab838-129">The following table lists the package identifiers:</span></span>

| <span data-ttu-id="ab838-130">Wersja platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="ab838-130">.NET Core version</span></span> | <span data-ttu-id="ab838-131">Pakiet przyciągania</span><span class="sxs-lookup"><span data-stu-id="ab838-131">Snap package</span></span>        |
|-------------------|---------------------|
| <span data-ttu-id="ab838-132">3,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="ab838-132">3.1 (LTS)</span></span>         | `dotnet-runtime-31` |
| <span data-ttu-id="ab838-133">3.0</span><span class="sxs-lookup"><span data-stu-id="ab838-133">3.0</span></span>               | `dotnet-runtime-30` |
| <span data-ttu-id="ab838-134">2.2</span><span class="sxs-lookup"><span data-stu-id="ab838-134">2.2</span></span>               | `dotnet-runtime-22` |
| <span data-ttu-id="ab838-135">2,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="ab838-135">2.1 (LTS)</span></span>         | `dotnet-runtime-21` |

<span data-ttu-id="ab838-136">Użyj `snap install` polecenia, aby zainstalować pakiet przyciągania środowiska uruchomieniowego platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ab838-136">Use the `snap install` command to install a .NET Core Runtime snap package.</span></span> <span data-ttu-id="ab838-137">W tym przykładzie jest zainstalowany program .NET Core 3,1:</span><span class="sxs-lookup"><span data-stu-id="ab838-137">In this example, .NET Core 3.1 is installed:</span></span>

```bash
sudo snap install dotnet-runtime-31 --classic
```

<span data-ttu-id="ab838-138">Następnie zarejestruj `dotnet` polecenie dla systemu przy użyciu `snap alias` polecenia:</span><span class="sxs-lookup"><span data-stu-id="ab838-138">Next, register the `dotnet` command for the system with the `snap alias` command:</span></span>

```bash
sudo snap alias dotnet-runtime-31.dotnet dotnet
```

<span data-ttu-id="ab838-139">To polecenie jest sformatowane jako: `sudo snap alias {package}.{command} {alias}` .</span><span class="sxs-lookup"><span data-stu-id="ab838-139">This command is formatted as: `sudo snap alias {package}.{command} {alias}`.</span></span> <span data-ttu-id="ab838-140">Możesz wybrać dowolną `{alias}` nazwę.</span><span class="sxs-lookup"><span data-stu-id="ab838-140">You can choose any `{alias}` name you would like.</span></span> <span data-ttu-id="ab838-141">Można na przykład nazwać polecenie po zainstalowaniu określonej wersji przez przyciąganie: `sudo snap alias dotnet-runtime-31.dotnet dotnet31` .</span><span class="sxs-lookup"><span data-stu-id="ab838-141">For example, you could name the command after the specific version installed by snap: `sudo snap alias dotnet-runtime-31.dotnet dotnet31`.</span></span> <span data-ttu-id="ab838-142">Korzystając z polecenia `dotnet31` , należy wywołać tę konkretną wersję platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="ab838-142">When you use the command `dotnet31`, you'll invoke this specific version of .NET.</span></span> <span data-ttu-id="ab838-143">Ale jest to niezgodne z większością samouczków i przykładów, ponieważ oczekuje, że `dotnet` polecenie jest dostępne.</span><span class="sxs-lookup"><span data-stu-id="ab838-143">But this is incompatible with most tutorials and examples as they expect a `dotnet` command to be available.</span></span>

### <a name="ssl-certificate-errors"></a><span data-ttu-id="ab838-144">Błędy certyfikatów SSL</span><span class="sxs-lookup"><span data-stu-id="ab838-144">SSL Certificate errors</span></span>

<span data-ttu-id="ab838-145">Po zainstalowaniu programu .NET za pośrednictwem przyciągania możliwe jest, że na niektórych dystrybucje nie można odnaleźć certyfikatów protokołu SSL platformy .NET i może zostać wyświetlony błąd podobny do poniższego `restore` :</span><span class="sxs-lookup"><span data-stu-id="ab838-145">When .NET is installed through Snap, it's possible that on some distros the .NET SSL certificates may not be found and you may receive an error similar to the following during `restore`:</span></span>

```bash
Processing post-creation actions...
Running 'dotnet restore' on /home/myhome/test/test.csproj...
  Restoring packages for /home/myhome/test/test.csproj...
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error : Unable to load the service index for source https://api.nuget.org/v3/index.json. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The SSL connection could not be established, see inner exception. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The remote certificate is invalid according to the validation procedure. [/home/myhome/test/test.csproj]
```

<span data-ttu-id="ab838-146">Aby rozwiązać ten problem, ustaw kilka zmiennych środowisko:</span><span class="sxs-lookup"><span data-stu-id="ab838-146">To resolve this issue, set a few enviornment variables:</span></span>

```bash
export SSL_CERT_FILE=[path-to-certificate-file]
export SSL_CERT_DIR=/dev/null
```

<span data-ttu-id="ab838-147">Lokalizacja certyfikatu zależy od dystrybucji.</span><span class="sxs-lookup"><span data-stu-id="ab838-147">The certificate location will vary by distro.</span></span> <span data-ttu-id="ab838-148">Poniżej znajdują się lokalizacje dystrybucje, w których wystąpił problem.</span><span class="sxs-lookup"><span data-stu-id="ab838-148">Here are the locations for the distros where we have experienced the issue.</span></span>

* <span data-ttu-id="ab838-149">Fedora`/etc/pki/ca-trust/extracted/pem/tls-ca-bundle.pem`</span><span class="sxs-lookup"><span data-stu-id="ab838-149">Fedora - `/etc/pki/ca-trust/extracted/pem/tls-ca-bundle.pem`</span></span>
* <span data-ttu-id="ab838-150">OpenSUSE`/etc/ssl/ca-bundle.pem`</span><span class="sxs-lookup"><span data-stu-id="ab838-150">OpenSUSE - `/etc/ssl/ca-bundle.pem`</span></span>
* <span data-ttu-id="ab838-151">Solus -`/etc/ssl/certs/ca-certificates.crt`</span><span class="sxs-lookup"><span data-stu-id="ab838-151">Solus - `/etc/ssl/certs/ca-certificates.crt`</span></span>
