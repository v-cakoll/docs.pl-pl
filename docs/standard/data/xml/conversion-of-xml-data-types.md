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
ms.openlocfilehash: cec2b85c55871c8a21a74e79cfcdd041fa063bec
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43866627"
---
# <a name="conversion-of-xml-data-types"></a><span data-ttu-id="41b41-102">Konwersja typów danych XML</span><span class="sxs-lookup"><span data-stu-id="41b41-102">Conversion of XML Data Types</span></span>
<span data-ttu-id="41b41-103">Większość metod znaleziony w **obiekt XmlConvert** klasy są używane do konwersji danych pomiędzy ciągami a silnie typizowane formatów.</span><span class="sxs-lookup"><span data-stu-id="41b41-103">The majority of the methods found in an **XmlConvert** class are used to convert data between strings and strongly-typed formats.</span></span> <span data-ttu-id="41b41-104">Metody są niezależnie od ustawień regionalnych.</span><span class="sxs-lookup"><span data-stu-id="41b41-104">Methods are locale independent.</span></span> <span data-ttu-id="41b41-105">Oznacza to, że nie uwzględniają żadnych ustawień regionalnych podczas wykonywania konwersji.</span><span class="sxs-lookup"><span data-stu-id="41b41-105">This means that they do not take into account any locale settings when doing conversion.</span></span>  
  
## <a name="reading-string-as-types"></a><span data-ttu-id="41b41-106">Parametry odczytu jako typy</span><span class="sxs-lookup"><span data-stu-id="41b41-106">Reading String as types</span></span>  
 <span data-ttu-id="41b41-107">Poniższy przykład odczytuje parametry i konwertuje ją na **daty/godziny** typu.</span><span class="sxs-lookup"><span data-stu-id="41b41-107">The following sample reads a string and converts it to a **DateTime** type.</span></span>  
  
 <span data-ttu-id="41b41-108">Biorąc pod uwagę następujące dane wejściowe XML:</span><span class="sxs-lookup"><span data-stu-id="41b41-108">Given the following XML input:</span></span>  
  
 <span data-ttu-id="41b41-109">**Dane wejściowe**</span><span class="sxs-lookup"><span data-stu-id="41b41-109">**Input**</span></span>  
  
```xml  
<Element>2001-02-27T11:13:23</Element>  
```  
  
 <span data-ttu-id="41b41-110">Ten kod konwertuje ciąg na **daty/godziny** formatu:</span><span class="sxs-lookup"><span data-stu-id="41b41-110">This code converts the string to the **DateTime** format:</span></span>  
  
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
  
## <a name="writing-strings-as-types"></a><span data-ttu-id="41b41-111">Zapisywanie ciągów jako typy</span><span class="sxs-lookup"><span data-stu-id="41b41-111">Writing Strings as types</span></span>  
 <span data-ttu-id="41b41-112">Następujące przykładowe odczyty **Int32** i konwertuje ją na ciąg.</span><span class="sxs-lookup"><span data-stu-id="41b41-112">The following sample reads an **Int32** and converts it to a string.</span></span>  
  
 <span data-ttu-id="41b41-113">Biorąc pod uwagę następujące dane wejściowe XML:</span><span class="sxs-lookup"><span data-stu-id="41b41-113">Given the following XML input:</span></span>  
  
 <span data-ttu-id="41b41-114">**Dane wejściowe**</span><span class="sxs-lookup"><span data-stu-id="41b41-114">**Input**</span></span>  
  
```xml  
<TestInt32>-2147483648</TestInt32>  
```  
  
 <span data-ttu-id="41b41-115">Ten kod konwertuje **Int32** do **ciąg**:</span><span class="sxs-lookup"><span data-stu-id="41b41-115">This code converts the **Int32** into a **String**:</span></span>  
  
```vb  
Dim vInt32 As Int32 = -2147483648  
writer.WriteElementString("TestInt32", XmlConvert.ToString(vInt32))  
```  
  
```csharp  
Int32 vInt32=-2147483648;  
writer.WriteElementString("TestInt32",XmlConvert.ToString(vInt32));  
```  
  
## <a name="see-also"></a><span data-ttu-id="41b41-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="41b41-116">See also</span></span>

- [<span data-ttu-id="41b41-117">Konwertowanie ciągów na typy danych programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="41b41-117">Converting Strings to .NET Framework Data Types</span></span>](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)  
- [<span data-ttu-id="41b41-118">Konwertowanie typów programu .NET Framework na ciągi</span><span class="sxs-lookup"><span data-stu-id="41b41-118">Converting .NET Framework Types to Strings</span></span>](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
