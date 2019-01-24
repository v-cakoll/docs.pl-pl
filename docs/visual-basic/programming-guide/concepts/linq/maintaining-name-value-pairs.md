---
title: Obsługa pary nazwa wartość (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 57ac2072-d9f5-432b-84f0-a889c62fd813
ms.openlocfilehash: d0f0306ef354eb55bb32d28332590c02425b112a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54705959"
---
# <a name="maintaining-namevalue-pairs-visual-basic"></a>Obsługa pary nazwa/wartość (Visual Basic)
Masz wiele aplikacji do zarządzania danymi, który jest najlepiej pozostawić w postaci par nazwa/wartość. Te informacje mogą być informacje o konfiguracji lub ustawień globalnych. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zawiera niektóre metody, które ułatwiają zapewnienie zestaw par nazwa/wartość. Możesz zachować informacje jako atrybuty lub zbiór podrzędnych elementów.  
  
 Jedną różnicą między przechowywanie informacji jako atrybutów lub elementów podrzędnych jest atrybuty ograniczenie, że może istnieć tylko jeden atrybut o określonej nazwie elementu. To ograniczenie nie ma zastosowania do elementów podrzędnych.  
  
## <a name="setattributevalue-and-setelementvalue"></a>SetAttributeValue i SetElementValue  
 Te dwie metody, które ułatwiają utrzymanie par nazwa/wartość są <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> i <xref:System.Xml.Linq.XElement.SetElementValue%2A>. Te dwie metody mają podobną semantyką.  
  
 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> można dodać, modyfikowanie lub usuwanie atrybutów elementu.  
  
-   Jeśli wywołasz <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> nazwą atrybutu, który nie istnieje metoda tworzy nowy atrybut i dodaje go do określonego elementu.  
  
-   Jeśli wywołasz <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> z nazwą istniejącego atrybutu i niektórych określonych zawartości, zawartość atrybutu są zastępowane określonej zawartości.  
  
-   Jeśli wywołasz <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> z nazwą istniejącego atrybutu, a następnie określ wartość null dla zawartości, ten atrybut jest usuwany z jego elementu nadrzędnego.  
  
 <xref:System.Xml.Linq.XElement.SetElementValue%2A> dodać, zmodyfikować lub usunąć elementy podrzędne elementu.  
  
-   Jeśli wywołasz <xref:System.Xml.Linq.XElement.SetElementValue%2A> nazwą elementu podrzędnego, który nie istnieje metoda tworzy nowy element i dodaje go do określonego elementu.  
  
-   Jeśli wywołasz <xref:System.Xml.Linq.XElement.SetElementValue%2A> z nazwą istniejącego elementu i niektórych określonych zawartości, zawartość elementu są zastępowane określonej zawartości.  
  
-   Jeśli wywołasz <xref:System.Xml.Linq.XElement.SetElementValue%2A> z nazwą istniejącego elementu i określ wartość null w przypadku zawartości, element zostanie usunięty z jego elementu nadrzędnego.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy element bez atrybutów. Następnie używa <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> metodę, aby utworzyć i utrzymywać listę par nazwa/wartość.  
  
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
 Poniższy przykład tworzy element z podrzędnych nie elementów. Następnie używa <xref:System.Xml.Linq.XElement.SetElementValue%2A> metodę, aby utworzyć i utrzymywać listę par nazwa/wartość.  
  
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
