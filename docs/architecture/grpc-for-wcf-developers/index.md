---
title: ASP.NET Core gRPC for WCF Developers — gRPC dla deweloperów WCF
description: Wprowadzenie do tworzenia usług gRPC w ASP.NET Core 3,0 dla deweloperów WCF
ms.date: 09/02/2019
ms.openlocfilehash: 6e18ecfdb8fcbe20f71fd0a7c77076166451427a
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144360"
---
# <a name="aspnet-core-grpc-for-wcf-developers"></a><span data-ttu-id="35516-103">Usługa gRPC platformy ASP.NET Core dla deweloperów WCF</span><span class="sxs-lookup"><span data-stu-id="35516-103">ASP.NET Core gRPC for WCF Developers</span></span>

![obraz okładki](./media/cover.png)

<span data-ttu-id="35516-105">OPUBLIKOWANA PRZEZ</span><span class="sxs-lookup"><span data-stu-id="35516-105">PUBLISHED BY</span></span>

<span data-ttu-id="35516-106">Zespoły deweloperów firmy Microsoft, .NET i Visual Studio</span><span class="sxs-lookup"><span data-stu-id="35516-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="35516-107">Dział firmy Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="35516-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="35516-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="35516-108">One Microsoft Way</span></span>

<span data-ttu-id="35516-109">Redmond, Waszyngton 98052-6399</span><span class="sxs-lookup"><span data-stu-id="35516-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="35516-110">Prawa autorskie © 2019 przez firmę Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="35516-110">Copyright © 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="35516-111">Wszelkie prawa zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="35516-111">All rights reserved.</span></span> <span data-ttu-id="35516-112">Żadna część zawartości tej księgi nie może być odtwarzana ani przekazywana w żadnej formie ani za pomocą jakichkolwiek środków bez zgody na wydawcę.</span><span class="sxs-lookup"><span data-stu-id="35516-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="35516-113">Ta książka jest świadczona w postaci "AS-IS" i zawiera widoki i opinie autora.</span><span class="sxs-lookup"><span data-stu-id="35516-113">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="35516-114">Widoki, opinie i informacje wyrażone w tej książce, w tym adresy URL i inne odwołania do witryn internetowych, mogą ulec zmianie bez powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="35516-114">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="35516-115">Niektóre z przykładów przedstawiono wyłącznie do celów informacyjnych i są one fikcyjne.</span><span class="sxs-lookup"><span data-stu-id="35516-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="35516-116">Żadne rzeczywiste skojarzenia lub związki nie są zamierzone ani wnioskowane.</span><span class="sxs-lookup"><span data-stu-id="35516-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="35516-117">Firma Microsoft i znaki towarowe wymienione na <https://www.microsoft.com> stronie "znaki towarowe" są znakami towarowymi grupy firm Microsoft.</span><span class="sxs-lookup"><span data-stu-id="35516-117">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="35516-118">Logo Docker Whale jest zastrzeżonym znakiem towarowym platformy Docker, Inc. używanym przez uprawnienie.</span><span class="sxs-lookup"><span data-stu-id="35516-118">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="35516-119">Wszystkie inne znaczniki i logo są własnością odpowiednich właścicieli.</span><span class="sxs-lookup"><span data-stu-id="35516-119">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="35516-120">Autorów</span><span class="sxs-lookup"><span data-stu-id="35516-120">Authors:</span></span>

