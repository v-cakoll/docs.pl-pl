---
title: Tworzenie architektury natywnych aplikacji .NET w chmurze dla platformy Azure
description: Przewodnik tworzenia aplikacji natywnych w chmurze wykorzystujących kontenery, mikrousługi i funkcje bezserwerowe platformy Azure.
author: ardalis
ms.date: 03/07/2019
ms.openlocfilehash: 67e235b051702308d2455b2501bfb59a4317635b
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214167"
---
# <a name="architecting-cloud-native-net-applications-for-azure"></a><span data-ttu-id="7dde2-103">Tworzenie architektury natywnych aplikacji .NET w chmurze dla platformy Azure</span><span class="sxs-lookup"><span data-stu-id="7dde2-103">Architecting Cloud Native .NET Applications for Azure</span></span>

![obraz okładki](./media/cover.png)

<span data-ttu-id="7dde2-105">OPUBLIKOWANO PRZEZ</span><span class="sxs-lookup"><span data-stu-id="7dde2-105">PUBLISHED BY</span></span>

<span data-ttu-id="7dde2-106">Zespoły deweloperów firmy Microsoft, .NET i Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7dde2-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="7dde2-107">Dział firmy Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="7dde2-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="7dde2-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="7dde2-108">One Microsoft Way</span></span>

<span data-ttu-id="7dde2-109">Redmond, Waszyngton 98052-6399</span><span class="sxs-lookup"><span data-stu-id="7dde2-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="7dde2-110">Prawa autorskie © 2019 przez firmę Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="7dde2-110">Copyright © 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="7dde2-111">Wszelkie prawa zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="7dde2-111">All rights reserved.</span></span> <span data-ttu-id="7dde2-112">Żadna część zawartości tej księgi nie może być odtwarzana ani przekazywana w żadnej formie ani za pomocą jakichkolwiek środków bez zgody na wydawcę.</span><span class="sxs-lookup"><span data-stu-id="7dde2-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="7dde2-113">Ta książka jest świadczona w postaci "AS-IS" i zawiera widoki i opinie autora.</span><span class="sxs-lookup"><span data-stu-id="7dde2-113">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="7dde2-114">Widoki, opinie i informacje wyrażone w tej książce, w tym adresy URL i inne odwołania do witryn internetowych, mogą ulec zmianie bez powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="7dde2-114">The views, opinions, and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="7dde2-115">Niektóre przykłady opisane w niniejszym dokumencie są dostępne tylko dla ilustracji i są fikcyjne.</span><span class="sxs-lookup"><span data-stu-id="7dde2-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="7dde2-116">Żadne prawdziwe skojarzenie lub połączenie nie jest zamierzone ani nie powinno zostać wywnioskowane.</span><span class="sxs-lookup"><span data-stu-id="7dde2-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="7dde2-117">Firma Microsoft i znaki towarowe https://www.microsoft.com wymienione na stronie "znaki towarowe" są znakami towarowymi grupy firm Microsoft.</span><span class="sxs-lookup"><span data-stu-id="7dde2-117">Microsoft and the trademarks listed at https://www.microsoft.com on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="7dde2-118">Komputery Mac i macOS są znakami towarowymi firmy Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="7dde2-118">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="7dde2-119">Logo Docker Whale jest zastrzeżonym znakiem towarowym platformy Docker, Inc. Używane przez uprawnienie.</span><span class="sxs-lookup"><span data-stu-id="7dde2-119">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="7dde2-120">Wszystkie inne znaczniki i logo są własnością odpowiednich właścicieli.</span><span class="sxs-lookup"><span data-stu-id="7dde2-120">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="7dde2-121">Autorów</span><span class="sxs-lookup"><span data-stu-id="7dde2-121">Authors:</span></span>

