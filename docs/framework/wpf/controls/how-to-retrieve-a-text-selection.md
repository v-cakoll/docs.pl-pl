---
title: Jak odzyskać wybór tekstu
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [WPF], retrieving
- TextBox control [WPF], retrieving text
- retrieving text [WPF]
ms.assetid: d5793172-1e11-4a39-9be0-73f336ed858d
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d010d0c5bbe5ba3cad826df74d054af4c9b8f452
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-retrieve-a-text-selection"></a><span data-ttu-id="e76d6-102">Jak odzyskać wybór tekstu</span><span class="sxs-lookup"><span data-stu-id="e76d6-102">How to: Retrieve a Text Selection</span></span>
<span data-ttu-id="e76d6-103">W tym przykładzie pokazano sposób użycia <xref:System.Windows.Controls.TextBox.SelectedText%2A> właściwości do pobierania tekstu zaznaczonego w <xref:System.Windows.Controls.TextBox> formantu.</span><span class="sxs-lookup"><span data-stu-id="e76d6-103">This example shows one way to use the <xref:System.Windows.Controls.TextBox.SelectedText%2A> property to retrieve text that the user has selected in a <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e76d6-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="e76d6-104">Example</span></span>  
 <span data-ttu-id="e76d6-105">Następujące [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przykładzie pokazano definicję <xref:System.Windows.Controls.TextBox> kontrolki zawierającej tekst, który zostanie wybrana, a <xref:System.Windows.Controls.Button> kontroli z określonym <xref:System.Windows.Controls.Button.OnClick%2A> — metoda.</span><span class="sxs-lookup"><span data-stu-id="e76d6-105">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example shows the definition of a <xref:System.Windows.Controls.TextBox> control that contains some text to select, and a <xref:System.Windows.Controls.Button> control with a specified <xref:System.Windows.Controls.Button.OnClick%2A> method.</span></span>  
  
 <span data-ttu-id="e76d6-106">W tym przykładzie przycisk skojarzony <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obsługi zdarzeń służy do pobierania zaznaczonego tekstu.</span><span class="sxs-lookup"><span data-stu-id="e76d6-106">In this example, a button with an associated <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler is used to retrieve the text selection.</span></span> <span data-ttu-id="e76d6-107">Gdy użytkownik kliknie przycisk <xref:System.Windows.Controls.Button.OnClick%2A> metoda Kopiuje zaznaczony tekst w polu tekstowym na ciąg.</span><span class="sxs-lookup"><span data-stu-id="e76d6-107">When the user clicks the button, the <xref:System.Windows.Controls.Button.OnClick%2A> method copies any selected text in the textbox into a string.</span></span> <span data-ttu-id="e76d6-108">Okoliczności za pomocą których zaznaczenie tekstu jest pobierana (kliknięcie przycisku), jak i akcji wykonanych za pomocą tego zaznaczenia (kopiowanie zaznaczenia tekstu do ciągu), można łatwo zmodyfikowane w celu uwzględnienia wielu różnych scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="e76d6-108">The particular circumstances by which the text selection is retrieved (clicking a button), as well as the action taken with that selection (copying the text selection to a string), can easily be modified to accommodate a wide variety of scenarios.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_TextBoxSelectTextXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxselecttextxaml)]  
  
## <a name="example"></a><span data-ttu-id="e76d6-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="e76d6-109">Example</span></span>  
 <span data-ttu-id="e76d6-110">C# ilustruje przykład <xref:System.Windows.Controls.Button.OnClick%2A> programu obsługi zdarzeń dla przycisku zdefiniowane w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e76d6-110">The following C# example shows an <xref:System.Windows.Controls.Button.OnClick%2A> event handler for the button defined in the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] for this example.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_SelectText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_selecttext)]
 [!code-vb[TextBox_MiscCode#_SelectText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_selecttext)]  
  
## <a name="see-also"></a><span data-ttu-id="e76d6-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e76d6-111">See Also</span></span>  
 [<span data-ttu-id="e76d6-112">TextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="e76d6-112">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="e76d6-113">RichTextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="e76d6-113">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
