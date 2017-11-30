---
title: "Jak utworzyć i używać obiekt GridLengthConverter"
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
helpviewer_keywords: Grid control [WPF], creating [WPF], GridLengthConverter objects
ms.assetid: 5ab75911-e36a-4825-80e4-081c57e8e182
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 775d51a35f64f8736931dec32fb439bb9925be53
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-and-use-a-gridlengthconverter-object"></a><span data-ttu-id="b637c-102">Jak utworzyć i używać obiekt GridLengthConverter</span><span class="sxs-lookup"><span data-stu-id="b637c-102">How to: Create and Use a GridLengthConverter Object</span></span>
## <a name="example"></a><span data-ttu-id="b637c-103">Przykład</span><span class="sxs-lookup"><span data-stu-id="b637c-103">Example</span></span>  
 <span data-ttu-id="b637c-104">Poniższy przykład przedstawia sposób tworzenia i używania wystąpienia <xref:System.Windows.GridLengthConverter>.</span><span class="sxs-lookup"><span data-stu-id="b637c-104">The following example shows how to create and use an instance of <xref:System.Windows.GridLengthConverter>.</span></span> <span data-ttu-id="b637c-105">W przykładzie zdefiniowano niestandardowe metodę o nazwie `changeCol`, które przechodzą <xref:System.Windows.Controls.ListBoxItem> do <xref:System.Windows.GridLengthConverter> konwertująca <xref:System.Windows.Controls.ContentControl.Content%2A> z <xref:System.Windows.Controls.ListBoxItem> na wystąpienie <xref:System.Windows.GridLength>.</span><span class="sxs-lookup"><span data-stu-id="b637c-105">The example defines a custom method called `changeCol`, which passes the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.Windows.GridLengthConverter> that converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of a <xref:System.Windows.Controls.ListBoxItem> to an instance of <xref:System.Windows.GridLength>.</span></span> <span data-ttu-id="b637c-106">Wartość przekonwertowana są następnie przekazywane jako wartość <xref:System.Windows.Controls.ColumnDefinition.Width%2A> właściwość <xref:System.Windows.Controls.ColumnDefinition> elementu.</span><span class="sxs-lookup"><span data-stu-id="b637c-106">The converted value is then passed back as the value of the <xref:System.Windows.Controls.ColumnDefinition.Width%2A> property of the <xref:System.Windows.Controls.ColumnDefinition> element.</span></span>  
  
 <span data-ttu-id="b637c-107">W przykładzie zdefiniowano także drugi metody niestandardowe, o nazwie `changeColVal`.</span><span class="sxs-lookup"><span data-stu-id="b637c-107">The example also defines a second custom method, called `changeColVal`.</span></span> <span data-ttu-id="b637c-108">Ta metoda niestandardowych konwertuje <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> z <xref:System.Windows.Controls.Slider> do <xref:System.String> , a następnie przekazuje, które wartości z powrotem do <xref:System.Windows.Controls.ColumnDefinition> jako <xref:System.Windows.Controls.ColumnDefinition.Width%2A> elementu.</span><span class="sxs-lookup"><span data-stu-id="b637c-108">This custom method converts the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> of a <xref:System.Windows.Controls.Slider> to a <xref:System.String> and then passes that value back to the <xref:System.Windows.Controls.ColumnDefinition> as the <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of the element.</span></span>  
  
 <span data-ttu-id="b637c-109">Należy pamiętać, że oddzielnej [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] plik definiuje zawartość <xref:System.Windows.Controls.ListBoxItem>.</span><span class="sxs-lookup"><span data-stu-id="b637c-109">Note that a separate [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file defines the contents of a <xref:System.Windows.Controls.ListBoxItem>.</span></span>  
  
 [!code-csharp[gridlengthConverterGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridlengthConverterGrid/CSharp/Window1.xaml.cs#1)]
 [!code-vb[gridlengthConverterGrid#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridlengthConverterGrid/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="b637c-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b637c-110">See Also</span></span>  
 <xref:System.Windows.GridLengthConverter>  
 <xref:System.Windows.GridLength>
