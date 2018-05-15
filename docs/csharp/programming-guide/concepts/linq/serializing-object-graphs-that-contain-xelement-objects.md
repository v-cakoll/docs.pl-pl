---
title: Serializacja wykresów obiektów, które zawierają obiekty klasy XElement (C#)
ms.date: 07/20/2015
ms.assetid: fcbc3951-3cc4-4d0f-9259-e97549ed68f0
ms.openlocfilehash: f51a026642563e1c1690d9a49220aae462840211
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="serializing-object-graphs-that-contain-xelement-objects-c"></a><span data-ttu-id="019e7-102">Serializacja wykresów obiektów, które zawierają obiekty klasy XElement (C#)</span><span class="sxs-lookup"><span data-stu-id="019e7-102">Serializing Object Graphs that Contain XElement Objects (C#)</span></span>
<span data-ttu-id="019e7-103">W tym temacie przedstawiono możliwość serializowania wykresów obiektów, które zawierają odwołania do obiektów typu <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="019e7-103">This topic introduces the capability of serializing object graphs that contain references to objects of type <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="019e7-104">Obiekcie tego typu serializacji, <xref:System.Xml.Linq.XElement> implementuje <xref:System.Xml.Serialization.IXmlSerializable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="019e7-104">To facility this type of serializing, <xref:System.Xml.Linq.XElement> implements the <xref:System.Xml.Serialization.IXmlSerializable> interface.</span></span>  
  
 <span data-ttu-id="019e7-105">Uwaga tylko <xref:System.Xml.Linq.XElement> klasa implementuje serializacji.</span><span class="sxs-lookup"><span data-stu-id="019e7-105">Note that only the <xref:System.Xml.Linq.XElement> class implements serialization.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="019e7-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="019e7-106">In This Section</span></span>  
  
|<span data-ttu-id="019e7-107">Temat</span><span class="sxs-lookup"><span data-stu-id="019e7-107">Topic</span></span>|<span data-ttu-id="019e7-108">Opis</span><span class="sxs-lookup"><span data-stu-id="019e7-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="019e7-109">Porady: serializacji przy użyciu elementu XmlSerializer (C#)</span><span class="sxs-lookup"><span data-stu-id="019e7-109">How to: Serialize Using XmlSerializer (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)|<span data-ttu-id="019e7-110">Pokazuje, jak do serializacji przy użyciu <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="019e7-110">Demonstrates how to serialize using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>|  
|[<span data-ttu-id="019e7-111">Porady: serializacji przy użyciu elementu DataContractSerializer (C#)</span><span class="sxs-lookup"><span data-stu-id="019e7-111">How to: Serialize Using DataContractSerializer (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-serialize-using-datacontractserializer.md)|<span data-ttu-id="019e7-112">Pokazuje, jak do serializacji przy użyciu <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="019e7-112">Demonstrates how to serialize using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="019e7-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="019e7-113">See Also</span></span>  
 [<span data-ttu-id="019e7-114">Zaawansowane LINQ do XML programowania (C#)</span><span class="sxs-lookup"><span data-stu-id="019e7-114">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
