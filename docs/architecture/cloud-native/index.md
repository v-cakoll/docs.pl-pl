---
title: Tworzenie architektury natywnych aplikacji .NET w chmurze dla platformy Azure
description: Przewodnik tworzenia aplikacji natywnych w chmurze wykorzystujących kontenery, mikrousługi i funkcje bezserwerowe platformy Azure.
author: ardalis
ms.date: 05/13/2020
ms.openlocfilehash: 1607c1bbcc9bbb3c9fe19840a2827aa5ea083728
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614005"
---
# <a name="architecting-cloud-native-net-applications-for-azure"></a><span data-ttu-id="c86ab-103">Tworzenie architektury natywnych aplikacji .NET w chmurze dla platformy Azure</span><span class="sxs-lookup"><span data-stu-id="c86ab-103">Architecting Cloud Native .NET Applications for Azure</span></span>

![obraz okładki](./media/cover.png)

<span data-ttu-id="c86ab-105">**Wersja 1.0**</span><span class="sxs-lookup"><span data-stu-id="c86ab-105">**EDITION v.1.0**</span></span>

<span data-ttu-id="c86ab-106">OPUBLIKOWANA PRZEZ</span><span class="sxs-lookup"><span data-stu-id="c86ab-106">PUBLISHED BY</span></span>

<span data-ttu-id="c86ab-107">Zespoły deweloperów firmy Microsoft, .NET i Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c86ab-107">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="c86ab-108">Dział firmy Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="c86ab-108">A division of Microsoft Corporation</span></span>

<span data-ttu-id="c86ab-109">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="c86ab-109">One Microsoft Way</span></span>

<span data-ttu-id="c86ab-110">Redmond, Waszyngton 98052-6399</span><span class="sxs-lookup"><span data-stu-id="c86ab-110">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="c86ab-111">Copyright &copy; 2020 od firmy Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="c86ab-111">Copyright &copy; 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="c86ab-112">Wszelkie prawa zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="c86ab-112">All rights reserved.</span></span> <span data-ttu-id="c86ab-113">Żadna część zawartości tej księgi nie może być odtwarzana ani przekazywana w żadnej formie ani za pomocą jakichkolwiek środków bez zgody na wydawcę.</span><span class="sxs-lookup"><span data-stu-id="c86ab-113">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="c86ab-114">Ta książka jest świadczona w postaci "AS-IS" i zawiera widoki i opinie autora.</span><span class="sxs-lookup"><span data-stu-id="c86ab-114">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="c86ab-115">Widoki, opinie i informacje wyrażone w tej książce, w tym adresy URL i inne odwołania do witryn internetowych, mogą ulec zmianie bez powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="c86ab-115">The views, opinions, and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="c86ab-116">Niektóre z przykładów przedstawiono wyłącznie do celów informacyjnych i są one fikcyjne.</span><span class="sxs-lookup"><span data-stu-id="c86ab-116">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="c86ab-117">Żadne rzeczywiste skojarzenia lub związki nie są zamierzone ani wnioskowane.</span><span class="sxs-lookup"><span data-stu-id="c86ab-117">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="c86ab-118">Firma Microsoft i znaki towarowe wymienione na https://www.microsoft.com stronie "znaki towarowe" są znakami towarowymi grupy firm Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c86ab-118">Microsoft and the trademarks listed at https://www.microsoft.com on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="c86ab-119">Komputery Mac i macOS są znakami towarowymi firmy Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="c86ab-119">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="c86ab-120">Logo Docker Whale jest zastrzeżonym znakiem towarowym platformy Docker, Inc. używanym przez uprawnienie.</span><span class="sxs-lookup"><span data-stu-id="c86ab-120">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="c86ab-121">Wszystkie inne znaczniki i logo są własnością odpowiednich właścicieli.</span><span class="sxs-lookup"><span data-stu-id="c86ab-121">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="c86ab-122">Autorów</span><span class="sxs-lookup"><span data-stu-id="c86ab-122">Authors:</span></span>

