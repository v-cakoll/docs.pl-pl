---
title: ASP.NET Core gRPC dla programistów WCF - gRPC dla programistów WCF
description: Wprowadzenie do tworzenia usług gRPC w ASP.NET Core 3.0 dla programistów WCF
ms.date: 09/02/2019
ms.openlocfilehash: 175dfbf1880a0937615543c248fba3bed0e25c23
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988963"
---
# <a name="aspnet-core-grpc-for-wcf-developers"></a><span data-ttu-id="d773e-103">Usługa gRPC platformy ASP.NET Core dla deweloperów WCF</span><span class="sxs-lookup"><span data-stu-id="d773e-103">ASP.NET Core gRPC for WCF Developers</span></span>

![obraz okładki](./media/cover.png)

<span data-ttu-id="d773e-105">OPUBLIKOWANA PRZEZ</span><span class="sxs-lookup"><span data-stu-id="d773e-105">PUBLISHED BY</span></span>

<span data-ttu-id="d773e-106">Zespoły produktów Microsoft Developer Division, .NET i Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d773e-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="d773e-107">Oddział firmy Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="d773e-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="d773e-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="d773e-108">One Microsoft Way</span></span>

<span data-ttu-id="d773e-109">Redmond, Waszyngton 98052-6399</span><span class="sxs-lookup"><span data-stu-id="d773e-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="d773e-110">Prawa autorskie © 2019 przez Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="d773e-110">Copyright © 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="d773e-111">Wszelkie prawa zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="d773e-111">All rights reserved.</span></span> <span data-ttu-id="d773e-112">Żadna część zawartości tej książki nie może być powielana ani przekazywana w jakiejkolwiek formie lub w jakikolwiek sposób bez pisemnej zgody wydawcy.</span><span class="sxs-lookup"><span data-stu-id="d773e-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="d773e-113">Książka ta jest dostarczana "tak jak jest" i wyraża poglądy i opinie autora.</span><span class="sxs-lookup"><span data-stu-id="d773e-113">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="d773e-114">Poglądy, opinie i informacje wyrażone w tej książce, w tym adresy URL i inne odniesienia do stron internetowych, mogą ulec zmianie bez powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="d773e-114">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="d773e-115">Niektóre z przykładów przedstawiono wyłącznie do celów informacyjnych i są one fikcyjne.</span><span class="sxs-lookup"><span data-stu-id="d773e-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="d773e-116">Żadne rzeczywiste skojarzenia lub związki nie są zamierzone ani wnioskowane.</span><span class="sxs-lookup"><span data-stu-id="d773e-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="d773e-117">Firma Microsoft i znaki https://www.microsoft.com towarowe wymienione na stronie internetowej "Znaki towarowe" są znakami towarowymi grupy firm Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d773e-117">Microsoft and the trademarks listed at https://www.microsoft.com on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="d773e-118">Logo docker wielorybów jest zastrzeżonym znakiem towarowym firmy Docker, Inc. Używany za zgodą.</span><span class="sxs-lookup"><span data-stu-id="d773e-118">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="d773e-119">Wszystkie inne znaki i logo są własnością ich odpowiednich właścicieli.</span><span class="sxs-lookup"><span data-stu-id="d773e-119">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="d773e-120">Autorów:</span><span class="sxs-lookup"><span data-stu-id="d773e-120">Authors:</span></span>

