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
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2018
ms.locfileid: "45664582"
---
# <a name="conversion-of-xml-data-types"></a><span data-ttu-id="3f226-102">Konwersja typów danych XML</span><span class="sxs-lookup"><span data-stu-id="3f226-102">Conversion of XML Data Types</span></span>
<span data-ttu-id="3f226-103">Większość metod znaleziony w **obiekt XmlConvert** klasy są używane do konwersji danych pomiędzy ciągami a silnie typizowane formatów.</span><span class="sxs-lookup"><span data-stu-id="3f226-103">The majority of the methods found in an **XmlConvert** class are used to convert data between strings and strongly-typed formats.</span></span> <span data-ttu-id="3f226-104">Metody są niezależnie od ustawień regionalnych.</span><span class="sxs-lookup"><span data-stu-id="3f226-104">Methods are locale independent.</span></span> <span data-ttu-id="3f226-105">Oznacza to, że nie uwzględniają żadnych ustawień regionalnych podczas wykonywania konwersji.</span><span class="sxs-lookup"><span data-stu-id="3f226-105">This means that they do not take into account any locale settings when doing conversion.</span></span>  
  
## <a name="reading-string-as-types"></a><span data-ttu-id="3f226-106">Parametry odczytu jako typy</span><span class="sxs-lookup"><span data-stu-id="3f226-106">Reading String as types</span></span>  
 <span data-ttu-id="3f226-107">Poniższy przykład odczytuje parametry i konwertuje ją na **daty/godziny** typu.</span><span class="sxs-lookup"><span data-stu-id="3f226-107">The following sample reads a string and converts it to a **DateTime** type.</span></span>  
  
 <span data-ttu-id="3f226-108">Biorąc pod uwagę następujące dane wejściowe XML:</span><span class="sxs-lookup"><span data-stu-id="3f226-108">Given the following XML input:</span></span>  
  
 <span data-ttu-id="3f226-109">**Dane wejściowe**</span><span class="sxs-lookup"><span data-stu-id="3f226-109">**Input**</span></span>  
  
```xml  
<Element>2001-02-27T11:13:23</Element>  
```  
  
 <span data-ttu-id="3f226-110">Ten kod konwertuje ciąg na **daty/godziny** formatu:</span><span class="sxs-lookup"><span data-stu-id="3f226-110">This code converts the string to the **DateTime** format:</span></span>  
  
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
  
## <a name="writing-strings-as-types"></a><span data-ttu-id="3f226-111">Zapisywanie ciągów jako typy</span><span class="sxs-lookup"><span data-stu-id="3f226-111">Writing Strings as types</span></span>  
 <span data-ttu-id="3f226-112">Następujące przykładowe odczyty **Int32** i konwertuje ją na ciąg.</span><span class="sxs-lookup"><span data-stu-id="3f226-112">The following sample reads an **Int32** and converts it to a string.</span></span>  
  
 <span data-ttu-id="3f226-113">Biorąc pod uwagę następujące dane wejściowe XML:</span><span class="sxs-lookup"><span data-stu-id="3f226-113">Given the following XML input:</span></span>  
  
 <span data-ttu-id="3f226-114">**Dane wejściowe**</span><span class="sxs-lookup"><span data-stu-id="3f226-114">**Input**</span></span>  
  
```xml  
<TestInt32>-2147483648</TestInt32>  
```  
  
 <span data-ttu-id="3f226-115">Ten kod konwertuje **Int32** do **ciąg**:</span><span class="sxs-lookup"><span data-stu-id="3f226-115">This code converts the **Int32** into a **String**:</span></span>  
  
```vb  
Dim vInt32 As Int32 = -2147483648  
writer.WriteElementString("TestInt32", XmlConvert.ToString(vInt32))  
```  
  
```csharp  
Int32 vInt32=-2147483648;  
writer.WriteElementString("TestInt32",XmlConvert.ToString(vInt32));  
```  
  
## <a name="see-also"></a><span data-ttu-id="3f226-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3f226-116">See also</span></span>

- [<span data-ttu-id="3f226-117">Konwertowanie ciągów na typy danych programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3f226-117">Converting Strings to .NET Framework Data Types</span></span>](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)  
- [<span data-ttu-id="3f226-118">Konwertowanie typów programu .NET Framework na ciągi</span><span class="sxs-lookup"><span data-stu-id="3f226-118">Converting .NET Framework Types to Strings</span></span>](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
