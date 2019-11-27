---
title: Serializowanie wykresów obiektów, które zawierają obiekty XElement
ms.date: 07/20/2015
ms.assetid: c0cc5c92-5ca3-44b1-98dd-371601df721b
ms.openlocfilehash: caf594fc23eee15cc79cfad47e62a057518f62dd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349373"
---
# <a name="serializing-object-graphs-that-contain-xelement-objects-visual-basic"></a><span data-ttu-id="1dbfe-102">Serializacja grafów obiektów, które zawierają obiekty XElement (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1dbfe-102">Serializing Object Graphs that Contain XElement Objects (Visual Basic)</span></span>
<span data-ttu-id="1dbfe-103">W tym temacie przedstawiono możliwości serializowania grafów obiektów, które zawierają odwołania do obiektów typu <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="1dbfe-103">This topic introduces the capability of serializing object graphs that contain references to objects of type <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="1dbfe-104">Aby obsłużyć ten typ serializacji, <xref:System.Xml.Linq.XElement> implementuje interfejs <xref:System.Xml.Serialization.IXmlSerializable>.</span><span class="sxs-lookup"><span data-stu-id="1dbfe-104">To facility this type of serializing, <xref:System.Xml.Linq.XElement> implements the <xref:System.Xml.Serialization.IXmlSerializable> interface.</span></span>  
  
 <span data-ttu-id="1dbfe-105">Należy zauważyć, że tylko Klasa <xref:System.Xml.Linq.XElement> implementuje serializacji.</span><span class="sxs-lookup"><span data-stu-id="1dbfe-105">Note that only the <xref:System.Xml.Linq.XElement> class implements serialization.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1dbfe-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="1dbfe-106">In This Section</span></span>  
  
|<span data-ttu-id="1dbfe-107">Temat</span><span class="sxs-lookup"><span data-stu-id="1dbfe-107">Topic</span></span>|<span data-ttu-id="1dbfe-108">Opis</span><span class="sxs-lookup"><span data-stu-id="1dbfe-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="1dbfe-109">Instrukcje: Serializowanie przy użyciu elementu XmlSerializer (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1dbfe-109">How to: Serialize Using XmlSerializer (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)|<span data-ttu-id="1dbfe-110">Pokazuje, jak serializować przy użyciu <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="1dbfe-110">Demonstrates how to serialize using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>|  
|[<span data-ttu-id="1dbfe-111">Instrukcje: Serializowanie przy użyciu obiektu DataContractSerializer (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1dbfe-111">How to: Serialize Using DataContractSerializer (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-serialize-using-datacontractserializer.md)|<span data-ttu-id="1dbfe-112">Pokazuje, jak serializować przy użyciu <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="1dbfe-112">Demonstrates how to serialize using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1dbfe-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1dbfe-113">See also</span></span>

- [<span data-ttu-id="1dbfe-114">Zaawansowane programowanie LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1dbfe-114">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
