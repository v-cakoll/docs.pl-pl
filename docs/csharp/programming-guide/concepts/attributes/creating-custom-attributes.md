---
title: Tworzenie atrybutów niestandardowych (C#)
ms.date: 07/20/2015
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
ms.openlocfilehash: ec959723c339a13a40fd62388421ceacb736dfca
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389557"
---
# <a name="creating-custom-attributes-c"></a>Tworzenie atrybutów niestandardowych (C#)
Można utworzyć własne atrybuty niestandardowe, definiując klasę atrybutu, klasę, <xref:System.Attribute>która wywodzi się bezpośrednio lub pośrednio z , co sprawia, że identyfikowanie definicji atrybutów w metadanych jest szybkie i łatwe. Załóżmy, że chcesz oznaczyć typy z nazwą programisty, który napisał typ. Można zdefiniować `Author` klasę atrybutów niestandardowych:  
  
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
  
 Nazwa klasy jest nazwą atrybutu `Author`, . Jest pochodną `System.Attribute`, więc jest to klasa atrybutu niestandardowego. Parametry konstruktora są parametry pozycyjne atrybutu niestandardowego. W tym `name` przykładzie jest parametrem pozycyjnym. Wszystkie publiczne pola odczytu i zapisu lub właściwości są nazywane parametrami. W takim `version` przypadku jest jedynym nazwanym parametrem. Zanotuj `AttributeUsage` użycie atrybutu, `Author` aby atrybut był `struct` prawidłowy tylko dla klasy i deklaracji.  
  
 Możesz użyć tego nowego atrybutu w następujący sposób:  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 `AttributeUsage`ma nazwany parametr, `AllowMultiple`za pomocą którego można wykonać atrybut niestandardowy jednorazowego użytku lub wielokrotnego użytku. W poniższym przykładzie kodu tworzony jest atrybut wielofunkcyjny.  
  
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
- [C# Przewodnik programowania](../../index.md)
- [Wpisywanie atrybutów niestandardowych](../../../../standard/attributes/writing-custom-attributes.md)
- [Odbicie (C#)](../reflection.md)
- [Atrybuty (C#)](./index.md)
- [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)](./accessing-attributes-by-using-reflection.md)
- [AttributeUsage (C#)](../../../language-reference/attributes/general.md)
