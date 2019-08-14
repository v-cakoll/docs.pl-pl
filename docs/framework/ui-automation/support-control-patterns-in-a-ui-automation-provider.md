---
title: Obsługa wzorców formantów dostawcy automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, supporting in UI Automation provider
- UI Automation, supporting control patterns in provider
ms.assetid: 0d635c35-ffa8-4dc8-bbc9-12fcd5445776
ms.openlocfilehash: da423af259ac3ef88d5b52d576d3ab5ebb4f916e
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971802"
---
# <a name="support-control-patterns-in-a-ui-automation-provider"></a><span data-ttu-id="22bb3-102">Obsługa wzorców formantów dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="22bb3-102">Support Control Patterns in a UI Automation Provider</span></span>

> [!NOTE]
> <span data-ttu-id="22bb3-103">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="22bb3-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="22bb3-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="22bb3-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>

<span data-ttu-id="22bb3-105">W tym temacie przedstawiono sposób implementacji co najmniej jednego wzorca kontroli dla dostawcy automatyzacji interfejsu użytkownika, dzięki czemu aplikacje klienckie mogą manipulować kontrolkami i pobierać z nich dane.</span><span class="sxs-lookup"><span data-stu-id="22bb3-105">This topic shows how to implement one or more control patterns on a UI Automation provider so that client applications can manipulate controls and get data from them.</span></span>

## <a name="support-control-patterns"></a><span data-ttu-id="22bb3-106">Obsługa wzorców kontrolek</span><span class="sxs-lookup"><span data-stu-id="22bb3-106">Support Control Patterns</span></span>

1. <span data-ttu-id="22bb3-107">Zaimplementuj odpowiednie interfejsy dla wzorców kontrolek, które element powinien obsługiwać, <xref:System.Windows.Automation.Provider.IInvokeProvider> na <xref:System.Windows.Automation.InvokePattern>przykład.</span><span class="sxs-lookup"><span data-stu-id="22bb3-107">Implement the appropriate interfaces for the control patterns that the element should support, such as <xref:System.Windows.Automation.Provider.IInvokeProvider> for <xref:System.Windows.Automation.InvokePattern>.</span></span>

2. <span data-ttu-id="22bb3-108">Zwróć obiekt zawierający implementację każdego interfejsu sterowania w implementacji programu<xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="22bb3-108">Return the object containing your implementation of each control interface in your implementation of <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType></span></span>

## <a name="example"></a><span data-ttu-id="22bb3-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="22bb3-109">Example</span></span>

<span data-ttu-id="22bb3-110">W poniższym przykładzie przedstawiono implementację <xref:System.Windows.Automation.Provider.ISelectionProvider> dla niestandardowego pola listy o pojedynczym zaznaczeniu.</span><span class="sxs-lookup"><span data-stu-id="22bb3-110">The following example shows an implementation of <xref:System.Windows.Automation.Provider.ISelectionProvider> for a single-selection custom list box.</span></span> <span data-ttu-id="22bb3-111">Zwraca trzy właściwości i pobiera aktualnie wybrany element.</span><span class="sxs-lookup"><span data-stu-id="22bb3-111">It returns three properties and gets the currently selected item.</span></span>

[!code-csharp[UIAFragmentProvider_snip#119](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListPattern.cs#119)]
[!code-vb[UIAFragmentProvider_snip#119](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListPattern.vb#119)]

## <a name="example"></a><span data-ttu-id="22bb3-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="22bb3-112">Example</span></span>

<span data-ttu-id="22bb3-113">W poniższym przykładzie przedstawiono implementację <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> , która zwraca klasę implementującą. <xref:System.Windows.Automation.Provider.ISelectionProvider></span><span class="sxs-lookup"><span data-stu-id="22bb3-113">The following example shows an implementation of <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> that returns the class implementing <xref:System.Windows.Automation.Provider.ISelectionProvider>.</span></span> <span data-ttu-id="22bb3-114">Większość formantów pola listy obsługuje inne wzorce, ale w tym przykładzie odwołanie null (`Nothing` w Microsoft Visual Basic .NET) jest zwracane dla wszystkich innych identyfikatorów wzorców.</span><span class="sxs-lookup"><span data-stu-id="22bb3-114">Most list box controls would support other patterns as well, but in this example a null reference (`Nothing` in Microsoft Visual Basic .NET) is returned for all other pattern identifiers.</span></span>

[!code-csharp[UIAFragmentProvider_snip#120](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#120)]
[!code-vb[UIAFragmentProvider_snip#120](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#120)]

## <a name="see-also"></a><span data-ttu-id="22bb3-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="22bb3-115">See also</span></span>

- [<span data-ttu-id="22bb3-116">Przegląd dostawców automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="22bb3-116">UI Automation Providers Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
- [<span data-ttu-id="22bb3-117">Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie serwera</span><span class="sxs-lookup"><span data-stu-id="22bb3-117">Server-Side UI Automation Provider Implementation</span></span>](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
