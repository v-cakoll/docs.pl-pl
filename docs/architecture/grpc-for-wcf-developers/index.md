---
title: ASP.NET Core gRPC dla programistów WCF - gRPC dla programistów WCF
description: Wprowadzenie do budowania usług gRPC w ASP.NET Core 3.0 dla deweloperów WCF
ms.date: 09/02/2019
ms.openlocfilehash: 40307124c521659a00339884bacf48881fa3e048
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "77543238"
---
# <a name="aspnet-core-grpc-for-wcf-developers"></a><span data-ttu-id="8eaa4-103">Usługa gRPC platformy ASP.NET Core dla deweloperów WCF</span><span class="sxs-lookup"><span data-stu-id="8eaa4-103">ASP.NET Core gRPC for WCF Developers</span></span>

![obraz okładki](./media/cover.png)

<span data-ttu-id="8eaa4-105">OPUBLIKOWANA PRZEZ</span><span class="sxs-lookup"><span data-stu-id="8eaa4-105">PUBLISHED BY</span></span>

<span data-ttu-id="8eaa4-106">Zespoły produktów Microsoft Developer Division, .NET i Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8eaa4-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="8eaa4-107">Oddział Firmy Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="8eaa4-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="8eaa4-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="8eaa4-108">One Microsoft Way</span></span>

<span data-ttu-id="8eaa4-109">Redmond (Waszyngton) 98052-6399</span><span class="sxs-lookup"><span data-stu-id="8eaa4-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="8eaa4-110">Prawa autorskie © 2019 przez Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="8eaa4-110">Copyright © 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="8eaa4-111">Wszelkie prawa zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="8eaa4-111">All rights reserved.</span></span> <span data-ttu-id="8eaa4-112">Żadna część treści tej książki nie może być powielana lub przekazywana w jakiejkolwiek formie lub w jakikolwiek sposób bez pisemnej zgody wydawcy.</span><span class="sxs-lookup"><span data-stu-id="8eaa4-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="8eaa4-113">Ta książka jest "tak jak jest" i wyraża poglądy i opinie autora.</span><span class="sxs-lookup"><span data-stu-id="8eaa4-113">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="8eaa4-114">Poglądy, opinie i informacje wyrażone w tej książce, w tym adresy URL i inne odniesienia do stron internetowych, mogą ulec zmianie bez powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="8eaa4-114">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="8eaa4-115">Niektóre z przykładów przedstawiono wyłącznie do celów informacyjnych i są one fikcyjne.</span><span class="sxs-lookup"><span data-stu-id="8eaa4-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="8eaa4-116">Żadne rzeczywiste skojarzenia lub związki nie są zamierzone ani wnioskowane.</span><span class="sxs-lookup"><span data-stu-id="8eaa4-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="8eaa4-117">Microsoft i znaki towarowe https://www.microsoft.com wymienione na stronie internetowej "Znaki towarowe" są znakami towarowymi grupy firm Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8eaa4-117">Microsoft and the trademarks listed at https://www.microsoft.com on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="8eaa4-118">Logo wieloryba Docker jest zastrzeżonym znakiem towarowym firmy Docker, Inc. Używanym za zgodą.</span><span class="sxs-lookup"><span data-stu-id="8eaa4-118">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="8eaa4-119">Wszystkie inne znaki i logo są własnością ich właścicieli.</span><span class="sxs-lookup"><span data-stu-id="8eaa4-119">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="8eaa4-120">Autorów:</span><span class="sxs-lookup"><span data-stu-id="8eaa4-120">Authors:</span></span>

