---
title: Operatory logiczne (F#)
description: 'Więcej informacji na temat operatorów logicznych, które są dostępne w języku programowania w języku F #.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 0b11b5133b02b6f507c7886b2fbaebf30abf46cb
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="boolean-operators"></a><span data-ttu-id="cfe33-103">Operatory logiczne</span><span class="sxs-lookup"><span data-stu-id="cfe33-103">Boolean Operators</span></span>

<span data-ttu-id="cfe33-104">W tym temacie opisano obsługę operatorów logicznych w języku F #.</span><span class="sxs-lookup"><span data-stu-id="cfe33-104">This topic describes the support for Boolean operators in the F# language.</span></span>


## <a name="summary-of-boolean-operators"></a><span data-ttu-id="cfe33-105">Podsumowanie operatory logiczne</span><span class="sxs-lookup"><span data-stu-id="cfe33-105">Summary of Boolean Operators</span></span>
<span data-ttu-id="cfe33-106">Poniższa tabela zawiera podsumowanie operatorów logicznych, które są dostępne w języku F #.</span><span class="sxs-lookup"><span data-stu-id="cfe33-106">The following table summarizes the Boolean operators that are available in the F# language.</span></span> <span data-ttu-id="cfe33-107">Jest to jedyny typ obsługiwany przez te podmioty `bool` typu.</span><span class="sxs-lookup"><span data-stu-id="cfe33-107">The only type supported by these operators is the `bool` type.</span></span>

|<span data-ttu-id="cfe33-108">Operator</span><span class="sxs-lookup"><span data-stu-id="cfe33-108">Operator</span></span>|<span data-ttu-id="cfe33-109">Opis</span><span class="sxs-lookup"><span data-stu-id="cfe33-109">Description</span></span>|
|--------|-----------|
|`not`|<span data-ttu-id="cfe33-110">Logiczna Negacja</span><span class="sxs-lookup"><span data-stu-id="cfe33-110">Boolean negation</span></span>|
|<code>&#124;&#124;</code>|<span data-ttu-id="cfe33-111">Wartość logiczna lub</span><span class="sxs-lookup"><span data-stu-id="cfe33-111">Boolean OR</span></span>|
|`&&`|<span data-ttu-id="cfe33-112">Wartość logiczna AND</span><span class="sxs-lookup"><span data-stu-id="cfe33-112">Boolean AND</span></span>|

<span data-ttu-id="cfe33-113">Wykonaj logicznych AND i OR operatory *ocena zwarcia*, to znaczy umożliwiają podawanie wartości wyrażenie po prawej stronie operatora tylko w przypadku, gdy jest to niezbędne do obliczenia ogólnej wyniku wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="cfe33-113">The Boolean AND and OR operators perform *short-circuit evaluation*, that is, they evaluate the expression on the right of the operator only when it is necessary to determine the overall result of the expression.</span></span> <span data-ttu-id="cfe33-114">Drugie wyrażenie `&&` operator jest oceniany, tylko, jeśli pierwsze wyrażenie daje w wyniku `true`; drugie wyrażenie `||` operator jest oceniany, tylko, jeśli pierwsze wyrażenie daje w wyniku `false`.</span><span class="sxs-lookup"><span data-stu-id="cfe33-114">The second expression of the `&&` operator is evaluated only if the first expression evaluates to `true`; the second expression of the `||` operator is evaluated only if the first expression evaluates to `false`.</span></span>

## <a name="see-also"></a><span data-ttu-id="cfe33-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cfe33-115">See Also</span></span>
[<span data-ttu-id="cfe33-116">Operatory bitowe</span><span class="sxs-lookup"><span data-stu-id="cfe33-116">Bitwise Operators</span></span>](bitwise-operators.md)

[<span data-ttu-id="cfe33-117">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="cfe33-117">Arithmetic Operators</span></span>](arithmetic-operators.md)

[<span data-ttu-id="cfe33-118">Odwołanie do symboli i operatorów</span><span class="sxs-lookup"><span data-stu-id="cfe33-118">Symbol and Operator Reference</span></span>](index.md)
