---
title: "Kopiowanie wartości &#39; ByRef &#39; Parametr &#39; &lt;parametername&gt;&#39; z powrotem pasującego narrows argumentu typu &#39;&lt; typename1&gt;&#39; na typ &#39;&lt; typename2&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32053
- vbc32053
helpviewer_keywords: BC32053
ms.assetid: 281564b7-99f7-451f-b10d-f985e831bb25
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4bf993639007162e2e17d4b8cb9dfe8d5316acaa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument-narrows-from-type-39lttypename1gt39-to-type-39lttypename2gt39"></a><span data-ttu-id="fb94c-102">Kopiowanie wartości &#39; ByRef &#39; Parametr &#39; &lt;parametername&gt;&#39; z powrotem pasującego narrows argumentu typu &#39;&lt; typename1&gt;&#39; na typ &#39;&lt; typename2&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="fb94c-102">Copying the value of &#39;ByRef&#39; parameter &#39;&lt;parametername&gt;&#39; back to the matching argument narrows from type &#39;&lt;typename1&gt;&#39; to type &#39;&lt;typename2&gt;&#39;</span></span>
<span data-ttu-id="fb94c-103">Procedura jest wywoływana z argumentem rozszerzająca do odpowiedniego typu parametru, a jest zawężanie konwersji z parametru do argumentu.</span><span class="sxs-lookup"><span data-stu-id="fb94c-103">A procedure is called with an argument that widens to the corresponding parameter type, and the conversion from the parameter to the argument is narrowing.</span></span>  
  
 <span data-ttu-id="fb94c-104">Podczas definiowania klasy lub struktury, można zdefiniować co najmniej jeden operatory konwersji można przekonwertować typu klasy lub struktury na inne typy.</span><span class="sxs-lookup"><span data-stu-id="fb94c-104">When you define a class or structure, you can define one or more conversion operators to convert that class or structure type to other types.</span></span> <span data-ttu-id="fb94c-105">Można również definiować operatory konwersji odwrotnej do konwertowania tych typów do własnej klasy lub typ struktury.</span><span class="sxs-lookup"><span data-stu-id="fb94c-105">You can also define reverse conversion operators to convert those other types back to your class or structure type.</span></span> <span data-ttu-id="fb94c-106">Korzystając z danego typu klasy lub struktury w wywołaniu procedury, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] można użyć tych operatory konwersji można przekonwertować typu argumentu na typ jego odpowiadającego mu parametru.</span><span class="sxs-lookup"><span data-stu-id="fb94c-106">When you use your class or structure type in a procedure call, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] can use these conversion operators to convert the type of an argument to the type of its corresponding parameter.</span></span>  
  
 <span data-ttu-id="fb94c-107">Jeśli zostanie przekazany argument [ByRef](../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] czasami kopiuje wartość argumentu do zmiennej lokalnej w procedurze, a przekazywaniem odwołań do.</span><span class="sxs-lookup"><span data-stu-id="fb94c-107">If you pass the argument [ByRef](../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] sometimes copies the argument value into a local variable in the procedure instead of passing a reference.</span></span> <span data-ttu-id="fb94c-108">W takim przypadku po powrocie z procedurą [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] musi skopiować wartości zmiennej lokalnej powrót do argumentu w wywoływanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="fb94c-108">In such a case, when the procedure returns, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] must then copy the local variable value back into the argument in the calling code.</span></span>  
  
 <span data-ttu-id="fb94c-109">Jeśli `ByRef` wartość argumentu jest kopiowany do procedury i argumentów i parametrów są tego samego typu, niezbędne jest brak konwersji.</span><span class="sxs-lookup"><span data-stu-id="fb94c-109">If a `ByRef` argument value is copied into the procedure and the argument and parameter are of the same type, no conversion is necessary.</span></span> <span data-ttu-id="fb94c-110">Ale jeśli typy są różne, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] należy przekonwertować w obu kierunkach.</span><span class="sxs-lookup"><span data-stu-id="fb94c-110">But if the types are different, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] must convert in both directions.</span></span> <span data-ttu-id="fb94c-111">Jeśli jeden z typów jest danego typu klasy lub struktury [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] po przekonwertowaniu zarówno do, jak i z innego typu.</span><span class="sxs-lookup"><span data-stu-id="fb94c-111">If one of the types is your class or structure type, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] must convert it both to and from the other type.</span></span> <span data-ttu-id="fb94c-112">Jeśli jeden z tych konwersje to rozszerzenie, może być zawężanie konwersji odwrotnej.</span><span class="sxs-lookup"><span data-stu-id="fb94c-112">If one of these conversions is widening, the reverse conversion might be narrowing.</span></span>  
  
 <span data-ttu-id="fb94c-113">**Identyfikator błędu:** BC32053</span><span class="sxs-lookup"><span data-stu-id="fb94c-113">**Error ID:** BC32053</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fb94c-114">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="fb94c-114">To correct this error</span></span>  
  
-   <span data-ttu-id="fb94c-115">Jeśli to możliwe, więc użyć wywoływania argumentów tego samego typu jako parametru procedury [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] konieczne wszelkiej konwersji.</span><span class="sxs-lookup"><span data-stu-id="fb94c-115">If possible, use a calling argument of the same type as the procedure parameter, so [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] does not need to do any conversion.</span></span>  
  
-   <span data-ttu-id="fb94c-116">Jeśli musisz wywołać procedurę z argumentem Typ inny niż typ parametru, ale nie muszą zwracać wartość do wywołującego argumentu, zdefiniuj dany parametr jako [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) zamiast `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="fb94c-116">If you need to call the procedure with an argument type different from the parameter type but do not need to return a value into the calling argument, define the parameter to be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) instead of `ByRef`.</span></span>  
  
-   <span data-ttu-id="fb94c-117">Jeśli trzeba zwrócić wartość do wywołującego argumentu, należy zdefiniować operator konwersji odwrotnej jako [Widening](../../../visual-basic/language-reference/modifiers/widening.md), jeśli to możliwe.</span><span class="sxs-lookup"><span data-stu-id="fb94c-117">If you need to return a value into the calling argument, define the reverse conversion operator as [Widening](../../../visual-basic/language-reference/modifiers/widening.md), if possible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb94c-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fb94c-118">See Also</span></span>  
 [<span data-ttu-id="fb94c-119">Procedury</span><span class="sxs-lookup"><span data-stu-id="fb94c-119">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="fb94c-120">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="fb94c-120">Procedure Parameters and Arguments</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="fb94c-121">Przekazywanie argumentów według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="fb94c-121">Passing Arguments by Value and by Reference</span></span>](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="fb94c-122">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="fb94c-122">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [<span data-ttu-id="fb94c-123">Operator — instrukcja</span><span class="sxs-lookup"><span data-stu-id="fb94c-123">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="fb94c-124">Porady: Definiowanie operatora</span><span class="sxs-lookup"><span data-stu-id="fb94c-124">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [<span data-ttu-id="fb94c-125">Porady: Definiowanie operatora konwersji</span><span class="sxs-lookup"><span data-stu-id="fb94c-125">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="fb94c-126">Konwersje typów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fb94c-126">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="fb94c-127">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="fb94c-127">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
