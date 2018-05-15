---
title: Słowa kluczowe jako nazwy elementów w Code (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts [Visual Basic]
- element names [Visual Basic], in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
ms.openlocfilehash: 53c3172e8518115d001c23be2430fbc87ae1b60f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="keywords-as-element-names-in-code-visual-basic"></a><span data-ttu-id="4acf8-102">Słowa kluczowe jako nazwy elementów w Code (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4acf8-102">Keywords as Element Names in Code (Visual Basic)</span></span>
<span data-ttu-id="4acf8-103">Każdy element program — takie jak zmienna, klasa lub element członkowski — może mieć taką samą nazwę jak ograniczeniami — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="4acf8-103">Any program element — such as a variable, class, or member — can have the same name as a restricted keyword.</span></span> <span data-ttu-id="4acf8-104">Na przykład można utworzyć zmiennej o nazwie `Loop`.</span><span class="sxs-lookup"><span data-stu-id="4acf8-104">For example, you can create a variable named `Loop`.</span></span> <span data-ttu-id="4acf8-105">Jednak aby odwołać się do używanej wersji — który ma taką samą nazwę jak ograniczeniami `Loop` — słowo kluczowe — należy poprzedzić ciągu pełnej kwalifikacji lub została ujęta w nawiasy kwadratowe (`[ ]`), jak pokazano na poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="4acf8-105">However, to refer to your version of it — which has the same name as the restricted `Loop` keyword — you must either precede it with a full qualification string or enclose it in square brackets (`[ ]`), as the following example shows.</span></span>  
  
 [!code-vb[VbVbcnConventions#8](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/keywords-as-element-names-in-code_1.vb)]  
  
 <span data-ttu-id="4acf8-106">Wykonaj jedną z nich, a następnie Visual Basic założono użycie wewnętrznej `Loop` — słowo kluczowe i tworzy błąd, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="4acf8-106">If you do not do either of these, then Visual Basic assumes use of the intrinsic `Loop` keyword and produces an error, as in the following example:</span></span>  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 <span data-ttu-id="4acf8-107">Podczas odwoływania się do formularzy i kontrolek i gdy służy nawiasy kwadratowe deklarowanie zmiennej lub definiujący procedurę o tej samej nazwie jako ograniczeniami — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="4acf8-107">You can use square brackets when referring to forms and controls, and when declaring a variable or defining a procedure with the same name as a restricted keyword.</span></span> <span data-ttu-id="4acf8-108">Można go łatwo Pamiętaj, aby zakwalifikować nazwy lub obejmują nawiasów kwadratowych, w związku z tym spowodują one błędów w kodzie i utrudnić odczytu.</span><span class="sxs-lookup"><span data-stu-id="4acf8-108">It can be easy to forget to qualify names or include square brackets, and thus introduce errors into your code and make it harder to read.</span></span> <span data-ttu-id="4acf8-109">Z tego powodu zalecamy nie używać ograniczeniami słowa kluczowe jako nazwy elementów programu.</span><span class="sxs-lookup"><span data-stu-id="4acf8-109">For this reason, we recommend that you not use restricted keywords as the names of program elements.</span></span> <span data-ttu-id="4acf8-110">Jednak jeśli przyszłych wersjach programu Visual Basic definiuje new — słowo kluczowe powodujący konflikt z istniejącym formularzu lub nazwa formantu, następnie służy ta technika podczas aktualizowania kodu do pracy z nową wersją.</span><span class="sxs-lookup"><span data-stu-id="4acf8-110">However, if a future version of Visual Basic defines a new keyword that conflicts with an existing form or control name, then you can use this technique when updating your code to work with the new version.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4acf8-111">Program może również obejmować nazwy elementów udostępnione przez innych zestawów występujących w odwołaniach.</span><span class="sxs-lookup"><span data-stu-id="4acf8-111">Your program also might include element names provided by other referenced assemblies.</span></span> <span data-ttu-id="4acf8-112">Jeśli te nazwy w konflikcie z ograniczeniami słów kluczowych, następnie umieszczenie nawiasy kwadratowe wokół nich spowoduje Visual Basic zinterpretować je jako określonych elementów.</span><span class="sxs-lookup"><span data-stu-id="4acf8-112">If these names conflict with restricted keywords, then placing square brackets around them causes Visual Basic to interpret them as your defined elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4acf8-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4acf8-113">See Also</span></span>  
 [<span data-ttu-id="4acf8-114">Visual Basic — konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="4acf8-114">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [<span data-ttu-id="4acf8-115">Struktura programu i konwencje związane z kodami</span><span class="sxs-lookup"><span data-stu-id="4acf8-115">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [<span data-ttu-id="4acf8-116">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="4acf8-116">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
