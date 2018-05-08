---
title: AttributeUsage (C#)
ms.date: 07/20/2015
ms.assetid: 22c45568-9a6a-4c2f-8480-f38c1caa0a99
ms.openlocfilehash: f8add9de7f472703048f81ec7f34b601611c2e63
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="attributeusage-c"></a>AttributeUsage (C#)
Określa sposób użycia klasy atrybutu niestandardowego. `AttributeUsage` jest atrybut, który może odnosić się do definicji atrybutu niestandardowego do kontrolowania, jak można zastosować nowego atrybutu. Po zastosowaniu jawnie, domyślne ustawienia następującą postać:  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.All,  
                   AllowMultiple = false,  
                   Inherited = true)]  
class NewAttribute : System.Attribute { }  
```  
  
 W tym przykładzie `NewAttribute` klasa może być stosowane do dowolnej jednostki kodu atrybutu można, ale mogą być stosowane tylko raz do każdej jednostki. Zostało ono odziedziczone przez klas pochodnych po zastosowaniu do klasy podstawowej.  
  
 `AllowMultiple` i `Inherited` argumenty są opcjonalne, dlatego ten kod działa tak samo:  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.All)]  
class NewAttribute : System.Attribute { }  
```  
  
 Pierwszy `AttributeUsage` argument musi być jeden lub więcej elementów <xref:System.AttributeTargets> wyliczenia. Wiele typów docelowy może odnosić się wraz z operatora OR w następujący sposób:  
  
```csharp  
using System;  

[AttributeUsage(AttributeTargets.Property | AttributeTargets.Field)]  
class NewPropertyOrFieldAttribute : Attribute { }  
```  
  
 Jeśli `AllowMultiple` argument ma wartość `true`, następnie wynikowy atrybut można stosować więcej niż raz do jednej jednostki, takich jak to:  
  
```csharp  
using System;  

[AttributeUsage(AttributeTargets.Class, AllowMultiple = true)]  
class MultiUseAttr : Attribute { }  
  
[MultiUseAttr]  
[MultiUseAttr]  
class Class1 { }  
  
[MultiUseAttr, MultiUseAttr]  
class Class2 { }  
```  
  
 W takim przypadku `MultiUseAttr` może odnosić się wielokrotnie ponieważ `AllowMultiple` ma ustawioną wartość `true`. Obu formatów pokazano stosowania wiele atrybutów są prawidłowe.  
  
 Jeśli `Inherited` ma ustawioną wartość `false`, a następnie ten atrybut nie jest dziedziczone przez klasy, które są pochodnymi klasy, która ma atrybut. Na przykład:  
  
```csharp  
using System;  

[AttributeUsage(AttributeTargets.Class, Inherited = false)]  
class Attr1 : Attribute { }  
  
[Attr1]  
class BClass { }  
  
class DClass : BClass { }  
```  
  
 W takim przypadku `Attr1` nie ma zastosowania do `DClass` za pośrednictwem dziedziczenia.  
  
## <a name="remarks"></a>Uwagi  
 `AttributeUsage` Jest atrybutem jednorazowy — nie można zastosować w więcej niż raz do tej samej klasy. `AttributeUsage` alias jest <xref:System.AttributeUsageAttribute>.  
  
 Aby uzyskać więcej informacji, zobacz [podczas uzyskiwania dostępu do atrybutów przy użyciu odbicia (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje efekt `Inherited` i `AllowMultiple` argumenty `AttributeUsage` atrybut i jak mogą być wyliczane atrybuty niestandardowe zastosowane do klasy.  
  
```csharp  
using System;  

// Create some custom attributes:  
[AttributeUsage(System.AttributeTargets.Class, Inherited = false)]  
class A1 : System.Attribute { }  
  
[AttributeUsage(System.AttributeTargets.Class)]  
class A2 : System.Attribute { }  
  
[AttributeUsage(System.AttributeTargets.Class, AllowMultiple = true)]  
class A3 : System.Attribute { }  
  
// Apply custom attributes to classes:  
[A1, A2]  
class BaseClass { }  
  
[A3, A3]  
class DerivedClass : BaseClass { }  
  
public class TestAttributeUsage  
{  
    static void Main()  
    {  
        BaseClass b = new BaseClass();  
        DerivedClass d = new DerivedClass();  
  
        // Display custom attributes for each class.  
        Console.WriteLine("Attributes on Base Class:");  
        object[] attrs = b.GetType().GetCustomAttributes(true);  
        foreach (Attribute attr in attrs)  
        {  
            Console.WriteLine(attr);  
        }  
  
        Console.WriteLine("Attributes on Derived Class:");  
        attrs = d.GetType().GetCustomAttributes(true);  
        foreach (Attribute attr in attrs)  
        {  
            Console.WriteLine(attr);  
        }  
    }  
}  
```  
  
## <a name="sample-output"></a>Przykładowe dane wyjściowe  
  
```  
Attributes on Base Class:  
A1  
A2  
Attributes on Derived Class:  
A3  
A3  
A2  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Attribute>  
 <xref:System.Reflection>  
 [Przewodnik programowania w języku C#](../../../../csharp/programming-guide/index.md)  
 [Atrybuty](../../../../../docs/standard/attributes/index.md)  
 [Odbicie (C#)](../../../../csharp/programming-guide/concepts/reflection.md)  
 [Atrybuty](../../../../csharp/programming-guide/concepts/attributes/index.md)  
 [Tworzenie atrybutów niestandardowych (C#)](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)  
 [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
