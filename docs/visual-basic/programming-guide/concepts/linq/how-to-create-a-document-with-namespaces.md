---
title: 'Instrukcje: Tworzenie dokumentu z przestrzeniami nazw (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: cc5b0d4d-360c-4ada-94fa-2d2916e989be
ms.openlocfilehash: bbd23840b0356cf14d2c7d6cb71591fe6461a8bd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332587"
---
# <a name="how-to-create-a-document-with-namespaces-linq-to-xml-visual-basic"></a>Instrukcje: Tworzenie dokumentu z przestrzeniami nazw (LINQ to XML) (Visual Basic)
W tym temacie przedstawiono sposób tworzenia dokumentu z przestrzeniami nazw w Visual Basic.  
  
 W przypadku używania literałów XML w Visual Basic użytkownicy mogą definiować jedną globalną domyślną przestrzeń nazw XML. Ta przestrzeń nazw jest domyślną przestrzenią nazw dla literałów XML i właściwości XML. Domyślną przestrzeń nazw XML można zdefiniować na poziomie projektu lub na poziomie pliku. Jeśli jest zdefiniowany na poziomie pliku, zastępuje domyślny obszar nazw na poziomie projektu.  
  
 Można również zdefiniować inne przestrzenie nazw i określić prefiksy przestrzeni nazw dla tych przestrzeni nazw.  
  
 Można zdefiniować zarówno domyślne przestrzenie nazw, jak i przestrzenie nazw z prefiksem za pomocą słowa kluczowego `Imports`.  
  
 Aby uzyskać więcej informacji, zobacz [wprowadzenie do literałów XML w Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-xml-literals.md).  
  
 Należy zauważyć, że domyślna przestrzeń nazw XML dotyczy tylko elementów i nie do atrybutów. Atrybuty są domyślnie zawsze w obszarze brak przestrzeni nazw. Można jednak użyć prefiksu przestrzeni nazw, aby umieścić atrybut w przestrzeni nazw.  
  
## <a name="example"></a>Przykład  
 Ten przykład tworzy dokument zawierający przestrzeń nazw.  
  
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
 W tym przykładzie tworzony jest dokument zawierający dwie przestrzenie nazw, z których jedna jest domyślną przestrzenią nazw.  
  
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
 Poniższy przykład tworzy dokument zawierający wiele przestrzeni nazw, zarówno z prefiksami przestrzeni nazw.  
  
 Podczas serializowania drzewa XML [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] emituje deklaracje przestrzeni nazw zgodnie z wymaganiami, aby każdy element był w wyznaczeniu przestrzeni nazw.  
  
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

- [Przegląd przestrzeni nazw (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md)