> <span data-ttu-id="c86ab-123">**Rob Vettor**, główny architekt systemu w chmurze/IP architekt- [thinkingincloudnative.com](http://thinkingincloudnative.com/about/), Microsoft</span><span class="sxs-lookup"><span data-stu-id="c86ab-123">**Rob Vettor**, Principal Cloud System Architect/IP Architect - [thinkingincloudnative.com](http://thinkingincloudnative.com/about/), Microsoft</span></span>
>
> <span data-ttu-id="c86ab-124">**Steve "ardalis" Smith**, architekt oprogramowania i Trainer- [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="c86ab-124">**Steve "ardalis" Smith**, Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>

<span data-ttu-id="c86ab-125">Uczestnicy i recenzenci:</span><span class="sxs-lookup"><span data-stu-id="c86ab-125">Participants and Reviewers:</span></span>

> <span data-ttu-id="c86ab-126">**Cesar de La Torre**, główny Menedżer programu, zespół .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="c86ab-126">**Cesar De la Torre**, Principal Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="c86ab-127">**Nish Anil**, starszy kierownik ds. programów, .NET Team, Microsoft</span><span class="sxs-lookup"><span data-stu-id="c86ab-127">**Nish Anil**, Senior Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="c86ab-128">**Jeremy Likness**, starszy kierownik ds. programów, .NET Team, Microsoft</span><span class="sxs-lookup"><span data-stu-id="c86ab-128">**Jeremy Likness**, Senior Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="c86ab-129">**Cecil Phillip**, starszy ambasador w chmurze, Microsoft</span><span class="sxs-lookup"><span data-stu-id="c86ab-129">**Cecil Phillip**, Senior Cloud Advocate, Microsoft</span></span>

<span data-ttu-id="c86ab-130">Edytory</span><span class="sxs-lookup"><span data-stu-id="c86ab-130">Editors:</span></span>

> <span data-ttu-id="c86ab-131">**Maira Wenzel**, Menedżer programów, .NET Team, Microsoft</span><span class="sxs-lookup"><span data-stu-id="c86ab-131">**Maira Wenzel**, Program Manager, .NET team, Microsoft</span></span>

## <a name="version"></a><span data-ttu-id="c86ab-132">Wersja</span><span class="sxs-lookup"><span data-stu-id="c86ab-132">Version</span></span>

<span data-ttu-id="c86ab-133">Ten przewodnik został zapisany w celu uwzględnienia wersji **programu .NET Core 3,1** wraz z wieloma dodatkowymi aktualizacjami związanymi z tym samym "" Wave "technologiami (czyli platformą Azure i dodatkowymi technologiami innych firm), które są zgodne z wersją platformy .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="c86ab-133">This guide has been written to cover **.NET Core 3.1** version along with many additional updates related to the same “wave” of technologies (that is, Azure and additional third-party technologies) coinciding in time with the .NET Core 3.1 release.</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="c86ab-134">Kto powinien korzystać z tego przewodnika</span><span class="sxs-lookup"><span data-stu-id="c86ab-134">Who should use this guide</span></span>

<span data-ttu-id="c86ab-135">Odbiorcy tego przewodnika są głównie deweloperzy, potencjalni klienci programistyczni i architektzy, którzy interesują się tworzeniem aplikacji przeznaczonych dla chmury.</span><span class="sxs-lookup"><span data-stu-id="c86ab-135">The audience for this guide is mainly developers, development leads, and architects who are interested in learning how to build applications designed for the cloud.</span></span>

<span data-ttu-id="c86ab-136">Dodatkowymi odbiorcami są, którzy decydują o wyborze, czy kompilować aplikacje przy użyciu podejścia natywnego w chmurze.</span><span class="sxs-lookup"><span data-stu-id="c86ab-136">A secondary audience is technical decision-makers who plan to choose whether to build their applications using a cloud-native approach.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="c86ab-137">Jak można użyć tego przewodnika</span><span class="sxs-lookup"><span data-stu-id="c86ab-137">How you can use this guide</span></span>

<span data-ttu-id="c86ab-138">Ten przewodnik rozpoczyna się od zdefiniowania natywnej chmury i wprowadzenia aplikacji referencyjnej skompilowanej przy użyciu zasad i technologii natywnych w chmurze.</span><span class="sxs-lookup"><span data-stu-id="c86ab-138">This guide begins by defining cloud native and introducing a reference application built using cloud-native principles and technologies.</span></span> <span data-ttu-id="c86ab-139">Oprócz tych pierwszych dwóch rozdziałów pozostała część książki jest dzielona do określonych rozdziałów ukierunkowanych na tematy wspólne dla większości aplikacji natywnych w chmurze.</span><span class="sxs-lookup"><span data-stu-id="c86ab-139">Beyond these first two chapters, the rest of the book is broken up into specific chapters focused on topics common to most cloud-native applications.</span></span> <span data-ttu-id="c86ab-140">Możesz przejść do dowolnego z tych rozdziałów, aby dowiedzieć się więcej na temat podejścia natywnego w chmurze:</span><span class="sxs-lookup"><span data-stu-id="c86ab-140">You can jump to any of these chapters to learn about cloud-native approaches to:</span></span>

- <span data-ttu-id="c86ab-141">Dostęp do danych i danych</span><span class="sxs-lookup"><span data-stu-id="c86ab-141">Data and data access</span></span>
- <span data-ttu-id="c86ab-142">Wzorce komunikacji</span><span class="sxs-lookup"><span data-stu-id="c86ab-142">Communication patterns</span></span>
- <span data-ttu-id="c86ab-143">Skalowanie i skalowalność</span><span class="sxs-lookup"><span data-stu-id="c86ab-143">Scaling and scalability</span></span>
- <span data-ttu-id="c86ab-144">Odporność aplikacji</span><span class="sxs-lookup"><span data-stu-id="c86ab-144">Application resiliency</span></span>
- <span data-ttu-id="c86ab-145">Monitorowanie i kondycja</span><span class="sxs-lookup"><span data-stu-id="c86ab-145">Monitoring and health</span></span>
- <span data-ttu-id="c86ab-146">Tożsamość i zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="c86ab-146">Identity and security</span></span>
- <span data-ttu-id="c86ab-147">DevOps</span><span class="sxs-lookup"><span data-stu-id="c86ab-147">DevOps</span></span>

<span data-ttu-id="c86ab-148">Ten przewodnik jest dostępny zarówno w formacie PDF, jak i w trybie online.</span><span class="sxs-lookup"><span data-stu-id="c86ab-148">This guide is available both in PDF form and online.</span></span> <span data-ttu-id="c86ab-149">Możesz przesłać dalej ten dokument lub linki do swojej wersji online swojego zespołu, aby pomóc w zapewnieniu powszechnego poznania się z tymi tematami.</span><span class="sxs-lookup"><span data-stu-id="c86ab-149">Feel free to forward this document or links to its online version to your team to help ensure common understanding of these topics.</span></span> <span data-ttu-id="c86ab-150">Większość z tych tematów korzysta ze spójnych zasad i wzorców, a także tych, których dotyczą decyzje związane z tymi tematami.</span><span class="sxs-lookup"><span data-stu-id="c86ab-150">Most of these topics benefit from a consistent understanding of the underlying principles and patterns, as well as the trade-offs involved in decisions related to these topics.</span></span> <span data-ttu-id="c86ab-151">Naszym celem tego dokumentu jest wyposażenie zespołów i ich liderów z informacjami potrzebnymi do podejmowania świadomych decyzji o architekturze, programowaniu i hostingu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c86ab-151">Our goal with this document is to equip teams and their leaders with the information they need to make well-informed decisions for their applications' architecture, development, and hosting.</span></span>

## <a name="send-your-feedback"></a><span data-ttu-id="c86ab-152">Wyślij opinię</span><span class="sxs-lookup"><span data-stu-id="c86ab-152">Send your feedback</span></span>

<span data-ttu-id="c86ab-153">Ta książka i powiązane przykłady są ciągle zmieniane, dzięki czemu Twoje opinie są gotowe!</span><span class="sxs-lookup"><span data-stu-id="c86ab-153">This book and related samples are constantly evolving, so your feedback is welcomed!</span></span> <span data-ttu-id="c86ab-154">Jeśli masz komentarze dotyczące sposobu, w jaki można ulepszyć tę książkę, Skorzystaj z sekcji opinia w dolnej części strony utworzonej w witrynie [GitHub](https://github.com/dotnet/docs/issues).</span><span class="sxs-lookup"><span data-stu-id="c86ab-154">If you have comments about how this book can be improved, use the feedback section at the bottom of any page built on [GitHub issues](https://github.com/dotnet/docs/issues).</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="c86ab-155">Dalej</span><span class="sxs-lookup"><span data-stu-id="c86ab-155">Next</span></span>](introduction.md)
