---
title: Architekt nowoczesnych aplikacji internetowych z ASP.NET Core i Azure
description: Przewodnik, który zawiera kompleksowe wskazówki dotyczące tworzenia monolitycznych aplikacji sieci web przy użyciu ASP.NET Core i Azure.
author: ardalis
ms.author: wiwagn
ms.date: 12/4/2019
ms.openlocfilehash: c19e5e90cfb96463f744cfb064abe72ee5db2e9f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "77449334"
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a><span data-ttu-id="21cb6-103">Tworzenie architektury nowoczesnych aplikacji internetowych za pomocą platformy ASP.NET Core i platformy Azure</span><span class="sxs-lookup"><span data-stu-id="21cb6-103">Architect Modern Web Applications with ASP.NET Core and Azure</span></span>

![Zarezerwuj okładkę przewodnika Architect Modern Web Applications.](./media/index/web-application-guide-cover-image.png)

<span data-ttu-id="21cb6-105">**EDITION v3.1** - Zaktualizowano do ASP.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="21cb6-105">**EDITION v3.1** - Updated to ASP.NET Core 3.1</span></span>

<span data-ttu-id="21cb6-106">OPUBLIKOWANA PRZEZ</span><span class="sxs-lookup"><span data-stu-id="21cb6-106">PUBLISHED BY</span></span>

<span data-ttu-id="21cb6-107">Zespoły produktów Microsoft Developer Division, .NET i Visual Studio</span><span class="sxs-lookup"><span data-stu-id="21cb6-107">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="21cb6-108">Oddział Firmy Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="21cb6-108">A division of Microsoft Corporation</span></span>

<span data-ttu-id="21cb6-109">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="21cb6-109">One Microsoft Way</span></span>

<span data-ttu-id="21cb6-110">Redmond (Waszyngton) 98052-6399</span><span class="sxs-lookup"><span data-stu-id="21cb6-110">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="21cb6-111">Prawa autorskie © 2020 r. przez Firmę Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="21cb6-111">Copyright © 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="21cb6-112">Wszelkie prawa zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="21cb6-112">All rights reserved.</span></span> <span data-ttu-id="21cb6-113">Żadna część treści tej książki nie może być powielana lub przekazywana w jakiejkolwiek formie lub w jakikolwiek sposób bez pisemnej zgody wydawcy.</span><span class="sxs-lookup"><span data-stu-id="21cb6-113">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="21cb6-114">Ta książka jest "tak jak jest" i wyraża poglądy i opinie autora.</span><span class="sxs-lookup"><span data-stu-id="21cb6-114">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="21cb6-115">Poglądy, opinie i informacje wyrażone w tej książce, w tym adresy URL i inne odniesienia do stron internetowych, mogą ulec zmianie bez powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="21cb6-115">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="21cb6-116">Niektóre z przykładów przedstawiono wyłącznie do celów informacyjnych i są one fikcyjne.</span><span class="sxs-lookup"><span data-stu-id="21cb6-116">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="21cb6-117">Żadne rzeczywiste skojarzenia lub związki nie są zamierzone ani wnioskowane.</span><span class="sxs-lookup"><span data-stu-id="21cb6-117">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="21cb6-118">Microsoft i znaki towarowe https://www.microsoft.com wymienione na stronie internetowej "Znaki towarowe" są znakami towarowymi grupy firm Microsoft.</span><span class="sxs-lookup"><span data-stu-id="21cb6-118">Microsoft and the trademarks listed at https://www.microsoft.com on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="21cb6-119">Mac i macOS są znakami towarowymi firmy Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="21cb6-119">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="21cb6-120">Logo wieloryba Docker jest zastrzeżonym znakiem towarowym firmy Docker, Inc. Używanym za zgodą.</span><span class="sxs-lookup"><span data-stu-id="21cb6-120">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="21cb6-121">Wszystkie inne znaki i logo są własnością ich właścicieli.</span><span class="sxs-lookup"><span data-stu-id="21cb6-121">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="21cb6-122">Autor:</span><span class="sxs-lookup"><span data-stu-id="21cb6-122">Author:</span></span>

