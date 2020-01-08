---
title: Jak wykonać zapytanie dotyczące metadanych zestawu z odbiciem (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: c4cdce49-b1c8-4420-b12a-9ff7e6671368
ms.openlocfilehash: 65f27ae17d77553bfd7a78c1310febd337a55a6e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345688"
---
# <a name="how-to-query-an-assemblys-metadata-with-reflection-linq-c"></a>Jak wykonać zapytanie dotyczące metadanych zestawu z odbiciem (LINQ) (C#)

Interfejsy API odbicia w bibliotece klas .NET Framework mogą służyć do badania metadanych w zestawie .NET i tworzenia kolekcji typów, elementów członkowskich, parametrów i tak dalej, które znajdują się w tym zestawie. Ponieważ te kolekcje obsługują ogólny interfejs <xref:System.Collections.Generic.IEnumerable%601>, można je zbadać przy użyciu LINQ.  
  
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

W przykładzie zastosowano metodę <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType>, aby zwrócić tablicę typów w określonym zestawie. Filtr [WHERE](../../../language-reference/keywords/where-clause.md) jest stosowany, aby zwracane były tylko typy publiczne. Dla każdego typu publicznego podzapytanie jest generowane przy użyciu tablicy <xref:System.Reflection.MethodInfo>, która jest zwracana z wywołania <xref:System.Type.GetMethods%2A?displayProperty=nameWithType>. Te wyniki są filtrowane tak, aby zwracały tylko te metody, których typem zwracanym jest tablica lub inny typ, który implementuje <xref:System.Collections.Generic.IEnumerable%601>. Na koniec te wyniki są pogrupowane przy użyciu nazwy typu jako klucza.  
  
## <a name="see-also"></a>Zobacz także

- [LINQ to Objects (C#)](./linq-to-objects.md)
