---
title: Niejawnie wpisane wyrażenia lambda
description: Dowiedz się, dlaczego nie można użyć deklaracji zmiennej o typie określonym niejawnie do zadeklarowania wyrażenia lambda.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: a3851da9-e018-4389-9922-233db7d0f841
ms.openlocfilehash: cf16bb4d9ed27f536ae163284f36a0f305877139
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713886"
---
# <a name="implicitly-typed-lambda-expressions"></a><span data-ttu-id="22e25-103">Niejawnie wpisane wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="22e25-103">Implicitly typed lambda expressions</span></span>

<span data-ttu-id="22e25-104">Nie można użyć deklaracji zmiennej typu niejawnie wpisanej do deklarowania wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="22e25-104">You can't use an implicitly typed variable declaration to declare a lambda expression.</span></span>
<span data-ttu-id="22e25-105">Tworzy cykliczny problem logiki kompilatora.</span><span class="sxs-lookup"><span data-stu-id="22e25-105">It creates a circular logic problem for the compiler.</span></span> <span data-ttu-id="22e25-106">Deklaracja `var` informuje kompilator, aby ustalić typ zmiennej z typu wyrażenia po prawej stronie operatora przypisania.</span><span class="sxs-lookup"><span data-stu-id="22e25-106">The `var` declaration tells the compiler to figure out the type of the variable from the type of expression on the right hand side of the assignment operator.</span></span> <span data-ttu-id="22e25-107">Wyrażenie lambda nie ma typu czasu kompilacji, ale jest konwertowane na dowolny pasujący delegat lub typ wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="22e25-107">A lambda expression does not have a compile time type, but is convertible to any matching delegate or expression type.</span></span> <span data-ttu-id="22e25-108">Po przypisaniu wyrażenia lambda do zmiennej obiektu delegowanego lub typu wyrażenia poinformujesz kompilator, aby wypróbować i skonwertować wyrażenie lambda do wyrażenia lub delegata, który pasuje do sygnatury zmiennej "Assigned to".</span><span class="sxs-lookup"><span data-stu-id="22e25-108">When you assign a lambda expression to a variable of a delegate or expression type, you tell the compiler to try and convert the lambda expression into an expression or delegate that matches the signature of the 'assigned to' variable.</span></span> <span data-ttu-id="22e25-109">Kompilator musi próbować wykonać tę czynność po prawej stronie przypisania dopasowuje się do typu po lewej stronie przypisania.</span><span class="sxs-lookup"><span data-stu-id="22e25-109">The compiler must try to make the thing on the right hand side of the assignment match the type on the left hand side of the assignment.</span></span> 

<span data-ttu-id="22e25-110">Obie strony przypisania nie mogą być informować kompilatora, aby wyszukać obiekt po drugiej stronie operatora przypisania i zobaczyć, czy mój typ jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="22e25-110">Both sides of the assignment can't be telling the compiler to look at the object on the other side of the assignment operator and see if my type matches.</span></span>

<span data-ttu-id="22e25-111">Możesz uzyskać jeszcze więcej szczegółowych informacji na temat tego C# , dlaczego język określa takie zachowanie, czytając [ten artykuł](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (pobieranie plików PDF).</span><span class="sxs-lookup"><span data-stu-id="22e25-111">You can get even more details on why the C# language specifies that behavior by reading [this article](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (PDF download).</span></span>
