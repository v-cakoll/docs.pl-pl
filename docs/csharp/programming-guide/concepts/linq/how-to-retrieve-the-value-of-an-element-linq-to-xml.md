---
title: Jak pobrać wartość elementu (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: 4228c007-07c9-4cf2-a45b-e7074c109581
ms.openlocfilehash: c4bb78e937fe0de08242923cdd7cd638abf571c7
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805832"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-c"></a>Jak pobrać wartość elementu (LINQ do XML) (C#)

W tym artykule pokazano, jak uzyskać wartość elementów. Istnieją dwa główne sposoby uzyskania wartości:

- Rzut <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XAttribute> do żądanego typu. Operator konwersji jawne następnie konwertuje zawartość elementu lub atrybutu do określonego typu i przypisuje go do zmiennej.

- Użyj <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> właściwości <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> lub. Można również ustawić wartość przy użyciu tych właściwości.

Z C#, odlewania jest na ogół lepsze podejście. Jeśli rzutujesz element lub atrybut na typ wartości możliwej do wartości null, kod jest prostszy do zapisania podczas pobierania wartości elementu (lub atrybutu), który może lub nie może istnieć. Ostatni [przykład](#element-might-not-exist-example) w tym artykule pokazuje, że rzutowanie jest prostsze w przypadku, gdy element może nie istnieć. Jednak nie można ustawić zawartość elementu za pomocą rzutowania, jak można za pośrednictwem <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> właściwości.  
  
## <a name="string-cast-example"></a>Przykład rzutowania ciągiem  
 Aby pobrać wartość elementu, przerzuć obiekt na <xref:System.Xml.Linq.XElement> żądany typ. Element można rzutować na ciąg w następujący sposób:  
  
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
  
## <a name="integer-cast-example"></a>Przykład rzutowania całkowitej  
 Można również rzutować elementy do typów innych niż ciąg. Na przykład jeśli masz element, który zawiera całkowitą, można `int`go przerzucić na , jak pokazano w poniższym kodzie:  
  
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
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zapewnia operatory jawnego rzutu `string` `bool`dla `bool?` `int`następujących `int?` `uint`typów `uint?` `long`danych: , , , , , , `GUID`, `GUID?` `decimal` `decimal?` `DateTime` `DateTime?` `TimeSpan` `TimeSpan?` `long?` `ulong` `ulong?` `float`, , , `float?`, , `double`, `double?`, , , , , , , , , , i .  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zapewnia te same <xref:System.Xml.Linq.XAttribute> operatory rzutowania dla obiektów.  
  
## <a name="value-property-example"></a>Przykład właściwości wartość  
 Można użyć <xref:System.Xml.Linq.XElement.Value%2A> właściwości, aby pobrać zawartość elementu:  
  
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
  
## <a name="element-might-not-exist-example"></a>Element może nie istnieć przykład
 Czasami spróbuj odzyskać wartość elementu, nawet jeśli nie masz pewności, czy istnieje. W takim przypadku po przypisaniu elementu rzutowanego do typu odwołania możliwego do wartości null lub typu wartości `null`nullable, jeśli element nie istnieje, przypisana zmienna jest ustawiona na . Poniższy kod pokazuje, że gdy element może lub nie może istnieć, <xref:System.Xml.Linq.XElement.Value%2A> jest łatwiejsze w użyciu rzutowania niż do korzystania z właściwości.  
  
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
  
 Ogólnie rzecz biorąc można napisać prostszy kod podczas korzystania z rzutowania do pobierania zawartości elementów i atrybutów.  
  
## <a name="see-also"></a>Zobacz też

- [Osie LINQ do XML (C#)](./linq-to-xml-axes-overview.md)
