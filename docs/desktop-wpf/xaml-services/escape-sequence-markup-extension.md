---
title: '{}Sekwencja ucieczki — rozszerzenie znaczników'
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
ms.openlocfilehash: f84243994557d76fa52d72b060a1ba35460e98b0
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071746"
---
# <a name="-escape-sequence--markup-extension"></a><span data-ttu-id="b2f87-102">{}Rozszerzenie sekwencji ucieczki / znaczników</span><span class="sxs-lookup"><span data-stu-id="b2f87-102">{} Escape sequence / markup extension</span></span>

<span data-ttu-id="b2f87-103">Udostępnia sekwencję unikową XAML dla wartości atrybutów.</span><span class="sxs-lookup"><span data-stu-id="b2f87-103">Provides the XAML escape sequence for attribute values.</span></span> <span data-ttu-id="b2f87-104">Sekwencja ucieczki umożliwia kolejne wartości w atrybucie, które mają być interpretowane jako literał.</span><span class="sxs-lookup"><span data-stu-id="b2f87-104">The escape sequence allows the subsequent values in the attribute to be interpreted as a literal.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="b2f87-105">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="b2f87-105">XAML Attribute Usage</span></span>

```xaml
<object property="{} literalValue" .../>
```

## <a name="xaml-property-element-usage"></a><span data-ttu-id="b2f87-106">Użycie elementu właściwości języka XAML</span><span class="sxs-lookup"><span data-stu-id="b2f87-106">XAML Property Element Usage</span></span>

