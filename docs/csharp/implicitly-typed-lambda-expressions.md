---
title: Niejawnie wpisane lambda — wyrażenia
description: Dowiedz się, dlaczego nie można zadeklarować wyrażenia lambda za pomocą deklaracji zmiennej typie określonym niejawnie.
ms.date: 06/20/2016
ms.assetid: a3851da9-e018-4389-9922-233db7d0f841
ms.openlocfilehash: f06c55f51c30c941d6d507ac8e2edd95c5152742
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33211826"
---
# <a name="implicitly-typed-lambda-expressions"></a><span data-ttu-id="d4bfe-103">Niejawnie wpisane lambda — wyrażenia</span><span class="sxs-lookup"><span data-stu-id="d4bfe-103">Implicitly typed lambda expressions</span></span>

<span data-ttu-id="d4bfe-104">Nie używam `var` można zadeklarować tego drzewa wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="d4bfe-104">I'm not using `var` to declare this expression tree.</span></span> <span data-ttu-id="d4bfe-105">Niejawnie wpisane deklaracja zmiennej nie można użyć do zadeklarowania wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="d4bfe-105">You can't use an implicitly typed variable declaration to declare a lambda expression.</span></span>
<span data-ttu-id="d4bfe-106">Tworzy problem cykliczne logiki dla kompilatora.</span><span class="sxs-lookup"><span data-stu-id="d4bfe-106">It creates a circular logic problem for the compiler.</span></span> <span data-ttu-id="d4bfe-107">`var` Deklaracji informuje kompilator, aby ustalić typ zmiennej z typu wyrażenie po prawej stronie operatora przypisania.</span><span class="sxs-lookup"><span data-stu-id="d4bfe-107">The `var` declaration tells the compiler to figure out the type of the variable from the type of expression on the right hand side of the assignment operator.</span></span> <span data-ttu-id="d4bfe-108">Wyrażenia lambda nie ma typu czasu kompilacji, ale jest możliwe do przekonwertowania na żadnych zgodnych delegata lub typ wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="d4bfe-108">A lambda expression does not have a compile time type, but is convertible to any matching delegate or expression type.</span></span> <span data-ttu-id="d4bfe-109">Po przypisaniu wyrażenia lambda do zmiennej typu delegat lub wyrażenie nakazuje kompilatorowi i spróbuj przekonwertować wyrażenia lambda do delegata, który pasuje do podpisu "przypisane do" zmiennej lub wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="d4bfe-109">When you assign a lambda expression to a variable of a delegate or expression type, you tell the compiler to try and convert the lambda expression into an expression or delegate that matches the signature of the 'assigned to' variable.</span></span> <span data-ttu-id="d4bfe-110">Kompilator musi spróbuj wprowadzić ten efekt na po prawej stronie przypisania zgodny typ po lewej stronie przypisania.</span><span class="sxs-lookup"><span data-stu-id="d4bfe-110">The compiler must try to make the thing on the right hand side of the assignment match the type on the left hand side of the assignment.</span></span> 

<span data-ttu-id="d4bfe-111">Obie strony przypisania nie informuje kompilator, aby przyjrzeć się obiektu po drugiej stronie operatora przypisania i czy Moje typu zgodne.</span><span class="sxs-lookup"><span data-stu-id="d4bfe-111">Both sides of the assignment can't be telling the compiler to look at the object on the other side of the assignment operator and see if my type matches.</span></span>

<span data-ttu-id="d4bfe-112">Więcej informacji na Dlaczego języka C# określa tego zachowania, odczytując można uzyskać [w tym artykule](http://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (Pobierz plik PDF)</span><span class="sxs-lookup"><span data-stu-id="d4bfe-112">You can get even more details on why the C# language specifies that behavior by reading [this article](http://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (PDF Download)</span></span>


