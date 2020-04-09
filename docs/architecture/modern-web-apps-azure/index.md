---
title: Tworzenie architektury nowoczesnych aplikacji internetowych za pomocą platformy ASP.NET Core i platformy Azure
description: Przewodnik, który zawiera kompleksowe wskazówki dotyczące tworzenia monolitycznych aplikacji sieci web przy użyciu ASP.NET Core i Azure.
author: ardalis
ms.author: wiwagn
ms.date: 12/4/2019
ms.openlocfilehash: 18449ea02b7f9e89744a0f3088f80b7a51a807da
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80987897"
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a><span data-ttu-id="da6ba-103">Tworzenie architektury nowoczesnych aplikacji internetowych za pomocą platformy ASP.NET Core i platformy Azure</span><span class="sxs-lookup"><span data-stu-id="da6ba-103">Architect Modern Web Applications with ASP.NET Core and Azure</span></span>

![Zarezerwuj obraz okładki przewodnika Architect Modern Web Applications.](./media/index/web-application-guide-cover-image.png)

<span data-ttu-id="da6ba-105">**EDITION v3.1** - Zaktualizowano do ASP.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="da6ba-105">**EDITION v3.1** - Updated to ASP.NET Core 3.1</span></span>

<span data-ttu-id="da6ba-106">OPUBLIKOWANA PRZEZ</span><span class="sxs-lookup"><span data-stu-id="da6ba-106">PUBLISHED BY</span></span>

<span data-ttu-id="da6ba-107">Zespoły produktów Microsoft Developer Division, .NET i Visual Studio</span><span class="sxs-lookup"><span data-stu-id="da6ba-107">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="da6ba-108">Oddział firmy Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="da6ba-108">A division of Microsoft Corporation</span></span>

<span data-ttu-id="da6ba-109">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="da6ba-109">One Microsoft Way</span></span>

<span data-ttu-id="da6ba-110">Redmond, Waszyngton 98052-6399</span><span class="sxs-lookup"><span data-stu-id="da6ba-110">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="da6ba-111">Prawa autorskie © 2020 roku przez Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="da6ba-111">Copyright © 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="da6ba-112">Wszelkie prawa zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="da6ba-112">All rights reserved.</span></span> <span data-ttu-id="da6ba-113">Żadna część zawartości tej książki nie może być powielana ani przekazywana w jakiejkolwiek formie lub w jakikolwiek sposób bez pisemnej zgody wydawcy.</span><span class="sxs-lookup"><span data-stu-id="da6ba-113">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="da6ba-114">Książka ta jest dostarczana "tak jak jest" i wyraża poglądy i opinie autora.</span><span class="sxs-lookup"><span data-stu-id="da6ba-114">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="da6ba-115">Poglądy, opinie i informacje wyrażone w tej książce, w tym adresy URL i inne odniesienia do stron internetowych, mogą ulec zmianie bez powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="da6ba-115">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="da6ba-116">Niektóre z przykładów przedstawiono wyłącznie do celów informacyjnych i są one fikcyjne.</span><span class="sxs-lookup"><span data-stu-id="da6ba-116">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="da6ba-117">Żadne rzeczywiste skojarzenia lub związki nie są zamierzone ani wnioskowane.</span><span class="sxs-lookup"><span data-stu-id="da6ba-117">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="da6ba-118">Firma Microsoft i znaki https://www.microsoft.com towarowe wymienione na stronie internetowej "Znaki towarowe" są znakami towarowymi grupy firm Microsoft.</span><span class="sxs-lookup"><span data-stu-id="da6ba-118">Microsoft and the trademarks listed at https://www.microsoft.com on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="da6ba-119">Mac i macOS są znakami towarowymi firmy Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="da6ba-119">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="da6ba-120">Logo docker wielorybów jest zastrzeżonym znakiem towarowym firmy Docker, Inc. Używany za zgodą.</span><span class="sxs-lookup"><span data-stu-id="da6ba-120">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="da6ba-121">Wszystkie inne znaki i logo są własnością ich odpowiednich właścicieli.</span><span class="sxs-lookup"><span data-stu-id="da6ba-121">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="da6ba-122">Autor:</span><span class="sxs-lookup"><span data-stu-id="da6ba-122">Author:</span></span>

