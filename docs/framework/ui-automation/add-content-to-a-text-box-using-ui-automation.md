---
title: Dodawanie zawartości do pola tekstowego przy użyciu automatyzacji interfejsu użytkownika
description: Zapoznaj się z przykładem, jak dodać zawartość do jednowierszowego pola tekstowego przy użyciu automatyzacji interfejsu użytkownika firmy Microsoft w ramach platformy .NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adding content to text boxes
- text boxes, adding content
- UI Automation, adding content to text boxes
ms.assetid: 8bdd1a73-1ecb-4a05-a891-a7827ebb767f
ms.openlocfilehash: 4136d460de7091a515580cade16f06e54699727a
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166909"
---
# <a name="add-content-to-a-text-box-using-ui-automation"></a><span data-ttu-id="8ad65-103">Dodawanie zawartości do pola tekstowego przy użyciu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="8ad65-103">Add Content to a Text Box Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="8ad65-104">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="8ad65-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="8ad65-105">Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="8ad65-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="8ad65-106">Ten temat zawiera przykładowy kod, który demonstruje sposób użycia [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] do wstawiania tekstu w jednowierszowym polu tekstowym.</span><span class="sxs-lookup"><span data-stu-id="8ad65-106">This topic contains example code that demonstrates how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to insert text into a single-line text box.</span></span> <span data-ttu-id="8ad65-107">Podano alternatywną metodę dla formantów tekstu wielowierszowego i sformatowanego, gdzie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nie ma zastosowania.</span><span class="sxs-lookup"><span data-stu-id="8ad65-107">An alternate method is provided for multi-line and rich text controls where [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] is not applicable.</span></span> <span data-ttu-id="8ad65-108">W celu porównania przykład ilustruje sposób użycia metod Win32 do osiągnięcia tych samych wyników.</span><span class="sxs-lookup"><span data-stu-id="8ad65-108">For comparison purposes, the example also demonstrates how to use Win32 methods to accomplish the same results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ad65-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="8ad65-109">Example</span></span>  
 <span data-ttu-id="8ad65-110">Poniższy przykład przechodzi przez sekwencję formantów tekstowych w aplikacji docelowej.</span><span class="sxs-lookup"><span data-stu-id="8ad65-110">The following example steps through a sequence of text controls in a target application.</span></span> <span data-ttu-id="8ad65-111">Każda kontrolka tekstowa jest testowana, aby sprawdzić, czy <xref:System.Windows.Automation.ValuePattern> obiekt można uzyskać z niego przy użyciu <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="8ad65-111">Each text control is tested to see if a <xref:System.Windows.Automation.ValuePattern> object can be obtained from it using the <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> method.</span></span> <span data-ttu-id="8ad65-112">Jeśli kontrolka tekstu obsługuje <xref:System.Windows.Automation.ValuePattern> , metoda służy <xref:System.Windows.Automation.ValuePattern.SetValue%2A> do wstawiania ciągu zdefiniowanego przez użytkownika do kontrolki tekstowej.</span><span class="sxs-lookup"><span data-stu-id="8ad65-112">If the text control does support <xref:System.Windows.Automation.ValuePattern>, the <xref:System.Windows.Automation.ValuePattern.SetValue%2A> method is used to insert a user-defined string into the text control.</span></span> <span data-ttu-id="8ad65-113">W przeciwnym razie <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> Metoda jest używana.</span><span class="sxs-lookup"><span data-stu-id="8ad65-113">Otherwise, the <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> method is used.</span></span>  
  
 [!code-csharp[InsertText#InsertText](../../../samples/snippets/csharp/VS_Snippets_Wpf/InsertText/CSharp/Window1.xaml.cs#inserttext)]
 [!code-vb[InsertText#InsertText](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InsertText/VisualBasic/Window1.xaml.vb#inserttext)]  
  
## <a name="see-also"></a><span data-ttu-id="8ad65-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8ad65-114">See also</span></span>

- <span data-ttu-id="8ad65-115">[Przykład wstawiania TextPattern tekstu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771478(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="8ad65-115">[TextPattern Insert Text Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771478(v=vs.90))</span></span>
