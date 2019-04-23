---
title: x:XData — Typ funkcji XAML
ms.date: 03/30/2017
f1_keywords:
- x:XData
- XData
- xXData
helpviewer_keywords:
- XAML [XAML Services], x:XData directive element
- XData in XAML [XAML Services]
- x:XData XAML directive element [XAML Services]
ms.assetid: 7ce209c2-621b-4977-b643-565f7e663534
ms.openlocfilehash: c8044bc341ded6ef7b03bbdf701e724654460d54
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59125162"
---
# <a name="xxdata-intrinsic-xaml-type"></a><span data-ttu-id="85e74-102">x:XData — Typ funkcji XAML</span><span class="sxs-lookup"><span data-stu-id="85e74-102">x:XData Intrinsic XAML Type</span></span>
<span data-ttu-id="85e74-103">Umożliwia umieszczanie Wyspy danych XML w ramach produkcji XAML.</span><span class="sxs-lookup"><span data-stu-id="85e74-103">Enables placement of XML data islands within a XAML production.</span></span> <span data-ttu-id="85e74-104">Elementy XML wewnątrz `x:XData` nie powinny być traktowane przez procesory XAML, jak gdyby były częścią acting domyślna przestrzeń nazw XAML lub innych nazw XAML.</span><span class="sxs-lookup"><span data-stu-id="85e74-104">XML elements within `x:XData` should not be treated by XAML processors as if they are a part of the acting default XAML namespace or any other XAML namespace.</span></span> <span data-ttu-id="85e74-105">`x:XData` może zawierać dowolną poprawnie sformułowany dokument XML.</span><span class="sxs-lookup"><span data-stu-id="85e74-105">`x:XData` can contain arbitrary well-formed XML.</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="85e74-106">Użycie elementu obiektu języka XAML</span><span class="sxs-lookup"><span data-stu-id="85e74-106">XAML Object Element Usage</span></span>  
  
