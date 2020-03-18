---
title: Utrzymywanie par name-value (C#)
ms.date: 07/20/2015
ms.assetid: 7b04b0f1-af64-42eb-8737-83f8861b5915
ms.openlocfilehash: 9c42a154a4c3ed1463e428faab4c7d33197ef4a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69591702"
---
# <a name="maintaining-namevalue-pairs-c"></a>Utrzymywanie par nazwy/wartości (C#)
Wiele aplikacji musi przechowywać informacje, które najlepiej są przechowywane jako pary nazw i wartości. Te informacje mogą być informacje o konfiguracji lub ustawienia globalne. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zawiera kilka metod, które ułatwiają zachowanie zestawu par nazw/wartości. Informacje można zachować jako atrybuty lub jako zestaw elementów podrzędnych.  
  
 Jedną różnicą między przechowywanie informacji jako atrybuty lub jako elementy podrzędne jest to, że atrybuty mają ograniczenie, że może istnieć tylko jeden atrybut o określonej nazwie dla elementu. To ograniczenie nie ma zastosowania do elementów podrzędnych.  
  
## <a name="setattributevalue-and-setelementvalue"></a>SetAttributeValue i SetElementValue  
 Dwie metody, które ułatwiają utrzymywanie <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> par <xref:System.Xml.Linq.XElement.SetElementValue%2A>nazwy/wartości są i . Te dwie metody mają podobną semantyki.  
  
 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>można dodawać, modyfikować lub usuwać atrybuty elementu.  
  
- Jeśli wywołasz <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> z nazwą atrybutu, który nie istnieje, metoda tworzy nowy atrybut i dodaje go do określonego elementu.  
  
- Jeśli wywołasz <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> nazwę istniejącego atrybutu i z określoną zawartością, zawartość atrybutu zostanie zastąpiona określoną zawartością.  
  
- Jeśli wywołasz <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> z nazwą istniejącego atrybutu i określisz wartość null dla zawartości, atrybut zostanie usunięty z jego nadrzędnego.  
  
 <xref:System.Xml.Linq.XElement.SetElementValue%2A>można dodawać, modyfikować lub usuwać elementy podrzędne elementu.  
  
- Jeśli wywołanie <xref:System.Xml.Linq.XElement.SetElementValue%2A> z nazwą elementu podrzędnego, który nie istnieje, metoda tworzy nowy element i dodaje go do określonego elementu.  
  
- Jeśli wywołasz <xref:System.Xml.Linq.XElement.SetElementValue%2A> nazwę istniejącego elementu i z określoną zawartością, zawartość elementu zostanie zastąpiona określoną zawartością.  
  
- Jeśli wywołasz <xref:System.Xml.Linq.XElement.SetElementValue%2A> z nazwą istniejącego elementu i określisz wartość null dla zawartości, element zostanie usunięty z jego elementu nadrzędnego.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy element bez atrybutów. Następnie używa <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> metody do tworzenia i utrzymywania listy par nazw/wartości.  
  
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
 Poniższy przykład tworzy element bez elementów podrzędnych. Następnie używa <xref:System.Xml.Linq.XElement.SetElementValue%2A> metody do tworzenia i utrzymywania listy par nazw/wartości.  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>
- <xref:System.Xml.Linq.XElement.SetElementValue%2A>
- [Modyfikowanie drzew XML (LINQ do XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md)
