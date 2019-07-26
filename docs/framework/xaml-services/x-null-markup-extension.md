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
ms.openlocfilehash: 7dbea2c7d4010d8defc572dbdc14a0dfd6d7601e
ms.sourcegitcommit: 4b9c2d893b45d47048c6598b4182ba87759b1b59
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2019
ms.locfileid: "68484705"
---
# <a name="xnull-markup-extension"></a><span data-ttu-id="795cf-102">x:Null — Rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="795cf-102">x:Null Markup Extension</span></span>
<span data-ttu-id="795cf-103">Określa `null` jako wartość dla elementu członkowskiego języka XAML.</span><span class="sxs-lookup"><span data-stu-id="795cf-103">Specifies `null` as a value for a XAML member.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="795cf-104">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="795cf-104">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{x:Null}" .../>  
```  
  
## <a name="remarks"></a><span data-ttu-id="795cf-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="795cf-105">Remarks</span></span>  
 <span data-ttu-id="795cf-106">Słowo kluczowe dla odwołania o wartości null C# w C++ i ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="795cf-106">The keyword for a null reference in C# and C++ is null.</span></span> <span data-ttu-id="795cf-107">Słowo kluczowe Microsoft Visual Basic dla odwołania o wartości null `Nothing`to, ale jest zawsze `{x:Null}` używane jako użycie XAML, niezależnie od kodu związanego z kodem, który jest skojarzony z XAML.</span><span class="sxs-lookup"><span data-stu-id="795cf-107">The Microsoft Visual Basic keyword for a null reference is `Nothing`, but you always use `{x:Null}` as the XAML usage regardless which code-behind language you associate with the XAML.</span></span>  
  
 <span data-ttu-id="795cf-108">Rozszerzenie `x:Null` znaczników nie ma właściwości settable.</span><span class="sxs-lookup"><span data-stu-id="795cf-108">The `x:Null` markup extension has no settable properties.</span></span>  
  
 <span data-ttu-id="795cf-109">Użycie wartości null jest często kojarzone ze współczynnikiem członkowskim języka XAML <xref:System.Nullable%601> dla wartości CLR.</span><span class="sxs-lookup"><span data-stu-id="795cf-109">A null usage is often associated with the XAML member exposure of a CLR <xref:System.Nullable%601> value.</span></span>  
  
 <span data-ttu-id="795cf-110">Rozszerzenie znacznika, takie jak wszystkie rozszerzenia znaczników XAML, używa nawiasów (`{,}`) do ucieczki obsługi wartości atrybutów, aby były inne niż literały lub odwołania do obsługi zdarzeń. `x:Null`</span><span class="sxs-lookup"><span data-stu-id="795cf-110">The `x:Null` markup extension, like all XAML markup extensions, uses the braces (`{,}`) for escaping the handling of attribute values to be other than literals or event-handler references.</span></span> <span data-ttu-id="795cf-111">Składnia atrybutu jest składnią najczęściej używaną z tym rozszerzeniem znacznika.</span><span class="sxs-lookup"><span data-stu-id="795cf-111">Attribute syntax is the syntax most frequently used with this markup extension.</span></span> <span data-ttu-id="795cf-112">Składnia `<x:Null />` elementu obiektu jest technicznie możliwa, ale rzadko jest używana, `x:Null` ponieważ rozszerzenie znaczników nie ma parametrów pozycyjnych ani argumentów konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="795cf-112">An object element syntax `<x:Null />` is technically possible, but is rarely used because the `x:Null` markup extension has no positional parameters or construction arguments.</span></span>  
  
 <span data-ttu-id="795cf-113">Aby uzyskać informacje na temat rozszerzeń znaczników, zobacz [rozszerzenia znaczników i XAML WPF](../wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="795cf-113">For information about markup extensions, see [Markup Extensions and WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
 <span data-ttu-id="795cf-114">W .NET Framework usługach XAML obsługa tego rozszerzenia znacznika jest definiowana przez <xref:System.Windows.Markup.NullExtension> klasę.</span><span class="sxs-lookup"><span data-stu-id="795cf-114">In .NET Framework XAML Services, the handling for this markup extension is defined by the <xref:System.Windows.Markup.NullExtension> class.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="795cf-115">Uwagi dotyczące użycia WPF</span><span class="sxs-lookup"><span data-stu-id="795cf-115">WPF Usage Notes</span></span>  
 <span data-ttu-id="795cf-116">Należy pamiętać `null` , że nie musi być początkową wartością ustawienia dla właściwości zależności typu odwołania.</span><span class="sxs-lookup"><span data-stu-id="795cf-116">Note that `null` is not necessarily the initial unset value for a reference-type dependency property.</span></span> <span data-ttu-id="795cf-117">Początkowa wartość domyślna może różnić się w zależności od właściwości zależności i może opierać się na metadanych specyficznych dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="795cf-117">The initial default value can vary for each dependency property and can be based on property-specific metadata.</span></span> <span data-ttu-id="795cf-118">Wiele właściwości zależności nie akceptuje `null` jako wartości, za pomocą znaczników ani kodu ze względu na implementacje wywołania zwrotnego walidacji.</span><span class="sxs-lookup"><span data-stu-id="795cf-118">Many dependency properties do not accept `null` as a value, either through markup or code because of their validation callback implementations.</span></span> <span data-ttu-id="795cf-119">Aby uzyskać więcej informacji na temat właściwości zależności, zobacz [Omówienie właściwości zależności](../wpf/advanced/dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="795cf-119">For more information about dependency properties, see [Dependency Properties Overview](../wpf/advanced/dependency-properties-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="795cf-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="795cf-120">See also</span></span>

- <xref:System.Windows.DependencyProperty.UnsetValue>
- [<span data-ttu-id="795cf-121">Przegląd XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="795cf-121">XAML Overview (WPF)</span></span>](../wpf/advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="795cf-122">Rozszerzenia znaczników i WPF XAML</span><span class="sxs-lookup"><span data-stu-id="795cf-122">Markup Extensions and WPF XAML</span></span>](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
