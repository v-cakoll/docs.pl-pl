---
title: 'Instrukcje: Utwórz formant TextBox tylko do odczytu'
ms.date: 03/30/2017
helpviewer_keywords:
- read-only TextBox controls [WPF]
- TextBox control read-only
ms.assetid: e707ec59-8b22-473e-b77c-3060a237517a
ms.openlocfilehash: 3784471020210f995c8bb0a377d56a2466d97da1
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364545"
---
# <a name="how-to-make-a-textbox-control-read-only"></a><span data-ttu-id="f3e83-102">Instrukcje: Utwórz formant TextBox tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f3e83-102">How to: Make a TextBox Control Read-Only</span></span>
<span data-ttu-id="f3e83-103">W tym przykładzie pokazano, jak skonfigurować <xref:System.Windows.Controls.TextBox> formantu nie zezwalać na dane wejściowe użytkownika lub modyfikacji.</span><span class="sxs-lookup"><span data-stu-id="f3e83-103">This example shows how to configure a <xref:System.Windows.Controls.TextBox> control to not allow user input or modification.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3e83-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="f3e83-104">Example</span></span>  
 <span data-ttu-id="f3e83-105">Aby uniemożliwić użytkownikom modyfikowanie zawartości <xref:System.Windows.Controls.TextBox> , ustaw <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> atrybutu **true**.</span><span class="sxs-lookup"><span data-stu-id="f3e83-105">To prevent users from modifying the contents of a <xref:System.Windows.Controls.TextBox> control, set the <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> attribute to **true**.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_ReadOnlyTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_readonlytextboxxaml)]  
  
 <span data-ttu-id="f3e83-106"><xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> Atrybutu, dotyczy tylko dane wejściowe użytkownika; nie ma wpływu na tekstu, ustawianego [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] opis <xref:System.Windows.Controls.TextBox> formantu lub tekstu, ustawianego programowo za pomocą <xref:System.Windows.Controls.TextBox.Text%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f3e83-106">The <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> attribute affects user input only; it does not affect text set in the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] description of a <xref:System.Windows.Controls.TextBox> control, or text set programmatically through the <xref:System.Windows.Controls.TextBox.Text%2A> property.</span></span>  
  
 <span data-ttu-id="f3e83-107">Wartość domyślna <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> jest **false**.</span><span class="sxs-lookup"><span data-stu-id="f3e83-107">The default value of <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> is **false**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3e83-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f3e83-108">See also</span></span>
- [<span data-ttu-id="f3e83-109">TextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="f3e83-109">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="f3e83-110">RichTextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="f3e83-110">RichTextBox Overview</span></span>](richtextbox-overview.md)
