---
title: "{} Sekwencja unikowa — rozszerzenie znaczników"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: '{}'
helpviewer_keywords:
- XAML [XAML Services], quotation mark (")
- '{} escape sequence [XAML Services]'
- XAML [XAML Services], {} escape sequence
- XAML [XAML Services], escape sequence
- quotation mark (") [XAML Services]
- escape sequence [XAML Services]
ms.assetid: 3ce3e2ad-a868-43f9-9c98-b29561cb146e
caps.latest.revision: "21"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8419a1e89d5e94b9868b0fd1fb81540253efca5d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="-escape-sequence--markup-extension"></a><span data-ttu-id="57bb9-102">{} Sekwencja unikowa / rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="57bb9-102">{} Escape Sequence / Markup Extension</span></span>
<span data-ttu-id="57bb9-103">Udostępnia sekwencji unikowej XAML dla wartości atrybutu.</span><span class="sxs-lookup"><span data-stu-id="57bb9-103">Provides the XAML escape sequence for attribute values.</span></span> <span data-ttu-id="57bb9-104">Sekwencja specjalna umożliwia kolejnych wartości w atrybucie interpretowane jako literału.</span><span class="sxs-lookup"><span data-stu-id="57bb9-104">The escape sequence allows the subsequent values in the attribute to be interpreted as a literal.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="57bb9-105">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="57bb9-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{} literalValue" .../>  
```  
  
## <a name="xaml-property-element-usage"></a><span data-ttu-id="57bb9-106">Użycie elementu właściwości języka XAML</span><span class="sxs-lookup"><span data-stu-id="57bb9-106">XAML Property Element Usage</span></span>  
  
```  
<object>  
  <object.property>  
    {} literalValue  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="57bb9-107">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="57bb9-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="57bb9-108">*literalValue*</span><span class="sxs-lookup"><span data-stu-id="57bb9-108">*literalValue*</span></span>|<span data-ttu-id="57bb9-109">Literał znajdujący się sekwencji ucieczki.</span><span class="sxs-lookup"><span data-stu-id="57bb9-109">The literal string that follows the escape sequence.</span></span> <span data-ttu-id="57bb9-110">Zazwyczaj ten ciąg zawiera otwierania lub zamykania nawiasu klamrowego ({lub}).</span><span class="sxs-lookup"><span data-stu-id="57bb9-110">Typically this string contains an open or close brace ({ or }).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57bb9-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="57bb9-111">Remarks</span></span>  
 <span data-ttu-id="57bb9-112">Sekwencja specjalna ({}) jest używany, aby otwierający nawias klamrowy ({}) może być używany jako znak w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="57bb9-112">The escape sequence ({}) is used so that an open brace ({)can be used as a literal character in XAML.</span></span>  
  
 <span data-ttu-id="57bb9-113">Czytniki XAML zwykle otwierający nawias klamrowy ({}) do określenia punktu wejścia rozszerzenia znacznika; jednak najpierw sprawdzają następny znak w celu ustalenia, czy jest ono zamykający nawias klamrowy (}).</span><span class="sxs-lookup"><span data-stu-id="57bb9-113">XAML readers typically use the open brace ({) to denote the entry point of a markup extension; however, they first check the next character to determine whether it is a closing brace (}).</span></span> <span data-ttu-id="57bb9-114">Tylko wtedy, gdy dwa nawiasy klamrowe ({}) znajdują się obok siebie, są one traktowane jako sekwencja ucieczki.</span><span class="sxs-lookup"><span data-stu-id="57bb9-114">Only when the two braces ({}) are adjacent, are they considered an escape sequence.</span></span>  
  
 <span data-ttu-id="57bb9-115">W przypadku sekwencji ucieczki czytnika XAML ma być przetwarzane w pozostałej części ciągu jako ciąg.</span><span class="sxs-lookup"><span data-stu-id="57bb9-115">If the escape sequence is encountered, the XAML reader should process the remainder of the string as a string.</span></span> <span data-ttu-id="57bb9-116">Jednak jeśli sekwencja specjalna jest stosowany do elementu członkowskiego, który ma konwertera typów, ciąg mogą być konwersji typu, gdy jest interpretowany przez moduł zapisujący XAML.</span><span class="sxs-lookup"><span data-stu-id="57bb9-116">However, if the escape sequence is applied to a member that has a type converter, the string might undergo type conversion when it is interpreted by a XAML writer.</span></span>  
  
 <span data-ttu-id="57bb9-117">Sekwencja specjalna nie jest rozszerzeniem znacznika i nie jest ona obsługiwana przez klasę.</span><span class="sxs-lookup"><span data-stu-id="57bb9-117">The escape sequence is not a markup extension and is not backed by a class.</span></span> <span data-ttu-id="57bb9-118">Jest jednak Konwencji, która powinna być zgodna czytników XAML (w tym niestandardowe czytników XAML).</span><span class="sxs-lookup"><span data-stu-id="57bb9-118">However, it is a convention that XAML readers (including custom XAML readers) should respect.</span></span>  
  
 <span data-ttu-id="57bb9-119">Znak cudzysłowu (") nie można użyć jako sekwencję ucieczki w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="57bb9-119">A quotation mark (") cannot be used as an escape sequence in this manner.</span></span> <span data-ttu-id="57bb9-120">Należy ustawić znak cudzysłowu jako wartość właściwości dla właściwości noncontent, należy użyć składni elementu właściwości i umieścić cudzysłów jako ciąg w elemencie właściwości lub Użyj jednostki znaków XML.</span><span class="sxs-lookup"><span data-stu-id="57bb9-120">If you need to set a quotation mark as a property value for a noncontent property, use property element syntax and place the quotation mark as a string inside the property element, or use an XML character entity.</span></span> <span data-ttu-id="57bb9-121">Dla właściwości content znaku cudzysłowu można całej zawartości.</span><span class="sxs-lookup"><span data-stu-id="57bb9-121">For a content property, the quotation mark can be the entire content.</span></span>  
  
 <span data-ttu-id="57bb9-122">Sekwencja specjalna ({}) jest często wymagana podczas określania typu XML, który musi zawierać kwalifikatora przestrzeni nazw w lokalizacji, gdzie mogą być wyświetlane rozszerzenie znaczników w XAML.</span><span class="sxs-lookup"><span data-stu-id="57bb9-122">The escape sequence ({}) is frequently required when specifying an XML type that must include a namespace qualifier in a location where a XAML markup extension might appear.</span></span> <span data-ttu-id="57bb9-123">Początek wartości atrybutu XAML, a w rozszerzeniu znacznika, w tym bezpośrednio po znaku równości (=).</span><span class="sxs-lookup"><span data-stu-id="57bb9-123">This includes the start of a XAML attribute value, and in a markup extension, immediately after an equal sign (=).</span></span> <span data-ttu-id="57bb9-124">W poniższym przykładzie przedstawiono sekwencji ucieczki dla przestrzeni nazw XML, który pojawia się na początku wartości atrybutu XAML.</span><span class="sxs-lookup"><span data-stu-id="57bb9-124">The following example shows escape sequences for an XML namespace that appears at the start of a XAML attribute value.</span></span>  
  
 [!code-xaml[XLINQExample#StackPanelResources](../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
  
## <a name="see-also"></a><span data-ttu-id="57bb9-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="57bb9-125">See Also</span></span>  
 [<span data-ttu-id="57bb9-126">Typy konwerterów i rozszerzenia znaczników dla XAML</span><span class="sxs-lookup"><span data-stu-id="57bb9-126">Type Converters and Markup Extensions for XAML</span></span>](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)  
 [<span data-ttu-id="57bb9-127">Jednostki znaków XML i XAML</span><span class="sxs-lookup"><span data-stu-id="57bb9-127">XML Character Entities and XAML</span></span>](../../../docs/framework/xaml-services/xml-character-entities-and-xaml.md)
