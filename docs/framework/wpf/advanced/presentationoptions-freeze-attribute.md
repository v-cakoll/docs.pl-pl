---
title: PresentationOptions:Freeze — Atrybut
ms.date: 03/30/2017
helpviewer_keywords:
- Freeze attribute [WPF]
- Freezable elements [WPF]
- PresentationOptions prefix [WPF]
ms.assetid: 391032dd-2fba-4804-bb8a-3b071797a9f4
ms.openlocfilehash: d3e0cee293a9585b972b0145da953976ed94b74c
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991427"
---
# <a name="presentationoptionsfreeze-attribute"></a><span data-ttu-id="e5683-102">PresentationOptions:Freeze — Atrybut</span><span class="sxs-lookup"><span data-stu-id="e5683-102">PresentationOptions:Freeze Attribute</span></span>
<span data-ttu-id="e5683-103"><xref:System.Windows.Freezable.IsFrozen%2A> Ustawia <xref:System.Windows.Freezable> stan na `true` dla elementu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="e5683-103">Sets the <xref:System.Windows.Freezable.IsFrozen%2A> state to `true` on the containing <xref:System.Windows.Freezable> element.</span></span> <span data-ttu-id="e5683-104">Zachowanie domyślne dla a <xref:System.Windows.Freezable> `PresentationOptions:Freeze` bez określonego <xref:System.Windows.Freezable.IsFrozen%2A> <xref:System.Windows.Freezable> atrybutu jest w czasie ładowania i zależne od ogólnego zachowania w czasie wykonywania. `false`</span><span class="sxs-lookup"><span data-stu-id="e5683-104">Default behavior for a <xref:System.Windows.Freezable> without the `PresentationOptions:Freeze` attribute specified is that <xref:System.Windows.Freezable.IsFrozen%2A> is `false` at load time, and dependent on general <xref:System.Windows.Freezable> behavior at runtime.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="e5683-105">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="e5683-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object  
  xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="PresentationOptions">  
    <freezableElement PresentationOptions:Freeze="true"/>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="e5683-106">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="e5683-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`PresentationOptions`|<span data-ttu-id="e5683-107">Prefiks przestrzeni nazw XML, który może być dowolnym prawidłowym ciągiem prefiksu na specyfikację XML 1,0.</span><span class="sxs-lookup"><span data-stu-id="e5683-107">An XML namespace prefix, which can be any valid prefix string, per the XML 1.0 specification.</span></span> <span data-ttu-id="e5683-108">Prefiks `PresentationOptions` jest używany na potrzeby identyfikacji w tej dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="e5683-108">The prefix `PresentationOptions` is used for identification purposes in this documentation.</span></span>|  
|`freezableElement`|<span data-ttu-id="e5683-109">Element, który tworzy wystąpienie klasy <xref:System.Windows.Freezable>pochodnej.</span><span class="sxs-lookup"><span data-stu-id="e5683-109">An element that instantiates any derived class of <xref:System.Windows.Freezable>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5683-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e5683-110">Remarks</span></span>  
 <span data-ttu-id="e5683-111">Ten `Freeze` atrybut jest jedynym atrybutem lub innym elementem programistycznym zdefiniowanym `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options` w przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="e5683-111">The `Freeze` attribute is the only attribute or other programming element defined in the `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options` XML namespace.</span></span> <span data-ttu-id="e5683-112">Ten atrybut istnieje w tej specjalnej przestrzeni nazw, aby można było go wyznaczyć w sposób ignorowany, przy użyciu funkcji [MC: atrybut do ignorowania](mc-ignorable-attribute.md) jako część deklaracji elementu głównego. `Freeze`</span><span class="sxs-lookup"><span data-stu-id="e5683-112">The `Freeze` attribute exists in this special namespace specifically so that it can be designated as ignorable, using [mc:Ignorable Attribute](mc-ignorable-attribute.md) as part of the root element declarations.</span></span> <span data-ttu-id="e5683-113">Przyczyną, że `Freeze` musi być możliwe ignorowanie, jest to, że nie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] wszystkie implementacje procesora <xref:System.Windows.Freezable> mogą zamrozić w czasie ładowania [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ; ta funkcja nie jest częścią specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="e5683-113">The reason that `Freeze` must be able to be ignorable is because not all [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementations are able to freeze a <xref:System.Windows.Freezable> at load time; this capability is not part of the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] specification.</span></span>  
  
 <span data-ttu-id="e5683-114">Możliwość przetwarzania `Freeze` atrybutu jest specjalnie wbudowana w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor, który przetwarza [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] skompilowane aplikacje.</span><span class="sxs-lookup"><span data-stu-id="e5683-114">The ability to process the `Freeze` attribute is specifically built in to the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor that processes [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] for compiled applications.</span></span> <span data-ttu-id="e5683-115">Atrybut nie jest obsługiwany przez żadną klasę, a składnia atrybutu nie jest rozszerzalna ani modyfikowalna.</span><span class="sxs-lookup"><span data-stu-id="e5683-115">The attribute is not supported by any class, and the attribute syntax is not extensible or modifiable.</span></span> <span data-ttu-id="e5683-116">Jeśli wdrażasz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] własny procesor, możesz wybrać równoległe zachowanie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] procesora podczas przetwarzania `Freeze` atrybutu dla <xref:System.Windows.Freezable> elementów w czasie ładowania.</span><span class="sxs-lookup"><span data-stu-id="e5683-116">If you are implementing your own [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor you can choose to parallel the freezing behavior of the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor when processing the `Freeze` attribute on <xref:System.Windows.Freezable> elements at load time.</span></span>  
  
 <span data-ttu-id="e5683-117">Dowolna wartość `Freeze` atrybutu innego niż `true` (bez uwzględniania wielkości liter) generuje błąd ładowania.</span><span class="sxs-lookup"><span data-stu-id="e5683-117">Any value for the `Freeze` attribute other than `true` (not case sensitive) generates a load time error.</span></span> <span data-ttu-id="e5683-118">(Określenie `Freeze` atrybutu jako `false` nie jest błędem, ale jest już ustawieniem `false` domyślnym, więc nie robi nic).</span><span class="sxs-lookup"><span data-stu-id="e5683-118">(Specifying the `Freeze` attribute as `false` is not an error, but that is already the default, so setting to `false` does nothing).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5683-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e5683-119">See also</span></span>

- <xref:System.Windows.Freezable>
- [<span data-ttu-id="e5683-120">Przegląd obiektów Freezable</span><span class="sxs-lookup"><span data-stu-id="e5683-120">Freezable Objects Overview</span></span>](freezable-objects-overview.md)
- [<span data-ttu-id="e5683-121">mc:Ignorable, atrybut</span><span class="sxs-lookup"><span data-stu-id="e5683-121">mc:Ignorable Attribute</span></span>](mc-ignorable-attribute.md)