```  
<x:XData>  
  <elementDataRoot>  
    [elementData]  
  </elementDataRoot>  
</x:XData>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="85e74-107">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="85e74-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`elementDataRoot`|<span data-ttu-id="85e74-108">Element z jednym elementem głównym Wyspy danych zamknięte.</span><span class="sxs-lookup"><span data-stu-id="85e74-108">The single root element of the enclosed data island.</span></span> <span data-ttu-id="85e74-109">Dla większości klientów ostatecznej XML, który nie ma jednym elementem głównym jest uznawane za nieprawidłowe.</span><span class="sxs-lookup"><span data-stu-id="85e74-109">For most eventual consumers, XML that does not have a single root is considered invalid.</span></span> <span data-ttu-id="85e74-110">W szczególności jednym elementem głównym jest wymagany, jeśli `x:XData` ma służyć jako źródło danych XML do WPF lub wiele technologii, używające źródła XML dla powiązania danych.</span><span class="sxs-lookup"><span data-stu-id="85e74-110">In particular, a single root is required if the `x:XData` is intended as an XML data source for WPF or many other technologies that use XML sources for data binding.</span></span>|  
|`[elementData]`|<span data-ttu-id="85e74-111">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="85e74-111">Optional.</span></span> <span data-ttu-id="85e74-112">Plik XML, który reprezentuje dane XML.</span><span class="sxs-lookup"><span data-stu-id="85e74-112">XML that represents the XML data.</span></span> <span data-ttu-id="85e74-113">Dowolną liczbę elementów mogą być zawarte jako element danych i elementy zagnieżdżone mogą być zawarte w innych elementów; Jednakże zastosowania ogólne zasady XML.</span><span class="sxs-lookup"><span data-stu-id="85e74-113">Any number of elements can be contained as element data and nested elements can be contained in other elements; however, the general rules of XML apply.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85e74-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="85e74-114">Remarks</span></span>  
 <span data-ttu-id="85e74-115">Elementy XML w ramach `x:XData` obiektu ponownie zadeklarować wszystkie możliwe przestrzenie nazw i prefiksy zawierającego XMLDOM w ramach danych.</span><span class="sxs-lookup"><span data-stu-id="85e74-115">The XML elements within an `x:XData` object can re-declare all possible namespaces and prefixes of the containing XMLDOM within the data.</span></span>  
  
 <span data-ttu-id="85e74-116">Programowy dostęp do danych XML i `x:XData` wewnętrzny typ XAML jest możliwe w .NET Framework XAML usług za pośrednictwem <xref:System.Windows.Markup.XData> klasy.</span><span class="sxs-lookup"><span data-stu-id="85e74-116">Programmatic access to XML data and the `x:XData` intrinsic XAML type is possible in .NET Framework XAML Services through the <xref:System.Windows.Markup.XData> class.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="85e74-117">Uwagi dotyczące użytkowania WPF</span><span class="sxs-lookup"><span data-stu-id="85e74-117">WPF Usage Notes</span></span>  
 <span data-ttu-id="85e74-118">`x:XData` Obiekt jest używany głównie jako obiekt podrzędny panelu <xref:System.Windows.Data.XmlDataProvider>, albo, jako obiekt podrzędny obiektu <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> właściwości (w XAML, to jest zwykle wyrażona w składni elementu właściwości).</span><span class="sxs-lookup"><span data-stu-id="85e74-118">The `x:XData` object is primarily used as a child object of an <xref:System.Windows.Data.XmlDataProvider>, or alternatively, as the child object of the <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> property (in XAML, this is typically expressed in property element syntax).</span></span>  
  
 <span data-ttu-id="85e74-119">Dane zwykle powinny również ponownie definiować podstawowej przestrzeni nazw XML, w ramach Wyspy danych do nowego domyślnej przestrzeni nazw XML (ustawiony na pusty ciąg znaków).</span><span class="sxs-lookup"><span data-stu-id="85e74-119">The data should typically redefine the base XML namespace within the data island to be a new default XML namespace (set to an empty string).</span></span> <span data-ttu-id="85e74-120">Jest to najprostszy Wyspy danych proste, ponieważ <xref:System.Windows.Data.Binding.XPath%2A> wyrażeń, które są używane do odwołania i powiąż z danymi można uniknąć włączenia prefiksów.</span><span class="sxs-lookup"><span data-stu-id="85e74-120">This is easiest for simple data islands because the <xref:System.Windows.Data.Binding.XPath%2A> expressions that are used to reference and bind to the data can avoid inclusion of prefixes.</span></span> <span data-ttu-id="85e74-121">Bardziej złożone Wyspy danych może zdefiniować wiele prefiksów dla danych i używaj określonego prefiksu dla przestrzeni nazw XML w folderze głównym.</span><span class="sxs-lookup"><span data-stu-id="85e74-121">More complex data islands might define multiple prefixes for the data and use a specific prefix for the XML namespace at the root.</span></span> <span data-ttu-id="85e74-122">W takim przypadku wszystkie <xref:System.Windows.Data.Binding.XPath%2A> wyrażenie odwołuje się powinna zawierać odpowiedni prefiks mapowane w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="85e74-122">In this case, all <xref:System.Windows.Data.Binding.XPath%2A> expression references should include the appropriate namespace-mapped prefix.</span></span> <span data-ttu-id="85e74-123">Aby uzyskać więcej informacji, zobacz [Przegląd wiązanie danych](../wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="85e74-123">For more information, see [Data Binding Overview](../wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="85e74-124">Z technicznego punktu widzenia `x:XData` może służyć jako zawartość żadnej właściwości typu <xref:System.Xml.Serialization.IXmlSerializable>.</span><span class="sxs-lookup"><span data-stu-id="85e74-124">Technically, `x:XData` can be used as the content of any property of type <xref:System.Xml.Serialization.IXmlSerializable>.</span></span> <span data-ttu-id="85e74-125">Jednak <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> tylko widocznym implementacji.</span><span class="sxs-lookup"><span data-stu-id="85e74-125">However, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> is the only prominent implementation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85e74-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="85e74-126">See also</span></span>

- <xref:System.Windows.Data.XmlDataProvider>
- [<span data-ttu-id="85e74-127">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="85e74-127">Data Binding Overview</span></span>](../wpf/data/data-binding-overview.md)
- [<span data-ttu-id="85e74-128">Rozszerzenie znaczników powiązania</span><span class="sxs-lookup"><span data-stu-id="85e74-128">Binding Markup Extension</span></span>](../wpf/advanced/binding-markup-extension.md)
