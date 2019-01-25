---
title: 'Instrukcje: Zmień typ kolumny formantu DataGridView formularzy Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], types
- DataGridView control [Windows Forms], changing column type
- data [Windows Forms], displaying
ms.assetid: 7f994d45-600d-4190-a187-35803214b40c
ms.openlocfilehash: 12e6e15dd3b4e7941be198a526e8145ceb126e8d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54544617"
---
# <a name="how-to-change-the-type-of-a-windows-forms-datagridview-column-using-the-designer"></a><span data-ttu-id="991ee-102">Instrukcje: Zmień typ kolumny formantu DataGridView formularzy Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="991ee-102">How to: Change the Type of a Windows Forms DataGridView Column Using the Designer</span></span>
<span data-ttu-id="991ee-103">Czasami można zmienić typ kolumny, który został już dodany do formularzy Windows <xref:System.Windows.Forms.DataGridView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="991ee-103">Sometimes you will want to change the type of a column that has already been added to a Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="991ee-104">Na przykład można modyfikować typy niektórych kolumn, które są generowane automatycznie, gdy powiąże formant ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="991ee-104">For example, you may want to modify the types of some of the columns that are generated automatically when you bind the control to a data source.</span></span> <span data-ttu-id="991ee-105">Jest to przydatne, gdy tabelę, którą możesz wyświetlić ma kolumn zawierających klucze obce do wierszy w powiązanej tabeli.</span><span class="sxs-lookup"><span data-stu-id="991ee-105">This is useful when the table you display has columns containing foreign keys to rows in a related table.</span></span> <span data-ttu-id="991ee-106">W takim przypadku można zastąpić tekst kolumny pole zawierające te klucze obce kolumny pola kombi, zawierające bardziej zrozumiały wartości z tabeli powiązanej.</span><span class="sxs-lookup"><span data-stu-id="991ee-106">In this case, you may want to replace the text box columns that display these foreign keys with combo box columns that display more meaningful values from the related table.</span></span>  
  
 <span data-ttu-id="991ee-107">Poniższa procedura wymaga **aplikacji Windows** projektu za pomocą zawierający formularz <xref:System.Windows.Forms.DataGridView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="991ee-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="991ee-108">Aby uzyskać informacje o konfigurowaniu taki projekt, zobacz [jak: Utwórz projekt aplikacji Windows](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) i [jak: Dodawanie formantów do formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="991ee-108">For information about setting up such a project, see [How to: Create a Windows Application Project](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="991ee-109">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="991ee-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="991ee-110">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="991ee-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="991ee-111">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="991ee-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-change-the-type-of-a-column-using-the-designer"></a><span data-ttu-id="991ee-112">Aby zmienić typ kolumny przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="991ee-112">To change the type of a column using the designer</span></span>  
  
1.  <span data-ttu-id="991ee-113">Kliknij symbol tagu inteligentnego (![symbol tagu inteligentnego](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) w prawym górnym rogu <xref:System.Windows.Forms.DataGridView> sterowania, a następnie wybierz **Edytowanie kolumn**.</span><span class="sxs-lookup"><span data-stu-id="991ee-113">Click the smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>  
  
2.  <span data-ttu-id="991ee-114">Wybierz kolumnę z **wybrane kolumny** listy.</span><span class="sxs-lookup"><span data-stu-id="991ee-114">Select a column from the **Selected Columns** list.</span></span>  
  
3.  <span data-ttu-id="991ee-115">W **właściwości kolumny** siatki, ustaw `ColumnType` właściwości nowego typu kolumny.</span><span class="sxs-lookup"><span data-stu-id="991ee-115">In the **Column Properties** grid, set the `ColumnType` property to the new column type.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="991ee-116">`ColumnType` Właściwości jest właściwością projektowania — tylko od czasu, która określa klasy reprezentujące typ kolumny.</span><span class="sxs-lookup"><span data-stu-id="991ee-116">The `ColumnType` property is a design-time-only property that indicates the class representing the column type.</span></span> <span data-ttu-id="991ee-117">Nie jest właściwością rzeczywiste zdefiniowanej w klasie kolumny.</span><span class="sxs-lookup"><span data-stu-id="991ee-117">It is not an actual property defined in a column class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="991ee-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="991ee-118">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [<span data-ttu-id="991ee-119">Instrukcje: Utwórz projekt aplikacji Windows</span><span class="sxs-lookup"><span data-stu-id="991ee-119">How to: Create a Windows Application Project</span></span>](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)
- [<span data-ttu-id="991ee-120">Instrukcje: Dodawanie formantów do formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="991ee-120">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
