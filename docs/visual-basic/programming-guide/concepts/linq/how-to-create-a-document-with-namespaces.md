---
title: 'Porady: Tworzenie dokumentu z przestrzeni nazw (LINQ do XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: cc5b0d4d-360c-4ada-94fa-2d2916e989be
ms.openlocfilehash: 204d8a9cbb6ce47c6334c7309d27910c75b90ae0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643081"
---
# <a name="how-to-create-a-document-with-namespaces-linq-to-xml-visual-basic"></a>Porady: Tworzenie dokumentu z przestrzeni nazw (LINQ do XML) (Visual Basic)
W tym temacie przedstawiono sposób tworzenia dokumentu z przestrzeni nazw w języku Visual Basic.  
  
 Przy użyciu literałów XML w Visual Basic, użytkownicy mogą definiować jedną globalnego domyślnej przestrzeni nazw XML. Ta przestrzeń nazw jest domyślny obszar nazw dla literałów XML i właściwości XML. Domyślna przestrzeń nazw XML można zdefiniować na poziomie projektu lub poziomie plików. Jeśli jest zdefiniowana na poziomie plików, zastępuje on domyślnej przestrzeni nazw na poziomie projektu.  
  
 Można również zdefiniować innych przestrzeniach nazw i określić prefiksy przestrzeni nazw dla tych obszarów nazw.  
  
 Zdefiniuj zarówno domyślne obszary nazw, jak i przestrzeni nazw z prefiksem przy użyciu `Imports` — słowo kluczowe.  
  
 Aby uzyskać więcej informacji, zobacz [wprowadzenie do literałów XML w Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-xml-literals.md).  
  
 Należy pamiętać, że domyślna przestrzeń nazw XML ma zastosowanie tylko do elementów, a nie do atrybutów. Atrybuty są domyślnie zawsze w bez przestrzeni nazw. Jednak można prefiks przestrzeni nazw umieść atrybut w przestrzeni nazw.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie tworzy dokument, który zawiera przestrzeń nazw.  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child aw:Att="attvalue"/>  
            </aw:Root>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child aw:Att="attvalue" />  
</aw:Root>  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie tworzy dokument, który zawiera dwie przestrzenie nazw, z których jeden jest domyślnej przestrzeni nazw.  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
Imports <xmlns:fc="www.fourthcoffee.com">  
  
Module Module1  
  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
                <Child Att="attvalue"/>  
                <fc:Child2>child2 content</fc:Child2>  
            </Root>  
        Console.WriteLine(root)  
    End Sub  
  
End Module  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Root xmlns:fc="www.fourthcoffee.com" xmlns="http://www.adventure-works.com">  
  <Child Att="attvalue" />  
  <fc:Child2>child2 content</fc:Child2>  
</Root>  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy dokument, który zawiera wiele obszarów nazw, zarówno z prefiksy przestrzeni nazw.  
  
 Podczas serializowania drzewo XML [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] emituje deklaracje przestrzeni nazw zgodnie z wymaganiami, dzięki czemu każdy element znajduje się w wyznaczonym przestrzeń nazw.  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
Imports <xmlns:fc="www.fourthcoffee.com">  
  
Module Module1  
  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <fc:Child>  
                    <aw:DifferentChild>other content</aw:DifferentChild>  
                </fc:Child>  
                <aw:Child2>c2 content</aw:Child2>  
                <fc:Child3>c3 content</fc:Child3>  
            </aw:Root>  
        Console.WriteLine(root)  
    End Sub  
  
End Module  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z przestrzeni nazw XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
