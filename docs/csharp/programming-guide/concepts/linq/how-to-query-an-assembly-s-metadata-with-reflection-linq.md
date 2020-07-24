---
title: Jak wykonać zapytanie dotyczące metadanych zestawu z odbiciem (LINQ) (C#)
description: Dowiedz się, jak używać LINQ z interfejsami API odbicia .NET w języku C#, aby pobierać określone metadane dotyczące metod, które pasują do kryterium wyszukiwania.
ms.date: 07/20/2015
ms.assetid: c4cdce49-b1c8-4420-b12a-9ff7e6671368
ms.openlocfilehash: dc5352e9cb90e9ad2808fb027823174d07d69da6
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104594"
---
# <a name="how-to-query-an-assemblys-metadata-with-reflection-linq-c"></a>Jak wykonać zapytanie dotyczące metadanych zestawu z odbiciem (LINQ) (C#)

Interfejsy API odbicia .NET mogą służyć do badania metadanych w zestawie .NET i tworzenia kolekcji typów, elementów członkowskich, parametrów i tak dalej, które znajdują się w tym zestawie. Ponieważ te kolekcje obsługują interfejs ogólny <xref:System.Collections.Generic.IEnumerable%601> , można je zbadać przy użyciu LINQ.  
  
Poniższy przykład pokazuje, w jaki sposób LINQ może być używane z odbiciem w celu pobrania określonych metadanych dotyczących metod, które pasują do określonego kryterium wyszukiwania. W takim przypadku zapytanie znajdzie nazwy wszystkich metod w zestawie, które zwracają wyliczalne typy, takie jak tablice.  
  
## <a name="example"></a>Przykład  
  
```csharp  
using System;
using System.Linq;
using System.Reflection;  

class ReflectionHowTO  
{  
    static void Main()  
    {  
        Assembly assembly = Assembly.Load("System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken= b77a5c561934e089");  
        var pubTypesQuery = from type in assembly.GetTypes()  
                    where type.IsPublic  
                        from method in type.GetMethods()  
                        where method.ReturnType.IsArray == true
                            || ( method.ReturnType.GetInterface(  
                                typeof(System.Collections.Generic.IEnumerable<>).FullName ) != null  
                            && method.ReturnType.FullName != "System.String" )  
                        group method.ToString() by type.ToString();  

        foreach (var groupOfMethods in pubTypesQuery)  
        {  
            Console.WriteLine("Type: {0}", groupOfMethods.Key);  
            foreach (var method in groupOfMethods)  
            {  
                Console.WriteLine("  {0}", method);  
            }  
        }  

        Console.WriteLine("Press any key to exit... ");  
        Console.ReadKey();  
    }  
}
```  

W przykładzie zastosowano <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> metodę, aby zwrócić tablicę typów w określonym zestawie. Filtr [WHERE](../../../language-reference/keywords/where-clause.md) jest stosowany, aby zwracane były tylko typy publiczne. Dla każdego typu publicznego podzapytanie jest generowane przy użyciu <xref:System.Reflection.MethodInfo> tablicy zwracanej z <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> wywołania. Te wyniki są filtrowane tak, aby zwracały tylko te metody, których typem zwracanym jest tablica lub inny typ, który implementuje <xref:System.Collections.Generic.IEnumerable%601> . Na koniec te wyniki są pogrupowane przy użyciu nazwy typu jako klucza.  
  
## <a name="see-also"></a>Zobacz też

- [LINQ to Objects (C#)](./linq-to-objects.md)
