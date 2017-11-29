---
title: "Porady: pobieranie wartości atrybutu (LINQ do XML) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5f4b3790-c83f-4eb3-a889-e3587edf3ca1
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5eed0c34f79a4a338dda7b26049f2c1510443736
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-visual-basic"></a>Porady: pobieranie wartości atrybutu (LINQ do XML) (Visual Basic)
W tym temacie przedstawiono sposób uzyskiwania wartości atrybutów. Istnieją dwa sposoby: można rzutować <xref:System.Xml.Linq.XAttribute> na żądany typ.; operator jawnej konwersji następnie konwertuje zawartość elementu lub atrybutu do określonego typu. Alternatywnie można użyć <xref:System.Xml.Linq.XAttribute.Value%2A> właściwości. Rzutowanie jest jednak ogólnie lepszym rozwiązaniem. Jeśli rzutowania atrybut do typu dopuszczającego wartość null, kod jest łatwiejsze do zapisania podczas pobierania wartości atrybutu, który może lub nie istnieje. Przykłady tej metody, zobacz [porady: pobieranie wartości elementu (LINQ do XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).  
  
## <a name="example"></a>Przykład  
 W języku Visual Basic właściwość zintegrowane atrybutu służy do pobierania wartości atrybutu.  
  
```vb  
Dim root As XElement = <Root Attr="abcde"/>  
Console.WriteLine(root)  
Dim str As String = root.@Attr  
Console.WriteLine(str)  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a>Przykład  
 W języku Visual Basic służy właściwości atrybutu zintegrowane można ustawić wartości atrybutu. Ponadto użycie właściwości atrybutu zintegrowane można ustawić wartość atrybutu, który nie istnieje, zostanie utworzona atrybutu.  
  
```vb  
Dim root As XElement = <Root Att1="content"/>  
root.@Att1 = "new content"  
root.@Att2 = "new attribute"  
Console.WriteLine(root)  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Root Att1="new content" Att2="new attribute" />  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak można pobrać wartości atrybutu którym atrybut jest w przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [Praca z przestrzeni nazw XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root aw:Attr="abcde"/>  
        Dim str As String = root.@aw:Attr  
        Console.WriteLine(str)  
    End Sub  
End Module  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```  
abcde  
```  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ do osi XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
