---
title: "Niejawnie wpisane lambda — wyrażenia"
description: "Dowiedz się, dlaczego nie można zadeklarować wyrażenia lambda za pomocą deklaracji zmiennej typie określonym niejawnie."
keywords: .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: a3851da9-e018-4389-9922-233db7d0f841
ms.openlocfilehash: 663613af001f9727c48bd48553540305e47a6bab
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="implicitly-typed-lambda-expressions"></a><span data-ttu-id="40e20-104">Niejawnie wpisane lambda — wyrażenia</span><span class="sxs-lookup"><span data-stu-id="40e20-104">Implicitly typed lambda expressions</span></span>

<span data-ttu-id="40e20-105">Nie używam `var` można zadeklarować tego drzewa wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="40e20-105">I'm not using `var` to declare this expression tree.</span></span> <span data-ttu-id="40e20-106">Niejawnie wpisane deklaracja zmiennej nie można użyć do zadeklarowania wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="40e20-106">You can't use an implicitly typed variable declaration to declare a lambda expression.</span></span>
<span data-ttu-id="40e20-107">Tworzy problem cykliczne logiki dla kompilatora.</span><span class="sxs-lookup"><span data-stu-id="40e20-107">It creates a circular logic problem for the compiler.</span></span> <span data-ttu-id="40e20-108">`var` Deklaracji informuje kompilator, aby ustalić typ zmiennej z typu wyrażenie po prawej stronie operatora przypisania.</span><span class="sxs-lookup"><span data-stu-id="40e20-108">The `var` declaration tells the compiler to figure out the type of the variable from the type of expression on the right hand side of the assignment operator.</span></span> <span data-ttu-id="40e20-109">Wyrażenia lambda nie ma typu czasu kompilacji, ale jest możliwe do przekonwertowania na żadnych zgodnych delegata lub typ wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="40e20-109">A lambda expression does not have a compile time type, but is convertible to any matching delegate or expression type.</span></span> <span data-ttu-id="40e20-110">Po przypisaniu wyrażenia lambda do zmiennej typu delegat lub wyrażenie nakazuje kompilatorowi i spróbuj przekonwertować wyrażenia lambda do delegata, który pasuje do podpisu "przypisane do" zmiennej lub wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="40e20-110">When you assign a lambda expression to a variable of a delegate or expression type, you tell the compiler to try and convert the lambda expression into an expression or delegate that matches the signature of the 'assigned to' variable.</span></span> <span data-ttu-id="40e20-111">Kompilator musi spróbuj wprowadzić ten efekt na po prawej stronie przypisania zgodny typ po lewej stronie przypisania.</span><span class="sxs-lookup"><span data-stu-id="40e20-111">The compiler must try to make the thing on the right hand side of the assignment match the type on the left hand side of the assignment.</span></span> 

<span data-ttu-id="40e20-112">Obie strony przypisania nie informuje kompilator, aby przyjrzeć się obiektu po drugiej stronie operatora przypisania i czy Moje typu zgodne.</span><span class="sxs-lookup"><span data-stu-id="40e20-112">Both sides of the assignment can't be telling the compiler to look at the object on the other side of the assignment operator and see if my type matches.</span></span>

<span data-ttu-id="40e20-113">Więcej informacji na Dlaczego języka C# określa tego zachowania, odczytując można uzyskać [w tym artykule](http://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (Pobierz plik PDF)</span><span class="sxs-lookup"><span data-stu-id="40e20-113">You can get even more details on why the C# language specifies that behavior by reading [this article](http://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (PDF Download)</span></span>


