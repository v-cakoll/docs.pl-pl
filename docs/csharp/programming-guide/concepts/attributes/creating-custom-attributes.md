---
title: Tworzenie atrybutów niestandardowych (C#)
ms.date: 07/20/2015
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
ms.openlocfilehash: 5a846771eb26e3760e3f47458b862356f4da1ae6
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43503709"
---
# <a name="creating-custom-attributes-c"></a>Tworzenie atrybutów niestandardowych (C#)
Można utworzyć własne niestandardowe atrybuty, definiując klasę atrybutów klasy, która pochodzi bezpośrednio lub pośrednio z <xref:System.Attribute>, co sprawia, że identyfikowanie definicji atrybutów w metadanych jest łatwe i szybkie. Załóżmy, że chcesz typy tag o nazwie programisty, który napisał typu. Można zdefiniować niestandardowy `Author` klasy atrybutu:  
  
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
  
 Nazwa klasy jest nazwą atrybutu `Author`. Jest pochodną `System.Attribute`, więc jest klasą atrybutu niestandardowego. Parametry Konstruktora są parametry pozycyjne atrybutu niestandardowego. W tym przykładzie `name` jest parametr pozycyjne. Właściwości lub pola publiczne odczytu / zapisu czy nazwanych parametrów. W tym przypadku `version` tylko nosi nazwę parametru. Zwróć uwagę na użycie `AttributeUsage` atrybutu, aby wprowadzić `Author` atrybut jest prawidłowy tylko w klasie i `struct` deklaracji.  
  
 Można użyć tego nowego atrybutu w następujący sposób:  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 `AttributeUsage` został nazwany parametr `AllowMultiple`, dzięki którym możesz ustawić atrybutu niestandardowego jednorazowych lub multiuse —. W poniższym przykładzie kodu multiuse — atrybut jest tworzony.  
  
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
  
> [!NOTE]
>  Jeśli atrybut klasy zawiera właściwości, ta właściwość musi być odczytu i zapisu.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Reflection>  
- [Przewodnik programowania w języku C#](../../../../csharp/programming-guide/index.md)  
- [Wpisywanie atrybutów niestandardowych](../../../../standard/attributes/writing-custom-attributes.md)  
- [Odbicie (C#)](../../../../csharp/programming-guide/concepts/reflection.md)  
- [Atrybuty (C#)](../../../../csharp/programming-guide/concepts/attributes/index.md)  
- [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
- [AttributeUsage (C#)](../../../../csharp/programming-guide/concepts/attributes/attributeusage.md)
