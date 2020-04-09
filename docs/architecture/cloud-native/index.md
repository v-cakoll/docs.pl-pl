---
title: Projektowanie aplikacji platformy .NET natywnych dla chmury dla platformy Azure
description: Przewodnik do tworzenia aplikacji natywnych dla chmury, wykorzystując kontenery, mikrousług i bezserwerowych funkcji platformy Azure.
author: ardalis
ms.date: 03/07/2019
ms.openlocfilehash: cf3be07f0d37aacf4f0252ef2f4d922b7be93eee
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989067"
---
# <a name="architecting-cloud-native-net-applications-for-azure"></a><span data-ttu-id="5f54a-103">Projektowanie aplikacji platformy .NET natywnych dla chmury dla platformy Azure</span><span class="sxs-lookup"><span data-stu-id="5f54a-103">Architecting Cloud Native .NET Applications for Azure</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

![obraz okładki](./media/cover.png)

<span data-ttu-id="5f54a-105">OPUBLIKOWANA PRZEZ</span><span class="sxs-lookup"><span data-stu-id="5f54a-105">PUBLISHED BY</span></span>

<span data-ttu-id="5f54a-106">Zespoły produktów Microsoft Developer Division, .NET i Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5f54a-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="5f54a-107">Oddział firmy Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="5f54a-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="5f54a-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="5f54a-108">One Microsoft Way</span></span>

<span data-ttu-id="5f54a-109">Redmond, Waszyngton 98052-6399</span><span class="sxs-lookup"><span data-stu-id="5f54a-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="5f54a-110">Prawa &copy; autorskie 2019 firmy Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="5f54a-110">Copyright &copy; 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="5f54a-111">Wszelkie prawa zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="5f54a-111">All rights reserved.</span></span> <span data-ttu-id="5f54a-112">Żadna część zawartości tej książki nie może być powielana ani przekazywana w jakiejkolwiek formie lub w jakikolwiek sposób bez pisemnej zgody wydawcy.</span><span class="sxs-lookup"><span data-stu-id="5f54a-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="5f54a-113">Książka ta jest dostarczana "tak jak jest" i wyraża poglądy i opinie autora.</span><span class="sxs-lookup"><span data-stu-id="5f54a-113">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="5f54a-114">Poglądy, opinie i informacje wyrażone w tej książce, w tym adresy URL i inne odniesienia do stron internetowych, mogą ulec zmianie bez powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="5f54a-114">The views, opinions, and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="5f54a-115">Niektóre z przykładów przedstawiono wyłącznie do celów informacyjnych i są one fikcyjne.</span><span class="sxs-lookup"><span data-stu-id="5f54a-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="5f54a-116">Żadne rzeczywiste skojarzenia lub związki nie są zamierzone ani wnioskowane.</span><span class="sxs-lookup"><span data-stu-id="5f54a-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="5f54a-117">Firma Microsoft i znaki https://www.microsoft.com towarowe wymienione na stronie internetowej "Znaki towarowe" są znakami towarowymi grupy firm Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5f54a-117">Microsoft and the trademarks listed at https://www.microsoft.com on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="5f54a-118">Mac i macOS są znakami towarowymi firmy Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="5f54a-118">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="5f54a-119">Logo docker wielorybów jest zastrzeżonym znakiem towarowym firmy Docker, Inc. Używany za zgodą.</span><span class="sxs-lookup"><span data-stu-id="5f54a-119">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="5f54a-120">Wszystkie inne znaki i logo są własnością ich odpowiednich właścicieli.</span><span class="sxs-lookup"><span data-stu-id="5f54a-120">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="5f54a-121">Autorów:</span><span class="sxs-lookup"><span data-stu-id="5f54a-121">Authors:</span></span>

