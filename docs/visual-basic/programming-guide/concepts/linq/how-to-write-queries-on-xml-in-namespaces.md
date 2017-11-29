---
title: "Porady: Pisanie zapytań na kod XML w przestrzeni nazw (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d4131b5-3288-414f-b77c-b2edc2a1f465
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5708a2a162132262722f390842f59c9c6a6838e4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-write-queries-on-xml-in-namespaces-visual-basic"></a>Porady: Pisanie zapytań na kod XML w przestrzeni nazw (Visual Basic)
Aby napisać zapytanie na języku XML, który znajduje się w przestrzeni nazw, należy użyć <xref:System.Xml.Linq.XName> obiektów, które mają poprawną przestrzeń nazw.  
  
 W języku Visual Basic najbardziej typowym podejściem jest zdefiniowanie globalnej przestrzeni nazw, a następnie użyj literały XML i właściwości XML, które używają globalnej przestrzeni nazw. Można określić domyślnej globalnej przestrzeni nazw, w którym to przypadku elementy w literałach XML będzie się w przestrzeni nazw domyślnie. Alternatywnie można zdefiniować globalnej przestrzeni nazw z prefiksem, a następnie użyć prefiksu zgodnie z wymaganiami w literałach XML i właściwości XML. Podobnie jak w przypadku innych rodzajów XML atrybuty są zawsze podkatalogi domyślnie obszaru nazw.  
  
 Pierwszy zestaw przykłady w tym temacie przedstawiono sposób tworzenia drzewo XML w domyślnej przestrzeni nazw. Drugi zestaw pokazano, jak utworzyć drzewo XML w przestrzeni nazw z prefiksem.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy drzewo XML, który znajduje się w domyślnej przestrzeni nazw. Następnie pobierania kolekcję elementów.  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
                <Child>1</Child>  
                <Child>2</Child>  
                <Child>3</Child>  
                <AnotherChild>4</AnotherChild>  
                <AnotherChild>5</AnotherChild>  
                <AnotherChild>6</AnotherChild>  
            </Root>  
        Dim c1 As IEnumerable(Of XElement) = _  
            From el In root.<Child> _  
            Select el  
        For Each el As XElement In c1  
            Console.WriteLine(el.Value)  
        Next  
    End Sub  
End Module  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```  
1  
2  
3  
```  
  
## <a name="example"></a>Przykład  
 W języku Visual Basic, jednak Pisanie zapytań w drzewie XML, który używa przestrzeni nazw z prefiksem bardzo różni się od badania drzewo XML w domyślnej przestrzeni nazw. Zazwyczaj używają `Imports` instrukcji, aby zaimportować przestrzeni nazw z prefiksem. Następnie należy użyć prefiksu w nazwach elementów i atrybutów podczas skonstruuj drzewo XML. Prefiks można także użyć podczas wykonywania zapytania drzewa XML za pomocą właściwości XML.  
  
 Poniższy przykład tworzy drzewo XML, który znajduje się w przestrzeni nazw z prefiksem. Następnie pobierania kolekcję elementów.  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child>1</aw:Child>  
                <aw:Child>2</aw:Child>  
                <aw:Child>3</aw:Child>  
                <aw:AnotherChild>4</aw:AnotherChild>  
                <aw:AnotherChild>5</aw:AnotherChild>  
                <aw:AnotherChild>6</aw:AnotherChild>  
            </aw:Root>  
        Dim c1 As IEnumerable(Of XElement) = _  
            From el In root.<aw:Child> _  
            Select el  
        For Each el As XElement In c1  
            Console.WriteLine(CInt(el))  
        Next  
    End Sub  
End Module  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```  
1  
2  
3  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z przestrzeni nazw XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
