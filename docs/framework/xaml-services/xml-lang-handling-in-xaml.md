---
title: xml:lang — Obsługa w XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:lang attribute
- xml:lang attribute [XAML Services]
- RFC 3066 standard [XAML Services]
- standards [XAML Services], RFC 3066
ms.assetid: 7aac0078-a1c5-41f8-b8b0-975510d9dca0
ms.openlocfilehash: 3af85f298f7581146b5ecc8a559b185f1a01e54c
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2019
ms.locfileid: "72919999"
---
# <a name="xmllang-handling-in-xaml"></a><span data-ttu-id="28fc0-102">xml:lang — Obsługa w XAML</span><span class="sxs-lookup"><span data-stu-id="28fc0-102">xml:lang Handling in XAML</span></span>
<span data-ttu-id="28fc0-103">Atrybut `xml:lang` jest atrybutem zdefiniowanym przez [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)], który deklaruje informacje o języku i kulturze dla elementu w formacie XML.</span><span class="sxs-lookup"><span data-stu-id="28fc0-103">The `xml:lang` attribute is an [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)]-defined attribute that declares the language and culture information for an element in XML.</span></span> <span data-ttu-id="28fc0-104">Takie samo znaczenie atrybutu utrzymuje się w języku XAML; Niektóre dodatkowe zagadnienia są jednak stosowane.</span><span class="sxs-lookup"><span data-stu-id="28fc0-104">This same meaning of the attribute persists in XAML; however, some additional considerations apply.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="28fc0-105">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="28fc0-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object xml:lang="rfc3066lang" />  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="28fc0-106">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="28fc0-106">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="28fc0-107">*rfc3066lang*</span><span class="sxs-lookup"><span data-stu-id="28fc0-107">*rfc3066lang*</span></span>|<span data-ttu-id="28fc0-108">Ciąg pochodzący ze standardu [RFC 3066](https://go.microsoft.com/fwlink/?LinkId=132454) i identyfikujący język lub region języka.</span><span class="sxs-lookup"><span data-stu-id="28fc0-108">A string that is derived from the [RFC 3066](https://go.microsoft.com/fwlink/?LinkId=132454) standard and identifies either a language or a language-region.</span></span> <span data-ttu-id="28fc0-109">Gdy jest to ostatni, język i region są rozdzielone pojedynczym łącznikiem.</span><span class="sxs-lookup"><span data-stu-id="28fc0-109">When it is the latter, the language and region are separated by a single hyphen.</span></span> <span data-ttu-id="28fc0-110">Aby uzyskać więcej informacji na temat wartości i formatu, zobacz <xref:System.Windows.Markup.XmlLanguage>.</span><span class="sxs-lookup"><span data-stu-id="28fc0-110">See <xref:System.Windows.Markup.XmlLanguage> for more information about the values and format.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28fc0-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="28fc0-111">Remarks</span></span>  
 <span data-ttu-id="28fc0-112">Definicja atrybutu `xml:lang` w [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] pochodzi od `xml:lang`, jak określono jako "atrybut specjalny" przez organizacja World Wide Web Consortium (W3C) dla [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="28fc0-112">The definition for the `xml:lang` attribute in [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] is derived from `xml:lang` as defined as a "special attribute" by the World Wide Web Consortium (W3C) for [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)].</span></span> <span data-ttu-id="28fc0-113">Informacje o języku i kulturze mogą być przetwarzane na różne sposoby według elementów, w zależności od ich implementacji; nie ma jednak domyślnego przetwarzania [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] atrybutu `xml:lang`.</span><span class="sxs-lookup"><span data-stu-id="28fc0-113">Language and culture information is potentially processed in different ways by elements, depending on their implementations; however, there is no default [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] processing of the `xml:lang` attribute.</span></span>  
  
 <span data-ttu-id="28fc0-114">Wartość domyślna atrybutu `xml:lang` jest ciągiem pustym na poziomie atrybutu.</span><span class="sxs-lookup"><span data-stu-id="28fc0-114">The default value of the `xml:lang` attribute is an empty string at the attribute level.</span></span>  
  
 <span data-ttu-id="28fc0-115">`xml:lang` efekty atrybutu i wartość atrybutu są zwykle perpetuated do elementów podrzędnych, gdy są interpretowane przez systemy, które działają na wartościach `xml:lang`.</span><span class="sxs-lookup"><span data-stu-id="28fc0-115">The `xml:lang` attribute effects and the value of the attribute are generally perpetuated to child elements, when interpreted by systems that act on `xml:lang` values.</span></span>  
  
 <span data-ttu-id="28fc0-116">W przypadku interpretowania przez autorów XAML .NET Framework usług XAML, `xml:lang` wartość może tworzyć obiekty <xref:System.Windows.Markup.XmlLanguage> lub <xref:System.Globalization.CultureInfo> w reprezentacji bazowego obiektu; jednak takie zachowanie zależy od tego, czy wartość określona dla `xml:lang` jest prawidłową konstrukcją dla tych klas.</span><span class="sxs-lookup"><span data-stu-id="28fc0-116">When interpreted by XAML writers of .NET Framework XAML Services, an `xml:lang` value can create <xref:System.Windows.Markup.XmlLanguage> or <xref:System.Globalization.CultureInfo> objects in the underlying object representation; however, that behavior depends on whether the value specified for `xml:lang` is a valid construction for those classes.</span></span>  
  
 <span data-ttu-id="28fc0-117">Struktury programu mogą tworzyć skojarzenia między właściwościami zdefiniowanymi przez platformę i znaczenie `xml:lang` w kodzie XML przez zastosowanie <xref:System.Windows.Markup.XmlLangPropertyAttribute> do właściwości.</span><span class="sxs-lookup"><span data-stu-id="28fc0-117">Frameworks can create associations between framework-defined properties and the meaning of `xml:lang` in XML by applying <xref:System.Windows.Markup.XmlLangPropertyAttribute> to the property.</span></span>  
  
## <a name="wpf-usage-nodes"></a><span data-ttu-id="28fc0-118">Węzły użycia WPF</span><span class="sxs-lookup"><span data-stu-id="28fc0-118">WPF Usage Nodes</span></span>  
 <span data-ttu-id="28fc0-119">Dla elementów, które są klasami pochodnymi <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement>, można użyć równoważnej właściwości zależności <xref:System.Windows.FrameworkElement.Language%2A> zamiast atrybutu `xml:lang`.</span><span class="sxs-lookup"><span data-stu-id="28fc0-119">For elements that are derived classes of <xref:System.Windows.FrameworkElement> or <xref:System.Windows.FrameworkContentElement>, you can use the equivalent <xref:System.Windows.FrameworkElement.Language%2A> dependency property instead of the `xml:lang` attribute.</span></span> <span data-ttu-id="28fc0-120">Domyślnie właściwość <xref:System.Windows.FrameworkElement.Language%2A> używa wartości "pl-US", jeśli nie została ustawiona inaczej, przez właściwość lub poprzez przetwarzanie atrybutu `xml:lang`.</span><span class="sxs-lookup"><span data-stu-id="28fc0-120">By default, the <xref:System.Windows.FrameworkElement.Language%2A> property uses "en-US" if it is not otherwise set, either through the property or through processing the `xml:lang` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28fc0-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="28fc0-121">See also</span></span>

- [<span data-ttu-id="28fc0-122">Globalizacja dla WPF</span><span class="sxs-lookup"><span data-stu-id="28fc0-122">Globalization for WPF</span></span>](../wpf/advanced/globalization-for-wpf.md)
