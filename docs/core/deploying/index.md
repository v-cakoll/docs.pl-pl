---
title: Wdrażanie aplikacji .NET core
description: Wdrażanie aplikacji .NET Core.
keywords: Wdrożenie .NET Core .NET i .NET core
author: rpetrusha
ms.author: ronpet
ms.date: 04/18/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: da7a31a0-8072-4f23-82aa-8a19184cb701
ms.workload:
- dotnetcore
ms.openlocfilehash: 87a70ac246e37c646f9be578a03dda7037cfdd2d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="net-core-application-deployment"></a><span data-ttu-id="aee93-104">Wdrażanie aplikacji .NET core</span><span class="sxs-lookup"><span data-stu-id="aee93-104">.NET Core application deployment</span></span>

<span data-ttu-id="aee93-105">Można tworzyć dwa typy wdrożeń dla aplikacji .NET Core:</span><span class="sxs-lookup"><span data-stu-id="aee93-105">You can create two types of deployments for .NET Core applications:</span></span>

- <span data-ttu-id="aee93-106">Zależne od Framework wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="aee93-106">Framework-dependent deployment.</span></span> <span data-ttu-id="aee93-107">Jak wskazuje nazwę, zależne od framework wdrożenia (stacje) zależy od obecności udostępnionego systemowe wersji platformy .NET Core w systemie docelowym.</span><span class="sxs-lookup"><span data-stu-id="aee93-107">As the name implies, framework-dependent deployment (FDD) relies on the presence of a shared system-wide version of .NET Core on the target system.</span></span> <span data-ttu-id="aee93-108">Ponieważ .NET Core jest już obecny, aplikacji jest również przenosić między instalacji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="aee93-108">Because .NET Core is already present, your app is also portable between installations of .NET Core.</span></span> <span data-ttu-id="aee93-109">Aplikacja zawiera tylko własnego kodu i wszelkie zależności innych firm, które znajdują się poza bibliotek .NET Core.</span><span class="sxs-lookup"><span data-stu-id="aee93-109">Your app contains only its own code and any third-party dependencies that are outside of the .NET Core libraries.</span></span> <span data-ttu-id="aee93-110">Zawiera FDDs *.dll* pliki, które można uruchomić przy użyciu [narzędzie dotnet](../tools/dotnet.md) z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="aee93-110">FDDs contain *.dll* files that can be launched by using the [dotnet utility](../tools/dotnet.md) from the command line.</span></span> <span data-ttu-id="aee93-111">Na przykład `dotnet app.dll` działa aplikacja o nazwie `app`.</span><span class="sxs-lookup"><span data-stu-id="aee93-111">For example, `dotnet app.dll` runs an application named `app`.</span></span>

- <span data-ttu-id="aee93-112">Samodzielne wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="aee93-112">Self-contained deployment.</span></span> <span data-ttu-id="aee93-113">W odróżnieniu od Dyskietki niezależne wdrożenia (SCD) nie zależą od obecności współużytkowanych składników w systemie docelowym.</span><span class="sxs-lookup"><span data-stu-id="aee93-113">Unlike FDD, a self-contained deployment (SCD) doesn't rely on the presence of shared components on the target system.</span></span> <span data-ttu-id="aee93-114">Wszystkie składniki, w tym zarówno do bibliotek .NET Core i środowiska uruchomieniowego .NET Core, są dołączone do aplikacji i odizolowana od innych aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="aee93-114">All components, including both the .NET Core libraries and the .NET Core runtime, are included with the application and are isolated from other .NET Core applications.</span></span> <span data-ttu-id="aee93-115">SCDs obejmują plik wykonywalny (takich jak *app.exe* na platformach systemu Windows dla aplikacji o nazwie `app`), zmieniono nazwę wersji specyficzne dla platformy .NET Core hosta, a *.dll* plików (takich jak *app.dll*), która jest rzeczywista aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aee93-115">SCDs include an executable (such as *app.exe* on Windows platforms for an application named `app`), which is  a renamed version of the platform-specific .NET Core host, and a *.dll* file (such as *app.dll*), which is the actual application.</span></span>

