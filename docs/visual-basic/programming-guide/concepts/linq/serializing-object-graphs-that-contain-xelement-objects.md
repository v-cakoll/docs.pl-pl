---
title: Serializowanie wykresów obiektów, które zawierają obiekty XElement
ms.date: 07/20/2015
ms.assetid: c0cc5c92-5ca3-44b1-98dd-371601df721b
ms.openlocfilehash: 5390cfaa77229b60af6388fc643544c539c15fe9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360686"
---
# <a name="serializing-object-graphs-that-contain-xelement-objects-visual-basic"></a><span data-ttu-id="46df9-102">Serializacja grafów obiektów, które zawierają obiekty XElement (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="46df9-102">Serializing Object Graphs that Contain XElement Objects (Visual Basic)</span></span>
<span data-ttu-id="46df9-103">W tym temacie przedstawiono możliwości serializowania grafów obiektów, które zawierają odwołania do obiektów typu <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="46df9-103">This topic introduces the capability of serializing object graphs that contain references to objects of type <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="46df9-104">Aby zastanowić się nad tym typem serializacji, <xref:System.Xml.Linq.XElement> implementuje <xref:System.Xml.Serialization.IXmlSerializable> interfejs.</span><span class="sxs-lookup"><span data-stu-id="46df9-104">To facility this type of serializing, <xref:System.Xml.Linq.XElement> implements the <xref:System.Xml.Serialization.IXmlSerializable> interface.</span></span>  
  
 <span data-ttu-id="46df9-105">Należy zauważyć, że tylko <xref:System.Xml.Linq.XElement> Klasa implementuje serializacji.</span><span class="sxs-lookup"><span data-stu-id="46df9-105">Note that only the <xref:System.Xml.Linq.XElement> class implements serialization.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="46df9-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="46df9-106">In This Section</span></span>  
  
|<span data-ttu-id="46df9-107">Temat</span><span class="sxs-lookup"><span data-stu-id="46df9-107">Topic</span></span>|<span data-ttu-id="46df9-108">Opis</span><span class="sxs-lookup"><span data-stu-id="46df9-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="46df9-109">Instrukcje: Serializowanie przy użyciu elementu XmlSerializer (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="46df9-109">How to: Serialize Using XmlSerializer (Visual Basic)</span></span>](how-to-serialize-using-xmlserializer.md)|<span data-ttu-id="46df9-110">Pokazuje, jak serializować przy użyciu <xref:System.Xml.Serialization.XmlSerializer> .</span><span class="sxs-lookup"><span data-stu-id="46df9-110">Demonstrates how to serialize using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>|  
|[<span data-ttu-id="46df9-111">Instrukcje: Serializowanie przy użyciu obiektu DataContractSerializer (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="46df9-111">How to: Serialize Using DataContractSerializer (Visual Basic)</span></span>](how-to-serialize-using-datacontractserializer.md)|<span data-ttu-id="46df9-112">Pokazuje, jak serializować przy użyciu <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="46df9-112">Demonstrates how to serialize using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="46df9-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="46df9-113">See also</span></span>

- [<span data-ttu-id="46df9-114">Zaawansowane programowanie LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="46df9-114">Advanced LINQ to XML Programming (Visual Basic)</span></span>](advanced-linq-to-xml-programming.md)
