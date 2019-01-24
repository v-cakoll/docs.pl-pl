---
title: 'Instrukcje: Pobierz wybór tekstu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [WPF], retrieving
- TextBox control [WPF], retrieving text
- retrieving text [WPF]
ms.assetid: d5793172-1e11-4a39-9be0-73f336ed858d
ms.openlocfilehash: 3e2a4d9938f73cb306e8fd8b0e6b25b5abfa3b4a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54517776"
---
# <a name="how-to-retrieve-a-text-selection"></a><span data-ttu-id="7cf84-102">Instrukcje: Pobierz wybór tekstu</span><span class="sxs-lookup"><span data-stu-id="7cf84-102">How to: Retrieve a Text Selection</span></span>
<span data-ttu-id="7cf84-103">Ten przykład przedstawia sposób użycia <xref:System.Windows.Controls.TextBox.SelectedText%2A> właściwość służąca do pobierania tekstu zaznaczonego na <xref:System.Windows.Controls.TextBox> kontroli.</span><span class="sxs-lookup"><span data-stu-id="7cf84-103">This example shows one way to use the <xref:System.Windows.Controls.TextBox.SelectedText%2A> property to retrieve text that the user has selected in a <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7cf84-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cf84-104">Example</span></span>  
 <span data-ttu-id="7cf84-105">Następujące [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przykład przedstawia definicję <xref:System.Windows.Controls.TextBox> formant, który zawiera tekst, który zostanie wybrana, i <xref:System.Windows.Controls.Button> kontrolki z określonym <xref:System.Windows.Controls.Button.OnClick%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="7cf84-105">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example shows the definition of a <xref:System.Windows.Controls.TextBox> control that contains some text to select, and a <xref:System.Windows.Controls.Button> control with a specified <xref:System.Windows.Controls.Button.OnClick%2A> method.</span></span>  
  
 <span data-ttu-id="7cf84-106">W tym przykładzie przycisku ze skojarzoną <xref:System.Windows.Controls.Primitives.ButtonBase.Click> program obsługi zdarzeń służy do pobierania zaznaczonego tekstu.</span><span class="sxs-lookup"><span data-stu-id="7cf84-106">In this example, a button with an associated <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler is used to retrieve the text selection.</span></span> <span data-ttu-id="7cf84-107">Gdy użytkownik kliknie przycisk, <xref:System.Windows.Controls.Button.OnClick%2A> metoda Kopiuje zaznaczony tekst w polu tekstowym w ciąg.</span><span class="sxs-lookup"><span data-stu-id="7cf84-107">When the user clicks the button, the <xref:System.Windows.Controls.Button.OnClick%2A> method copies any selected text in the textbox into a string.</span></span> <span data-ttu-id="7cf84-108">Szczególne okoliczności, przez które zaznaczonego tekstu są pobierane (kliknięcie przycisku), również akcji wykonywanej za pomocą tego zaznaczenia (skopiowanie zaznaczonego tekstu do ciągu), można łatwo zmodyfikowane w celu uwzględnienia wielu różnych scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="7cf84-108">The particular circumstances by which the text selection is retrieved (clicking a button), as well as the action taken with that selection (copying the text selection to a string), can easily be modified to accommodate a wide variety of scenarios.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_TextBoxSelectTextXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxselecttextxaml)]  
  
## <a name="example"></a><span data-ttu-id="7cf84-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cf84-109">Example</span></span>  
 <span data-ttu-id="7cf84-110">Następujące C# pokazano w przykładzie <xref:System.Windows.Controls.Button.OnClick%2A> programu obsługi zdarzeń dla przycisku, zdefiniowane w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7cf84-110">The following C# example shows an <xref:System.Windows.Controls.Button.OnClick%2A> event handler for the button defined in the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] for this example.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_SelectText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_selecttext)]
 [!code-vb[TextBox_MiscCode#_SelectText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_selecttext)]  
  
## <a name="see-also"></a><span data-ttu-id="7cf84-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7cf84-111">See also</span></span>
- [<span data-ttu-id="7cf84-112">TextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="7cf84-112">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)
- [<span data-ttu-id="7cf84-113">RichTextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="7cf84-113">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
