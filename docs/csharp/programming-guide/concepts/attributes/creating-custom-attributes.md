---
title: "Tworzenie atrybutów niestandardowych (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 38bdedb352cc79f7a4cc3d08eb6138e7d994514b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="creating-custom-attributes-c"></a>Tworzenie atrybutów niestandardowych (C#)
Można utworzyć własne niestandardowe atrybuty, definiując klasę atrybutów klasy, która jest pochodną bezpośrednio lub pośrednio <xref:System.Attribute>, która sprawia, że identyfikacji definicje atrybutów w metadanych szybkie i łatwe. Załóżmy, że chcesz typów tagu o nazwie programisty autorze typu. Możesz zdefiniować niestandardowy `Author` klasy atrybutu:  
  
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
  
 Nazwa klasy jest nazwa atrybutu `Author`. Jest pochodną `System.Attribute`, co klasa atrybutu niestandardowego. Konstruktor parametry są parametry pozycyjne atrybutu niestandardowego. W tym przykładzie `name` jest parametrów pozycyjnych. Parametry są nazwane właściwości lub pola publiczne odczytu i zapisu. W takim przypadku `version` tylko nosi nazwę parametru. Zwróć uwagę na użycie `AttributeUsage` atrybutu, aby `Author` atrybut jest prawidłowy tylko w klasie i `struct` deklaracji.  
  
 Ten nowy atrybut można użyć w następujący sposób:  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 `AttributeUsage`Nazwany parametr `AllowMultiple`, z której można utworzyć atrybutu niestandardowego, jednorazowych lub multiuse. W poniższym przykładzie jest tworzony multiuse atrybutu.  
  
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
>  Jeśli atrybut klasy zawiera właściwości, tej właściwości musi być do odczytu / zapisu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Reflection>  
 [Przewodnik programowania w języku C#](../../../../csharp/programming-guide/index.md)  
 [Wpisywanie atrybutów niestandardowych](../../../../standard/attributes/writing-custom-attributes.md)  
 [Odbicie (C#)](../../../../csharp/programming-guide/concepts/reflection.md)  
 [Atrybuty (C#)](../../../../csharp/programming-guide/concepts/attributes/index.md)  
 [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
 [AttributeUsage (C#)](../../../../csharp/programming-guide/concepts/attributes/attributeusage.md)
