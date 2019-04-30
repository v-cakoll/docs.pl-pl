---
title: Obsługa pary nazwa wartość (C#)
ms.date: 07/20/2015
ms.assetid: 7b04b0f1-af64-42eb-8737-83f8861b5915
ms.openlocfilehash: 2f350083724cba7d5b9cfa593ed5733cc9836df8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61682381"
---
# <a name="maintaining-namevalue-pairs-c"></a>Obsługa pary nazwa/wartość (C#)
Masz wiele aplikacji do zarządzania danymi, który jest najlepiej pozostawić w postaci par nazwa/wartość. Te informacje mogą być informacje o konfiguracji lub ustawień globalnych. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zawiera niektóre metody, które ułatwiają zapewnienie zestaw par nazwa/wartość. Możesz zachować informacje jako atrybuty lub zbiór podrzędnych elementów.  
  
 Jedną różnicą między przechowywanie informacji jako atrybutów lub elementów podrzędnych jest atrybuty ograniczenie, że może istnieć tylko jeden atrybut o określonej nazwie elementu. To ograniczenie nie ma zastosowania do elementów podrzędnych.  
  
## <a name="setattributevalue-and-setelementvalue"></a>SetAttributeValue i SetElementValue  
 Te dwie metody, które ułatwiają utrzymanie par nazwa/wartość są <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> i <xref:System.Xml.Linq.XElement.SetElementValue%2A>. Te dwie metody mają podobną semantyką.  
  
 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> można dodać, modyfikowanie lub usuwanie atrybutów elementu.  
  
- Jeśli wywołasz <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> nazwą atrybutu, który nie istnieje metoda tworzy nowy atrybut i dodaje go do określonego elementu.  
  
- Jeśli wywołasz <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> z nazwą istniejącego atrybutu i niektórych określonych zawartości, zawartość atrybutu są zastępowane określonej zawartości.  
  
- Jeśli wywołasz <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> z nazwą istniejącego atrybutu, a następnie określ wartość null dla zawartości, ten atrybut jest usuwany z jego elementu nadrzędnego.  
  
 <xref:System.Xml.Linq.XElement.SetElementValue%2A> dodać, zmodyfikować lub usunąć elementy podrzędne elementu.  
  
- Jeśli wywołasz <xref:System.Xml.Linq.XElement.SetElementValue%2A> nazwą elementu podrzędnego, który nie istnieje metoda tworzy nowy element i dodaje go do określonego elementu.  
  
- Jeśli wywołasz <xref:System.Xml.Linq.XElement.SetElementValue%2A> z nazwą istniejącego elementu i niektórych określonych zawartości, zawartość elementu są zastępowane określonej zawartości.  
  
- Jeśli wywołasz <xref:System.Xml.Linq.XElement.SetElementValue%2A> z nazwą istniejącego elementu i określ wartość null w przypadku zawartości, element zostanie usunięty z jego elementu nadrzędnego.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy element bez atrybutów. Następnie używa <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> metodę, aby utworzyć i utrzymywać listę par nazwa/wartość.  
  
```csharp  
// Create an element with no content.  
XElement root = new XElement("Root");  
  
// Add a number of name/value pairs as attributes.  
root.SetAttributeValue("Top", 22);  
root.SetAttributeValue("Left", 20);  
root.SetAttributeValue("Bottom", 122);  
root.SetAttributeValue("Right", 300);  
root.SetAttributeValue("DefaultColor", "Color.Red");  
Console.WriteLine(root);  
  
// Replace the value of Top.  
root.SetAttributeValue("Top", 10);  
Console.WriteLine(root);  
  
// Remove DefaultColor.  
root.SetAttributeValue("DefaultColor", null);  
Console.WriteLine(root);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Root Top="22" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" />  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy element z podrzędnych nie elementów. Następnie używa <xref:System.Xml.Linq.XElement.SetElementValue%2A> metodę, aby utworzyć i utrzymywać listę par nazwa/wartość.  
  
```csharp  
// Create an element with no content.  
XElement root = new XElement("Root");  
  
// Add a number of name/value pairs as elements.  
root.SetElementValue("Top", 22);  
root.SetElementValue("Left", 20);  
root.SetElementValue("Bottom", 122);  
root.SetElementValue("Right", 300);  
root.SetElementValue("DefaultColor", "Color.Red");  
Console.WriteLine(root);  
Console.WriteLine("----");  
  
// Replace the value of Top.  
root.SetElementValue("Top", 10);  
Console.WriteLine(root);  
Console.WriteLine("----");  
  
// Remove DefaultColor.  
root.SetElementValue("DefaultColor", null);  
Console.WriteLine(root);  
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
- [Modyfikowanie drzew XML (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
