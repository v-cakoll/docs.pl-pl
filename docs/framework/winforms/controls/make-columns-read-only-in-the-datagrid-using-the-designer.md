---
title: 'Instrukcje: Nadawanie kolumnom w trybie tylko do odczytu w formancie DataGridView formularzy Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- DataGridView control [Windows Forms], read-only columns
- data [Windows Forms], displaying
- columns [Windows Forms], read-only
ms.assetid: b4ef7a75-ab33-4ee3-b2cf-201530e454e9
ms.openlocfilehash: 0219f0cf50d9cce630dc44a37dd3c16d26874012
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57718561"
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="3e613-102">Instrukcje: Nadawanie kolumnom w trybie tylko do odczytu w formancie DataGridView formularzy Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="3e613-102">How to: Make Columns Read-Only in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="3e613-103">Domyślnie użytkownicy mogą modyfikować tekstu i danych liczbowych są wyświetlane w formularzach Windows <xref:System.Windows.Forms.DataGridView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="3e613-103">By default, users can modify text and numerical data displayed in the Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="3e613-104">Jeśli chcesz wyświetlić dane, która nie jest przeznaczona do modyfikacji, należy kolumn, które zawierają dane tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="3e613-104">If you want to display data that is not meant for modification, you must make the columns that contain the data read-only.</span></span> <span data-ttu-id="3e613-105">Aby dowiedzieć się, jak sprawić, że formant całkowicie tylko do odczytu, zobacz [jak: Zapobieganie dodawaniu i usuwaniu rzędów Windows do formantu DataGridView przy użyciu narzędzia Projektant formularzy](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="3e613-105">For information about how to make the control entirely read-only, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).</span></span>  
  
 <span data-ttu-id="3e613-106">Poniższa procedura wymaga **aplikacji Windows** projektu za pomocą zawierający formularz <xref:System.Windows.Forms.DataGridView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="3e613-106">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="3e613-107">Aby uzyskać informacje o konfigurowaniu taki projekt, zobacz [jak: Utwórz projekt aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [jak: Dodawanie formantów do formularzy Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="3e613-107">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3e613-108">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="3e613-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="3e613-109">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="3e613-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="3e613-110">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="3e613-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-make-a-column-read-only-by-using-the-designer"></a><span data-ttu-id="3e613-111">Aby kolumnę tylko do odczytu przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="3e613-111">To make a column read-only by using the designer</span></span>  
  
1.  <span data-ttu-id="3e613-112">Kliknij symbol tagu inteligentnego (![symbol tagu inteligentnego](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) w prawym górnym rogu <xref:System.Windows.Forms.DataGridView> sterowania, a następnie wybierz **Edytowanie kolumn**.</span><span class="sxs-lookup"><span data-stu-id="3e613-112">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>  
  
2.  <span data-ttu-id="3e613-113">Wybierz kolumnę z **wybrane kolumny** listy.</span><span class="sxs-lookup"><span data-stu-id="3e613-113">Select a column from the **Selected Columns** list.</span></span>  
  
3.  <span data-ttu-id="3e613-114">W **właściwości kolumny** siatki, ustaw <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="3e613-114">In the **Column Properties** grid, set the <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> property to `true`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3e613-115">Można również ustawić kolumną tylko do odczytu po dodaniu, wybierając **tylko do odczytu** pole wyboru w **Dodaj kolumnę** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="3e613-115">You can also make a column read-only when you add it by selecting the **Read Only** check box in the **Add Column** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e613-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3e613-116">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="3e613-117">Instrukcje: Dodawanie i usuwanie kolumn w formancie DataGridView formularzy Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="3e613-117">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="3e613-118">Instrukcje: Zapobiegaj wierszy i usuwanie w formancie DataGridView formularzy Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="3e613-118">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer</span></span>](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="3e613-119">Instrukcje: Utwórz projekt aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3e613-119">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="3e613-120">Instrukcje: Dodawanie formantów do formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3e613-120">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
