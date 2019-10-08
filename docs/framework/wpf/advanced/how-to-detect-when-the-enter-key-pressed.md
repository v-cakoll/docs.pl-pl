---
title: Jak wykryć kiedy wciśnięto klawisz Enter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Enter key [WPF], detecting
- keys [WPF], Enter
ms.assetid: a66f39d2-ef4a-43a5-b454-a4ea0fe88655
ms.openlocfilehash: e2337826077c836696937f91541d6d261f1270aa
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004822"
---
# <a name="how-to-detect-when-the-enter-key-pressed"></a><span data-ttu-id="f2834-102">Jak wykryć kiedy wciśnięto klawisz Enter</span><span class="sxs-lookup"><span data-stu-id="f2834-102">How to: Detect When the Enter Key Pressed</span></span>
<span data-ttu-id="f2834-103">Ten przykład pokazuje, jak wykryć, kiedy naciśnięto klawisz <xref:System.Windows.Input.Key.Enter> na klawiaturze.</span><span class="sxs-lookup"><span data-stu-id="f2834-103">This example shows how to detect when the <xref:System.Windows.Input.Key.Enter> key is pressed on the keyboard.</span></span>  
  
 <span data-ttu-id="f2834-104">Ten przykład składa się z pliku [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] i pliku związanego z kodem.</span><span class="sxs-lookup"><span data-stu-id="f2834-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2834-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="f2834-105">Example</span></span>  
 <span data-ttu-id="f2834-106">Gdy użytkownik naciśnie klawisz <xref:System.Windows.Input.Key.Enter> w <xref:System.Windows.Controls.TextBox>, dane wejściowe w polu tekstowym pojawiają się w innym obszarze [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f2834-106">When the user presses the <xref:System.Windows.Input.Key.Enter> key in the <xref:System.Windows.Controls.TextBox>, the input in the text box appears in another area of the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span></span>  
  
 <span data-ttu-id="f2834-107">Poniższy kod XAML tworzy interfejs użytkownika, który składa się z <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.TextBlock> i <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="f2834-107">The following XAML creates the user interface, which consists of a <xref:System.Windows.Controls.StackPanel>, a <xref:System.Windows.Controls.TextBlock>, and a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
 [!code-xaml[keydown#KeyDownUI](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml#keydownui)]  
  
 <span data-ttu-id="f2834-108">Poniższy kod w tle tworzy procedurę obsługi zdarzeń <xref:System.Windows.UIElement.KeyDown>.</span><span class="sxs-lookup"><span data-stu-id="f2834-108">The following code behind creates the <xref:System.Windows.UIElement.KeyDown> event handler.</span></span>  <span data-ttu-id="f2834-109">Jeśli klawisz, który jest wciśnięty, jest kluczem <xref:System.Windows.Input.Key.Enter>, zostanie wyświetlony komunikat w <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="f2834-109">If the key that is pressed is the <xref:System.Windows.Input.Key.Enter> key, a message is displayed in the <xref:System.Windows.Controls.TextBlock>.</span></span>  
  
 [!code-csharp[keydown#KeyDownSample](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml.cs#keydownsample)]
 [!code-vb[keydown#KeyDownSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyDown/VisualBasic/Window1.xaml.vb#keydownsample)]  
  
## <a name="see-also"></a><span data-ttu-id="f2834-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f2834-110">See also</span></span>

- [<span data-ttu-id="f2834-111">Przegląd danych wejściowych</span><span class="sxs-lookup"><span data-stu-id="f2834-111">Input Overview</span></span>](input-overview.md)
- [<span data-ttu-id="f2834-112">Przegląd zdarzeń trasowanych</span><span class="sxs-lookup"><span data-stu-id="f2834-112">Routed Events Overview</span></span>](routed-events-overview.md)
