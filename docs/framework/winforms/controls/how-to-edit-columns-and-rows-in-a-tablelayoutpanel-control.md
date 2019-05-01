---
title: 'Instrukcje: edytowanie rzędów i kolumn w kontrolce TableLayoutPanel'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor
helpviewer_keywords:
- columns [Windows Forms], editing
- TableLayoutPanel control [Windows Forms], editing
- rows [Windows Forms], editing
ms.assetid: c367ed43-40dc-49eb-9e0f-ba70e83dfec0
ms.openlocfilehash: 2149cac7fb15052c2602ef20a6684696730aae1b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941521"
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a><span data-ttu-id="b4360-102">Instrukcje: edytowanie rzędów i kolumn w kontrolce TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="b4360-102">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>
<span data-ttu-id="b4360-103">Można użyć edytora kolekcji <xref:System.Windows.Forms.TableLayoutPanel> kontrolę, wywoływana **Style kolumn i wierszy** okno dialogowe Edytuj wiersze i kolumny kontrolki.</span><span class="sxs-lookup"><span data-stu-id="b4360-103">You can use the collection editor of the <xref:System.Windows.Forms.TableLayoutPanel> control, called the **Column and Row Styles** dialog box, to edit the rows and columns of your controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b4360-104">Jeśli chcesz, aby formant ma obejmować wiele wierszy lub kolumn, ustaw `RowSpan` i `ColumnSpan` właściwości formantu.</span><span class="sxs-lookup"><span data-stu-id="b4360-104">If you want a control to span multiple rows or columns, set the `RowSpan` and `ColumnSpan` properties on the control.</span></span> <span data-ttu-id="b4360-105">Aby uzyskać więcej informacji, zobacz [instruktażu: Rozmieszczanie kontrolek na formularzach Windows Forms za pomocą TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span><span class="sxs-lookup"><span data-stu-id="b4360-105">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span>  
>   
>  <span data-ttu-id="b4360-106">Aby Wyrównaj formant w komórce lub jeśli chcesz rozciągnąć formant w komórce, należy użyć formantu <xref:System.Windows.Forms.Control.Anchor%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="b4360-106">If you want to align a control within a cell, or if you want a control to stretch within a cell, use the control's <xref:System.Windows.Forms.Control.Anchor%2A> property.</span></span> <span data-ttu-id="b4360-107">Aby uzyskać więcej informacji, zobacz [instruktażu: Rozmieszczanie kontrolek na formularzach Windows Forms za pomocą TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span><span class="sxs-lookup"><span data-stu-id="b4360-107">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span>  
>   
>  <span data-ttu-id="b4360-108">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="b4360-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="b4360-109">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="b4360-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="b4360-110">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="b4360-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-edit-rows-and-columns"></a><span data-ttu-id="b4360-111">Aby edytować wierszy i kolumn</span><span class="sxs-lookup"><span data-stu-id="b4360-111">To edit rows and columns</span></span>  
  
1. <span data-ttu-id="b4360-112">Przeciągnij <xref:System.Windows.Forms.TableLayoutPanel> z kontrolować **przybornika** do formularza.</span><span class="sxs-lookup"><span data-stu-id="b4360-112">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>  
  
2. <span data-ttu-id="b4360-113">Kliknij przycisk <xref:System.Windows.Forms.TableLayoutPanel> symbol tagu inteligentnego kontrolki (![symbol tagu inteligentnego](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) i wybierz **Edytuj wiersze i kolumny** otworzyć  **Style kolumn i wierszy** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="b4360-113">Click the <xref:System.Windows.Forms.TableLayoutPanel> control's smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) and select **Edit Rows and Columns** to open the **Column and Row Styles** dialog box.</span></span> <span data-ttu-id="b4360-114">Możesz również kliknąć prawym przyciskiem myszy na <xref:System.Windows.Forms.TableLayoutPanel> sterowania i wybierz **Edytuj wiersze i kolumny** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="b4360-114">You can also right click on the <xref:System.Windows.Forms.TableLayoutPanel> control and select **Edit Rows and Columns** from the shortcut menu.</span></span>  
  
3. <span data-ttu-id="b4360-115">Aby dodać lub usunąć kolumny, zaznacz **kolumn** z **typ elementu członkowskiego** pole listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="b4360-115">To add or remove columns, select **Columns** from the **Member type** drop-down list box.</span></span>  
  
4. <span data-ttu-id="b4360-116">Aby dodać lub usunąć wiersze, wybierz pozycję **wierszy** z **typ elementu członkowskiego** pole listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="b4360-116">To add or remove rows, select **Rows** from the **Member type** drop-down list box.</span></span>  
  
5. <span data-ttu-id="b4360-117">Kliknij przycisk **Dodaj** przycisk, aby dodać wiersz lub kolumnę do końca **elementu członkowskiego** listy.</span><span class="sxs-lookup"><span data-stu-id="b4360-117">Click the **Add** button to add a row or column to the end of the **Member** list.</span></span>  
  
6. <span data-ttu-id="b4360-118">Kliknij przycisk **Wstaw** przycisk, aby dodać wiersz lub kolumnę przed aktualnie wybranego elementu na liście.</span><span class="sxs-lookup"><span data-stu-id="b4360-118">Click the **Insert** button to add a row or column before the currently selected item in the list.</span></span>  
  
7. <span data-ttu-id="b4360-119">W przypadku dodawania wierszy lub kolumn, wybierz **typu rozmiaru** dla nowego wiersza lub kolumny.</span><span class="sxs-lookup"><span data-stu-id="b4360-119">If you are adding a row or column, select the **Size Type** for the new row or column.</span></span> <span data-ttu-id="b4360-120">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.SizeType>.</span><span class="sxs-lookup"><span data-stu-id="b4360-120">For more information, see <xref:System.Windows.Forms.SizeType>.</span></span>  
  
8. <span data-ttu-id="b4360-121">Aby usunąć wiersz lub kolumnę, kliknij **Usuń** przycisk, aby usunąć aktualnie wybranego elementu w **elementu członkowskiego** listy.</span><span class="sxs-lookup"><span data-stu-id="b4360-121">To remove a row or column, click the **Remove** button to delete the currently selected item in the **Member** list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4360-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b4360-122">See also</span></span>

- <xref:System.Windows.Forms.SizeType>
- [<span data-ttu-id="b4360-123">TableLayoutPanel, kontrolka</span><span class="sxs-lookup"><span data-stu-id="b4360-123">TableLayoutPanel Control</span></span>](tablelayoutpanel-control-windows-forms.md)
