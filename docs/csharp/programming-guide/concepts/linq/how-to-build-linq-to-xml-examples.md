---
title: Jak kompilować przykłady LINQ to XML (C#)
description: Należy podać odpowiednie dyrektywy dotyczące użycia wymagane do skompilowania języka C#, aby uruchomić dostarczone fragmenty kodu i przykłady LINQ to XML.
ms.date: 07/20/2015
ms.assetid: e5d18fa1-2704-48fe-a44b-1564f97c9e9c
ms.openlocfilehash: f54944dcb68e1fd7d00f37c9c5381f345efc820e
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103591"
---
# <a name="how-to-build-linq-to-xml-examples-c"></a><span data-ttu-id="90c00-103">Jak kompilować przykłady LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="90c00-103">How to build LINQ to XML examples (C#)</span></span>
<span data-ttu-id="90c00-104">Różne fragmenty kodu i przykłady w tej dokumentacji używają klas i typów z różnych przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="90c00-104">The various snippets and examples in this documentation use classes and types from a variety of namespaces.</span></span> <span data-ttu-id="90c00-105">Podczas kompilowania kodu w języku C# należy dostarczyć odpowiednie `using` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="90c00-105">When compiling C# code, you need to supply appropriate `using` directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="90c00-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="90c00-106">Example</span></span>  
 <span data-ttu-id="90c00-107">Poniższy kod zawiera `using` dyrektywy, których przykłady w języku C# wymagają do skompilowania i uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="90c00-107">The following code contains the `using` directives that the C# examples require to build and run.</span></span> <span data-ttu-id="90c00-108">Nie wszystkie `using` dyrektywy są wymagane dla każdego przykładu.</span><span class="sxs-lookup"><span data-stu-id="90c00-108">Not all `using` directives are required for every example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="90c00-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="90c00-109">See also</span></span>

- [<span data-ttu-id="90c00-110">Omówienie programowania LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="90c00-110">LINQ to XML Programming Overview (C#)</span></span>](./linq-to-xml-overview.md)
