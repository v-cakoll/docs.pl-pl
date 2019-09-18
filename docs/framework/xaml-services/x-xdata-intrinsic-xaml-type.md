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
ms.openlocfilehash: c5f729837b9bb52ca7d232ca66b58e283a2bcefc
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053697"
---
# <a name="xxdata-intrinsic-xaml-type"></a><span data-ttu-id="6f95a-102">x:XData — Typ funkcji XAML</span><span class="sxs-lookup"><span data-stu-id="6f95a-102">x:XData Intrinsic XAML Type</span></span>
<span data-ttu-id="6f95a-103">Umożliwia umieszczanie wysp danych XML w środowisku produkcyjnym XAML.</span><span class="sxs-lookup"><span data-stu-id="6f95a-103">Enables placement of XML data islands within a XAML production.</span></span> <span data-ttu-id="6f95a-104">Elementy XML w `x:XData` ramach nie powinny być traktowane przez procesory XAML tak, jakby były częścią działającej domyślnej przestrzeni nazw XAML lub dowolnej innej przestrzeni nazw XAML.</span><span class="sxs-lookup"><span data-stu-id="6f95a-104">XML elements within `x:XData` should not be treated by XAML processors as if they are a part of the acting default XAML namespace or any other XAML namespace.</span></span> <span data-ttu-id="6f95a-105">`x:XData`może zawierać dowolny poprawnie sformułowany kod XML.</span><span class="sxs-lookup"><span data-stu-id="6f95a-105">`x:XData` can contain arbitrary well-formed XML.</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="6f95a-106">Użycie elementu obiektu języka XAML</span><span class="sxs-lookup"><span data-stu-id="6f95a-106">XAML Object Element Usage</span></span>  
  
