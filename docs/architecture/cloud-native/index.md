---
title: Tworzenie architektury natywnych aplikacji .NET w chmurze dla platformy Azure
description: Przewodnik tworzenia aplikacji natywnych w chmurze wykorzystujących kontenery, mikrousługi i funkcje bezserwerowe platformy Azure.
author: ardalis
ms.date: 04/23/2020
ms.openlocfilehash: ebef97fb355cbf682b37ee441a19fbbfdd2d0dc3
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2020
ms.locfileid: "82199823"
---
# <a name="architecting-cloud-native-net-applications-for-azure"></a><span data-ttu-id="5579e-103">Tworzenie architektury natywnych aplikacji .NET w chmurze dla platformy Azure</span><span class="sxs-lookup"><span data-stu-id="5579e-103">Architecting Cloud Native .NET Applications for Azure</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

![obraz okładki](./media/cover.png)

<span data-ttu-id="5579e-105">OPUBLIKOWANA PRZEZ</span><span class="sxs-lookup"><span data-stu-id="5579e-105">PUBLISHED BY</span></span>

<span data-ttu-id="5579e-106">Zespoły deweloperów firmy Microsoft, .NET i Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5579e-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="5579e-107">Dział firmy Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="5579e-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="5579e-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="5579e-108">One Microsoft Way</span></span>

<span data-ttu-id="5579e-109">Redmond, Waszyngton 98052-6399</span><span class="sxs-lookup"><span data-stu-id="5579e-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="5579e-110">Copyright &copy; 2019 od firmy Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="5579e-110">Copyright &copy; 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="5579e-111">Wszelkie prawa zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="5579e-111">All rights reserved.</span></span> <span data-ttu-id="5579e-112">Żadna część zawartości tej księgi nie może być odtwarzana ani przekazywana w żadnej formie ani za pomocą jakichkolwiek środków bez zgody na wydawcę.</span><span class="sxs-lookup"><span data-stu-id="5579e-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="5579e-113">Ta książka jest świadczona w postaci "AS-IS" i zawiera widoki i opinie autora.</span><span class="sxs-lookup"><span data-stu-id="5579e-113">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="5579e-114">Widoki, opinie i informacje wyrażone w tej książce, w tym adresy URL i inne odwołania do witryn internetowych, mogą ulec zmianie bez powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="5579e-114">The views, opinions, and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="5579e-115">Niektóre z przykładów przedstawiono wyłącznie do celów informacyjnych i są one fikcyjne.</span><span class="sxs-lookup"><span data-stu-id="5579e-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="5579e-116">Żadne rzeczywiste skojarzenia lub związki nie są zamierzone ani wnioskowane.</span><span class="sxs-lookup"><span data-stu-id="5579e-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="5579e-117">Firma Microsoft i znaki towarowe https://www.microsoft.com wymienione na stronie "znaki towarowe" są znakami towarowymi grupy firm Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5579e-117">Microsoft and the trademarks listed at https://www.microsoft.com on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="5579e-118">Komputery Mac i macOS są znakami towarowymi firmy Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="5579e-118">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="5579e-119">Logo Docker Whale jest zastrzeżonym znakiem towarowym platformy Docker, Inc. używanym przez uprawnienie.</span><span class="sxs-lookup"><span data-stu-id="5579e-119">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="5579e-120">Wszystkie inne znaczniki i logo są własnością odpowiednich właścicieli.</span><span class="sxs-lookup"><span data-stu-id="5579e-120">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="5579e-121">Autorów</span><span class="sxs-lookup"><span data-stu-id="5579e-121">Authors:</span></span>