> <span data-ttu-id="8eaa4-121">**Mark Rendle** - Dyrektor Techniczny - [Visual Recode](https://visualrecode.com)</span><span class="sxs-lookup"><span data-stu-id="8eaa4-121">**Mark Rendle** - Chief Technical Officer - [Visual Recode](https://visualrecode.com)</span></span>
>
> <span data-ttu-id="8eaa4-122">**Miranda Steiner** - Autor techniczny</span><span class="sxs-lookup"><span data-stu-id="8eaa4-122">**Miranda Steiner** - Technical Author</span></span>

<span data-ttu-id="8eaa4-123">Edytor:</span><span class="sxs-lookup"><span data-stu-id="8eaa4-123">Editor:</span></span>

> <span data-ttu-id="8eaa4-124">**Maira Wenzel** - Sr. Content Developer - Microsoft</span><span class="sxs-lookup"><span data-stu-id="8eaa4-124">**Maira Wenzel** - Sr. Content Developer - Microsoft</span></span>

## <a name="introduction"></a><span data-ttu-id="8eaa4-125">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8eaa4-125">Introduction</span></span>

<span data-ttu-id="8eaa4-126">gRPC to nowoczesne ramy budowania usług sieciowych i aplikacji rozproszonych.</span><span class="sxs-lookup"><span data-stu-id="8eaa4-126">gRPC is a modern framework for building networked services and distributed applications.</span></span> <span data-ttu-id="8eaa4-127">Wyobraź sobie wydajność powiązań NetTCP usługi Windows Communication Foundation (WCF) w połączeniu z współdziałaniem protokołu SOAP między platformami.</span><span class="sxs-lookup"><span data-stu-id="8eaa4-127">Imagine the performance of Windows Communication Foundation (WCF) NetTCP bindings, combined with the cross-platform interoperability of SOAP.</span></span> <span data-ttu-id="8eaa4-128">gRPC opiera się na HTTP/2 i protobuf ie kodowania komunikatów, aby zapewnić wysoką wydajność, niską przepustowość komunikacji między aplikacjami i usługami.</span><span class="sxs-lookup"><span data-stu-id="8eaa4-128">gRPC builds on HTTP/2 and the Protobuf message-encoding protocol to provide high performance, low-bandwidth communication between applications and services.</span></span> <span data-ttu-id="8eaa4-129">Obsługuje generowanie kodu serwera i klienta w najpopularniejszych językach i platformach programowania, w tym .NET, Java, Python, Node.js, Go i C++.</span><span class="sxs-lookup"><span data-stu-id="8eaa4-129">It supports server and client code generation across most popular programming languages and platforms, including .NET, Java, Python, Node.js, Go, and C++.</span></span> <span data-ttu-id="8eaa4-130">Dzięki pierwszorzędnej obsłudze gRPC w ASP.NET Core 3.0, obok istniejących narzędzi i bibliotek gRPC dla .NET 4.x, jest to doskonała alternatywa dla WCF dla zespołów programistycznych, które chcą przyjąć .NET Core w swoich organizacjach.</span><span class="sxs-lookup"><span data-stu-id="8eaa4-130">With the first-class support for gRPC in ASP.NET Core 3.0, alongside the existing gRPC tools and libraries for .NET 4.x, it's an excellent alternative to WCF for development teams looking to adopt .NET Core in their organizations.</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="8eaa4-131">Kto powinien skorzystać z tego przewodnika</span><span class="sxs-lookup"><span data-stu-id="8eaa4-131">Who should use this guide</span></span>

<span data-ttu-id="8eaa4-132">Ten przewodnik został napisany dla deweloperów pracujących w .NET Framework lub .NET Core, którzy wcześniej używali WCF i którzy chcą przeprowadzić migrację swoich aplikacji do nowoczesnego środowiska RPC dla .NET Core 3.0 i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="8eaa4-132">This guide was written for developers working in .NET Framework or .NET Core who have previously used WCF, and who are seeking to migrate their applications to a modern RPC environment for .NET Core 3.0 and later versions.</span></span> <span data-ttu-id="8eaa4-133">Ogólnie rzecz biorąc, jeśli uaktualniasz lub rozważasz uaktualnienie do .NET Core 3.0 i chcesz użyć wbudowanych narzędzi gRPC, ten przewodnik jest również przydatny.</span><span class="sxs-lookup"><span data-stu-id="8eaa4-133">More generally, if you are upgrading, or considering upgrading, to .NET Core 3.0, and you want to use the built-in gRPC tools, this guide is also useful.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="8eaa4-134">Jak korzystać z tego przewodnika</span><span class="sxs-lookup"><span data-stu-id="8eaa4-134">How you can use this guide</span></span>

<span data-ttu-id="8eaa4-135">Jest to krótkie wprowadzenie do tworzenia usług gRPC w ASP.NET Core 3.0, ze szczególnym odniesieniem do WCF jako analogicznej platformy.</span><span class="sxs-lookup"><span data-stu-id="8eaa4-135">This is a short introduction to building gRPC Services in ASP.NET Core 3.0, with particular reference to WCF as an analogous platform.</span></span> <span data-ttu-id="8eaa4-136">Wyjaśnia zasady gRPC, odnoszące się do każdej koncepcji do równoważnych funkcji WCF i oferuje wskazówki dotyczące migracji istniejącej aplikacji WCF do gRPC.</span><span class="sxs-lookup"><span data-stu-id="8eaa4-136">It explains the principles of gRPC, relating each concept to the equivalent features of WCF, and offers guidance for migrating an existing WCF application to gRPC.</span></span> <span data-ttu-id="8eaa4-137">Jest to również przydatne dla programistów, którzy mają doświadczenie z WCF i chcą nauczyć gRPC do tworzenia nowych usług.</span><span class="sxs-lookup"><span data-stu-id="8eaa4-137">It's also useful for developers who have experience with WCF and are looking to learn gRPC to build new services.</span></span> <span data-ttu-id="8eaa4-138">Przykładowe aplikacje można użyć jako szablon lub odwołanie do własnych projektów i można swobodnie kopiować i ponownie używać kodu z książki lub jej przykładów.</span><span class="sxs-lookup"><span data-stu-id="8eaa4-138">You can use the sample applications as a template or reference for your own projects, and you are free to copy and reuse code from the book or its samples.</span></span>

<span data-ttu-id="8eaa4-139">Nie krępuj się przekazać ten przewodnik do swojego zespołu, aby zapewnić wspólne zrozumienie tych rozważań i możliwości.</span><span class="sxs-lookup"><span data-stu-id="8eaa4-139">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="8eaa4-140">Możliwość zapewnienia spójnego stosowania wzorców i praktyk architektonicznych przez wszystkich pracujących na podstawie wspólnego zestawu terminów i podstawowych zasad.</span><span class="sxs-lookup"><span data-stu-id="8eaa4-140">Having everybody working from a common set of terms and underlying principles helps ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="8eaa4-141">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="8eaa4-141">References</span></span>

- <span data-ttu-id="8eaa4-142">**Witryna internetowa strony internetowej gRPC**
  <https://grpc.io></span><span class="sxs-lookup"><span data-stu-id="8eaa4-142">**gRPC website**
<https://grpc.io></span></span>
- <span data-ttu-id="8eaa4-143">**Wybór między programami .NET Core a platformą .NET Framework dla aplikacji serwerowych**
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server></span><span class="sxs-lookup"><span data-stu-id="8eaa4-143">**Choosing between .NET Core and .NET Framework for server apps**
<https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server></span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="8eaa4-144">Dalej</span><span class="sxs-lookup"><span data-stu-id="8eaa4-144">Next</span></span>](introduction.md)
