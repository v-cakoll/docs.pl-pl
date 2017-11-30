---
title: "Niejawna konwersja z &#39; &lt;typename1&gt;&#39; do &#39;&lt; typename2&gt;&#39; podczas kopiowania wartości &#39; ByRef &#39; Parametr &#39; &lt;parametername&gt;&#39; z powrotem do pasującego argumentu."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc41999
- bc41999
helpviewer_keywords: BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9e858b475a816a35d18822643de5a273abe28562
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="implicit-conversion-from-39lttypename1gt39-to-39lttypename2gt39-in-copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument"></a><span data-ttu-id="9ee9b-102">Niejawna konwersja z &#39; &lt;typename1&gt;&#39; do &#39;&lt; typename2&gt;&#39; podczas kopiowania wartości &#39; ByRef &#39; Parametr &#39; &lt;parametername&gt;&#39; z powrotem do pasującego argumentu.</span><span class="sxs-lookup"><span data-stu-id="9ee9b-102">Implicit conversion from &#39;&lt;typename1&gt;&#39; to &#39;&lt;typename2&gt;&#39; in copying the value of &#39;ByRef&#39; parameter &#39;&lt;parametername&gt;&#39; back to the matching argument.</span></span>
<span data-ttu-id="9ee9b-103">Procedura jest wywoływana z [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) argumentu typu innego niż jego odpowiadającego mu parametru.</span><span class="sxs-lookup"><span data-stu-id="9ee9b-103">A procedure is called with a [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) argument of a different type than that of its corresponding parameter.</span></span>  
  
 <span data-ttu-id="9ee9b-104">Jeśli zostanie przekazany argument `ByRef`, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] czasami kopiuje wartość argumentu do zmiennej lokalnej w procedurze, a przekazywaniem odwołań do.</span><span class="sxs-lookup"><span data-stu-id="9ee9b-104">If you pass an argument `ByRef`, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] sometimes copies the argument value into a local variable in the procedure instead of passing a reference.</span></span> <span data-ttu-id="9ee9b-105">W takim przypadku po powrocie z procedurą [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] musi skopiować wartości zmiennej lokalnej powrót do argumentu w wywoływanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="9ee9b-105">In such a case, when the procedure returns, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] must then copy the local variable value back into the argument in the calling code.</span></span>  
  
 <span data-ttu-id="9ee9b-106">Jeśli `ByRef` wartość argumentu jest kopiowany do procedury i argumentów i parametrów są tego samego typu, niezbędne jest brak konwersji.</span><span class="sxs-lookup"><span data-stu-id="9ee9b-106">If a `ByRef` argument value is copied into the procedure and the argument and parameter are of the same type, no conversion is necessary.</span></span> <span data-ttu-id="9ee9b-107">Ale jeśli typy są różne, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] należy przekonwertować w obu kierunkach.</span><span class="sxs-lookup"><span data-stu-id="9ee9b-107">But if the types are different, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] must convert in both directions.</span></span> <span data-ttu-id="9ee9b-108">Ponieważ nie można użyć `CType` lub wszelkie inne słowa kluczowe konwersji na argumentu procedury lub parametrów, takich konwersji zawsze jest niejawnie.</span><span class="sxs-lookup"><span data-stu-id="9ee9b-108">Because you cannot use `CType` or any of the other conversion keywords on a procedure argument or parameter, such a conversion is always implicit.</span></span>  
  
 <span data-ttu-id="9ee9b-109">Domyślnie ten komunikat jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="9ee9b-109">By default, this message is a warning.</span></span> <span data-ttu-id="9ee9b-110">Aby uzyskać informacje na ukrywanie ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="9ee9b-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="9ee9b-111">**Identyfikator błędu:** BC41999</span><span class="sxs-lookup"><span data-stu-id="9ee9b-111">**Error ID:** BC41999</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9ee9b-112">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="9ee9b-112">To correct this error</span></span>  
  
-   <span data-ttu-id="9ee9b-113">Jeśli to możliwe, więc użyć wywoływania argumentów tego samego typu jako parametru procedury [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] konieczne wszelkiej konwersji.</span><span class="sxs-lookup"><span data-stu-id="9ee9b-113">If possible, use a calling argument of the same type as the procedure parameter, so [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] does not need to do any conversion.</span></span>  
  
-   <span data-ttu-id="9ee9b-114">Jeśli musisz wywołać procedurę z argumentem Typ inny niż typ parametru, ale nie muszą zwracać wartość do wywołującego argumentu, zdefiniuj dany parametr jako [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) zamiast `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="9ee9b-114">If you need to call the procedure with an argument type different from the parameter type but do not need to return a value into the calling argument, define the parameter to be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) instead of `ByRef`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ee9b-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9ee9b-115">See Also</span></span>  
 [<span data-ttu-id="9ee9b-116">Procedury</span><span class="sxs-lookup"><span data-stu-id="9ee9b-116">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="9ee9b-117">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="9ee9b-117">Procedure Parameters and Arguments</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="9ee9b-118">Przekazywanie argumentów według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="9ee9b-118">Passing Arguments by Value and by Reference</span></span>](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="9ee9b-119">Konwersje jawne i niejawne</span><span class="sxs-lookup"><span data-stu-id="9ee9b-119">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
