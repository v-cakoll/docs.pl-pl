---
title: xml:lang — Obsługa w XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:lang attribute
- xml:lang attribute [XAML Services]
- RFC 3066 standard [XAML Services]
- standards [XAML Services], RFC 3066
ms.assetid: 7aac0078-a1c5-41f8-b8b0-975510d9dca0
ms.openlocfilehash: b5a06adbb7cb874bc09899118f13b91fbec7a85e
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071445"
---
# <a name="xmllang-handling-in-xaml"></a><span data-ttu-id="4c6c5-102">xml:lang — Obsługa w XAML</span><span class="sxs-lookup"><span data-stu-id="4c6c5-102">xml:lang Handling in XAML</span></span>

<span data-ttu-id="4c6c5-103">Atrybut `xml:lang` jest atrybutem zdefiniowanym przez XML, który deklaruje informacje o języku i kulturze dla elementu w języku XML.</span><span class="sxs-lookup"><span data-stu-id="4c6c5-103">The `xml:lang` attribute is an XML-defined attribute that declares the language and culture information for an element in XML.</span></span> <span data-ttu-id="4c6c5-104">To samo znaczenie atrybutu utrzymuje się w XAML; istnieją jednak pewne dodatkowe kwestie.</span><span class="sxs-lookup"><span data-stu-id="4c6c5-104">This same meaning of the attribute persists in XAML; however, some additional considerations apply.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="4c6c5-105">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="4c6c5-105">XAML Attribute Usage</span></span>

```xaml
<object xml:lang="rfc3066lang" />
```

## <a name="xaml-values"></a><span data-ttu-id="4c6c5-106">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="4c6c5-106">XAML Values</span></span>

