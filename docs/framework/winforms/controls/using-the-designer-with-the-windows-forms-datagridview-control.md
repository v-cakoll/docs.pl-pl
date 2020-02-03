---
title: Używanie projektanta z kontrolką DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- tables [Windows Forms]
- DataGridView control [Windows Forms], designer support
- formatting [Windows Forms]
ms.assetid: b66057a6-5983-4864-b4e7-8cbc88a7010c
ms.openlocfilehash: 50e8bddb97c2dfb84cebdbb2ca4d42a6c5743304
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728356"
---
# <a name="using-the-designer-with-the-windows-forms-datagridview-control"></a><span data-ttu-id="a23c8-102">Używanie narzędzia Projektant z formantem DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a23c8-102">Using the Designer with the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="a23c8-103">Program Visual Studio zapewnia obsługę projektanta dla kontrolki `DataGridView`, która umożliwia wykonywanie wielu zadań konfiguracyjnych bez pisania kodu.</span><span class="sxs-lookup"><span data-stu-id="a23c8-103">Visual Studio provides designer support for the `DataGridView` control that enables you to perform many setup tasks without writing code.</span></span> <span data-ttu-id="a23c8-104">Te zadania obejmują powiązanie kontrolki ze źródłem danych, Modyfikowanie kolumn używanych do wyświetlania danych oraz Dostosowywanie wyglądu i podstawowe zachowanie kontrolki.</span><span class="sxs-lookup"><span data-stu-id="a23c8-104">These tasks include binding the control to a data source, modifying the columns used to display data, and adjusting the appearance and basic behavior of the control.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a23c8-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="a23c8-105">In This Section</span></span>  
 [<span data-ttu-id="a23c8-106">Instrukcje: dodawanie i usuwanie kolumn do kontrolki DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="a23c8-106">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](add-and-remove-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="a23c8-107">Opisuje sposób użycia okien dialogowych **Dodawanie kolumn** i **Edytowanie kolumn** do wypełniania i modyfikowania kolekcji kolumn.</span><span class="sxs-lookup"><span data-stu-id="a23c8-107">Describes how to use the **Add Columns** and **Edit Columns** dialog boxes to populate and modify the columns collection.</span></span>  
  
 [<span data-ttu-id="a23c8-108">Instrukcje: powiązywanie danych z kontrolką DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="a23c8-108">How to: Bind Data to the Windows Forms DataGridView Control Using the Designer</span></span>](bind-data-to-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="a23c8-109">Opisuje sposób używania opcji **Wybierz źródło danych** w tagu inteligentnym kontrolki do łączenia się z danymi.</span><span class="sxs-lookup"><span data-stu-id="a23c8-109">Describes how to use the **Choose Data Source** option on the control's smart tag to connect to data.</span></span>  
  
 [<span data-ttu-id="a23c8-110">Instrukcje: zmienianie kolejności kolumn w kontrolce DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="a23c8-110">How to: Change the Order of Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](change-the-order-of-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="a23c8-111">Opisuje sposób korzystania z okna dialogowego **Edytowanie kolumn** w celu zmiany układu kolumn.</span><span class="sxs-lookup"><span data-stu-id="a23c8-111">Describes how to use the **Edit Columns** dialog box to rearrange columns.</span></span>  
  
 [<span data-ttu-id="a23c8-112">Instrukcje: zmienianie typu kontrolki DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="a23c8-112">How to: Change the Type of a Windows Forms DataGridView Column Using the Designer</span></span>](change-the-type-of-a-wf-datagridview-column-using-the-designer.md)  
 <span data-ttu-id="a23c8-113">Opisuje sposób korzystania z okna dialogowego **Edytowanie kolumn** w celu zmiany typów kolumn.</span><span class="sxs-lookup"><span data-stu-id="a23c8-113">Describes how to use the **Edit Columns** dialog box to change column types.</span></span>  
  
 [<span data-ttu-id="a23c8-114">Instrukcje: włączanie zmiany układu kolumn w kontrolce DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="a23c8-114">How to: Enable Column Reordering in the Windows Forms DataGridView Control Using the Designer</span></span>](enable-column-reordering-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="a23c8-115">Opisuje, jak używać tagu inteligentnego kontrolki, aby umożliwić użytkownikom zmianę rozmieszczenia kolumn.</span><span class="sxs-lookup"><span data-stu-id="a23c8-115">Describes how to use the control's smart tag to enable users to rearrange columns.</span></span>  
  
 [<span data-ttu-id="a23c8-116">Instrukcje: blokowanie kolumn w kontrolce DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="a23c8-116">How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](freeze-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="a23c8-117">Opisuje sposób korzystania z okna dialogowego **Edytowanie kolumn** , aby uniemożliwić przewijanie określonych kolumn.</span><span class="sxs-lookup"><span data-stu-id="a23c8-117">Describes how to use the **Edit Columns** dialog box to prevent specific columns from scrolling.</span></span>  
  
 [<span data-ttu-id="a23c8-118">Instrukcje: ukrywanie kolumn w kontrolce DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="a23c8-118">How to: Hide Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](hide-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="a23c8-119">Opisuje sposób korzystania z okna dialogowego **Edytowanie kolumn** w celu ukrycia określonych kolumn.</span><span class="sxs-lookup"><span data-stu-id="a23c8-119">Describes how to use the **Edit Columns** dialog box to hide specific columns.</span></span>  
  
 [<span data-ttu-id="a23c8-120">Instrukcje: określanie kolumn jako tylko do odczytu w kontrolce DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="a23c8-120">How to: Make Columns Read-Only in the Windows Forms DataGridView Control Using the Designer</span></span>](make-columns-read-only-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="a23c8-121">Opisuje sposób korzystania z okna dialogowego **Edytowanie kolumn** , aby uniemożliwić użytkownikom edytowanie wartości w określonych kolumnach.</span><span class="sxs-lookup"><span data-stu-id="a23c8-121">Describes how to use the **Edit Columns** dialog box to prevent users from editing values in specific columns.</span></span>  
  
 [<span data-ttu-id="a23c8-122">Instrukcje: zapobieganie dodawaniu i usuwaniu wierszy do kontrolki DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="a23c8-122">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer</span></span>](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="a23c8-123">Opisuje, jak używać tagu inteligentnego kontrolki, aby uniemożliwić użytkownikom dodawanie lub usuwanie wierszy.</span><span class="sxs-lookup"><span data-stu-id="a23c8-123">Describes how to use the control's smart tag to prevent users from adding or deleting rows.</span></span>  
  
 [<span data-ttu-id="a23c8-124">Instrukcje: ustawianie przemiennych wierszy dla kontrolki DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="a23c8-124">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control Using the Designer</span></span>](set-alternating-row-styles-for-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="a23c8-125">Opisuje, jak używać okna dialogowego **Konstruktor komórek** do tworzenia wyglądu przypominającego finanse w formancie.</span><span class="sxs-lookup"><span data-stu-id="a23c8-125">Describes how to use the **CellStyle Builder** dialog box to create a ledger-like appearance in the control.</span></span>  
  
 [<span data-ttu-id="a23c8-126">Instrukcje: ustawianie domyślnych stylów komórek i formatów danych dla kontrolki DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="a23c8-126">How to: Set Default Cell Styles and Data Formats for the Windows Forms DataGridView Control Using the Designer</span></span>](default-cell-styles-datagridview.md)  
 <span data-ttu-id="a23c8-127">Opisuje sposób użycia okna dialogowego **Konstruktor komórek** w celu skonfigurowania podstawowych formatów wyglądu i wyświetlania danych dla kontrolki.</span><span class="sxs-lookup"><span data-stu-id="a23c8-127">Describes how to use the **CellStyle Builder** dialog box to set up the basic appearance and data-display formats for the control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a23c8-128">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="a23c8-128">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="a23c8-129">Zawiera dokumentację referencyjną dla kontrolki <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="a23c8-129">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a23c8-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a23c8-130">See also</span></span>

- [<span data-ttu-id="a23c8-131">DataGridView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="a23c8-131">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
