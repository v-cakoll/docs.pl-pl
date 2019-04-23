---
title: x:Null — Rozszerzenie znaczników
ms.date: 03/30/2017
f1_keywords:
- NullExtension
- x:NullExtension
- x:Null
- "Null"
- xNull
helpviewer_keywords:
- Null markup extension in XAML [XAML Services]
- x:Null markup extension [XAML Services]
- XAML [XAML Services], x:Null markup extension
ms.assetid: 2e3ccc21-4996-481d-91b5-3910d8b3bfa3
ms.openlocfilehash: e46d8561b62d9137d4fed4df447338a97fc0577b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59100811"
---
# <a name="xnull-markup-extension"></a><span data-ttu-id="511da-102">x:Null — Rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="511da-102">x:Null Markup Extension</span></span>
<span data-ttu-id="511da-103">Określa `null` jako wartość dla elementu członkowskiego XAML.</span><span class="sxs-lookup"><span data-stu-id="511da-103">Specifies `null` as a value for a XAML member.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="511da-104">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="511da-104">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{x:Null}" .../>  
```  
  
## <a name="remarks"></a><span data-ttu-id="511da-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="511da-105">Remarks</span></span>  
 <span data-ttu-id="511da-106">Słowo kluczowe odwołanie o wartości null w C# i [!INCLUDE[TLA#tla_cpp](../../../includes/tlasharptla-cpp-md.md)] ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="511da-106">The keyword for a null reference in C# and [!INCLUDE[TLA#tla_cpp](../../../includes/tlasharptla-cpp-md.md)] is null.</span></span> <span data-ttu-id="511da-107">Słowo kluczowe języka Visual Basic dla odwołanie o wartości null jest `Nothing`, ale zawsze używaj `{x:Null}` jako użycie XAML niezależnie od tego, jaki język związanym z kodem, należy skojarzyć z XAML.</span><span class="sxs-lookup"><span data-stu-id="511da-107">The Microsoft Visual Basic keyword for a null reference is `Nothing`, but you always use `{x:Null}` as the XAML usage regardless which code-behind language you associate with the XAML.</span></span>  
  
 <span data-ttu-id="511da-108">`x:Null` — Rozszerzenie znaczników nie ma żadnych właściwości do ustawienia.</span><span class="sxs-lookup"><span data-stu-id="511da-108">The `x:Null` markup extension has no settable properties.</span></span>  
  
 <span data-ttu-id="511da-109">Użycie o wartości null jest często kojarzona z narażenia elementu członkowskiego XAML CLR <xref:System.Nullable%601> wartość.</span><span class="sxs-lookup"><span data-stu-id="511da-109">A null usage is often associated with the XAML member exposure of a CLR <xref:System.Nullable%601> value.</span></span>  
  
 <span data-ttu-id="511da-110">`x:Null` — Rozszerzenie znaczników, takich jak wszystkie rozszerzenia znaczników XAML używa nawiasów klamrowych (`{,}`) do anulowania obsługi wartości atrybutów były inne niż literały ani odwołania do obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="511da-110">The `x:Null` markup extension, like all XAML markup extensions, uses the braces (`{,}`) for escaping the handling of attribute values to be other than literals or event-handler references.</span></span> <span data-ttu-id="511da-111">Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika.</span><span class="sxs-lookup"><span data-stu-id="511da-111">Attribute syntax is the syntax most frequently used with this markup extension.</span></span> <span data-ttu-id="511da-112">Składnia elementu obiektu `<x:Null />` jest technicznie możliwe, ale jest rzadko używana, ponieważ `x:Null` — rozszerzenie znaczników nie ma parametry pozycyjne ani argumentów.</span><span class="sxs-lookup"><span data-stu-id="511da-112">An object element syntax `<x:Null />` is technically possible, but is rarely used because the `x:Null` markup extension has no positional parameters or construction arguments.</span></span>  
  
 <span data-ttu-id="511da-113">Aby uzyskać informacje na temat rozszerzeń znaczników, zobacz [rozszerzenia znacznikowania i WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="511da-113">For information about markup extensions, see [Markup Extensions and WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
 <span data-ttu-id="511da-114">W programie .NET Framework XAML Services obsługi dla tego rozszerzenia znacznika jest definiowany przez <xref:System.Windows.Markup.NullExtension> klasy.</span><span class="sxs-lookup"><span data-stu-id="511da-114">In .NET Framework XAML Services, the handling for this markup extension is defined by the <xref:System.Windows.Markup.NullExtension> class.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="511da-115">Uwagi dotyczące użytkowania WPF</span><span class="sxs-lookup"><span data-stu-id="511da-115">WPF Usage Notes</span></span>  
 <span data-ttu-id="511da-116">Należy pamiętać, że `null` niekoniecznie jest początkowa nie ustawiono wartość dla właściwości zależności typu odwołania.</span><span class="sxs-lookup"><span data-stu-id="511da-116">Note that `null` is not necessarily the initial unset value for a reference-type dependency property.</span></span> <span data-ttu-id="511da-117">Wartość domyślna początkowej mogą się różnić dla każdej właściwości zależności i mogą opierać się na metadane właściwe dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="511da-117">The initial default value can vary for each dependency property and can be based on property-specific metadata.</span></span> <span data-ttu-id="511da-118">Wiele właściwości zależności nie są akceptowane `null` jako wartość za pomocą znaczników lub innego kodu ze względu na ich implementacji wywołanie zwrotne weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="511da-118">Many dependency properties do not accept `null` as a value, either through markup or code because of their validation callback implementations.</span></span> <span data-ttu-id="511da-119">Aby uzyskać więcej informacji na temat właściwości zależności zobacz [Przegląd właściwości zależności](../wpf/advanced/dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="511da-119">For more information about dependency properties, see [Dependency Properties Overview](../wpf/advanced/dependency-properties-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="511da-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="511da-120">See also</span></span>

- <xref:System.Windows.DependencyProperty.UnsetValue>
- [<span data-ttu-id="511da-121">Przegląd XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="511da-121">XAML Overview (WPF)</span></span>](../wpf/advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="511da-122">Rozszerzenia znaczników i WPF XAML</span><span class="sxs-lookup"><span data-stu-id="511da-122">Markup Extensions and WPF XAML</span></span>](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
