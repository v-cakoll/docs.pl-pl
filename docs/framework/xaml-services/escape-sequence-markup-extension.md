---
title: '{} Znak ucieczki sekwencja — rozszerzenie znaczników'
ms.date: 03/30/2017
f1_keywords:
- '{}'
helpviewer_keywords:
- XAML [XAML Services], quotation mark (")
- '{} escape sequence [XAML Services]'
- XAML [XAML Services], {} escape sequence
- XAML [XAML Services], escape sequence
- quotation mark (") [XAML Services]
- escape sequence [XAML Services]
ms.assetid: 3ce3e2ad-a868-43f9-9c98-b29561cb146e
ms.openlocfilehash: 8a065573abb5a230d2a51f1767bd8d2e829bccd2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521273"
---
# <a name="-escape-sequence--markup-extension"></a><span data-ttu-id="4a07a-102">{} Sekwencja unikowa / rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="4a07a-102">{} Escape Sequence / Markup Extension</span></span>
<span data-ttu-id="4a07a-103">Sekwencja unikowa XAML zawiera wartości atrybutów.</span><span class="sxs-lookup"><span data-stu-id="4a07a-103">Provides the XAML escape sequence for attribute values.</span></span> <span data-ttu-id="4a07a-104">Sekwencja unikowa umożliwia kolejnych wartości w atrybucie należy interpretować jako literał.</span><span class="sxs-lookup"><span data-stu-id="4a07a-104">The escape sequence allows the subsequent values in the attribute to be interpreted as a literal.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="4a07a-105">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="4a07a-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{} literalValue" .../>  
```  
  
## <a name="xaml-property-element-usage"></a><span data-ttu-id="4a07a-106">Użycie elementu właściwości języka XAML</span><span class="sxs-lookup"><span data-stu-id="4a07a-106">XAML Property Element Usage</span></span>  
  
```  
<object>  
  <object.property>  
    {} literalValue  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="4a07a-107">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="4a07a-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4a07a-108">*literalValue*</span><span class="sxs-lookup"><span data-stu-id="4a07a-108">*literalValue*</span></span>|<span data-ttu-id="4a07a-109">Literał ciągu następujący sekwencji unikowej.</span><span class="sxs-lookup"><span data-stu-id="4a07a-109">The literal string that follows the escape sequence.</span></span> <span data-ttu-id="4a07a-110">Ten ciąg zawiera zazwyczaj otwierania lub zamykania nawias klamrowy ({lub}).</span><span class="sxs-lookup"><span data-stu-id="4a07a-110">Typically this string contains an open or close brace ({ or }).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a07a-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4a07a-111">Remarks</span></span>  
 <span data-ttu-id="4a07a-112">Sekwencja unikowa ({}) jest używany, tak aby otwierający nawias klamrowy ({}) może być używany jako znak literałowy, w XAML.</span><span class="sxs-lookup"><span data-stu-id="4a07a-112">The escape sequence ({}) is used so that an open brace ({)can be used as a literal character in XAML.</span></span>  
  
 <span data-ttu-id="4a07a-113">Czytelnicy XAML zazwyczaj używają otwierający nawias klamrowy ({}) do określenia punktu wejścia rozszerzenia znaczników; jednak najpierw sprawdzają następny znak w celu ustalenia, czy jest ono zamykającego nawiasu klamrowego (}).</span><span class="sxs-lookup"><span data-stu-id="4a07a-113">XAML readers typically use the open brace ({) to denote the entry point of a markup extension; however, they first check the next character to determine whether it is a closing brace (}).</span></span> <span data-ttu-id="4a07a-114">Tylko wtedy, gdy dwa nawiasów ({}) czy sąsiadujących, są one traktowane jako sekwencji unikowej.</span><span class="sxs-lookup"><span data-stu-id="4a07a-114">Only when the two braces ({}) are adjacent, are they considered an escape sequence.</span></span>  
  
 <span data-ttu-id="4a07a-115">Jeśli sekwencja unikowa czytnika XAML ma być przetwarzana w pozostałej części ciągu jako ciąg.</span><span class="sxs-lookup"><span data-stu-id="4a07a-115">If the escape sequence is encountered, the XAML reader should process the remainder of the string as a string.</span></span> <span data-ttu-id="4a07a-116">Jednak jeśli sekwencja unikowa jest stosowany do składowej, która ma konwertera typów, ciąg może zostać poddane konwersji typu, gdy jest on interpretowany przez Edytor XAML.</span><span class="sxs-lookup"><span data-stu-id="4a07a-116">However, if the escape sequence is applied to a member that has a type converter, the string might undergo type conversion when it is interpreted by a XAML writer.</span></span>  
  
 <span data-ttu-id="4a07a-117">Sekwencja unikowa nie jest rozszerzeniem znacznika i nie jest obsługiwane przez klasę.</span><span class="sxs-lookup"><span data-stu-id="4a07a-117">The escape sequence is not a markup extension and is not backed by a class.</span></span> <span data-ttu-id="4a07a-118">Jest jednak Konwencji, który należy przestrzegać czytelnicy XAML (w tym niestandardowych czytelnicy XAML).</span><span class="sxs-lookup"><span data-stu-id="4a07a-118">However, it is a convention that XAML readers (including custom XAML readers) should respect.</span></span>  
  
 <span data-ttu-id="4a07a-119">Znak cudzysłowu (") nie może służyć jako sekwencja unikowa w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="4a07a-119">A quotation mark (") cannot be used as an escape sequence in this manner.</span></span> <span data-ttu-id="4a07a-120">Jeśli musisz ustawić znak cudzysłowu jako wartość właściwości dla właściwości noncontent, należy użyć składni elementu właściwości i umieścić znak cudzysłowu jako ciąg w elemencie właściwości lub Użyj jednostki znaków XML.</span><span class="sxs-lookup"><span data-stu-id="4a07a-120">If you need to set a quotation mark as a property value for a noncontent property, use property element syntax and place the quotation mark as a string inside the property element, or use an XML character entity.</span></span> <span data-ttu-id="4a07a-121">Właściwość zawartości znaku cudzysłowu mogą być całej zawartości.</span><span class="sxs-lookup"><span data-stu-id="4a07a-121">For a content property, the quotation mark can be the entire content.</span></span>  
  
 <span data-ttu-id="4a07a-122">Sekwencja unikowa ({}) często jest wymagany podczas określania typu XML, który musi zawierać kwalifikator przestrzeni nazw w miejscu, gdzie mogą być wyświetlane jako rozszerzenie znacznika XAML.</span><span class="sxs-lookup"><span data-stu-id="4a07a-122">The escape sequence ({}) is frequently required when specifying an XML type that must include a namespace qualifier in a location where a XAML markup extension might appear.</span></span> <span data-ttu-id="4a07a-123">Dotyczy to również początku wartości atrybutu XAML oraz rozszerzeniem znacznika bezpośrednio po znaku równości (=).</span><span class="sxs-lookup"><span data-stu-id="4a07a-123">This includes the start of a XAML attribute value, and in a markup extension, immediately after an equal sign (=).</span></span> <span data-ttu-id="4a07a-124">Poniższy przykład pokazuje sekwencji unikowych dla przestrzeni nazw XML, który pojawia się na początku wartości atrybutu XAML.</span><span class="sxs-lookup"><span data-stu-id="4a07a-124">The following example shows escape sequences for an XML namespace that appears at the start of a XAML attribute value.</span></span>  
  
 [!code-xaml[XLINQExample#StackPanelResources](../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
  
## <a name="see-also"></a><span data-ttu-id="4a07a-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4a07a-125">See also</span></span>
- [<span data-ttu-id="4a07a-126">Typy konwerterów i rozszerzenia znaczników dla XAML</span><span class="sxs-lookup"><span data-stu-id="4a07a-126">Type Converters and Markup Extensions for XAML</span></span>](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)
- [<span data-ttu-id="4a07a-127">Jednostki znaków XML i XAML</span><span class="sxs-lookup"><span data-stu-id="4a07a-127">XML Character Entities and XAML</span></span>](../../../docs/framework/xaml-services/xml-character-entities-and-xaml.md)
