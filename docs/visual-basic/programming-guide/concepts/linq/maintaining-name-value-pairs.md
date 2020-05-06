---
title: Obsługiwanie par nazwa-wartość
ms.date: 07/20/2015
ms.assetid: 57ac2072-d9f5-432b-84f0-a889c62fd813
ms.openlocfilehash: b8c9487330239e7e6365055d5f08a02f2dbb0e37
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82796161"
---
# <a name="maintaining-namevalue-pairs-visual-basic"></a>Obsługa par nazwa/wartość (Visual Basic)
Wiele aplikacji musi utrzymywać informacje, które najlepiej są przechowywane jako pary nazwa/wartość. Te informacje mogą dotyczyć informacji konfiguracyjnych lub ustawień globalnych. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zawiera kilka metod, które ułatwiają przechowywanie zestawu par nazwa/wartość. Możesz zachować informacje jako atrybuty lub jako zestaw elementów podrzędnych.  
  
 Jedną z różnic między przechowywaniem informacji jako atrybuty lub jako elementami podrzędnymi jest to, że atrybuty mogą mieć tylko jeden atrybut z określoną nazwą dla elementu. To ograniczenie nie ma zastosowania do elementów podrzędnych.  
  
## <a name="setattributevalue-and-setelementvalue"></a>SetAttributeValue i SetElementValue  
 Dwie metody, które ułatwiają utrzymywanie par nazwa/ <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> wartość <xref:System.Xml.Linq.XElement.SetElementValue%2A>, i. Te dwie metody mają podobną semantykę.  
  
 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>może dodawać, modyfikować lub usuwać atrybuty elementu.  
  
- Jeśli wywoływana <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> jest nazwa atrybutu, który nie istnieje, metoda tworzy nowy atrybut i dodaje go do określonego elementu.  
  
- Jeśli wywołasz <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> nazwę istniejącego atrybutu i z określoną zawartością, zawartość atrybutu zostanie zastąpiona określoną zawartością.  
  
- Jeśli wywołasz <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> nazwę istniejącego atrybutu i określisz wartość null dla zawartości, atrybut zostanie usunięty z jego elementu nadrzędnego.  
  
 <xref:System.Xml.Linq.XElement.SetElementValue%2A>może dodawać, modyfikować lub usuwać elementy podrzędne elementu.  
  
- W przypadku wywołania <xref:System.Xml.Linq.XElement.SetElementValue%2A> z nazwą elementu podrzędnego, który nie istnieje, metoda tworzy nowy element i dodaje go do określonego elementu.  
  
- Jeśli wywołasz <xref:System.Xml.Linq.XElement.SetElementValue%2A> nazwę istniejącego elementu i z określoną zawartością, zawartość elementu zostanie zastąpiona określoną zawartością.  
  
- Jeśli wywołasz <xref:System.Xml.Linq.XElement.SetElementValue%2A> nazwę istniejącego elementu i określisz wartość null dla zawartości, element zostanie usunięty z jego elementu nadrzędnego.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy element bez atrybutów. Następnie używa <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> metody, aby utworzyć i zachować listę par nazwa/wartość.  
  
```vb  
' Create an element with no content.  
Dim root As XElement = <Root/>  
  
' Add a number of name/value pairs as attributes.  
root.SetAttributeValue("Top", 22)  
root.SetAttributeValue("Left", 20)  
root.SetAttributeValue("Bottom", 122)  
root.SetAttributeValue("Right", 300)  
root.SetAttributeValue("DefaultColor", "Color.Red")  
Console.WriteLine(root)  
  
' Replace the value of Top.  
root.SetAttributeValue("Top", 10)  
Console.WriteLine(root)  
  
' Remove DefaultColor.  
root.SetAttributeValue("DefaultColor", Nothing)  
Console.WriteLine(root)  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Root Top="22" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" />  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy element bez elementów podrzędnych. Następnie używa <xref:System.Xml.Linq.XElement.SetElementValue%2A> metody, aby utworzyć i zachować listę par nazwa/wartość.  
  
```vb  
' Create an element with no content.  
Dim root As XElement = <Root/>  
  
' Add a number of name/value pairs as elements.  
root.SetElementValue("Top", 22)  
root.SetElementValue("Left", 20)  
root.SetElementValue("Bottom", 122)  
root.SetElementValue("Right", 300)  
root.SetElementValue("DefaultColor", "Color.Red")  
Console.WriteLine(root)  
Console.WriteLine("----")  
  
' Replace the value of Top.  
root.SetElementValue("Top", 10)  
Console.WriteLine(root)  
Console.WriteLine("----")  
  
' Remove DefaultColor.  
root.SetElementValue("DefaultColor", Nothing)  
Console.WriteLine(root)  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Root>  
  <Top>22</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
  <DefaultColor>Color.Red</DefaultColor>  
</Root>
----  
<Root>  
  <Top>10</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
  <DefaultColor>Color.Red</DefaultColor>  
</Root>
----
<Root>  
  <Top>10</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
</Root>
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>
- <xref:System.Xml.Linq.XElement.SetElementValue%2A>
- [Modyfikowanie drzew XML (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
