---
title: "Jak zmienić typ kursora"
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
- mouse pointer [WPF], cursor type
- cursor (mouse pointer)
ms.assetid: 08c945a7-8ab0-4320-acf3-0b4955a344c2
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 31c59f4c90eed00775fc9fceaf872391faa93784
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-cursor-type"></a><span data-ttu-id="856e8-102">Jak zmienić typ kursora</span><span class="sxs-lookup"><span data-stu-id="856e8-102">How to: Change the Cursor Type</span></span>
<span data-ttu-id="856e8-103">W tym przykładzie pokazano, jak zmienić <xref:System.Windows.Input.Cursor> wskaźnika myszy dla określonego elementu i aplikacji.</span><span class="sxs-lookup"><span data-stu-id="856e8-103">This example shows how to change the <xref:System.Windows.Input.Cursor> of the mouse pointer for a specific element and for the application.</span></span>  
  
 <span data-ttu-id="856e8-104">W tym przykładzie składa się z [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] plików i pliku CodeBehind.</span><span class="sxs-lookup"><span data-stu-id="856e8-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="856e8-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="856e8-105">Example</span></span>  
 <span data-ttu-id="856e8-106">Interfejs użytkownika został utworzony, który składa się z <xref:System.Windows.Controls.ComboBox> wybrać żądaną <xref:System.Windows.Input.Cursor>, para <xref:System.Windows.Controls.RadioButton> obiektów do określenia, czy zmiany kursora dotyczy tylko jeden element i ma zastosowanie do całej aplikacji, a <xref:System.Windows.Controls.Border> czyli element nowy kursor jest stosowany do.</span><span class="sxs-lookup"><span data-stu-id="856e8-106">The user interface is created, which consists of a <xref:System.Windows.Controls.ComboBox> to select the desired <xref:System.Windows.Input.Cursor>, a pair of <xref:System.Windows.Controls.RadioButton> objects to determine if the cursor change applies to only a single element or applies to the entire application, and a <xref:System.Windows.Controls.Border> which is the element that the new cursor is applied to.</span></span>  
  
 [!code-xaml[cursors#ChangeCursorsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml#changecursorsxaml)]  
  
 <span data-ttu-id="856e8-107">Poniższy kod za tworzy <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> obsługi zdarzeń, które jest wywoływane, gdy typ kursora została zmieniona w <xref:System.Windows.Controls.ComboBox>.</span><span class="sxs-lookup"><span data-stu-id="856e8-107">The following code behind creates a <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event handler which is called when the cursor type is changed in the <xref:System.Windows.Controls.ComboBox>.</span></span>  <span data-ttu-id="856e8-108">Instrukcja switch filtry kursora o nazwie i zestawy <xref:System.Windows.FrameworkElement.Cursor%2A> właściwości na <xref:System.Windows.Controls.Border> który o nazwie *DisplayArea*.</span><span class="sxs-lookup"><span data-stu-id="856e8-108">A switch statement filters on the cursor name and sets the <xref:System.Windows.FrameworkElement.Cursor%2A> property on the <xref:System.Windows.Controls.Border> which is named *DisplayArea*.</span></span>  
  
 <span data-ttu-id="856e8-109">Jeśli zmiana kursora jest równa "Całą aplikację" <xref:System.Windows.Input.Mouse.OverrideCursor%2A> właściwość jest ustawiona na <xref:System.Windows.FrameworkElement.Cursor%2A> właściwość <xref:System.Windows.Controls.Border> formantu.</span><span class="sxs-lookup"><span data-stu-id="856e8-109">If the cursor change is set to "Entire Application", the <xref:System.Windows.Input.Mouse.OverrideCursor%2A> property is set to the <xref:System.Windows.FrameworkElement.Cursor%2A> property of the <xref:System.Windows.Controls.Border> control.</span></span>  <span data-ttu-id="856e8-110">Dzięki temu kursor zmiany dla całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="856e8-110">This forces the cursor to change for the whole application.</span></span>  
  
 [!code-csharp[cursors#ChangeCursorsSample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml.cs#changecursorssample)]
 [!code-vb[cursors#ChangeCursorsSample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/cursors/VisualBasic/Window1.xaml.vb#changecursorssample)]  
  
## <a name="see-also"></a><span data-ttu-id="856e8-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="856e8-111">See Also</span></span>  
 [<span data-ttu-id="856e8-112">Przegląd danych wejściowych</span><span class="sxs-lookup"><span data-stu-id="856e8-112">Input Overview</span></span>](../../../../docs/framework/wpf/advanced/input-overview.md)
