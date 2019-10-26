---
title: Informacje dotyczące LINQ to XML właściwości dynamicznych
ms.date: 10/22/2019
ms.topic: reference
ms.openlocfilehash: ca3684716f9b562d0e6a006c26730a1d1a28f8b1
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920931"
---
# <a name="linq-to-xml-dynamic-properties"></a><span data-ttu-id="2de38-102">Właściwości dynamiczne LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="2de38-102">LINQ to XML dynamic properties</span></span>

<span data-ttu-id="2de38-103">Ta sekcja zawiera informacje referencyjne na temat właściwości dynamicznych w LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="2de38-103">This section provides reference information about the dynamic properties in LINQ to XML.</span></span> <span data-ttu-id="2de38-104">W szczególnych przypadkach te właściwości są uwidaczniane przez klasy <xref:System.Xml.Linq.XAttribute> i <xref:System.Xml.Linq.XElement>, które znajdują się w przestrzeni nazw <xref:System.Xml.Linq>.</span><span class="sxs-lookup"><span data-stu-id="2de38-104">Specifically, these properties are exposed by the <xref:System.Xml.Linq.XAttribute> and <xref:System.Xml.Linq.XElement> classes, which are in the <xref:System.Xml.Linq> namespace.</span></span>

<span data-ttu-id="2de38-105">Jak wyjaśniono w temacie [Omówienie powiązania danych WPF z LINQ to XML](wpf-data-binding-with-linq-to-xml-overview.md), Każda właściwość dynamiczna jest równoważna z standardową właściwością publiczną lub metodą w tej samej klasie.</span><span class="sxs-lookup"><span data-stu-id="2de38-105">As explained in the topic [Overview of WPF data binding with LINQ to XML](wpf-data-binding-with-linq-to-xml-overview.md), each of the dynamic properties is equivalent to a standard public property or method in the same class.</span></span> <span data-ttu-id="2de38-106">Tych standardowych członków należy używać w większości celów; właściwości dynamiczne są udostępniane w ramach scenariuszy powiązań danych LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="2de38-106">These standard members should be used for most purposes; dynamic properties are provided specifically for LINQ to XML data binding scenarios.</span></span> <span data-ttu-id="2de38-107">Aby uzyskać więcej informacji na temat standardowych elementów członkowskich tych klas, zobacz tematy dotyczące <xref:System.Xml.Linq.XAttribute> i <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="2de38-107">For more information about the standard members of these classes, see the <xref:System.Xml.Linq.XAttribute> and <xref:System.Xml.Linq.XElement> reference topics.</span></span>

<span data-ttu-id="2de38-108">W odniesieniu do ich rozwiązanych wartości właściwości dynamiczne w tej sekcji należą do dwóch kategorii:</span><span class="sxs-lookup"><span data-stu-id="2de38-108">With respect to their resolved values, the dynamic properties in this section fall into two categories:</span></span>

- <span data-ttu-id="2de38-109">Proste, takie jak `Value` właściwości w klasach <xref:System.Xml.Linq.XAttribute> i <xref:System.Xml.Linq.XElement>, które rozpoznają się z jedną wartością.</span><span class="sxs-lookup"><span data-stu-id="2de38-109">Simple ones, such as the `Value` properties in the <xref:System.Xml.Linq.XAttribute> and <xref:System.Xml.Linq.XElement> classes, that resolve to a single value.</span></span>

- <span data-ttu-id="2de38-110">Indeksowane wartości, takie jak [elementy](elements-xelement-dynamic-property.md) i właściwości [potomne](descendants-xelement-dynamic-property.md) <xref:System.Xml.Linq.XElement>, które są rozpoznawane jako typ indeksatora.</span><span class="sxs-lookup"><span data-stu-id="2de38-110">Indexed values, such as the [Elements](elements-xelement-dynamic-property.md) and [Descendants](descendants-xelement-dynamic-property.md) properties of <xref:System.Xml.Linq.XElement>, that resolve into an indexer type.</span></span> <span data-ttu-id="2de38-111">Aby można było rozpoznać typy indeksatora do żądanej wartości lub kolekcji, należy do nich przekazywać parametry rozszerzonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="2de38-111">For indexer types to be resolved to the desired value or collection, an expanded name parameter must be passed to them.</span></span>

<span data-ttu-id="2de38-112">Wszystkie właściwości dynamiczne zwracające wartość indeksowaną typu <xref:System.Collections.Generic.IEnumerable%601> korzystają z odroczonego wykonania.</span><span class="sxs-lookup"><span data-stu-id="2de38-112">All the dynamic properties that return an indexed value of type <xref:System.Collections.Generic.IEnumerable%601> use deferred execution.</span></span> <span data-ttu-id="2de38-113">Aby uzyskać więcej informacji o odroczonym wykonywaniu, zobacz [wprowadzenie do zapytań LINQC#()](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries).</span><span class="sxs-lookup"><span data-stu-id="2de38-113">For more information about deferred execution, see [Introduction to LINQ queries (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries).</span></span>

## <a name="reference"></a><span data-ttu-id="2de38-114">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="2de38-114">Reference</span></span>

- <xref:System.Xml.Linq>
- <xref:System.Xml.Linq.XElement?displayProperty=fullName>
- <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>

## <a name="see-also"></a><span data-ttu-id="2de38-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2de38-115">See also</span></span>

- [<span data-ttu-id="2de38-116">Powiązanie danych WPF za pomocą LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="2de38-116">WPF data binding with LINQ to XML</span></span>](wpf-data-binding-with-linq-to-xml-overview.md)
- [<span data-ttu-id="2de38-117">Powiązanie danych WPF z LINQ to XML przegląd</span><span class="sxs-lookup"><span data-stu-id="2de38-117">WPF data binding with LINQ to XML overview</span></span>](wpf-data-binding-with-linq-to-xml-overview.md)
- [<span data-ttu-id="2de38-118">Wprowadzenie do zapytań LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="2de38-118">Introduction to LINQ queries (C#)</span></span>](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)
