---
title: Operatory logiczne (F#)
description: "Więcej informacji na temat operatorów logicznych, które są dostępne w języku programowania w języku F #."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: f79370b8-4bc2-4704-b514-d392c80942bd
ms.openlocfilehash: 63588f2e371bf2c0f15de0b8a26a46be82f832c7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="boolean-operators"></a><span data-ttu-id="be0ec-104">Operatory logiczne</span><span class="sxs-lookup"><span data-stu-id="be0ec-104">Boolean Operators</span></span>

<span data-ttu-id="be0ec-105">W tym temacie opisano obsługę operatorów logicznych w języku F #.</span><span class="sxs-lookup"><span data-stu-id="be0ec-105">This topic describes the support for Boolean operators in the F# language.</span></span>


## <a name="summary-of-boolean-operators"></a><span data-ttu-id="be0ec-106">Podsumowanie operatory logiczne</span><span class="sxs-lookup"><span data-stu-id="be0ec-106">Summary of Boolean Operators</span></span>
<span data-ttu-id="be0ec-107">Poniższa tabela zawiera podsumowanie operatorów logicznych, które są dostępne w języku F #.</span><span class="sxs-lookup"><span data-stu-id="be0ec-107">The following table summarizes the Boolean operators that are available in the F# language.</span></span> <span data-ttu-id="be0ec-108">Jest to jedyny typ obsługiwany przez te podmioty `bool` typu.</span><span class="sxs-lookup"><span data-stu-id="be0ec-108">The only type supported by these operators is the `bool` type.</span></span>

|<span data-ttu-id="be0ec-109">Operator</span><span class="sxs-lookup"><span data-stu-id="be0ec-109">Operator</span></span>|<span data-ttu-id="be0ec-110">Opis</span><span class="sxs-lookup"><span data-stu-id="be0ec-110">Description</span></span>|
|--------|-----------|
|`not`|<span data-ttu-id="be0ec-111">Logiczna Negacja</span><span class="sxs-lookup"><span data-stu-id="be0ec-111">Boolean negation</span></span>|
|<code>&#124;&#124;</code>|<span data-ttu-id="be0ec-112">Wartość logiczna lub</span><span class="sxs-lookup"><span data-stu-id="be0ec-112">Boolean OR</span></span>|
|`&&`|<span data-ttu-id="be0ec-113">Wartość logiczna AND</span><span class="sxs-lookup"><span data-stu-id="be0ec-113">Boolean AND</span></span>|

<span data-ttu-id="be0ec-114">Wykonaj logicznych AND i OR operatory *ocena zwarcia*, to znaczy umożliwiają podawanie wartości wyrażenie po prawej stronie operatora tylko w przypadku, gdy jest to niezbędne do obliczenia ogólnej wyniku wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="be0ec-114">The Boolean AND and OR operators perform *short-circuit evaluation*, that is, they evaluate the expression on the right of the operator only when it is necessary to determine the overall result of the expression.</span></span> <span data-ttu-id="be0ec-115">Drugie wyrażenie `&&` operator jest oceniany, tylko, jeśli pierwsze wyrażenie daje w wyniku `true`; drugie wyrażenie `||` operator jest oceniany, tylko, jeśli pierwsze wyrażenie daje w wyniku `false`.</span><span class="sxs-lookup"><span data-stu-id="be0ec-115">The second expression of the `&&` operator is evaluated only if the first expression evaluates to `true`; the second expression of the `||` operator is evaluated only if the first expression evaluates to `false`.</span></span>

## <a name="see-also"></a><span data-ttu-id="be0ec-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="be0ec-116">See Also</span></span>
[<span data-ttu-id="be0ec-117">Operatory bitowe</span><span class="sxs-lookup"><span data-stu-id="be0ec-117">Bitwise Operators</span></span>](bitwise-operators.md)

[<span data-ttu-id="be0ec-118">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="be0ec-118">Arithmetic Operators</span></span>](arithmetic-operators.md)

[<span data-ttu-id="be0ec-119">Operator odwołanie do symbolu i</span><span class="sxs-lookup"><span data-stu-id="be0ec-119">Symbol and Operator Reference</span></span>](index.md)
