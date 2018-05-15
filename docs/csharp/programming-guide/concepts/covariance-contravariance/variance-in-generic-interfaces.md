---
title: Wariancje w interfejsach (C#)
ms.date: 07/20/2015
ms.assetid: 4828a8f9-48c0-4128-9749-7fcd6bf19a06
ms.openlocfilehash: fdcfd13a645ffc9b596beed65b74f8e593c642f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="variance-in-generic-interfaces-c"></a><span data-ttu-id="d2124-102">Wariancje w interfejsach (C#)</span><span class="sxs-lookup"><span data-stu-id="d2124-102">Variance in Generic Interfaces (C#)</span></span>
<span data-ttu-id="d2124-103">.NET framework 4 wprowadzono obsługę wariancji w kilku interfejsach istniejących.</span><span class="sxs-lookup"><span data-stu-id="d2124-103">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="d2124-104">Obsługa wariancję umożliwia niejawna konwersja klas implementujących tych interfejsów.</span><span class="sxs-lookup"><span data-stu-id="d2124-104">Variance support enables implicit conversion of classes that implement these interfaces.</span></span> <span data-ttu-id="d2124-105">Następujące interfejsy są teraz wariant:</span><span class="sxs-lookup"><span data-stu-id="d2124-105">The following interfaces are now variant:</span></span>  
  
-   <span data-ttu-id="d2124-106"><xref:System.Collections.Generic.IEnumerable%601> (T jest kowariantny)</span><span class="sxs-lookup"><span data-stu-id="d2124-106"><xref:System.Collections.Generic.IEnumerable%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="d2124-107"><xref:System.Collections.Generic.IEnumerator%601> (T jest kowariantny)</span><span class="sxs-lookup"><span data-stu-id="d2124-107"><xref:System.Collections.Generic.IEnumerator%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="d2124-108"><xref:System.Linq.IQueryable%601> (T jest kowariantny)</span><span class="sxs-lookup"><span data-stu-id="d2124-108"><xref:System.Linq.IQueryable%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="d2124-109"><xref:System.Linq.IGrouping%602> (`TKey` i `TElement` są kowariantnego)</span><span class="sxs-lookup"><span data-stu-id="d2124-109"><xref:System.Linq.IGrouping%602> (`TKey` and `TElement` are covariant)</span></span>  
  
-   <span data-ttu-id="d2124-110"><xref:System.Collections.Generic.IComparer%601> (T jest kontrawariantny)</span><span class="sxs-lookup"><span data-stu-id="d2124-110"><xref:System.Collections.Generic.IComparer%601> (T is contravariant)</span></span>  
  
-   <span data-ttu-id="d2124-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T jest kontrawariantny)</span><span class="sxs-lookup"><span data-stu-id="d2124-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T is contravariant)</span></span>  
  
-   <span data-ttu-id="d2124-112"><xref:System.IComparable%601> (T jest kontrawariantny)</span><span class="sxs-lookup"><span data-stu-id="d2124-112"><xref:System.IComparable%601> (T is contravariant)</span></span>  
  
 <span data-ttu-id="d2124-113">Kowariancja zezwala na metodę typem zwracanym bardziej pochodny niż określone przez parametr typu ogólnego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="d2124-113">Covariance permits a method to have a more derived return type than that defined by the generic type parameter of the interface.</span></span> <span data-ttu-id="d2124-114">Aby zilustrować funkcji KOWARIANCJA, należy wziąć pod uwagę następujące interfejsy ogólne: `IEnumerable<Object>` i `IEnumerable<String>`.</span><span class="sxs-lookup"><span data-stu-id="d2124-114">To illustrate the covariance feature, consider these generic interfaces: `IEnumerable<Object>` and `IEnumerable<String>`.</span></span> <span data-ttu-id="d2124-115">`IEnumerable<String>` Interfejsu nie dziedziczy `IEnumerable<Object>` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="d2124-115">The `IEnumerable<String>` interface does not inherit the `IEnumerable<Object>` interface.</span></span> <span data-ttu-id="d2124-116">Jednak `String` typ dziedziczy `Object` typu, a w niektórych przypadkach można przypisać obiekty te interfejsy do siebie.</span><span class="sxs-lookup"><span data-stu-id="d2124-116">However, the `String` type does inherit the `Object` type, and in some cases you may want to assign objects of these interfaces to each other.</span></span> <span data-ttu-id="d2124-117">Przedstawiono to w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="d2124-117">This is shown in the following code example.</span></span>  
  
```csharp  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 <span data-ttu-id="d2124-118">We wcześniejszych wersjach programu .NET Framework, ten kod powoduje błąd kompilacji w języku C# z `Option Strict On`.</span><span class="sxs-lookup"><span data-stu-id="d2124-118">In earlier versions of the .NET Framework, this code causes a compilation error in C# with `Option Strict On`.</span></span> <span data-ttu-id="d2124-119">Teraz można używać `strings` zamiast `objects`, jak pokazano w poprzednim przykładzie, ponieważ <xref:System.Collections.Generic.IEnumerable%601> interfejsu jest kowariantny.</span><span class="sxs-lookup"><span data-stu-id="d2124-119">But now you can use `strings` instead of `objects`, as shown in the previous example, because the <xref:System.Collections.Generic.IEnumerable%601> interface is covariant.</span></span>  
  
 <span data-ttu-id="d2124-120">Kontrawariancja zezwala na metodę typy argumentu są mniej pochodnego od określonej przez parametr ogólny interfejsu.</span><span class="sxs-lookup"><span data-stu-id="d2124-120">Contravariance permits a method to have argument types that are less derived than that specified by the generic parameter of the interface.</span></span> <span data-ttu-id="d2124-121">Aby zilustrować kontrawariancji, załóżmy, że utworzono `BaseComparer` klasy do porównania wystąpienia `BaseClass` klasy.</span><span class="sxs-lookup"><span data-stu-id="d2124-121">To illustrate contravariance, assume that you have created a `BaseComparer` class to compare instances of the `BaseClass` class.</span></span> <span data-ttu-id="d2124-122">`BaseComparer` Klasa implementuje `IEqualityComparer<BaseClass>` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="d2124-122">The `BaseComparer` class implements the `IEqualityComparer<BaseClass>` interface.</span></span> <span data-ttu-id="d2124-123">Ponieważ <xref:System.Collections.Generic.IEqualityComparer%601> interfejs jest już kontrawariantnego, możesz użyć `BaseComparer` do porównania wystąpienia klas, które dziedziczą `BaseClass` klasy.</span><span class="sxs-lookup"><span data-stu-id="d2124-123">Because the <xref:System.Collections.Generic.IEqualityComparer%601> interface is now contravariant, you can use `BaseComparer` to compare instances of classes that inherit the `BaseClass` class.</span></span> <span data-ttu-id="d2124-124">Przedstawiono to w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="d2124-124">This is shown in the following code example.</span></span>  
  
```csharp  
// Simple hierarchy of classes.  
class BaseClass { }  
class DerivedClass : BaseClass { }  
  
// Comparer class.  
class BaseComparer : IEqualityComparer<BaseClass>   
{  
    public int GetHashCode(BaseClass baseInstance)  
    {  
        return baseInstance.GetHashCode();  
    }  
    public bool Equals(BaseClass x, BaseClass y)  
    {  
        return x == y;  
    }  
}  
class Program  
{  
    static void Test()  
    {  
        IEqualityComparer<BaseClass> baseComparer = new BaseComparer();  
  
        // Implicit conversion of IEqualityComparer<BaseClass> to   
        // IEqualityComparer<DerivedClass>.  
        IEqualityComparer<DerivedClass> childComparer = baseComparer;  
    }  
}  
```  
  
 <span data-ttu-id="d2124-125">Aby uzyskać więcej przykładów, zobacz [korzystanie z wariancji w interfejsach dla kolekcji (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).</span><span class="sxs-lookup"><span data-stu-id="d2124-125">For more examples, see [Using Variance in Interfaces for Generic Collections (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).</span></span>  
  
 <span data-ttu-id="d2124-126">Wariancje w interfejsach jest obsługiwana tylko dla typów odniesienia.</span><span class="sxs-lookup"><span data-stu-id="d2124-126">Variance in generic interfaces is supported for reference types only.</span></span> <span data-ttu-id="d2124-127">Typy wartości nie obsługują wariancji.</span><span class="sxs-lookup"><span data-stu-id="d2124-127">Value types do not support variance.</span></span> <span data-ttu-id="d2124-128">Na przykład `IEnumerable<int>` nie można niejawnie przekonwertować `IEnumerable<object>`, ponieważ liczb całkowitych są reprezentowane przez typ wartości.</span><span class="sxs-lookup"><span data-stu-id="d2124-128">For example, `IEnumerable<int>` cannot be implicitly converted to `IEnumerable<object>`, because integers are represented by a value type.</span></span>  
  
```csharp  
IEnumerable<int> integers = new List<int>();  
// The following statement generates a compiler errror,  
// because int is a value type.  
// IEnumerable<Object> objects = integers;  
```  
  
 <span data-ttu-id="d2124-129">Jest również pamiętać, że klas implementujących interfejsów typu variant są nadal niezmiennej.</span><span class="sxs-lookup"><span data-stu-id="d2124-129">It is also important to remember that classes that implement variant interfaces are still invariant.</span></span> <span data-ttu-id="d2124-130">Na przykład chociaż <xref:System.Collections.Generic.List%601> implementuje interfejs kowariantnego <xref:System.Collections.Generic.IEnumerable%601>, nie można niejawnie przekonwertować `List<Object>` do `List<String>`.</span><span class="sxs-lookup"><span data-stu-id="d2124-130">For example, although <xref:System.Collections.Generic.List%601> implements the covariant interface <xref:System.Collections.Generic.IEnumerable%601>, you cannot implicitly convert `List<Object>` to `List<String>`.</span></span> <span data-ttu-id="d2124-131">Jest to zilustrowane w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="d2124-131">This is illustrated in the following code example.</span></span>  
  
```csharp  
// The following line generates a compiler error  
// because classes are invariant.  
// List<Object> list = new List<String>();  
  
// You can use the interface object instead.  
IEnumerable<Object> listObjects = new List<String>();  
```  
  
## <a name="see-also"></a><span data-ttu-id="d2124-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d2124-132">See Also</span></span>  
 [<span data-ttu-id="d2124-133">Korzystanie z wariancji w interfejsach dla kolekcji (C#)</span><span class="sxs-lookup"><span data-stu-id="d2124-133">Using Variance in Interfaces for Generic Collections (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)  
 [<span data-ttu-id="d2124-134">Tworzenie interfejsów ogólnych typu Variant (C#)</span><span class="sxs-lookup"><span data-stu-id="d2124-134">Creating Variant Generic Interfaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)  
 [<span data-ttu-id="d2124-135">Interfejsy ogólne</span><span class="sxs-lookup"><span data-stu-id="d2124-135">Generic Interfaces</span></span>](../../../../standard/generics/interfaces.md)  
 [<span data-ttu-id="d2124-136">Wariancje w Delegatach (C#)</span><span class="sxs-lookup"><span data-stu-id="d2124-136">Variance in Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
