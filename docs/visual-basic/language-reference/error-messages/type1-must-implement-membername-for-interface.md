---
title: '&lt;type1&gt;&#39;&lt;typename&gt; &#39; musi implementować &#39; &lt;membername&gt; &#39; interfejsu &#39; &lt;interfacename&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: 14e7bd199215764676a4b563eafc68bd6dabadc7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574745"
---
# <a name="lttype1gt39lttypenamegt39-must-implement-39ltmembernamegt39-for-interface-39ltinterfacenamegt39"></a><span data-ttu-id="db350-102">&lt;type1&gt;&#39;&lt;typename&gt; &#39; musi implementować &#39; &lt;membername&gt; &#39; interfejsu &#39; &lt;interfacename&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="db350-102">&lt;type1&gt;&#39;&lt;typename&gt;&#39; must implement &#39;&lt;membername&gt;&#39; for interface &#39;&lt;interfacename&gt;&#39;</span></span>
<span data-ttu-id="db350-103">"\<typename >" musi implementować "\<membername >" dla interfejsu "\<interfacename >".</span><span class="sxs-lookup"><span data-stu-id="db350-103">'\<typename>' must implement '\<membername>' for interface '\<interfacename>'.</span></span> <span data-ttu-id="db350-104">Implementowanie właściwości musi mieć dopasowania "ReadOnly" / specyfikatorów "WriteOnly".</span><span class="sxs-lookup"><span data-stu-id="db350-104">Implementing property must have matching 'ReadOnly'/'WriteOnly' specifiers.</span></span>  
  
 <span data-ttu-id="db350-105">Klasa lub struktura oświadczeń zaimplementować interfejs, ale nie implementuje procedurę, właściwości lub zdarzenia, zdefiniowany przez interfejs.</span><span class="sxs-lookup"><span data-stu-id="db350-105">A class or structure claims to implement an interface but does not implement a procedure, property, or event defined by the interface.</span></span> <span data-ttu-id="db350-106">Należy zaimplementować każdego członka interfejsu.</span><span class="sxs-lookup"><span data-stu-id="db350-106">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="db350-107">**Identyfikator błędu:** BC30154</span><span class="sxs-lookup"><span data-stu-id="db350-107">**Error ID:** BC30154</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="db350-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="db350-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="db350-109">Zadeklaruj element członkowski o takiej samej nazwie i podpisie, zgodnie z definicją w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="db350-109">Declare a member with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="db350-110">Pamiętaj uwzględnić co najmniej `End Function`, `End Sub`, lub `End Property` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="db350-110">Be sure to include at least the `End Function`, `End Sub`, or `End Property` statement.</span></span>  
  
2.  <span data-ttu-id="db350-111">Dodaj `Implements` klauzulę na końcu `Function`, `Sub`, `Property`, lub `Event` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="db350-111">Add an `Implements` clause to the end of the `Function`, `Sub`, `Property`, or `Event` statement.</span></span> <span data-ttu-id="db350-112">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="db350-112">For example:</span></span>  
  
    ```  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3.  <span data-ttu-id="db350-113">Podczas implementowania właściwością, upewnij się, że `ReadOnly` lub `WriteOnly` jest używana w taki sam sposób jak w definicji interfejsu.</span><span class="sxs-lookup"><span data-stu-id="db350-113">When implementing a property, make sure that `ReadOnly` or `WriteOnly` is used in the same way as in the interface definition.</span></span>  
  
4.  <span data-ttu-id="db350-114">Podczas implementowania właściwość, należy zadeklarować `Get` i `Set` procedur, zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="db350-114">When implementing a property, declare `Get` and `Set` procedures, as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db350-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="db350-115">See also</span></span>
- [<span data-ttu-id="db350-116">Implements, instrukcja</span><span class="sxs-lookup"><span data-stu-id="db350-116">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
- [<span data-ttu-id="db350-117">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="db350-117">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
