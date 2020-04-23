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
ms.openlocfilehash: b7f0954158988db107feb4a6c51ba81d5db11dcb
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071543"
---
# <a name="xxdata-intrinsic-xaml-type"></a><span data-ttu-id="5e0fb-102">x:XData — Typ funkcji XAML</span><span class="sxs-lookup"><span data-stu-id="5e0fb-102">x:XData Intrinsic XAML Type</span></span>
<span data-ttu-id="5e0fb-103">Umożliwia umieszczenie wysp danych XML w środowisku produkcyjnym XAML.</span><span class="sxs-lookup"><span data-stu-id="5e0fb-103">Enables placement of XML data islands within a XAML production.</span></span> <span data-ttu-id="5e0fb-104">Elementy XML `x:XData` wewnątrz nie powinny być traktowane przez procesory XAML tak, jakby były częścią działającej domyślnej przestrzeni nazw XAML lub innej przestrzeni nazw XAML.</span><span class="sxs-lookup"><span data-stu-id="5e0fb-104">XML elements within `x:XData` should not be treated by XAML processors as if they are a part of the acting default XAML namespace or any other XAML namespace.</span></span> <span data-ttu-id="5e0fb-105">`x:XData`może zawierać dowolny dobrze uformowany kod XML.</span><span class="sxs-lookup"><span data-stu-id="5e0fb-105">`x:XData` can contain arbitrary well-formed XML.</span></span>

## <a name="xaml-object-element-usage"></a><span data-ttu-id="5e0fb-106">Użycie elementu obiektu języka XAML</span><span class="sxs-lookup"><span data-stu-id="5e0fb-106">XAML Object Element Usage</span></span>

```xaml
<x:XData>
  <elementDataRoot>
    [elementData]
  </elementDataRoot>
</x:XData>
```

## <a name="xaml-values"></a><span data-ttu-id="5e0fb-107">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="5e0fb-107">XAML Values</span></span>

|||
|-|-|
|`elementDataRoot`|<span data-ttu-id="5e0fb-108">Pojedynczy element główny zamkniętej wyspy danych.</span><span class="sxs-lookup"><span data-stu-id="5e0fb-108">The single root element of the enclosed data island.</span></span> <span data-ttu-id="5e0fb-109">Dla większości potencjalnych konsumentów XML, który nie ma jednego katalogu głównego jest uważany za nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="5e0fb-109">For most eventual consumers, XML that does not have a single root is considered invalid.</span></span> <span data-ttu-id="5e0fb-110">W szczególności pojedynczy katalog główny jest `x:XData` wymagany, jeśli jest przeznaczony jako źródło danych XML dla WPF lub wiele innych technologii, które używają źródeł XML do wiązania danych.</span><span class="sxs-lookup"><span data-stu-id="5e0fb-110">In particular, a single root is required if the `x:XData` is intended as an XML data source for WPF or many other technologies that use XML sources for data binding.</span></span>|
|`[elementData]`|<span data-ttu-id="5e0fb-111">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5e0fb-111">Optional.</span></span> <span data-ttu-id="5e0fb-112">XML reprezentujący dane XML.</span><span class="sxs-lookup"><span data-stu-id="5e0fb-112">XML that represents the XML data.</span></span> <span data-ttu-id="5e0fb-113">Dowolna liczba elementów może być zawarta jako dane elementu i elementy zagnieżdżone mogą być zawarte w innych elementach; zastosowanie mają jednak ogólne zasady XML.</span><span class="sxs-lookup"><span data-stu-id="5e0fb-113">Any number of elements can be contained as element data and nested elements can be contained in other elements; however, the general rules of XML apply.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5e0fb-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5e0fb-114">Remarks</span></span>

<span data-ttu-id="5e0fb-115">Elementy XML w `x:XData` obiekcie można ponownie zadeklarować wszystkie możliwe przestrzenie nazw i prefiksy zawierające XMLDOM w danych.</span><span class="sxs-lookup"><span data-stu-id="5e0fb-115">The XML elements within an `x:XData` object can re-declare all possible namespaces and prefixes of the containing XMLDOM within the data.</span></span>

