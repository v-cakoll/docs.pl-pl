---
title: 'Instrukcje: Pisanie zapytań dotyczących kodu XML w przestrzeniach nazw (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 7d4131b5-3288-414f-b77c-b2edc2a1f465
ms.openlocfilehash: 4efa1de254a0264752514c5ae6e601a66fa56f95
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833441"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-visual-basic"></a>Instrukcje: Pisanie zapytań dotyczących kodu XML w przestrzeniach nazw (Visual Basic)
Aby napisać zapytanie na języku XML, który znajduje się w przestrzeni nazw, należy użyć <xref:System.Xml.Linq.XName> obiektów, które mają poprawną przestrzeń nazw.  
  
 W języku Visual Basic najbardziej typowym podejściem jest zdefiniowanie globalnej przestrzeni nazw, a następnie użyj literały XML i właściwości XML, które używają globalnej przestrzeni nazw. Można określić domyślnej globalnej przestrzeni nazw, w którym to przypadku elementy w literałach XML będzie się w przestrzeni nazw, domyślnie. Alternatywnie można zdefiniować globalnej przestrzeni nazw z prefiksem, a następnie użyć prefiksu zgodnie z potrzebami w literałach XML i właściwości XML. Podobnie jak w przypadku innych form XML atrybuty są zawsze w żadnej przestrzeni nazw, domyślnie.  
  
 Pierwszy zestaw przykładów w tym temacie przedstawiono sposób tworzenia drzewa XML w domyślnej przestrzeni nazw. Drugi zestaw przedstawia sposób tworzenia drzewa XML w przestrzeni nazw z prefiksem.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy drzewa XML, który znajduje się w domyślnej przestrzeni nazw. Pobiera kolekcję elementów.  
  
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
 W języku Visual Basic, Pisanie zapytań w drzewie XML, który używa przestrzeni nazw z prefiksem bardzo różni się od zapytania drzewa XML w domyślnej przestrzeni nazw. Zazwyczaj używają `Imports` instrukcję, aby zaimportować obszar nazw z prefiksem. Następnie należy użyć prefiksu w nazwach elementów i atrybutów podczas konstruowania drzewa XML. Możesz także użyć prefiksu, podczas wykonywania zapytania drzewa XML przy użyciu właściwości XML.  
  
 Poniższy przykład tworzy drzewa XML, który znajduje się w przestrzeni nazw z prefiksem. Pobiera kolekcję elementów.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Praca z przestrzeniami nazw XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
