---
title: Ustalanie przeciążenia późnego wiązania nie może zostać zastosowane w elemencie „<procedurename>”, ponieważ wystąpienie uzyskujące dostęp jest typem interfejsu
ms.date: 07/20/2015
f1_keywords:
- vbc30933
- bc30933
helpviewer_keywords:
- overload resolution [Visual Basic], with late-bound argument
- BC30933
ms.assetid: 8182eea0-dd34-4d6e-9ca0-41d8713e9dc4
ms.openlocfilehash: 4500a177c7a4729fe5131af1b007fd38e77afe07
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397340"
---
# <a name="latebound-overload-resolution-cannot-be-applied-to-procedurename-because-the-accessing-instance-is-an-interface-type"></a><span data-ttu-id="a8598-102">Ustalanie przeciążenia późnego wiązania nie może zostać zastosowane w elemencie „\<procedurename>”, ponieważ wystąpienie uzyskujące dostęp jest typem interfejsu</span><span class="sxs-lookup"><span data-stu-id="a8598-102">Latebound overload resolution cannot be applied to '\<procedurename>' because the accessing instance is an interface type</span></span>

<span data-ttu-id="a8598-103">Kompilator próbuje rozpoznać odwołania do przeciążonej właściwości lub procedury, ale odwołanie nie powiedzie się, ponieważ argument jest typu, `Object` a odwołujący obiekt ma typ danych interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a8598-103">The compiler is attempting to resolve a reference to an overloaded property or procedure, but the reference fails because an argument is of type `Object` and the referring object has the data type of an interface.</span></span> <span data-ttu-id="a8598-104">`Object`Argument wymusza, aby kompilator rozpoznał odwołanie jako późne powiązanie.</span><span class="sxs-lookup"><span data-stu-id="a8598-104">The `Object` argument forces the compiler to resolve the reference as late-bound.</span></span>

<span data-ttu-id="a8598-105">W tych okolicznościach kompilator rozpoznaje Przeciążenie za pomocą klasy implementującej, a nie za pomocą interfejsu bazowego.</span><span class="sxs-lookup"><span data-stu-id="a8598-105">In these circumstances, the compiler resolves the overload through the implementing class instead of through the underlying interface.</span></span> <span data-ttu-id="a8598-106">Jeśli Klasa zmienia nazwę jednej ze przeciążonych wersji, kompilator nie traktuje tej wersji jako przeciążenia, ponieważ jej nazwa jest inna.</span><span class="sxs-lookup"><span data-stu-id="a8598-106">If the class renames one of the overloaded versions, the compiler does not consider that version to be an overload because its name is different.</span></span> <span data-ttu-id="a8598-107">To z kolei powoduje, że kompilator ignoruje wersję o zmienionej nazwie, gdy mogło być to poprawny wybór w celu rozpoznania odwołania.</span><span class="sxs-lookup"><span data-stu-id="a8598-107">This in turn causes the compiler to ignore the renamed version when it might have been the correct choice to resolve the reference.</span></span>

<span data-ttu-id="a8598-108">**Identyfikator błędu:** BC30933</span><span class="sxs-lookup"><span data-stu-id="a8598-108">**Error ID:** BC30933</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="a8598-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="a8598-109">To correct this error</span></span>

- <span data-ttu-id="a8598-110">Służy `CType` do rzutowania argumentu z `Object` na typ określony przez sygnaturę przeciążenia, które chcesz wywołać.</span><span class="sxs-lookup"><span data-stu-id="a8598-110">Use `CType` to cast the argument from `Object` to the type specified by the signature of the overload you want to call.</span></span>

  <span data-ttu-id="a8598-111">Należy zauważyć, że nie jest on pomocny do rzutowania obiektu odwołującego na podstawowy interfejs.</span><span class="sxs-lookup"><span data-stu-id="a8598-111">Note that it does not help to cast the referring object to the underlying interface.</span></span> <span data-ttu-id="a8598-112">Należy rzutować argument, aby uniknąć tego błędu.</span><span class="sxs-lookup"><span data-stu-id="a8598-112">You must cast the argument to avoid this error.</span></span>

## <a name="example"></a><span data-ttu-id="a8598-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="a8598-113">Example</span></span>

<span data-ttu-id="a8598-114">W poniższym przykładzie pokazano wywołanie przeciążonej `Sub` procedury, która powoduje ten błąd w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="a8598-114">The following example shows a call to an overloaded `Sub` procedure that causes this error at compile time.</span></span>

```vb
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

<span data-ttu-id="a8598-115">W poprzednim przykładzie, jeśli kompilator zezwolił na `s1` zapisanie, rozdzielczość odbywa się za pomocą klasy, `c1` a nie interfejsu `i1` .</span><span class="sxs-lookup"><span data-stu-id="a8598-115">In the preceding example, if the compiler allowed the call to `s1` as written, the resolution would take place through the class `c1` instead of the interface `i1`.</span></span> <span data-ttu-id="a8598-116">Oznacza to, że kompilator nie będzie rozważany `s2` , ponieważ jego nazwa jest inna w, mimo że `c1` jest to poprawny wybór zdefiniowany przez `i1` .</span><span class="sxs-lookup"><span data-stu-id="a8598-116">This would mean that the compiler would not consider `s2` because its name is different in `c1`, even though it is the correct choice as defined by `i1`.</span></span>

<span data-ttu-id="a8598-117">Błąd można poprawić, zmieniając wywołanie jednego z następujących wierszy kodu:</span><span class="sxs-lookup"><span data-stu-id="a8598-117">You can correct the error by changing the call to either of the following lines of code:</span></span>

```vb
refer.s1(CType(o1, Integer))
refer.s1(CType(o1, Double))
```

<span data-ttu-id="a8598-118">Każdy z powyższych wierszy kodu jawnie rzutuje `Object` zmienną `o1` na jeden z typów parametrów zdefiniowanych dla przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="a8598-118">Each of the preceding lines of code explicitly casts the `Object` variable `o1` to one of the parameter types defined for the overloads.</span></span>

## <a name="see-also"></a><span data-ttu-id="a8598-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a8598-119">See also</span></span>

- [<span data-ttu-id="a8598-120">Przeciążanie procedury</span><span class="sxs-lookup"><span data-stu-id="a8598-120">Procedure Overloading</span></span>](../../programming-guide/language-features/procedures/procedure-overloading.md)
- [<span data-ttu-id="a8598-121">Rozpoznanie przeciążenia</span><span class="sxs-lookup"><span data-stu-id="a8598-121">Overload Resolution</span></span>](../../programming-guide/language-features/procedures/overload-resolution.md)
- [<span data-ttu-id="a8598-122">CType — Funkcja</span><span class="sxs-lookup"><span data-stu-id="a8598-122">CType Function</span></span>](../functions/ctype-function.md)
