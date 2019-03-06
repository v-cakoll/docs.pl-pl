---
title: 'Instrukcje: Zmień typ kursora'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mouse pointer [WPF], cursor type
- cursor (mouse pointer)
ms.assetid: 08c945a7-8ab0-4320-acf3-0b4955a344c2
ms.openlocfilehash: e62658f4c4249c93bd24dffd3878dd2ec2b75029
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57371159"
---
# <a name="how-to-change-the-cursor-type"></a><span data-ttu-id="3b67d-102">Instrukcje: Zmień typ kursora</span><span class="sxs-lookup"><span data-stu-id="3b67d-102">How to: Change the Cursor Type</span></span>
<span data-ttu-id="3b67d-103">W tym przykładzie pokazano, jak zmienić <xref:System.Windows.Input.Cursor> wskaźnika myszy dla określonego elementu i aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3b67d-103">This example shows how to change the <xref:System.Windows.Input.Cursor> of the mouse pointer for a specific element and for the application.</span></span>  
  
 <span data-ttu-id="3b67d-104">W tym przykładzie składa się z [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] plików i pliku CodeBehind.</span><span class="sxs-lookup"><span data-stu-id="3b67d-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b67d-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="3b67d-105">Example</span></span>  
 <span data-ttu-id="3b67d-106">Jest tworzony interfejs użytkownika, który składa się z <xref:System.Windows.Controls.ComboBox> wybrać żądaną <xref:System.Windows.Input.Cursor>, parę <xref:System.Windows.Controls.RadioButton> obiekty do ustalenia, czy zmiana kursora dotyczy tylko pojedynczy element lub ma zastosowanie do całej aplikacji i <xref:System.Windows.Controls.Border> czyli element, który nowy kursor jest stosowany do.</span><span class="sxs-lookup"><span data-stu-id="3b67d-106">The user interface is created, which consists of a <xref:System.Windows.Controls.ComboBox> to select the desired <xref:System.Windows.Input.Cursor>, a pair of <xref:System.Windows.Controls.RadioButton> objects to determine if the cursor change applies to only a single element or applies to the entire application, and a <xref:System.Windows.Controls.Border> which is the element that the new cursor is applied to.</span></span>  
  
 [!code-xaml[cursors#ChangeCursorsXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml#changecursorsxaml)]  
  
 <span data-ttu-id="3b67d-107">Poniższy kod tworzy <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> programu obsługi zdarzeń, które jest wywoływane, gdy typ kursora jest zmieniana w <xref:System.Windows.Controls.ComboBox>.</span><span class="sxs-lookup"><span data-stu-id="3b67d-107">The following code behind creates a <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event handler which is called when the cursor type is changed in the <xref:System.Windows.Controls.ComboBox>.</span></span>  <span data-ttu-id="3b67d-108">Filtr nazwy kursora i zestawy instrukcji switch <xref:System.Windows.FrameworkElement.Cursor%2A> właściwość <xref:System.Windows.Controls.Border> który nosi *DisplayArea*.</span><span class="sxs-lookup"><span data-stu-id="3b67d-108">A switch statement filters on the cursor name and sets the <xref:System.Windows.FrameworkElement.Cursor%2A> property on the <xref:System.Windows.Controls.Border> which is named *DisplayArea*.</span></span>  
  
 <span data-ttu-id="3b67d-109">Jeśli zmiana kursora jest równa "Całą aplikację" <xref:System.Windows.Input.Mouse.OverrideCursor%2A> właściwość jest ustawiona na <xref:System.Windows.FrameworkElement.Cursor%2A> właściwość <xref:System.Windows.Controls.Border> kontroli.</span><span class="sxs-lookup"><span data-stu-id="3b67d-109">If the cursor change is set to "Entire Application", the <xref:System.Windows.Input.Mouse.OverrideCursor%2A> property is set to the <xref:System.Windows.FrameworkElement.Cursor%2A> property of the <xref:System.Windows.Controls.Border> control.</span></span>  <span data-ttu-id="3b67d-110">Wymusza kursora, aby zmienić dla całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3b67d-110">This forces the cursor to change for the whole application.</span></span>  
  
 [!code-csharp[cursors#ChangeCursorsSample](~/samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml.cs#changecursorssample)]
 [!code-vb[cursors#ChangeCursorsSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/cursors/VisualBasic/Window1.xaml.vb#changecursorssample)]  
  
## <a name="see-also"></a><span data-ttu-id="3b67d-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3b67d-111">See also</span></span>
- [<span data-ttu-id="3b67d-112">Przegląd danych wejściowych</span><span class="sxs-lookup"><span data-stu-id="3b67d-112">Input Overview</span></span>](input-overview.md)
