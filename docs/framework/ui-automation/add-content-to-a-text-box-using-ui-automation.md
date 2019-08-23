---
title: Dodawanie zawartości do pola tekstowego przy użyciu automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adding content to text boxes
- text boxes, adding content
- UI Automation, adding content to text boxes
ms.assetid: 8bdd1a73-1ecb-4a05-a891-a7827ebb767f
ms.openlocfilehash: fdc52d0b94ce500b6560b60419d409f5cbd73b55
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932651"
---
# <a name="add-content-to-a-text-box-using-ui-automation"></a><span data-ttu-id="4396a-102">Dodawanie zawartości do pola tekstowego przy użyciu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="4396a-102">Add Content to a Text Box Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="4396a-103">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="4396a-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="4396a-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4396a-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="4396a-105">Ten temat zawiera przykładowy kod, który demonstruje sposób użycia [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] do wstawiania tekstu w jednowierszowym polu tekstowym.</span><span class="sxs-lookup"><span data-stu-id="4396a-105">This topic contains example code that demonstrates how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to insert text into a single-line text box.</span></span> <span data-ttu-id="4396a-106">Podano alternatywną metodę dla formantów tekstu wielowierszowego i sformatowanego [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , gdzie nie ma zastosowania.</span><span class="sxs-lookup"><span data-stu-id="4396a-106">An alternate method is provided for multi-line and rich text controls where [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] is not applicable.</span></span> <span data-ttu-id="4396a-107">W celu porównania przykład ilustruje sposób użycia metod Win32 do osiągnięcia tych samych wyników.</span><span class="sxs-lookup"><span data-stu-id="4396a-107">For comparison purposes, the example also demonstrates how to use Win32 methods to accomplish the same results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4396a-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="4396a-108">Example</span></span>  
 <span data-ttu-id="4396a-109">Poniższy przykład przechodzi przez sekwencję formantów tekstowych w aplikacji docelowej.</span><span class="sxs-lookup"><span data-stu-id="4396a-109">The following example steps through a sequence of text controls in a target application.</span></span> <span data-ttu-id="4396a-110">Każda kontrolka tekstowa jest testowana, aby <xref:System.Windows.Automation.ValuePattern> sprawdzić, czy obiekt można uzyskać z niego <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> przy użyciu metody.</span><span class="sxs-lookup"><span data-stu-id="4396a-110">Each text control is tested to see if a <xref:System.Windows.Automation.ValuePattern> object can be obtained from it using the <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> method.</span></span> <span data-ttu-id="4396a-111">Jeśli kontrolka <xref:System.Windows.Automation.ValuePattern>tekstu obsługuje <xref:System.Windows.Automation.ValuePattern.SetValue%2A> , metoda służy do wstawiania ciągu zdefiniowanego przez użytkownika do kontrolki tekstowej.</span><span class="sxs-lookup"><span data-stu-id="4396a-111">If the text control does support <xref:System.Windows.Automation.ValuePattern>, the <xref:System.Windows.Automation.ValuePattern.SetValue%2A> method is used to insert a user-defined string into the text control.</span></span> <span data-ttu-id="4396a-112">W przeciwnym razie metoda jest używana. <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="4396a-112">Otherwise, the <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> method is used.</span></span>  
  
 [!code-csharp[InsertText#InsertText](../../../samples/snippets/csharp/VS_Snippets_Wpf/InsertText/CSharp/Window1.xaml.cs#inserttext)]
 [!code-vb[InsertText#InsertText](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InsertText/VisualBasic/Window1.xaml.vb#inserttext)]  
  
## <a name="see-also"></a><span data-ttu-id="4396a-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4396a-113">See also</span></span>

- <span data-ttu-id="4396a-114">[Przykład wstawiania TextPattern tekstu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771478(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="4396a-114">[TextPattern Insert Text Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771478(v=vs.90))</span></span>