## <a name="framework-dependent-deployments-fdd"></a><span data-ttu-id="aee93-116">Zależne od Framework wdrożeń (stacje)</span><span class="sxs-lookup"><span data-stu-id="aee93-116">Framework-dependent deployments (FDD)</span></span>

<span data-ttu-id="aee93-117">STACJE wdrożeniem tylko aplikacji i zależności innych firm.</span><span class="sxs-lookup"><span data-stu-id="aee93-117">For an FDD, you deploy only your app and any third-party dependencies.</span></span> <span data-ttu-id="aee93-118">Nie trzeba wdrażać .NET Core, ponieważ Twoja aplikacja będzie używać wersji programu .NET Core, która występuje na komputerze docelowym.</span><span class="sxs-lookup"><span data-stu-id="aee93-118">You don't have to deploy .NET Core, since your app will use the version of .NET Core that's present on the target system.</span></span> <span data-ttu-id="aee93-119">Jest to domyślny model wdrażania dla aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="aee93-119">This is the default deployment model for .NET Core apps.</span></span>

### <a name="why-create-a-framework-dependent-deployment"></a><span data-ttu-id="aee93-120">Dlaczego warto utworzyć wdrożenia framework zależnych?</span><span class="sxs-lookup"><span data-stu-id="aee93-120">Why create a framework-dependent deployment?</span></span>

<span data-ttu-id="aee93-121">Wdrażanie Dyskietki ma następujące korzyści:</span><span class="sxs-lookup"><span data-stu-id="aee93-121">Deploying an FDD has a number of advantages:</span></span>

- <span data-ttu-id="aee93-122">Nie trzeba definiować systemów operacyjnych, które aplikacji .NET Core będą działać w wyprzedzeniem.</span><span class="sxs-lookup"><span data-stu-id="aee93-122">You don't have to define the target operating systems that your .NET Core app will run on in advance.</span></span> <span data-ttu-id="aee93-123">Ponieważ .NET Core używa formacie pliku PE wspólne dla obiektów wykonywalnych i bibliotek niezależnie od systemu operacyjnego, platformy .NET Core można wykonać aplikacji niezależnie od systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="aee93-123">Because .NET Core uses a common PE file format for executables and libraries regardless of operating system, .NET Core can execute your app regardless of the underlying operating system.</span></span> <span data-ttu-id="aee93-124">Aby uzyskać więcej informacji o formacie pliku PE, zobacz [Format pliku zestawu .NET](../../standard/assembly-format.md).</span><span class="sxs-lookup"><span data-stu-id="aee93-124">For more information on the PE file format, see [.NET Assembly File Format](../../standard/assembly-format.md).</span></span>

- <span data-ttu-id="aee93-125">Rozmiar pakietu wdrażania jest mała.</span><span class="sxs-lookup"><span data-stu-id="aee93-125">The size of your deployment package is small.</span></span> <span data-ttu-id="aee93-126">Można wdrażać tylko w aplikacji i jej zależności nie .NET Core samej siebie.</span><span class="sxs-lookup"><span data-stu-id="aee93-126">You only deploy your app and its dependencies, not .NET Core itself.</span></span>

- <span data-ttu-id="aee93-127">Wiele aplikacji używać tej samej instalacji .NET Core, co zmniejsza zarówno miejsca i pamięć użycia dysku w systemach hosta.</span><span class="sxs-lookup"><span data-stu-id="aee93-127">Multiple apps use the same .NET Core installation, which reduces both disk space and memory usage on host systems.</span></span>

<span data-ttu-id="aee93-128">Dostępne są również kilka wady:</span><span class="sxs-lookup"><span data-stu-id="aee93-128">There are also a few disadvantages:</span></span>

- <span data-ttu-id="aee93-129">Aplikację można uruchomić tylko wtedy, gdy jest to wersja platformy .NET Core, które są przeznaczone lub nowszy, jest już zainstalowana w systemie hosta.</span><span class="sxs-lookup"><span data-stu-id="aee93-129">Your app can run only if the version of .NET Core that you target, or a later version, is already installed on the host system.</span></span>

