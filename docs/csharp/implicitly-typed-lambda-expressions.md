---
title: Wyrażenia lambda wpisane niejawnie
description: Dowiedz się, dlaczego nie można użyć deklaracji zmiennej niejawnie wpisane do deklarowania wyrażenia lambda.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: a3851da9-e018-4389-9922-233db7d0f841
ms.openlocfilehash: ef437ef961210290db4150a8a5cfb70e01aee958
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79145725"
---
# <a name="implicitly-typed-lambda-expressions"></a><span data-ttu-id="92eb6-103">Wyrażenia lambda wpisane niejawnie</span><span class="sxs-lookup"><span data-stu-id="92eb6-103">Implicitly typed lambda expressions</span></span>

<span data-ttu-id="92eb6-104">Nie można użyć niejawnie wpisane deklaracji zmiennej do deklarowania wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="92eb6-104">You can't use an implicitly typed variable declaration to declare a lambda expression.</span></span>
<span data-ttu-id="92eb6-105">Tworzy problem logiki cyklicznej dla kompilatora.</span><span class="sxs-lookup"><span data-stu-id="92eb6-105">It creates a circular logic problem for the compiler.</span></span> <span data-ttu-id="92eb6-106">Deklaracja `var` informuje kompilator, aby dowiedzieć się typ zmiennej z typu wyrażenia po prawej stronie operatora przypisania.</span><span class="sxs-lookup"><span data-stu-id="92eb6-106">The `var` declaration tells the compiler to figure out the type of the variable from the type of expression on the right hand side of the assignment operator.</span></span> <span data-ttu-id="92eb6-107">Wyrażenie lambda nie ma typu czasu kompilacji, ale jest konwertowalne do dowolnego pasującego delegata lub typu wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="92eb6-107">A lambda expression does not have a compile time type, but is convertible to any matching delegate or expression type.</span></span> <span data-ttu-id="92eb6-108">Po przypisaniu wyrażenia lambda do zmiennej typu delegata lub wyrażenia, należy powiedzieć kompilatorowi, aby spróbować przekonwertować wyrażenie lambda do wyrażenia lub delegata, który pasuje do podpisu zmiennej "przypisane do".</span><span class="sxs-lookup"><span data-stu-id="92eb6-108">When you assign a lambda expression to a variable of a delegate or expression type, you tell the compiler to try and convert the lambda expression into an expression or delegate that matches the signature of the 'assigned to' variable.</span></span> <span data-ttu-id="92eb6-109">Kompilator musi starać się, aby rzecz po prawej stronie przypisania była zgodna z typem po lewej stronie przypisania.</span><span class="sxs-lookup"><span data-stu-id="92eb6-109">The compiler must try to make the thing on the right hand side of the assignment match the type on the left hand side of the assignment.</span></span>

<span data-ttu-id="92eb6-110">Obie strony przypisania nie można poinformować kompilatora, aby spojrzeć na obiekt po drugiej stronie operatora przypisania i sprawdzić, czy mój typ pasuje.</span><span class="sxs-lookup"><span data-stu-id="92eb6-110">Both sides of the assignment can't be telling the compiler to look at the object on the other side of the assignment operator and see if my type matches.</span></span>

<span data-ttu-id="92eb6-111">Możesz uzyskać jeszcze więcej szczegółów na temat tego, dlaczego język Języka C# określa to zachowanie, czytając [ten artykuł](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (plik PDF do pobrania).</span><span class="sxs-lookup"><span data-stu-id="92eb6-111">You can get even more details on why the C# language specifies that behavior by reading [this article](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (PDF download).</span></span>
