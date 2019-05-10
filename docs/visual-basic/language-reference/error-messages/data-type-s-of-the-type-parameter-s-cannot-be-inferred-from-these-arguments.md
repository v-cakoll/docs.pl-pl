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
ms.openlocfilehash: 4167905ca6ddab66b2cbc6c8c40dc7c984e94b8b
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2019
ms.locfileid: "64913192"
---
# <a name="data-types-of-the-type-parameters-cannot-be-inferred-from-these-arguments"></a><span data-ttu-id="c5c7f-102">Na podstawie tych argumentów nie można wywnioskować typów danych parametrów typu</span><span class="sxs-lookup"><span data-stu-id="c5c7f-102">Data type(s) of the type parameter(s) cannot be inferred from these arguments</span></span>
<span data-ttu-id="c5c7f-103">Nie można wywnioskować typów danych parametrów typu na podstawie tych argumentów.</span><span class="sxs-lookup"><span data-stu-id="c5c7f-103">Data type(s) of the type parameter(s) cannot be inferred from these arguments.</span></span> <span data-ttu-id="c5c7f-104">Określanie danych typów jawnie może rozwiązać ten problem.</span><span class="sxs-lookup"><span data-stu-id="c5c7f-104">Specifying the data type(s) explicitly might correct this error.</span></span>  
  
 <span data-ttu-id="c5c7f-105">Ten błąd występuje, gdy Rozpoznanie przeciążenia nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="c5c7f-105">This error occurs when overload resolution has failed.</span></span> <span data-ttu-id="c5c7f-106">Jest wykonywane jako podrzędnego komunikat informujący o tym, dlaczego został wyeliminowany kandydat określonego przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="c5c7f-106">It occurs as a subordinate message that states why a particular overload candidate has been eliminated.</span></span> <span data-ttu-id="c5c7f-107">Komunikat o błędzie wyjaśniono, że kompilator nie mogą używać wnioskowania o typie można znaleźć typów danych parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="c5c7f-107">The error message explains that the compiler cannot use type inference to find data types for the type parameters.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c5c7f-108">Gdy określenie argumentów nie jest opcją (na przykład dla operatorów zapytań w wyrażeniach zapytań), bez drugie zdanie pojawi się komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="c5c7f-108">When specifying arguments is not an option (for example, for query operators in query expressions), the error message appears without the second sentence.</span></span>  
  
 <span data-ttu-id="c5c7f-109">Poniższy przykład demonstruje ten błąd.</span><span class="sxs-lookup"><span data-stu-id="c5c7f-109">The following code demonstrates the error.</span></span>  
  
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
  
 <span data-ttu-id="c5c7f-110">**Identyfikator błędu:** BC36647 i BC36644</span><span class="sxs-lookup"><span data-stu-id="c5c7f-110">**Error ID:** BC36647 and BC36644</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c5c7f-111">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="c5c7f-111">To correct this error</span></span>  
  
- <span data-ttu-id="c5c7f-112">Można określić typu danych dla parametru typu lub parametrów zamiast polegania na wnioskowanie o typie.</span><span class="sxs-lookup"><span data-stu-id="c5c7f-112">You may be able to specify a data type for the type parameter or parameters instead of relying on type inference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5c7f-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c5c7f-113">See also</span></span>

- [<span data-ttu-id="c5c7f-114">Swobodna konwersja delegatów</span><span class="sxs-lookup"><span data-stu-id="c5c7f-114">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [<span data-ttu-id="c5c7f-115">Procedury ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c5c7f-115">Generic Procedures in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)
- [<span data-ttu-id="c5c7f-116">Konwersje typów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c5c7f-116">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
