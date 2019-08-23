---
title: Słowa kluczowe jako nazwy elementów w Code (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts [Visual Basic]
- element names [Visual Basic], in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
ms.openlocfilehash: 2e3613bd4a74da51cf7dbb63e52eddca811ca8e1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947666"
---
# <a name="keywords-as-element-names-in-code-visual-basic"></a><span data-ttu-id="f1a27-102">Słowa kluczowe jako nazwy elementów w Code (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1a27-102">Keywords as Element Names in Code (Visual Basic)</span></span>
<span data-ttu-id="f1a27-103">Każdy element programu, taki jak zmienna, Klasa lub element członkowski — może mieć taką samą nazwę jak słowo kluczowe z ograniczeniami.</span><span class="sxs-lookup"><span data-stu-id="f1a27-103">Any program element — such as a variable, class, or member — can have the same name as a restricted keyword.</span></span> <span data-ttu-id="f1a27-104">Na przykład można utworzyć zmienną o nazwie `Loop`.</span><span class="sxs-lookup"><span data-stu-id="f1a27-104">For example, you can create a variable named `Loop`.</span></span> <span data-ttu-id="f1a27-105">Jednak, aby odwołać się do używanej wersji programu, która ma taką samą nazwę jak `Loop` słowo kluczowe z ograniczeniami, należy poprzedzić ją ciągiem zawierającym pełną kwalifikację lub ująć ją w`[ ]`nawiasy kwadratowe (), jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f1a27-105">However, to refer to your version of it — which has the same name as the restricted `Loop` keyword — you must either precede it with a full qualification string or enclose it in square brackets (`[ ]`), as the following example shows.</span></span>  
  
 [!code-vb[VbVbcnConventions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#8)]  
  
 <span data-ttu-id="f1a27-106">Jeśli nie wykonasz żadnej z tych czynności, Visual Basic zakłada użycie słowa kluczowego wewnętrznego `Loop` i tworzy błąd, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="f1a27-106">If you do not do either of these, then Visual Basic assumes use of the intrinsic `Loop` keyword and produces an error, as in the following example:</span></span>  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 <span data-ttu-id="f1a27-107">Można użyć nawiasów kwadratowych podczas odwoływania się do formularzy i kontrolek, a w przypadku deklarowania zmiennej lub definiowania procedury o tej samej nazwie co słowo kluczowe z ograniczeniami.</span><span class="sxs-lookup"><span data-stu-id="f1a27-107">You can use square brackets when referring to forms and controls, and when declaring a variable or defining a procedure with the same name as a restricted keyword.</span></span> <span data-ttu-id="f1a27-108">Można łatwo zapomnieć o kwalifikowaniu się nazw lub dołączeniu nawiasów kwadratowych, a tym samym wprowadzić błędy do kodu i utrudnić odczytanie.</span><span class="sxs-lookup"><span data-stu-id="f1a27-108">It can be easy to forget to qualify names or include square brackets, and thus introduce errors into your code and make it harder to read.</span></span> <span data-ttu-id="f1a27-109">Z tego powodu zaleca się, aby nie używać słów kluczowych z ograniczeniami jako nazw elementów programu.</span><span class="sxs-lookup"><span data-stu-id="f1a27-109">For this reason, we recommend that you not use restricted keywords as the names of program elements.</span></span> <span data-ttu-id="f1a27-110">Jeśli jednak przyszła wersja Visual Basic definiuje nowe słowo kluczowe, które powoduje konflikt z istniejącą nazwą formularza lub kontrolki, wówczas można użyć tej techniki podczas aktualizowania kodu do pracy z nową wersją.</span><span class="sxs-lookup"><span data-stu-id="f1a27-110">However, if a future version of Visual Basic defines a new keyword that conflicts with an existing form or control name, then you can use this technique when updating your code to work with the new version.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f1a27-111">Program może również zawierać nazwy elementów udostępniane przez inne przywoływane zestawy.</span><span class="sxs-lookup"><span data-stu-id="f1a27-111">Your program also might include element names provided by other referenced assemblies.</span></span> <span data-ttu-id="f1a27-112">Jeśli te nazwy powodują konflikt z ograniczonymi słowami kluczowymi, umieszczenie nawiasów kwadratowych spowoduje, że Visual Basic interpretują je jako zdefiniowane elementy.</span><span class="sxs-lookup"><span data-stu-id="f1a27-112">If these names conflict with restricted keywords, then placing square brackets around them causes Visual Basic to interpret them as your defined elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1a27-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f1a27-113">See also</span></span>

- [<span data-ttu-id="f1a27-114">Konwencje nazewnictwa Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f1a27-114">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
- [<span data-ttu-id="f1a27-115">Konwencje dotyczące struktury programów i kodu</span><span class="sxs-lookup"><span data-stu-id="f1a27-115">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [<span data-ttu-id="f1a27-116">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="f1a27-116">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
