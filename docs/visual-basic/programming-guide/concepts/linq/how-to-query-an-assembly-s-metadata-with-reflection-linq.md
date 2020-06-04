---
title: 'Instrukcje: zapytanie dotyczące metadanych zestawu z odbiciem (LINQ)'
ms.date: 07/20/2015
ms.assetid: 53caa336-ab83-4181-b0f6-5c87c5f9e4ee
ms.openlocfilehash: a4f73bd2c8c01cbf92fac67991f01a1cb3dee932
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396457"
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
  
W przykładzie zastosowano <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> metodę, aby zwrócić tablicę typów w określonym zestawie. Filtr [klauzuli WHERE](../../../language-reference/queries/where-clause.md) jest stosowany w taki sposób, że zwracane są tylko typy publiczne. Dla każdego typu publicznego podzapytanie jest generowane przy użyciu <xref:System.Reflection.MethodInfo> tablicy zwracanej z <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> wywołania. Te wyniki są filtrowane tak, aby zwracały tylko te metody, których typem zwracanym jest tablica lub inny typ, który implementuje <xref:System.Collections.Generic.IEnumerable%601> . Na koniec te wyniki są pogrupowane przy użyciu nazwy typu jako klucza.  
  
## <a name="see-also"></a>Zobacz też

- [LINQ to Objects (Visual Basic)](linq-to-objects.md)
