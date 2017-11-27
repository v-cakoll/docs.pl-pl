---
title: "Porady: zmienianie kolejności kolumn w formancie DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- columns [Windows Forms], order of
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- data [Windows Forms], displaying
ms.assetid: 7fe52a98-75d6-448c-97a5-65ca2c568c1a
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dd0e0542e46a17cffef629bc9b916d7b5929e878
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="b828c-102">Porady: zmienianie kolejności kolumn w formancie DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="b828c-102">How to: Change the Order of Columns in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="b828c-103">Po powiązaniu formularzy systemu Windows <xref:System.Windows.Forms.DataGridView> formantu ze źródłem danych, kolejność wyświetlania kolumn automatycznie generowanych zależy od źródła danych.</span><span class="sxs-lookup"><span data-stu-id="b828c-103">When you bind a Windows Forms <xref:System.Windows.Forms.DataGridView> control to a data source, the display order of the automatically generated columns is dictated by the data source.</span></span> <span data-ttu-id="b828c-104">Jeśli nie chcesz tego zamówienia, można zmienić kolejność kolumn za pomocą projektanta.</span><span class="sxs-lookup"><span data-stu-id="b828c-104">If this order is not what you prefer, you can change the order of the columns using the designer.</span></span> <span data-ttu-id="b828c-105">Można również dodawanie niepowiązanych kolumn do formantu i zmienianie ich kolejności wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="b828c-105">You may also want to add unbound columns to the control and change their display order.</span></span> <span data-ttu-id="b828c-106">Aby dowiedzieć się, jak programowo zmienić kolejność kolumn, zobacz [porady: Zmienianie kolejności kolumn w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="b828c-106">For information about how to change the column order programmatically, see [How to: Change the Order of Columns in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="b828c-107">Poniższa procedura wymaga **aplikacji systemu Windows** projekt zawierający formularz <xref:System.Windows.Forms.DataGridView> formantu.</span><span class="sxs-lookup"><span data-stu-id="b828c-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="b828c-108">Informacje o konfigurowaniu tych projektu, zobacz [jak: utworzyć projekt aplikacji systemu Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) i [porady: dodawanie formantów do formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="b828c-108">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b828c-109">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="b828c-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="b828c-110">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="b828c-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="b828c-111">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)</span><span class="sxs-lookup"><span data-stu-id="b828c-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)</span></span>  
  
### <a name="to-change-the-column-order-using-the-designer"></a><span data-ttu-id="b828c-112">Aby zmienić kolejność kolumn przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="b828c-112">To change the column order using the designer</span></span>  
  
1.  <span data-ttu-id="b828c-113">Kliknij symbol tagu inteligentnego (![symbol tagu inteligentnego](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) w prawym górnym rogu <xref:System.Windows.Forms.DataGridView> kontroli, a następnie wybierz **Edytowanie kolumn**.</span><span class="sxs-lookup"><span data-stu-id="b828c-113">Click the smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>  
  
2.  <span data-ttu-id="b828c-114">Wybierz kolumny z **wybrane kolumny** listy.</span><span class="sxs-lookup"><span data-stu-id="b828c-114">Select a column from the **Selected Columns** list.</span></span>  
  
3.  <span data-ttu-id="b828c-115">Kliknij w górę lub w dół strzałkę po prawej stronie **wybranych kolumn** listy aż do wybranej kolumny w odpowiednie miejsce.</span><span class="sxs-lookup"><span data-stu-id="b828c-115">Click the up or down arrow to the right of the **Selected Columns** list until the selected column is in the position you want.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b828c-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b828c-116">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="b828c-117">Porady: Dodawanie i usuwanie kolumn w oknach formularzy formantu DataGridView, przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="b828c-117">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)  
 [<span data-ttu-id="b828c-118">Porady: Tworzenie projektu aplikacji systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b828c-118">How to: Create a Windows Application Project</span></span>](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [<span data-ttu-id="b828c-119">Porady: dodawanie formantów do formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b828c-119">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
