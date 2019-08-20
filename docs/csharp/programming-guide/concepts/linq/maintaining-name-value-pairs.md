---
title: Obsługa par nazwa-wartość (C#)
ms.date: 07/20/2015
ms.assetid: 7b04b0f1-af64-42eb-8737-83f8861b5915
ms.openlocfilehash: 9c42a154a4c3ed1463e428faab4c7d33197ef4a5
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591702"
---
# <a name="maintaining-namevalue-pairs-c"></a>Obsługa par nazwa/wartość (C#)
Wiele aplikacji musi utrzymywać informacje, które najlepiej są przechowywane jako pary nazwa/wartość. Te informacje mogą dotyczyć informacji konfiguracyjnych lub ustawień globalnych. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zawiera kilka metod, które ułatwiają przechowywanie zestawu par nazwa/wartość. Możesz zachować informacje jako atrybuty lub jako zestaw elementów podrzędnych.  
  
 Jedną z różnic między przechowywaniem informacji jako atrybuty lub jako elementami podrzędnymi jest to, że atrybuty mogą mieć tylko jeden atrybut z określoną nazwą dla elementu. To ograniczenie nie ma zastosowania do elementów podrzędnych.  
  
## <a name="setattributevalue-and-setelementvalue"></a>SetAttributeValue i SetElementValue  
 Dwie metody, które ułatwiają utrzymywanie par <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> nazwa/wartość, i. <xref:System.Xml.Linq.XElement.SetElementValue%2A> Te dwie metody mają podobną semantykę.  
  
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
 Poniższy przykład tworzy element bez elementów podrzędnych. Następnie używa <xref:System.Xml.Linq.XElement.SetElementValue%2A> metody, aby utworzyć i zachować listę par nazwa/wartość.  
  
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
- [Modyfikowanie drzew XML (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md)
