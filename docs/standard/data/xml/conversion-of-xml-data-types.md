---
title: "Konwersja typów danych XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: a2aa99ba-8239-4818-9281-f1d72ee40bde
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d2f5f5d27b3d21ff12f5eea7613e80e73c5b6597
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="conversion-of-xml-data-types"></a><span data-ttu-id="36ea7-102">Konwersja typów danych XML</span><span class="sxs-lookup"><span data-stu-id="36ea7-102">Conversion of XML Data Types</span></span>
<span data-ttu-id="36ea7-103">Znaleziono większości metod w **obiekt XmlConvert** klasy służą do konwertowania danych pomiędzy ciągami a jednoznacznie formatów.</span><span class="sxs-lookup"><span data-stu-id="36ea7-103">The majority of the methods found in an **XmlConvert** class are used to convert data between strings and strongly-typed formats.</span></span> <span data-ttu-id="36ea7-104">Metody są niezależnie od ustawień regionalnych.</span><span class="sxs-lookup"><span data-stu-id="36ea7-104">Methods are locale independent.</span></span> <span data-ttu-id="36ea7-105">Oznacza to, że nie uwzględniają wszystkie ustawienia regionalne podczas konwersji.</span><span class="sxs-lookup"><span data-stu-id="36ea7-105">This means that they do not take into account any locale settings when doing conversion.</span></span>  
  
## <a name="reading-string-as-types"></a><span data-ttu-id="36ea7-106">Parametry odczytu jako typy</span><span class="sxs-lookup"><span data-stu-id="36ea7-106">Reading String as types</span></span>  
 <span data-ttu-id="36ea7-107">Poniższy przykład odczytuje ciąg i konwertuje ją na **DateTime** typu.</span><span class="sxs-lookup"><span data-stu-id="36ea7-107">The following sample reads a string and converts it to a **DateTime** type.</span></span>  
  
 <span data-ttu-id="36ea7-108">Należy podać następujące dane wejściowe XML:</span><span class="sxs-lookup"><span data-stu-id="36ea7-108">Given the following XML input:</span></span>  
  
 <span data-ttu-id="36ea7-109">**Dane wejściowe**</span><span class="sxs-lookup"><span data-stu-id="36ea7-109">**Input**</span></span>  
  
```xml  
<Element>2001-02-27T11:13:23</Element>  
```  
  
 <span data-ttu-id="36ea7-110">Ten kod konwertuje ciąg na **DateTime** format:</span><span class="sxs-lookup"><span data-stu-id="36ea7-110">This code converts the string to the **DateTime** format:</span></span>  
  
```vb  
reader.ReadStartElement()  
Dim vDateTime As DateTime = XmlConvert.ToDateTime(reader.ReadString())  
Console.WriteLine(vDateTime)  
```  
  
```csharp  
reader.ReadStartElement();  
DateTime vDateTime = XmlConvert.ToDateTime(reader.ReadString());  
Console.WriteLine(vDateTime);  
```  
  
## <a name="writing-strings-as-types"></a><span data-ttu-id="36ea7-111">Zapisywanie ciągów jako typy</span><span class="sxs-lookup"><span data-stu-id="36ea7-111">Writing Strings as types</span></span>  
 <span data-ttu-id="36ea7-112">Następujące przykładowe odczyty **Int32** i konwertuje ją na ciąg.</span><span class="sxs-lookup"><span data-stu-id="36ea7-112">The following sample reads an **Int32** and converts it to a string.</span></span>  
  
 <span data-ttu-id="36ea7-113">Należy podać następujące dane wejściowe XML:</span><span class="sxs-lookup"><span data-stu-id="36ea7-113">Given the following XML input:</span></span>  
  
 <span data-ttu-id="36ea7-114">**Dane wejściowe**</span><span class="sxs-lookup"><span data-stu-id="36ea7-114">**Input**</span></span>  
  
```xml  
<TestInt32>-2147483648</TestInt32>  
```  
  
 <span data-ttu-id="36ea7-115">Ten kod konwertuje **Int32** do **ciąg**:</span><span class="sxs-lookup"><span data-stu-id="36ea7-115">This code converts the **Int32** into a **String**:</span></span>  
  
```vb  
Dim vInt32 As Int32 = -2147483648  
writer.WriteElementString("TestInt32", XmlConvert.ToString(vInt32))  
```  
  
```csharp  
Int32 vInt32=-2147483648;  
writer.WriteElementString("TestInt32",XmlConvert.ToString(vInt32));  
```  
  
## <a name="see-also"></a><span data-ttu-id="36ea7-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="36ea7-116">See Also</span></span>  
 [<span data-ttu-id="36ea7-117">Konwertowanie ciągów na typy danych programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="36ea7-117">Converting Strings to .NET Framework Data Types</span></span>](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)  
 [<span data-ttu-id="36ea7-118">Konwertowanie typów programu .NET Framework na ciągi</span><span class="sxs-lookup"><span data-stu-id="36ea7-118">Converting .NET Framework Types to Strings</span></span>](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
