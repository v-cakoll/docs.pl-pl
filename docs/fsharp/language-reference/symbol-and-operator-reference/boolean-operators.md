---
title: Operatory logiczne (F#)
description: 'Więcej informacji na temat operatorów logicznych, które są dostępne w F # języka programowania.'
ms.date: 05/16/2016
ms.openlocfilehash: faa181090efa7c4064a30b42d83afa4888e98b82
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44272322"
---
# <a name="boolean-operators"></a><span data-ttu-id="eb973-103">Operatory logiczne</span><span class="sxs-lookup"><span data-stu-id="eb973-103">Boolean Operators</span></span>

<span data-ttu-id="eb973-104">W tym temacie opisano obsługę operatorów logicznych w języku F #.</span><span class="sxs-lookup"><span data-stu-id="eb973-104">This topic describes the support for Boolean operators in the F# language.</span></span>

## <a name="summary-of-boolean-operators"></a><span data-ttu-id="eb973-105">Podsumowanie operatory logiczne</span><span class="sxs-lookup"><span data-stu-id="eb973-105">Summary of Boolean Operators</span></span>

<span data-ttu-id="eb973-106">Poniższa tabela zawiera podsumowanie operatorów logicznych, które są dostępne w języku F #.</span><span class="sxs-lookup"><span data-stu-id="eb973-106">The following table summarizes the Boolean operators that are available in the F# language.</span></span> <span data-ttu-id="eb973-107">Jest to jedyny typ obsługiwanych przez te operatory `bool` typu.</span><span class="sxs-lookup"><span data-stu-id="eb973-107">The only type supported by these operators is the `bool` type.</span></span>

|<span data-ttu-id="eb973-108">Operator</span><span class="sxs-lookup"><span data-stu-id="eb973-108">Operator</span></span>|<span data-ttu-id="eb973-109">Opis</span><span class="sxs-lookup"><span data-stu-id="eb973-109">Description</span></span>|
|--------|-----------|
|`not`|<span data-ttu-id="eb973-110">Negacja logiczna</span><span class="sxs-lookup"><span data-stu-id="eb973-110">Boolean negation</span></span>|
|<code>&#124;&#124;</code>|<span data-ttu-id="eb973-111">Logiczne OR</span><span class="sxs-lookup"><span data-stu-id="eb973-111">Boolean OR</span></span>|
|`&&`|<span data-ttu-id="eb973-112">AND logiczne</span><span class="sxs-lookup"><span data-stu-id="eb973-112">Boolean AND</span></span>|

<span data-ttu-id="eb973-113">Logiczne AND i OR operatory wykonać *zwarcia*, czyli umożliwiają podawanie wartości wyrażenia po prawej stronie operatora tylko w przypadku, gdy jest to konieczne określić ogólny wynik wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="eb973-113">The Boolean AND and OR operators perform *short-circuit evaluation*, that is, they evaluate the expression on the right of the operator only when it is necessary to determine the overall result of the expression.</span></span> <span data-ttu-id="eb973-114">Drugie wyrażenie `&&` operator jest oceniane tylko wtedy, gdy pierwsze wyrażenie, które daje w wyniku `true`; drugie wyrażenie `||` operator jest oceniane tylko wtedy, gdy pierwsze wyrażenie, które daje w wyniku `false`.</span><span class="sxs-lookup"><span data-stu-id="eb973-114">The second expression of the `&&` operator is evaluated only if the first expression evaluates to `true`; the second expression of the `||` operator is evaluated only if the first expression evaluates to `false`.</span></span>

## <a name="see-also"></a><span data-ttu-id="eb973-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eb973-115">See also</span></span>

- [<span data-ttu-id="eb973-116">Operatory bitowe</span><span class="sxs-lookup"><span data-stu-id="eb973-116">Bitwise Operators</span></span>](bitwise-operators.md)
- [<span data-ttu-id="eb973-117">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="eb973-117">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="eb973-118">Odwołanie do symboli i operatorów</span><span class="sxs-lookup"><span data-stu-id="eb973-118">Symbol and Operator Reference</span></span>](index.md)
