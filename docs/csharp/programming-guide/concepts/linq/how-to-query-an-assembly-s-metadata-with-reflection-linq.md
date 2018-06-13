---
title: 'Porady: zapytanie zestawu&#39;s metadanych z odbiciem (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: c4cdce49-b1c8-4420-b12a-9ff7e6671368
ms.openlocfilehash: ada4fdb8ea0a552b9b6a27d7f0dfd9da447e612e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33319501"
---
# <a name="how-to-query-an-assembly39s-metadata-with-reflection-linq-c"></a>Porady: zapytanie zestawu&#39;s metadanych z odbiciem (LINQ) (C#)
W poniższym przykładzie przedstawiono sposób LINQ może służyć za pomocą odbicia do pobierania metadanych określonych o metodach, spełniających określone kryteria wyszukiwania. W takim przypadku zapytanie znajdzie nazwy wszystkie metody w zestawie, która zwraca typów wyliczenia, takich jak tablic.  
  
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
  
 W przykładzie użyto <xref:System.Reflection.Assembly.GetTypes%2A> metoda zwraca tablicę typów w określonym zestawie. [Gdzie](../../../../csharp/language-reference/keywords/where-clause.md) jest stosowany filtr, tak aby zwracane są tylko typy publiczne. Dla każdego typu publicznego podzapytania jest generowany przy użyciu <xref:System.Reflection.MethodInfo> tablica, która jest zwracana z <xref:System.Type.GetMethods%2A> wywołania. Te wyniki są filtrowane do zwrócenia tylko tych metod, w których typem zwracanym jest tablicą, możesz też typu, który implementuje <xref:System.Collections.Generic.IEnumerable%601>. Ponadto te wyniki są pogrupowane według przy użyciu nazwy typu jako klucza.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Tworzenie projektu przeznaczonego dla programu .NET Framework w wersji 3.5 lub nowszego z odwołania do System.Core.dll i `using` dyrektywy dla przestrzeni nazw System.Linq i System.IO.  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ do obiektów (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
