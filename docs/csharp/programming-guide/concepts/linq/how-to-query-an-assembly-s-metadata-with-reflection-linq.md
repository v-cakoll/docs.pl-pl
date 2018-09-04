---
title: 'Porady: zapytanie zestawu&#39;s metadanych z odbiciem (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: c4cdce49-b1c8-4420-b12a-9ff7e6671368
ms.openlocfilehash: dece3cd6dbac2d10a3467892ef8aed80443cb2ef
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43516457"
---
# <a name="how-to-query-an-assembly39s-metadata-with-reflection-linq-c"></a>Porady: zapytanie zestawu&#39;s metadanych z odbiciem (LINQ) (C#)
Poniższy przykład pokazuje, jak LINQ może służyć za pomocą odbicia do pobierania metadanych określone informacje o metodach, spełniających określone kryteria wyszukiwania. W tym przypadku zapytanie znajdzie nazwy wszystkie metody w zestawie, który zwraca wyliczalny typów, takich jak tablice.  
  
## <a name="example"></a>Przykład  
  
```csharp  
using System.Reflection;  
using System.IO;  
namespace LINQReflection  
{  
    class ReflectionHowTO  
    {  
        static void Main(string[] args)  
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
  
            Console.WriteLine("Press any key to exit");  
            Console.ReadKey();  
        }  
    }    
}  
```  
  
 W przykładzie użyto <xref:System.Reflection.Assembly.GetTypes%2A> metodę, aby zwracało tablicę typów w określonym zestawie. [Gdzie](../../../../csharp/language-reference/keywords/where-clause.md) filtr jest stosowany, dzięki czemu zwracane są tylko typy publiczne. Dla każdego typu publicznego podzapytania jest generowany przy użyciu <xref:System.Reflection.MethodInfo> tablica, która jest zwracana z <xref:System.Type.GetMethods%2A> wywołania. Te wyniki są filtrowane, aby zwrócić tylko tych metod, którego typem zwracanym jest tablicą lub — w przeciwnym razie typ, który implementuje <xref:System.Collections.Generic.IEnumerable%601>. Na koniec te wyniki są grupowane, używając nazwy typu jako klucz.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Utwórz projekt, który jest przeznaczony dla .NET Framework w wersji 3.5 lub nowszego z odwołania do System.Core.dll i `using` dyrektywy dla przestrzeni nazw System.Linq i System.IO.  
  
## <a name="see-also"></a>Zobacz też

- [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
