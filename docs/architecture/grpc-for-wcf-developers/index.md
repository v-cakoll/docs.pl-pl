---
title: ASP.NET Core gRPC for WCF Developers — gRPC dla deweloperów WCF
description: DO ZAPISANIA
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 6a5b4f6d0b47a272f7a753e22bfd61b06202944a
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2019
ms.locfileid: "72919377"
---
# <a name="aspnet-core-grpc-for-wcf-developers"></a><span data-ttu-id="5302d-103">Usługa gRPC platformy ASP.NET Core dla deweloperów WCF</span><span class="sxs-lookup"><span data-stu-id="5302d-103">ASP.NET Core gRPC for WCF Developers</span></span>

![obraz okładki](./media/cover.png)

<span data-ttu-id="5302d-105">OPUBLIKOWANO PRZEZ</span><span class="sxs-lookup"><span data-stu-id="5302d-105">PUBLISHED BY</span></span>

<span data-ttu-id="5302d-106">Zespoły deweloperów firmy Microsoft, .NET i Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5302d-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="5302d-107">Dział firmy Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="5302d-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="5302d-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="5302d-108">One Microsoft Way</span></span>

<span data-ttu-id="5302d-109">Redmond, Waszyngton 98052-6399</span><span class="sxs-lookup"><span data-stu-id="5302d-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="5302d-110">Prawa autorskie © 2019 przez firmę Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="5302d-110">Copyright © 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="5302d-111">Wszelkie prawa zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="5302d-111">All rights reserved.</span></span> <span data-ttu-id="5302d-112">Żadna część zawartości tej księgi nie może być odtwarzana ani przekazywana w żadnej formie ani za pomocą jakichkolwiek środków bez zgody na wydawcę.</span><span class="sxs-lookup"><span data-stu-id="5302d-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="5302d-113">Ta książka jest świadczona w postaci "AS-IS" i zawiera widoki i opinie autora.</span><span class="sxs-lookup"><span data-stu-id="5302d-113">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="5302d-114">Widoki, opinie i informacje wyrażone w tej książce, w tym adresy URL i inne odwołania do witryn internetowych, mogą ulec zmianie bez powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="5302d-114">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="5302d-115">Niektóre przykłady opisane w niniejszym dokumencie są dostępne tylko dla ilustracji i są fikcyjne.</span><span class="sxs-lookup"><span data-stu-id="5302d-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="5302d-116">Żadne prawdziwe skojarzenie lub połączenie nie jest zamierzone ani nie powinno zostać wywnioskowane.</span><span class="sxs-lookup"><span data-stu-id="5302d-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="5302d-117">Firma Microsoft i znaki towarowe wymienione w https://www.microsoft.com na stronie "znaki towarowe" są znakami towarowymi grupy firm Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5302d-117">Microsoft and the trademarks listed at https://www.microsoft.com on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="5302d-118">Logo Docker Whale jest zastrzeżonym znakiem towarowym platformy Docker, Inc. używanym przez uprawnienie.</span><span class="sxs-lookup"><span data-stu-id="5302d-118">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="5302d-119">Wszystkie inne znaczniki i logo są własnością odpowiednich właścicieli.</span><span class="sxs-lookup"><span data-stu-id="5302d-119">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="5302d-120">Tworzone</span><span class="sxs-lookup"><span data-stu-id="5302d-120">Author:</span></span>

