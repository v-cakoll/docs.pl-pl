---
title: 'Instrukcje: Zapytanie dotyczące metadanych zestawu z odbiciem (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 53caa336-ab83-4181-b0f6-5c87c5f9e4ee
ms.openlocfilehash: 7966b85172af48c7762027877a03b12dd6e2b62d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55255162"
---
# <a name="how-to-query-an-assemblys-metadata-with-reflection-linq-visual-basic"></a>Instrukcje: Zapytanie dotyczące metadanych zestawu z odbiciem (LINQ) (Visual Basic)
Poniższy przykład pokazuje, jak LINQ może służyć za pomocą odbicia do pobierania metadanych określone informacje o metodach, spełniających określone kryteria wyszukiwania. W tym przypadku zapytanie znajdzie nazwy wszystkie metody w zestawie, który zwraca wyliczalny typów, takich jak tablice.  
  
## <a name="example"></a>Przykład  
  
```vb  
Imports System.Reflection  
Imports System.IO  
Imports System.Linq  
Module Module1  
  
    Sub Main()  
        Dim asmbly As Assembly =   
            Assembly.Load("System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken= b77a5c561934e089")  
  
        Dim pubTypesQuery = From type In asmbly.GetTypes()   
                            Where type.IsPublic   
                            From method In type.GetMethods()   
                            Where method.ReturnType.IsArray = True   
                            Let name = method.ToString()   
                            Let typeName = type.ToString()   
                            Group name By typeName Into methodNames = Group  
  
        Console.WriteLine("Getting ready to iterate")  
        For Each item In pubTypesQuery  
            Console.WriteLine(item.methodNames)  
  
            For Each type In item.methodNames  
                Console.WriteLine(" " & type)  
            Next  
        Next  
        Console.ReadKey()  
    End Sub  
  
End Module  
```  
  
 W przykładzie użyto <xref:System.Reflection.Assembly.GetTypes%2A> metodę, aby zwracało tablicę typów w określonym zestawie. [Klauzuli Where](../../../../visual-basic/language-reference/queries/where-clause.md) filtr jest stosowany, dzięki czemu zwracane są tylko typy publiczne. Dla każdego typu publicznego podzapytania jest generowany przy użyciu <xref:System.Reflection.MethodInfo> tablica, która jest zwracana z <xref:System.Type.GetMethods%2A> wywołania. Te wyniki są filtrowane, aby zwrócić tylko tych metod, którego typem zwracanym jest tablicą lub — w przeciwnym razie typ, który implementuje <xref:System.Collections.Generic.IEnumerable%601>. Na koniec te wyniki są grupowane, używając nazwy typu jako klucz.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Utwórz projekt, który jest przeznaczony dla .NET Framework w wersji 3.5 lub nowszego z odwołania do System.Core.dll i `Imports` instrukcji dla przestrzeni nazw System.Linq.  
  
## <a name="see-also"></a>Zobacz także
- [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