```xaml
<object>
  <object.property>
    {} literalValue
  </object.property>
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="b2f87-107">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="b2f87-107">XAML Values</span></span>

|||
|-|-|
|<span data-ttu-id="b2f87-108">*literałValue*</span><span class="sxs-lookup"><span data-stu-id="b2f87-108">*literalValue*</span></span>|<span data-ttu-id="b2f87-109">Ciąg literał, który następuje sekwencji ucieczki.</span><span class="sxs-lookup"><span data-stu-id="b2f87-109">The literal string that follows the escape sequence.</span></span> <span data-ttu-id="b2f87-110">Zazwyczaj ten ciąg zawiera nawias klamrowy otwarty lub zamknięty ({ lub }).</span><span class="sxs-lookup"><span data-stu-id="b2f87-110">Typically this string contains an open or close brace ({ or }).</span></span>|

## <a name="remarks"></a><span data-ttu-id="b2f87-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b2f87-111">Remarks</span></span>

<span data-ttu-id="b2f87-112">Sekwencja ucieczki ({}) jest używana tak, aby otwarty nawias klamrowy ({) mógł być używany jako znak literału w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="b2f87-112">The escape sequence ({}) is used so that an open brace ({) can be used as a literal character in XAML.</span></span>

<span data-ttu-id="b2f87-113">Czytniki XAML zazwyczaj używają otwartego nawiasu klamrowego ({) do oznaczania punktu wejścia rozszerzenia znaczników; najpierw sprawdzają następny znak, aby ustalić, czy jest to nawias zamykający (}).</span><span class="sxs-lookup"><span data-stu-id="b2f87-113">XAML readers typically use the open brace ({) to denote the entry point of a markup extension; however, they first check the next character to determine whether it is a closing brace (}).</span></span> <span data-ttu-id="b2f87-114">Tylko wtedy, gdy{}dwie nawiasy klamrowe ( ) sąsiadują, są one uważane za sekwencję ucieczki.</span><span class="sxs-lookup"><span data-stu-id="b2f87-114">Only when the two braces ({}) are adjacent, are they considered an escape sequence.</span></span>

<span data-ttu-id="b2f87-115">Jeśli zostanie napotkana sekwencja ucieczki, czytnik XAML powinien przetworzyć pozostałą część ciągu jako ciąg.</span><span class="sxs-lookup"><span data-stu-id="b2f87-115">If the escape sequence is encountered, the XAML reader should process the remainder of the string as a string.</span></span> <span data-ttu-id="b2f87-116">Jeśli jednak sekwencja unikowa jest stosowana do elementu członkowskiego, który ma konwerter typów, ciąg może zostać poddany konwersji typu, gdy jest interpretowany przez moduł zapisujący XAML.</span><span class="sxs-lookup"><span data-stu-id="b2f87-116">However, if the escape sequence is applied to a member that has a type converter, the string might undergo type conversion when it is interpreted by a XAML writer.</span></span>

<span data-ttu-id="b2f87-117">Sekwencja ucieczki nie jest rozszerzeniem znaczników i nie jest wspierana przez klasę.</span><span class="sxs-lookup"><span data-stu-id="b2f87-117">The escape sequence is not a markup extension and is not backed by a class.</span></span> <span data-ttu-id="b2f87-118">Jest to jednak konwencja, którą czytelnicy XAML (w tym niestandardowe czytniki XAML) powinni przestrzegać.</span><span class="sxs-lookup"><span data-stu-id="b2f87-118">However, it is a convention that XAML readers (including custom XAML readers) should respect.</span></span>

<span data-ttu-id="b2f87-119">Cudzysłów (") nie może być używany jako sekwencja ucieczki w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="b2f87-119">A quotation mark (") cannot be used as an escape sequence in this manner.</span></span> <span data-ttu-id="b2f87-120">Jeśli chcesz ustawić cudzysłów jako wartość właściwości dla właściwości niezgodnej, użyj składni elementu właściwości i umieść cudzysłów jako ciąg wewnątrz elementu właściwości lub użyj encji znaku XML.</span><span class="sxs-lookup"><span data-stu-id="b2f87-120">If you need to set a quotation mark as a property value for a noncontent property, use property element syntax and place the quotation mark as a string inside the property element, or use an XML character entity.</span></span> <span data-ttu-id="b2f87-121">Dla właściwości zawartości cudzysłow może być całą zawartością.</span><span class="sxs-lookup"><span data-stu-id="b2f87-121">For a content property, the quotation mark can be the entire content.</span></span>

<span data-ttu-id="b2f87-122">Sekwencja ucieczki ({}) jest często wymagana przy określaniu typu XML, który musi zawierać kwalifikator obszaru nazw w lokalizacji, w której może pojawić się rozszerzenie znaczników XAML.</span><span class="sxs-lookup"><span data-stu-id="b2f87-122">The escape sequence ({}) is frequently required when specifying an XML type that must include a namespace qualifier in a location where a XAML markup extension might appear.</span></span> <span data-ttu-id="b2f87-123">Ta lokalizacja obejmuje początek wartości atrybutu XAML i w rozszerzeniu znaczników bezpośrednio po znaku równości (=).</span><span class="sxs-lookup"><span data-stu-id="b2f87-123">This location includes the start of a XAML attribute value, and in a markup extension immediately after an equal sign (=).</span></span> <span data-ttu-id="b2f87-124">Poniższy przykład przedstawia sekwencje usztywnienia dla obszaru nazw XML, który pojawia się na początku wartości atrybutu XAML.</span><span class="sxs-lookup"><span data-stu-id="b2f87-124">The following example shows escape sequences for an XML namespace that appears at the start of a XAML attribute value.</span></span>

[!code-xaml[XLINQExample#StackPanelResources](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]

## <a name="see-also"></a><span data-ttu-id="b2f87-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b2f87-125">See also</span></span>

- [<span data-ttu-id="b2f87-126">Typy konwerterów i rozszerzenia znaczników dla XAML</span><span class="sxs-lookup"><span data-stu-id="b2f87-126">Type Converters and Markup Extensions for XAML</span></span>](type-converters-and-markup-extensions.md)
- [<span data-ttu-id="b2f87-127">Jednostki znaków XML i XAML</span><span class="sxs-lookup"><span data-stu-id="b2f87-127">XML Character Entities and XAML</span></span>](xml-character-entities.md)
