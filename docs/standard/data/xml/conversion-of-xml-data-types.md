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
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d18b69c2d5baeac77cbdf45bebd6f0c9d5c94d9f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="conversion-of-xml-data-types"></a><span data-ttu-id="cb0a5-102">Konwersja typów danych XML</span><span class="sxs-lookup"><span data-stu-id="cb0a5-102">Conversion of XML Data Types</span></span>
<span data-ttu-id="cb0a5-103">Znaleziono większości metod w **obiekt XmlConvert** klasy służą do konwertowania danych pomiędzy ciągami a jednoznacznie formatów.</span><span class="sxs-lookup"><span data-stu-id="cb0a5-103">The majority of the methods found in an **XmlConvert** class are used to convert data between strings and strongly-typed formats.</span></span> <span data-ttu-id="cb0a5-104">Metody są niezależnie od ustawień regionalnych.</span><span class="sxs-lookup"><span data-stu-id="cb0a5-104">Methods are locale independent.</span></span> <span data-ttu-id="cb0a5-105">Oznacza to, że nie uwzględniają wszystkie ustawienia regionalne podczas konwersji.</span><span class="sxs-lookup"><span data-stu-id="cb0a5-105">This means that they do not take into account any locale settings when doing conversion.</span></span>  
  
## <a name="reading-string-as-types"></a><span data-ttu-id="cb0a5-106">Parametry odczytu jako typy</span><span class="sxs-lookup"><span data-stu-id="cb0a5-106">Reading String as types</span></span>  
 <span data-ttu-id="cb0a5-107">Poniższy przykład odczytuje ciąg i konwertuje ją na **DateTime** typu.</span><span class="sxs-lookup"><span data-stu-id="cb0a5-107">The following sample reads a string and converts it to a **DateTime** type.</span></span>  
  
 <span data-ttu-id="cb0a5-108">Należy podać następujące dane wejściowe XML:</span><span class="sxs-lookup"><span data-stu-id="cb0a5-108">Given the following XML input:</span></span>  
  
 <span data-ttu-id="cb0a5-109">**Dane wejściowe**</span><span class="sxs-lookup"><span data-stu-id="cb0a5-109">**Input**</span></span>  
  
```xml  
<Element>2001-02-27T11:13:23</Element>  
```  
  
 <span data-ttu-id="cb0a5-110">Ten kod konwertuje ciąg na **DateTime** format:</span><span class="sxs-lookup"><span data-stu-id="cb0a5-110">This code converts the string to the **DateTime** format:</span></span>  
  
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
  
## <a name="writing-strings-as-types"></a><span data-ttu-id="cb0a5-111">Zapisywanie ciągów jako typy</span><span class="sxs-lookup"><span data-stu-id="cb0a5-111">Writing Strings as types</span></span>  
 <span data-ttu-id="cb0a5-112">Następujące przykładowe odczyty **Int32** i konwertuje ją na ciąg.</span><span class="sxs-lookup"><span data-stu-id="cb0a5-112">The following sample reads an **Int32** and converts it to a string.</span></span>  
  
 <span data-ttu-id="cb0a5-113">Należy podać następujące dane wejściowe XML:</span><span class="sxs-lookup"><span data-stu-id="cb0a5-113">Given the following XML input:</span></span>  
  
 <span data-ttu-id="cb0a5-114">**Dane wejściowe**</span><span class="sxs-lookup"><span data-stu-id="cb0a5-114">**Input**</span></span>  
  
```xml  
<TestInt32>-2147483648</TestInt32>  
```  
  
 <span data-ttu-id="cb0a5-115">Ten kod konwertuje **Int32** do **ciąg**:</span><span class="sxs-lookup"><span data-stu-id="cb0a5-115">This code converts the **Int32** into a **String**:</span></span>  
  
```vb  
Dim vInt32 As Int32 = -2147483648  
writer.WriteElementString("TestInt32", XmlConvert.ToString(vInt32))  
```  
  
```csharp  
Int32 vInt32=-2147483648;  
writer.WriteElementString("TestInt32",XmlConvert.ToString(vInt32));  
```  
  
## <a name="see-also"></a><span data-ttu-id="cb0a5-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cb0a5-116">See Also</span></span>  
 [<span data-ttu-id="cb0a5-117">Konwertowanie ciągów na typy danych programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="cb0a5-117">Converting Strings to .NET Framework Data Types</span></span>](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)  
 [<span data-ttu-id="cb0a5-118">Konwertowanie typów programu .NET Framework na ciągi</span><span class="sxs-lookup"><span data-stu-id="cb0a5-118">Converting .NET Framework Types to Strings</span></span>](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
