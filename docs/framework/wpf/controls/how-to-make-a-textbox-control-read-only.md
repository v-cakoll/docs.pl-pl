---
title: "Jak utworzyć formant TextBox tylko do odczytu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- read-only TextBox controls [WPF]
- TextBox control read-only
ms.assetid: e707ec59-8b22-473e-b77c-3060a237517a
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f3d3acf1e5065633f9f4c75f24780230525b01ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-make-a-textbox-control-read-only"></a><span data-ttu-id="ebbca-102">Jak utworzyć formant TextBox tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="ebbca-102">How to: Make a TextBox Control Read-Only</span></span>
<span data-ttu-id="ebbca-103">W tym przykładzie przedstawiono sposób konfigurowania <xref:System.Windows.Controls.TextBox> formantu nie zezwalać na dane wejściowe użytkownika lub modyfikacji.</span><span class="sxs-lookup"><span data-stu-id="ebbca-103">This example shows how to configure a <xref:System.Windows.Controls.TextBox> control to not allow user input or modification.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ebbca-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="ebbca-104">Example</span></span>  
 <span data-ttu-id="ebbca-105">Aby zapobiec modyfikowaniu zawartości <xref:System.Windows.Controls.TextBox> kontrolować, ustaw <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> atrybutu **true**.</span><span class="sxs-lookup"><span data-stu-id="ebbca-105">To prevent users from modifying the contents of a <xref:System.Windows.Controls.TextBox> control, set the <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> attribute to **true**.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_ReadOnlyTextBoxXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_readonlytextboxxaml)]  
  
 <span data-ttu-id="ebbca-106"><xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> Atrybutu dotyczy tylko danych wejściowych użytkownika; nie ma wpływu na tekst w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] opis <xref:System.Windows.Controls.TextBox> formant lub programistycznie za pomocą tekstem <xref:System.Windows.Controls.TextBox.Text%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="ebbca-106">The <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> attribute affects user input only; it does not affect text set in the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] description of a <xref:System.Windows.Controls.TextBox> control, or text set programmatically through the <xref:System.Windows.Controls.TextBox.Text%2A> property.</span></span>  
  
 <span data-ttu-id="ebbca-107">Wartość domyślna <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> jest **false**.</span><span class="sxs-lookup"><span data-stu-id="ebbca-107">The default value of <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> is **false**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebbca-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ebbca-108">See Also</span></span>  
 [<span data-ttu-id="ebbca-109">TextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="ebbca-109">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="ebbca-110">RichTextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="ebbca-110">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
