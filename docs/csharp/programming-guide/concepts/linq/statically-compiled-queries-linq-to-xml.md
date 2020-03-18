---
title: Statycznie skompilowane zapytania (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: 3bf558fe-0705-479d-86d4-00188f5fcf9c
ms.openlocfilehash: 98725cece1006ba13afb64bb8ae17ae6e62c53cf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253032"
---
# <a name="statically-compiled-queries-linq-to-xml-c"></a>Statycznie skompilowane zapytania (LINQ do XML) (C#)
Jedną z najważniejszych korzyści wydajności LINQ do XML, w przeciwieństwie do <xref:System.Xml.XmlDocument>, jest to, że zapytania w LINQ do XML są statycznie skompilowany, podczas gdy zapytania XPath muszą być interpretowane w czasie wykonywania. Ta funkcja jest wbudowana w LINQ do XML, więc nie trzeba wykonywać dodatkowych kroków, aby z niej skorzystać, ale warto zrozumieć rozróżnienie przy wyborze między dwiema technologiami. W tym temacie wyjaśniono różnicę.  
  
## <a name="statically-compiled-queries-vs-xpath"></a>Statycznie skompilowane zapytania vs. XPath  
 W poniższym przykładzie pokazano, jak uzyskać elementy podrzędne o określonej nazwie i z atrybutem o określonej wartości.  
  
 Poniżej przedstawiono równoważne wyrażenie XPath:`//Address[@Type='Shipping']`
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    from el in po.Descendants("Address")  
    where (string)el.Attribute("Type") == "Shipping"  
    select el;  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 Wyrażenie kwerendy w tym przykładzie jest ponownie zapisywane przez kompilator do składni zapytań opartych na metodach. Poniższy przykład, który jest napisany w składni kwerendy opartej na metodach, daje takie same wyniki jak poprzedni:  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    po  
    .Descendants("Address")  
    .Where(el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 Metoda <xref:System.Linq.Enumerable.Where%2A> jest metodą rozszerzenia. Aby uzyskać więcej informacji, zobacz [Metody rozszerzenia](../../classes-and-structs/extension-methods.md). Ponieważ <xref:System.Linq.Enumerable.Where%2A> jest metodą rozszerzenia, powyższa kwerenda jest kompilowana tak, jakby została napisana w następujący sposób:  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    System.Linq.Enumerable.Where(  
        po.Descendants("Address"),  
        el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 W tym przykładzie daje dokładnie takie same wyniki jak w poprzednich dwóch przykładach. Ilustruje to fakt, że zapytania są skutecznie kompilowane do wywołań metod połączonych statycznie. To, w połączeniu z semantyką odroczonego wykonania iteratorów, poprawia wydajność. Aby uzyskać więcej informacji na temat semantyki odroczonego wykonywania iteratorów, zobacz [Odroczone wykonanie i ocena z opóźnieniem w LINQ do XML (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).  
  
> [!NOTE]
> Te przykłady są reprezentatywne dla kodu, który kompilator może napisać. Rzeczywista implementacja może nieznacznie różnić się od tych przykładów, ale wydajność będzie taka sama lub podobna do tych przykładów.  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a>Wykonywanie wyrażeń XPath za pomocą xmlDocument  
 W poniższym <xref:System.Xml.XmlDocument> przykładzie użyto do osiągnięcia tych samych wyników, co poprzednie przykłady:  
  
```csharp  
XmlReader reader = XmlReader.Create("PurchaseOrders.xml");  
XmlDocument doc = new XmlDocument();  
doc.Load(reader);  
XmlNodeList nl = doc.SelectNodes(".//Address[@Type='Shipping']");  
foreach (XmlNode n in nl)  
    Console.WriteLine(n.OuterXml);  
reader.Close();  
```  
  
 Ta kwerenda zwraca te same dane wyjściowe, co przykłady, które używają LINQ do XML; Jedyną różnicą jest to, że LINQ do XML <xref:System.Xml.XmlDocument> wcina wydrukowany kod XML, podczas gdy nie.  
  
 Jednak <xref:System.Xml.XmlDocument> podejście zazwyczaj nie działa tak dobrze, jak LINQ <xref:System.Xml.XmlNode.SelectNodes%2A> do XML, ponieważ metoda musi wykonać następujące wewnętrznie za każdym razem, gdy jest wywoływana:  
  
- Analizuje ciąg, który zawiera wyrażenie XPath, podział ciągu na tokeny.  
  
- Sprawdza poprawność tokenów, aby upewnić się, że wyrażenie XPath jest prawidłowe.  
  
- Tłumaczy wyrażenie na wewnętrzne drzewo wyrażeń.  
  
- Iteretują przez węzły, odpowiednio wybierając węzły dla zestawu wyników na podstawie oceny wyrażenia.  
  
 Jest to znacznie więcej niż praca wykonana przez odpowiednie linq do xml kwerendy. Różnica w wydajności zależy od różnych typów zapytań, ale ogólnie linq do xml zapytania zrobić mniej pracy <xref:System.Xml.XmlDocument>i dlatego lepiej, niż oceny wyrażeń XPath przy użyciu .  
