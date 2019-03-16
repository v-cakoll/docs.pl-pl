---
title: xml:lang — Obsługa w XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:lang attribute
- xml:lang attribute [XAML Services]
- RFC 3066 standard [XAML Services]
- standards [XAML Services], RFC 3066
ms.assetid: 7aac0078-a1c5-41f8-b8b0-975510d9dca0
ms.openlocfilehash: 9ec844c37ee2ef7979c82b308cdf167a46a3c072
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2019
ms.locfileid: "58034430"
---
# <a name="xmllang-handling-in-xaml"></a><span data-ttu-id="bf39c-102">xml:lang — Obsługa w XAML</span><span class="sxs-lookup"><span data-stu-id="bf39c-102">xml:lang Handling in XAML</span></span>
<span data-ttu-id="bf39c-103">`xml:lang` Atrybut jest [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)]-zdefiniowany atrybut deklarujący informacje języka i kultury dla elementu w pliku XML.</span><span class="sxs-lookup"><span data-stu-id="bf39c-103">The `xml:lang` attribute is an [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)]-defined attribute that declares the language and culture information for an element in XML.</span></span> <span data-ttu-id="bf39c-104">To takie samo znaczenie atrybut będzie nadal występował w XAML; jednak dodatkowe zagadnienia do rozważenia.</span><span class="sxs-lookup"><span data-stu-id="bf39c-104">This same meaning of the attribute persists in XAML; however, some additional considerations apply.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="bf39c-105">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="bf39c-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object xml:lang="rfc3066lang" />  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="bf39c-106">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="bf39c-106">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bf39c-107">*rfc3066lang*</span><span class="sxs-lookup"><span data-stu-id="bf39c-107">*rfc3066lang*</span></span>|<span data-ttu-id="bf39c-108">Ciąg, który jest tworzony na podstawie [RFC 3066](https://go.microsoft.com/fwlink/?LinkId=132454) standardowe i identyfikuje języka lub obszarem języka.</span><span class="sxs-lookup"><span data-stu-id="bf39c-108">A string that is derived from the [RFC 3066](https://go.microsoft.com/fwlink/?LinkId=132454) standard and identifies either a language or a language-region.</span></span> <span data-ttu-id="bf39c-109">Gdy jest to ten ostatni, język i region są oddzielone pojedynczy łącznik.</span><span class="sxs-lookup"><span data-stu-id="bf39c-109">When it is the latter, the language and region are separated by a single hyphen.</span></span> <span data-ttu-id="bf39c-110">Zobacz <xref:System.Windows.Markup.XmlLanguage> Aby uzyskać więcej informacji na temat wartości i formatu.</span><span class="sxs-lookup"><span data-stu-id="bf39c-110">See <xref:System.Windows.Markup.XmlLanguage> for more information about the values and format.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf39c-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bf39c-111">Remarks</span></span>  
 <span data-ttu-id="bf39c-112">Definicja `xml:lang` atrybutu w [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] jest tworzony na podstawie `xml:lang` zgodnie z definicją jako "specjalne atrybutu" [!INCLUDE[TLA#tla_w3c](../../../includes/tlasharptla-w3c-md.md)] dla [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bf39c-112">The definition for the `xml:lang` attribute in [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] is derived from `xml:lang` as defined as a "special attribute" by the [!INCLUDE[TLA#tla_w3c](../../../includes/tlasharptla-w3c-md.md)] for [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)].</span></span> <span data-ttu-id="bf39c-113">Informacje o języku i kulturze potencjalnie jest przetwarzany na różne sposoby przez elementy, w zależności od ich implementacji; jednak nie jest domyślnie [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] przetwarzanie `xml:lang` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="bf39c-113">Language and culture information is potentially processed in different ways by elements, depending on their implementations; however, there is no default [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] processing of the `xml:lang` attribute.</span></span>  
  
 <span data-ttu-id="bf39c-114">Wartość domyślna `xml:lang` atrybut jest pusty ciąg na poziomie atrybutu.</span><span class="sxs-lookup"><span data-stu-id="bf39c-114">The default value of the `xml:lang` attribute is an empty string at the attribute level.</span></span>  
  
 <span data-ttu-id="bf39c-115">`xml:lang` Efekty atrybutu i wartość atrybutu zazwyczaj są perpetuated do elementów podrzędnych, kiedy interpretowane przez systemy, które działają w `xml:lang` wartości.</span><span class="sxs-lookup"><span data-stu-id="bf39c-115">The `xml:lang` attribute effects and the value of the attribute are generally perpetuated to child elements, when interpreted by systems that act on `xml:lang` values.</span></span>  
  
 <span data-ttu-id="bf39c-116">Kiedy interpretowane przez autorów XAML usług .NET Framework XAML, `xml:lang` można utworzyć wartości <xref:System.Windows.Markup.XmlLanguage> lub <xref:System.Globalization.CultureInfo> obiektów w źródłowym obiekcie reprezentacji; jednak to zachowanie zależy od tego, czy wartość określona dla `xml:lang`składa się z prawidłową dla tych klas.</span><span class="sxs-lookup"><span data-stu-id="bf39c-116">When interpreted by XAML writers of .NET Framework XAML Services, an `xml:lang` value can create <xref:System.Windows.Markup.XmlLanguage> or <xref:System.Globalization.CultureInfo> objects in the underlying object representation; however, that behavior depends on whether the value specified for `xml:lang` is a valid construction for those classes.</span></span>  
  
 <span data-ttu-id="bf39c-117">Platformy można utworzyć skojarzenia między właściwościami zdefiniowanych i znaczenie `xml:lang` w formacie XML, stosując <xref:System.Windows.Markup.XmlLangPropertyAttribute> do właściwości.</span><span class="sxs-lookup"><span data-stu-id="bf39c-117">Frameworks can create associations between framework-defined properties and the meaning of `xml:lang` in XML by applying <xref:System.Windows.Markup.XmlLangPropertyAttribute> to the property.</span></span>  
  
## <a name="wpf-usage-nodes"></a><span data-ttu-id="bf39c-118">Węzły użycia WPF</span><span class="sxs-lookup"><span data-stu-id="bf39c-118">WPF Usage Nodes</span></span>  
 <span data-ttu-id="bf39c-119">Dla elementów, które są pochodne klasy <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement>, można użyć odpowiednik <xref:System.Windows.FrameworkElement.Language%2A> właściwość zależności zamiast `xml:lang` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="bf39c-119">For elements that are derived classes of <xref:System.Windows.FrameworkElement> or <xref:System.Windows.FrameworkContentElement>, you can use the equivalent <xref:System.Windows.FrameworkElement.Language%2A> dependency property instead of the `xml:lang` attribute.</span></span> <span data-ttu-id="bf39c-120">Domyślnie <xref:System.Windows.FrameworkElement.Language%2A> właściwość używa "en US", jeśli nie jest w przeciwnym razie ustawiona, za pomocą właściwości lub za pośrednictwem przetwarzania `xml:lang` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="bf39c-120">By default, the <xref:System.Windows.FrameworkElement.Language%2A> property uses "en-US" if it is not otherwise set, either through the property or through processing the `xml:lang` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf39c-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bf39c-121">See also</span></span>
- [<span data-ttu-id="bf39c-122">Globalizacja dla WPF</span><span class="sxs-lookup"><span data-stu-id="bf39c-122">Globalization for WPF</span></span>](../wpf/advanced/globalization-for-wpf.md)
