---
title: Jak wysyłać zapytania do metadanych zestawu za pomocą odbicia (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: c4cdce49-b1c8-4420-b12a-9ff7e6671368
ms.openlocfilehash: 6e68cfea2bf3e03aed9de3e4a18cf9941ece34e3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168924"
---
# <a name="how-to-query-an-assemblys-metadata-with-reflection-linq-c"></a>Jak wysyłać zapytania do metadanych zestawu za pomocą odbicia (LINQ) (C#)

Interfejsów API odbicia biblioteki klas .NET Framework może służyć do badania metadanych w zestawie .NET i tworzenia kolekcji typów, elementów członkowskich typu, parametrów i tak dalej, które znajdują się w tym zestawie. Ponieważ te kolekcje <xref:System.Collections.Generic.IEnumerable%601> obsługują ogólny interfejs, można ich zbadać za pomocą LINQ.  
  
W poniższym przykładzie pokazano, jak LINQ może służyć z odbiciem do pobierania określonych metadanych dotyczących metod, które pasują do określonego kryterium wyszukiwania. W takim przypadku kwerenda znajdzie nazwy wszystkich metod w zestawie, które zwracają wyliczalne typy, takie jak tablice.  
  
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

W przykładzie <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> użyto metody do zwrócenia tablicy typów w określonym zestawie. Where [where](../../../language-reference/keywords/where-clause.md) filtr jest stosowany tak, że zwracane są tylko typy publiczne. Dla każdego typu publicznego podkwerenda jest <xref:System.Reflection.MethodInfo> generowana przy użyciu <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> tablicy, która jest zwracana z wywołania. Wyniki te są filtrowane, aby zwrócić tylko te metody, których zwracany typ jest tablicą lub typem, który implementuje <xref:System.Collections.Generic.IEnumerable%601>. Na koniec te wyniki są grupowane przy użyciu nazwy typu jako klucza.  
  
## <a name="see-also"></a>Zobacz też

- [LINQ do obiektów (C#)](./linq-to-objects.md)
