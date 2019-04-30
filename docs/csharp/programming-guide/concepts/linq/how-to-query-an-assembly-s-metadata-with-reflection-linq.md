---
title: 'Instrukcje: Zapytanie dotyczące metadanych zestawu z odbiciem (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: c4cdce49-b1c8-4420-b12a-9ff7e6671368
ms.openlocfilehash: 849244f1345966dbe198686f4f9024fc321b6ded
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667824"
---
# <a name="how-to-query-an-assemblys-metadata-with-reflection-linq-c"></a>Instrukcje: Zapytanie dotyczące metadanych zestawu z odbiciem (LINQ) (C#)
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
  
## <a name="see-also"></a>Zobacz także

- [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
