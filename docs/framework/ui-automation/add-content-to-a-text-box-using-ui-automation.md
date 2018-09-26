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
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 7c4772d36a88dfede04f7592c1cab776ddcd7d7d
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47084361"
---
# <a name="add-content-to-a-text-box-using-ui-automation"></a><span data-ttu-id="965fb-102">Dodawanie zawartości do pola tekstowego przy użyciu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="965fb-102">Add Content to a Text Box Using UI Automation</span></span>
> [!NOTE]
>  <span data-ttu-id="965fb-103">Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="965fb-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="965fb-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: automatyzacji interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="965fb-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="965fb-105">Ten temat zawiera przykładowy kod, który demonstruje sposób używania [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] umożliwia wstawianie tekstu w polu tekstu jednowierszowego.</span><span class="sxs-lookup"><span data-stu-id="965fb-105">This topic contains example code that demonstrates how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to insert text into a single-line text box.</span></span> <span data-ttu-id="965fb-106">Alternatywna metoda jest przewidziana kontrolek tekstu wielowierszowego i oferuje szeroki wachlarz gdzie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nie ma zastosowania.</span><span class="sxs-lookup"><span data-stu-id="965fb-106">An alternate method is provided for multi-line and rich text controls where [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] is not applicable.</span></span> <span data-ttu-id="965fb-107">Dla celów porównawczych w przykładzie pokazano sposób użycia metod Win32 na takie same wyniki.</span><span class="sxs-lookup"><span data-stu-id="965fb-107">For comparison purposes, the example also demonstrates how to use Win32 methods to accomplish the same results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="965fb-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="965fb-108">Example</span></span>  
 <span data-ttu-id="965fb-109">Krokach w poniższym przykładzie za pośrednictwem sekwencji kontrolek tekstu w aplikacji docelowej.</span><span class="sxs-lookup"><span data-stu-id="965fb-109">The following example steps through a sequence of text controls in a target application.</span></span> <span data-ttu-id="965fb-110">Każdy formant tekstu jest testowany, aby sprawdzić, czy <xref:System.Windows.Automation.ValuePattern> obiektu można uzyskać za pomocą <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="965fb-110">Each text control is tested to see if a <xref:System.Windows.Automation.ValuePattern> object can be obtained from it using the <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> method.</span></span> <span data-ttu-id="965fb-111">Jeśli obsługuje kontrolki tekstu <xref:System.Windows.Automation.ValuePattern>, <xref:System.Windows.Automation.ValuePattern.SetValue%2A> metoda służy do wstawiania ciągiem zdefiniowanym przez użytkownika do kontrolki tekstu.</span><span class="sxs-lookup"><span data-stu-id="965fb-111">If the text control does support <xref:System.Windows.Automation.ValuePattern>, the <xref:System.Windows.Automation.ValuePattern.SetValue%2A> method is used to insert a user-defined string into the text control.</span></span> <span data-ttu-id="965fb-112">W przeciwnym razie <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> metoda jest używana.</span><span class="sxs-lookup"><span data-stu-id="965fb-112">Otherwise, the <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> method is used.</span></span>  
  
 [!code-csharp[InsertText#InsertText](../../../samples/snippets/csharp/VS_Snippets_Wpf/InsertText/CSharp/Window1.xaml.cs#inserttext)]
 [!code-vb[InsertText#InsertText](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InsertText/VisualBasic/Window1.xaml.vb#inserttext)]  
  
## <a name="see-also"></a><span data-ttu-id="965fb-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="965fb-113">See Also</span></span>  
 [<span data-ttu-id="965fb-114">Przykładowy tekst wstawienia TextPattern</span><span class="sxs-lookup"><span data-stu-id="965fb-114">TextPattern Insert Text Sample</span></span>](https://msdn.microsoft.com/library/67353f93-7ee2-42f2-ab76-5c078cf6ca16)
