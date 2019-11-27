---
title: 'Instrukcje: Pisanie zapytań dotyczących kodu XML w przestrzeniach nazw'
ms.date: 07/20/2015
ms.assetid: 7d4131b5-3288-414f-b77c-b2edc2a1f465
ms.openlocfilehash: 496cf8daf5136e8aafff000312bbd730a5152e9f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344469"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-visual-basic"></a>Instrukcje: Pisanie zapytań dotyczących kodu XML w przestrzeniach nazw (Visual Basic)
Aby napisać zapytanie dotyczące kodu XML, który znajduje się w przestrzeni nazw, należy użyć <xref:System.Xml.Linq.XName> obiektów, które mają prawidłową przestrzeń nazw.  
  
 W Visual Basic, najbardziej typowym podejściem jest zdefiniowanie globalnej przestrzeni nazw, a następnie użycie literałów XML i właściwości XML, które używają globalnej przestrzeni nazw. Można zdefiniować globalną domyślną przestrzeń nazw, w której elementy case w literałach XML będą domyślnie w przestrzeni nazw. Alternatywnie można zdefiniować globalną przestrzeń nazw z prefiksem, a następnie użyć prefiksu zgodnie z wymaganiami w literałach XML i we właściwościach XML. Podobnie jak w przypadku innych form XML, atrybuty są zawsze domyślnie w żadnej przestrzeni nazw.  
  
 Pierwszy zestaw przykładów w tym temacie przedstawia sposób tworzenia drzewa XML w domyślnej przestrzeni nazw. Drugi zestaw pokazuje, jak utworzyć drzewo XML w przestrzeni nazw z prefiksem.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy drzewo XML, który znajduje się w domyślnym obszarze nazw. Następnie pobiera kolekcję elementów.  
  
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
  
```console  
1  
2  
3  
```  
  
## <a name="example"></a>Przykład  
 W Visual Basic jednak zapisywanie zapytań w drzewie XML, który używa przestrzeni nazw z prefiksem, jest zupełnie inne niż wykonywanie zapytań względem drzewa XML w domyślnej przestrzeni nazw. Zwykle używasz instrukcji `Imports`, aby zaimportować przestrzeń nazw z prefiksem. Następnie użyj prefiksu w nazwach elementów i atrybutów podczas konstruowania drzewa XML. Należy również użyć prefiksu podczas wykonywania zapytania w drzewie XML przy użyciu właściwości XML.  
  
 Poniższy przykład tworzy drzewo XML, który znajduje się w przestrzeni nazw z prefiksem. Następnie pobiera kolekcję elementów.  
  
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
  
```console  
1  
2  
3  
```  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd przestrzeni nazw (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md)
