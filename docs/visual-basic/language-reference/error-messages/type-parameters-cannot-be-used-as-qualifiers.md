---
title: Parametrów typu nie można używać jako kwalifikatorów
ms.date: 07/20/2015
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords:
- BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
ms.openlocfilehash: 563010efc4f3049d330ee2b38b7f59e23292e630
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595147"
---
# <a name="type-parameters-cannot-be-used-as-qualifiers"></a><span data-ttu-id="6dbbf-102">Parametrów typu nie można używać jako kwalifikatorów</span><span class="sxs-lookup"><span data-stu-id="6dbbf-102">Type parameters cannot be used as qualifiers</span></span>
<span data-ttu-id="6dbbf-103">Element programowania jest kwalifikowany za pomocą kwalifikacji ciąg, który zawiera parametr typu.</span><span class="sxs-lookup"><span data-stu-id="6dbbf-103">A programming element is qualified with a qualification string that includes a type parameter.</span></span>  
  
 <span data-ttu-id="6dbbf-104">Parametr typu reprezentuje typ, który ma zostać podane w przypadku typu ogólnego jest tworzony.</span><span class="sxs-lookup"><span data-stu-id="6dbbf-104">A type parameter represents a requirement for a type that is to be supplied when the generic type is constructed.</span></span> <span data-ttu-id="6dbbf-105">Ten element nie reprezentuje określonego typu zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="6dbbf-105">It does not represent a specific defined type.</span></span> <span data-ttu-id="6dbbf-106">Ciąg kwalifikacji musi zawierać tylko elementy, które są zdefiniowane w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="6dbbf-106">A qualification string must include only elements that are defined at compile time.</span></span>  
  
 <span data-ttu-id="6dbbf-107">Poniższe instrukcje może spowodować wygenerowanie tego błędu.</span><span class="sxs-lookup"><span data-stu-id="6dbbf-107">The following statements can generate this error.</span></span>  
  
```  
Public Function checkText(Of c As System.Windows.Forms.Control)(  
    ByVal badText As String) As Boolean  
  
    Dim saveText As c.Text  
    ' Insert code to look for badText within saveText.  
End Function  
```  
  
 <span data-ttu-id="6dbbf-108">**Identyfikator błędu:** BC32098</span><span class="sxs-lookup"><span data-stu-id="6dbbf-108">**Error ID:** BC32098</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6dbbf-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="6dbbf-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="6dbbf-110">Usuń parametr typu z ciągu kwalifikacji lub Zamień zdefiniowanego typu.</span><span class="sxs-lookup"><span data-stu-id="6dbbf-110">Remove the type parameter from the qualification string, or replace it with a defined type.</span></span>  
  
2.  <span data-ttu-id="6dbbf-111">Jeśli musisz użyć skonstruowanego typu można znaleźć elementu programistycznego jest kwalifikowana, należy użyć dodatkowe logice programu.</span><span class="sxs-lookup"><span data-stu-id="6dbbf-111">If you need to use a constructed type to locate the programming element being qualified, you must use additional program logic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dbbf-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6dbbf-112">See Also</span></span>  
 [<span data-ttu-id="6dbbf-113">Odwołania do elementów zadeklarowanych</span><span class="sxs-lookup"><span data-stu-id="6dbbf-113">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="6dbbf-114">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6dbbf-114">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="6dbbf-115">Lista typów</span><span class="sxs-lookup"><span data-stu-id="6dbbf-115">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