```xaml  
<x:XData>  
  <elementDataRoot>  
    [elementData]  
  </elementDataRoot>  
</x:XData>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="6f95a-107">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="6f95a-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`elementDataRoot`|<span data-ttu-id="6f95a-108">Pojedynczy element główny z podanej Wyspy danych.</span><span class="sxs-lookup"><span data-stu-id="6f95a-108">The single root element of the enclosed data island.</span></span> <span data-ttu-id="6f95a-109">W przypadku większości odbiorców, XML, który nie ma jednego katalogu głównego, jest uznawany za nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="6f95a-109">For most eventual consumers, XML that does not have a single root is considered invalid.</span></span> <span data-ttu-id="6f95a-110">W szczególności, jeśli `x:XData` jest to źródło danych XML dla WPF lub wiele innych technologii, które używają źródeł danych XML do tworzenia powiązań z danymi, wymagany jest pojedynczy element główny.</span><span class="sxs-lookup"><span data-stu-id="6f95a-110">In particular, a single root is required if the `x:XData` is intended as an XML data source for WPF or many other technologies that use XML sources for data binding.</span></span>|  
|`[elementData]`|<span data-ttu-id="6f95a-111">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="6f95a-111">Optional.</span></span> <span data-ttu-id="6f95a-112">KOD XML, który reprezentuje dane XML.</span><span class="sxs-lookup"><span data-stu-id="6f95a-112">XML that represents the XML data.</span></span> <span data-ttu-id="6f95a-113">Dowolna liczba elementów może być zawarta jako dane elementu, a zagnieżdżone elementy mogą być zawarte w innych elementach. jednak ogólne reguły dotyczące języka XML mają zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="6f95a-113">Any number of elements can be contained as element data and nested elements can be contained in other elements; however, the general rules of XML apply.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f95a-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6f95a-114">Remarks</span></span>  
 <span data-ttu-id="6f95a-115">Elementy XML w `x:XData` obiekcie mogą ponownie deklarować wszystkie możliwe przestrzenie nazw i prefiksy zawierające XMLDOM w danych.</span><span class="sxs-lookup"><span data-stu-id="6f95a-115">The XML elements within an `x:XData` object can re-declare all possible namespaces and prefixes of the containing XMLDOM within the data.</span></span>  
  
 <span data-ttu-id="6f95a-116">Dostęp programistyczny do danych XML i `x:XData` wewnętrzny typ XAML jest możliwy w .NET Framework usługach XAML <xref:System.Windows.Markup.XData> za pomocą klasy.</span><span class="sxs-lookup"><span data-stu-id="6f95a-116">Programmatic access to XML data and the `x:XData` intrinsic XAML type is possible in .NET Framework XAML Services through the <xref:System.Windows.Markup.XData> class.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="6f95a-117">Uwagi dotyczące użycia WPF</span><span class="sxs-lookup"><span data-stu-id="6f95a-117">WPF Usage Notes</span></span>  
 <span data-ttu-id="6f95a-118">Obiekt jest głównie używany jako obiekt <xref:System.Windows.Data.XmlDataProvider>podrzędny obiektu, lub alternatywnie, jako obiekt <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> podrzędny właściwości (w języku XAML jest zwykle wyrażona w składni elementu właściwości). `x:XData`</span><span class="sxs-lookup"><span data-stu-id="6f95a-118">The `x:XData` object is primarily used as a child object of an <xref:System.Windows.Data.XmlDataProvider>, or alternatively, as the child object of the <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> property (in XAML, this is typically expressed in property element syntax).</span></span>  
  
 <span data-ttu-id="6f95a-119">Dane powinny zwykle przedefiniować podstawową przestrzeń nazw XML w obrębie Wyspy danych, aby była nową domyślną przestrzenią nazw XML (ustawioną na pusty ciąg).</span><span class="sxs-lookup"><span data-stu-id="6f95a-119">The data should typically redefine the base XML namespace within the data island to be a new default XML namespace (set to an empty string).</span></span> <span data-ttu-id="6f95a-120">Jest to najłatwiej w przypadku prostych wysp <xref:System.Windows.Data.Binding.XPath%2A> danych, ponieważ wyrażenia, które są używane do odwoływania się do danych i tworzenia powiązań z danymi, mogą uniknąć włączenia prefiksów.</span><span class="sxs-lookup"><span data-stu-id="6f95a-120">This is easiest for simple data islands because the <xref:System.Windows.Data.Binding.XPath%2A> expressions that are used to reference and bind to the data can avoid inclusion of prefixes.</span></span> <span data-ttu-id="6f95a-121">Bardziej złożone Wyspy danych mogą definiować wiele prefiksów danych i używać określonego prefiksu dla przestrzeni nazw XML w katalogu głównym.</span><span class="sxs-lookup"><span data-stu-id="6f95a-121">More complex data islands might define multiple prefixes for the data and use a specific prefix for the XML namespace at the root.</span></span> <span data-ttu-id="6f95a-122">W takim przypadku wszystkie <xref:System.Windows.Data.Binding.XPath%2A> odwołania do wyrażeń powinny zawierać odpowiedni prefiks mapowany na przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="6f95a-122">In this case, all <xref:System.Windows.Data.Binding.XPath%2A> expression references should include the appropriate namespace-mapped prefix.</span></span> <span data-ttu-id="6f95a-123">Aby uzyskać więcej informacji, zobacz temat [powiązanie danych — omówienie](../wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6f95a-123">For more information, see [Data Binding Overview](../wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="6f95a-124">Technicznie `x:XData` , może być używany jako zawartość dowolnej właściwości typu <xref:System.Xml.Serialization.IXmlSerializable>.</span><span class="sxs-lookup"><span data-stu-id="6f95a-124">Technically, `x:XData` can be used as the content of any property of type <xref:System.Xml.Serialization.IXmlSerializable>.</span></span> <span data-ttu-id="6f95a-125"><xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> Jest jednak jedyną wyrazistą implementacją.</span><span class="sxs-lookup"><span data-stu-id="6f95a-125">However, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> is the only prominent implementation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f95a-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6f95a-126">See also</span></span>

- <xref:System.Windows.Data.XmlDataProvider>
- [<span data-ttu-id="6f95a-127">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="6f95a-127">Data Binding Overview</span></span>](../wpf/data/data-binding-overview.md)
- [<span data-ttu-id="6f95a-128">Rozszerzenie znaczników powiązania</span><span class="sxs-lookup"><span data-stu-id="6f95a-128">Binding Markup Extension</span></span>](../wpf/advanced/binding-markup-extension.md)
