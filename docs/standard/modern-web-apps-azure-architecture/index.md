---
title: Projektowania nowoczesnych aplikacji sieci web za pomocą platformy ASP.NET Core i platformy Azure
description: Przewodnik, który dostarcza wskazówki end-to-end na tworzeniu aplikacji monolitycznych internetowych przy użyciu platformy ASP.NET Core i platformy Azure.
author: ardalis
ms.author: wiwagn
ms.date: 06/28/2018
ms.openlocfilehash: 0d59a07e01897400a53f48799383d1670a468d73
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53148109"
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a><span data-ttu-id="7ec4c-103">Projektowania nowoczesnych aplikacji sieci Web za pomocą platformy ASP.NET Core i platformy Azure</span><span class="sxs-lookup"><span data-stu-id="7ec4c-103">Architect Modern Web Applications with ASP.NET Core and Azure</span></span>

![Obraz okładki](./media/cover.png)

<span data-ttu-id="7ec4c-105">OPUBLIKOWANE PRZEZ</span><span class="sxs-lookup"><span data-stu-id="7ec4c-105">PUBLISHED BY</span></span>

<span data-ttu-id="7ec4c-106">Zespoły produktu Microsoft Developer Division, .NET i Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7ec4c-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="7ec4c-107">Dzielenie firmy Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="7ec4c-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="7ec4c-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="7ec4c-108">One Microsoft Way</span></span>

<span data-ttu-id="7ec4c-109">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="7ec4c-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="7ec4c-110">Copyright © 2018 Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="7ec4c-110">Copyright © 2018 by Microsoft Corporation</span></span>

<span data-ttu-id="7ec4c-111">Wszelkie prawa zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="7ec4c-111">All rights reserved.</span></span> <span data-ttu-id="7ec4c-112">Nie części zawartości tej książki może odtworzyć lub przenoszone w jakiejkolwiek formie lub za pomocą jakichkolwiek środków bez pisemnej zgody wydawcy.</span><span class="sxs-lookup"><span data-stu-id="7ec4c-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="7ec4c-113">Ten podręcznik jest dostarczany "jako — jest" i wyraża, widoki i opinie od autora.</span><span class="sxs-lookup"><span data-stu-id="7ec4c-113">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="7ec4c-114">Widoki, opinie i informacje wyrażone w tym podręczniku, w tym adresy URL i inne odnośniki do witryn internetowych, mogą ulec zmianie bez powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="7ec4c-114">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="7ec4c-115">Niektóre przedstawione przykłady znajdują się wyłącznie do celów informacyjnych i są fikcyjne.</span><span class="sxs-lookup"><span data-stu-id="7ec4c-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="7ec4c-116">Nie rzeczywiste skojarzenia ani powiązania nie są zamierzone ani powinny być zakładane.</span><span class="sxs-lookup"><span data-stu-id="7ec4c-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="7ec4c-117">Firma Microsoft i znaków towarowych, opisane w temacie https://www.microsoft.com na stronie sieci Web "Znakami" są znakami towarowymi grupy firm Microsoft.</span><span class="sxs-lookup"><span data-stu-id="7ec4c-117">Microsoft and the trademarks listed at https://www.microsoft.com on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="7ec4c-118">Komputery Mac i z systemem macOS są znakami towarowymi firmy Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="7ec4c-118">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="7ec4c-119">Logo whale platformy Docker jest zastrzeżonym znakiem towarowym firmy Docker, Inc. Używane przez uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="7ec4c-119">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="7ec4c-120">Wszystkie inne znaki i logo są własnością ich prawnych właścicieli.</span><span class="sxs-lookup"><span data-stu-id="7ec4c-120">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="7ec4c-121">Autor:</span><span class="sxs-lookup"><span data-stu-id="7ec4c-121">Author:</span></span>