> <span data-ttu-id="35516-121">**Mark The Rendle** -dyrektor ds. technicznych — [Visual firmy Recode](https://visualrecode.com)</span><span class="sxs-lookup"><span data-stu-id="35516-121">**Mark Rendle** - Chief Technical Officer - [Visual Recode](https://visualrecode.com)</span></span>
>
> <span data-ttu-id="35516-122">**Miranda Steiner** — autor techniczny</span><span class="sxs-lookup"><span data-stu-id="35516-122">**Miranda Steiner** - Technical Author</span></span>

<span data-ttu-id="35516-123">Edytora</span><span class="sxs-lookup"><span data-stu-id="35516-123">Editor:</span></span>

> <span data-ttu-id="35516-124">**Maira Wenzel** — SR. Content Developer — Microsoft</span><span class="sxs-lookup"><span data-stu-id="35516-124">**Maira Wenzel** - Sr. Content Developer - Microsoft</span></span>

## <a name="introduction"></a><span data-ttu-id="35516-125">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="35516-125">Introduction</span></span>

<span data-ttu-id="35516-126">gRPC to nowoczesne środowisko do tworzenia usług sieciowych i aplikacji rozproszonych.</span><span class="sxs-lookup"><span data-stu-id="35516-126">gRPC is a modern framework for building networked services and distributed applications.</span></span> <span data-ttu-id="35516-127">Wyobraź sobie Windows Communication Foundation wydajność powiązań NetTCP (WCF) w połączeniu z międzyplatformowym współdziałaniem protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="35516-127">Imagine the performance of Windows Communication Foundation (WCF) NetTCP bindings, combined with the cross-platform interoperability of SOAP.</span></span> <span data-ttu-id="35516-128">gRPC kompiluje na HTTP/2 i protokół kodowania komunikatów protobuf, aby zapewnić wysoką wydajność, komunikację o niskiej przepustowości między aplikacjami i usługami.</span><span class="sxs-lookup"><span data-stu-id="35516-128">gRPC builds on HTTP/2 and the Protobuf message-encoding protocol to provide high performance, low-bandwidth communication between applications and services.</span></span> <span data-ttu-id="35516-129">Obsługuje ona generowanie kodu serwera i klienta w większości popularnych języków programowania i platform, w tym .NET, Java, Python, Node. js, go i C++.</span><span class="sxs-lookup"><span data-stu-id="35516-129">It supports server and client code generation across most popular programming languages and platforms, including .NET, Java, Python, Node.js, Go, and C++.</span></span> <span data-ttu-id="35516-130">Dzięki pierwszej klasie wsparcia dla gRPC w ASP.NET Core 3,0 wraz z istniejącymi narzędziami i bibliotekami gRPC dla platformy .NET 4. x jest to świetna alternatywa dla usług WCF dla zespołów programistycznych, które chcą przyjąć platformę .NET Core w swoich organizacjach.</span><span class="sxs-lookup"><span data-stu-id="35516-130">With the first-class support for gRPC in ASP.NET Core 3.0, alongside the existing gRPC tools and libraries for .NET 4.x, it's an excellent alternative to WCF for development teams looking to adopt .NET Core in their organizations.</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="35516-131">Kto powinien korzystać z tego przewodnika</span><span class="sxs-lookup"><span data-stu-id="35516-131">Who should use this guide</span></span>

<span data-ttu-id="35516-132">Ten przewodnik został utworzony dla deweloperów pracujących w .NET Framework lub .NET Core, którzy wcześniej korzystali z usług WCF, i którzy chcą migrować swoje aplikacje do nowoczesnego środowiska RPC dla programu .NET Core 3,0 i jego nowszych wersji.</span><span class="sxs-lookup"><span data-stu-id="35516-132">This guide was written for developers working in .NET Framework or .NET Core who have previously used WCF, and who are seeking to migrate their applications to a modern RPC environment for .NET Core 3.0 and later versions.</span></span> <span data-ttu-id="35516-133">Ogólnie rzecz biorąc, Jeśli uaktualniasz lub rozważasz uaktualnienie do programu .NET Core 3,0 i chcesz korzystać z wbudowanych narzędzi gRPC, ten przewodnik jest również przydatny.</span><span class="sxs-lookup"><span data-stu-id="35516-133">More generally, if you are upgrading, or considering upgrading, to .NET Core 3.0, and you want to use the built-in gRPC tools, this guide is also useful.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="35516-134">Jak można użyć tego przewodnika</span><span class="sxs-lookup"><span data-stu-id="35516-134">How you can use this guide</span></span>

<span data-ttu-id="35516-135">Jest to krótkie wprowadzenie do tworzenia usług gRPC w ASP.NET Core 3,0, z uwzględnieniem programu WCF jako analogicznej platformy.</span><span class="sxs-lookup"><span data-stu-id="35516-135">This is a short introduction to building gRPC Services in ASP.NET Core 3.0, with particular reference to WCF as an analogous platform.</span></span> <span data-ttu-id="35516-136">Wyjaśniono zasady gRPC, odnoszące się do poszczególnych koncepcji funkcji WCF i oferuje wskazówki dotyczące migrowania istniejącej aplikacji WCF do gRPC.</span><span class="sxs-lookup"><span data-stu-id="35516-136">It explains the principles of gRPC, relating each concept to the equivalent features of WCF, and offers guidance for migrating an existing WCF application to gRPC.</span></span> <span data-ttu-id="35516-137">Jest on również przydatny dla deweloperów, którzy korzystają z WCF i chcą uczyć się gRPC w tworzeniu nowych usług.</span><span class="sxs-lookup"><span data-stu-id="35516-137">It's also useful for developers who have experience with WCF and are looking to learn gRPC to build new services.</span></span> <span data-ttu-id="35516-138">Przykładowymi aplikacjami można używać jako szablonu lub odwołania do własnych projektów i możesz kopiować i ponownie używać kodu z książki lub jej przykładów.</span><span class="sxs-lookup"><span data-stu-id="35516-138">You can use the sample applications as a template or reference for your own projects, and you are free to copy and reuse code from the book or its samples.</span></span>

<span data-ttu-id="35516-139">Możesz przesłać dalej ten przewodnik do zespołu, aby pomóc w zapewnieniu powszechnej wiedzy na temat tych zagadnień i możliwości.</span><span class="sxs-lookup"><span data-stu-id="35516-139">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="35516-140">Korzystanie ze wspólnego zestawu warunków i podstawowych zasad ułatwia zapewnienie spójnego stosowania wzorców i praktyk architektury.</span><span class="sxs-lookup"><span data-stu-id="35516-140">Having everybody working from a common set of terms and underlying principles helps ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="35516-141">Odwołania</span><span class="sxs-lookup"><span data-stu-id="35516-141">References</span></span>

- <span data-ttu-id="35516-142">**Witryna sieci Web gRPC**
  <https://grpc.io></span><span class="sxs-lookup"><span data-stu-id="35516-142">**gRPC website**
<https://grpc.io></span></span>
- <span data-ttu-id="35516-143">**Wybieranie między programami .NET Core i .NET Framework dla aplikacji serwerowych**
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server></span><span class="sxs-lookup"><span data-stu-id="35516-143">**Choosing between .NET Core and .NET Framework for server apps**
<https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server></span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="35516-144">Dalej</span><span class="sxs-lookup"><span data-stu-id="35516-144">Next</span></span>](introduction.md)
