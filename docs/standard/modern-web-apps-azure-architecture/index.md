---
title: "Architektów nowoczesnych aplikacji sieci web platformy ASP.NET Core i Azure"
description: Projektowania nowoczesnych aplikacji sieci Web platformy ASP.NET Core i Azure | wprowadzenie
author: ardalis
ms.author: wiwagn
ms.date: 10/06/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.openlocfilehash: 93a74bb7ba537d3c7c0291f7903112dc470133a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a><span data-ttu-id="7a713-103">Architektów nowoczesnych aplikacji sieci Web platformy ASP.NET Core i Azure</span><span class="sxs-lookup"><span data-stu-id="7a713-103">Architect Modern Web Applications with ASP.NET Core and Azure</span></span>

<span data-ttu-id="7a713-104">Oprogramowanie .NET core i ASP.NET Core oferują wiele zalet w porównaniu do tradycyjnego .NET — rozwój.</span><span class="sxs-lookup"><span data-stu-id="7a713-104">.NET Core and ASP.NET Core offer several advantages over traditional .NET development.</span></span> <span data-ttu-id="7a713-105">Jeśli niektóre lub wszystkie z następujących czynności są ważne, aby wskazywał Powodzenie, aplikacji, należy użyć .NET Core dla aplikacji serwera:</span><span class="sxs-lookup"><span data-stu-id="7a713-105">You should use .NET Core for your server applications if some or all of the following are important to your application's success:</span></span>

-   <span data-ttu-id="7a713-106">Obsługa platform</span><span class="sxs-lookup"><span data-stu-id="7a713-106">Cross-platform support</span></span>

-   <span data-ttu-id="7a713-107">Użyj mikrousług</span><span class="sxs-lookup"><span data-stu-id="7a713-107">Use of microservices</span></span>

-   <span data-ttu-id="7a713-108">Używanie kontenerów Docker</span><span class="sxs-lookup"><span data-stu-id="7a713-108">Use of Docker containers</span></span>

-   <span data-ttu-id="7a713-109">Wymagania dotyczące wysokiej wydajności i skalowalności</span><span class="sxs-lookup"><span data-stu-id="7a713-109">High performance and scalability requirements</span></span>

-   <span data-ttu-id="7a713-110">Przechowywanie wersji Side-by-side wersji platformy .NET przez aplikację na tym samym serwerze</span><span class="sxs-lookup"><span data-stu-id="7a713-110">Side-by-side versioning of .NET versions by application on the same server</span></span>

<span data-ttu-id="7a713-111">Tradycyjne aplikacje .NET mogą i obsługują tych wymagań, ale .NET Core i ASP.NET Core zostały zoptymalizowane do oferują ulepszoną obsługę powyższych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="7a713-111">Traditional .NET applications can and do support these requirements, but ASP.NET Core and .NET Core have been optimized to offer improved support for the above scenarios.</span></span>

<span data-ttu-id="7a713-112">Organizacje coraz więcej wybierania do obsługi aplikacji sieci web w chmurze przy użyciu usługi Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="7a713-112">More and more organizations are choosing to host their web applications in the cloud using services like Microsoft Azure.</span></span> <span data-ttu-id="7a713-113">Należy rozważyć obsługę aplikacji w chmurze, czy następujące usługi są ważne do aplikacji lub organizacji:</span><span class="sxs-lookup"><span data-stu-id="7a713-113">You should consider hosting your application in the cloud if the following are important to your application or organization:</span></span>

-   <span data-ttu-id="7a713-114">Inwestycji zmniejszenie kosztów centrum danych (sprzętu, oprogramowania, miejsca, narzędzia itp.)</span><span class="sxs-lookup"><span data-stu-id="7a713-114">Reduced investment in data center costs (hardware, software, space, utilities, etc)</span></span>

-   <span data-ttu-id="7a713-115">Elastyczne cennik (płatności na podstawie użycia nie dla bezczynności pojemności)</span><span class="sxs-lookup"><span data-stu-id="7a713-115">Flexible pricing (pay based on usage, not for idle capacity)</span></span>

-   <span data-ttu-id="7a713-116">Extreme niezawodności</span><span class="sxs-lookup"><span data-stu-id="7a713-116">Extreme reliability</span></span>