> <span data-ttu-id="7ec4c-122">**Steve Smith (@ardalis)**, Doradca architektury oprogramowania, [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="7ec4c-122">**Steve Smith (@ardalis)**, Software Architecture Advisor, [Ardalis.com](https://ardalis.com)</span></span>

<span data-ttu-id="7ec4c-123">Edytory:</span><span class="sxs-lookup"><span data-stu-id="7ec4c-123">Editors:</span></span>

> <span data-ttu-id="7ec4c-124">**Maira Wenzel**</span><span class="sxs-lookup"><span data-stu-id="7ec4c-124">**Maira Wenzel**</span></span>

## <a name="introduction"></a><span data-ttu-id="7ec4c-125">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="7ec4c-125">Introduction</span></span>

<span data-ttu-id="7ec4c-126">.NET core i ASP.NET Core oferują wiele zalet w porównaniu do tradycyjnego programowania na platformie .NET.</span><span class="sxs-lookup"><span data-stu-id="7ec4c-126">.NET Core and ASP.NET Core offer several advantages over traditional .NET development.</span></span> <span data-ttu-id="7ec4c-127">Jeśli niektóre lub wszystkie z następujących czynności są ważne dla Powodzenie swojej aplikacji, należy użyć platformy .NET Core dla aplikacji serwera:</span><span class="sxs-lookup"><span data-stu-id="7ec4c-127">You should use .NET Core for your server applications if some or all of the following are important to your application's success:</span></span>

- <span data-ttu-id="7ec4c-128">Obsługa wielu platform.</span><span class="sxs-lookup"><span data-stu-id="7ec4c-128">Cross-platform support.</span></span>

- <span data-ttu-id="7ec4c-129">Korzystanie z mikrousług.</span><span class="sxs-lookup"><span data-stu-id="7ec4c-129">Use of microservices.</span></span>

- <span data-ttu-id="7ec4c-130">Korzystanie z kontenerów platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="7ec4c-130">Use of Docker containers.</span></span>

- <span data-ttu-id="7ec4c-131">Wymagania wysokiej wydajności i skalowalności.</span><span class="sxs-lookup"><span data-stu-id="7ec4c-131">High performance and scalability requirements.</span></span>

- <span data-ttu-id="7ec4c-132">Side-by-side wersji programu .NET w wersji przez aplikację na tym samym serwerze.</span><span class="sxs-lookup"><span data-stu-id="7ec4c-132">Side-by-side versioning of .NET versions by application on the same server.</span></span>

<span data-ttu-id="7ec4c-133">Tradycyjne aplikacje .NET można i należy zapewnić obsługę tych wymagań, ale platformy ASP.NET Core i .NET Core zostały zoptymalizowane do zaoferowania Ulepszona obsługa dla powyższych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="7ec4c-133">Traditional .NET applications can and do support these requirements, but ASP.NET Core and .NET Core have been optimized to offer improved support for the above scenarios.</span></span>

<span data-ttu-id="7ec4c-134">Coraz więcej organizacji decyduje się na hostowanie aplikacji sieci web w chmurze przy użyciu usług takich jak Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="7ec4c-134">More and more organizations are choosing to host their web applications in the cloud using services like Microsoft Azure.</span></span> <span data-ttu-id="7ec4c-135">Należy rozważyć obsługę aplikacji w chmurze, jeśli następujące usługi są ważne do aplikacji lub organizacji:</span><span class="sxs-lookup"><span data-stu-id="7ec4c-135">You should consider hosting your application in the cloud if the following are important to your application or organization:</span></span>

- <span data-ttu-id="7ec4c-136">Inwestycji zmniejszenie kosztów centrum danych (sprzętu, oprogramowania, miejsca, narzędzia itp.)</span><span class="sxs-lookup"><span data-stu-id="7ec4c-136">Reduced investment in data center costs (hardware, software, space, utilities, etc.)</span></span>

- <span data-ttu-id="7ec4c-137">Elastyczny cennik (płatność na podstawie użycia, nie za bezczynną dyspozycyjność).</span><span class="sxs-lookup"><span data-stu-id="7ec4c-137">Flexible pricing (pay based on usage, not for idle capacity).</span></span>

- <span data-ttu-id="7ec4c-138">Extreme niezawodność.</span><span class="sxs-lookup"><span data-stu-id="7ec4c-138">Extreme reliability.</span></span>

- <span data-ttu-id="7ec4c-139">Mobilność aplikacji została poprawiona; łatwo zmienić, gdzie i w jaki sposób Twoja aplikacja jest wdrożona.</span><span class="sxs-lookup"><span data-stu-id="7ec4c-139">Improved app mobility; easily change where and how your app is deployed.</span></span>

- <span data-ttu-id="7ec4c-140">Elastyczna pojemność; Skalowanie w górę lub w dół na podstawie rzeczywistych potrzeb.</span><span class="sxs-lookup"><span data-stu-id="7ec4c-140">Flexible capacity; scale up or down based on actual needs.</span></span>

<span data-ttu-id="7ec4c-141">Tworzenie aplikacji sieci web za pomocą programu ASP.NET Core, hostowanych na platformie Azure, oferuje wiele przewagi nad alternatyw tradycyjnych.</span><span class="sxs-lookup"><span data-stu-id="7ec4c-141">Building web applications with ASP.NET Core, hosted in Azure, offers many competitive advantages over traditional alternatives.</span></span> <span data-ttu-id="7ec4c-142">Platforma ASP.NET Core jest zoptymalizowany pod kątem wytwarzania oprogramowania aplikacji nowoczesne rozwiązania sieci web i w chmurze, w scenariuszach hostingu.</span><span class="sxs-lookup"><span data-stu-id="7ec4c-142">ASP.NET Core is optimized for modern web application development practices and cloud hosting scenarios.</span></span> <span data-ttu-id="7ec4c-143">W tym przewodniku dowiesz się, jak zaprojektować najlepsze wykorzystanie tych możliwości aplikacji platformy ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="7ec4c-143">In this guide, you'll learn how to architect your ASP.NET Core applications to best take advantage of these capabilities.</span></span>

## <a name="purpose"></a><span data-ttu-id="7ec4c-144">Cel</span><span class="sxs-lookup"><span data-stu-id="7ec4c-144">Purpose</span></span>

<span data-ttu-id="7ec4c-145">Ten przewodnik zawiera wskazówki dotyczące end-to-end na tworzeniu aplikacji monolitycznych internetowych przy użyciu platformy ASP.NET Core i platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="7ec4c-145">This guide provides end-to-end guidance on building monolithic web applications using ASP.NET Core and Azure.</span></span>

<span data-ttu-id="7ec4c-146">Ten przewodnik jest uzupełnieniem ["_Mikrousługi .NET. Architektura aplikacji kontenerowych nimi .NET_"](../microservices-architecture/index.md) hostowanie aplikacji przedsiębiorstwa który skupia się więcej na platformy Docker, Mikrousługi i wdrażanie kontenerów.</span><span class="sxs-lookup"><span data-stu-id="7ec4c-146">This guide is complementary to the ["_.NET Microservices. Architecture for Containerized .NET Applications_"](../microservices-architecture/index.md) which focuses more on Docker, Microservices, and Deployment of Containers to host enterprise applications.</span></span>

### <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="7ec4c-147">Mikrousługi .NET.</span><span class="sxs-lookup"><span data-stu-id="7ec4c-147">.NET Microservices.</span></span> <span data-ttu-id="7ec4c-148">Architektura konteneryzowanych aplikacji .NET</span><span class="sxs-lookup"><span data-stu-id="7ec4c-148">Architecture for Containerized .NET Applications</span></span>

- <span data-ttu-id="7ec4c-149">**e-book**</span><span class="sxs-lookup"><span data-stu-id="7ec4c-149">**e-book**</span></span>  
  <https://aka.ms/MicroservicesEbook>
- <span data-ttu-id="7ec4c-150">**Przykładowa aplikacja**</span><span class="sxs-lookup"><span data-stu-id="7ec4c-150">**Sample Application**</span></span>  
  <https://aka.ms/microservicesarchitecture>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="7ec4c-151">Kto powinien używać tego przewodnika</span><span class="sxs-lookup"><span data-stu-id="7ec4c-151">Who should use this guide</span></span>

<span data-ttu-id="7ec4c-152">Odbiorcami tego przewodnika jest przede wszystkim deweloperom, kierownikami ds. programowania i architektów, którzy są zainteresowani tworzenia nowoczesnych aplikacji internetowych przy użyciu technologii firmy Microsoft i usługi w chmurze.</span><span class="sxs-lookup"><span data-stu-id="7ec4c-152">The audience for this guide is mainly developers, development leads, and architects who are interested in building modern web applications using Microsoft technologies and services in the cloud.</span></span>

<span data-ttu-id="7ec4c-153">Pomocniczy odbiorców jest techniczne inne osoby podejmujące decyzje, którzy już znanych ASP.NET lub na platformie Azure i szukasz informacji na temat tego, czy warto uaktualnić do programu ASP.NET Core dla nowych lub istniejących projektów.</span><span class="sxs-lookup"><span data-stu-id="7ec4c-153">A secondary audience is technical decision makers who are already familiar ASP.NET or Azure and are looking for information on whether it makes sense to upgrade to ASP.NET Core for new or existing projects.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="7ec4c-154">Jak można użyć tego przewodnika</span><span class="sxs-lookup"><span data-stu-id="7ec4c-154">How you can use this guide</span></span>

<span data-ttu-id="7ec4c-155">Ten przewodnik zawiera zostało zmniejszone do stosunkowo mały dokument, który koncentruje się na tworzeniu aplikacji sieci web za pomocą nowoczesnych technologii .NET i usługi Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="7ec4c-155">This guide has been condensed into a relatively small document that focuses on building web applications with modern .NET technologies and Windows Azure.</span></span> <span data-ttu-id="7ec4c-156">W efekcie mogą być odczytywane w całości, aby zapewnić podstawę zrozumienia tego typu aplikacji i ich zagadnienia techniczne.</span><span class="sxs-lookup"><span data-stu-id="7ec4c-156">As such, it can be read in its entirety to provide a foundation of understanding such applications and their technical considerations.</span></span> <span data-ttu-id="7ec4c-157">Przewodnik, wraz z przykładowej aplikacji, może również służyć jako punkt początkowy lub odwołania.</span><span class="sxs-lookup"><span data-stu-id="7ec4c-157">The guide, along with its sample application, can also serve as a starting point or reference.</span></span> <span data-ttu-id="7ec4c-158">Skojarzone przykładowej aplikacji należy użyć jako szablonu dla własnych aplikacjach lub aby zobaczyć, jak możesz organizować części składnika swojej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7ec4c-158">Use the associated sample application as a template for your own applications, or to see how you might organize your application's component parts.</span></span> <span data-ttu-id="7ec4c-159">Odnoszą się do zasad i pokrycie architektury i technologii opcje i zagadnienia dotyczące decyzji Przewodnik po należy zwrócić uwagę na te opcje dla swojej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7ec4c-159">Refer back to the guide's principles and coverage of architecture and technology options and decision considerations when you're weighing these choices for your own application.</span></span>

<span data-ttu-id="7ec4c-160">Możesz przekazywać tego przewodnika, aby Twój zespół do pomagają zagwarantować, że te zagadnienia i możliwości.</span><span class="sxs-lookup"><span data-stu-id="7ec4c-160">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="7ec4c-161">Posiadanie wszystkich działa z wspólny zbiór terminologii i podstawowymi zasadami pomaga zapewnić spójnego stosowania architektury wzorców i praktyk.</span><span class="sxs-lookup"><span data-stu-id="7ec4c-161">Having everybody working from a common set of terminology and underlying principles helps ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="7ec4c-162">Odwołania</span><span class="sxs-lookup"><span data-stu-id="7ec4c-162">References</span></span>

- <span data-ttu-id="7ec4c-163">**Wybieranie między programami .NET Core i .NET Framework na potrzeby aplikacji serwerowych**</span><span class="sxs-lookup"><span data-stu-id="7ec4c-163">**Choosing between .NET Core and .NET Framework for server apps**</span></span>  
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server>

>[!div class="step-by-step"]
>[<span data-ttu-id="7ec4c-164">Next</span><span class="sxs-lookup"><span data-stu-id="7ec4c-164">Next</span></span>](modern-web-applications-characteristics.md)