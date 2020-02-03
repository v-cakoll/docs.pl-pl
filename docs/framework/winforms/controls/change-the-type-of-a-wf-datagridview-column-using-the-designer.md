---
title: Zmienianie typu kolumny DataGridView przy użyciu narzędzia Projektant
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], types
- DataGridView control [Windows Forms], changing column type
- data [Windows Forms], displaying
ms.assetid: 7f994d45-600d-4190-a187-35803214b40c
ms.openlocfilehash: 976f257d38dc7be5c904e63da47c61486bd3301c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737130"
---
# <a name="how-to-change-the-type-of-a-windows-forms-datagridview-column-using-the-designer"></a><span data-ttu-id="657a3-102">Porady: zmienianie typu formantu DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="657a3-102">How to: Change the Type of a Windows Forms DataGridView Column Using the Designer</span></span>
<span data-ttu-id="657a3-103">Czasami trzeba zmienić typ kolumny, która została już dodana do kontrolki <xref:System.Windows.Forms.DataGridView> Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="657a3-103">Sometimes you will want to change the type of a column that has already been added to a Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="657a3-104">Na przykład możesz chcieć zmodyfikować typy niektórych kolumn, które są generowane automatycznie podczas wiązania kontrolki ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="657a3-104">For example, you may want to modify the types of some of the columns that are generated automatically when you bind the control to a data source.</span></span> <span data-ttu-id="657a3-105">Jest to przydatne, gdy wyświetlana tabela zawiera kolumny zawierające klucze obce do wierszy w powiązanej tabeli.</span><span class="sxs-lookup"><span data-stu-id="657a3-105">This is useful when the table you display has columns containing foreign keys to rows in a related table.</span></span> <span data-ttu-id="657a3-106">W takim przypadku można zastąpić kolumny pól tekstowych, które wyświetlają te klucze obce z kolumnami pól kombi, które wyświetlają bardziej zrozumiałe wartości z powiązanej tabeli.</span><span class="sxs-lookup"><span data-stu-id="657a3-106">In this case, you may want to replace the text box columns that display these foreign keys with combo box columns that display more meaningful values from the related table.</span></span>

 <span data-ttu-id="657a3-107">Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym formant <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="657a3-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="657a3-108">Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Create a Windows Forms Project Application](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [How to: Add controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="657a3-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

### <a name="to-change-the-type-of-a-column-using-the-designer"></a><span data-ttu-id="657a3-109">Aby zmienić typ kolumny przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="657a3-109">To change the type of a column using the designer</span></span>

1. <span data-ttu-id="657a3-110">Kliknij symbol taga inteligentnego (![symbol tagu inteligentnego](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) w prawym górnym rogu kontrolki <xref:System.Windows.Forms.DataGridView>, a następnie wybierz pozycję **Edytuj kolumny**.</span><span class="sxs-lookup"><span data-stu-id="657a3-110">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>

2. <span data-ttu-id="657a3-111">Wybierz kolumnę z listy **wybrane kolumny** .</span><span class="sxs-lookup"><span data-stu-id="657a3-111">Select a column from the **Selected Columns** list.</span></span>

3. <span data-ttu-id="657a3-112">W siatce **Właściwości kolumny** ustaw właściwość `ColumnType` na nowy typ kolumny.</span><span class="sxs-lookup"><span data-stu-id="657a3-112">In the **Column Properties** grid, set the `ColumnType` property to the new column type.</span></span>

    > [!NOTE]
    > <span data-ttu-id="657a3-113">Właściwość `ColumnType` jest właściwością czasu projektowania, która wskazuje klasę reprezentującą typ kolumny.</span><span class="sxs-lookup"><span data-stu-id="657a3-113">The `ColumnType` property is a design-time-only property that indicates the class representing the column type.</span></span> <span data-ttu-id="657a3-114">Nie jest to rzeczywista Właściwość zdefiniowana w klasie Column.</span><span class="sxs-lookup"><span data-stu-id="657a3-114">It is not an actual property defined in a column class.</span></span>

## <a name="see-also"></a><span data-ttu-id="657a3-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="657a3-115">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [<span data-ttu-id="657a3-116">Instrukcje: Tworzenie projektu aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="657a3-116">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="657a3-117">Instrukcje: dodawanie kontrolek do formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="657a3-117">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
