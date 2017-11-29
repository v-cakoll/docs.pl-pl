---
title: "Porady: znajdowanie Element z elementu podrzędnego określonego (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 00cf5555-374e-4369-bf93-7bd2e7f21db3
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7d4d865b6e412f6f039df3578340db046ca59fa6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-find-an-element-with-a-specific-child-element-c"></a>Porady: znajdowanie Element z elementu podrzędnego określonego (C#)
W tym temacie pokazano, jak można znaleźć określonego elementu, który ma element podrzędny o określonej wartości.  
  
## <a name="example"></a>Przykład  
 W przykładzie są znajdowane `Test` element, który ma `CommandLine` element podrzędny o wartości "Examp2.EXE".  
  
 W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: konfiguracji testu (LINQ do XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).  
  
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
  
```  
0002  
0006  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano tego samego zapytania w formacie XML, który znajduje się w przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [Praca z przestrzeni nazw XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
 W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: Konfiguracja testu w Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-in-a-namespace1.md).  
  
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
  
```  
0002  
0006  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Linq.XElement.Attribute%2A>  
 <xref:System.Xml.Linq.XContainer.Elements%2A>  
 [Podstawowe zapytania (LINQ do XML) (C#)](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)  
 [Operatory standardowe zapytań — omówienie (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Operacje rzutowania (C#)](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)
