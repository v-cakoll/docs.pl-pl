---
title: Jak pobrać wartość elementu (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: 4228c007-07c9-4cf2-a45b-e7074c109581
ms.openlocfilehash: 6f2d355eac9914cd4c03d3a4521992b346b92f0b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168690"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-c"></a>Jak pobrać wartość elementu (LINQ do XML) (C#)
W tym temacie pokazano, jak uzyskać wartość elementów. Istnieją dwa główne sposoby, aby to zrobić. Jednym ze sposobów <xref:System.Xml.Linq.XElement> jest <xref:System.Xml.Linq.XAttribute> rzut lub do żądanego typu. Operator konwersji jawnej następnie konwertuje zawartość elementu lub atrybutu na określony typ i przypisuje go do zmiennej. Goście mogą również korzystać <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> z <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> obiektu lub obiektu.  
  
 Z C#, jednak casting jest na ogół lepszym podejściem. Jeśli rzutowane elementu lub atrybutu do typu nullable, kod jest prostsze do zapisu podczas pobierania wartości elementu (lub atrybutu), które mogą lub nie mogą istnieć. Ostatni przykład w tym temacie pokazuje to. Jednak nie można ustawić zawartość elementu za pomocą rzutowania, jak można za pośrednictwem <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> właściwości.  
  
## <a name="example"></a>Przykład  
 Aby pobrać wartość elementu, wystarczy rzutować <xref:System.Xml.Linq.XElement> obiekt do żądanego typu. Zawsze można rzutować element na ciąg, w następujący sposób:  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (string)e);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```output  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a>Przykład  
 Można również rzutować elementy do typów innych niż ciąg. Na przykład jeśli masz element, który zawiera całkowitą, można `int`rzutować go do , jak pokazano w następującym kodzie:  
  
```csharp  
XElement e = new XElement("Age", "44");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (int)e);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```output  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zapewnia operatory oddanych jawnie `string` `bool`dla `bool?` `int`następujących `int?` `uint`typów `uint?` `long`danych: , , , `decimal` `decimal?`, `DateTime` `DateTime?`, `TimeSpan` `TimeSpan?`, `GUID`, `GUID?` `long?` `ulong` `ulong?` `float`, , `float?`, `double`, `double?`, , , , i .  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zapewnia te same <xref:System.Xml.Linq.XAttribute> operatory rzutów dla obiektów.  
  
## <a name="example"></a>Przykład  
 Właściwość służy <xref:System.Xml.Linq.XElement.Value%2A> do pobierania zawartości elementu:  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + e.Value);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```output  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a>Przykład  
 Czasami próbujesz pobrać wartość elementu, nawet jeśli nie masz pewności, że istnieje. W takim przypadku po przypisaniu casted element do `string` typu nullable (lub jeden z typów nullable w .NET Framework), jeśli `null`element nie istnieje przypisane zmiennej jest po prostu ustawiona na . Poniższy kod pokazuje, że gdy element może lub nie może istnieć, <xref:System.Xml.Linq.XElement.Value%2A> łatwiej jest używać rzutowania niż do korzystania z właściwości.  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child1", "child 1 content"),  
    new XElement("Child2", "2")  
);  
  
// The following assignments show why it is easier to use  
// casting when the element might or might not exist.  
  
string c1 = (string)root.Element("Child1");  
Console.WriteLine("c1:{0}", c1 == null ? "element does not exist" : c1);  
  
int? c2 = (int?)root.Element("Child2");  
Console.WriteLine("c2:{0}", c2 == null ? "element does not exist" : c2.ToString());  
  
string c3 = (string)root.Element("Child3");  
Console.WriteLine("c3:{0}", c3 == null ? "element does not exist" : c3);  
  
int? c4 = (int?)root.Element("Child4");  
Console.WriteLine("c4:{0}", c4 == null ? "element does not exist" : c4.ToString());  
  
Console.WriteLine();  
  
// The following assignments show the required code when using  
// the Value property when the element might or might not exist.  
// Notice that this is more difficult than the casting approach.  
  
XElement e1 = root.Element("Child1");  
string v1;  
if (e1 == null)  
    v1 = null;  
else  
    v1 = e1.Value;  
Console.WriteLine("v1:{0}", v1 == null ? "element does not exist" : v1);  
  
XElement e2 = root.Element("Child2");  
int? v2;  
if (e2 == null)  
    v2 = null;  
else  
    v2 = Int32.Parse(e2.Value);  
Console.WriteLine("v2:{0}", v2 == null ? "element does not exist" : v2.ToString());  
  
XElement e3 = root.Element("Child3");  
string v3;  
if (e3 == null)  
    v3 = null;  
else  
    v3 = e3.Value;  
Console.WriteLine("v3:{0}", v3 == null ? "element does not exist" : v3);  
  
XElement e4 = root.Element("Child4");  
int? v4;  
if (e4 == null)  
    v4 = null;  
else  
    v4 = Int32.Parse(e4.Value);  
Console.WriteLine("v4:{0}", v4 == null ? "element does not exist" : v4.ToString());  
```  
  
 Ten kod generuje następujące dane wyjściowe:  
  
```output  
c1:child 1 content  
c2:2  
c3:element does not exist  
c4:element does not exist  
  
v1:child 1 content  
v2:2  
v3:element does not exist  
v4:element does not exist  
```  
  
 Ogólnie rzecz biorąc można napisać prostszy kod podczas używania rzutowania do pobierania zawartości elementów i atrybutów.  
  
## <a name="see-also"></a>Zobacz też

- [LINQ do osi XML (C#)](./linq-to-xml-axes-overview.md)
