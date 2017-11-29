---
title: "Omówienie przestrzenie nazw (LINQ do XML)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8eb31fa-4b26-4acf-8050-6e705687f458
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 082172720abd39634f7183367d4d7b8d53d2bb7e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="namespaces-overview-linq-to-xml"></a><span data-ttu-id="2878b-102">Omówienie przestrzenie nazw (LINQ do XML)</span><span class="sxs-lookup"><span data-stu-id="2878b-102">Namespaces Overview (LINQ to XML)</span></span>
<span data-ttu-id="2878b-103">W tym temacie przedstawiono obszary nazw, <xref:System.Xml.Linq.XName> klasy, a <xref:System.Xml.Linq.XNamespace> klasy.</span><span class="sxs-lookup"><span data-stu-id="2878b-103">This topic introduces namespaces, the <xref:System.Xml.Linq.XName> class, and the <xref:System.Xml.Linq.XNamespace> class.</span></span>  
  
## <a name="xml-names"></a><span data-ttu-id="2878b-104">Nazwy XML</span><span class="sxs-lookup"><span data-stu-id="2878b-104">XML Names</span></span>  
 <span data-ttu-id="2878b-105">Nazwy XML często są źródłem złożoności programowania w języku XML.</span><span class="sxs-lookup"><span data-stu-id="2878b-105">XML names are often a source of complexity in XML programming.</span></span> <span data-ttu-id="2878b-106">Nazwa XML składa się z przestrzeni nazw XML (nazywanych również identyfikator URI przestrzeni nazw XML) i nazwa lokalna.</span><span class="sxs-lookup"><span data-stu-id="2878b-106">An XML name consists of an XML namespace (also called an XML namespace URI) and a local name.</span></span> <span data-ttu-id="2878b-107">Obszar nazw XML jest podobny do przestrzeni nazw w [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]-programu.</span><span class="sxs-lookup"><span data-stu-id="2878b-107">An XML namespace is similar to a namespace in a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]-based program.</span></span> <span data-ttu-id="2878b-108">Umożliwia ona zakwalifikować unikatowej nazwy elementów i atrybutów.</span><span class="sxs-lookup"><span data-stu-id="2878b-108">It enables you to uniquely qualify the names of elements and attributes.</span></span> <span data-ttu-id="2878b-109">Dzięki temu można uniknąć konfliktów nazw między różnymi składnikami dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="2878b-109">This helps avoid name conflicts between various parts of an XML document.</span></span> <span data-ttu-id="2878b-110">Po zadeklarowaniu przestrzeni nazw XML, można wybrać nazwę lokalną o tylko musi być unikatowa w obrębie tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="2878b-110">When you have declared an XML namespace, you can select a local name that only has to be unique within that namespace.</span></span>  
  
 <span data-ttu-id="2878b-111">Innym aspektem nazw XML jest XML *prefiksy przestrzeni nazw*.</span><span class="sxs-lookup"><span data-stu-id="2878b-111">Another aspect of XML names is XML *namespace prefixes*.</span></span> <span data-ttu-id="2878b-112">Prefiksy XML, że większość złożoność nazwy XML.</span><span class="sxs-lookup"><span data-stu-id="2878b-112">XML prefixes cause most of the complexity of XML names.</span></span> <span data-ttu-id="2878b-113">Tymi prefiksami umożliwiają tworzenie skrótu dla przestrzeni nazw XML, co sprawia, że dokument XML bardziej zwięzłe i zrozumienia.</span><span class="sxs-lookup"><span data-stu-id="2878b-113">These prefixes enable you to create a shortcut for an XML namespace, which makes the XML document more concise and understandable.</span></span> <span data-ttu-id="2878b-114">Jednak prefiksy XML w zależności od kontekstu ma znaczenie, który dodaje złożoności.</span><span class="sxs-lookup"><span data-stu-id="2878b-114">However, XML prefixes depend on their context to have meaning, which adds complexity.</span></span> <span data-ttu-id="2878b-115">Na przykład prefiks XML `aw` może być skojarzony z jedną przestrzeń nazw XML w jednej części drzewa XML oraz z różnych przestrzeni nazw XML w innej części drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="2878b-115">For example, the XML prefix `aw` could be associated with one XML namespace in one part of an XML tree, and with a different XML namespace in a different part of the XML tree.</span></span>  
  
 <span data-ttu-id="2878b-116">Korzystając z [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] z literały Visual Basic i XML, należy użyć prefiksy przestrzeni nazw podczas pracy z dokumentami w przestrzeniach nazw.</span><span class="sxs-lookup"><span data-stu-id="2878b-116">When using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] with Visual Basic and XML literals, you must use namespace prefixes when working with documents in namespaces.</span></span>  
  
 <span data-ttu-id="2878b-117">W [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], jest klasa, która reprezentuje nazw XML <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="2878b-117">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], the class that represents XML names is <xref:System.Xml.Linq.XName>.</span></span> <span data-ttu-id="2878b-118">Nazwy XML często są wyświetlane w całym [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] interfejsu API, i wszędzie tam, gdzie nazwa XML jest wymagana, można znaleźć <xref:System.Xml.Linq.XName> parametru.</span><span class="sxs-lookup"><span data-stu-id="2878b-118">XML names appear frequently throughout the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] API, and wherever an XML name is required, you will find an <xref:System.Xml.Linq.XName> parameter.</span></span> <span data-ttu-id="2878b-119">Jednak rzadko pracę bezpośrednio z <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="2878b-119">However, you rarely work directly with an <xref:System.Xml.Linq.XName>.</span></span> <span data-ttu-id="2878b-120"><xref:System.Xml.Linq.XName>zawiera niejawna konwersja z ciągu.</span><span class="sxs-lookup"><span data-stu-id="2878b-120"><xref:System.Xml.Linq.XName> contains an implicit conversion from string.</span></span>  
  
 <span data-ttu-id="2878b-121">Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Linq.XNamespace> i <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="2878b-121">For more information, see <xref:System.Xml.Linq.XNamespace> and <xref:System.Xml.Linq.XName>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2878b-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2878b-122">See Also</span></span>  
 [<span data-ttu-id="2878b-123">Praca z przestrzeni nazw XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2878b-123">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
