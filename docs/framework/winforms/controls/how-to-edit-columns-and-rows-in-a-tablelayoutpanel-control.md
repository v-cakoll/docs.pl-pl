---
title: 'Porady: edytowanie rzędów i kolumn w formancie TableLayoutPanel'
description: Dowiedz się, w jaki sposób używać okna dialogowego kolumny i stylów wierszy do edytowania wierszy i kolumn kontrolek Windows Forms.
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor
helpviewer_keywords:
- columns [Windows Forms], editing
- TableLayoutPanel control [Windows Forms], editing
- rows [Windows Forms], editing
ms.assetid: c367ed43-40dc-49eb-9e0f-ba70e83dfec0
ms.openlocfilehash: cfd2ca4be5d5a2658a9a129d911f1dba9670ccfd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619354"
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a><span data-ttu-id="f0208-103">Porady: edytowanie rzędów i kolumn w formancie TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="f0208-103">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>

<span data-ttu-id="f0208-104"><xref:System.Windows.Forms.TableLayoutPanel>Aby edytować wiersze i kolumny kontrolek, można użyć edytora kolekcji, zwanego oknem dialogowym **kolumny i style wierszy** .</span><span class="sxs-lookup"><span data-stu-id="f0208-104">You can use the collection editor of the <xref:System.Windows.Forms.TableLayoutPanel> control, called the **Column and Row Styles** dialog box, to edit the rows and columns of your controls.</span></span>

> [!NOTE]
> <span data-ttu-id="f0208-105">Jeśli chcesz, aby kontrolka obejmowała wiele wierszy lub kolumn, ustaw `RowSpan` `ColumnSpan` właściwości i dla kontrolki.</span><span class="sxs-lookup"><span data-stu-id="f0208-105">If you want a control to span multiple rows or columns, set the `RowSpan` and `ColumnSpan` properties on the control.</span></span> <span data-ttu-id="f0208-106">Aby uzyskać więcej informacji, zobacz [Przewodnik: rozmieszczanie formantów na Windows Forms przy użyciu TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span><span class="sxs-lookup"><span data-stu-id="f0208-106">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span>
>
> <span data-ttu-id="f0208-107">Jeśli chcesz wyrównać formant w komórce lub chcesz, aby formant rozciągał się w komórce, użyj właściwości kontrolki <xref:System.Windows.Forms.Control.Anchor%2A> .</span><span class="sxs-lookup"><span data-stu-id="f0208-107">If you want to align a control within a cell, or if you want a control to stretch within a cell, use the control's <xref:System.Windows.Forms.Control.Anchor%2A> property.</span></span> <span data-ttu-id="f0208-108">Aby uzyskać więcej informacji, zobacz [Przewodnik: rozmieszczanie formantów na Windows Forms przy użyciu TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span><span class="sxs-lookup"><span data-stu-id="f0208-108">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span>

## <a name="to-edit-rows-and-columns"></a><span data-ttu-id="f0208-109">Aby edytować wiersze i kolumny</span><span class="sxs-lookup"><span data-stu-id="f0208-109">To edit rows and columns</span></span>

1. <span data-ttu-id="f0208-110">Przeciągnij <xref:System.Windows.Forms.TableLayoutPanel> kontrolkę z **przybornika** do formularza.</span><span class="sxs-lookup"><span data-stu-id="f0208-110">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>

2. <span data-ttu-id="f0208-111">Kliknij <xref:System.Windows.Forms.TableLayoutPanel> symbol akcji projektanta kontrolki ( ![ Mała czarna strzałka ](./media/designer-actions-glyph.gif) ) i wybierz opcję **Edytuj wiersze i kolumny** , aby otworzyć okno dialogowe **Style kolumn i wierszy** .</span><span class="sxs-lookup"><span data-stu-id="f0208-111">Click the <xref:System.Windows.Forms.TableLayoutPanel> control's designer actions glyph (![Small black arrow](./media/designer-actions-glyph.gif)) and select **Edit Rows and Columns** to open the **Column and Row Styles** dialog box.</span></span> <span data-ttu-id="f0208-112">Możesz również kliknąć prawym przyciskiem myszy <xref:System.Windows.Forms.TableLayoutPanel> formant i wybrać polecenie **Edytuj wiersze i kolumny** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="f0208-112">You can also right click on the <xref:System.Windows.Forms.TableLayoutPanel> control and select **Edit Rows and Columns** from the shortcut menu.</span></span>

3. <span data-ttu-id="f0208-113">Aby dodać lub usunąć kolumny, wybierz pozycję **kolumny** w polu listy rozwijanej **Typ elementu członkowskiego** .</span><span class="sxs-lookup"><span data-stu-id="f0208-113">To add or remove columns, select **Columns** from the **Member type** drop-down list box.</span></span>

4. <span data-ttu-id="f0208-114">Aby dodać lub usunąć wiersze, zaznacz opcję **wiersze** w polu listy rozwijanej **Typ elementu członkowskiego** .</span><span class="sxs-lookup"><span data-stu-id="f0208-114">To add or remove rows, select **Rows** from the **Member type** drop-down list box.</span></span>

5. <span data-ttu-id="f0208-115">Kliknij przycisk **Dodaj** , aby dodać wiersz lub kolumnę do końca listy **elementów członkowskich** .</span><span class="sxs-lookup"><span data-stu-id="f0208-115">Click the **Add** button to add a row or column to the end of the **Member** list.</span></span>

6. <span data-ttu-id="f0208-116">Kliknij przycisk **Wstaw** , aby dodać wiersz lub kolumnę przed aktualnie wybranym elementem na liście.</span><span class="sxs-lookup"><span data-stu-id="f0208-116">Click the **Insert** button to add a row or column before the currently selected item in the list.</span></span>

7. <span data-ttu-id="f0208-117">Jeśli dodajesz wiersz lub kolumnę, wybierz **Typ rozmiaru** dla nowego wiersza lub kolumny.</span><span class="sxs-lookup"><span data-stu-id="f0208-117">If you are adding a row or column, select the **Size Type** for the new row or column.</span></span> <span data-ttu-id="f0208-118">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.SizeType>.</span><span class="sxs-lookup"><span data-stu-id="f0208-118">For more information, see <xref:System.Windows.Forms.SizeType>.</span></span>

8. <span data-ttu-id="f0208-119">Aby usunąć wiersz lub kolumnę, kliknij przycisk **Usuń** , aby usunąć aktualnie wybrany element z listy **elementów członkowskich** .</span><span class="sxs-lookup"><span data-stu-id="f0208-119">To remove a row or column, click the **Remove** button to delete the currently selected item in the **Member** list.</span></span>

## <a name="see-also"></a><span data-ttu-id="f0208-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f0208-120">See also</span></span>

- <xref:System.Windows.Forms.SizeType>
- [<span data-ttu-id="f0208-121">TableLayoutPanel — formant</span><span class="sxs-lookup"><span data-stu-id="f0208-121">TableLayoutPanel Control</span></span>](tablelayoutpanel-control-windows-forms.md)
