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
ms.openlocfilehash: 8496e7c87cf7e6eea996ca7af4f288b7495c7661
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459896"
---
# <a name="xxdata-intrinsic-xaml-type"></a><span data-ttu-id="eeac6-102">x:XData — Typ funkcji XAML</span><span class="sxs-lookup"><span data-stu-id="eeac6-102">x:XData Intrinsic XAML Type</span></span>
<span data-ttu-id="eeac6-103">Umożliwia umieszczanie wysp danych XML w środowisku produkcyjnym XAML.</span><span class="sxs-lookup"><span data-stu-id="eeac6-103">Enables placement of XML data islands within a XAML production.</span></span> <span data-ttu-id="eeac6-104">Elementy XML w ramach `x:XData` nie powinny być traktowane przez procesory XAML tak, jakby były częścią działającej domyślnej przestrzeni nazw XAML lub dowolnej innej przestrzeni nazw XAML.</span><span class="sxs-lookup"><span data-stu-id="eeac6-104">XML elements within `x:XData` should not be treated by XAML processors as if they are a part of the acting default XAML namespace or any other XAML namespace.</span></span> <span data-ttu-id="eeac6-105">`x:XData` może zawierać dowolny poprawnie sformułowany kod XML.</span><span class="sxs-lookup"><span data-stu-id="eeac6-105">`x:XData` can contain arbitrary well-formed XML.</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="eeac6-106">Użycie elementu obiektu języka XAML</span><span class="sxs-lookup"><span data-stu-id="eeac6-106">XAML Object Element Usage</span></span>  
  
