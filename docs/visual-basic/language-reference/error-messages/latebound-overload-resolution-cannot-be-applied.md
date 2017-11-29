---
title: "Ustalanie przeciążenia późnego nie można zastosować do &#39; &lt;nazwaprocedury&gt;&#39; ponieważ wystąpienie uzyskujące dostęp jest typem interfejsu"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30933
- bc30933
helpviewer_keywords:
- overload resolution [Visual Basic], with late-bound argument
- BC30933
ms.assetid: 8182eea0-dd34-4d6e-9ca0-41d8713e9dc4
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fb7f8a9f6eadfc9fd856ea57d362b43d25ff81a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="latebound-overload-resolution-cannot-be-applied-to-39ltprocedurenamegt39-because-the-accessing-instance-is-an-interface-type"></a><span data-ttu-id="4403b-102">Ustalanie przeciążenia późnego nie można zastosować do &#39; &lt;nazwaprocedury&gt;&#39; ponieważ wystąpienie uzyskujące dostęp jest typem interfejsu</span><span class="sxs-lookup"><span data-stu-id="4403b-102">Latebound overload resolution cannot be applied to &#39;&lt;procedurename&gt;&#39; because the accessing instance is an interface type</span></span>
<span data-ttu-id="4403b-103">Kompilator próbuje rozpoznać odwołania do przeciążonej właściwość lub procedura, ale odwołanie nie powiedzie się, ponieważ argument jest typu `Object` i odwołuje się do innych obiektów o typie danych interfejsu.</span><span class="sxs-lookup"><span data-stu-id="4403b-103">The compiler is attempting to resolve a reference to an overloaded property or procedure, but the reference fails because an argument is of type `Object` and the referring object has the data type of an interface.</span></span> <span data-ttu-id="4403b-104">`Object` Argument wymusza na rozpoznania odwołania jako późnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="4403b-104">The `Object` argument forces the compiler to resolve the reference as late-bound.</span></span>  
  
 <span data-ttu-id="4403b-105">W takiej sytuacji kompilator rozpoznaje przeciążenia za pośrednictwem klasy implementującej zamiast za pośrednictwem powiązanego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="4403b-105">In these circumstances, the compiler resolves the overload through the implementing class instead of through the underlying interface.</span></span> <span data-ttu-id="4403b-106">Jeśli klasa zmienia nazwę jednej z zastąpionej wersji, kompilator nie należy wziąć pod uwagę tej wersji na przeciążenia, ponieważ jego nazwa różni się.</span><span class="sxs-lookup"><span data-stu-id="4403b-106">If the class renames one of the overloaded versions, the compiler does not consider that version to be an overload because its name is different.</span></span> <span data-ttu-id="4403b-107">To z kolei powoduje, że kompilator ignorować zmienioną nazwę wersji, gdy było poprawne wybór rozpoznać odwołania do.</span><span class="sxs-lookup"><span data-stu-id="4403b-107">This in turn causes the compiler to ignore the renamed version when it might have been the correct choice to resolve the reference.</span></span>  
  
 <span data-ttu-id="4403b-108">**Identyfikator błędu:** BC30933</span><span class="sxs-lookup"><span data-stu-id="4403b-108">**Error ID:** BC30933</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4403b-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="4403b-109">To correct this error</span></span>  
  
-   <span data-ttu-id="4403b-110">Użyj `CType` można rzutować argumentu z `Object` na typ określony przez sygnaturę przeładowania ma zostać wywołana.</span><span class="sxs-lookup"><span data-stu-id="4403b-110">Use `CType` to cast the argument from `Object` to the type specified by the signature of the overload you want to call.</span></span>  
  
     <span data-ttu-id="4403b-111">Należy pamiętać, że nie jest pomocne można rzutować obiektu odwołujący się do powiązanego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="4403b-111">Note that it does not help to cast the referring object to the underlying interface.</span></span> <span data-ttu-id="4403b-112">Należy rzutować argumentu, aby uniknąć tego błędu.</span><span class="sxs-lookup"><span data-stu-id="4403b-112">You must cast the argument to avoid this error.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4403b-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="4403b-113">Example</span></span>  
 <span data-ttu-id="4403b-114">W poniższym przykładzie pokazano wywołanie przeciążonej `Sub` procedury, która powoduje, że ten błąd w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4403b-114">The following example shows a call to an overloaded `Sub` procedure that causes this error at compile time.</span></span>  
  
```  
Module m1  
    Interface i1  
        Sub s1(ByVal p1 As Integer)  
        Sub s1(ByVal p1 As Double)  
    End Interface  
    Class c1  
        Implements i1  
        Public Overloads Sub s1(ByVal p1 As Integer) Implements i1.s1  
        End Sub  
        Public Overloads Sub s2(ByVal p1 As Double) Implements i1.s1  
        End Sub  
    End Class  
    Sub Main()  
        Dim refer As i1 = New c1  
        Dim o1 As Object = 3.1415  
        ' The following reference is INVALID and causes a compiler error.  
        refer.s1(o1)   
    End Sub  
End Module  
```  
  
 <span data-ttu-id="4403b-115">W poprzednim przykładzie, jeśli kompilator może wywołać `s1` podczas zapisywania, rozdzielczość nastąpi za pośrednictwem klasy `c1` zamiast interfejsu `i1`.</span><span class="sxs-lookup"><span data-stu-id="4403b-115">In the preceding example, if the compiler allowed the call to `s1` as written, the resolution would take place through the class `c1` instead of the interface `i1`.</span></span> <span data-ttu-id="4403b-116">To oznacza, że kompilator może nie należy wziąć pod uwagę `s2` jego nazwa różni się w `c1`, nawet jeśli jest to poprawny wybór zgodnie z definicją w `i1`.</span><span class="sxs-lookup"><span data-stu-id="4403b-116">This would mean that the compiler would not consider `s2` because its name is different in `c1`, even though it is the correct choice as defined by `i1`.</span></span>  
  
 <span data-ttu-id="4403b-117">Zmieniając wywołania do jednej z następujących wierszy kodu można poprawić błąd:</span><span class="sxs-lookup"><span data-stu-id="4403b-117">You can correct the error by changing the call to either of the following lines of code:</span></span>  
  
```  
refer.s1(CType(o1, Integer))  
refer.s1(CType(o1, Double))  
```  
  
 <span data-ttu-id="4403b-118">Każdy z powyższych wierszy kodu jawnie rzutuje `Object` zmiennej `o1` do jednego z typów parametrów zdefiniowanych dla przeciążeń.</span><span class="sxs-lookup"><span data-stu-id="4403b-118">Each of the preceding lines of code explicitly casts the `Object` variable `o1` to one of the parameter types defined for the overloads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4403b-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4403b-119">See Also</span></span>  
 [<span data-ttu-id="4403b-120">Przeciążanie procedury</span><span class="sxs-lookup"><span data-stu-id="4403b-120">Procedure Overloading</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)  
 [<span data-ttu-id="4403b-121">Rozpoznanie przeciążenia</span><span class="sxs-lookup"><span data-stu-id="4403b-121">Overload Resolution</span></span>](../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)  
 [<span data-ttu-id="4403b-122">CType — funkcja</span><span class="sxs-lookup"><span data-stu-id="4403b-122">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)