> <span data-ttu-id="d773e-121">**Mark Rendle** - Dyrektor Techniczny - [Visual Recode](https://visualrecode.com)</span><span class="sxs-lookup"><span data-stu-id="d773e-121">**Mark Rendle** - Chief Technical Officer - [Visual Recode](https://visualrecode.com)</span></span>
>
> <span data-ttu-id="d773e-122">**Miranda Steiner** - autor techniczny</span><span class="sxs-lookup"><span data-stu-id="d773e-122">**Miranda Steiner** - Technical Author</span></span>

<span data-ttu-id="d773e-123">Edytor:</span><span class="sxs-lookup"><span data-stu-id="d773e-123">Editor:</span></span>

> <span data-ttu-id="d773e-124">**Maira Wenzel** - Sr. Content Developer - Microsoft</span><span class="sxs-lookup"><span data-stu-id="d773e-124">**Maira Wenzel** - Sr. Content Developer - Microsoft</span></span>

## <a name="introduction"></a><span data-ttu-id="d773e-125">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="d773e-125">Introduction</span></span>

<span data-ttu-id="d773e-126">gRPC to nowoczesne ramy dla tworzenia usług sieciowych i aplikacji rozproszonych.</span><span class="sxs-lookup"><span data-stu-id="d773e-126">gRPC is a modern framework for building networked services and distributed applications.</span></span> <span data-ttu-id="d773e-127">Wyobraź sobie wydajność powiązań NetTCP programu Windows Communication Foundation (WCF) w połączeniu z interoperacyjnością protokołu SOAP na wielu platformach.</span><span class="sxs-lookup"><span data-stu-id="d773e-127">Imagine the performance of Windows Communication Foundation (WCF) NetTCP bindings, combined with the cross-platform interoperability of SOAP.</span></span> <span data-ttu-id="d773e-128">GRPC opiera się na HTTP/2 i protobuf message-encoding protocol, aby zapewnić wysoką wydajność, niską przepustowość komunikacji między aplikacjami i usługami.</span><span class="sxs-lookup"><span data-stu-id="d773e-128">gRPC builds on HTTP/2 and the Protobuf message-encoding protocol to provide high performance, low-bandwidth communication between applications and services.</span></span> <span data-ttu-id="d773e-129">Obsługuje generowanie kodu serwera i klienta w najpopularniejszych językach programowania i platformach, w tym .NET, Java, Python, Node.js, Go i C++.</span><span class="sxs-lookup"><span data-stu-id="d773e-129">It supports server and client code generation across most popular programming languages and platforms, including .NET, Java, Python, Node.js, Go, and C++.</span></span> <span data-ttu-id="d773e-130">Dzięki najwyższej klasy obsłudze gRPC w ASP.NET Core 3.0, obok istniejących narzędzi i bibliotek gRPC dla platformy .NET 4.x, jest to doskonała alternatywa dla WCF dla zespołów programistycznych, które chcą przyjąć .NET Core w swoich organizacjach.</span><span class="sxs-lookup"><span data-stu-id="d773e-130">With the first-class support for gRPC in ASP.NET Core 3.0, alongside the existing gRPC tools and libraries for .NET 4.x, it's an excellent alternative to WCF for development teams looking to adopt .NET Core in their organizations.</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="d773e-131">Kto powinien korzystać z tego przewodnika</span><span class="sxs-lookup"><span data-stu-id="d773e-131">Who should use this guide</span></span>

<span data-ttu-id="d773e-132">Ten przewodnik został napisany dla deweloperów pracujących w programie .NET Framework lub .NET Core, którzy wcześniej używali WCF i którzy chcą przeprowadzić migrację swoich aplikacji do nowoczesnego środowiska RPC dla platformy .NET Core 3.0 i nowszych wersji.</span><span class="sxs-lookup"><span data-stu-id="d773e-132">This guide was written for developers working in .NET Framework or .NET Core who have previously used WCF, and who are seeking to migrate their applications to a modern RPC environment for .NET Core 3.0 and later versions.</span></span> <span data-ttu-id="d773e-133">Ogólniej rzecz biorąc, jeśli uaktualniasz lub rozważasz uaktualnienie do platformy .NET Core 3.0 i chcesz użyć wbudowanych narzędzi gRPC, ten przewodnik jest również przydatny.</span><span class="sxs-lookup"><span data-stu-id="d773e-133">More generally, if you are upgrading, or considering upgrading, to .NET Core 3.0, and you want to use the built-in gRPC tools, this guide is also useful.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="d773e-134">Jak można korzystać z tego przewodnika</span><span class="sxs-lookup"><span data-stu-id="d773e-134">How you can use this guide</span></span>

<span data-ttu-id="d773e-135">Jest to krótkie wprowadzenie do tworzenia usług gRPC w ASP.NET Core 3.0, ze szczególnym uwzględnieniem WCF jako analogicznej platformy.</span><span class="sxs-lookup"><span data-stu-id="d773e-135">This is a short introduction to building gRPC Services in ASP.NET Core 3.0, with particular reference to WCF as an analogous platform.</span></span> <span data-ttu-id="d773e-136">Wyjaśniono w nim zasady gRPC, odnoszące się do każdej koncepcji z równoważnymi cechami WCF, i oferuje wskazówki dotyczące migracji istniejącej aplikacji WCF do gRPC.</span><span class="sxs-lookup"><span data-stu-id="d773e-136">It explains the principles of gRPC, relating each concept to the equivalent features of WCF, and offers guidance for migrating an existing WCF application to gRPC.</span></span> <span data-ttu-id="d773e-137">Jest to również przydatne dla programistów, którzy mają doświadczenie z WCF i chcą nauczyć się gRPC do tworzenia nowych usług.</span><span class="sxs-lookup"><span data-stu-id="d773e-137">It's also useful for developers who have experience with WCF and are looking to learn gRPC to build new services.</span></span> <span data-ttu-id="d773e-138">Przykładowe aplikacje można używać jako szablonu lub odwołania dla własnych projektów i można kopiować i ponownie używać kodu z książki lub jej przykładów.</span><span class="sxs-lookup"><span data-stu-id="d773e-138">You can use the sample applications as a template or reference for your own projects, and you are free to copy and reuse code from the book or its samples.</span></span>

<span data-ttu-id="d773e-139">Możesz przesłać ten przewodnik do swojego zespołu, aby zapewnić wspólne zrozumienie tych zagadnień i możliwości.</span><span class="sxs-lookup"><span data-stu-id="d773e-139">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="d773e-140">Posiadanie wszystkich pracujących ze wspólnego zestawu terminów i podstawowych zasad pomaga zapewnić spójne stosowanie wzorców i praktyk architektonicznych.</span><span class="sxs-lookup"><span data-stu-id="d773e-140">Having everybody working from a common set of terms and underlying principles helps ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="d773e-141">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="d773e-141">References</span></span>

- <span data-ttu-id="d773e-142">**Witryna internetowa firmy gRPC**
  <https://grpc.io></span><span class="sxs-lookup"><span data-stu-id="d773e-142">**gRPC website**
<https://grpc.io></span></span>
- <span data-ttu-id="d773e-143">**Wybór między programem .NET Core a platformą .NET Framework dla aplikacji serwerowych**
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server></span><span class="sxs-lookup"><span data-stu-id="d773e-143">**Choosing between .NET Core and .NET Framework for server apps**
<https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server></span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="d773e-144">Dalej</span><span class="sxs-lookup"><span data-stu-id="d773e-144">Next</span></span>](introduction.md)