```xaml  
<x:XData>  
  <elementDataRoot>  
    [elementData]  
  </elementDataRoot>  
</x:XData>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="eeac6-107">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="eeac6-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`elementDataRoot`|<span data-ttu-id="eeac6-108">Pojedynczy element główny z podanej Wyspy danych.</span><span class="sxs-lookup"><span data-stu-id="eeac6-108">The single root element of the enclosed data island.</span></span> <span data-ttu-id="eeac6-109">W przypadku większości odbiorców, XML, który nie ma jednego katalogu głównego, jest uznawany za nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="eeac6-109">For most eventual consumers, XML that does not have a single root is considered invalid.</span></span> <span data-ttu-id="eeac6-110">W szczególności jest wymagany pojedynczy katalog główny, jeśli `x:XData` jest to źródło danych XML dla WPF lub wiele innych technologii, które używają źródeł XML do powiązania danych.</span><span class="sxs-lookup"><span data-stu-id="eeac6-110">In particular, a single root is required if the `x:XData` is intended as an XML data source for WPF or many other technologies that use XML sources for data binding.</span></span>|  
|`[elementData]`|<span data-ttu-id="eeac6-111">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="eeac6-111">Optional.</span></span> <span data-ttu-id="eeac6-112">KOD XML, który reprezentuje dane XML.</span><span class="sxs-lookup"><span data-stu-id="eeac6-112">XML that represents the XML data.</span></span> <span data-ttu-id="eeac6-113">Dowolna liczba elementów może być zawarta jako dane elementu, a zagnieżdżone elementy mogą być zawarte w innych elementach. jednak ogólne reguły dotyczące języka XML mają zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="eeac6-113">Any number of elements can be contained as element data and nested elements can be contained in other elements; however, the general rules of XML apply.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eeac6-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="eeac6-114">Remarks</span></span>  
 <span data-ttu-id="eeac6-115">Elementy XML w obiekcie `x:XData` mogą ponownie deklarować wszystkie możliwe przestrzenie nazw i prefiksy zawierające XMLDOM w danych.</span><span class="sxs-lookup"><span data-stu-id="eeac6-115">The XML elements within an `x:XData` object can re-declare all possible namespaces and prefixes of the containing XMLDOM within the data.</span></span>  
  
 <span data-ttu-id="eeac6-116">Dostęp programistyczny do danych XML i `x:XData` wewnętrzny typ XAML jest możliwy w .NET Framework usług XAML za pomocą klasy <xref:System.Windows.Markup.XData>.</span><span class="sxs-lookup"><span data-stu-id="eeac6-116">Programmatic access to XML data and the `x:XData` intrinsic XAML type is possible in .NET Framework XAML Services through the <xref:System.Windows.Markup.XData> class.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="eeac6-117">Uwagi dotyczące użycia WPF</span><span class="sxs-lookup"><span data-stu-id="eeac6-117">WPF Usage Notes</span></span>  
 <span data-ttu-id="eeac6-118">Obiekt `x:XData` jest używany głównie jako obiekt podrzędny <xref:System.Windows.Data.XmlDataProvider>lub alternatywnie, jako obiekt podrzędny właściwości <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> (w języku XAML jest zwykle wyrażona w składni elementu właściwości).</span><span class="sxs-lookup"><span data-stu-id="eeac6-118">The `x:XData` object is primarily used as a child object of an <xref:System.Windows.Data.XmlDataProvider>, or alternatively, as the child object of the <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> property (in XAML, this is typically expressed in property element syntax).</span></span>  
  
 <span data-ttu-id="eeac6-119">Dane powinny zwykle przedefiniować podstawową przestrzeń nazw XML w obrębie Wyspy danych, aby była nową domyślną przestrzenią nazw XML (ustawioną na pusty ciąg).</span><span class="sxs-lookup"><span data-stu-id="eeac6-119">The data should typically redefine the base XML namespace within the data island to be a new default XML namespace (set to an empty string).</span></span> <span data-ttu-id="eeac6-120">Jest to najłatwiejsze w przypadku prostych wysp danych, ponieważ wyrażenia <xref:System.Windows.Data.Binding.XPath%2A>, które są używane do odwoływania się do danych i wiązania z nią, mogą uniknąć włączenia prefiksów.</span><span class="sxs-lookup"><span data-stu-id="eeac6-120">This is easiest for simple data islands because the <xref:System.Windows.Data.Binding.XPath%2A> expressions that are used to reference and bind to the data can avoid inclusion of prefixes.</span></span> <span data-ttu-id="eeac6-121">Bardziej złożone Wyspy danych mogą definiować wiele prefiksów danych i używać określonego prefiksu dla przestrzeni nazw XML w katalogu głównym.</span><span class="sxs-lookup"><span data-stu-id="eeac6-121">More complex data islands might define multiple prefixes for the data and use a specific prefix for the XML namespace at the root.</span></span> <span data-ttu-id="eeac6-122">W takim przypadku wszystkie odwołania do wyrażenia <xref:System.Windows.Data.Binding.XPath%2A> powinny zawierać odpowiedni prefiks mapowany na przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="eeac6-122">In this case, all <xref:System.Windows.Data.Binding.XPath%2A> expression references should include the appropriate namespace-mapped prefix.</span></span> <span data-ttu-id="eeac6-123">Aby uzyskać więcej informacji, zobacz temat [powiązanie danych — omówienie](../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="eeac6-123">For more information, see [Data Binding Overview](../../desktop-wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="eeac6-124">Technicznie `x:XData` może służyć jako zawartość dowolnej właściwości typu <xref:System.Xml.Serialization.IXmlSerializable>.</span><span class="sxs-lookup"><span data-stu-id="eeac6-124">Technically, `x:XData` can be used as the content of any property of type <xref:System.Xml.Serialization.IXmlSerializable>.</span></span> <span data-ttu-id="eeac6-125">Jednak <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> jest jedyną wyrazistą implementacją.</span><span class="sxs-lookup"><span data-stu-id="eeac6-125">However, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> is the only prominent implementation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eeac6-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eeac6-126">See also</span></span>

- <xref:System.Windows.Data.XmlDataProvider>
- [<span data-ttu-id="eeac6-127">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="eeac6-127">Data Binding Overview</span></span>](../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="eeac6-128">Rozszerzenie znaczników powiązania</span><span class="sxs-lookup"><span data-stu-id="eeac6-128">Binding Markup Extension</span></span>](../wpf/advanced/binding-markup-extension.md)
