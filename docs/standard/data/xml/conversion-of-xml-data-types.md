---
title: Konwersja typów danych XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a2aa99ba-8239-4818-9281-f1d72ee40bde
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 56b5b51848858b7f1240059ca30eb48474650b73
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555131"
---
# <a name="conversion-of-xml-data-types"></a><span data-ttu-id="af6e6-102">Konwersja typów danych XML</span><span class="sxs-lookup"><span data-stu-id="af6e6-102">Conversion of XML Data Types</span></span>
<span data-ttu-id="af6e6-103">Większość metod znaleziony w **obiekt XmlConvert** klasy są używane do konwersji danych pomiędzy ciągami a silnie typizowane formatów.</span><span class="sxs-lookup"><span data-stu-id="af6e6-103">The majority of the methods found in an **XmlConvert** class are used to convert data between strings and strongly-typed formats.</span></span> <span data-ttu-id="af6e6-104">Metody są niezależnie od ustawień regionalnych.</span><span class="sxs-lookup"><span data-stu-id="af6e6-104">Methods are locale independent.</span></span> <span data-ttu-id="af6e6-105">Oznacza to, że nie uwzględniają żadnych ustawień regionalnych podczas wykonywania konwersji.</span><span class="sxs-lookup"><span data-stu-id="af6e6-105">This means that they do not take into account any locale settings when doing conversion.</span></span>  
  
## <a name="reading-string-as-types"></a><span data-ttu-id="af6e6-106">Parametry odczytu jako typy</span><span class="sxs-lookup"><span data-stu-id="af6e6-106">Reading String as types</span></span>  
 <span data-ttu-id="af6e6-107">Poniższy przykład odczytuje parametry i konwertuje ją na **daty/godziny** typu.</span><span class="sxs-lookup"><span data-stu-id="af6e6-107">The following sample reads a string and converts it to a **DateTime** type.</span></span>  
  
 <span data-ttu-id="af6e6-108">Biorąc pod uwagę następujące dane wejściowe XML:</span><span class="sxs-lookup"><span data-stu-id="af6e6-108">Given the following XML input:</span></span>  
  
 <span data-ttu-id="af6e6-109">**Dane wejściowe**</span><span class="sxs-lookup"><span data-stu-id="af6e6-109">**Input**</span></span>  
  
```xml  
<Element>2001-02-27T11:13:23</Element>  
```  
  
 <span data-ttu-id="af6e6-110">Ten kod konwertuje ciąg na **daty/godziny** formatu:</span><span class="sxs-lookup"><span data-stu-id="af6e6-110">This code converts the string to the **DateTime** format:</span></span>  
  
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
  
## <a name="writing-strings-as-types"></a><span data-ttu-id="af6e6-111">Zapisywanie ciągów jako typy</span><span class="sxs-lookup"><span data-stu-id="af6e6-111">Writing Strings as types</span></span>  
 <span data-ttu-id="af6e6-112">Następujące przykładowe odczyty **Int32** i konwertuje ją na ciąg.</span><span class="sxs-lookup"><span data-stu-id="af6e6-112">The following sample reads an **Int32** and converts it to a string.</span></span>  
  
 <span data-ttu-id="af6e6-113">Biorąc pod uwagę następujące dane wejściowe XML:</span><span class="sxs-lookup"><span data-stu-id="af6e6-113">Given the following XML input:</span></span>  
  
 <span data-ttu-id="af6e6-114">**Dane wejściowe**</span><span class="sxs-lookup"><span data-stu-id="af6e6-114">**Input**</span></span>  
  
```xml  
<TestInt32>-2147483648</TestInt32>  
```  
  
 <span data-ttu-id="af6e6-115">Ten kod konwertuje **Int32** do **ciąg**:</span><span class="sxs-lookup"><span data-stu-id="af6e6-115">This code converts the **Int32** into a **String**:</span></span>  
  
```vb  
Dim vInt32 As Int32 = -2147483648  
writer.WriteElementString("TestInt32", XmlConvert.ToString(vInt32))  
```  
  
```csharp  
Int32 vInt32=-2147483648;  
writer.WriteElementString("TestInt32",XmlConvert.ToString(vInt32));  
```  
  
## <a name="see-also"></a><span data-ttu-id="af6e6-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="af6e6-116">See also</span></span>

- [<span data-ttu-id="af6e6-117">Konwertowanie ciągów na typy danych programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="af6e6-117">Converting Strings to .NET Framework Data Types</span></span>](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)
- [<span data-ttu-id="af6e6-118">Konwertowanie typów programu .NET Framework na ciągi</span><span class="sxs-lookup"><span data-stu-id="af6e6-118">Converting .NET Framework Types to Strings</span></span>](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
