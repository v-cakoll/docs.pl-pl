---
title: 'Instrukcje: Ustaw położenie menu kontekstowego w RichTextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom context menus [WPF], positioning
- positioning custom context menus [WPF]
- RichTextBox control [WPF], positioning custom context menus
- context menus [WPF], positioning
ms.assetid: bf77c930-a546-4573-9a56-9af345ba189a
ms.openlocfilehash: abb5bbb5d5a537b14f334782e87fa7caf0c7976f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57367885"
---
# <a name="how-to-position-a-custom-context-menu-in-a-richtextbox"></a><span data-ttu-id="84eaf-102">Instrukcje: Ustaw położenie menu kontekstowego w RichTextBox</span><span class="sxs-lookup"><span data-stu-id="84eaf-102">How to: Position a Custom Context Menu in a RichTextBox</span></span>
<span data-ttu-id="84eaf-103">W tym przykładzie pokazano, jak położenie menu kontekstowego dla <xref:System.Windows.Controls.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="84eaf-103">This example shows how to position a custom context menu for a <xref:System.Windows.Controls.RichTextBox>.</span></span>  
  
 <span data-ttu-id="84eaf-104">Podczas implementacji menu kontekstowego dla **RichTextBox**, jesteś odpowiedzialny za obsługę położenie menu kontekstowego.</span><span class="sxs-lookup"><span data-stu-id="84eaf-104">When you implement a custom context menu for a **RichTextBox**, you are responsible for handling the placement of the context menu.</span></span>  <span data-ttu-id="84eaf-105">Domyślnie menu kontekstowego jest otwarty w środku **RichTextBox**.</span><span class="sxs-lookup"><span data-stu-id="84eaf-105">By default, a custom context menu is opened at the center of the **RichTextBox**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84eaf-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="84eaf-106">Example</span></span>  
 <span data-ttu-id="84eaf-107">Aby zastąpić domyślne zachowanie umieszczania, dodanie detektora <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="84eaf-107">To override the default placement behavior, add a listener for the <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> event.</span></span>  <span data-ttu-id="84eaf-108">Poniższy przykład pokazuje, jak to zrobić programowo.</span><span class="sxs-lookup"><span data-stu-id="84eaf-108">The following example shows how to do this programmatically.</span></span>  
  
 [!code-csharp[RichTextBox_ContextMenu#_AddListener](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_ContextMenu/CSharp/app.xaml.cs#_addlistener)]
 [!code-vb[RichTextBox_ContextMenu#_AddListener](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBox_ContextMenu/VisualBasic/app.xaml.vb#_addlistener)]  
  
## <a name="example"></a><span data-ttu-id="84eaf-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="84eaf-109">Example</span></span>  
 <span data-ttu-id="84eaf-110">W poniższym przykładzie pokazano implementację odpowiednich <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> odbiornik zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="84eaf-110">The following example shows an implementation the corresponding <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> event listener.</span></span>  
  
 [!code-csharp[RichTextBox_ContextMenu#_ListenerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_ContextMenu/CSharp/app.xaml.cs#_listenerbody)]
 [!code-vb[RichTextBox_ContextMenu#_ListenerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBox_ContextMenu/VisualBasic/app.xaml.vb#_listenerbody)]  
  
## <a name="see-also"></a><span data-ttu-id="84eaf-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="84eaf-111">See also</span></span>
- [<span data-ttu-id="84eaf-112">RichTextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="84eaf-112">RichTextBox Overview</span></span>](richtextbox-overview.md)
- [<span data-ttu-id="84eaf-113">TextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="84eaf-113">TextBox Overview</span></span>](textbox-overview.md)
