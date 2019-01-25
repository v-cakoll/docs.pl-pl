---
title: 'Instrukcje: Utwórz formant TextBox tylko do odczytu'
ms.date: 03/30/2017
helpviewer_keywords:
- read-only TextBox controls [WPF]
- TextBox control read-only
ms.assetid: e707ec59-8b22-473e-b77c-3060a237517a
ms.openlocfilehash: 1e9d333f22099d9593e58b4087f185b2988215ce
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54517178"
---
# <a name="how-to-make-a-textbox-control-read-only"></a><span data-ttu-id="86e82-102">Instrukcje: Utwórz formant TextBox tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="86e82-102">How to: Make a TextBox Control Read-Only</span></span>
<span data-ttu-id="86e82-103">W tym przykładzie pokazano, jak skonfigurować <xref:System.Windows.Controls.TextBox> formantu nie zezwalać na dane wejściowe użytkownika lub modyfikacji.</span><span class="sxs-lookup"><span data-stu-id="86e82-103">This example shows how to configure a <xref:System.Windows.Controls.TextBox> control to not allow user input or modification.</span></span>  
  
## <a name="example"></a><span data-ttu-id="86e82-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="86e82-104">Example</span></span>  
 <span data-ttu-id="86e82-105">Aby uniemożliwić użytkownikom modyfikowanie zawartości <xref:System.Windows.Controls.TextBox> , ustaw <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> atrybutu **true**.</span><span class="sxs-lookup"><span data-stu-id="86e82-105">To prevent users from modifying the contents of a <xref:System.Windows.Controls.TextBox> control, set the <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> attribute to **true**.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_ReadOnlyTextBoxXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_readonlytextboxxaml)]  
  
 <span data-ttu-id="86e82-106"><xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> Atrybutu, dotyczy tylko dane wejściowe użytkownika; nie ma wpływu na tekstu, ustawianego [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] opis <xref:System.Windows.Controls.TextBox> formantu lub tekstu, ustawianego programowo za pomocą <xref:System.Windows.Controls.TextBox.Text%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="86e82-106">The <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> attribute affects user input only; it does not affect text set in the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] description of a <xref:System.Windows.Controls.TextBox> control, or text set programmatically through the <xref:System.Windows.Controls.TextBox.Text%2A> property.</span></span>  
  
 <span data-ttu-id="86e82-107">Wartość domyślna <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> jest **false**.</span><span class="sxs-lookup"><span data-stu-id="86e82-107">The default value of <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> is **false**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86e82-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86e82-108">See also</span></span>
- [<span data-ttu-id="86e82-109">TextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="86e82-109">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)
- [<span data-ttu-id="86e82-110">RichTextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="86e82-110">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