> <span data-ttu-id="7dde2-122">**Steve "ardalis" Smith** — architekt oprogramowania i Trainer- [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="7dde2-122">**Steve "ardalis" Smith** - Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>
>
> <span data-ttu-id="7dde2-123">**Rob Vettor** — Microsoft-Principal Cloud System Architect/IP architekt — [RobVettor.com](https://robvettor.com)</span><span class="sxs-lookup"><span data-stu-id="7dde2-123">**Rob Vettor** - Microsoft - Principal Cloud System Architect/IP Architect - [RobVettor.com](https://robvettor.com)</span></span>

<span data-ttu-id="7dde2-124">Uczestnicy i recenzenci:</span><span class="sxs-lookup"><span data-stu-id="7dde2-124">Participants and Reviewers:</span></span>

> <span data-ttu-id="7dde2-125">**Cesar de La Torre**, główny Menedżer programu, zespół .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="7dde2-125">**Cesar De la Torre**, Principal Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="7dde2-126">**Nish Anil**, SR. Program Manager, .NET Team, Microsoft</span><span class="sxs-lookup"><span data-stu-id="7dde2-126">**Nish Anil**, Sr. Program Manager, .NET team, Microsoft</span></span>

<span data-ttu-id="7dde2-127">Edytory</span><span class="sxs-lookup"><span data-stu-id="7dde2-127">Editors:</span></span>

> <span data-ttu-id="7dde2-128">**Maira Wenzel**, SR. Content Developer, .NET Team, Microsoft</span><span class="sxs-lookup"><span data-stu-id="7dde2-128">**Maira Wenzel**, Sr. Content Developer, .NET team, Microsoft</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="7dde2-129">Kto powinien korzystać z tego przewodnika</span><span class="sxs-lookup"><span data-stu-id="7dde2-129">Who should use this guide</span></span>

<span data-ttu-id="7dde2-130">Odbiorcy tego przewodnika są głównie deweloperzy, potencjalni klienci programistyczni i architektzy, którzy interesują się tworzeniem aplikacji przeznaczonych dla chmury.</span><span class="sxs-lookup"><span data-stu-id="7dde2-130">The audience for this guide is mainly developers, development leads, and architects who are interested in learning how to build applications designed for the cloud.</span></span>

<span data-ttu-id="7dde2-131">Dodatkowymi odbiorcami są, którzy decydują o wyborze, czy kompilować aplikacje przy użyciu podejścia natywnego w chmurze.</span><span class="sxs-lookup"><span data-stu-id="7dde2-131">A secondary audience is technical decision-makers who plan to choose whether to build their applications using a cloud-native approach.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="7dde2-132">Jak można użyć tego przewodnika</span><span class="sxs-lookup"><span data-stu-id="7dde2-132">How you can use this guide</span></span>

<span data-ttu-id="7dde2-133">Ten przewodnik rozpoczyna się od zdefiniowania natywnej chmury i wprowadzenia aplikacji referencyjnej skompilowanej przy użyciu zasad i technologii natywnych w chmurze.</span><span class="sxs-lookup"><span data-stu-id="7dde2-133">This guide begins by defining cloud native and introducing a reference application built using cloud-native principles and technologies.</span></span> <span data-ttu-id="7dde2-134">Oprócz tych pierwszych dwóch rozdziałów pozostała część książki jest dzielona do określonych rozdziałów ukierunkowanych na tematy wspólne dla większości aplikacji natywnych w chmurze.</span><span class="sxs-lookup"><span data-stu-id="7dde2-134">Beyond these first two chapters, the rest of the book is broken up into specific chapters focused on topics common to most cloud-native applications.</span></span> <span data-ttu-id="7dde2-135">Możesz przejść do dowolnego z tych rozdziałów, aby dowiedzieć się więcej na temat podejścia natywnego w chmurze:</span><span class="sxs-lookup"><span data-stu-id="7dde2-135">You can jump to any of these chapters to learn about cloud-native approaches to:</span></span>

- <span data-ttu-id="7dde2-136">Dostęp do danych i danych</span><span class="sxs-lookup"><span data-stu-id="7dde2-136">Data and data access</span></span>
- <span data-ttu-id="7dde2-137">Wzorce komunikacji</span><span class="sxs-lookup"><span data-stu-id="7dde2-137">Communication patterns</span></span>
- <span data-ttu-id="7dde2-138">Skalowanie i skalowalność</span><span class="sxs-lookup"><span data-stu-id="7dde2-138">Scaling and scalability</span></span>
- <span data-ttu-id="7dde2-139">Odporność aplikacji</span><span class="sxs-lookup"><span data-stu-id="7dde2-139">Application resiliency</span></span>
- <span data-ttu-id="7dde2-140">Monitorowanie i kondycja</span><span class="sxs-lookup"><span data-stu-id="7dde2-140">Monitoring and health</span></span>
- <span data-ttu-id="7dde2-141">Tożsamość i zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="7dde2-141">Identity and security</span></span>
- <span data-ttu-id="7dde2-142">DevOps</span><span class="sxs-lookup"><span data-stu-id="7dde2-142">DevOps</span></span>

<span data-ttu-id="7dde2-143">Ten przewodnik jest dostępny zarówno w formacie PDF, jak i w trybie online.</span><span class="sxs-lookup"><span data-stu-id="7dde2-143">This guide is available both in PDF form and online.</span></span> <span data-ttu-id="7dde2-144">Możesz przesłać dalej ten dokument lub linki do swojej wersji online swojego zespołu, aby pomóc w zapewnieniu powszechnego poznania się z tymi tematami.</span><span class="sxs-lookup"><span data-stu-id="7dde2-144">Feel free to forward this document or links to its online version to your team to help ensure common understanding of these topics.</span></span> <span data-ttu-id="7dde2-145">Większość z tych tematów korzysta ze spójnych zasad i wzorców, a także tych, których dotyczą decyzje związane z tymi tematami.</span><span class="sxs-lookup"><span data-stu-id="7dde2-145">Most of these topics benefit from a consistent understanding of the underlying principles and patterns, as well as the trade-offs involved in decisions related to these topics.</span></span> <span data-ttu-id="7dde2-146">Naszym celem tego dokumentu jest wyposażenie zespołów i ich liderów z informacjami potrzebnymi do podejmowania świadomych decyzji o architekturze, programowaniu i hostingu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7dde2-146">Our goal with this document is to equip teams and their leaders with the information they need to make well-informed decisions for their applications' architecture, development, and hosting.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="7dde2-147">Next</span><span class="sxs-lookup"><span data-stu-id="7dde2-147">Next</span></span>](introduction.md)