> <span data-ttu-id="5579e-122">**Rob Vettor**, główny architekt systemu w chmurze/IP architekt- [thinkingincloudnative.com](http://thinkingincloudnative.com/about/), Microsoft</span><span class="sxs-lookup"><span data-stu-id="5579e-122">**Rob Vettor**, Principal Cloud System Architect/IP Architect - [thinkingincloudnative.com](http://thinkingincloudnative.com/about/), Microsoft</span></span>
>
> <span data-ttu-id="5579e-123">**Steve "ardalis" Smith**, architekt oprogramowania i Trainer- [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="5579e-123">**Steve "ardalis" Smith**, Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>

<span data-ttu-id="5579e-124">Uczestnicy i recenzenci:</span><span class="sxs-lookup"><span data-stu-id="5579e-124">Participants and Reviewers:</span></span>

> <span data-ttu-id="5579e-125">**Cesar de La Torre**, główny Menedżer programu, zespół .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="5579e-125">**Cesar De la Torre**, Principal Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="5579e-126">**Nish Anil**, starszy kierownik ds. programów, .NET Team, Microsoft</span><span class="sxs-lookup"><span data-stu-id="5579e-126">**Nish Anil**, Senior Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="5579e-127">**Jeremy Likeness**, starszy kierownik ds. programów, .NET Team, Microsoft</span><span class="sxs-lookup"><span data-stu-id="5579e-127">**Jeremy Likeness**, Senior Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="5579e-128">**Cecil Phillip**, starszy ambasador w chmurze, Microsoft</span><span class="sxs-lookup"><span data-stu-id="5579e-128">**Cecil Phillip**, Senior Cloud Advocate, Microsoft</span></span>

<span data-ttu-id="5579e-129">Dowiedz się więcej o eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="5579e-129">Learn more about eShopOnContainers</span></span>

<span data-ttu-id="5579e-130">Edytory</span><span class="sxs-lookup"><span data-stu-id="5579e-130">Editors:</span></span>

> <span data-ttu-id="5579e-131">**Maira Wenzel**, Menedżer programów, .NET Team, Microsoft</span><span class="sxs-lookup"><span data-stu-id="5579e-131">**Maira Wenzel**, Program Manager, .NET team, Microsoft</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="5579e-132">Kto powinien korzystać z tego przewodnika</span><span class="sxs-lookup"><span data-stu-id="5579e-132">Who should use this guide</span></span>

<span data-ttu-id="5579e-133">Odbiorcy tego przewodnika są głównie deweloperzy, potencjalni klienci programistyczni i architektzy, którzy interesują się tworzeniem aplikacji przeznaczonych dla chmury.</span><span class="sxs-lookup"><span data-stu-id="5579e-133">The audience for this guide is mainly developers, development leads, and architects who are interested in learning how to build applications designed for the cloud.</span></span>

<span data-ttu-id="5579e-134">Dodatkowymi odbiorcami są, którzy decydują o wyborze, czy kompilować aplikacje przy użyciu podejścia natywnego w chmurze.</span><span class="sxs-lookup"><span data-stu-id="5579e-134">A secondary audience is technical decision-makers who plan to choose whether to build their applications using a cloud-native approach.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="5579e-135">Jak można użyć tego przewodnika</span><span class="sxs-lookup"><span data-stu-id="5579e-135">How you can use this guide</span></span>

<span data-ttu-id="5579e-136">Ten przewodnik rozpoczyna się od zdefiniowania natywnej chmury i wprowadzenia aplikacji referencyjnej skompilowanej przy użyciu zasad i technologii natywnych w chmurze.</span><span class="sxs-lookup"><span data-stu-id="5579e-136">This guide begins by defining cloud native and introducing a reference application built using cloud-native principles and technologies.</span></span> <span data-ttu-id="5579e-137">Oprócz tych pierwszych dwóch rozdziałów pozostała część książki jest dzielona do określonych rozdziałów ukierunkowanych na tematy wspólne dla większości aplikacji natywnych w chmurze.</span><span class="sxs-lookup"><span data-stu-id="5579e-137">Beyond these first two chapters, the rest of the book is broken up into specific chapters focused on topics common to most cloud-native applications.</span></span> <span data-ttu-id="5579e-138">Możesz przejść do dowolnego z tych rozdziałów, aby dowiedzieć się więcej na temat podejścia natywnego w chmurze:</span><span class="sxs-lookup"><span data-stu-id="5579e-138">You can jump to any of these chapters to learn about cloud-native approaches to:</span></span>

- <span data-ttu-id="5579e-139">Dostęp do danych i danych</span><span class="sxs-lookup"><span data-stu-id="5579e-139">Data and data access</span></span>
- <span data-ttu-id="5579e-140">Wzorce komunikacji</span><span class="sxs-lookup"><span data-stu-id="5579e-140">Communication patterns</span></span>
- <span data-ttu-id="5579e-141">Skalowanie i skalowalność</span><span class="sxs-lookup"><span data-stu-id="5579e-141">Scaling and scalability</span></span>
- <span data-ttu-id="5579e-142">Odporność aplikacji</span><span class="sxs-lookup"><span data-stu-id="5579e-142">Application resiliency</span></span>
- <span data-ttu-id="5579e-143">Monitorowanie i kondycja</span><span class="sxs-lookup"><span data-stu-id="5579e-143">Monitoring and health</span></span>
- <span data-ttu-id="5579e-144">Tożsamość i zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="5579e-144">Identity and security</span></span>
- <span data-ttu-id="5579e-145">DevOps</span><span class="sxs-lookup"><span data-stu-id="5579e-145">DevOps</span></span>

<span data-ttu-id="5579e-146">Ten przewodnik jest dostępny zarówno w formacie PDF, jak i w trybie online.</span><span class="sxs-lookup"><span data-stu-id="5579e-146">This guide is available both in PDF form and online.</span></span> <span data-ttu-id="5579e-147">Możesz przesłać dalej ten dokument lub linki do swojej wersji online swojego zespołu, aby pomóc w zapewnieniu powszechnego poznania się z tymi tematami.</span><span class="sxs-lookup"><span data-stu-id="5579e-147">Feel free to forward this document or links to its online version to your team to help ensure common understanding of these topics.</span></span> <span data-ttu-id="5579e-148">Większość z tych tematów korzysta ze spójnych zasad i wzorców, a także tych, których dotyczą decyzje związane z tymi tematami.</span><span class="sxs-lookup"><span data-stu-id="5579e-148">Most of these topics benefit from a consistent understanding of the underlying principles and patterns, as well as the trade-offs involved in decisions related to these topics.</span></span> <span data-ttu-id="5579e-149">Naszym celem tego dokumentu jest wyposażenie zespołów i ich liderów z informacjami potrzebnymi do podejmowania świadomych decyzji o architekturze, programowaniu i hostingu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5579e-149">Our goal with this document is to equip teams and their leaders with the information they need to make well-informed decisions for their applications' architecture, development, and hosting.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="5579e-150">Dalej</span><span class="sxs-lookup"><span data-stu-id="5579e-150">Next</span></span>](introduction.md)
