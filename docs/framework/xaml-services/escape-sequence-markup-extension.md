---
title: '{}Sekwencja unikowa — rozszerzenie znaczników'
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
ms.openlocfilehash: b0646c62a1342eb160d1967e86ac286429013f3c
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053875"
---
# <a name="-escape-sequence--markup-extension"></a><span data-ttu-id="eded8-102">{}, sekwencja ucieczki/rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="eded8-102">{} Escape Sequence / Markup Extension</span></span>
<span data-ttu-id="eded8-103">Udostępnia sekwencję ucieczki XAML dla wartości atrybutów.</span><span class="sxs-lookup"><span data-stu-id="eded8-103">Provides the XAML escape sequence for attribute values.</span></span> <span data-ttu-id="eded8-104">Sekwencja ucieczki pozwala, aby kolejne wartości w atrybucie były interpretowane jako literał.</span><span class="sxs-lookup"><span data-stu-id="eded8-104">The escape sequence allows the subsequent values in the attribute to be interpreted as a literal.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="eded8-105">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="eded8-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{} literalValue" .../>  
```  
  
## <a name="xaml-property-element-usage"></a><span data-ttu-id="eded8-106">Użycie elementu właściwości języka XAML</span><span class="sxs-lookup"><span data-stu-id="eded8-106">XAML Property Element Usage</span></span>  
  
```xaml  
<object>  
  <object.property>  
    {} literalValue  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="eded8-107">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="eded8-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="eded8-108">*literalValue*</span><span class="sxs-lookup"><span data-stu-id="eded8-108">*literalValue*</span></span>|<span data-ttu-id="eded8-109">Ciąg literału, który następuje po sekwencji ucieczki.</span><span class="sxs-lookup"><span data-stu-id="eded8-109">The literal string that follows the escape sequence.</span></span> <span data-ttu-id="eded8-110">Zazwyczaj ten ciąg zawiera otwarty lub zamykający nawias klamrowy ({lub}).</span><span class="sxs-lookup"><span data-stu-id="eded8-110">Typically this string contains an open or close brace ({ or }).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eded8-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="eded8-111">Remarks</span></span>  
 <span data-ttu-id="eded8-112">Sekwencja ucieczki ({}) jest używana, aby w języku XAML można było użyć otwierającego nawiasu klamrowego ({) jako znaku literału.</span><span class="sxs-lookup"><span data-stu-id="eded8-112">The escape sequence ({}) is used so that an open brace ({)can be used as a literal character in XAML.</span></span>  
  
 <span data-ttu-id="eded8-113">Czytelnicy XAML zazwyczaj używają nawiasu otwierającego ({) do określenia punktu wejścia rozszerzenia znaczników, jednak najpierw sprawdzają następny znak, aby określić, czy jest to zamykający nawias klamrowy (}).</span><span class="sxs-lookup"><span data-stu-id="eded8-113">XAML readers typically use the open brace ({) to denote the entry point of a markup extension; however, they first check the next character to determine whether it is a closing brace (}).</span></span> <span data-ttu-id="eded8-114">Tylko wtedy, gdy dwa nawiasy{}klamrowe () są przyległe, są traktowane jako sekwencje ucieczki.</span><span class="sxs-lookup"><span data-stu-id="eded8-114">Only when the two braces ({}) are adjacent, are they considered an escape sequence.</span></span>  
  
 <span data-ttu-id="eded8-115">Jeśli zostanie wykryta sekwencja ucieczki, czytnik XAML powinien przetworzyć pozostałą część ciągu jako ciąg.</span><span class="sxs-lookup"><span data-stu-id="eded8-115">If the escape sequence is encountered, the XAML reader should process the remainder of the string as a string.</span></span> <span data-ttu-id="eded8-116">Jeśli jednak sekwencja ucieczki zostanie zastosowana do elementu członkowskiego, który ma konwerter typu, ciąg może zostać przekształcony na konwersję typu, gdy jest interpretowany przez moduł zapisujący XAML.</span><span class="sxs-lookup"><span data-stu-id="eded8-116">However, if the escape sequence is applied to a member that has a type converter, the string might undergo type conversion when it is interpreted by a XAML writer.</span></span>  
  
 <span data-ttu-id="eded8-117">Sekwencja ucieczki nie jest rozszerzeniem znaczników i nie jest obsługiwana przez klasę.</span><span class="sxs-lookup"><span data-stu-id="eded8-117">The escape sequence is not a markup extension and is not backed by a class.</span></span> <span data-ttu-id="eded8-118">Jednak jest to Konwencja, którą powinni przestrzegać czytelnicy XAML (w tym niestandardowe czytniki XAML).</span><span class="sxs-lookup"><span data-stu-id="eded8-118">However, it is a convention that XAML readers (including custom XAML readers) should respect.</span></span>  
  
 <span data-ttu-id="eded8-119">W ten sposób nie można użyć znaku cudzysłowu (") jako sekwencji unikowej.</span><span class="sxs-lookup"><span data-stu-id="eded8-119">A quotation mark (") cannot be used as an escape sequence in this manner.</span></span> <span data-ttu-id="eded8-120">Jeśli musisz ustawić znak cudzysłowu jako wartość właściwości dla właściwości niezawartości, użyj składni elementu właściwości i umieść znak cudzysłowu jako ciąg wewnątrz elementu Property lub Użyj jednostki znaku XML.</span><span class="sxs-lookup"><span data-stu-id="eded8-120">If you need to set a quotation mark as a property value for a noncontent property, use property element syntax and place the quotation mark as a string inside the property element, or use an XML character entity.</span></span> <span data-ttu-id="eded8-121">W przypadku właściwości content cudzysłowem może być cała zawartość.</span><span class="sxs-lookup"><span data-stu-id="eded8-121">For a content property, the quotation mark can be the entire content.</span></span>  
  
 <span data-ttu-id="eded8-122">Sekwencja ucieczki ({}) jest często wymagana podczas określania typu XML, który musi zawierać kwalifikator przestrzeni nazw w lokalizacji, w której może się pojawić rozszerzenie XAML markup.</span><span class="sxs-lookup"><span data-stu-id="eded8-122">The escape sequence ({}) is frequently required when specifying an XML type that must include a namespace qualifier in a location where a XAML markup extension might appear.</span></span> <span data-ttu-id="eded8-123">Obejmuje to początek wartości atrybutu XAML i w rozszerzeniu znacznika bezpośrednio po znaku równości (=).</span><span class="sxs-lookup"><span data-stu-id="eded8-123">This includes the start of a XAML attribute value, and in a markup extension, immediately after an equal sign (=).</span></span> <span data-ttu-id="eded8-124">Poniższy przykład pokazuje sekwencje ucieczki dla przestrzeni nazw XML, która pojawia się na początku wartości atrybutu XAML.</span><span class="sxs-lookup"><span data-stu-id="eded8-124">The following example shows escape sequences for an XML namespace that appears at the start of a XAML attribute value.</span></span>  
  
 [!code-xaml[XLINQExample#StackPanelResources](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
  
## <a name="see-also"></a><span data-ttu-id="eded8-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eded8-125">See also</span></span>

- [<span data-ttu-id="eded8-126">Typy konwerterów i rozszerzenia znaczników dla XAML</span><span class="sxs-lookup"><span data-stu-id="eded8-126">Type Converters and Markup Extensions for XAML</span></span>](type-converters-and-markup-extensions-for-xaml.md)
- [<span data-ttu-id="eded8-127">Jednostki znaków XML i XAML</span><span class="sxs-lookup"><span data-stu-id="eded8-127">XML Character Entities and XAML</span></span>](xml-character-entities-and-xaml.md)
