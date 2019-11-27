---
title: 'Porady: zapytanie dotyczące metadanych zestawu z odbiciem (LINQ)'
ms.date: 07/20/2015
ms.assetid: 53caa336-ab83-4181-b0f6-5c87c5f9e4ee
ms.openlocfilehash: 5cc525c6e60efd7cf34f9894b2cbb9389fd0b6ae
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347733"
---
# <a name="how-to-query-an-assemblys-metadata-with-reflection-linq-visual-basic"></a>Instrukcje: wykonywanie zapytania dotyczącego metadanych zestawu przy użyciu odbicia (LINQ) (Visual Basic)
Poniższy przykład pokazuje, w jaki sposób LINQ może być używane z odbiciem w celu pobrania określonych metadanych dotyczących metod, które pasują do określonego kryterium wyszukiwania. W takim przypadku zapytanie znajdzie nazwy wszystkich metod w zestawie, które zwracają wyliczalne typy, takie jak tablice.  
  
## <a name="example"></a>Przykład  
  
```vb
Imports System.Linq
Imports System.Reflection  

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
        Console.WriteLine("Press any key to exit... ")  
        Console.ReadKey()  
    End Sub  
End Module  
```  
  
W przykładzie zastosowano metodę <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType>, aby zwrócić tablicę typów w określonym zestawie. Filtr [klauzuli WHERE](../../../../visual-basic/language-reference/queries/where-clause.md) jest stosowany w taki sposób, że zwracane są tylko typy publiczne. Dla każdego typu publicznego podzapytanie jest generowane przy użyciu tablicy <xref:System.Reflection.MethodInfo>, która jest zwracana z wywołania <xref:System.Type.GetMethods%2A?displayProperty=nameWithType>. Te wyniki są filtrowane tak, aby zwracały tylko te metody, których typem zwracanym jest tablica lub inny typ, który implementuje <xref:System.Collections.Generic.IEnumerable%601>. Na koniec te wyniki są pogrupowane przy użyciu nazwy typu jako klucza.  
  
## <a name="see-also"></a>Zobacz także

- [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
