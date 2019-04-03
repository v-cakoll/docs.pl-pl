---
title: 'Instrukcje: Tworzenie dokumentu z przestrzeniami nazw (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: cc5b0d4d-360c-4ada-94fa-2d2916e989be
ms.openlocfilehash: b65d22451d900f7b20226f25b61bb235241dd84f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816865"
---
# <a name="how-to-create-a-document-with-namespaces-linq-to-xml-visual-basic"></a>Instrukcje: Tworzenie dokumentu z przestrzeniami nazw (LINQ to XML) (Visual Basic)
W tym temacie przedstawiono sposób tworzenia dokumentu z przestrzeniami nazw w języku Visual Basic.  
  
 Przy użyciu literałów XML w Visual Basic, użytkownicy mogą definiować jednej domyślnej globalnej przestrzeni nazw XML. Ta przestrzeń nazw jest domyślny obszar nazw dla literały XML i właściwości XML. Domyślny obszar nazw XML można definiować na poziomie projektu lub na poziomie plików. Jeśli jest zdefiniowana na poziomie plików, zastępuje ona domyślny obszar nazw na poziomie projektu.  
  
 Można również zdefiniować inne przestrzenie nazw i określić prefiksy przestrzeni nazw dla tych przestrzeni nazw.  
  
 Zdefiniować domyślne obszary nazw i przestrzeni nazw z prefiksem przy użyciu `Imports` — słowo kluczowe.  
  
 Aby uzyskać więcej informacji, zobacz [wprowadzenie do literałów XML w Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-xml-literals.md).  
  
 Należy pamiętać, że domyślny obszar nazw XML ma zastosowanie tylko do elementów, a nie atrybutów. Atrybuty są domyślnie zawsze w żadnej przestrzeni nazw. Jednak umożliwia prefiks przestrzeni nazw umieść atrybut w przestrzeni nazw.  
  
## <a name="example"></a>Przykład  
 Ten przykład tworzy dokument, który zawiera przestrzeń nazw.  
  
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
 Ten przykład tworzy dokument, który zawiera dwie przestrzenie nazw, z których jedna jest domyślny obszar nazw.  
  
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
 Poniższy przykład tworzy dokument, który zawiera wiele przestrzeni nazw, obie z prefiksy przestrzeni nazw.  
  
 Podczas serializacji drzewa XML [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] emituje deklaracje przestrzeni nazw zgodnie z potrzebami, tak, aby każdy element jest w jej wyznaczoną przestrzeni nazw.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Praca z przestrzeniami nazw XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
