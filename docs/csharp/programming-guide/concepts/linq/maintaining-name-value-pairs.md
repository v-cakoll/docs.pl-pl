---
title: Obsługa pary nazwa wartość (C#)
ms.date: 07/20/2015
ms.assetid: 7b04b0f1-af64-42eb-8737-83f8861b5915
ms.openlocfilehash: ac1e6464618c00cba4ded92492fe4a687e1a25f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33325581"
---
# <a name="maintaining-namevalue-pairs-c"></a>Obsługa pary nazwa/wartość (C#)
Wiele aplikacji ma do przechowywania informacji, które najlepiej jest przechowywane jako pary nazwa/wartość. Informacje te mogą być informacje o konfiguracji lub ustawień globalnych. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zawiera niektórych metod, które ułatwiają Zachowaj zestaw par nazwa/wartość. Możesz zachować informacje jako atrybuty lub zbiór podrzędnych elementów.  
  
 Jeden różnica między jednoczesnym zachowaniu bezpieczeństwa informacji jako atrybuty lub jako elementy podrzędne jest atrybuty ograniczenia, że może istnieć tylko jeden atrybut o określonej nazwie dla elementu. To ograniczenie nie ma zastosowania do elementów podrzędnych.  
  
## <a name="setattributevalue-and-setelementvalue"></a>SetAttributeValue i SetElementValue  
 Te dwie metody, które ułatwiają utrzymanie par nazwa/wartość są <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> i <xref:System.Xml.Linq.XElement.SetElementValue%2A>. Te dwie metody mają podobne semantyki.  
  
 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> można dodać, modyfikowanie lub usuwanie atrybutów elementu.  
  
-   Jeśli należy wywołać <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> z nazwą atrybutu, który nie istnieje, metoda tworzy nowy atrybut i dodaje go do określonego elementu.  
  
-   Jeśli należy wywołać <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> z nazwą istniejącego atrybutu i niektóre określone zawartości, zawartość atrybutu są zastępowane z określoną zawartością.  
  
-   Wywołanie <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> z nazwą istniejącego atrybutu, a następnie określ wartość null dla zawartości, atrybut jest usuwany po swoim obiekcie nadrzędnym.  
  
 <xref:System.Xml.Linq.XElement.SetElementValue%2A> można dodać, modyfikowanie lub usuwanie elementów podrzędnych danego elementu.  
  
-   Jeśli należy wywołać <xref:System.Xml.Linq.XElement.SetElementValue%2A> z nazwą elementu podrzędnego, który nie istnieje, metoda tworzy nowy element i dodaje go do określonego elementu.  
  
-   Jeśli należy wywołać <xref:System.Xml.Linq.XElement.SetElementValue%2A> z nazwą istniejącego elementu i niektóre określone zawartości, zawartość elementu są zastępowane z określoną zawartością.  
  
-   Jeśli należy wywołać <xref:System.Xml.Linq.XElement.SetElementValue%2A> z nazwą istniejącego elementu i określ wartość null dla zawartości, element zostanie usunięty z jego elementu nadrzędnego.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy element bez atrybutów. Następnie używa <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> metodę, aby utworzyć i zachować listę par nazwa/wartość.  
  
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
 Poniższy przykład tworzy element z nie podrzędnych elementów. Następnie używa <xref:System.Xml.Linq.XElement.SetElementValue%2A> metodę, aby utworzyć i zachować listę par nazwa/wartość.  
  
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
 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>  
 <xref:System.Xml.Linq.XElement.SetElementValue%2A>  
 [Modyfikowanie drzew XML (LINQ do XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