> <span data-ttu-id="5f54a-122">**Steve "ardalis" Smith** - Architekt oprogramowania i trener - [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="5f54a-122">**Steve "ardalis" Smith** - Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>
>
> <span data-ttu-id="5f54a-123">**Rob Vettor** - Microsoft - Główny architekt systemu chmury/architekt IP - [thinkingincloudnative.com](http://thinkingincloudnative.com/about/)</span><span class="sxs-lookup"><span data-stu-id="5f54a-123">**Rob Vettor** - Microsoft - Principal Cloud System Architect/IP Architect - [thinkingincloudnative.com](http://thinkingincloudnative.com/about/)</span></span>

<span data-ttu-id="5f54a-124">Uczestnicy i recenzenci:</span><span class="sxs-lookup"><span data-stu-id="5f54a-124">Participants and Reviewers:</span></span>

> <span data-ttu-id="5f54a-125">**Cesar De la Torre**, Główny Menedżer Programu, zespół .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="5f54a-125">**Cesar De la Torre**, Principal Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="5f54a-126">**Nish Anil**, Sr. Program Manager, zespół .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="5f54a-126">**Nish Anil**, Sr. Program Manager, .NET team, Microsoft</span></span>

<span data-ttu-id="5f54a-127">Edytory:</span><span class="sxs-lookup"><span data-stu-id="5f54a-127">Editors:</span></span>

> <span data-ttu-id="5f54a-128">**Maira Wenzel**, Sr. Content Developer, zespół .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="5f54a-128">**Maira Wenzel**, Sr. Content Developer, .NET team, Microsoft</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="5f54a-129">Kto powinien korzystać z tego przewodnika</span><span class="sxs-lookup"><span data-stu-id="5f54a-129">Who should use this guide</span></span>

<span data-ttu-id="5f54a-130">Odbiorcami tego przewodnika są głównie deweloperzy, potencjalni klienci programiści i architekci, którzy są zainteresowani nauką tworzenia aplikacji zaprojektowanych dla chmury.</span><span class="sxs-lookup"><span data-stu-id="5f54a-130">The audience for this guide is mainly developers, development leads, and architects who are interested in learning how to build applications designed for the cloud.</span></span>

<span data-ttu-id="5f54a-131">Dodatkową grupą odbiorców są decydenci techniczni, którzy planują wybrać, czy mają tworzyć swoje aplikacje przy użyciu podejścia natywnego dla chmury.</span><span class="sxs-lookup"><span data-stu-id="5f54a-131">A secondary audience is technical decision-makers who plan to choose whether to build their applications using a cloud-native approach.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="5f54a-132">Jak można korzystać z tego przewodnika</span><span class="sxs-lookup"><span data-stu-id="5f54a-132">How you can use this guide</span></span>

<span data-ttu-id="5f54a-133">Ten przewodnik rozpoczyna się od zdefiniowania natywnego chmury i wprowadzenia aplikacji referencyjnej utworzonej przy użyciu natywnych dla chmury zasad i technologii.</span><span class="sxs-lookup"><span data-stu-id="5f54a-133">This guide begins by defining cloud native and introducing a reference application built using cloud-native principles and technologies.</span></span> <span data-ttu-id="5f54a-134">Poza tymi dwoma pierwszymi rozdziałami, reszta książki jest podzielona na konkretne rozdziały, koncentrujące się na tematach wspólnych dla większości aplikacji natywnych dla chmury.</span><span class="sxs-lookup"><span data-stu-id="5f54a-134">Beyond these first two chapters, the rest of the book is broken up into specific chapters focused on topics common to most cloud-native applications.</span></span> <span data-ttu-id="5f54a-135">Możesz przejść do dowolnego z tych rozdziałów, aby dowiedzieć się więcej o podejściach natywnych dla chmury:</span><span class="sxs-lookup"><span data-stu-id="5f54a-135">You can jump to any of these chapters to learn about cloud-native approaches to:</span></span>

- <span data-ttu-id="5f54a-136">Dostęp do danych i danych</span><span class="sxs-lookup"><span data-stu-id="5f54a-136">Data and data access</span></span>
- <span data-ttu-id="5f54a-137">Wzorce komunikacji</span><span class="sxs-lookup"><span data-stu-id="5f54a-137">Communication patterns</span></span>
- <span data-ttu-id="5f54a-138">Skalowanie i skalowalność</span><span class="sxs-lookup"><span data-stu-id="5f54a-138">Scaling and scalability</span></span>
- <span data-ttu-id="5f54a-139">Odporność aplikacji</span><span class="sxs-lookup"><span data-stu-id="5f54a-139">Application resiliency</span></span>
- <span data-ttu-id="5f54a-140">Monitorowanie i kondycja</span><span class="sxs-lookup"><span data-stu-id="5f54a-140">Monitoring and health</span></span>
- <span data-ttu-id="5f54a-141">Tożsamość i bezpieczeństwo</span><span class="sxs-lookup"><span data-stu-id="5f54a-141">Identity and security</span></span>
- <span data-ttu-id="5f54a-142">DevOps</span><span class="sxs-lookup"><span data-stu-id="5f54a-142">DevOps</span></span>

<span data-ttu-id="5f54a-143">Ten przewodnik jest dostępny zarówno w formacie PDF, jak i online.</span><span class="sxs-lookup"><span data-stu-id="5f54a-143">This guide is available both in PDF form and online.</span></span> <span data-ttu-id="5f54a-144">Możesz przesłać ten dokument lub łącza do jego wersji online do swojego zespołu, aby zapewnić wspólne zrozumienie tych tematów.</span><span class="sxs-lookup"><span data-stu-id="5f54a-144">Feel free to forward this document or links to its online version to your team to help ensure common understanding of these topics.</span></span> <span data-ttu-id="5f54a-145">Większość z tych tematów korzysta ze spójnego zrozumienia podstawowych zasad i wzorców, a także kompromisów związanych z decyzjami związanymi z tymi tematami.</span><span class="sxs-lookup"><span data-stu-id="5f54a-145">Most of these topics benefit from a consistent understanding of the underlying principles and patterns, as well as the trade-offs involved in decisions related to these topics.</span></span> <span data-ttu-id="5f54a-146">Naszym celem w tym dokumencie jest wyposażenie zespołów i ich liderów w informacje potrzebne do podejmowania świadomych decyzji dotyczących architektury, rozwoju i hostingu ich aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5f54a-146">Our goal with this document is to equip teams and their leaders with the information they need to make well-informed decisions for their applications' architecture, development, and hosting.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="5f54a-147">Dalej</span><span class="sxs-lookup"><span data-stu-id="5f54a-147">Next</span></span>](introduction.md)
