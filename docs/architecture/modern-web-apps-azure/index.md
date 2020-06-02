---
title: Tworzenie architektury nowoczesnych aplikacji internetowych za pomocą platformy ASP.NET Core i platformy Azure
description: Przewodnik, który oferuje kompleksowe wskazówki dotyczące tworzenia monolitycznych aplikacji sieci Web przy użyciu ASP.NET Core i platformy Azure.
author: ardalis
ms.author: wiwagn
ms.date: 5/25/2020
ms.openlocfilehash: 7be03ea8edb763096b0684a62e71826f1cfcd42f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84284458"
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a><span data-ttu-id="2450d-103">Tworzenie architektury nowoczesnych aplikacji internetowych za pomocą platformy ASP.NET Core i platformy Azure</span><span class="sxs-lookup"><span data-stu-id="2450d-103">Architect Modern Web Applications with ASP.NET Core and Azure</span></span>

![Obraz okładki książki nowoczesnej aplikacji sieci Web.](./media/index/web-application-guide-cover-image.png)

<span data-ttu-id="2450d-105">**Edition w wersji 3.1** — zaktualizowany do ASP.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="2450d-105">**EDITION v3.1** - Updated to ASP.NET Core 3.1</span></span>

<span data-ttu-id="2450d-106">OPUBLIKOWANA PRZEZ</span><span class="sxs-lookup"><span data-stu-id="2450d-106">PUBLISHED BY</span></span>

<span data-ttu-id="2450d-107">Zespoły deweloperów firmy Microsoft, .NET i Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2450d-107">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="2450d-108">Dział firmy Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="2450d-108">A division of Microsoft Corporation</span></span>

<span data-ttu-id="2450d-109">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="2450d-109">One Microsoft Way</span></span>

<span data-ttu-id="2450d-110">Redmond, Waszyngton 98052-6399</span><span class="sxs-lookup"><span data-stu-id="2450d-110">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="2450d-111">Prawa autorskie © 2020 przez firmę Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="2450d-111">Copyright © 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="2450d-112">Wszelkie prawa zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="2450d-112">All rights reserved.</span></span> <span data-ttu-id="2450d-113">Żadna część zawartości tej księgi nie może być odtwarzana ani przekazywana w żadnej formie ani za pomocą jakichkolwiek środków bez zgody na wydawcę.</span><span class="sxs-lookup"><span data-stu-id="2450d-113">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="2450d-114">Ta książka jest świadczona w postaci "AS-IS" i zawiera widoki i opinie autora.</span><span class="sxs-lookup"><span data-stu-id="2450d-114">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="2450d-115">Widoki, opinie i informacje wyrażone w tej książce, w tym adresy URL i inne odwołania do witryn internetowych, mogą ulec zmianie bez powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="2450d-115">The views, opinions, and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="2450d-116">Niektóre z przykładów przedstawiono wyłącznie do celów informacyjnych i są one fikcyjne.</span><span class="sxs-lookup"><span data-stu-id="2450d-116">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="2450d-117">Żadne rzeczywiste skojarzenia lub związki nie są zamierzone ani wnioskowane.</span><span class="sxs-lookup"><span data-stu-id="2450d-117">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="2450d-118">Firma Microsoft i znaki towarowe wymienione na <https://www.microsoft.com> stronie "znaki towarowe" są znakami towarowymi grupy firm Microsoft.</span><span class="sxs-lookup"><span data-stu-id="2450d-118">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="2450d-119">Komputery Mac i macOS są znakami towarowymi firmy Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="2450d-119">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="2450d-120">Logo Docker Whale jest zastrzeżonym znakiem towarowym platformy Docker, Inc. używanym przez uprawnienie.</span><span class="sxs-lookup"><span data-stu-id="2450d-120">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="2450d-121">Wszystkie inne znaczniki i logo są własnością odpowiednich właścicieli.</span><span class="sxs-lookup"><span data-stu-id="2450d-121">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="2450d-122">Autor:</span><span class="sxs-lookup"><span data-stu-id="2450d-122">Author:</span></span>

