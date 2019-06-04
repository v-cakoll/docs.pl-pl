---
title: 'Instrukcje: Tworzenie przykładów LINQ to XML (C#)'
ms.date: 07/20/2015
ms.assetid: e5d18fa1-2704-48fe-a44b-1564f97c9e9c
ms.openlocfilehash: 116f708eb18d642cbe914cea1ea44bd1833f2af6
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486063"
---
# <a name="how-to-build-linq-to-xml-examples-c"></a><span data-ttu-id="452cc-102">Instrukcje: Tworzenie przykładów LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="452cc-102">How to: Build LINQ to XML Examples (C#)</span></span>
<span data-ttu-id="452cc-103">Różne fragmenty kodu i przykłady w niniejszej dokumentacji używać klas i typów z różnych przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="452cc-103">The various snippets and examples in this documentation use classes and types from a variety of namespaces.</span></span> <span data-ttu-id="452cc-104">Podczas kompilowania kodu C#, należy podać odpowiednie `using` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="452cc-104">When compiling C# code, you need to supply appropriate `using` directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="452cc-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="452cc-105">Example</span></span>  
 <span data-ttu-id="452cc-106">Poniższy kod zawiera `using` dyrektyw, które wymagają przykłady języka C#, aby skompilować i uruchomić.</span><span class="sxs-lookup"><span data-stu-id="452cc-106">The following code contains the `using` directives that the C# examples require to build and run.</span></span> <span data-ttu-id="452cc-107">Nie wszystkie `using` dyrektywy są wymagane dla każdego przykładu.</span><span class="sxs-lookup"><span data-stu-id="452cc-107">Not all `using` directives are required for every example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="452cc-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="452cc-108">See also</span></span>

- [<span data-ttu-id="452cc-109">LINQ to XML — przegląd programowania (C#)</span><span class="sxs-lookup"><span data-stu-id="452cc-109">LINQ to XML Programming Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md)