> <span data-ttu-id="5302d-121">**Mark The Rendle** -dyrektor ds. technicznych — [Visual firmy Recode](https://visualrecode.com)</span><span class="sxs-lookup"><span data-stu-id="5302d-121">**Mark Rendle** - Chief Technical Officer - [Visual Recode](https://visualrecode.com)</span></span>
>
> <span data-ttu-id="5302d-122">**Miranda Steiner** — autor techniczny</span><span class="sxs-lookup"><span data-stu-id="5302d-122">**Miranda Steiner** - Technical Author</span></span>

<span data-ttu-id="5302d-123">Edytory</span><span class="sxs-lookup"><span data-stu-id="5302d-123">Editors:</span></span>

> <span data-ttu-id="5302d-124">**Maira Wenzel** — deweloper zawartości SR — Microsoft</span><span class="sxs-lookup"><span data-stu-id="5302d-124">**Maira Wenzel** - Sr Content Developer - Microsoft</span></span>

## <a name="introduction"></a><span data-ttu-id="5302d-125">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="5302d-125">Introduction</span></span>

<span data-ttu-id="5302d-126">CZYNNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="5302d-126">TODO</span></span>

## <a name="purpose"></a><span data-ttu-id="5302d-127">Cel</span><span class="sxs-lookup"><span data-stu-id="5302d-127">Purpose</span></span>

<span data-ttu-id="5302d-128">CZYNNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="5302d-128">TODO</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="5302d-129">Kto powinien korzystać z tego przewodnika</span><span class="sxs-lookup"><span data-stu-id="5302d-129">Who should use this guide</span></span>

<span data-ttu-id="5302d-130">**ZAKTUALIZUJ TEN**</span><span class="sxs-lookup"><span data-stu-id="5302d-130">**UPDATE THIS**</span></span>

<span data-ttu-id="5302d-131">Odbiorcy tego przewodnika są deweloperzy WCF, potencjalni klienci programistyczni i architektzy zainteresowani migrowaniem rozwiązań WCF w .NET Framework 4 i wcześniejszych, aby ASP.NET Core 3,0 przy użyciu usług gRPC Services.</span><span class="sxs-lookup"><span data-stu-id="5302d-131">The audience for this guide is WCF developers, development leads, and architects who are interested in migrating WCF solutions on .NET Framework 4 and earlier to ASP.NET Core 3.0 using gRPC services.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="5302d-132">Jak można użyć tego przewodnika</span><span class="sxs-lookup"><span data-stu-id="5302d-132">How you can use this guide</span></span>

<span data-ttu-id="5302d-133">**ZAKTUALIZUJ TEN**</span><span class="sxs-lookup"><span data-stu-id="5302d-133">**UPDATE THIS**</span></span>

<span data-ttu-id="5302d-134">Jest to krótkie wprowadzenie do tworzenia usług gRPC w ASP.NET Core 3,0 z konkretnym odwołaniem do programu WCF jako analogicznej platformy.</span><span class="sxs-lookup"><span data-stu-id="5302d-134">This is a short introduction to building gRPC Services in ASP.NET Core 3.0 with particular reference to WCF as an analogous platform.</span></span> <span data-ttu-id="5302d-135">Wyjaśniono zasady gRPC, odnoszące się do poszczególnych koncepcji funkcji WCF i oferuje wskazówki dotyczące migrowania istniejącej aplikacji WCF do gRPC.</span><span class="sxs-lookup"><span data-stu-id="5302d-135">It explains the principles of gRPC, relating each concept to the equivalent features of WCF, and offers guidance for migrating an existing WCF application to gRPC.</span></span> <span data-ttu-id="5302d-136">Jest on również przydatny dla deweloperów, którzy korzystają z programu WCF i poszukują gRPC w tworzeniu nowych usług.</span><span class="sxs-lookup"><span data-stu-id="5302d-136">It is also useful for developers who have experience of WCF and are looking to learn gRPC to build new services.</span></span> <span data-ttu-id="5302d-137">Przykładowa aplikacja może być używana jako szablon lub odwołanie do własnych projektów i możesz bezpłatnie kopiować i ponownie używać kodu z książki lub jej przykładów.</span><span class="sxs-lookup"><span data-stu-id="5302d-137">The sample application can be used as a template or reference for your own projects, and you are free to copy and reuse code from the book or its samples.</span></span>

<span data-ttu-id="5302d-138">Możesz przesłać dalej ten przewodnik do zespołu, aby pomóc w zapewnieniu powszechnej wiedzy na temat tych zagadnień i możliwości.</span><span class="sxs-lookup"><span data-stu-id="5302d-138">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="5302d-139">Korzystanie ze wspólnego zestawu terminologii i podstawowych zasad pomaga zapewnić spójne stosowanie wzorców i praktyk architektury.</span><span class="sxs-lookup"><span data-stu-id="5302d-139">Having everybody working from a common set of terminology and underlying principles helps ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="5302d-140">Odwołania</span><span class="sxs-lookup"><span data-stu-id="5302d-140">References</span></span>

- <span data-ttu-id="5302d-141">**Witryna sieci Web gRPC**</span><span class="sxs-lookup"><span data-stu-id="5302d-141">**gRPC web site**</span></span>  
  <https://grpc.io>
- <span data-ttu-id="5302d-142">**Wybieranie między programami .NET Core i .NET Framework na potrzeby aplikacji serwerowych**</span><span class="sxs-lookup"><span data-stu-id="5302d-142">**Choosing between .NET Core and .NET Framework for server apps**</span></span>  
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server>

>[!div class="step-by-step"]
>[<span data-ttu-id="5302d-143">Next</span><span class="sxs-lookup"><span data-stu-id="5302d-143">Next</span></span>](introduction.md)
