---
title: 'Porady: znajdowanie pojedynczego podrzędnym, przy użyciu metody elementy podrzędne (C#)'
ms.date: 07/20/2015
ms.assetid: 6f735be9-0293-4680-8007-ca9d96bfebed
ms.openlocfilehash: e08e07e0d32146a14b90b9d6463e6e58a233a923
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33316962"
---
# <a name="how-to-find-a-single-descendant-using-the-descendants-method-c"></a>Porady: znajdowanie pojedynczego podrzędnym, przy użyciu metody elementy podrzędne (C#)
Można użyć <xref:System.Xml.Linq.XContainer.Descendants%2A> osi metodę, aby szybko napisać kod, aby znaleźć pojedynczy jednoznacznie o nazwie elementu. Ta technika jest szczególnie przydatne, gdy chcesz znaleźć określonego obiektu podrzędnego o określonej nazwie. Można napisać kod, aby przejść do żądanego elementu, ale często jest szybsze i łatwiejsze do pisania kodu za pomocą <xref:System.Xml.Linq.XContainer.Descendants%2A> osi.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Linq.Enumerable.First%2A> — operator zapytań standardowa.  
  
```csharp  
XElement root = XElement.Parse(@"<Root>  
  <Child1>  
    <GrandChild1>GC1 Value</GrandChild1>  
  </Child1>  
  <Child2>  
    <GrandChild2>GC2 Value</GrandChild2>  
  </Child2>  
  <Child3>  
    <GrandChild3>GC3 Value</GrandChild3>  
  </Child3>  
  <Child4>  
    <GrandChild4>GC4 Value</GrandChild4>  
  </Child4>  
</Root>");  
string grandChild3 = (string)  
    (from el in root.Descendants("GrandChild3")  
    select el).First();  
Console.WriteLine(grandChild3);  
```  
  
 Ten kod generuje następujące dane wyjściowe:  
  
```  
GC3 Value  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano tego samego zapytania w formacie XML, który znajduje się w przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [Praca z przestrzeni nazw XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
```csharp  
XElement root = XElement.Parse(@"<aw:Root xmlns:aw='http://www.adventure-works.com'>  
  <aw:Child1>  
    <aw:GrandChild1>GC1 Value</aw:GrandChild1>  
  </aw:Child1>  
  <aw:Child2>  
    <aw:GrandChild2>GC2 Value</aw:GrandChild2>  
  </aw:Child2>  
  <aw:Child3>  
    <aw:GrandChild3>GC3 Value</aw:GrandChild3>  
  </aw:Child3>  
  <aw:Child4>  
    <aw:GrandChild4>GC4 Value</aw:GrandChild4>  
  </aw:Child4>  
</aw:Root>");  
XNamespace aw = "http://www.adventure-works.com";  
string grandChild3 = (string)  
    (from el in root.Descendants(aw + "GrandChild3")  
     select el).First();  
Console.WriteLine(grandChild3);  
```  
  
 Ten kod generuje następujące dane wyjściowe:  
  
```  
GC3 Value  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowe zapytania (LINQ do XML) (C#)](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
