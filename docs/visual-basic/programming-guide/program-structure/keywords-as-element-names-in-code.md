---
title: Słowa kluczowe jako nazwy elementów w Code (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts [Visual Basic]
- element names [Visual Basic], in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
ms.openlocfilehash: 053149334118d69e5e85bdbd0f9a45e855e3d4dd
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980103"
---
# <a name="keywords-as-element-names-in-code-visual-basic"></a><span data-ttu-id="d7628-102">Słowa kluczowe jako nazwy elementów w Code (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d7628-102">Keywords as Element Names in Code (Visual Basic)</span></span>
<span data-ttu-id="d7628-103">Dowolnego elementu programu — takie jak zmienna, klasy ani składowej — może mieć taką samą nazwę jak ograniczony — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="d7628-103">Any program element — such as a variable, class, or member — can have the same name as a restricted keyword.</span></span> <span data-ttu-id="d7628-104">Na przykład można utworzyć zmiennej o nazwie `Loop`.</span><span class="sxs-lookup"><span data-stu-id="d7628-104">For example, you can create a variable named `Loop`.</span></span> <span data-ttu-id="d7628-105">Jednak do odwoływania się do swoją wersję — która ma taką samą nazwę jak zastrzeżonego `Loop` — słowo kluczowe — należy poprzedzić go ukośnikiem ciągu pełnej kwalifikacji lub należy ją ująć w nawiasy kwadratowe (`[ ]`), jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d7628-105">However, to refer to your version of it — which has the same name as the restricted `Loop` keyword — you must either precede it with a full qualification string or enclose it in square brackets (`[ ]`), as the following example shows.</span></span>  
  
 [!code-vb[VbVbcnConventions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#8)]  
  
 <span data-ttu-id="d7628-106">Wykonaj jedną z tych wersji, a następnie języka Visual Basic założono użycie wewnętrznego `Loop` — słowo kluczowe i generuje błąd, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="d7628-106">If you do not do either of these, then Visual Basic assumes use of the intrinsic `Loop` keyword and produces an error, as in the following example:</span></span>  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 <span data-ttu-id="d7628-107">Można użyć nawiasy kwadratowe przy odwoływaniu się do formularzy i kontrolek, a w przypadku deklarowania zmiennej lub definiowanie procedury o takiej samej nazwie jako ograniczeniami — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="d7628-107">You can use square brackets when referring to forms and controls, and when declaring a variable or defining a procedure with the same name as a restricted keyword.</span></span> <span data-ttu-id="d7628-108">Można łatwo zapomnieć o kwalifikowania nazwy lub zawierać nawiasów kwadratowych, zatem wprowadzenie błędów w kodzie i utrudnić do odczytu.</span><span class="sxs-lookup"><span data-stu-id="d7628-108">It can be easy to forget to qualify names or include square brackets, and thus introduce errors into your code and make it harder to read.</span></span> <span data-ttu-id="d7628-109">Z tego powodu zaleca się nie używać ograniczeniami słowa kluczowe jako nazwy elementów programu.</span><span class="sxs-lookup"><span data-stu-id="d7628-109">For this reason, we recommend that you not use restricted keywords as the names of program elements.</span></span> <span data-ttu-id="d7628-110">Jednak jeśli przyszłych wersjach programu Visual Basic definiuje nowe słowo kluczowe powodującą konflikt z istniejącego formularza lub nazwa kontrolki, następnie służy ta technika podczas aktualizowania kodu do pracy z nową wersją.</span><span class="sxs-lookup"><span data-stu-id="d7628-110">However, if a future version of Visual Basic defines a new keyword that conflicts with an existing form or control name, then you can use this technique when updating your code to work with the new version.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d7628-111">Program może również obejmować nazwy elementów dostarczane przez inne przywoływanych zestawach.</span><span class="sxs-lookup"><span data-stu-id="d7628-111">Your program also might include element names provided by other referenced assemblies.</span></span> <span data-ttu-id="d7628-112">Jeśli te nazwy są w konflikcie z ograniczeniami słowami kluczowymi, następnie umieszczenie nawiasami kwadratowymi wokół nich powoduje, że Visual Basic, aby zinterpretować je jako elementów zdefiniowanych.</span><span class="sxs-lookup"><span data-stu-id="d7628-112">If these names conflict with restricted keywords, then placing square brackets around them causes Visual Basic to interpret them as your defined elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7628-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d7628-113">See also</span></span>
- [<span data-ttu-id="d7628-114">Visual Basic — konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="d7628-114">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
- [<span data-ttu-id="d7628-115">Konwencje dotyczące struktury programów i kodu</span><span class="sxs-lookup"><span data-stu-id="d7628-115">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [<span data-ttu-id="d7628-116">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="d7628-116">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
