---
title: Operatory logiczne (F#)
description: 'Więcej informacji na temat operatorów logicznych, które są dostępne w języku programowania w języku F #.'
ms.date: 05/16/2016
ms.openlocfilehash: f8516ceb531907400f98dc4226d2985d3119e9e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563431"
---
# <a name="boolean-operators"></a><span data-ttu-id="f63ff-103">Operatory logiczne</span><span class="sxs-lookup"><span data-stu-id="f63ff-103">Boolean Operators</span></span>

<span data-ttu-id="f63ff-104">W tym temacie opisano obsługę operatorów logicznych w języku F #.</span><span class="sxs-lookup"><span data-stu-id="f63ff-104">This topic describes the support for Boolean operators in the F# language.</span></span>


## <a name="summary-of-boolean-operators"></a><span data-ttu-id="f63ff-105">Podsumowanie operatory logiczne</span><span class="sxs-lookup"><span data-stu-id="f63ff-105">Summary of Boolean Operators</span></span>
<span data-ttu-id="f63ff-106">Poniższa tabela zawiera podsumowanie operatorów logicznych, które są dostępne w języku F #.</span><span class="sxs-lookup"><span data-stu-id="f63ff-106">The following table summarizes the Boolean operators that are available in the F# language.</span></span> <span data-ttu-id="f63ff-107">Jest to jedyny typ obsługiwany przez te podmioty `bool` typu.</span><span class="sxs-lookup"><span data-stu-id="f63ff-107">The only type supported by these operators is the `bool` type.</span></span>

|<span data-ttu-id="f63ff-108">Operator</span><span class="sxs-lookup"><span data-stu-id="f63ff-108">Operator</span></span>|<span data-ttu-id="f63ff-109">Opis</span><span class="sxs-lookup"><span data-stu-id="f63ff-109">Description</span></span>|
|--------|-----------|
|`not`|<span data-ttu-id="f63ff-110">Logiczna Negacja</span><span class="sxs-lookup"><span data-stu-id="f63ff-110">Boolean negation</span></span>|
|<code>&#124;&#124;</code>|<span data-ttu-id="f63ff-111">Wartość logiczna lub</span><span class="sxs-lookup"><span data-stu-id="f63ff-111">Boolean OR</span></span>|
|`&&`|<span data-ttu-id="f63ff-112">Wartość logiczna AND</span><span class="sxs-lookup"><span data-stu-id="f63ff-112">Boolean AND</span></span>|

<span data-ttu-id="f63ff-113">Wykonaj logicznych AND i OR operatory *ocena zwarcia*, to znaczy umożliwiają podawanie wartości wyrażenie po prawej stronie operatora tylko w przypadku, gdy jest to niezbędne do obliczenia ogólnej wyniku wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="f63ff-113">The Boolean AND and OR operators perform *short-circuit evaluation*, that is, they evaluate the expression on the right of the operator only when it is necessary to determine the overall result of the expression.</span></span> <span data-ttu-id="f63ff-114">Drugie wyrażenie `&&` operator jest oceniany, tylko, jeśli pierwsze wyrażenie daje w wyniku `true`; drugie wyrażenie `||` operator jest oceniany, tylko, jeśli pierwsze wyrażenie daje w wyniku `false`.</span><span class="sxs-lookup"><span data-stu-id="f63ff-114">The second expression of the `&&` operator is evaluated only if the first expression evaluates to `true`; the second expression of the `||` operator is evaluated only if the first expression evaluates to `false`.</span></span>

## <a name="see-also"></a><span data-ttu-id="f63ff-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f63ff-115">See Also</span></span>
[<span data-ttu-id="f63ff-116">Operatory bitowe</span><span class="sxs-lookup"><span data-stu-id="f63ff-116">Bitwise Operators</span></span>](bitwise-operators.md)

[<span data-ttu-id="f63ff-117">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="f63ff-117">Arithmetic Operators</span></span>](arithmetic-operators.md)

[<span data-ttu-id="f63ff-118">Odwołanie do symboli i operatorów</span><span class="sxs-lookup"><span data-stu-id="f63ff-118">Symbol and Operator Reference</span></span>](index.md)
