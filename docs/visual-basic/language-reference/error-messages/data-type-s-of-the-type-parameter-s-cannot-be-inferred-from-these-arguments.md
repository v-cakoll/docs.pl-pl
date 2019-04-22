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
ms.openlocfilehash: 91ee4bf9242df822890b0a171061f375a3b24cbc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58828007"
---
# <a name="data-types-of-the-type-parameters-cannot-be-inferred-from-these-arguments"></a><span data-ttu-id="70c53-102">Na podstawie tych argumentów nie można wywnioskować typów danych parametrów typu</span><span class="sxs-lookup"><span data-stu-id="70c53-102">Data type(s) of the type parameter(s) cannot be inferred from these arguments</span></span>
<span data-ttu-id="70c53-103">Nie można wywnioskować typów danych parametrów typu na podstawie tych argumentów.</span><span class="sxs-lookup"><span data-stu-id="70c53-103">Data type(s) of the type parameter(s) cannot be inferred from these arguments.</span></span> <span data-ttu-id="70c53-104">Określanie danych typów jawnie może rozwiązać ten problem.</span><span class="sxs-lookup"><span data-stu-id="70c53-104">Specifying the data type(s) explicitly might correct this error.</span></span>  
  
 <span data-ttu-id="70c53-105">Ten błąd występuje, gdy Rozpoznanie przeciążenia nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="70c53-105">This error occurs when overload resolution has failed.</span></span> <span data-ttu-id="70c53-106">Jest wykonywane jako podrzędnego komunikat informujący o tym, dlaczego został wyeliminowany kandydat określonego przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="70c53-106">It occurs as a subordinate message that states why a particular overload candidate has been eliminated.</span></span> <span data-ttu-id="70c53-107">Komunikat o błędzie wyjaśniono, że kompilator nie mogą używać wnioskowania o typie można znaleźć typów danych parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="70c53-107">The error message explains that the compiler cannot use type inference to find data types for the type parameters.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="70c53-108">Gdy określenie argumentów nie jest opcją (na przykład dla operatorów zapytań w wyrażeniach zapytań), bez drugie zdanie pojawi się komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="70c53-108">When specifying arguments is not an option (for example, for query operators in query expressions), the error message appears without the second sentence.</span></span>  
  
 <span data-ttu-id="70c53-109">Poniższy przykład demonstruje ten błąd.</span><span class="sxs-lookup"><span data-stu-id="70c53-109">The following code demonstrates the error.</span></span>  
  
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
  
 <span data-ttu-id="70c53-110">**Identyfikator błędu:** BC36647 i BC36644</span><span class="sxs-lookup"><span data-stu-id="70c53-110">**Error ID:** BC36647 and BC36644</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="70c53-111">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="70c53-111">To correct this error</span></span>  
  
-   <span data-ttu-id="70c53-112">Można określić typu danych dla parametru typu lub parametrów zamiast polegania na wnioskowanie o typie.</span><span class="sxs-lookup"><span data-stu-id="70c53-112">You may be able to specify a data type for the type parameter or parameters instead of relying on type inference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70c53-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="70c53-113">See also</span></span>

- [<span data-ttu-id="70c53-114">Swobodna konwersja delegatów</span><span class="sxs-lookup"><span data-stu-id="70c53-114">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [<span data-ttu-id="70c53-115">Procedury ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="70c53-115">Generic Procedures in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)
- [<span data-ttu-id="70c53-116">Konwersje typów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="70c53-116">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
