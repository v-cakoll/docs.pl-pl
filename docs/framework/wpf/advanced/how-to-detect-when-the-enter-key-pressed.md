---
title: 'Instrukcje: Wykryć kiedy wciśnięto klawisz Enter'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Enter key [WPF], detecting
- keys [WPF], Enter
ms.assetid: a66f39d2-ef4a-43a5-b454-a4ea0fe88655
ms.openlocfilehash: fbb9b1b9cbb56a49aba018f122a7e903bd4f677d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54592250"
---
# <a name="how-to-detect-when-the-enter-key-pressed"></a><span data-ttu-id="e0177-102">Instrukcje: Wykryć kiedy wciśnięto klawisz Enter</span><span class="sxs-lookup"><span data-stu-id="e0177-102">How to: Detect When the Enter Key Pressed</span></span>
<span data-ttu-id="e0177-103">W tym przykładzie pokazano, jak wykryć kiedy <xref:System.Windows.Input.Key.Enter> zostanie naciśnięty klawisz na klawiaturze.</span><span class="sxs-lookup"><span data-stu-id="e0177-103">This example shows how to detect when the <xref:System.Windows.Input.Key.Enter> key is pressed on the keyboard.</span></span>  
  
 <span data-ttu-id="e0177-104">W tym przykładzie składa się z [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] oraz plik CodeBehind.</span><span class="sxs-lookup"><span data-stu-id="e0177-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0177-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="e0177-105">Example</span></span>  
 <span data-ttu-id="e0177-106">Gdy użytkownik naciśnie <xref:System.Windows.Input.Key.Enter> w <xref:System.Windows.Controls.TextBox>, danych wejściowych w polu tekstowym zostanie wyświetlony w innym obszarze [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e0177-106">When the user presses the <xref:System.Windows.Input.Key.Enter> key in the <xref:System.Windows.Controls.TextBox>, the input in the text box appears in another area of the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span></span>  
  
 <span data-ttu-id="e0177-107">Następujące [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] tworzy interfejs użytkownika, który składa się z <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.TextBlock>, a <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="e0177-107">The following [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] creates the user interface, which consists of a <xref:System.Windows.Controls.StackPanel>, a <xref:System.Windows.Controls.TextBlock>, and a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
 [!code-xaml[keydown#KeyDownUI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml#keydownui)]  
  
 <span data-ttu-id="e0177-108">Poniższy kod tworzy <xref:System.Windows.UIElement.KeyDown> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="e0177-108">The following code behind creates the <xref:System.Windows.UIElement.KeyDown> event handler.</span></span>  <span data-ttu-id="e0177-109">W przypadku naciśnięcia klawisza <xref:System.Windows.Input.Key.Enter> klucza, zostanie wyświetlony komunikat w <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="e0177-109">If the key that is pressed is the <xref:System.Windows.Input.Key.Enter> key, a message is displayed in the <xref:System.Windows.Controls.TextBlock>.</span></span>  
  
 [!code-csharp[keydown#KeyDownSample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml.cs#keydownsample)]
 [!code-vb[keydown#KeyDownSample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/KeyDown/VisualBasic/Window1.xaml.vb#keydownsample)]  
  
## <a name="see-also"></a><span data-ttu-id="e0177-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e0177-110">See also</span></span>
- [<span data-ttu-id="e0177-111">Przegląd danych wejściowych</span><span class="sxs-lookup"><span data-stu-id="e0177-111">Input Overview</span></span>](../../../../docs/framework/wpf/advanced/input-overview.md)
- [<span data-ttu-id="e0177-112">Przegląd zdarzeń trasowanych</span><span class="sxs-lookup"><span data-stu-id="e0177-112">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
