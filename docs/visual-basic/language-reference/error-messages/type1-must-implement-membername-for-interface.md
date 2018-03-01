---
title: "&lt;type1&gt;&#39;&lt; Właściwość TypeName&gt;&#39; musi wdrożenie &#39;&lt; membername&gt;&#39; dla interfejsu &#39;&lt; InterfaceName&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 05e0229d0259c519d4db265c017a5040b425c79a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="lttype1gt39lttypenamegt39-must-implement-39ltmembernamegt39-for-interface-39ltinterfacenamegt39"></a><span data-ttu-id="1b907-102">&lt;type1&gt;&#39;&lt; Właściwość TypeName&gt;&#39; musi wdrożenie &#39;&lt; membername&gt;&#39; dla interfejsu &#39;&lt; InterfaceName&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="1b907-102">&lt;type1&gt;&#39;&lt;typename&gt;&#39; must implement &#39;&lt;membername&gt;&#39; for interface &#39;&lt;interfacename&gt;&#39;</span></span>
<span data-ttu-id="1b907-103">"\<typename >' musi implementować"\<membername > "dla interfejsu"\<interfacename > ".</span><span class="sxs-lookup"><span data-stu-id="1b907-103">'\<typename>' must implement '\<membername>' for interface '\<interfacename>'.</span></span> <span data-ttu-id="1b907-104">Właściwość implementowania musi mieć pasujące "ReadOnly" / specyfikatory "WriteOnly".</span><span class="sxs-lookup"><span data-stu-id="1b907-104">Implementing property must have matching 'ReadOnly'/'WriteOnly' specifiers.</span></span>  
  
 <span data-ttu-id="1b907-105">Klasy lub struktury oświadczeń do zaimplementowania interfejsu, ale nie implementuje procedury, właściwości lub zdarzeń zdefiniowanych przez interfejs.</span><span class="sxs-lookup"><span data-stu-id="1b907-105">A class or structure claims to implement an interface but does not implement a procedure, property, or event defined by the interface.</span></span> <span data-ttu-id="1b907-106">Każdy element członkowski interfejsu musi być implementowana.</span><span class="sxs-lookup"><span data-stu-id="1b907-106">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="1b907-107">**Identyfikator błędu:** BC30154</span><span class="sxs-lookup"><span data-stu-id="1b907-107">**Error ID:** BC30154</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1b907-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="1b907-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="1b907-109">Deklaruje elementu członkowskiego o tej samej nazwie i podpisie zgodnie z definicją w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="1b907-109">Declare a member with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="1b907-110">Należy uwzględnić co najmniej `End Function`, `End Sub`, lub `End Property` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="1b907-110">Be sure to include at least the `End Function`, `End Sub`, or `End Property` statement.</span></span>  
  
2.  <span data-ttu-id="1b907-111">Dodaj `Implements` klauzuli na końcu `Function`, `Sub`, `Property`, lub `Event` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="1b907-111">Add an `Implements` clause to the end of the `Function`, `Sub`, `Property`, or `Event` statement.</span></span> <span data-ttu-id="1b907-112">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="1b907-112">For example:</span></span>  
  
    ```  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3.  <span data-ttu-id="1b907-113">Podczas implementowania właściwości, upewnij się, że `ReadOnly` lub `WriteOnly` jest używana w taki sam sposób jak w definicji interfejsu.</span><span class="sxs-lookup"><span data-stu-id="1b907-113">When implementing a property, make sure that `ReadOnly` or `WriteOnly` is used in the same way as in the interface definition.</span></span>  
  
4.  <span data-ttu-id="1b907-114">Podczas implementowania właściwość, należy zadeklarować `Get` i `Set` procedur, zależnie od potrzeb.</span><span class="sxs-lookup"><span data-stu-id="1b907-114">When implementing a property, declare `Get` and `Set` procedures, as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b907-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1b907-115">See Also</span></span>  
 [<span data-ttu-id="1b907-116">Implements — instrukcja</span><span class="sxs-lookup"><span data-stu-id="1b907-116">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)  
 [<span data-ttu-id="1b907-117">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="1b907-117">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
