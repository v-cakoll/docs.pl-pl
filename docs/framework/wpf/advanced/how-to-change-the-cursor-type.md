---
title: Jak zmienić typ kursora
description: Zmień kursor wskaźnika myszy dla elementu i dla aplikacji w Windows Presentation Foundation. Ten przykład składa się z kodu XAML i pliku związanego z kodem.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mouse pointer [WPF], cursor type
- cursor (mouse pointer)
ms.assetid: 08c945a7-8ab0-4320-acf3-0b4955a344c2
ms.openlocfilehash: ce0bc290948a0e52e85f76ceb62a330b49fd87ea
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165961"
---
# <a name="how-to-change-the-cursor-type"></a><span data-ttu-id="d47b7-104">Jak zmienić typ kursora</span><span class="sxs-lookup"><span data-stu-id="d47b7-104">How to: Change the Cursor Type</span></span>
<span data-ttu-id="d47b7-105">Ten przykład pokazuje, jak zmienić <xref:System.Windows.Input.Cursor> wskaźnik myszy dla określonego elementu i dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d47b7-105">This example shows how to change the <xref:System.Windows.Input.Cursor> of the mouse pointer for a specific element and for the application.</span></span>  
  
 <span data-ttu-id="d47b7-106">Ten przykład zawiera plik [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] i plik związany z kodem.</span><span class="sxs-lookup"><span data-stu-id="d47b7-106">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d47b7-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="d47b7-107">Example</span></span>  
 <span data-ttu-id="d47b7-108">Interfejs użytkownika jest tworzony, który składa się z, <xref:System.Windows.Controls.ComboBox> Aby wybrać odpowiednią <xref:System.Windows.Input.Cursor> , parę <xref:System.Windows.Controls.RadioButton> obiektów do określenia, czy zmiana kursora dotyczy tylko pojedynczego elementu, czy ma zastosowanie do całej aplikacji, a także do elementu, <xref:System.Windows.Controls.Border> do którego zostanie zastosowany nowy kursor.</span><span class="sxs-lookup"><span data-stu-id="d47b7-108">The user interface is created, which consists of a <xref:System.Windows.Controls.ComboBox> to select the desired <xref:System.Windows.Input.Cursor>, a pair of <xref:System.Windows.Controls.RadioButton> objects to determine if the cursor change applies to only a single element or applies to the entire application, and a <xref:System.Windows.Controls.Border> which is the element that the new cursor is applied to.</span></span>  
  
 [!code-xaml[cursors#ChangeCursorsXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml#changecursorsxaml)]  
  
 <span data-ttu-id="d47b7-109">Poniższy kod w tle tworzy <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> procedurę obsługi zdarzeń, która jest wywoływana, gdy typ kursora zostanie zmieniony w <xref:System.Windows.Controls.ComboBox> .</span><span class="sxs-lookup"><span data-stu-id="d47b7-109">The following code behind creates a <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event handler which is called when the cursor type is changed in the <xref:System.Windows.Controls.ComboBox>.</span></span>  <span data-ttu-id="d47b7-110">Instrukcja Switch filtruje nazwę kursora i ustawia <xref:System.Windows.FrameworkElement.Cursor%2A> Właściwość o <xref:System.Windows.Controls.Border> nazwie *DisplayArea*.</span><span class="sxs-lookup"><span data-stu-id="d47b7-110">A switch statement filters on the cursor name and sets the <xref:System.Windows.FrameworkElement.Cursor%2A> property on the <xref:System.Windows.Controls.Border> which is named *DisplayArea*.</span></span>  
  
 <span data-ttu-id="d47b7-111">Jeśli dla zmiany kursora zostanie ustawiona wartość "Cała aplikacja", <xref:System.Windows.Input.Mouse.OverrideCursor%2A> Właściwość jest ustawiana na <xref:System.Windows.FrameworkElement.Cursor%2A> Właściwość <xref:System.Windows.Controls.Border> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="d47b7-111">If the cursor change is set to "Entire Application", the <xref:System.Windows.Input.Mouse.OverrideCursor%2A> property is set to the <xref:System.Windows.FrameworkElement.Cursor%2A> property of the <xref:System.Windows.Controls.Border> control.</span></span>  <span data-ttu-id="d47b7-112">Wymusza to zmianę kursora dla całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d47b7-112">This forces the cursor to change for the whole application.</span></span>  
  
 [!code-csharp[cursors#ChangeCursorsSample](~/samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml.cs#changecursorssample)]
 [!code-vb[cursors#ChangeCursorsSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/cursors/VisualBasic/Window1.xaml.vb#changecursorssample)]  
  
## <a name="see-also"></a><span data-ttu-id="d47b7-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d47b7-113">See also</span></span>

- [<span data-ttu-id="d47b7-114">Przegląd Dane wejściowe</span><span class="sxs-lookup"><span data-stu-id="d47b7-114">Input Overview</span></span>](input-overview.md)
