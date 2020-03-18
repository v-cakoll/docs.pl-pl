---
title: Jak znaleźć element z określonym elementem podrzędnym (C#)
ms.date: 07/20/2015
ms.assetid: 00cf5555-374e-4369-bf93-7bd2e7f21db3
ms.openlocfilehash: 0536b1b92d4d7fc18b5d406bbcd24aefc6a840c6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141144"
---
# <a name="how-to-find-an-element-with-a-specific-child-element-c"></a>Jak znaleźć element z określonym elementem podrzędnym (C#)
W tym temacie pokazano, jak znaleźć określony element, który ma element podrzędny o określonej wartości.  
  
## <a name="example"></a>Przykład  
 Przykład znajduje `Test` element, który `CommandLine` ma element podrzędny o wartości "Examp2.EXE".  
  
 W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: Konfiguracja testu (LINQ do XML)](./sample-xml-file-test-configuration-linq-to-xml.md).  
  
```csharp  
XElement root = XElement.Load("TestConfig.xml");  
IEnumerable<XElement> tests =  
    from el in root.Elements("Test")  
    where (string)el.Element("CommandLine") == "Examp2.EXE"  
    select el;  
foreach (XElement el in tests)  
    Console.WriteLine((string)el.Attribute("TestId"));  
```  
  
 Ten kod generuje następujące dane wyjściowe:  
  
```output  
0002  
0006  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono tę samą kwerendę dla języka XML, która znajduje się w obszarze nazw. Aby uzyskać więcej informacji, zobacz [Omówienie przestrzeni nazw (LINQ do XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
 W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: Konfiguracja testu w obszarze nazw](./sample-xml-file-test-configuration-in-a-namespace1.md).  
  
```csharp  
XElement root = XElement.Load("TestConfigInNamespace.xml");  
XNamespace ad = "http://www.adatum.com";  
IEnumerable<XElement> tests =  
    from el in root.Elements(ad + "Test")  
    where (string)el.Element(ad + "CommandLine") == "Examp2.EXE"  
    select el;  
foreach (XElement el in tests)  
    Console.WriteLine((string)el.Attribute("TestId"));  
```  
  
 Ten kod generuje następujące dane wyjściowe:  
  
```output  
0002  
0006  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [Omówienie standardowych operatorów zapytań (C#)](./standard-query-operators-overview.md)
- [Operacje projekcji (C#)](./projection-operations.md)
