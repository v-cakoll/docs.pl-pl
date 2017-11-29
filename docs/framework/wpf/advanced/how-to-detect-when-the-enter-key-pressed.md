---
title: "Jak wykryć kiedy wciśnięto klawisz Enter"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Enter key [WPF], detecting
- keys [WPF], Enter
ms.assetid: a66f39d2-ef4a-43a5-b454-a4ea0fe88655
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8311083b4b82d4ab4827e8d0a2cf958c67347014
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-detect-when-the-enter-key-pressed"></a><span data-ttu-id="ad7d4-102">Jak wykryć kiedy wciśnięto klawisz Enter</span><span class="sxs-lookup"><span data-stu-id="ad7d4-102">How to: Detect When the Enter Key Pressed</span></span>
<span data-ttu-id="ad7d4-103">W tym przykładzie pokazano, jak podczas wykrywania <xref:System.Windows.Input.Key.Enter> naciśnięcia klawisza na klawiaturze.</span><span class="sxs-lookup"><span data-stu-id="ad7d4-103">This example shows how to detect when the <xref:System.Windows.Input.Key.Enter> key is pressed on the keyboard.</span></span>  
  
 <span data-ttu-id="ad7d4-104">W tym przykładzie składa się z [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] oraz plik CodeBehind.</span><span class="sxs-lookup"><span data-stu-id="ad7d4-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad7d4-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="ad7d4-105">Example</span></span>  
 <span data-ttu-id="ad7d4-106">Gdy użytkownik naciśnie <xref:System.Windows.Input.Key.Enter> klucza w <xref:System.Windows.Controls.TextBox>, danych wejściowych w polu tekstowym pojawia się w innym obszarze [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ad7d4-106">When the user presses the <xref:System.Windows.Input.Key.Enter> key in the <xref:System.Windows.Controls.TextBox>, the input in the text box appears in another area of the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span></span>  
  
 <span data-ttu-id="ad7d4-107">Następujące [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] tworzy interfejs użytkownika, który składa się z <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.TextBlock>, a <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="ad7d4-107">The following [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] creates the user interface, which consists of a <xref:System.Windows.Controls.StackPanel>, a <xref:System.Windows.Controls.TextBlock>, and a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
 [!code-xaml[keydown#KeyDownUI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml#keydownui)]  
  
 <span data-ttu-id="ad7d4-108">Poniższy kod za tworzy <xref:System.Windows.UIElement.KeyDown> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="ad7d4-108">The following code behind creates the <xref:System.Windows.UIElement.KeyDown> event handler.</span></span>  <span data-ttu-id="ad7d4-109">W przypadku naciśnięcia klawisza <xref:System.Windows.Input.Key.Enter> klucza, zostanie wyświetlony komunikat w <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="ad7d4-109">If the key that is pressed is the <xref:System.Windows.Input.Key.Enter> key, a message is displayed in the <xref:System.Windows.Controls.TextBlock>.</span></span>  
  
 [!code-csharp[keydown#KeyDownSample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml.cs#keydownsample)]
 [!code-vb[keydown#KeyDownSample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/KeyDown/VisualBasic/Window1.xaml.vb#keydownsample)]  
  
## <a name="see-also"></a><span data-ttu-id="ad7d4-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ad7d4-110">See Also</span></span>  
 [<span data-ttu-id="ad7d4-111">Dane wejściowe — omówienie</span><span class="sxs-lookup"><span data-stu-id="ad7d4-111">Input Overview</span></span>](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [<span data-ttu-id="ad7d4-112">Omówienie kierowane zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ad7d4-112">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