<span data-ttu-id="5e0fb-116">Programowy dostęp do danych `x:XData` XML i wewnętrznego typu XAML jest możliwy w <xref:System.Windows.Markup.XData> usługach .NET XAML za pośrednictwem klasy.</span><span class="sxs-lookup"><span data-stu-id="5e0fb-116">Programmatic access to XML data and the `x:XData` intrinsic XAML type is possible in .NET XAML Services through the <xref:System.Windows.Markup.XData> class.</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="5e0fb-117">Uwagi dotyczące użycia WPF</span><span class="sxs-lookup"><span data-stu-id="5e0fb-117">WPF Usage Notes</span></span>

<span data-ttu-id="5e0fb-118">Obiekt `x:XData` jest używany głównie jako obiekt <xref:System.Windows.Data.XmlDataProvider>podrzędny , lub alternatywnie, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> jako obiekt podrzędny właściwości (w XAML, jest to zazwyczaj wyrażone w składni elementu właściwości).</span><span class="sxs-lookup"><span data-stu-id="5e0fb-118">The `x:XData` object is primarily used as a child object of an <xref:System.Windows.Data.XmlDataProvider>, or alternatively, as the child object of the <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> property (in XAML, this is typically expressed in property element syntax).</span></span>

<span data-ttu-id="5e0fb-119">Dane powinny zazwyczaj przedefiniować podstawową przestrzeń nazw XML w obrębie wyspy danych jako nową domyślną przestrzeń nazw XML (ustawioną na pusty ciąg).</span><span class="sxs-lookup"><span data-stu-id="5e0fb-119">The data should typically redefine the base XML namespace within the data island to be a new default XML namespace (set to an empty string).</span></span> <span data-ttu-id="5e0fb-120">Jest to najłatwiejsze dla <xref:System.Windows.Data.Binding.XPath%2A> prostych wysp danych, ponieważ wyrażenia, które są używane do odwoływania się i powiązania z danymi, mogą uniknąć dołączania prefiksów.</span><span class="sxs-lookup"><span data-stu-id="5e0fb-120">This is easiest for simple data islands because the <xref:System.Windows.Data.Binding.XPath%2A> expressions that are used to reference and bind to the data can avoid inclusion of prefixes.</span></span> <span data-ttu-id="5e0fb-121">Bardziej złożone wyspy danych mogą definiować wiele prefiksów danych i używać określonego prefiksu obszaru nazw XML w katalogu głównym.</span><span class="sxs-lookup"><span data-stu-id="5e0fb-121">More complex data islands might define multiple prefixes for the data and use a specific prefix for the XML namespace at the root.</span></span> <span data-ttu-id="5e0fb-122">W takim przypadku <xref:System.Windows.Data.Binding.XPath%2A> wszystkie odwołania do wyrażeń powinny zawierać odpowiedni prefiks mapowany przez obszar nazw.</span><span class="sxs-lookup"><span data-stu-id="5e0fb-122">In this case, all <xref:System.Windows.Data.Binding.XPath%2A> expression references should include the appropriate namespace-mapped prefix.</span></span> <span data-ttu-id="5e0fb-123">Aby uzyskać więcej informacji, zobacz [Omówienie powiązania danych](../data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5e0fb-123">For more information, see [Data Binding Overview](../data/data-binding-overview.md).</span></span>

<span data-ttu-id="5e0fb-124">Technicznie, `x:XData` może być używany jako zawartość dowolnej <xref:System.Xml.Serialization.IXmlSerializable>właściwości typu .</span><span class="sxs-lookup"><span data-stu-id="5e0fb-124">Technically, `x:XData` can be used as the content of any property of type <xref:System.Xml.Serialization.IXmlSerializable>.</span></span> <span data-ttu-id="5e0fb-125">Jest <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> to jednak jedyna znacząca implementacja.</span><span class="sxs-lookup"><span data-stu-id="5e0fb-125">However, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> is the only prominent implementation.</span></span>

## <a name="see-also"></a><span data-ttu-id="5e0fb-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5e0fb-126">See also</span></span>

- <xref:System.Windows.Data.XmlDataProvider>
- [<span data-ttu-id="5e0fb-127">Omówienie powiązania danych</span><span class="sxs-lookup"><span data-stu-id="5e0fb-127">Data Binding Overview</span></span>](../data/data-binding-overview.md)
- [<span data-ttu-id="5e0fb-128">Rozszerzenie znaczników powiązania</span><span class="sxs-lookup"><span data-stu-id="5e0fb-128">Binding Markup Extension</span></span>](../../framework/wpf/advanced/binding-markup-extension.md)
