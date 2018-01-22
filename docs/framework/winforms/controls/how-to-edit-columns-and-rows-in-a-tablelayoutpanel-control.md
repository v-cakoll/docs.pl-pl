---
title: "Porady: edytowanie rzędów i kolumn w formancie TableLayoutPanel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: net.ComponentModel.StyleCollectionEditor
helpviewer_keywords:
- columns [Windows Forms], editing
- TableLayoutPanel control [Windows Forms], editing
- rows [Windows Forms], editing
ms.assetid: c367ed43-40dc-49eb-9e0f-ba70e83dfec0
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bf54a02a409bead598a4e98315d5709e55677f3b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a><span data-ttu-id="c1191-102">Porady: edytowanie rzędów i kolumn w formancie TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="c1191-102">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>
<span data-ttu-id="c1191-103">Za pomocą edytora kolekcji z <xref:System.Windows.Forms.TableLayoutPanel> formantu o nazwie **Style kolumn i wierszy** okno dialogowe, aby edytować wierszy i kolumn dla Twoich kontrolek.</span><span class="sxs-lookup"><span data-stu-id="c1191-103">You can use the collection editor of the <xref:System.Windows.Forms.TableLayoutPanel> control, called the **Column and Row Styles** dialog box, to edit the rows and columns of your controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c1191-104">Jeśli chcesz, aby formant ma obejmować wiele wierszy lub kolumn, ustaw `RowSpan` i `ColumnSpan` właściwości formantu.</span><span class="sxs-lookup"><span data-stu-id="c1191-104">If you want a control to span multiple rows or columns, set the `RowSpan` and `ColumnSpan` properties on the control.</span></span> <span data-ttu-id="c1191-105">Aby uzyskać więcej informacji, zobacz [wskazówki: rozmieszczanie formantów w Windows Forms za pomocą TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span><span class="sxs-lookup"><span data-stu-id="c1191-105">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span>  
>   
>  <span data-ttu-id="c1191-106">Jeśli chcesz wyrównać formant w komórce lub jeśli chcesz rozciągnąć formant w komórce, użyj formantu <xref:System.Windows.Forms.Control.Anchor%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="c1191-106">If you want to align a control within a cell, or if you want a control to stretch within a cell, use the control's <xref:System.Windows.Forms.Control.Anchor%2A> property.</span></span> <span data-ttu-id="c1191-107">Aby uzyskać więcej informacji, zobacz [wskazówki: rozmieszczanie formantów w Windows Forms za pomocą TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span><span class="sxs-lookup"><span data-stu-id="c1191-107">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span>  
>   
>  <span data-ttu-id="c1191-108">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="c1191-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="c1191-109">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="c1191-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="c1191-110">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="c1191-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-edit-rows-and-columns"></a><span data-ttu-id="c1191-111">Aby edytować wierszy i kolumn</span><span class="sxs-lookup"><span data-stu-id="c1191-111">To edit rows and columns</span></span>  
  
1.  <span data-ttu-id="c1191-112">Przeciągnij <xref:System.Windows.Forms.TableLayoutPanel> kontrolować z **przybornika** na formularzu.</span><span class="sxs-lookup"><span data-stu-id="c1191-112">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>  
  
2.  <span data-ttu-id="c1191-113">Kliknij przycisk <xref:System.Windows.Forms.TableLayoutPanel> kontrolki symbolu tagu (![symbol tagu inteligentnego](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) i wybierz **Edytuj wiersze i kolumny** otworzyć  **Style kolumn i wierszy** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="c1191-113">Click the <xref:System.Windows.Forms.TableLayoutPanel> control's smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) and select **Edit Rows and Columns** to open the **Column and Row Styles** dialog box.</span></span> <span data-ttu-id="c1191-114">Możesz również kliknąć prawym przyciskiem myszy na <xref:System.Windows.Forms.TableLayoutPanel> sterowania i wybierz **Edytuj wiersze i kolumny** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="c1191-114">You can also right click on the <xref:System.Windows.Forms.TableLayoutPanel> control and select **Edit Rows and Columns** from the shortcut menu.</span></span>  
  
3.  <span data-ttu-id="c1191-115">Aby dodać lub usunąć kolumny, zaznacz **kolumn** z **typ elementu członkowskiego** pole listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="c1191-115">To add or remove columns, select **Columns** from the **Member type** drop-down list box.</span></span>  
  
4.  <span data-ttu-id="c1191-116">Aby dodać lub usunąć wiersze, wybierz **wierszy** z **typ elementu członkowskiego** pole listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="c1191-116">To add or remove rows, select **Rows** from the **Member type** drop-down list box.</span></span>  
  
5.  <span data-ttu-id="c1191-117">Kliknij przycisk **Dodaj** przycisk, aby dodać wiersz lub kolumnę do końca **elementu członkowskiego** listy.</span><span class="sxs-lookup"><span data-stu-id="c1191-117">Click the **Add** button to add a row or column to the end of the **Member** list.</span></span>  
  
6.  <span data-ttu-id="c1191-118">Kliknij przycisk **Wstaw** przycisk, aby dodać wiersz lub kolumnę przed aktualnie wybrany element na liście.</span><span class="sxs-lookup"><span data-stu-id="c1191-118">Click the **Insert** button to add a row or column before the currently selected item in the list.</span></span>  
  
7.  <span data-ttu-id="c1191-119">Jeśli dodajesz wiersz lub kolumnę, wybierz **typu rozmiaru** nowy wiersz lub kolumnę.</span><span class="sxs-lookup"><span data-stu-id="c1191-119">If you are adding a row or column, select the **Size Type** for the new row or column.</span></span> <span data-ttu-id="c1191-120">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.SizeType>.</span><span class="sxs-lookup"><span data-stu-id="c1191-120">For more information, see <xref:System.Windows.Forms.SizeType>.</span></span>  
  
8.  <span data-ttu-id="c1191-121">Aby usunąć wiersz lub kolumnę, kliknij przycisk **Usuń** przycisk, aby usunąć element aktualnie zaznaczony w **elementu członkowskiego** listy.</span><span class="sxs-lookup"><span data-stu-id="c1191-121">To remove a row or column, click the **Remove** button to delete the currently selected item in the **Member** list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1191-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c1191-122">See Also</span></span>  
 <xref:System.Windows.Forms.SizeType>  
 [<span data-ttu-id="c1191-123">TableLayoutPanel, kontrolka</span><span class="sxs-lookup"><span data-stu-id="c1191-123">TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
