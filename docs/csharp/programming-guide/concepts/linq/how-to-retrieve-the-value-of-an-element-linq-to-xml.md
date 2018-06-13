---
title: 'Porady: pobieranie wartości elementu (LINQ do XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 4228c007-07c9-4cf2-a45b-e7074c109581
ms.openlocfilehash: 5eb75ea3dddbc90141ec875f87a988157ddf0362
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33324333"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-c"></a>Porady: pobieranie wartości elementu (LINQ do XML) (C#)
W tym temacie pokazano, jak pobrać wartość elementów. Istnieją dwa sposoby, w tym celu. Jednym ze sposobów jest można rzutować <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XAttribute> do odpowiedniego typu. Operator jawnej konwersji następnie konwertuje zawartość elementu lub atrybutu na określony typ i przypisuje go do zmiennej użytkownika. Alternatywnie można użyć <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> właściwości lub <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> właściwości.  
  
 Języku C# jednak rzutowanie jest zwykle lepszym rozwiązaniem. Jeśli rzutować elementu lub atrybutu typu dopuszczającego wartość null, kod jest łatwiejsze do zapisania podczas pobierania wartości elementu (lub atrybut), który może lub nie istnieje. W ostatnim przykładzie w tym temacie pokazano to. Jednak nie można ustawić zawartość elementu za pośrednictwem rzutowanie, jak to możliwe za pośrednictwem <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> właściwości.  
  
## <a name="example"></a>Przykład  
 Do pobierania wartości elementu, należy po prostu rzutowania <xref:System.Xml.Linq.XElement> obiektu do żądanego typu. Zawsze można rzutować elementu na ciąg w następujący sposób:  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (string)e);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a>Przykład  
 Można również rzutować elementów typu innego niż ciąg. Na przykład, jeśli element, który zawiera całkowitą, można rzutować na `int`, jak pokazano w poniższym kodzie:  
  
```csharp  
XElement e = new XElement("Age", "44");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (int)e);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zawiera operatory jawnego rzutowania dla następujących typów danych: `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?` , `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, i `GUID?`.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] udostępnia tego samego operatory rzutowania dla <xref:System.Xml.Linq.XAttribute> obiektów.  
  
## <a name="example"></a>Przykład  
 Można użyć <xref:System.Xml.Linq.XElement.Value%2A> właściwość, aby pobrać zawartość elementu:  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");   
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + e.Value);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a>Przykład  
 Czasami użytkownik próbuje pobrać wartość elementu, nawet jeśli nie ma pewności, że istnieje. W takim przypadku po przypisaniu rzutować elementu do typu dopuszczającego wartości null (albo `string` lub jeden z typów wartości null w [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]), jeśli element nie istnieje przypisane tylko ustawiono zmienną `null`. Poniższy kod pokazuje, że element może lub nie istnieje, jest łatwiejsze w rzutowanie niż korzystać <xref:System.Xml.Linq.XElement.Value%2A> właściwości.  
  
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
  
```  
c1:child 1 content  
c2:2  
c3:element does not exist  
c4:element does not exist  
  
v1:child 1 content  
v2:2  
v3:element does not exist  
v4:element does not exist  
```  
  
 Ogólnie rzecz biorąc można napisać kod prostszy, używając rzutowanie Aby pobrać zawartość elementów i atrybutów.  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ do osi XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
