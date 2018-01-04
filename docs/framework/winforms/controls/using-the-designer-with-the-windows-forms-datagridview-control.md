---
title: "Używanie narzędzia Projektant z formantem DataGridView formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tables [Windows Forms]
- DataGridView control [Windows Forms], designer support
- formatting [Windows Forms]
ms.assetid: b66057a6-5983-4864-b4e7-8cbc88a7010c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9df10ecabc8f61c3ef984adb6466f195395fd181
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-designer-with-the-windows-forms-datagridview-control"></a><span data-ttu-id="24e7f-102">Używanie narzędzia Projektant z formantem DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="24e7f-102">Using the Designer with the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="24e7f-103">Program Visual Studio oferuje obsługę projektanta `DataGridView` formant, który umożliwia wykonywanie wielu zadań konfiguracyjnych bez konieczności pisania kodu.</span><span class="sxs-lookup"><span data-stu-id="24e7f-103">Visual Studio provides designer support for the `DataGridView` control that enables you to perform many setup tasks without writing code.</span></span> <span data-ttu-id="24e7f-104">Te zadania obejmują: powiązanie formantu ze źródłem danych, modyfikowania kolumn używana do wyświetlania danych i dostosowanie wyglądu i zachowania podstawowe formantu.</span><span class="sxs-lookup"><span data-stu-id="24e7f-104">These tasks include binding the control to a data source, modifying the columns used to display data, and adjusting the appearance and basic behavior of the control.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="24e7f-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="24e7f-105">In This Section</span></span>  
 [<span data-ttu-id="24e7f-106">Instrukcje: dodawanie i usuwanie kolumn do kontrolki DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="24e7f-106">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="24e7f-107">Informacje dotyczące używania **Dodawanie kolumn** i **Edytowanie kolumn** oknach dialogowych, aby wypełnić i modyfikować kolekcji kolumn.</span><span class="sxs-lookup"><span data-stu-id="24e7f-107">Describes how to use the **Add Columns** and **Edit Columns** dialog boxes to populate and modify the columns collection.</span></span>  
  
 [<span data-ttu-id="24e7f-108">Instrukcje: powiązywanie danych z kontrolką DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="24e7f-108">How to: Bind Data to the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/bind-data-to-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="24e7f-109">Informacje dotyczące używania **wybierz źródło danych** opcję w tagu formantu, aby połączyć się z danymi.</span><span class="sxs-lookup"><span data-stu-id="24e7f-109">Describes how to use the **Choose Data Source** option on the control's smart tag to connect to data.</span></span>  
  
 [<span data-ttu-id="24e7f-110">Instrukcje: zmienianie kolejności kolumn w kontrolce DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="24e7f-110">How to: Change the Order of Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/change-the-order-of-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="24e7f-111">Informacje dotyczące używania **Edytowanie kolumn** okno dialogowe, aby zmienić kolejność kolumn.</span><span class="sxs-lookup"><span data-stu-id="24e7f-111">Describes how to use the **Edit Columns** dialog box to rearrange columns.</span></span>  
  
 [<span data-ttu-id="24e7f-112">Instrukcje: zmienianie typu kontrolki DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="24e7f-112">How to: Change the Type of a Windows Forms DataGridView Column Using the Designer</span></span>](../../../../docs/framework/winforms/controls/change-the-type-of-a-wf-datagridview-column-using-the-designer.md)  
 <span data-ttu-id="24e7f-113">Informacje dotyczące używania **Edytowanie kolumn** okno dialogowe, aby zmienić typy kolumn.</span><span class="sxs-lookup"><span data-stu-id="24e7f-113">Describes how to use the **Edit Columns** dialog box to change column types.</span></span>  
  
 [<span data-ttu-id="24e7f-114">Instrukcje: włączanie zmiany układu kolumn w kontrolce DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="24e7f-114">How to: Enable Column Reordering in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/enable-column-reordering-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="24e7f-115">Informacje dotyczące używania tagów inteligentnych formantu, aby użytkownicy mogli zmieniać kolejności kolumn.</span><span class="sxs-lookup"><span data-stu-id="24e7f-115">Describes how to use the control's smart tag to enable users to rearrange columns.</span></span>  
  
 [<span data-ttu-id="24e7f-116">Instrukcje: blokowanie kolumn w kontrolce DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="24e7f-116">How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/freeze-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="24e7f-117">Informacje dotyczące używania **Edytowanie kolumn** okno dialogowe, aby uniemożliwić przewijanie określonych kolumn.</span><span class="sxs-lookup"><span data-stu-id="24e7f-117">Describes how to use the **Edit Columns** dialog box to prevent specific columns from scrolling.</span></span>  
  
 [<span data-ttu-id="24e7f-118">Instrukcje: ukrywanie kolumn w kontrolce DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="24e7f-118">How to: Hide Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/hide-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="24e7f-119">Informacje dotyczące używania **Edytowanie kolumn** okno dialogowe, aby ukryć określonych kolumn.</span><span class="sxs-lookup"><span data-stu-id="24e7f-119">Describes how to use the **Edit Columns** dialog box to hide specific columns.</span></span>  
  
 [<span data-ttu-id="24e7f-120">Instrukcje: określanie kolumn jako tylko do odczytu w kontrolce DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="24e7f-120">How to: Make Columns Read-Only in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/make-columns-read-only-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="24e7f-121">Informacje dotyczące używania **Edytowanie kolumn** okno dialogowe, aby uniemożliwić użytkownikom edytowanie wartości w określonych kolumnach.</span><span class="sxs-lookup"><span data-stu-id="24e7f-121">Describes how to use the **Edit Columns** dialog box to prevent users from editing values in specific columns.</span></span>  
  
 [<span data-ttu-id="24e7f-122">Instrukcje: zapobieganie dodawaniu i usuwaniu wierszy do kontrolki DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="24e7f-122">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="24e7f-123">Informacje dotyczące używania tagów inteligentnych formantu, aby uniemożliwić użytkownikom dodawanie lub usuwanie wierszy.</span><span class="sxs-lookup"><span data-stu-id="24e7f-123">Describes how to use the control's smart tag to prevent users from adding or deleting rows.</span></span>  
  
 [<span data-ttu-id="24e7f-124">Instrukcje: ustawianie przemiennych wierszy dla kontrolki DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="24e7f-124">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/set-alternating-row-styles-for-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="24e7f-125">Informacje dotyczące używania **konstruktora elementu CellStyle** okno dialogowe, aby utworzyć wygląd księgi przypominającej w formancie.</span><span class="sxs-lookup"><span data-stu-id="24e7f-125">Describes how to use the **CellStyle Builder** dialog box to create a ledger-like appearance in the control.</span></span>  
  
 [<span data-ttu-id="24e7f-126">Instrukcje: ustawianie domyślnych stylów komórek i formatów danych dla kontrolki DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="24e7f-126">How to: Set Default Cell Styles and Data Formats for the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/default-cell-styles-datagridview.md)  
 <span data-ttu-id="24e7f-127">Informacje dotyczące używania **konstruktora elementu CellStyle** formatuje okno dialogowe do ustawiania podstawowa wygląd i wyświetlania danych dla formantu.</span><span class="sxs-lookup"><span data-stu-id="24e7f-127">Describes how to use the **CellStyle Builder** dialog box to set up the basic appearance and data-display formats for the control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="24e7f-128">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="24e7f-128">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="24e7f-129">Zawiera dokumentacja referencyjna dla <xref:System.Windows.Forms.DataGridView> formantu.</span><span class="sxs-lookup"><span data-stu-id="24e7f-129">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24e7f-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="24e7f-130">See Also</span></span>  
 [<span data-ttu-id="24e7f-131">DataGridView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="24e7f-131">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