-   <span data-ttu-id="7a713-117">Mobilność aplikacji została poprawiona; łatwo zmienić, jak i gdzie wdrożonej aplikacji</span><span class="sxs-lookup"><span data-stu-id="7a713-117">Improved app mobility; easily change where and how your app is deployed</span></span>

-   <span data-ttu-id="7a713-118">Elastyczna pojemność; Skalowanie w górę lub w dół na podstawie rzeczywistych potrzeb</span><span class="sxs-lookup"><span data-stu-id="7a713-118">Flexible capacity; scale up or down based on actual needs</span></span>

<span data-ttu-id="7a713-119">Tworzenie aplikacji sieci web platformy ASP.NET Core, obsługiwane na platformie Microsoft Azure oferuje wiele przewagi konkurencyjnej nad alternatyw tradycyjnych.</span><span class="sxs-lookup"><span data-stu-id="7a713-119">Building web applications with ASP.NET Core, hosted in Microsoft Azure, offers numerous competitive advantages over traditional alternatives.</span></span> <span data-ttu-id="7a713-120">Platformy ASP.NET Core jest zoptymalizowana pod kątem rozwiązania w zakresie tworzenia nowoczesnych witryn sieci web aplikacji i scenariusze hostingu w chmurze.</span><span class="sxs-lookup"><span data-stu-id="7a713-120">ASP.NET Core is optimized for modern web application development practices and cloud hosting scenarios.</span></span> <span data-ttu-id="7a713-121">W tym przewodniku dowiesz się, jak zaprojektować najlepiej wykorzystać te możliwości aplikacji platformy ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="7a713-121">In this guide, you will learn how to architect your ASP.NET Core applications to best take advantage of these capabilities.</span></span>

## <a name="purpose"></a><span data-ttu-id="7a713-122">Cel</span><span class="sxs-lookup"><span data-stu-id="7a713-122">Purpose</span></span>

<span data-ttu-id="7a713-123">W tym przewodniku znajdują się na trasie wskazówki dotyczące tworzenia aplikacji sieci web wbudowanymi za pomocą platformy ASP.NET Core i Azure.</span><span class="sxs-lookup"><span data-stu-id="7a713-123">This guide provides end-to-end guidance on building monolithic web applications using ASP.NET Core and Azure.</span></span>

<span data-ttu-id="7a713-124">Ten przewodnik jest uzupełniające "*Architecting i tworzenie konteneryzowanych i aplikacji z platformą .NET Mikrousługi*" do hosta przedsiębiorstwa który skupia się więcej na Docker Mikrousług oraz wdrożenia kontenerów aplikacje.</span><span class="sxs-lookup"><span data-stu-id="7a713-124">This guide is complementary to the "*Architecting and Developing Containerized and Microservice-based Applications with .NET*" which focuses more on Docker, Microservices, and Deployment of Containers to host enterprise applications.</span></span>

> ### <a name="architecting-and-developing-containerized-microservice-based-apps-in-net"></a><span data-ttu-id="7a713-125">Projektowania i opracowywania konteneryzowanych Mikrousługi na podstawie aplikacji w .NET</span><span class="sxs-lookup"><span data-stu-id="7a713-125">Architecting and Developing Containerized Microservice Based Apps in .NET</span></span>
> - <span data-ttu-id="7a713-126">**Książka elektroniczna**</span><span class="sxs-lookup"><span data-stu-id="7a713-126">**e-book**</span></span>  
> <span data-ttu-id="7a713-127"><http://aka.MS/MicroservicesEbook></span><span class="sxs-lookup"><span data-stu-id="7a713-127"><http://aka.ms/MicroservicesEbook></span></span>
> - <span data-ttu-id="7a713-128">**Przykładowa aplikacja**</span><span class="sxs-lookup"><span data-stu-id="7a713-128">**Sample Application**</span></span>  
> <span data-ttu-id="7a713-129"><http://aka.MS/microservicesarchitecture></span><span class="sxs-lookup"><span data-stu-id="7a713-129"><http://aka.ms/microservicesarchitecture></span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="7a713-130">Kto powinien używać ten przewodnik</span><span class="sxs-lookup"><span data-stu-id="7a713-130">Who should use this guide</span></span>

