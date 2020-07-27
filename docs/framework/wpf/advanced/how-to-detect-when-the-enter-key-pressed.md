---
title: Jak wykryć kiedy wciśnięto klawisz Enter
description: Wykryj, kiedy wybrano klawisz Enter na klawiaturze w Windows Presentation Foundation. Ten przykład składa się z kodu XAML i pliku związanego z kodem.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Enter key [WPF], detecting
- keys [WPF], Enter
ms.assetid: a66f39d2-ef4a-43a5-b454-a4ea0fe88655
ms.openlocfilehash: a955f52ec7bf93b32c70259b27fb51747664ac2e
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163183"
---
# <a name="how-to-detect-when-the-enter-key-pressed"></a><span data-ttu-id="68cf2-104">Jak wykryć kiedy wciśnięto klawisz Enter</span><span class="sxs-lookup"><span data-stu-id="68cf2-104">How to: Detect When the Enter Key Pressed</span></span>
<span data-ttu-id="68cf2-105">Ten przykład pokazuje, jak wykryć <xref:System.Windows.Input.Key.Enter> klawisz na klawiaturze.</span><span class="sxs-lookup"><span data-stu-id="68cf2-105">This example shows how to detect when the <xref:System.Windows.Input.Key.Enter> key is pressed on the keyboard.</span></span>  
  
 <span data-ttu-id="68cf2-106">Ten przykład zawiera [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] plik i plik związany z kodem.</span><span class="sxs-lookup"><span data-stu-id="68cf2-106">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="68cf2-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="68cf2-107">Example</span></span>  
 <span data-ttu-id="68cf2-108">Gdy użytkownik naciśnie klawisz <xref:System.Windows.Input.Key.Enter> w <xref:System.Windows.Controls.TextBox> , dane wejściowe w polu tekstowym pojawiają się w innym obszarze [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="68cf2-108">When the user presses the <xref:System.Windows.Input.Key.Enter> key in the <xref:System.Windows.Controls.TextBox>, the input in the text box appears in another area of the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span></span>  
  
 <span data-ttu-id="68cf2-109">Poniższy kod XAML tworzy interfejs użytkownika, który składa się z <xref:System.Windows.Controls.StackPanel> , a <xref:System.Windows.Controls.TextBlock> i <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="68cf2-109">The following XAML creates the user interface, which consists of a <xref:System.Windows.Controls.StackPanel>, a <xref:System.Windows.Controls.TextBlock>, and a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
 [!code-xaml[keydown#KeyDownUI](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml#keydownui)]  
  
 <span data-ttu-id="68cf2-110">Poniższy kod w tle tworzy <xref:System.Windows.UIElement.KeyDown> procedurę obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="68cf2-110">The following code behind creates the <xref:System.Windows.UIElement.KeyDown> event handler.</span></span>  <span data-ttu-id="68cf2-111">Jeśli klawisz, który jest wciśnięty <xref:System.Windows.Input.Key.Enter> , jest wyświetlany w oknie <xref:System.Windows.Controls.TextBlock> .</span><span class="sxs-lookup"><span data-stu-id="68cf2-111">If the key that is pressed is the <xref:System.Windows.Input.Key.Enter> key, a message is displayed in the <xref:System.Windows.Controls.TextBlock>.</span></span>  
  
 [!code-csharp[keydown#KeyDownSample](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml.cs#keydownsample)]
 [!code-vb[keydown#KeyDownSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyDown/VisualBasic/Window1.xaml.vb#keydownsample)]  
  
## <a name="see-also"></a><span data-ttu-id="68cf2-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="68cf2-112">See also</span></span>

- [<span data-ttu-id="68cf2-113">Przegląd Dane wejściowe</span><span class="sxs-lookup"><span data-stu-id="68cf2-113">Input Overview</span></span>](input-overview.md)
- [<span data-ttu-id="68cf2-114">Przegląd Zdarzenia trasowane</span><span class="sxs-lookup"><span data-stu-id="68cf2-114">Routed Events Overview</span></span>](routed-events-overview.md)
