---
title: Serializowanie wykresów obiektów, które zawierają obiekty XElement (C#)
ms.date: 07/20/2015
ms.assetid: fcbc3951-3cc4-4d0f-9259-e97549ed68f0
ms.openlocfilehash: db7354598fc84c6fa3f8ec4e5b53799030459387
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569144"
---
# <a name="serializing-object-graphs-that-contain-xelement-objects-c"></a><span data-ttu-id="a7eef-102">Serializowanie wykresów obiektów, które zawierają obiekty XElement (C#)</span><span class="sxs-lookup"><span data-stu-id="a7eef-102">Serializing Object Graphs that Contain XElement Objects (C#)</span></span>
<span data-ttu-id="a7eef-103">W tym temacie przedstawiono możliwości serializowanie wykresów obiektów, które zawierają odwołania do obiektów tego typu <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="a7eef-103">This topic introduces the capability of serializing object graphs that contain references to objects of type <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="a7eef-104">Do funkcji tego typu serializacji, <xref:System.Xml.Linq.XElement> implementuje <xref:System.Xml.Serialization.IXmlSerializable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a7eef-104">To facility this type of serializing, <xref:System.Xml.Linq.XElement> implements the <xref:System.Xml.Serialization.IXmlSerializable> interface.</span></span>  
  
 <span data-ttu-id="a7eef-105">Pamiętaj, że tylko <xref:System.Xml.Linq.XElement> klasa implementuje serializacji.</span><span class="sxs-lookup"><span data-stu-id="a7eef-105">Note that only the <xref:System.Xml.Linq.XElement> class implements serialization.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a7eef-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="a7eef-106">In This Section</span></span>  
  
|<span data-ttu-id="a7eef-107">Temat</span><span class="sxs-lookup"><span data-stu-id="a7eef-107">Topic</span></span>|<span data-ttu-id="a7eef-108">Opis</span><span class="sxs-lookup"><span data-stu-id="a7eef-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="a7eef-109">Instrukcje: Serializowanie przy użyciu elementu XmlSerializer (C#)</span><span class="sxs-lookup"><span data-stu-id="a7eef-109">How to: Serialize Using XmlSerializer (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)|<span data-ttu-id="a7eef-110">Pokazuje, jak serializowanie przy użyciu <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="a7eef-110">Demonstrates how to serialize using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>|  
|[<span data-ttu-id="a7eef-111">Instrukcje: Serializowanie przy użyciu elementu DataContractSerializer (C#)</span><span class="sxs-lookup"><span data-stu-id="a7eef-111">How to: Serialize Using DataContractSerializer (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-serialize-using-datacontractserializer.md)|<span data-ttu-id="a7eef-112">Pokazuje, jak serializowanie przy użyciu <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="a7eef-112">Demonstrates how to serialize using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a7eef-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a7eef-113">See also</span></span>

- [<span data-ttu-id="a7eef-114">Zaawansowane LINQ to XML programowania (C#)</span><span class="sxs-lookup"><span data-stu-id="a7eef-114">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
