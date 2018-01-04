---
title: "Jak ustawić położenie menu kontekstowego w RichTextBox"
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
- custom context menus [WPF], positioning
- positioning custom context menus [WPF]
- RichTextBox control [WPF], positioning custom context menus
- context menus [WPF], positioning
ms.assetid: bf77c930-a546-4573-9a56-9af345ba189a
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4651953ec8ae6373b9a6946b31f96213bec570cc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-position-a-custom-context-menu-in-a-richtextbox"></a><span data-ttu-id="cb39d-102">Jak ustawić położenie menu kontekstowego w RichTextBox</span><span class="sxs-lookup"><span data-stu-id="cb39d-102">How to: Position a Custom Context Menu in a RichTextBox</span></span>
<span data-ttu-id="cb39d-103">W tym przykładzie pokazano, jak pozycja menu kontekstowego niestandardowych dla <xref:System.Windows.Controls.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="cb39d-103">This example shows how to position a custom context menu for a <xref:System.Windows.Controls.RichTextBox>.</span></span>  
  
 <span data-ttu-id="cb39d-104">Podczas implementacji menu kontekstowe niestandardowych **RichTextBox**, jest odpowiedzialny za obsługę położenie menu kontekstowego.</span><span class="sxs-lookup"><span data-stu-id="cb39d-104">When you implement a custom context menu for a **RichTextBox**, you are responsible for handling the placement of the context menu.</span></span>  <span data-ttu-id="cb39d-105">Domyślnie menu kontekstowe niestandardowy jest otwarty w Centrum **RichTextBox**.</span><span class="sxs-lookup"><span data-stu-id="cb39d-105">By default, a custom context menu is opened at the center of the **RichTextBox**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb39d-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="cb39d-106">Example</span></span>  
 <span data-ttu-id="cb39d-107">Aby zastąpić domyślne zachowanie umieszczania, Dodaj odbiornika dla <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="cb39d-107">To override the default placement behavior, add a listener for the <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> event.</span></span>  <span data-ttu-id="cb39d-108">Poniższy przykład pokazuje, jak to zrobić programowo.</span><span class="sxs-lookup"><span data-stu-id="cb39d-108">The following example shows how to do this programmatically.</span></span>  
  
 [!code-csharp[RichTextBox_ContextMenu#_AddListener](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_ContextMenu/CSharp/app.xaml.cs#_addlistener)]
 [!code-vb[RichTextBox_ContextMenu#_AddListener](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBox_ContextMenu/VisualBasic/app.xaml.vb#_addlistener)]  
  
## <a name="example"></a><span data-ttu-id="cb39d-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="cb39d-109">Example</span></span>  
 <span data-ttu-id="cb39d-110">Poniższy przykład przedstawia implementację odpowiadającego <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> odbiornik zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="cb39d-110">The following example shows an implementation the corresponding <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> event listener.</span></span>  
  
 [!code-csharp[RichTextBox_ContextMenu#_ListenerBody](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_ContextMenu/CSharp/app.xaml.cs#_listenerbody)]
 [!code-vb[RichTextBox_ContextMenu#_ListenerBody](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBox_ContextMenu/VisualBasic/app.xaml.vb#_listenerbody)]  
  
## <a name="see-also"></a><span data-ttu-id="cb39d-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cb39d-111">See Also</span></span>  
 [<span data-ttu-id="cb39d-112">RichTextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="cb39d-112">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)  
 [<span data-ttu-id="cb39d-113">TextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="cb39d-113">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)
