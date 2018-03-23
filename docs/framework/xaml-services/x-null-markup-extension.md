---
title: x:Null — Rozszerzenie znaczników
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: ''
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5b10d759a4f79eabe973a0fcd60736428e46f659
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="xnull-markup-extension"></a><span data-ttu-id="d9d65-102">x:Null — Rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="d9d65-102">x:Null Markup Extension</span></span>
<span data-ttu-id="d9d65-103">Określa `null` jako wartość dla elementu członkowskiego XAML.</span><span class="sxs-lookup"><span data-stu-id="d9d65-103">Specifies `null` as a value for a XAML member.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="d9d65-104">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="d9d65-104">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{x:Null}" .../>  
```  
  
## <a name="remarks"></a><span data-ttu-id="d9d65-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d9d65-105">Remarks</span></span>  
 <span data-ttu-id="d9d65-106">Słowo kluczowe odwołanie o wartości null w [!INCLUDE[TLA#tla_cshrp](../../../includes/tlasharptla-cshrp-md.md)] i [!INCLUDE[TLA#tla_cpp](../../../includes/tlasharptla-cpp-md.md)] ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="d9d65-106">The keyword for a null reference in [!INCLUDE[TLA#tla_cshrp](../../../includes/tlasharptla-cshrp-md.md)] and [!INCLUDE[TLA#tla_cpp](../../../includes/tlasharptla-cpp-md.md)] is null.</span></span> <span data-ttu-id="d9d65-107">[!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)] — Słowo kluczowe dla odwołanie o wartości null jest `Nothing`, ale zawsze używaj `{x:Null}` jako użycia XAML niezależnie od języka kodu z opóźnieniem, w którym jest skojarzona z XAML.</span><span class="sxs-lookup"><span data-stu-id="d9d65-107">The [!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)] keyword for a null reference is `Nothing`, but you always use `{x:Null}` as the XAML usage regardless which code-behind language you associate with the XAML.</span></span>  
  
 <span data-ttu-id="d9d65-108">`x:Null` — Rozszerzenie znaczników nie ma można ustawić właściwości.</span><span class="sxs-lookup"><span data-stu-id="d9d65-108">The `x:Null` markup extension has no settable properties.</span></span>  
  
 <span data-ttu-id="d9d65-109">Użycie wartości null jest często skojarzony z ujawnienia elementu członkowskiego XAML CLR <xref:System.Nullable%601> wartość.</span><span class="sxs-lookup"><span data-stu-id="d9d65-109">A null usage is often associated with the XAML member exposure of a CLR <xref:System.Nullable%601> value.</span></span>  
  
 <span data-ttu-id="d9d65-110">`x:Null` — Rozszerzenie znaczników, podobnie jak wszystkie rozszerzenia znaczników XAML, używa nawiasy klamrowe (`{,}`) dla anulowanie obsługi wartości atrybutów, aby być inne niż literały lub odwołania do obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d9d65-110">The `x:Null` markup extension, like all XAML markup extensions, uses the braces (`{,}`) for escaping the handling of attribute values to be other than literals or event-handler references.</span></span> <span data-ttu-id="d9d65-111">Składnia atrybutu jest składnia najczęściej używane dla tego rozszerzenia znacznika.</span><span class="sxs-lookup"><span data-stu-id="d9d65-111">Attribute syntax is the syntax most frequently used with this markup extension.</span></span> <span data-ttu-id="d9d65-112">Składnia elementu obiektu `<x:Null />` jest technicznie możliwe, ale jest rzadko używana, ponieważ `x:Null` — rozszerzenie znaczników nie ma parametrów pozycyjnych ani konstrukcji argumentów.</span><span class="sxs-lookup"><span data-stu-id="d9d65-112">An object element syntax `<x:Null />` is technically possible, but is rarely used because the `x:Null` markup extension has no positional parameters or construction arguments.</span></span>  
  
 <span data-ttu-id="d9d65-113">Aby uzyskać informacje na temat rozszerzeń znaczników, zobacz [rozszerzenia znaczników i WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="d9d65-113">For information about markup extensions, see [Markup Extensions and WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
 <span data-ttu-id="d9d65-114">W programie .NET Framework XAML Services obsługę tego rozszerzenia znacznika jest definiowana za pomocą <xref:System.Windows.Markup.NullExtension> klasy.</span><span class="sxs-lookup"><span data-stu-id="d9d65-114">In .NET Framework XAML Services, the handling for this markup extension is defined by the <xref:System.Windows.Markup.NullExtension> class.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="d9d65-115">Uwagi dotyczące użycia WPF</span><span class="sxs-lookup"><span data-stu-id="d9d65-115">WPF Usage Notes</span></span>  
 <span data-ttu-id="d9d65-116">Należy pamiętać, że `null` niekoniecznie początkowej nie ustawiono wartości dla właściwości zależności typu odwołania.</span><span class="sxs-lookup"><span data-stu-id="d9d65-116">Note that `null` is not necessarily the initial unset value for a reference-type dependency property.</span></span> <span data-ttu-id="d9d65-117">Wartość domyślna początkowej mogą się różnić dla każdej właściwości zależności i mogą być oparte na metadane dotyczące właściwości.</span><span class="sxs-lookup"><span data-stu-id="d9d65-117">The initial default value can vary for each dependency property and can be based on property-specific metadata.</span></span> <span data-ttu-id="d9d65-118">Wiele właściwości zależności nie akceptują `null` jako wartość, przy użyciu znaczników lub kodu ze względu na ich implementacji wywołanie zwrotne weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="d9d65-118">Many dependency properties do not accept `null` as a value, either through markup or code because of their validation callback implementations.</span></span> <span data-ttu-id="d9d65-119">Aby uzyskać więcej informacji na temat właściwości zależności, zobacz [Przegląd właściwości zależności](../../../docs/framework/wpf/advanced/dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d9d65-119">For more information about dependency properties, see [Dependency Properties Overview](../../../docs/framework/wpf/advanced/dependency-properties-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9d65-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d9d65-120">See Also</span></span>  
 <xref:System.Windows.DependencyProperty.UnsetValue>  
 [<span data-ttu-id="d9d65-121">Przegląd XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="d9d65-121">XAML Overview (WPF)</span></span>](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="d9d65-122">Rozszerzenia znaczników i WPF XAML</span><span class="sxs-lookup"><span data-stu-id="d9d65-122">Markup Extensions and WPF XAML</span></span>](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
