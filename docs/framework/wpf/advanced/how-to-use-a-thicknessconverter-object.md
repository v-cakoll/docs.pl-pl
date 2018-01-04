---
title: "Jak użyć obiektu ThicknessConverter"
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
- border thickness [WPF]
- ThicknessConverter objects [WPF]
ms.assetid: 52682194-d7fd-499c-8005-73fcc84e7b2c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 311998595cb1584c276afc28510e1750c770ae93
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-thicknessconverter-object"></a><span data-ttu-id="fc483-102">Jak użyć obiektu ThicknessConverter</span><span class="sxs-lookup"><span data-stu-id="fc483-102">How to: Use a ThicknessConverter Object</span></span>
## <a name="example"></a><span data-ttu-id="fc483-103">Przykład</span><span class="sxs-lookup"><span data-stu-id="fc483-103">Example</span></span>  
 <span data-ttu-id="fc483-104">W tym przykładzie przedstawiono sposób tworzenia wystąpienia <xref:System.Windows.ThicknessConverter> i użyj go, aby zmienić szerokość krawędzi.</span><span class="sxs-lookup"><span data-stu-id="fc483-104">This example shows how to create an instance of <xref:System.Windows.ThicknessConverter> and use it to change the thickness of a border.</span></span>  
  
 <span data-ttu-id="fc483-105">W przykładzie zdefiniowano niestandardowe metodę o nazwie `changeThickness`; ta metoda konwertuje najpierw zawartość <xref:System.Windows.Controls.ListBoxItem>, zgodnie z definicją w oddzielnej [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pliku, aby wystąpienie <xref:System.Windows.Thickness>i później Konwertuje zawartość do <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="fc483-105">The example defines a custom method called `changeThickness`; this method first converts the contents of a <xref:System.Windows.Controls.ListBoxItem>, as defined in a separate [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file, to an instance of <xref:System.Windows.Thickness>, and later converts the content into a <xref:System.String>.</span></span> <span data-ttu-id="fc483-106">Ta metoda przekazuje <xref:System.Windows.Controls.ListBoxItem> do <xref:System.Windows.ThicknessConverter> obiektu, który konwertuje <xref:System.Windows.Controls.ContentControl.Content%2A> z <xref:System.Windows.Controls.ListBoxItem> na wystąpienie <xref:System.Windows.Thickness>.</span><span class="sxs-lookup"><span data-stu-id="fc483-106">This method passes the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.Windows.ThicknessConverter> object, which converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of a <xref:System.Windows.Controls.ListBoxItem> to an instance of <xref:System.Windows.Thickness>.</span></span> <span data-ttu-id="fc483-107">Ta wartość jest następnie przekazywany z powrotem jako wartość <xref:System.Windows.Controls.Border.BorderThickness%2A> właściwość <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="fc483-107">This value is then passed back as the value of the <xref:System.Windows.Controls.Border.BorderThickness%2A> property of the <xref:System.Windows.Controls.Border>.</span></span>  
  
 <span data-ttu-id="fc483-108">W tym przykładzie nie działa.</span><span class="sxs-lookup"><span data-stu-id="fc483-108">This example does not run.</span></span>  
  
 [!code-csharp[ThicknessConverter#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThicknessConverter/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ThicknessConverter#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThicknessConverter/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="fc483-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fc483-109">See Also</span></span>  
 <xref:System.Windows.Thickness>  
 <xref:System.Windows.ThicknessConverter>  
 <xref:System.Windows.Controls.Border>  
 [<span data-ttu-id="fc483-110">Porady: Zmienianie właściwości margines</span><span class="sxs-lookup"><span data-stu-id="fc483-110">How to: Change the Margin Property</span></span>](http://msdn.microsoft.com/en-us/8a313efd-5f99-4097-b4c1-8fa49d8379a2)  
 [<span data-ttu-id="fc483-111">Porady: Konwertowanie elementu ListBoxItem na nowy typ danych</span><span class="sxs-lookup"><span data-stu-id="fc483-111">How to: Convert a ListBoxItem to a new Data Type</span></span>](http://msdn.microsoft.com/en-us/7a080b88-184e-4b27-bb61-d42bafba9727)  
 [<span data-ttu-id="fc483-112">Panele — omówienie</span><span class="sxs-lookup"><span data-stu-id="fc483-112">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
