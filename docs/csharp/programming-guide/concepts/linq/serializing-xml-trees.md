---
title: Serializowanie drzew XML (C#)
ms.date: 07/20/2015
ms.assetid: b3937e54-4ce9-4236-ac96-14e7972aa594
ms.openlocfilehash: a1c39c4c85cbd01fa7c3f3f99f2dfae49e3721d9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61711736"
---
# <a name="serializing-xml-trees-c"></a><span data-ttu-id="76d0a-102">Serializowanie drzew XML (C#)</span><span class="sxs-lookup"><span data-stu-id="76d0a-102">Serializing XML Trees (C#)</span></span>
<span data-ttu-id="76d0a-103">Serializacji drzewa XML oznacza, że Generowanie XML z drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="76d0a-103">Serializing an XML tree means generating XML from the XML tree.</span></span> <span data-ttu-id="76d0a-104">Może wykonywać serializację do pliku, aby konkretną implementację <xref:System.IO.TextWriter> klasy, lub na konkretną implementację <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="76d0a-104">You can serialize to a file, to a concrete implementation of the <xref:System.IO.TextWriter> class, or to a concrete implementation of an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="76d0a-105">Można kontrolować różne aspekty serializacji.</span><span class="sxs-lookup"><span data-stu-id="76d0a-105">You can control various aspects of serialization.</span></span> <span data-ttu-id="76d0a-106">Na przykład można kontrolować, czy zwiększyć wcięcie serializacji XML i można zapisać deklaracji XML.</span><span class="sxs-lookup"><span data-stu-id="76d0a-106">For example, you can control whether to indent the serialized XML, and whether to write an XML declaration.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="76d0a-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="76d0a-107">In This Section</span></span>  
  
|<span data-ttu-id="76d0a-108">Temat</span><span class="sxs-lookup"><span data-stu-id="76d0a-108">Topic</span></span>|<span data-ttu-id="76d0a-109">Opis</span><span class="sxs-lookup"><span data-stu-id="76d0a-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="76d0a-110">Zachowywanie białych znaków podczas serializowania</span><span class="sxs-lookup"><span data-stu-id="76d0a-110">Preserving White Space While Serializing</span></span>](../../../../csharp/programming-guide/concepts/linq/preserving-white-space-while-serializing.md)|<span data-ttu-id="76d0a-111">Zawiera opis sposobu kontrolowania zachowania biały znak, gdy serializowanie drzew XML.</span><span class="sxs-lookup"><span data-stu-id="76d0a-111">Describes how to control white space behavior when you serialize XML trees.</span></span>|  
|[<span data-ttu-id="76d0a-112">Serializowanie przy użyciu deklaracji XML (C#)</span><span class="sxs-lookup"><span data-stu-id="76d0a-112">Serializing with an XML Declaration (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-with-an-xml-declaration.md)|<span data-ttu-id="76d0a-113">W tym artykule opisano, jak do serializacji drzewa XML, który zawiera deklaracji XML.</span><span class="sxs-lookup"><span data-stu-id="76d0a-113">Describes how to serialize an XML tree that includes an XML declaration.</span></span>|  
|[<span data-ttu-id="76d0a-114">Serializowanie do plików, elementów TextWriter i elementów XmlWriter</span><span class="sxs-lookup"><span data-stu-id="76d0a-114">Serializing to Files, TextWriters, and XmlWriters</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-to-files-textwriters-and-xmlwriters.md)|<span data-ttu-id="76d0a-115">W tym artykule opisano jak do serializacji dokument <xref:System.IO.File>, <xref:System.IO.TextWriter>, lub <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="76d0a-115">Describes how to serialize a document to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>|  
|[<span data-ttu-id="76d0a-116">Serializowanie do elementu XmlReader (wywoływanie XSLT) (C#)</span><span class="sxs-lookup"><span data-stu-id="76d0a-116">Serializing to an XmlReader (Invoking XSLT) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-to-an-xmlreader-invoking-xslt.md)|<span data-ttu-id="76d0a-117">W tym artykule opisano sposób tworzenia <xref:System.Xml.XmlReader> inny moduł odczytać zawartość drzewa XML, który umożliwia.</span><span class="sxs-lookup"><span data-stu-id="76d0a-117">Describes how to create a <xref:System.Xml.XmlReader> that enables another module to read the contents of an XML tree.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="76d0a-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="76d0a-118">See also</span></span>

- [<span data-ttu-id="76d0a-119">Przewodnik programowania (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="76d0a-119">Programming Guide (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
