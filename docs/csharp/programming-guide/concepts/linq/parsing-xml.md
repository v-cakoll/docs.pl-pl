---
title: Analiza kodu XML (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 7ea83f83-a779-423a-9875-4ea4e51f97fc
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3d262fd2177ac77ab5109362f94cc51d03c9563c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="parsing-xml-c"></a><span data-ttu-id="764ac-102">Analiza kodu XML (C#)</span><span class="sxs-lookup"><span data-stu-id="764ac-102">Parsing XML (C#)</span></span>
<span data-ttu-id="764ac-103">Tematy w tej sekcji opisano sposoby analizowania dokumentów XML.</span><span class="sxs-lookup"><span data-stu-id="764ac-103">The topics in this section describe how to parse XML documents.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="764ac-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="764ac-104">In This Section</span></span>  
  
|<span data-ttu-id="764ac-105">Temat</span><span class="sxs-lookup"><span data-stu-id="764ac-105">Topic</span></span>|<span data-ttu-id="764ac-106">Opis</span><span class="sxs-lookup"><span data-stu-id="764ac-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="764ac-107">Porady: przeanalizować składni ciągu (C#)</span><span class="sxs-lookup"><span data-stu-id="764ac-107">How to: Parse a String (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-parse-a-string.md)|<span data-ttu-id="764ac-108">Pokazuje, jak można przeanalizować parametrów, aby utworzyć drzewo XML.</span><span class="sxs-lookup"><span data-stu-id="764ac-108">Shows how to parse a string to create an XML tree.</span></span>|  
|[<span data-ttu-id="764ac-109">Porady: ładowanie XML z pliku (C#)</span><span class="sxs-lookup"><span data-stu-id="764ac-109">How to: Load XML from a File (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md)|<span data-ttu-id="764ac-110">Pokazuje, jak ładowanie XML z identyfikatorem URI przy użyciu <xref:System.Xml.Linq.XElement.Load%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="764ac-110">Shows how to load XML from a URI using the <xref:System.Xml.Linq.XElement.Load%2A> method.</span></span>|  
|[<span data-ttu-id="764ac-111">Zachowywanie biały znak podczas ładowania lub analiza kodu XML</span><span class="sxs-lookup"><span data-stu-id="764ac-111">Preserving White Space while Loading or Parsing XML</span></span>](../../../../csharp/programming-guide/concepts/linq/preserving-white-space-while-loading-or-parsing-xml1.md)|<span data-ttu-id="764ac-112">Zawiera opis sposobu kontrolowania zachowania biały znak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] podczas ładowania drzew XML.</span><span class="sxs-lookup"><span data-stu-id="764ac-112">Describes how to control the white space behavior of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] while loading XML trees.</span></span>|  
|[<span data-ttu-id="764ac-113">Porady: Catch analizowanie błędów (C#)</span><span class="sxs-lookup"><span data-stu-id="764ac-113">How to: Catch Parsing Errors (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-catch-parsing-errors.md)|<span data-ttu-id="764ac-114">Pokazuje, jak wykryć źle sformułowany lub nieprawidłowy XML.</span><span class="sxs-lookup"><span data-stu-id="764ac-114">Shows how to detect badly formed or invalid XML.</span></span>|  
|[<span data-ttu-id="764ac-115">Porady: Tworzenie drzewa z element XmlReader (C#)</span><span class="sxs-lookup"><span data-stu-id="764ac-115">How to: Create a Tree from an XmlReader (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-create-a-tree-from-an-xmlreader.md)|<span data-ttu-id="764ac-116">Pokazuje, jak utworzyć drzewo XML bezpośrednio z <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="764ac-116">Shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span>|  
|[<span data-ttu-id="764ac-117">Porady: strumienia fragmenty XML z element XmlReader (C#)</span><span class="sxs-lookup"><span data-stu-id="764ac-117">How to: Stream XML Fragments from an XmlReader (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-from-an-xmlreader.md)|<span data-ttu-id="764ac-118">Pokazuje, jak strumienia fragmenty XML przy użyciu <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="764ac-118">Shows how to stream XML fragments by using an <xref:System.Xml.XmlReader>.</span></span><br /><br /> <span data-ttu-id="764ac-119">Jeśli masz przetworzyć arbitralnie dużych plików XML, może nie być możliwe do załadowania całego drzewa XML do pamięci.</span><span class="sxs-lookup"><span data-stu-id="764ac-119">When you have to process arbitrarily large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="764ac-120">Zamiast tego można przesłać strumieniowo fragmenty XML.</span><span class="sxs-lookup"><span data-stu-id="764ac-120">Instead, you can stream XML fragments.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="764ac-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="764ac-121">See Also</span></span>  
 [<span data-ttu-id="764ac-122">Tworzenie drzewa XML (C#)</span><span class="sxs-lookup"><span data-stu-id="764ac-122">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