- <span data-ttu-id="aee93-130">Istnieje możliwość środowiska uruchomieniowego .NET Core i biblioteki można zmienić bez wiedzy użytkownika w przyszłych wersjach.</span><span class="sxs-lookup"><span data-stu-id="aee93-130">It's possible for the .NET Core runtime and libraries to change without your knowledge in future releases.</span></span> <span data-ttu-id="aee93-131">W rzadkich przypadkach może to spowodować zmianę zachowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aee93-131">In rare cases, this may change the behavior of your app.</span></span>

## <a name="self-contained-deployments-scd"></a><span data-ttu-id="aee93-132">Samodzielne wdrożeń (SCD)</span><span class="sxs-lookup"><span data-stu-id="aee93-132">Self-contained deployments (SCD)</span></span>

<span data-ttu-id="aee93-133">Niezależne wdrożenia możesz wdrożyć aplikację i wszystkie wymagane zależności innych firm oraz wersji platformy .NET Core, który był używany podczas kompilowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aee93-133">For a self-contained deployment, you deploy your app and any required third-party dependencies along with the version of .NET Core that you used to build the app.</span></span> <span data-ttu-id="aee93-134">Tworzenie SCD nie zawiera [natywnego zależności programu .NET Core](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) na różnych platformach, więc te musi występować przed uruchomieniem aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aee93-134">Creating an SCD doesn't include the [native dependencies of .NET Core](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) on various platforms, so these must be present before the app runs.</span></span>

<span data-ttu-id="aee93-135">Wdrożenia Dyskietki i SCD Użyj hosta oddzielne pliki wykonywalne, więc możesz utworzyć pliku wykonywalnego hosta SCD w podpisie wydawcy.</span><span class="sxs-lookup"><span data-stu-id="aee93-135">FDD and SCD deployments use separate host executables, so you can sign a host executable for an SCD with your publisher signature.</span></span>

### <a name="why-deploy-a-self-contained-deployment"></a><span data-ttu-id="aee93-136">Dlaczego wdrożenia niezależne?</span><span class="sxs-lookup"><span data-stu-id="aee93-136">Why deploy a self-contained deployment?</span></span>

<span data-ttu-id="aee93-137">Wdrażanie niezależne wdrożenia ma dwie główne zalety:</span><span class="sxs-lookup"><span data-stu-id="aee93-137">Deploying a Self-contained deployment has two major advantages:</span></span>

- <span data-ttu-id="aee93-138">Masz wyłączną kontrolę wersji platformy .NET Core, który jest wdrażany z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="aee93-138">You have sole control of the version of .NET Core that is deployed with your app.</span></span> <span data-ttu-id="aee93-139">Oprogramowanie .NET core może być obsługiwany tylko przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="aee93-139">.NET Core can be serviced only by you.</span></span>

- <span data-ttu-id="aee93-140">Można mieć pewność, system docelowy można uruchomić aplikacji .NET Core, ponieważ jest zapewnienie wersji programu .NET Core, który będzie uruchamiany na.</span><span class="sxs-lookup"><span data-stu-id="aee93-140">You can be assured that the target system can run your .NET Core app, since you're providing the version of .NET Core that it will run on.</span></span>

<span data-ttu-id="aee93-141">Ma on również szereg wady:</span><span class="sxs-lookup"><span data-stu-id="aee93-141">It also has a number of disadvantages:</span></span>

- <span data-ttu-id="aee93-142">Ponieważ .NET Core znajduje się w pakiecie wdrożenia, musisz wybrać platformy docelowe, dla których tworzenia pakietów wdrożeniowych z wyprzedzeniem.</span><span class="sxs-lookup"><span data-stu-id="aee93-142">Because .NET Core is included in your deployment package, you must select the target platforms for which you build deployment packages in advance.</span></span>