|||
|-|-|
|<span data-ttu-id="4c6c5-107">*rfc3066lang*</span><span class="sxs-lookup"><span data-stu-id="4c6c5-107">*rfc3066lang*</span></span>|<span data-ttu-id="4c6c5-108">Ciąg, który jest pochodną standardu [RFC 3066](https://www.ietf.org/rfc/rfc3066.txt) i identyfikuje język lub region języka.</span><span class="sxs-lookup"><span data-stu-id="4c6c5-108">A string that is derived from the [RFC 3066](https://www.ietf.org/rfc/rfc3066.txt) standard and identifies either a language or a language-region.</span></span> <span data-ttu-id="4c6c5-109">Gdy jest to ostatni, język i region są oddzielone pojedynczym łącznikiem.</span><span class="sxs-lookup"><span data-stu-id="4c6c5-109">When it is the latter, the language and region are separated by a single hyphen.</span></span> <span data-ttu-id="4c6c5-110">Zobacz <xref:System.Windows.Markup.XmlLanguage> więcej informacji na temat wartości i formatu.</span><span class="sxs-lookup"><span data-stu-id="4c6c5-110">See <xref:System.Windows.Markup.XmlLanguage> for more information about the values and format.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4c6c5-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4c6c5-111">Remarks</span></span>

<span data-ttu-id="4c6c5-112">Definicja atrybutu `xml:lang` w [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] pochodzi od `xml:lang` zdefiniowane jako "atrybut specjalny" przez Konsorcjum Sieci World Wide Web (W3C) dla XML.</span><span class="sxs-lookup"><span data-stu-id="4c6c5-112">The definition for the `xml:lang` attribute in [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] is derived from `xml:lang` as defined as a "special attribute" by the World Wide Web Consortium (W3C) for XML.</span></span> <span data-ttu-id="4c6c5-113">Informacje o języku i kulturze są potencjalnie przetwarzane na różne sposoby przez elementy, w zależności od ich implementacji; jednak nie ma [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] domyślnego `xml:lang` przetwarzania atrybutu.</span><span class="sxs-lookup"><span data-stu-id="4c6c5-113">Language and culture information is potentially processed in different ways by elements, depending on their implementations; however, there is no default [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] processing of the `xml:lang` attribute.</span></span>

<span data-ttu-id="4c6c5-114">Domyślną wartością `xml:lang` atrybutu jest pusty ciąg na poziomie atrybutu.</span><span class="sxs-lookup"><span data-stu-id="4c6c5-114">The default value of the `xml:lang` attribute is an empty string at the attribute level.</span></span>

<span data-ttu-id="4c6c5-115">Efekty `xml:lang` atrybutów i wartość atrybutu są zazwyczaj utrwalane do elementów podrzędnych, podczas `xml:lang` gdy są interpretowane przez systemy, które działają na wartości.</span><span class="sxs-lookup"><span data-stu-id="4c6c5-115">The `xml:lang` attribute effects and the value of the attribute are generally perpetuated to child elements, when interpreted by systems that act on `xml:lang` values.</span></span>

<span data-ttu-id="4c6c5-116">Podczas interpretowania przez moduły zapisu xaml `xml:lang` usług .NET XAML Services, wartość może tworzyć <xref:System.Windows.Markup.XmlLanguage> lub <xref:System.Globalization.CultureInfo> obiekty w reprezentacji obiektu źródłowego; jednak to zachowanie zależy od tego, czy wartość określona dla `xml:lang` jest prawidłową konstrukcją dla tych klas.</span><span class="sxs-lookup"><span data-stu-id="4c6c5-116">When interpreted by XAML writers of .NET XAML Services, an `xml:lang` value can create <xref:System.Windows.Markup.XmlLanguage> or <xref:System.Globalization.CultureInfo> objects in the underlying object representation; however, that behavior depends on whether the value specified for `xml:lang` is a valid construction for those classes.</span></span>

<span data-ttu-id="4c6c5-117">Frameworks można utworzyć skojarzenia między właściwości zdefiniowane `xml:lang` przez ramy i <xref:System.Windows.Markup.XmlLangPropertyAttribute> znaczenie w XML, stosując do właściwości.</span><span class="sxs-lookup"><span data-stu-id="4c6c5-117">Frameworks can create associations between framework-defined properties and the meaning of `xml:lang` in XML by applying <xref:System.Windows.Markup.XmlLangPropertyAttribute> to the property.</span></span>

## <a name="wpf-usage-nodes"></a><span data-ttu-id="4c6c5-118">Węzły użycia WPF</span><span class="sxs-lookup"><span data-stu-id="4c6c5-118">WPF Usage Nodes</span></span>

<span data-ttu-id="4c6c5-119">Dla elementów, które <xref:System.Windows.FrameworkElement> są <xref:System.Windows.FrameworkContentElement>klasy pochodne <xref:System.Windows.FrameworkElement.Language%2A> lub , można użyć `xml:lang` właściwości równoważne zależności zamiast atrybutu.</span><span class="sxs-lookup"><span data-stu-id="4c6c5-119">For elements that are derived classes of <xref:System.Windows.FrameworkElement> or <xref:System.Windows.FrameworkContentElement>, you can use the equivalent <xref:System.Windows.FrameworkElement.Language%2A> dependency property instead of the `xml:lang` attribute.</span></span> <span data-ttu-id="4c6c5-120">Domyślnie <xref:System.Windows.FrameworkElement.Language%2A> właściwość używa "en-US", jeśli nie jest w inny sposób ustawiona, za pośrednictwem właściwości lub poprzez przetwarzanie atrybutu. `xml:lang`</span><span class="sxs-lookup"><span data-stu-id="4c6c5-120">By default, the <xref:System.Windows.FrameworkElement.Language%2A> property uses "en-US" if it is not otherwise set, either through the property or through processing the `xml:lang` attribute.</span></span>

## <a name="see-also"></a><span data-ttu-id="4c6c5-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4c6c5-121">See also</span></span>

- [<span data-ttu-id="4c6c5-122">Globalizacja dla WPF</span><span class="sxs-lookup"><span data-stu-id="4c6c5-122">Globalization for WPF</span></span>](../../framework/wpf/advanced/globalization-for-wpf.md)
