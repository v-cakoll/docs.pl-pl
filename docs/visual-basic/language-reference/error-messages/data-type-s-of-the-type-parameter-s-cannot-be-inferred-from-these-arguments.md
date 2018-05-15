---
title: Na podstawie tych argumentów nie można wywnioskować typów danych parametrów typu
ms.date: 07/20/2015
f1_keywords:
- bc36644
- bc36647
- vbc36647
- vbc36644
helpviewer_keywords:
- BC36644
- BC36647
ms.assetid: 0e0050f2-2039-4311-b260-f0ebfde84189
ms.openlocfilehash: 6f84df5c9388220e5ca817d95362753df0920534
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="data-types-of-the-type-parameters-cannot-be-inferred-from-these-arguments"></a><span data-ttu-id="859b3-102">Na podstawie tych argumentów nie można wywnioskować typów danych parametrów typu</span><span class="sxs-lookup"><span data-stu-id="859b3-102">Data type(s) of the type parameter(s) cannot be inferred from these arguments</span></span>
<span data-ttu-id="859b3-103">Na podstawie tych argumentów nie można wywnioskować typów danych parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="859b3-103">Data type(s) of the type parameter(s) cannot be inferred from these arguments.</span></span> <span data-ttu-id="859b3-104">Określanie danych typów jawnie może rozwiązać ten problem.</span><span class="sxs-lookup"><span data-stu-id="859b3-104">Specifying the data type(s) explicitly might correct this error.</span></span>  
  
 <span data-ttu-id="859b3-105">Ten błąd występuje, gdy Rozpoznanie przeciążenia nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="859b3-105">This error occurs when overload resolution has failed.</span></span> <span data-ttu-id="859b3-106">Nastąpi to jako podrzędny komunikat informujący o tym, dlaczego określonego przeciążenie kandydujące został wyeliminowany.</span><span class="sxs-lookup"><span data-stu-id="859b3-106">It occurs as a subordinate message that states why a particular overload candidate has been eliminated.</span></span> <span data-ttu-id="859b3-107">Komunikat o błędzie wyjaśniono, że kompilator nie mogą używać wnioskowanie o typie można znaleźć typów danych parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="859b3-107">The error message explains that the compiler cannot use type inference to find data types for the type parameters.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="859b3-108">Podczas określania argumentów nie jest opcją (na przykład dla operatorów zapytań w wyrażeniach zapytań), zostanie wyświetlony komunikat o błędzie bez drugie zdanie.</span><span class="sxs-lookup"><span data-stu-id="859b3-108">When specifying arguments is not an option (for example, for query operators in query expressions), the error message appears without the second sentence.</span></span>  
  
 <span data-ttu-id="859b3-109">Poniższy kod przedstawia błędu.</span><span class="sxs-lookup"><span data-stu-id="859b3-109">The following code demonstrates the error.</span></span>  
  
```vb  
Module Module1  
  
    Sub Main()  
  
        '' Not Valid.  
        'OverloadedGenericMethod("Hello", "World")  
  
    End Sub  
  
    Sub OverloadedGenericMethod(Of T)(ByVal x As String,   
                                      ByVal y As InterfaceExample(Of T))  
    End Sub  
  
    Sub OverloadedGenericMethod(Of T, R)(ByVal x As T,   
                                         ByVal y As InterfaceExample(Of R))  
    End Sub  
  
End Module  
  
Interface InterfaceExample(Of T)  
End Interface  
```  
  
 <span data-ttu-id="859b3-110">**Identyfikator błędu:** BC36647 i BC36644</span><span class="sxs-lookup"><span data-stu-id="859b3-110">**Error ID:** BC36647 and BC36644</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="859b3-111">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="859b3-111">To correct this error</span></span>  
  
-   <span data-ttu-id="859b3-112">Można określić typ dla parametru typu lub parametrów zamiast polegania na wnioskowanie o typie danych.</span><span class="sxs-lookup"><span data-stu-id="859b3-112">You may be able to specify a data type for the type parameter or parameters instead of relying on type inference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="859b3-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="859b3-113">See Also</span></span>  
 [<span data-ttu-id="859b3-114">Swobodna konwersja delegatów</span><span class="sxs-lookup"><span data-stu-id="859b3-114">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)  
 [<span data-ttu-id="859b3-115">Procedury ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="859b3-115">Generic Procedures in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)  
 [<span data-ttu-id="859b3-116">Konwersje typów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="859b3-116">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
