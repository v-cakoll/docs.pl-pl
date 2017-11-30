---
title: Wariancje w interfejsach (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 4828a8f9-48c0-4128-9749-7fcd6bf19a06
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cc3fe009e89d5d8f6619b406c8c08f47620a881d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="variance-in-generic-interfaces-c"></a>Wariancje w interfejsach (C#)
.NET framework 4 wprowadzono obsługę wariancji w kilku interfejsach istniejących. Obsługa wariancję umożliwia niejawna konwersja klas implementujących tych interfejsów. Następujące interfejsy są teraz wariant:  
  
-   <xref:System.Collections.Generic.IEnumerable%601>(T jest kowariantny)  
  
-   <xref:System.Collections.Generic.IEnumerator%601>(T jest kowariantny)  
  
-   <xref:System.Linq.IQueryable%601>(T jest kowariantny)  
  
-   <xref:System.Linq.IGrouping%602>(`TKey` i `TElement` są kowariantnego)  
  
-   <xref:System.Collections.Generic.IComparer%601>(T jest kontrawariantny)  
  
-   <xref:System.Collections.Generic.IEqualityComparer%601>(T jest kontrawariantny)  
  
-   <xref:System.IComparable%601>(T jest kontrawariantny)  
  
 Kowariancja zezwala na metodę typem zwracanym bardziej pochodny niż określone przez parametr typu ogólnego interfejsu. Aby zilustrować funkcji KOWARIANCJA, należy wziąć pod uwagę następujące interfejsy ogólne: `IEnumerable<Object>` i `IEnumerable<String>`. `IEnumerable<String>` Interfejsu nie dziedziczy `IEnumerable<Object>` interfejsu. Jednak `String` typ dziedziczy `Object` typu, a w niektórych przypadkach można przypisać obiekty te interfejsy do siebie. Przedstawiono to w poniższym przykładzie kodu.  
  
```csharp  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 We wcześniejszych wersjach programu .NET Framework, ten kod powoduje błąd kompilacji w języku C# z `Option Strict On`. Teraz można używać `strings` zamiast `objects`, jak pokazano w poprzednim przykładzie, ponieważ <xref:System.Collections.Generic.IEnumerable%601> interfejsu jest kowariantny.  
  
 Kontrawariancja zezwala na metodę typy argumentu są mniej pochodnego od określonej przez parametr ogólny interfejsu. Aby zilustrować kontrawariancji, załóżmy, że utworzono `BaseComparer` klasy do porównania wystąpienia `BaseClass` klasy. `BaseComparer` Klasa implementuje `IEqualityComparer<BaseClass>` interfejsu. Ponieważ <xref:System.Collections.Generic.IEqualityComparer%601> interfejs jest już kontrawariantnego, możesz użyć `BaseComparer` do porównania wystąpienia klas, które dziedziczą `BaseClass` klasy. Przedstawiono to w poniższym przykładzie kodu.  
  
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
  
 Aby uzyskać więcej przykładów, zobacz [korzystanie z wariancji w interfejsach dla kolekcji (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).  
  
 Wariancje w interfejsach jest obsługiwana tylko dla typów odniesienia. Typy wartości nie obsługują wariancji. Na przykład `IEnumerable<int>` nie można niejawnie przekonwertować `IEnumerable<object>`, ponieważ liczb całkowitych są reprezentowane przez typ wartości.  
  
```csharp  
IEnumerable<int> integers = new List<int>();  
// The following statement generates a compiler errror,  
// because int is a value type.  
// IEnumerable<Object> objects = integers;  
```  
  
 Jest również pamiętać, że klas implementujących interfejsów typu variant są nadal niezmiennej. Na przykład chociaż <xref:System.Collections.Generic.List%601> implementuje interfejs kowariantnego <xref:System.Collections.Generic.IEnumerable%601>, nie można niejawnie przekonwertować `List<Object>` do `List<String>`. Jest to zilustrowane w poniższym przykładzie kodu.  
  
```csharp  
// The following line generates a compiler error  
// because classes are invariant.  
// List<Object> list = new List<String>();  
  
// You can use the interface object instead.  
IEnumerable<Object> listObjects = new List<String>();  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z wariancji w interfejsach dla kolekcji (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)  
 [Tworzenie interfejsów ogólnych typu Variant (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)  
 [Interfejsy ogólne](../../../../standard/generics/interfaces.md)  
 [Wariancje w Delegatach (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
