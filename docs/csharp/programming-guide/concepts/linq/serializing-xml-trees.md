---
title: Serializacja XML drzew (C#)
ms.date: 07/20/2015
ms.assetid: b3937e54-4ce9-4236-ac96-14e7972aa594
ms.openlocfilehash: 8f372a05bd69b801085cba9d9a3b11ae01841a2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33338354"
---
# <a name="serializing-xml-trees-c"></a><span data-ttu-id="98a32-102">Serializacja XML drzew (C#)</span><span class="sxs-lookup"><span data-stu-id="98a32-102">Serializing XML Trees (C#)</span></span>
<span data-ttu-id="98a32-103">Serializacja XML drzewa oznacza wygenerowaniem kodu XML z drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="98a32-103">Serializing an XML tree means generating XML from the XML tree.</span></span> <span data-ttu-id="98a32-104">Można serializować do pliku, aby konkretną implementację <xref:System.IO.TextWriter> klasy lub konkretną implementację <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="98a32-104">You can serialize to a file, to a concrete implementation of the <xref:System.IO.TextWriter> class, or to a concrete implementation of an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="98a32-105">Można kontrolować różne aspekty serializacji.</span><span class="sxs-lookup"><span data-stu-id="98a32-105">You can control various aspects of serialization.</span></span> <span data-ttu-id="98a32-106">Na przykład można kontrolować, czy zwiększyć wcięcie serializacji XML i czy można zapisać deklaracji XML.</span><span class="sxs-lookup"><span data-stu-id="98a32-106">For example, you can control whether to indent the serialized XML, and whether to write an XML declaration.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="98a32-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="98a32-107">In This Section</span></span>  
  
|<span data-ttu-id="98a32-108">Temat</span><span class="sxs-lookup"><span data-stu-id="98a32-108">Topic</span></span>|<span data-ttu-id="98a32-109">Opis</span><span class="sxs-lookup"><span data-stu-id="98a32-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="98a32-110">Zachowywanie białych znaków podczas serializowania</span><span class="sxs-lookup"><span data-stu-id="98a32-110">Preserving White Space While Serializing</span></span>](../../../../csharp/programming-guide/concepts/linq/preserving-white-space-while-serializing.md)|<span data-ttu-id="98a32-111">Zawiera opis sposobu kontrolowania zachowania biały znak, podczas serializacji XML drzewa.</span><span class="sxs-lookup"><span data-stu-id="98a32-111">Describes how to control white space behavior when you serialize XML trees.</span></span>|  
|[<span data-ttu-id="98a32-112">Serializacja z deklaracją XML (C#)</span><span class="sxs-lookup"><span data-stu-id="98a32-112">Serializing with an XML Declaration (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-with-an-xml-declaration.md)|<span data-ttu-id="98a32-113">Opisuje sposób serializacji drzewa XML, który zawiera deklaracji XML.</span><span class="sxs-lookup"><span data-stu-id="98a32-113">Describes how to serialize an XML tree that includes an XML declaration.</span></span>|  
|[<span data-ttu-id="98a32-114">Serializowanie do plików, elementów TextWriter i elementów XmlWriter</span><span class="sxs-lookup"><span data-stu-id="98a32-114">Serializing to Files, TextWriters, and XmlWriters</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-to-files-textwriters-and-xmlwriters.md)|<span data-ttu-id="98a32-115">Opisuje sposób serializacji dokument <xref:System.IO.File>, <xref:System.IO.TextWriter>, lub <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="98a32-115">Describes how to serialize a document to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>|  
|[<span data-ttu-id="98a32-116">Serializacja na element XmlReader (wywoływanie XSLT) (C#)</span><span class="sxs-lookup"><span data-stu-id="98a32-116">Serializing to an XmlReader (Invoking XSLT) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-to-an-xmlreader-invoking-xslt.md)|<span data-ttu-id="98a32-117">Opisuje sposób tworzenia <xref:System.Xml.XmlReader> inny moduł do odczytu treści drzewo XML, który umożliwia.</span><span class="sxs-lookup"><span data-stu-id="98a32-117">Describes how to create a <xref:System.Xml.XmlReader> that enables another module to read the contents of an XML tree.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="98a32-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="98a32-118">See Also</span></span>  
 [<span data-ttu-id="98a32-119">Przewodnik programowania w języku (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="98a32-119">Programming Guide (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
