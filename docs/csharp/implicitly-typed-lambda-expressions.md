---
title: Wyrażenia lambda niejawnie wpisane
description: Dowiedz się, dlaczego nie można używać deklaracji zmiennej niejawnie wpisany do deklarowania wyrażenia lambda.
ms.date: 06/20/2016
ms.assetid: a3851da9-e018-4389-9922-233db7d0f841
ms.openlocfilehash: 9b798f40676afaad2075806d6dc512f279bc7065
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61672084"
---
# <a name="implicitly-typed-lambda-expressions"></a><span data-ttu-id="02061-103">Wyrażenia lambda niejawnie wpisane</span><span class="sxs-lookup"><span data-stu-id="02061-103">Implicitly typed lambda expressions</span></span>

<span data-ttu-id="02061-104">Niejawnie wpisane deklaracji zmiennych nie można użyć do deklarowania wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="02061-104">You can't use an implicitly typed variable declaration to declare a lambda expression.</span></span>
<span data-ttu-id="02061-105">Tworzy problem cykliczne logiki dla kompilatora.</span><span class="sxs-lookup"><span data-stu-id="02061-105">It creates a circular logic problem for the compiler.</span></span> <span data-ttu-id="02061-106">`var` Deklaracji informuje kompilator, aby ustalić typ zmiennej z typu wyrażeniem po prawej stronie operatora przypisania.</span><span class="sxs-lookup"><span data-stu-id="02061-106">The `var` declaration tells the compiler to figure out the type of the variable from the type of expression on the right hand side of the assignment operator.</span></span> <span data-ttu-id="02061-107">Wyrażenie lambda nie ma typów w czasie kompilacji, ale jest konwertowany na wszystkie dopasowania delegata lub typ wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="02061-107">A lambda expression does not have a compile time type, but is convertible to any matching delegate or expression type.</span></span> <span data-ttu-id="02061-108">Po przypisaniu do wyrażenia lambda do zmiennej na delegata lub typ wyrażenia nakazuje kompilatorowi i spróbuj przekonwertować wyrażenia lambda na wyrażenie lub delegata, która pasuje do oznaczenia "przypisane do" zmiennej.</span><span class="sxs-lookup"><span data-stu-id="02061-108">When you assign a lambda expression to a variable of a delegate or expression type, you tell the compiler to try and convert the lambda expression into an expression or delegate that matches the signature of the 'assigned to' variable.</span></span> <span data-ttu-id="02061-109">Kompilator będą musieli spróbować dokonuje się po prawej stronie przypisania dopasowanie typu po lewej stronie przypisania w kolejności.</span><span class="sxs-lookup"><span data-stu-id="02061-109">The compiler must try to make the thing on the right hand side of the assignment match the type on the left hand side of the assignment.</span></span> 

<span data-ttu-id="02061-110">Obie strony przypisania nie informuje kompilator, aby obejrzeć obiektu po drugiej stronie operatora przypisania i sprawdzić, czy mój typ odpowiada.</span><span class="sxs-lookup"><span data-stu-id="02061-110">Both sides of the assignment can't be telling the compiler to look at the object on the other side of the assignment operator and see if my type matches.</span></span>

<span data-ttu-id="02061-111">Można uzyskać nawet więcej informacji na temat Dlaczego języka C# określa to zachowanie, czytając [w tym artykule](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (Pobierz plik PDF)</span><span class="sxs-lookup"><span data-stu-id="02061-111">You can get even more details on why the C# language specifies that behavior by reading [this article](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (PDF Download)</span></span>
