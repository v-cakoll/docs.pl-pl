---
title: 'Porady: zapytanie zestawu&#39;s metadanych z odbiciem (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 53caa336-ab83-4181-b0f6-5c87c5f9e4ee
ms.openlocfilehash: f465cccef2009bb9d8da1dc57c14eb09dc008f54
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-query-an-assembly39s-metadata-with-reflection-linq-visual-basic"></a>Porady: zapytanie zestawu&#39;s metadanych z odbiciem (LINQ) (Visual Basic)
W poniższym przykładzie przedstawiono sposób LINQ może służyć za pomocą odbicia do pobierania metadanych określonych o metodach, spełniających określone kryteria wyszukiwania. W takim przypadku zapytanie znajdzie nazwy wszystkie metody w zestawie, która zwraca typów wyliczenia, takich jak tablic.  
  
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
  
 W przykładzie użyto <xref:System.Reflection.Assembly.GetTypes%2A> metoda zwraca tablicę typów w określonym zestawie. [Klauzuli Where](../../../../visual-basic/language-reference/queries/where-clause.md) jest stosowany filtr, tak aby zwracane są tylko typy publiczne. Dla każdego typu publicznego podzapytania jest generowany przy użyciu <xref:System.Reflection.MethodInfo> tablica, która jest zwracana z <xref:System.Type.GetMethods%2A> wywołania. Te wyniki są filtrowane do zwrócenia tylko tych metod, w których typem zwracanym jest tablicą, możesz też typu, który implementuje <xref:System.Collections.Generic.IEnumerable%601>. Ponadto te wyniki są pogrupowane według przy użyciu nazwy typu jako klucza.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Tworzenie projektu przeznaczonego dla programu .NET Framework w wersji 3.5 lub nowszego z odwołania do System.Core.dll i `Imports` instrukcji System.Linq przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ do obiektów (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