> <span data-ttu-id="da6ba-123">**Steve "ardalis" Smith** - Architekt oprogramowania i trener - [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="da6ba-123">**Steve "ardalis" Smith** - Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>

<span data-ttu-id="da6ba-124">Edytory:</span><span class="sxs-lookup"><span data-stu-id="da6ba-124">Editors:</span></span>

> <span data-ttu-id="da6ba-125">**Maira Wenzel**</span><span class="sxs-lookup"><span data-stu-id="da6ba-125">**Maira Wenzel**</span></span>

## <a name="introduction"></a><span data-ttu-id="da6ba-126">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="da6ba-126">Introduction</span></span>

<span data-ttu-id="da6ba-127">.NET Core i ASP.NET Core oferują kilka zalet w stosunku do tradycyjnego rozwoju platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="da6ba-127">.NET Core and ASP.NET Core offer several advantages over traditional .NET development.</span></span> <span data-ttu-id="da6ba-128">Należy użyć .NET Core dla aplikacji serwera, jeśli niektóre lub wszystkie z następujących są ważne dla sukcesu aplikacji:</span><span class="sxs-lookup"><span data-stu-id="da6ba-128">You should use .NET Core for your server applications if some or all of the following are important to your application's success:</span></span>

- <span data-ttu-id="da6ba-129">Obsługa międzyplatformowa.</span><span class="sxs-lookup"><span data-stu-id="da6ba-129">Cross-platform support.</span></span>

- <span data-ttu-id="da6ba-130">Korzystanie z mikrousług.</span><span class="sxs-lookup"><span data-stu-id="da6ba-130">Use of microservices.</span></span>

- <span data-ttu-id="da6ba-131">Korzystanie z kontenerów platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="da6ba-131">Use of Docker containers.</span></span>

- <span data-ttu-id="da6ba-132">Wymagania dotyczące wysokiej wydajności i skalowalności.</span><span class="sxs-lookup"><span data-stu-id="da6ba-132">High performance and scalability requirements.</span></span>

- <span data-ttu-id="da6ba-133">Przechowywanie wersji obok siebie wersji platformy .NET przez aplikację na tym samym serwerze.</span><span class="sxs-lookup"><span data-stu-id="da6ba-133">Side-by-side versioning of .NET versions by application on the same server.</span></span>

<span data-ttu-id="da6ba-134">Tradycyjne aplikacje platformy .NET mogą i obsługują wiele z tych wymagań, ale ASP.NET Core i .NET Core zostały zoptymalizowane w celu zaoferowania ulepszonej obsługi powyższych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="da6ba-134">Traditional .NET applications can and do support many of these requirements, but ASP.NET Core and .NET Core have been optimized to offer improved support for the above scenarios.</span></span>

<span data-ttu-id="da6ba-135">Coraz więcej organizacji decyduje się na hostowania swoich aplikacji sieci web w chmurze przy użyciu usług, takich jak Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="da6ba-135">More and more organizations are choosing to host their web applications in the cloud using services like Microsoft Azure.</span></span> <span data-ttu-id="da6ba-136">Należy rozważyć hostowanie aplikacji w chmurze, jeśli są ważne dla aplikacji lub organizacji:</span><span class="sxs-lookup"><span data-stu-id="da6ba-136">You should consider hosting your application in the cloud if the following are important to your application or organization:</span></span>

- <span data-ttu-id="da6ba-137">Mniejsze inwestycje w koszty centrów danych (sprzęt, oprogramowanie, przestrzeń, narzędzia, zarządzanie serwerami itp.)</span><span class="sxs-lookup"><span data-stu-id="da6ba-137">Reduced investment in data center costs (hardware, software, space, utilities, server management, etc.)</span></span>

- <span data-ttu-id="da6ba-138">Elastyczne ceny (wynagrodzenie oparte na użyciu, a nie na bezczynności).</span><span class="sxs-lookup"><span data-stu-id="da6ba-138">Flexible pricing (pay based on usage, not for idle capacity).</span></span>

- <span data-ttu-id="da6ba-139">Ekstremalna niezawodność.</span><span class="sxs-lookup"><span data-stu-id="da6ba-139">Extreme reliability.</span></span>

- <span data-ttu-id="da6ba-140">Ulepszona mobilność aplikacji; łatwo zmienić miejsce i sposób wdrażania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="da6ba-140">Improved app mobility; easily change where and how your app is deployed.</span></span>

- <span data-ttu-id="da6ba-141">Elastyczna pojemność; w górę lub w dół w zależności od rzeczywistych potrzeb.</span><span class="sxs-lookup"><span data-stu-id="da6ba-141">Flexible capacity; scale up or down based on actual needs.</span></span>

<span data-ttu-id="da6ba-142">Tworzenie aplikacji sieci web za pomocą ASP.NET Core, hostowanych na platformie Azure, oferuje wiele korzyści konkurencyjnych w stosunku do tradycyjnych alternatyw.</span><span class="sxs-lookup"><span data-stu-id="da6ba-142">Building web applications with ASP.NET Core, hosted in Azure, offers many competitive advantages over traditional alternatives.</span></span> <span data-ttu-id="da6ba-143">ASP.NET Core jest zoptymalizowany pod kątem nowoczesnych praktyk tworzenia aplikacji sieci web i scenariuszy hostingu w chmurze.</span><span class="sxs-lookup"><span data-stu-id="da6ba-143">ASP.NET Core is optimized for modern web application development practices and cloud hosting scenarios.</span></span> <span data-ttu-id="da6ba-144">W tym przewodniku dowiesz się, jak zaprojektować aplikacje ASP.NET Core, aby jak najlepiej wykorzystać te możliwości.</span><span class="sxs-lookup"><span data-stu-id="da6ba-144">In this guide, you'll learn how to architect your ASP.NET Core applications to best take advantage of these capabilities.</span></span>

## <a name="purpose"></a><span data-ttu-id="da6ba-145">Przeznaczenie</span><span class="sxs-lookup"><span data-stu-id="da6ba-145">Purpose</span></span>

<span data-ttu-id="da6ba-146">Ten przewodnik zawiera kompleksowe wskazówki dotyczące tworzenia *monolitycznych* aplikacji sieci web przy użyciu ASP.NET Core i azure.</span><span class="sxs-lookup"><span data-stu-id="da6ba-146">This guide provides end-to-end guidance on building *monolithic* web applications using ASP.NET Core and Azure.</span></span> <span data-ttu-id="da6ba-147">W tym kontekście "monolityczne" odnosi się do faktu, że te aplikacje są wdrażane jako pojedyncza jednostka, a nie jako zbiór interakcji usług i aplikacji.</span><span class="sxs-lookup"><span data-stu-id="da6ba-147">In this context, "monolithic" refers to the fact that these applications are deployed as a single unit, not as a collection of interacting services and applications.</span></span>

<span data-ttu-id="da6ba-148">Ten przewodnik jest uzupełnieniem ["_.NET Microservices. Architektura konteneryzowanych aplikacji .NET_",](../microservices/index.md) która koncentruje się bardziej na platformie Docker, Mikrousług i wdrażaniu kontenerów do obsługi aplikacji korporacyjnych.</span><span class="sxs-lookup"><span data-stu-id="da6ba-148">This guide is complementary to the ["_.NET Microservices. Architecture for Containerized .NET Applications_"](../microservices/index.md) which focuses more on Docker, Microservices, and Deployment of Containers to host enterprise applications.</span></span>

### <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="da6ba-149">Mikrousług .NET.</span><span class="sxs-lookup"><span data-stu-id="da6ba-149">.NET Microservices.</span></span> <span data-ttu-id="da6ba-150">architektura konteneryzowanych aplikacji .NET</span><span class="sxs-lookup"><span data-stu-id="da6ba-150">Architecture for Containerized .NET Applications</span></span>

- <span data-ttu-id="da6ba-151">**książka elektroniczna**</span><span class="sxs-lookup"><span data-stu-id="da6ba-151">**e-book**</span></span>  
  <https://aka.ms/MicroservicesEbook>
- <span data-ttu-id="da6ba-152">**Przykładowa aplikacja**</span><span class="sxs-lookup"><span data-stu-id="da6ba-152">**Sample Application**</span></span>  
  <https://aka.ms/microservicesarchitecture>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="da6ba-153">Kto powinien korzystać z tego przewodnika</span><span class="sxs-lookup"><span data-stu-id="da6ba-153">Who should use this guide</span></span>

<span data-ttu-id="da6ba-154">Odbiorcami tego przewodnika są głównie deweloperzy, potencjalni klienci programiści i architekci, którzy są zainteresowani tworzeniem nowoczesnych aplikacji sieci Web przy użyciu technologii i usług firmy Microsoft w chmurze.</span><span class="sxs-lookup"><span data-stu-id="da6ba-154">The audience for this guide is mainly developers, development leads, and architects who are interested in building modern web applications using Microsoft technologies and services in the cloud.</span></span>

<span data-ttu-id="da6ba-155">Dodatkową grupą odbiorców są decydenci techniczni, którzy są już znani ASP.NET lub platformy Azure i szukają informacji na temat tego, czy warto uaktualnić do ASP.NET Core dla nowych lub istniejących projektów.</span><span class="sxs-lookup"><span data-stu-id="da6ba-155">A secondary audience is technical decision makers who are already familiar ASP.NET or Azure and are looking for information on whether it makes sense to upgrade to ASP.NET Core for new or existing projects.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="da6ba-156">Jak można korzystać z tego przewodnika</span><span class="sxs-lookup"><span data-stu-id="da6ba-156">How you can use this guide</span></span>

<span data-ttu-id="da6ba-157">Ten przewodnik został skondensowany w stosunkowo mały dokument, który koncentruje się na tworzeniu aplikacji sieci web z nowoczesnymi technologiami platformy .NET i systemem Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="da6ba-157">This guide has been condensed into a relatively small document that focuses on building web applications with modern .NET technologies and Windows Azure.</span></span> <span data-ttu-id="da6ba-158">Jako takie, można go odczytać w całości, aby zapewnić podstawę zrozumienia takich zastosowań i ich względów technicznych.</span><span class="sxs-lookup"><span data-stu-id="da6ba-158">As such, it can be read in its entirety to provide a foundation of understanding such applications and their technical considerations.</span></span> <span data-ttu-id="da6ba-159">Przewodnik, wraz z jego przykładową aplikacją, może również służyć jako punkt wyjścia lub odniesienia.</span><span class="sxs-lookup"><span data-stu-id="da6ba-159">The guide, along with its sample application, can also serve as a starting point or reference.</span></span> <span data-ttu-id="da6ba-160">Użyj skojarzonej przykładowej aplikacji jako szablonu dla własnych aplikacji lub aby zobaczyć, jak można zorganizować części składowe aplikacji.</span><span class="sxs-lookup"><span data-stu-id="da6ba-160">Use the associated sample application as a template for your own applications, or to see how you might organize your application's component parts.</span></span> <span data-ttu-id="da6ba-161">Zapoznaj się z zasadami przewodnika oraz zakresem opcji architektury i technologii oraz zagadnieniami decyzyjnymi podczas ważenia tych opcji dla własnego zastosowania.</span><span class="sxs-lookup"><span data-stu-id="da6ba-161">Refer back to the guide's principles and coverage of architecture and technology options and decision considerations when you're weighing these choices for your own application.</span></span>

<span data-ttu-id="da6ba-162">Możesz przesłać ten przewodnik do swojego zespołu, aby zapewnić wspólne zrozumienie tych zagadnień i możliwości.</span><span class="sxs-lookup"><span data-stu-id="da6ba-162">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="da6ba-163">Posiadanie wszystkich pracujących z wspólnego zestawu terminologii i podstawowych zasad pomaga zapewnić spójne stosowanie wzorców i praktyk architektonicznych.</span><span class="sxs-lookup"><span data-stu-id="da6ba-163">Having everybody working from a common set of terminology and underlying principles helps ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="da6ba-164">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="da6ba-164">References</span></span>

- <span data-ttu-id="da6ba-165">**Wybieranie między programami .NET Core i .NET Framework na potrzeby aplikacji serwerowych**</span><span class="sxs-lookup"><span data-stu-id="da6ba-165">**Choosing between .NET Core and .NET Framework for server apps**</span></span>  
  [https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server](../../standard/choosing-core-framework-server.md)

>[!div class="step-by-step"]
>[<span data-ttu-id="da6ba-166">Dalej</span><span class="sxs-lookup"><span data-stu-id="da6ba-166">Next</span></span>](modern-web-applications-characteristics.md)
