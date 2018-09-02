---
title: Wyrażenia lambda niejawnie wpisane
description: Dowiedz się, dlaczego nie można używać deklaracji zmiennej niejawnie wpisany do deklarowania wyrażenia lambda.
ms.date: 06/20/2016
ms.assetid: a3851da9-e018-4389-9922-233db7d0f841
ms.openlocfilehash: 0a6b52ba49ea39c0cb37e72b0ad40e18986c9be0
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43401503"
---
# <a name="implicitly-typed-lambda-expressions"></a><span data-ttu-id="6611c-103">Wyrażenia lambda niejawnie wpisane</span><span class="sxs-lookup"><span data-stu-id="6611c-103">Implicitly typed lambda expressions</span></span>

<span data-ttu-id="6611c-104">Nie używam `var` do deklarowania tego drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="6611c-104">I'm not using `var` to declare this expression tree.</span></span> <span data-ttu-id="6611c-105">Niejawnie wpisane deklaracji zmiennych nie można użyć do deklarowania wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="6611c-105">You can't use an implicitly typed variable declaration to declare a lambda expression.</span></span>
<span data-ttu-id="6611c-106">Tworzy problem cykliczne logiki dla kompilatora.</span><span class="sxs-lookup"><span data-stu-id="6611c-106">It creates a circular logic problem for the compiler.</span></span> <span data-ttu-id="6611c-107">`var` Deklaracji informuje kompilator, aby ustalić typ zmiennej z typu wyrażeniem po prawej stronie operatora przypisania.</span><span class="sxs-lookup"><span data-stu-id="6611c-107">The `var` declaration tells the compiler to figure out the type of the variable from the type of expression on the right hand side of the assignment operator.</span></span> <span data-ttu-id="6611c-108">Wyrażenie lambda nie ma typów w czasie kompilacji, ale jest konwertowany na wszystkie dopasowania delegata lub typ wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="6611c-108">A lambda expression does not have a compile time type, but is convertible to any matching delegate or expression type.</span></span> <span data-ttu-id="6611c-109">Po przypisaniu do wyrażenia lambda do zmiennej na delegata lub typ wyrażenia nakazuje kompilatorowi i spróbuj przekonwertować wyrażenia lambda na wyrażenie lub delegata, która pasuje do oznaczenia "przypisane do" zmiennej.</span><span class="sxs-lookup"><span data-stu-id="6611c-109">When you assign a lambda expression to a variable of a delegate or expression type, you tell the compiler to try and convert the lambda expression into an expression or delegate that matches the signature of the 'assigned to' variable.</span></span> <span data-ttu-id="6611c-110">Kompilator będą musieli spróbować dokonuje się po prawej stronie przypisania dopasowanie typu po lewej stronie przypisania w kolejności.</span><span class="sxs-lookup"><span data-stu-id="6611c-110">The compiler must try to make the thing on the right hand side of the assignment match the type on the left hand side of the assignment.</span></span> 

<span data-ttu-id="6611c-111">Obie strony przypisania nie informuje kompilator, aby obejrzeć obiektu po drugiej stronie operatora przypisania i sprawdzić, czy mój typ odpowiada.</span><span class="sxs-lookup"><span data-stu-id="6611c-111">Both sides of the assignment can't be telling the compiler to look at the object on the other side of the assignment operator and see if my type matches.</span></span>

<span data-ttu-id="6611c-112">Można uzyskać nawet więcej informacji na temat Dlaczego języka C# określa to zachowanie, czytając [w tym artykule](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (Pobierz plik PDF)</span><span class="sxs-lookup"><span data-stu-id="6611c-112">You can get even more details on why the C# language specifies that behavior by reading [this article](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (PDF Download)</span></span>


