---
title: 'Porady: edytowanie rzędów i kolumn w formancie TableLayoutPanel'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor
helpviewer_keywords:
- columns [Windows Forms], editing
- TableLayoutPanel control [Windows Forms], editing
- rows [Windows Forms], editing
ms.assetid: c367ed43-40dc-49eb-9e0f-ba70e83dfec0
ms.openlocfilehash: 4473b20eea57088104a51eb1b6c080219223d214
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628647"
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a><span data-ttu-id="c9261-102">Porady: edytowanie rzędów i kolumn w formancie TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="c9261-102">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>

<span data-ttu-id="c9261-103">Aby edytować wiersze i kolumny kontrolek, można użyć edytora kolekcji w kontrolce <xref:System.Windows.Forms.TableLayoutPanel>, nazywanej **kolumną i stylem wierszy** .</span><span class="sxs-lookup"><span data-stu-id="c9261-103">You can use the collection editor of the <xref:System.Windows.Forms.TableLayoutPanel> control, called the **Column and Row Styles** dialog box, to edit the rows and columns of your controls.</span></span>

> [!NOTE]
> <span data-ttu-id="c9261-104">Jeśli chcesz, aby kontrolka obejmowała wiele wierszy lub kolumn, ustaw `RowSpan` i `ColumnSpan` właściwości formantu.</span><span class="sxs-lookup"><span data-stu-id="c9261-104">If you want a control to span multiple rows or columns, set the `RowSpan` and `ColumnSpan` properties on the control.</span></span> <span data-ttu-id="c9261-105">Aby uzyskać więcej informacji, zobacz [Przewodnik: rozmieszczanie formantów na Windows Forms przy użyciu TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span><span class="sxs-lookup"><span data-stu-id="c9261-105">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span>
>
> <span data-ttu-id="c9261-106">Jeśli chcesz wyrównać formant w komórce lub chcesz, aby formant rozciągał się w komórce, użyj właściwości <xref:System.Windows.Forms.Control.Anchor%2A> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="c9261-106">If you want to align a control within a cell, or if you want a control to stretch within a cell, use the control's <xref:System.Windows.Forms.Control.Anchor%2A> property.</span></span> <span data-ttu-id="c9261-107">Aby uzyskać więcej informacji, zobacz [Przewodnik: rozmieszczanie formantów na Windows Forms przy użyciu TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span><span class="sxs-lookup"><span data-stu-id="c9261-107">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span>

## <a name="to-edit-rows-and-columns"></a><span data-ttu-id="c9261-108">Aby edytować wiersze i kolumny</span><span class="sxs-lookup"><span data-stu-id="c9261-108">To edit rows and columns</span></span>

1. <span data-ttu-id="c9261-109">Przeciągnij kontrolkę <xref:System.Windows.Forms.TableLayoutPanel> z **przybornika** na formularz.</span><span class="sxs-lookup"><span data-stu-id="c9261-109">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>

2. <span data-ttu-id="c9261-110">Kliknij symbol akcji projektanta <xref:System.Windows.Forms.TableLayoutPanel> kontrolki (![małą czarną strzałkę](./media/designer-actions-glyph.gif)) i wybierz opcję **Edytuj wiersze i kolumny** , aby otworzyć okno dialogowe **Style kolumn i wierszy** .</span><span class="sxs-lookup"><span data-stu-id="c9261-110">Click the <xref:System.Windows.Forms.TableLayoutPanel> control's designer actions glyph (![Small black arrow](./media/designer-actions-glyph.gif)) and select **Edit Rows and Columns** to open the **Column and Row Styles** dialog box.</span></span> <span data-ttu-id="c9261-111">Możesz również kliknąć prawym przyciskiem myszy formant <xref:System.Windows.Forms.TableLayoutPanel> i wybrać polecenie **Edytuj wiersze i kolumny** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="c9261-111">You can also right click on the <xref:System.Windows.Forms.TableLayoutPanel> control and select **Edit Rows and Columns** from the shortcut menu.</span></span>

3. <span data-ttu-id="c9261-112">Aby dodać lub usunąć kolumny, wybierz pozycję **kolumny** w polu listy rozwijanej **Typ elementu członkowskiego** .</span><span class="sxs-lookup"><span data-stu-id="c9261-112">To add or remove columns, select **Columns** from the **Member type** drop-down list box.</span></span>

4. <span data-ttu-id="c9261-113">Aby dodać lub usunąć wiersze, zaznacz opcję **wiersze** w polu listy rozwijanej **Typ elementu członkowskiego** .</span><span class="sxs-lookup"><span data-stu-id="c9261-113">To add or remove rows, select **Rows** from the **Member type** drop-down list box.</span></span>

5. <span data-ttu-id="c9261-114">Kliknij przycisk **Dodaj** , aby dodać wiersz lub kolumnę do końca listy **elementów członkowskich** .</span><span class="sxs-lookup"><span data-stu-id="c9261-114">Click the **Add** button to add a row or column to the end of the **Member** list.</span></span>

6. <span data-ttu-id="c9261-115">Kliknij przycisk **Wstaw** , aby dodać wiersz lub kolumnę przed aktualnie wybranym elementem na liście.</span><span class="sxs-lookup"><span data-stu-id="c9261-115">Click the **Insert** button to add a row or column before the currently selected item in the list.</span></span>

7. <span data-ttu-id="c9261-116">Jeśli dodajesz wiersz lub kolumnę, wybierz **Typ rozmiaru** dla nowego wiersza lub kolumny.</span><span class="sxs-lookup"><span data-stu-id="c9261-116">If you are adding a row or column, select the **Size Type** for the new row or column.</span></span> <span data-ttu-id="c9261-117">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.SizeType>.</span><span class="sxs-lookup"><span data-stu-id="c9261-117">For more information, see <xref:System.Windows.Forms.SizeType>.</span></span>

8. <span data-ttu-id="c9261-118">Aby usunąć wiersz lub kolumnę, kliknij przycisk **Usuń** , aby usunąć aktualnie wybrany element z listy **elementów członkowskich** .</span><span class="sxs-lookup"><span data-stu-id="c9261-118">To remove a row or column, click the **Remove** button to delete the currently selected item in the **Member** list.</span></span>

## <a name="see-also"></a><span data-ttu-id="c9261-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c9261-119">See also</span></span>

- <xref:System.Windows.Forms.SizeType>
- [<span data-ttu-id="c9261-120">TableLayoutPanel, kontrolka</span><span class="sxs-lookup"><span data-stu-id="c9261-120">TableLayoutPanel Control</span></span>](tablelayoutpanel-control-windows-forms.md)
