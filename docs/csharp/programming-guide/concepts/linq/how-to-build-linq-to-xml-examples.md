---
title: Jak tworzyć przykłady LINQ do XML (C#)
ms.date: 07/20/2015
ms.assetid: e5d18fa1-2704-48fe-a44b-1564f97c9e9c
ms.openlocfilehash: 289a13daed7e3c871156bf50c6fa04c113c0cd13
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141456"
---
# <a name="how-to-build-linq-to-xml-examples-c"></a><span data-ttu-id="fbf54-102">Jak tworzyć przykłady LINQ do XML (C#)</span><span class="sxs-lookup"><span data-stu-id="fbf54-102">How to build LINQ to XML examples (C#)</span></span>
<span data-ttu-id="fbf54-103">Różne fragmenty kodu i przykłady w tej dokumentacji używają klas i typów z różnych przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="fbf54-103">The various snippets and examples in this documentation use classes and types from a variety of namespaces.</span></span> <span data-ttu-id="fbf54-104">Podczas kompilowania kodu C#, należy `using` podać odpowiednie dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="fbf54-104">When compiling C# code, you need to supply appropriate `using` directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fbf54-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="fbf54-105">Example</span></span>  
 <span data-ttu-id="fbf54-106">Poniższy kod zawiera `using` dyrektywy, które przykłady Języka C# wymagają do tworzenia i uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="fbf54-106">The following code contains the `using` directives that the C# examples require to build and run.</span></span> <span data-ttu-id="fbf54-107">Nie `using` wszystkie dyrektywy są wymagane dla każdego przykładu.</span><span class="sxs-lookup"><span data-stu-id="fbf54-107">Not all `using` directives are required for every example.</span></span>  
  
```csharp  
using System;  
using System.Diagnostics;  
using System.Collections;  
using System.Collections.Generic;  
using System.Collections.Specialized;  
using System.Text;  
using System.Linq;  
using System.Xml;  
using System.Xml.Linq;  
using System.Xml.Schema;  
using System.Xml.XPath;  
using System.Xml.Xsl;  
using System.IO;  
using System.Threading;  
using System.Reflection;  
using System.IO.Packaging;  
```  
  
## <a name="see-also"></a><span data-ttu-id="fbf54-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fbf54-108">See also</span></span>

- [<span data-ttu-id="fbf54-109">Omówienie programowania LINQ do XML (C#)</span><span class="sxs-lookup"><span data-stu-id="fbf54-109">LINQ to XML Programming Overview (C#)</span></span>](./linq-to-xml-overview.md)