- <span data-ttu-id="aee93-143">Rozmiar pakietu wdrażania jest stosunkowo dużej, ponieważ powinien obejmować oprogramowanie .NET Core, a także aplikacji i jej zależności innych firm.</span><span class="sxs-lookup"><span data-stu-id="aee93-143">The size of your deployment package is relatively large, since you have to include .NET Core as well as your app and its third-party dependencies.</span></span>

- <span data-ttu-id="aee93-144">Wdrażania wielu niezależne aplikacji .NET Core do systemu, jaką może wykorzystać znacznej ilości miejsca na dysku, od każdej aplikacji duplikaty plików .NET Core.</span><span class="sxs-lookup"><span data-stu-id="aee93-144">Deploying numerous self-contained .NET Core apps to a system can consume significant amounts of disk space, since each app duplicates .NET Core files.</span></span>

## <a name="step-by-step-examples"></a><span data-ttu-id="aee93-145">Przykłady krok po kroku</span><span class="sxs-lookup"><span data-stu-id="aee93-145">Step-by-step examples</span></span>

<span data-ttu-id="aee93-146">Przykłady krok po kroku wdrażania aplikacji .NET Core za pomocą narzędzi interfejsu wiersza polecenia, zobacz [wdrażanie aplikacji programu .NET Core przy użyciu narzędzi interfejsu wiersza polecenia](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="aee93-146">For step-by-step examples of deploying .NET Core apps with CLI tools, see [Deploying .NET Core Apps with CLI Tools](deploy-with-cli.md).</span></span> <span data-ttu-id="aee93-147">Przykłady krok po kroku wdrażania aplikacji .NET Core za pomocą programu Visual Studio, zobacz [wdrażanie aplikacji programu .NET Core z programem Visual Studio](deploy-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="aee93-147">For step-by-step examples of deploying .NET Core apps with Visual Studio, see [Deploying .NET Core Apps with Visual Studio](deploy-with-vs.md).</span></span> <span data-ttu-id="aee93-148">Każdego tematu zawiera przykłady następujących wdrożeń:</span><span class="sxs-lookup"><span data-stu-id="aee93-148">Each topic includes examples of the following deployments:</span></span>

- <span data-ttu-id="aee93-149">Zależne od Framework wdrożenia</span><span class="sxs-lookup"><span data-stu-id="aee93-149">Framework-dependent deployment</span></span>
- <span data-ttu-id="aee93-150">Wdrożenie Framework zależne zależności innych firm</span><span class="sxs-lookup"><span data-stu-id="aee93-150">Framework-dependent deployment with third-party dependencies</span></span>
- <span data-ttu-id="aee93-151">Samodzielne wdrożenia</span><span class="sxs-lookup"><span data-stu-id="aee93-151">Self-contained deployment</span></span>
- <span data-ttu-id="aee93-152">Samodzielne wdrożenia zależności innych firm</span><span class="sxs-lookup"><span data-stu-id="aee93-152">Self-contained deployment with third-party dependencies</span></span>

# <a name="see-also"></a><span data-ttu-id="aee93-153">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aee93-153">See also</span></span>

<span data-ttu-id="aee93-154">[Wdrażanie aplikacji .NET Core za pomocą narzędzi interfejsu wiersza polecenia](deploy-with-cli.md) </span><span class="sxs-lookup"><span data-stu-id="aee93-154">[Deploying .NET Core Apps with CLI Tools](deploy-with-cli.md) </span></span>  
<span data-ttu-id="aee93-155">[Wdrażanie aplikacji programu .NET Core z programem Visual Studio](deploy-with-vs.md) </span><span class="sxs-lookup"><span data-stu-id="aee93-155">[Deploying .NET Core Apps with Visual Studio](deploy-with-vs.md) </span></span>  
<span data-ttu-id="aee93-156">[Pakiety, Metapackages i platform](../packages.md) </span><span class="sxs-lookup"><span data-stu-id="aee93-156">[Packages, Metapackages and Frameworks](../packages.md) </span></span>  
[<span data-ttu-id="aee93-157">Katalogu .NET core środowiska uruchomieniowego identyfikator (RID)</span><span class="sxs-lookup"><span data-stu-id="aee93-157">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
