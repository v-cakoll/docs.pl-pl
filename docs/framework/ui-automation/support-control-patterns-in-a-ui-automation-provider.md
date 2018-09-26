---
title: Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, supporting in UI Automation provider
- UI Automation, supporting control patterns in provider
ms.assetid: 0d635c35-ffa8-4dc8-bbc9-12fcd5445776
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 4daa7f0ec869771e8e7ceb11f6871e4b5791badd
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47193502"
---
# <a name="support-control-patterns-in-a-ui-automation-provider"></a><span data-ttu-id="390f8-102">Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="390f8-102">Support Control Patterns in a UI Automation Provider</span></span>
> [!NOTE]
>  <span data-ttu-id="390f8-103">Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="390f8-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="390f8-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: automatyzacji interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="390f8-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="390f8-105">W tym temacie pokazano, jak można zaimplementować jeden lub więcej wzorców kontrolek w dostawcy automatyzacji interfejsu użytkownika, dzięki czemu aplikacje klienckie mogą manipulowanie kontrolkami i pobieranie danych z nich.</span><span class="sxs-lookup"><span data-stu-id="390f8-105">This topic shows how to implement one or more control patterns on a UI Automation provider so that client applications can manipulate controls and get data from them.</span></span>  
  
### <a name="support-control-patterns"></a><span data-ttu-id="390f8-106">Obsługa wzorców kontrolek</span><span class="sxs-lookup"><span data-stu-id="390f8-106">Support Control Patterns</span></span>  
  
1.  <span data-ttu-id="390f8-107">Implementowanie odpowiednich interfejsów dla wzorców kontrolki, które element powinien obsługiwać, takich jak <xref:System.Windows.Automation.Provider.IInvokeProvider> dla <xref:System.Windows.Automation.InvokePattern>.</span><span class="sxs-lookup"><span data-stu-id="390f8-107">Implement the appropriate interfaces for the control patterns that the element should support, such as <xref:System.Windows.Automation.Provider.IInvokeProvider> for <xref:System.Windows.Automation.InvokePattern>.</span></span>  
  
2.  <span data-ttu-id="390f8-108">Zwraca obiekt zawierający implementacji interfejsu każdego kontroli w danej implementacji <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="390f8-108">Return the object containing your implementation of each control interface in your implementation of <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType></span></span>  
  
## <a name="example"></a><span data-ttu-id="390f8-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="390f8-109">Example</span></span>  
 <span data-ttu-id="390f8-110">W poniższym przykładzie pokazano implementację <xref:System.Windows.Automation.Provider.ISelectionProvider> pola listy niestandardowej z pojedynczym wyborem.</span><span class="sxs-lookup"><span data-stu-id="390f8-110">The following example shows an implementation of <xref:System.Windows.Automation.Provider.ISelectionProvider> for a single-selection custom list box.</span></span> <span data-ttu-id="390f8-111">Go może zwraca trzy właściwości, a następnie pobiera aktualnie wybranego elementu.</span><span class="sxs-lookup"><span data-stu-id="390f8-111">It returns three properties and gets the currently selected item.</span></span>  
  
 [!code-csharp[UIAFragmentProvider_snip#119](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListPattern.cs#119)]
 [!code-vb[UIAFragmentProvider_snip#119](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListPattern.vb#119)]  
  
## <a name="example"></a><span data-ttu-id="390f8-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="390f8-112">Example</span></span>  
 <span data-ttu-id="390f8-113">W poniższym przykładzie pokazano implementację <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> zwracającego Implementacja klasy <xref:System.Windows.Automation.Provider.ISelectionProvider>.</span><span class="sxs-lookup"><span data-stu-id="390f8-113">The following example shows an implementation of <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> that returns the class implementing <xref:System.Windows.Automation.Provider.ISelectionProvider>.</span></span> <span data-ttu-id="390f8-114">Większość formanty pola listy będzie obsługa innych wzorców, także, ale w tym przykładzie odwołanie o wartości null (`Nothing` w Microsoft Visual Basic .NET) jest zwracany w przypadku innych identyfikatorów w wzorca.</span><span class="sxs-lookup"><span data-stu-id="390f8-114">Most list box controls would support other patterns as well, but in this example a null reference (`Nothing` in Microsoft Visual Basic .NET) is returned for all other pattern identifiers.</span></span>  
  
 [!code-csharp[UIAFragmentProvider_snip#120](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#120)]
 [!code-vb[UIAFragmentProvider_snip#120](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#120)]  
  
## <a name="see-also"></a><span data-ttu-id="390f8-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="390f8-115">See Also</span></span>  
 [<span data-ttu-id="390f8-116">Przegląd dostawców automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="390f8-116">UI Automation Providers Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)  
 [<span data-ttu-id="390f8-117">Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie serwera</span><span class="sxs-lookup"><span data-stu-id="390f8-117">Server-Side UI Automation Provider Implementation</span></span>](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
