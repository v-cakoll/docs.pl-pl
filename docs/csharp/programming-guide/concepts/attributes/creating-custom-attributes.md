---
title: Tworzenie atrybutów niestandardowych (C#)
ms.date: 07/20/2015
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
ms.openlocfilehash: c0f25adf0d562b659edaa8f36e72332fd0c1ee7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69595406"
---
# <a name="creating-custom-attributes-c"></a>Tworzenie atrybutów niestandardowych (C#)
Można utworzyć własne atrybuty niestandardowe, definiując klasę atrybutów, klasę, <xref:System.Attribute>która wywodzi się bezpośrednio lub pośrednio z , co sprawia, że identyfikowanie definicji atrybutów w metadanych jest szybkie i łatwe. Załóżmy, że chcesz oznaczyć typy z nazwą programisty, który napisał typ. Można zdefiniować klasę `Author` atrybutu niestandardowego:  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct)  
]  
public class Author : System.Attribute  
{  
    private string name;  
    public double version;  
  
    public Author(string name)  
    {  
        this.name = name;  
        version = 1.0;  
    }  
}  
```  
  
 Nazwa klasy jest nazwą atrybutu `Author`. Pochodzi z `System.Attribute`, więc jest to klasa atrybutów niestandardowych. Parametry konstruktora są parametrami pozycyjnymi atrybutu niestandardowego. W tym `name` przykładzie jest parametrem pozycyjnym. Wszystkie publiczne pola odczytu i zapisu są nazywane parametrami. W tym `version` przypadku jest jedynym nazwanym parametrem. Należy zwrócić uwagę `AttributeUsage` na użycie `Author` atrybutu, aby `struct` atrybut był prawidłowy tylko w klasie i deklaracjach.  
  
 Możesz użyć tego nowego atrybutu w następujący sposób:  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 `AttributeUsage`ma nazwany parametr, `AllowMultiple`, z którym można dokonać atrybutu niestandardowego jednorazowego użytku lub wielokrotnego użytku. W poniższym przykładzie kodu tworzony jest atrybut wielokrotnego użytku.  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // multiuse attribute  
]  
public class Author : System.Attribute  
```  
  
 W poniższym przykładzie kodu wiele atrybutów tego samego typu są stosowane do klasy.  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
[Author("R. Koch", version = 1.2)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
    // R. Koch's code goes here...  
}  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Reflection>
- [Przewodnik programowania języka C#](../../index.md)
- [Wpisywanie atrybutów niestandardowych](../../../../standard/attributes/writing-custom-attributes.md)
- [Odbicie (C#)](../reflection.md)
- [Atrybuty (C#)](./index.md)
- [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)](./accessing-attributes-by-using-reflection.md)
- [Użycie atrybutu (C#)](./attributeusage.md)