<span data-ttu-id="7a713-131">Odbiorcami tego przewodnika jest głównie deweloperom, programowanie potencjalnych klientów i architektów zainteresowanych tworzenie nowoczesnych aplikacji sieci web przy użyciu usług i technologii firmy Microsoft w chmurze.</span><span class="sxs-lookup"><span data-stu-id="7a713-131">The audience for this guide is mainly developers, development leads, and architects who are interested in building modern web applications using Microsoft technologies and services in the cloud.</span></span>

<span data-ttu-id="7a713-132">Dodatkowej odbiorców jest techniczne inne osoby podejmujące decyzje, które są już znane ASP.NET i/lub Azure i szukasz informacji na temat tego, czy dobrym rozwiązaniem jest uaktualnienie do platformy ASP.NET Core dla nowych lub istniejących projektów.</span><span class="sxs-lookup"><span data-stu-id="7a713-132">A secondary audience is technical decision makers who are already familiar ASP.NET and/or Azure and are looking for information on whether it makes sense to upgrade to ASP.NET Core for new or existing projects.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="7a713-133">Sposób korzystania z tego przewodnika</span><span class="sxs-lookup"><span data-stu-id="7a713-133">How you can use this guide</span></span>

<span data-ttu-id="7a713-134">Ten przewodnik zawiera zostały zmniejszenia dokumentem stosunkowo mały, który koncentruje się na tworzeniu aplikacji sieci web z nowoczesnej technologii .NET i systemu Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="7a713-134">This guide has been condensed into a relatively small document that focuses on building web applications with modern .NET technologies and Windows Azure.</span></span> <span data-ttu-id="7a713-135">W efekcie mogą być odczytywane w całości, aby zapewnić podstawę zrozumienia takich aplikacji i ich zagadnienia techniczne.</span><span class="sxs-lookup"><span data-stu-id="7a713-135">As such, it can be read in its entirety to provide a foundation of understanding such applications and their technical considerations.</span></span> <span data-ttu-id="7a713-136">Przewodnik, wraz z przykładowej aplikacji, mogą również służyć jako punktu wyjścia lub odwołanie.</span><span class="sxs-lookup"><span data-stu-id="7a713-136">The guide, along with its sample application, can also serve as a starting point or reference.</span></span> <span data-ttu-id="7a713-137">Użyj skojarzone przykładowej aplikacji jako szablonu dla własnej aplikacji lub sprawdzić, jak mogą organizować części aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7a713-137">Use the associated sample application as a template for your own applications, or to see how you might organize your application's component parts.</span></span> <span data-ttu-id="7a713-138">Odwołują się do zasad i pokrycia architektury i opcje technologii i zagadnienia dotyczące decyzji Przewodnik po o wadze tych opcji dla swojej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7a713-138">Refer back to the guide's principles and coverage of architecture and technology options and decision considerations when weighing these choices for your own application.</span></span>

<span data-ttu-id="7a713-139">Możesz przesłać ten przewodnik do zespołu w celu zapewnienia zrozumienie tych zagadnień i możliwości.</span><span class="sxs-lookup"><span data-stu-id="7a713-139">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="7a713-140">Każdy Praca ze wspólnego zestawu terminologii i podstawowymi zasadami o pomoże zapewnienia spójnego stosowania wzorców architektury rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="7a713-140">Having everybody working from a common set of terminology and underlying principles will help ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="7a713-141">Odwołania</span><span class="sxs-lookup"><span data-stu-id="7a713-141">References</span></span>
- <span data-ttu-id="7a713-142">**Wybór między .NET Core i .NET Framework dla serwera aplikacji**</span><span class="sxs-lookup"><span data-stu-id="7a713-142">**Choosing between .NET Core and .NET Framework for server apps**</span></span>  
<span data-ttu-id="7a713-143"><https://docs.microsoft.com/DotNet/articles/Standard/Choosing-Core-Framework-Server></span><span class="sxs-lookup"><span data-stu-id="7a713-143"><https://docs.microsoft.com/dotnet/articles/standard/choosing-core-framework-server></span></span>

>[!div class="step-by-step"]
<span data-ttu-id="7a713-144">[Next] (modern-web aplikacje characteristics.md)</span><span class="sxs-lookup"><span data-stu-id="7a713-144">[Next] (modern-web-applications-characteristics.md)</span></span>
