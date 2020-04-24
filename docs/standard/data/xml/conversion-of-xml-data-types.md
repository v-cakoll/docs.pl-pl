---
title: Konwersja typów danych XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a2aa99ba-8239-4818-9281-f1d72ee40bde
ms.openlocfilehash: b0cdab8861ca50b40ce2b422fcc1acf16e2f2273
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711093"
---
# <a name="conversion-of-xml-data-types"></a><span data-ttu-id="1ac16-102">Konwersja typów danych XML</span><span class="sxs-lookup"><span data-stu-id="1ac16-102">Conversion of XML Data Types</span></span>
<span data-ttu-id="1ac16-103">Większość metod znalezionych w klasie **XmlConvert** służy do konwertowania danych między ciągami i formatami o jednoznacznie określonym typie.</span><span class="sxs-lookup"><span data-stu-id="1ac16-103">The majority of the methods found in an **XmlConvert** class are used to convert data between strings and strongly-typed formats.</span></span> <span data-ttu-id="1ac16-104">Metody są niezależne od ustawień regionalnych.</span><span class="sxs-lookup"><span data-stu-id="1ac16-104">Methods are locale independent.</span></span> <span data-ttu-id="1ac16-105">Oznacza to, że nie uwzględniają żadnych ustawień regionalnych podczas konwersji.</span><span class="sxs-lookup"><span data-stu-id="1ac16-105">This means that they do not take into account any locale settings when doing conversion.</span></span>  
  
## <a name="reading-string-as-types"></a><span data-ttu-id="1ac16-106">Odczytywanie ciągu jako typów</span><span class="sxs-lookup"><span data-stu-id="1ac16-106">Reading String as types</span></span>  
 <span data-ttu-id="1ac16-107">Poniższy przykład odczytuje ciąg i konwertuje go na typ **DateTime** .</span><span class="sxs-lookup"><span data-stu-id="1ac16-107">The following sample reads a string and converts it to a **DateTime** type.</span></span>  
  
 <span data-ttu-id="1ac16-108">Uwzględniając następujące dane wejściowe XML:</span><span class="sxs-lookup"><span data-stu-id="1ac16-108">Given the following XML input:</span></span>  
  
 <span data-ttu-id="1ac16-109">**Dane wejściowe**</span><span class="sxs-lookup"><span data-stu-id="1ac16-109">**Input**</span></span>  
  
```xml  
<Element>2001-02-27T11:13:23</Element>  
```  
  
 <span data-ttu-id="1ac16-110">Ten kod konwertuje ciąg na format **DateTime** :</span><span class="sxs-lookup"><span data-stu-id="1ac16-110">This code converts the string to the **DateTime** format:</span></span>  
  
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
  
## <a name="writing-strings-as-types"></a><span data-ttu-id="1ac16-111">Pisanie ciągów jako typów</span><span class="sxs-lookup"><span data-stu-id="1ac16-111">Writing Strings as types</span></span>  
 <span data-ttu-id="1ac16-112">Poniższy przykład odczytuje wartość **Int32** i konwertuje ją na ciąg.</span><span class="sxs-lookup"><span data-stu-id="1ac16-112">The following sample reads an **Int32** and converts it to a string.</span></span>  
  
 <span data-ttu-id="1ac16-113">Uwzględniając następujące dane wejściowe XML:</span><span class="sxs-lookup"><span data-stu-id="1ac16-113">Given the following XML input:</span></span>  
  
 <span data-ttu-id="1ac16-114">**Dane wejściowe**</span><span class="sxs-lookup"><span data-stu-id="1ac16-114">**Input**</span></span>  
  
```xml  
<TestInt32>-2147483648</TestInt32>  
```  
  
 <span data-ttu-id="1ac16-115">Ten kod konwertuje wartość **Int32** na **ciąg**:</span><span class="sxs-lookup"><span data-stu-id="1ac16-115">This code converts the **Int32** into a **String**:</span></span>  
  
```vb  
Dim vInt32 As Int32 = -2147483648  
writer.WriteElementString("TestInt32", XmlConvert.ToString(vInt32))  
```  
  
```csharp  
Int32 vInt32=-2147483648;  
writer.WriteElementString("TestInt32",XmlConvert.ToString(vInt32));  
```  
  
## <a name="see-also"></a><span data-ttu-id="1ac16-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1ac16-116">See also</span></span>

- [<span data-ttu-id="1ac16-117">Konwertowanie ciągów na typy danych programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1ac16-117">Converting Strings to .NET Framework Data Types</span></span>](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)
- [<span data-ttu-id="1ac16-118">Konwertowanie typów programu .NET Framework na ciągi</span><span class="sxs-lookup"><span data-stu-id="1ac16-118">Converting .NET Framework Types to Strings</span></span>](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