> <span data-ttu-id="2450d-123">**Steve "ardalis" Smith** — architekt oprogramowania i Trainer- [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="2450d-123">**Steve "ardalis" Smith** - Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>

<span data-ttu-id="2450d-124">Edytory</span><span class="sxs-lookup"><span data-stu-id="2450d-124">Editors:</span></span>

> <span data-ttu-id="2450d-125">**Maira Wenzel**</span><span class="sxs-lookup"><span data-stu-id="2450d-125">**Maira Wenzel**</span></span>

## <a name="action-links"></a><span data-ttu-id="2450d-126">Linki akcji</span><span class="sxs-lookup"><span data-stu-id="2450d-126">Action links</span></span>

- <span data-ttu-id="2450d-127">Ta książka elektroniczna jest również dostępna w formacie PDF (tylko wersja w języku angielskim [).](https://aka.ms/webappebook)</span><span class="sxs-lookup"><span data-stu-id="2450d-127">This e-book is also available in a PDF format (English version only) [Download](https://aka.ms/webappebook)</span></span>

- <span data-ttu-id="2450d-128">Klonowanie/rozwidlenie aplikacji referencyjnej [eShopOnWeb w witrynie GitHub](https://github.com/dotnet-architecture/eShopOnWeb)</span><span class="sxs-lookup"><span data-stu-id="2450d-128">Clone/Fork the reference application [eShopOnWeb on GitHub](https://github.com/dotnet-architecture/eShopOnWeb)</span></span>

## <a name="introduction"></a><span data-ttu-id="2450d-129">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="2450d-129">Introduction</span></span>

<span data-ttu-id="2450d-130">Platforma .NET Core i ASP.NET Core oferują kilka korzyści w porównaniu z tradycyjnym programowaniem platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="2450d-130">.NET Core and ASP.NET Core offer several advantages over traditional .NET development.</span></span> <span data-ttu-id="2450d-131">Należy używać platformy .NET Core dla aplikacji serwerowych, jeśli niektóre lub wszystkie z następujących elementów są ważne dla sukcesu aplikacji:</span><span class="sxs-lookup"><span data-stu-id="2450d-131">You should use .NET Core for your server applications if some or all of the following are important to your application's success:</span></span>

- <span data-ttu-id="2450d-132">Obsługa wielu platform.</span><span class="sxs-lookup"><span data-stu-id="2450d-132">Cross-platform support.</span></span>

- <span data-ttu-id="2450d-133">Korzystanie z mikrousług.</span><span class="sxs-lookup"><span data-stu-id="2450d-133">Use of microservices.</span></span>

- <span data-ttu-id="2450d-134">Korzystanie z kontenerów platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="2450d-134">Use of Docker containers.</span></span>

- <span data-ttu-id="2450d-135">Wymagania dotyczące wysokiej wydajności i skalowalności.</span><span class="sxs-lookup"><span data-stu-id="2450d-135">High performance and scalability requirements.</span></span>

- <span data-ttu-id="2450d-136">Równoczesne przechowywanie wersji platformy .NET według aplikacji na tym samym serwerze.</span><span class="sxs-lookup"><span data-stu-id="2450d-136">Side-by-side versioning of .NET versions by application on the same server.</span></span>

<span data-ttu-id="2450d-137">Tradycyjne aplikacje .NET mogą i obsługują wiele z tych wymagań, ale ASP.NET Core i .NET Core zostały zoptymalizowane w celu zapewnienia lepszej obsługi powyższych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="2450d-137">Traditional .NET applications can and do support many of these requirements, but ASP.NET Core and .NET Core have been optimized to offer improved support for the above scenarios.</span></span>

<span data-ttu-id="2450d-138">Więcej i więcej organizacji umożliwia hostowanie aplikacji sieci Web w chmurze przy użyciu usług takich jak Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="2450d-138">More and more organizations are choosing to host their web applications in the cloud using services like Microsoft Azure.</span></span> <span data-ttu-id="2450d-139">Należy rozważyć hosting aplikacji w chmurze, jeśli istnieją następujące istotne dla Twojej aplikacji lub organizacji:</span><span class="sxs-lookup"><span data-stu-id="2450d-139">You should consider hosting your application in the cloud if the following are important to your application or organization:</span></span>

- <span data-ttu-id="2450d-140">Zmniejszona inwestycja w koszty centrum danych (sprzęt, oprogramowanie, miejsce, narzędzia, zarządzanie serwerem itd.)</span><span class="sxs-lookup"><span data-stu-id="2450d-140">Reduced investment in data center costs (hardware, software, space, utilities, server management, etc.)</span></span>

- <span data-ttu-id="2450d-141">Elastyczne ceny (płatność na podstawie użycia, nie do bezczynnej wydajności).</span><span class="sxs-lookup"><span data-stu-id="2450d-141">Flexible pricing (pay based on usage, not for idle capacity).</span></span>

- <span data-ttu-id="2450d-142">Wysoka niezawodność.</span><span class="sxs-lookup"><span data-stu-id="2450d-142">Extreme reliability.</span></span>

- <span data-ttu-id="2450d-143">Lepsza mobilność aplikacji; łatwo zmieniaj miejsce i sposób wdrożenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2450d-143">Improved app mobility; easily change where and how your app is deployed.</span></span>

- <span data-ttu-id="2450d-144">Elastyczna pojemność; skalowanie w górę lub w dół na podstawie rzeczywistych potrzeb.</span><span class="sxs-lookup"><span data-stu-id="2450d-144">Flexible capacity; scale up or down based on actual needs.</span></span>

<span data-ttu-id="2450d-145">Tworzenie aplikacji sieci Web za pomocą ASP.NET Core hostowanych na platformie Azure oferuje wiele konkurencyjnych korzyści w porównaniu z tradycyjnymi alternatywami.</span><span class="sxs-lookup"><span data-stu-id="2450d-145">Building web applications with ASP.NET Core, hosted in Azure, offers many competitive advantages over traditional alternatives.</span></span> <span data-ttu-id="2450d-146">ASP.NET Core jest zoptymalizowany pod kątem nowoczesnych rozwiązań do tworzenia aplikacji sieci Web i scenariuszy hostingu w chmurze.</span><span class="sxs-lookup"><span data-stu-id="2450d-146">ASP.NET Core is optimized for modern web application development practices and cloud hosting scenarios.</span></span> <span data-ttu-id="2450d-147">W tym przewodniku dowiesz się, jak zaprojektować ASP.NET Core aplikacje, aby najlepiej wykorzystać te możliwości.</span><span class="sxs-lookup"><span data-stu-id="2450d-147">In this guide, you'll learn how to architect your ASP.NET Core applications to best take advantage of these capabilities.</span></span>

## <a name="version"></a><span data-ttu-id="2450d-148">Wersja</span><span class="sxs-lookup"><span data-stu-id="2450d-148">Version</span></span>

<span data-ttu-id="2450d-149">Ten przewodnik został zmieniony w celu uwzględnienia wersji **programu .NET Core 3,1** wraz z wieloma dodatkowymi aktualizacjami związanymi z tym samymi "" Wave "technologiami (czyli platformą Azure i dodatkowymi technologiami innych firm), które są zgodne z wersją platformy .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="2450d-149">This guide has been revised to cover **.NET Core 3.1** version along with many additional updates related to the same "wave" of technologies (that is, Azure and additional third-party technologies) coinciding in time with the .NET Core 3.1 release.</span></span> <span data-ttu-id="2450d-150">Dlatego też wersja książki została zaktualizowana do wersji **3,1**.</span><span class="sxs-lookup"><span data-stu-id="2450d-150">That's why the book version has also been updated to version **3.1**.</span></span>

## <a name="purpose"></a><span data-ttu-id="2450d-151">Przeznaczenie</span><span class="sxs-lookup"><span data-stu-id="2450d-151">Purpose</span></span>

<span data-ttu-id="2450d-152">Ten przewodnik zawiera kompleksowe wskazówki dotyczące tworzenia *monolitycznych* aplikacji sieci Web przy użyciu ASP.NET Core i platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="2450d-152">This guide provides end-to-end guidance on building *monolithic* web applications using ASP.NET Core and Azure.</span></span> <span data-ttu-id="2450d-153">W tym kontekście "monolityczne" odnosi się do faktu, że te aplikacje są wdrażane jako pojedyncza jednostka, nie jako kolekcja współpracujących usług i aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2450d-153">In this context, "monolithic" refers to the fact that these applications are deployed as a single unit, not as a collection of interacting services and applications.</span></span>

<span data-ttu-id="2450d-154">Ten przewodnik uzupełnia ["_mikrousługi platformy .NET". Architektura dla kontenerów aplikacji .NET_](../microservices/index.md), które koncentrują się na platformach Docker, mikrousług i wdrażaniu kontenerów w celu hostowania aplikacji dla przedsiębiorstw.</span><span class="sxs-lookup"><span data-stu-id="2450d-154">This guide is complementary to ["_.NET Microservices. Architecture for Containerized .NET Applications_"](../microservices/index.md), which focuses more on Docker, microservices, and deployment of containers to host enterprise applications.</span></span>

### <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="2450d-155">Mikrousługi platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="2450d-155">.NET Microservices.</span></span> <span data-ttu-id="2450d-156">architektura konteneryzowanych aplikacji .NET</span><span class="sxs-lookup"><span data-stu-id="2450d-156">Architecture for Containerized .NET Applications</span></span>

- <span data-ttu-id="2450d-157">**książka elektroniczna**</span><span class="sxs-lookup"><span data-stu-id="2450d-157">**e-book**</span></span>  
  <https://aka.ms/MicroservicesEbook>
- <span data-ttu-id="2450d-158">**Przykładowa aplikacja**</span><span class="sxs-lookup"><span data-stu-id="2450d-158">**Sample Application**</span></span>  
  <https://aka.ms/microservicesarchitecture>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="2450d-159">Kto powinien korzystać z tego przewodnika</span><span class="sxs-lookup"><span data-stu-id="2450d-159">Who should use this guide</span></span>

<span data-ttu-id="2450d-160">Odbiorcy tego przewodnika są głównie deweloperzy, liderzy programistyczni i architektzy, którzy chcą tworzyć nowoczesne aplikacje sieci Web przy użyciu technologii i usług firmy Microsoft w chmurze.</span><span class="sxs-lookup"><span data-stu-id="2450d-160">The audience for this guide is mainly developers, development leads, and architects who are interested in building modern web applications using Microsoft technologies and services in the cloud.</span></span>

<span data-ttu-id="2450d-161">Dodatkowymi odbiorcami są osoby podejmujące decyzje techniczne, które już znają ASP.NET lub platformę Azure i poszukują informacji na temat tego, czy warto przeprowadzić uaktualnienie do ASP.NET Core dla nowych lub istniejących projektów.</span><span class="sxs-lookup"><span data-stu-id="2450d-161">A secondary audience is technical decision makers who are already familiar ASP.NET or Azure and are looking for information on whether it makes sense to upgrade to ASP.NET Core for new or existing projects.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="2450d-162">Jak można użyć tego przewodnika</span><span class="sxs-lookup"><span data-stu-id="2450d-162">How you can use this guide</span></span>

<span data-ttu-id="2450d-163">Ten przewodnik został skrócony do stosunkowo małego dokumentu, który koncentruje się na tworzeniu aplikacji sieci Web przy użyciu nowoczesnych technologii .NET i platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="2450d-163">This guide has been condensed into a relatively small document that focuses on building web applications with modern .NET technologies and Azure.</span></span> <span data-ttu-id="2450d-164">W związku z tym może być odczytany w całości, aby zapewnić podstawę interpretacji takich aplikacji i ich zagadnień technicznych.</span><span class="sxs-lookup"><span data-stu-id="2450d-164">As such, it can be read in its entirety to provide a foundation of understanding such applications and their technical considerations.</span></span> <span data-ttu-id="2450d-165">Przewodnik wraz z przykładową aplikacją może również stanowić punkt początkowy lub odwołanie.</span><span class="sxs-lookup"><span data-stu-id="2450d-165">The guide, along with its sample application, can also serve as a starting point or reference.</span></span> <span data-ttu-id="2450d-166">Użyj skojarzonej przykładowej aplikacji jako szablonu dla własnych aplikacji lub, aby zobaczyć, w jaki sposób można organizować części składnika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2450d-166">Use the associated sample application as a template for your own applications, or to see how you might organize your application's component parts.</span></span> <span data-ttu-id="2450d-167">Zapoznaj się z artykułami dotyczącymi zasad i zakresu architektury i technologii oraz zagadnieniami dotyczącymi decyzji o tym, kiedy oceniasz wybór dla własnej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2450d-167">Refer back to the guide's principles and coverage of architecture and technology options and decision considerations when you're weighing these choices for your own application.</span></span>

<span data-ttu-id="2450d-168">Możesz przesłać dalej ten przewodnik do zespołu, aby pomóc w zapewnieniu powszechnej wiedzy na temat tych zagadnień i możliwości.</span><span class="sxs-lookup"><span data-stu-id="2450d-168">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="2450d-169">Korzystanie ze wspólnego zestawu terminologii i podstawowych zasad pomaga zapewnić spójne stosowanie wzorców i praktyk architektury.</span><span class="sxs-lookup"><span data-stu-id="2450d-169">Having everybody working from a common set of terminology and underlying principles helps ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="2450d-170">Odwołania</span><span class="sxs-lookup"><span data-stu-id="2450d-170">References</span></span>

- <span data-ttu-id="2450d-171">**Wybieranie między programami .NET Core i .NET Framework na potrzeby aplikacji serwerowych**</span><span class="sxs-lookup"><span data-stu-id="2450d-171">**Choosing between .NET Core and .NET Framework for server apps**</span></span>  
  [https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server](../../standard/choosing-core-framework-server.md)

>[!div class="step-by-step"]
>[<span data-ttu-id="2450d-172">Dalej</span><span class="sxs-lookup"><span data-stu-id="2450d-172">Next</span></span>](modern-web-applications-characteristics.md)