> <span data-ttu-id="21cb6-123">**Steve "ardalis" Smith** - Architekt oprogramowania i trener - [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="21cb6-123">**Steve "ardalis" Smith** - Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>

<span data-ttu-id="21cb6-124">Edytory:</span><span class="sxs-lookup"><span data-stu-id="21cb6-124">Editors:</span></span>

> <span data-ttu-id="21cb6-125">**Maira Wenzel**</span><span class="sxs-lookup"><span data-stu-id="21cb6-125">**Maira Wenzel**</span></span>

## <a name="introduction"></a><span data-ttu-id="21cb6-126">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="21cb6-126">Introduction</span></span>

<span data-ttu-id="21cb6-127">.NET Core i ASP.NET Core oferują kilka zalet w porównaniu z tradycyjnym rozwojem .NET.</span><span class="sxs-lookup"><span data-stu-id="21cb6-127">.NET Core and ASP.NET Core offer several advantages over traditional .NET development.</span></span> <span data-ttu-id="21cb6-128">Należy użyć .NET Core dla aplikacji serwera, jeśli niektóre lub wszystkie z następujących są ważne dla powodzenia aplikacji:</span><span class="sxs-lookup"><span data-stu-id="21cb6-128">You should use .NET Core for your server applications if some or all of the following are important to your application's success:</span></span>

- <span data-ttu-id="21cb6-129">Obsługa międzyplatformowa.</span><span class="sxs-lookup"><span data-stu-id="21cb6-129">Cross-platform support.</span></span>

- <span data-ttu-id="21cb6-130">Korzystanie z mikrousług.</span><span class="sxs-lookup"><span data-stu-id="21cb6-130">Use of microservices.</span></span>

- <span data-ttu-id="21cb6-131">Korzystanie z kontenerów platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="21cb6-131">Use of Docker containers.</span></span>

- <span data-ttu-id="21cb6-132">Wysoka wydajność i skalowalność wymagania.</span><span class="sxs-lookup"><span data-stu-id="21cb6-132">High performance and scalability requirements.</span></span>

- <span data-ttu-id="21cb6-133">Side-by-side przechowywanie wersji programu .NET przez aplikację na tym samym serwerze.</span><span class="sxs-lookup"><span data-stu-id="21cb6-133">Side-by-side versioning of .NET versions by application on the same server.</span></span>

<span data-ttu-id="21cb6-134">Tradycyjne aplikacje .NET mogą i obsługują wiele z tych wymagań, ale ASP.NET Core i .NET Core zostały zoptymalizowane w celu zaoferowania ulepszonej obsługi powyższych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="21cb6-134">Traditional .NET applications can and do support many of these requirements, but ASP.NET Core and .NET Core have been optimized to offer improved support for the above scenarios.</span></span>

<span data-ttu-id="21cb6-135">Coraz więcej organizacji decyduje się na hostowanie swoich aplikacji sieci web w chmurze przy użyciu usług, takich jak Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="21cb6-135">More and more organizations are choosing to host their web applications in the cloud using services like Microsoft Azure.</span></span> <span data-ttu-id="21cb6-136">Należy rozważyć hosting aplikacji w chmurze, jeśli następujące są ważne dla aplikacji lub organizacji:</span><span class="sxs-lookup"><span data-stu-id="21cb6-136">You should consider hosting your application in the cloud if the following are important to your application or organization:</span></span>

- <span data-ttu-id="21cb6-137">Mniejsze inwestycje w koszty centrów danych (sprzęt, oprogramowanie, przestrzeń, narzędzia, zarządzanie serwerami itp.)</span><span class="sxs-lookup"><span data-stu-id="21cb6-137">Reduced investment in data center costs (hardware, software, space, utilities, server management, etc.)</span></span>

- <span data-ttu-id="21cb6-138">Elastyczne ceny (płatność na podstawie użycia, a nie bezczynności).</span><span class="sxs-lookup"><span data-stu-id="21cb6-138">Flexible pricing (pay based on usage, not for idle capacity).</span></span>

- <span data-ttu-id="21cb6-139">Ekstremalna niezawodność.</span><span class="sxs-lookup"><span data-stu-id="21cb6-139">Extreme reliability.</span></span>

- <span data-ttu-id="21cb6-140">Ulepszona mobilność aplikacji; łatwo zmienić miejsce i sposób wdrażania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="21cb6-140">Improved app mobility; easily change where and how your app is deployed.</span></span>

- <span data-ttu-id="21cb6-141">Elastyczna pojemność; w górę lub w dół w zależności od rzeczywistych potrzeb.</span><span class="sxs-lookup"><span data-stu-id="21cb6-141">Flexible capacity; scale up or down based on actual needs.</span></span>

<span data-ttu-id="21cb6-142">Tworzenie aplikacji sieci Web z ASP.NET Core, hostowanym na platformie Azure, oferuje wiele przewag konkurencyjnych w porównaniu z tradycyjnymi alternatywami.</span><span class="sxs-lookup"><span data-stu-id="21cb6-142">Building web applications with ASP.NET Core, hosted in Azure, offers many competitive advantages over traditional alternatives.</span></span> <span data-ttu-id="21cb6-143">ASP.NET Core jest zoptymalizowany pod kątem nowoczesnych praktyk tworzenia aplikacji sieci web i scenariuszy hostingu w chmurze.</span><span class="sxs-lookup"><span data-stu-id="21cb6-143">ASP.NET Core is optimized for modern web application development practices and cloud hosting scenarios.</span></span> <span data-ttu-id="21cb6-144">W tym przewodniku dowiesz się, jak zaprojektować swoje ASP.NET aplikacje podstawowe, aby jak najlepiej wykorzystać te możliwości.</span><span class="sxs-lookup"><span data-stu-id="21cb6-144">In this guide, you'll learn how to architect your ASP.NET Core applications to best take advantage of these capabilities.</span></span>

## <a name="purpose"></a><span data-ttu-id="21cb6-145">Przeznaczenie</span><span class="sxs-lookup"><span data-stu-id="21cb6-145">Purpose</span></span>

<span data-ttu-id="21cb6-146">Ten przewodnik zawiera kompleksowe wskazówki dotyczące tworzenia *monolitycznych* aplikacji sieci web przy użyciu ASP.NET Core i Azure.</span><span class="sxs-lookup"><span data-stu-id="21cb6-146">This guide provides end-to-end guidance on building *monolithic* web applications using ASP.NET Core and Azure.</span></span> <span data-ttu-id="21cb6-147">W tym kontekście "monolityczne" odnosi się do faktu, że te aplikacje są wdrażane jako pojedyncza jednostka, a nie jako zbiór usług interakcji i aplikacji.</span><span class="sxs-lookup"><span data-stu-id="21cb6-147">In this context, "monolithic" refers to the fact that these applications are deployed as a single unit, not as a collection of interacting services and applications.</span></span>

<span data-ttu-id="21cb6-148">Ten przewodnik jest uzupełnieniem ["_Mikrousług .NET. Architektura konteneryzowanych aplikacji .NET_",](../microservices/index.md) która koncentruje się bardziej na platformie Docker, Mikrousługach i wdrażaniu kontenerów do hostowania aplikacji dla przedsiębiorstw.</span><span class="sxs-lookup"><span data-stu-id="21cb6-148">This guide is complementary to the ["_.NET Microservices. Architecture for Containerized .NET Applications_"](../microservices/index.md) which focuses more on Docker, Microservices, and Deployment of Containers to host enterprise applications.</span></span>

### <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="21cb6-149">Mikrousług .NET.</span><span class="sxs-lookup"><span data-stu-id="21cb6-149">.NET Microservices.</span></span> <span data-ttu-id="21cb6-150">architektura konteneryzowanych aplikacji .NET</span><span class="sxs-lookup"><span data-stu-id="21cb6-150">Architecture for Containerized .NET Applications</span></span>

- <span data-ttu-id="21cb6-151">**książka elektroniczna**</span><span class="sxs-lookup"><span data-stu-id="21cb6-151">**e-book**</span></span>  
  <https://aka.ms/MicroservicesEbook>
- <span data-ttu-id="21cb6-152">**Przykładowa aplikacja**</span><span class="sxs-lookup"><span data-stu-id="21cb6-152">**Sample Application**</span></span>  
  <https://aka.ms/microservicesarchitecture>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="21cb6-153">Kto powinien skorzystać z tego przewodnika</span><span class="sxs-lookup"><span data-stu-id="21cb6-153">Who should use this guide</span></span>

<span data-ttu-id="21cb6-154">Odbiorcami tego przewodnika są głównie deweloperzy, potencjalni klienci i architekci zainteresowani tworzeniem nowoczesnych aplikacji internetowych przy użyciu technologii i usług firmy Microsoft w chmurze.</span><span class="sxs-lookup"><span data-stu-id="21cb6-154">The audience for this guide is mainly developers, development leads, and architects who are interested in building modern web applications using Microsoft technologies and services in the cloud.</span></span>

<span data-ttu-id="21cb6-155">Dodatkowa grupa odbiorców to decydenci techniczni, którzy są już zaznajomieni ASP.NET lub platformie Azure i szukają informacji na temat tego, czy warto uaktualnić do ASP.NET Core dla nowych lub istniejących projektów.</span><span class="sxs-lookup"><span data-stu-id="21cb6-155">A secondary audience is technical decision makers who are already familiar ASP.NET or Azure and are looking for information on whether it makes sense to upgrade to ASP.NET Core for new or existing projects.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="21cb6-156">Jak korzystać z tego przewodnika</span><span class="sxs-lookup"><span data-stu-id="21cb6-156">How you can use this guide</span></span>

<span data-ttu-id="21cb6-157">Ten przewodnik został skondensowany do stosunkowo małego dokumentu, który koncentruje się na tworzeniu aplikacji sieci web przy zastosowaniu nowoczesnych technologii .NET i systemu Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="21cb6-157">This guide has been condensed into a relatively small document that focuses on building web applications with modern .NET technologies and Windows Azure.</span></span> <span data-ttu-id="21cb6-158">W związku z tym można je przeczytać w całości, aby zapewnić podstawę zrozumienia takich zastosowań i ich względów technicznych.</span><span class="sxs-lookup"><span data-stu-id="21cb6-158">As such, it can be read in its entirety to provide a foundation of understanding such applications and their technical considerations.</span></span> <span data-ttu-id="21cb6-159">Przewodnik, wraz z jego przykładowej aplikacji, może również służyć jako punkt wyjścia lub odniesienia.</span><span class="sxs-lookup"><span data-stu-id="21cb6-159">The guide, along with its sample application, can also serve as a starting point or reference.</span></span> <span data-ttu-id="21cb6-160">Użyj skojarzonej przykładowej aplikacji jako szablonu dla własnych aplikacji lub aby zobaczyć, jak można zorganizować części składowe aplikacji.</span><span class="sxs-lookup"><span data-stu-id="21cb6-160">Use the associated sample application as a template for your own applications, or to see how you might organize your application's component parts.</span></span> <span data-ttu-id="21cb6-161">Zapoznaj się z zasadami przewodnika i zakresarchitektury i technologii opcji i zagadnień decyzji, gdy jesteś ważenia tych wyborów dla własnej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="21cb6-161">Refer back to the guide's principles and coverage of architecture and technology options and decision considerations when you're weighing these choices for your own application.</span></span>

<span data-ttu-id="21cb6-162">Nie krępuj się przekazać ten przewodnik do swojego zespołu, aby zapewnić wspólne zrozumienie tych rozważań i możliwości.</span><span class="sxs-lookup"><span data-stu-id="21cb6-162">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="21cb6-163">Posiadanie wszystkich pracujących na podstawie wspólnego zestawu terminologii i podstawowych zasad pomaga zapewnić spójne stosowanie wzorców i praktyk architektonicznych.</span><span class="sxs-lookup"><span data-stu-id="21cb6-163">Having everybody working from a common set of terminology and underlying principles helps ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="21cb6-164">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="21cb6-164">References</span></span>

- <span data-ttu-id="21cb6-165">**Wybieranie między programami .NET Core i .NET Framework na potrzeby aplikacji serwerowych**</span><span class="sxs-lookup"><span data-stu-id="21cb6-165">**Choosing between .NET Core and .NET Framework for server apps**</span></span>  
  [https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server](../../standard/choosing-core-framework-server.md)

>[!div class="step-by-step"]
>[<span data-ttu-id="21cb6-166">Dalej</span><span class="sxs-lookup"><span data-stu-id="21cb6-166">Next</span></span>](modern-web-applications-characteristics.md)
