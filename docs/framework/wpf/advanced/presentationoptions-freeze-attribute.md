---
title: PresentationOptions:Freeze — Atrybut
ms.date: 03/30/2017
helpviewer_keywords:
- Freeze attribute [WPF]
- Freezable elements [WPF]
- PresentationOptions prefix [WPF]
ms.assetid: 391032dd-2fba-4804-bb8a-3b071797a9f4
ms.openlocfilehash: e60c4a505db42936f188354f52edd7832fb9632b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772843"
---
# <a name="presentationoptionsfreeze-attribute"></a><span data-ttu-id="e7aa7-102">PresentationOptions:Freeze — Atrybut</span><span class="sxs-lookup"><span data-stu-id="e7aa7-102">PresentationOptions:Freeze Attribute</span></span>
<span data-ttu-id="e7aa7-103">Zestawy <xref:System.Windows.Freezable.IsFrozen%2A> do stanu `true` na zawierający <xref:System.Windows.Freezable> elementu.</span><span class="sxs-lookup"><span data-stu-id="e7aa7-103">Sets the <xref:System.Windows.Freezable.IsFrozen%2A> state to `true` on the containing <xref:System.Windows.Freezable> element.</span></span> <span data-ttu-id="e7aa7-104">Domyślne zachowanie dla <xref:System.Windows.Freezable> bez `PresentationOptions:Freeze` określony atrybut jest to, że <xref:System.Windows.Freezable.IsFrozen%2A> jest `false` na czas ładowania, w zależności od ogólnego <xref:System.Windows.Freezable> zachowanie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e7aa7-104">Default behavior for a <xref:System.Windows.Freezable> without the `PresentationOptions:Freeze` attribute specified is that <xref:System.Windows.Freezable.IsFrozen%2A> is `false` at load time, and dependent on general <xref:System.Windows.Freezable> behavior at runtime.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="e7aa7-105">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="e7aa7-105">XAML Attribute Usage</span></span>  
  
```  
<object  
  xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="PresentationOptions">  
    <freezableElement PresentationOptions:Freeze="true"/>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="e7aa7-106">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="e7aa7-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`PresentationOptions`|<span data-ttu-id="e7aa7-107">Prefiks przestrzeni nazw XML, który może być dowolnym ciągiem prawidłowy prefiks na Specyfikacja XML 1.0.</span><span class="sxs-lookup"><span data-stu-id="e7aa7-107">An XML namespace prefix, which can be any valid prefix string, per the XML 1.0 specification.</span></span> <span data-ttu-id="e7aa7-108">Prefiks `PresentationOptions` jest używany w celach identyfikacyjnych w tej dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="e7aa7-108">The prefix `PresentationOptions` is used for identification purposes in this documentation.</span></span>|  
|`freezableElement`|<span data-ttu-id="e7aa7-109">Element, który tworzy dowolne pochodne klasy <xref:System.Windows.Freezable>.</span><span class="sxs-lookup"><span data-stu-id="e7aa7-109">An element that instantiates any derived class of <xref:System.Windows.Freezable>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7aa7-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e7aa7-110">Remarks</span></span>  
 <span data-ttu-id="e7aa7-111">`Freeze` Atrybut jest to jedyny atrybut lub innego elementu programowania zdefiniowanych w `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options` przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="e7aa7-111">The `Freeze` attribute is the only attribute or other programming element defined in the `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options` XML namespace.</span></span> <span data-ttu-id="e7aa7-112">`Freeze` Atrybut istnieje w tej przestrzeni nazw w specjalnych specjalnie tak, aby może zostać wyznaczony jako do pominięcia, za pomocą [mc: Ignorable — atrybut](mc-ignorable-attribute.md) jako część deklaracji elementu głównego.</span><span class="sxs-lookup"><span data-stu-id="e7aa7-112">The `Freeze` attribute exists in this special namespace specifically so that it can be designated as ignorable, using [mc:Ignorable Attribute](mc-ignorable-attribute.md) as part of the root element declarations.</span></span> <span data-ttu-id="e7aa7-113">Przyczyna, `Freeze` musi być w stanie się ignorable jest, ponieważ nie wszystkie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementacji procesora będą mogli zablokować <xref:System.Windows.Freezable> w czasie ładowania; ta funkcja nie jest częścią [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="e7aa7-113">The reason that `Freeze` must be able to be ignorable is because not all [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementations are able to freeze a <xref:System.Windows.Freezable> at load time; this capability is not part of the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] specification.</span></span>  
  
 <span data-ttu-id="e7aa7-114">Możliwość przetwarzania `Freeze` atrybut specjalnie wbudowanej w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora, który przetwarza [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dla skompilowanych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e7aa7-114">The ability to process the `Freeze` attribute is specifically built in to the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor that processes [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] for compiled applications.</span></span> <span data-ttu-id="e7aa7-115">Ten atrybut nie jest obsługiwany przez wszystkie klasy i składnia atrybutu nie jest rozszerzalna lub jako do modyfikacji.</span><span class="sxs-lookup"><span data-stu-id="e7aa7-115">The attribute is not supported by any class, and the attribute syntax is not extensible or modifiable.</span></span> <span data-ttu-id="e7aa7-116">W przypadku wdrażania własnych [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora, istnieje możliwość równoległego zamrożenia zachowanie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora podczas przetwarzania `Freeze` atrybutu na <xref:System.Windows.Freezable> elementy w czasie ładowania.</span><span class="sxs-lookup"><span data-stu-id="e7aa7-116">If you are implementing your own [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor you can choose to parallel the freezing behavior of the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor when processing the `Freeze` attribute on <xref:System.Windows.Freezable> elements at load time.</span></span>  
  
 <span data-ttu-id="e7aa7-117">Wszystkie wartości `Freeze` atrybutu innego niż `true` (bez uwzględniania wielkości liter) generuje błąd w czasie ładowania.</span><span class="sxs-lookup"><span data-stu-id="e7aa7-117">Any value for the `Freeze` attribute other than `true` (not case sensitive) generates a load time error.</span></span> <span data-ttu-id="e7aa7-118">(Określanie `Freeze` atrybutu jako `false` nie jest to błąd, ale która jest już domyślnie to ustawienie `false` nic nie robi).</span><span class="sxs-lookup"><span data-stu-id="e7aa7-118">(Specifying the `Freeze` attribute as `false` is not an error, but that is already the default, so setting to `false` does nothing).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7aa7-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e7aa7-119">See also</span></span>

- <xref:System.Windows.Freezable>
- [<span data-ttu-id="e7aa7-120">Przegląd obiektów Freezable</span><span class="sxs-lookup"><span data-stu-id="e7aa7-120">Freezable Objects Overview</span></span>](freezable-objects-overview.md)
- [<span data-ttu-id="e7aa7-121">mc:Ignorable, atrybut</span><span class="sxs-lookup"><span data-stu-id="e7aa7-121">mc:Ignorable Attribute</span></span>](mc-ignorable-attribute.md)
