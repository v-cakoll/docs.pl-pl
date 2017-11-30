---
title: "Serializacja wykresów obiektów, które zawierają obiekty klasy XElement (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: fcbc3951-3cc4-4d0f-9259-e97549ed68f0
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8b7da4429360beb20fa304b592020d48666fe732
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="serializing-object-graphs-that-contain-xelement-objects-c"></a><span data-ttu-id="cf02c-102">Serializacja wykresów obiektów, które zawierają obiekty klasy XElement (C#)</span><span class="sxs-lookup"><span data-stu-id="cf02c-102">Serializing Object Graphs that Contain XElement Objects (C#)</span></span>
<span data-ttu-id="cf02c-103">W tym temacie przedstawiono możliwość serializowania wykresów obiektów, które zawierają odwołania do obiektów typu <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="cf02c-103">This topic introduces the capability of serializing object graphs that contain references to objects of type <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="cf02c-104">Obiekcie tego typu serializacji, <xref:System.Xml.Linq.XElement> implementuje <xref:System.Xml.Serialization.IXmlSerializable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="cf02c-104">To facility this type of serializing, <xref:System.Xml.Linq.XElement> implements the <xref:System.Xml.Serialization.IXmlSerializable> interface.</span></span>  
  
 <span data-ttu-id="cf02c-105">Uwaga tylko <xref:System.Xml.Linq.XElement> klasa implementuje serializacji.</span><span class="sxs-lookup"><span data-stu-id="cf02c-105">Note that only the <xref:System.Xml.Linq.XElement> class implements serialization.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cf02c-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="cf02c-106">In This Section</span></span>  
  
|<span data-ttu-id="cf02c-107">Temat</span><span class="sxs-lookup"><span data-stu-id="cf02c-107">Topic</span></span>|<span data-ttu-id="cf02c-108">Opis</span><span class="sxs-lookup"><span data-stu-id="cf02c-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="cf02c-109">Porady: serializacji przy użyciu elementu XmlSerializer (C#)</span><span class="sxs-lookup"><span data-stu-id="cf02c-109">How to: Serialize Using XmlSerializer (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)|<span data-ttu-id="cf02c-110">Pokazuje, jak do serializacji przy użyciu <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="cf02c-110">Demonstrates how to serialize using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>|  
|[<span data-ttu-id="cf02c-111">Porady: serializacji przy użyciu elementu DataContractSerializer (C#)</span><span class="sxs-lookup"><span data-stu-id="cf02c-111">How to: Serialize Using DataContractSerializer (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-serialize-using-datacontractserializer.md)|<span data-ttu-id="cf02c-112">Pokazuje, jak do serializacji przy użyciu <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="cf02c-112">Demonstrates how to serialize using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cf02c-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cf02c-113">See Also</span></span>  
 [<span data-ttu-id="cf02c-114">Zaawansowane LINQ do XML programowania (C#)</span><span class="sxs-lookup"><span data-stu-id="cf02c-114">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
