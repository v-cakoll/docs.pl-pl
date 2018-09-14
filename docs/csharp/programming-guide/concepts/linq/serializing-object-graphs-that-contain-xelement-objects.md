---
title: Serializowanie wykresów obiektów, które zawierają obiekty XElement (C#)
ms.date: 07/20/2015
ms.assetid: fcbc3951-3cc4-4d0f-9259-e97549ed68f0
ms.openlocfilehash: 2e82165421d31ec234de4806b59565fa675217ef
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45514953"
---
# <a name="serializing-object-graphs-that-contain-xelement-objects-c"></a><span data-ttu-id="20531-102">Serializowanie wykresów obiektów, które zawierają obiekty XElement (C#)</span><span class="sxs-lookup"><span data-stu-id="20531-102">Serializing Object Graphs that Contain XElement Objects (C#)</span></span>
<span data-ttu-id="20531-103">W tym temacie przedstawiono możliwości serializowanie wykresów obiektów, które zawierają odwołania do obiektów tego typu <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="20531-103">This topic introduces the capability of serializing object graphs that contain references to objects of type <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="20531-104">Do funkcji tego typu serializacji, <xref:System.Xml.Linq.XElement> implementuje <xref:System.Xml.Serialization.IXmlSerializable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="20531-104">To facility this type of serializing, <xref:System.Xml.Linq.XElement> implements the <xref:System.Xml.Serialization.IXmlSerializable> interface.</span></span>  
  
 <span data-ttu-id="20531-105">Pamiętaj, że tylko <xref:System.Xml.Linq.XElement> klasa implementuje serializacji.</span><span class="sxs-lookup"><span data-stu-id="20531-105">Note that only the <xref:System.Xml.Linq.XElement> class implements serialization.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="20531-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="20531-106">In This Section</span></span>  
  
|<span data-ttu-id="20531-107">Temat</span><span class="sxs-lookup"><span data-stu-id="20531-107">Topic</span></span>|<span data-ttu-id="20531-108">Opis</span><span class="sxs-lookup"><span data-stu-id="20531-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="20531-109">Instrukcje: serializowanie przy użyciu elementu XmlSerializer (C#)</span><span class="sxs-lookup"><span data-stu-id="20531-109">How to: Serialize Using XmlSerializer (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)|<span data-ttu-id="20531-110">Pokazuje, jak serializowanie przy użyciu <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="20531-110">Demonstrates how to serialize using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>|  
|[<span data-ttu-id="20531-111">Instrukcje: serializowanie przy użyciu elementu DataContractSerializer (C#)</span><span class="sxs-lookup"><span data-stu-id="20531-111">How to: Serialize Using DataContractSerializer (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-serialize-using-datacontractserializer.md)|<span data-ttu-id="20531-112">Pokazuje, jak serializowanie przy użyciu <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="20531-112">Demonstrates how to serialize using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="20531-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="20531-113">See Also</span></span>

- [<span data-ttu-id="20531-114">Zaawansowane LINQ to XML programowania (C#)</span><span class="sxs-lookup"><span data-stu-id="20531-114">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
