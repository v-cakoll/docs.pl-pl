---
title: Tworzenie atrybutów niestandardowych (C#)
description: Dowiedz się, jak tworzyć atrybuty niestandardowe w języku C# przez zdefiniowanie klasy atrybutu, która dziedziczy z klasy Attribute.
ms.date: 07/20/2015
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
ms.openlocfilehash: 7d6f98620388af8715652dcbcfe78366952b853d
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925088"
---
# <a name="creating-custom-attributes-c"></a>Tworzenie atrybutów niestandardowych (C#)
Można utworzyć własne atrybuty niestandardowe przez zdefiniowanie klasy atrybutów, klasy, która dziedziczy bezpośrednio lub pośrednio z <xref:System.Attribute> , co sprawia, że definicje atrybutów i są łatwe w użyciu w metadanych. Załóżmy, że chcesz oznakować typy nazwą programisty, który zapisał typ. Można zdefiniować `Author` klasę niestandardowego atrybutu:  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct)  
]  
public class AuthorAttribute : System.Attribute  
{  
    private string name;  
    public double version;  
  
    public AuthorAttribute(string name)  
    {  
        this.name = name;  
        version = 1.0;  
    }  
}  
```  
  
 Nazwa klasy `AuthorAttribute` to nazwa atrybutu, `Author` a także `Attribute` sufiks. Jest ona pochodną `System.Attribute` , więc jest klasą atrybutów niestandardowych. Parametry konstruktora są parametrami pozycyjnymi atrybutu niestandardowego. W tym przykładzie `name` jest parametrem pozycyjnym. Wszystkie publiczne pola do odczytu i zapisu są nazwanymi parametrami. W tym przypadku `version` jest jedynym nazwanym parametrem. Zwróć uwagę na użycie `AttributeUsage` atrybutu, aby atrybut był `Author` prawidłowy tylko dla klasy i `struct` deklaracji.  
  
 Tego nowego atrybutu można użyć w następujący sposób:  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 `AttributeUsage`ma nazwany parametr, `AllowMultiple` za pomocą którego można wykonać pojedyncze użycie lub Multiuse atrybutu niestandardowego. W poniższym przykładzie kodu tworzony jest atrybut Multiuse.  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // multiuse attribute  
]  
public class AuthorAttribute : System.Attribute  
```  
  
 W poniższym przykładzie kodu do klasy są stosowane wiele atrybutów tego samego typu.  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
[Author("R. Koch", version = 1.2)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
    // R. Koch's code goes here...  
}  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Reflection>
- [Przewodnik programowania w języku C#](../../index.md)
- [Wpisywanie atrybutów niestandardowych](../../../../standard/attributes/writing-custom-attributes.md)
- [Odbicie (C#)](../reflection.md)
- [Atrybuty (C#)](./index.md)
- [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)](./accessing-attributes-by-using-reflection.md)
- [AttributeUsage (C#)](../../../language-reference/attributes/general.md)
