---
title: 'Porady: dodawanie i usuwanie kolumn do formantu DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
f1_keywords:
- vs.DataGridViewAddColumnDialog
helpviewer_keywords:
- DataGridView control [Windows Forms], adding columns
- DataGridView control [Windows Forms], removing columns
ms.assetid: 9e709f35-0a8c-4e7e-b4c4-bacb7a834077
ms.openlocfilehash: 99fe1b8ffb7ccc2a5bef13ea8fef6ace5d5bdfdc
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43452810"
---
# <a name="how-to-add-and-remove-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="ab7ff-102">Porady: dodawanie i usuwanie kolumn do formantu DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="ab7ff-102">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="ab7ff-103">Formularze Windows <xref:System.Windows.Forms.DataGridView> kontroli musi zawierać kolumny, aby wyświetlić dane.</span><span class="sxs-lookup"><span data-stu-id="ab7ff-103">The Windows Forms <xref:System.Windows.Forms.DataGridView> control must contain columns in order to display data.</span></span> <span data-ttu-id="ab7ff-104">Jeśli użytkownik chce ręcznie wypełnić kontrolki, należy dodać kolumny samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="ab7ff-104">If you plan to populate the control manually, you must add the columns yourself.</span></span> <span data-ttu-id="ab7ff-105">Alternatywnie można powiązać formant ze źródłem danych, która generuje i automatycznie wypełnia kolumny.</span><span class="sxs-lookup"><span data-stu-id="ab7ff-105">Alternately, you can bind the control to a data source, which generates and populates the columns automatically.</span></span> <span data-ttu-id="ab7ff-106">Jeśli źródło danych zawiera więcej kolumn niż mają być wyświetlane, można usunąć zbędne kolumny.</span><span class="sxs-lookup"><span data-stu-id="ab7ff-106">If the data source contains more columns than you want to display, you can remove the unwanted columns.</span></span>  
  
 <span data-ttu-id="ab7ff-107">Poniższe procedury wymagają **aplikacji Windows** projektu za pomocą zawierający formularz <xref:System.Windows.Forms.DataGridView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="ab7ff-107">The following procedures require a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="ab7ff-108">Uzyskać informacji o konfigurowaniu taki projekt, zobacz [jak: Tworzenie projektu aplikacji Windows](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) i [porady: dodawanie formantów do formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="ab7ff-108">For information about setting up such a project, see [How to: Create a Windows Application Project](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ab7ff-109">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="ab7ff-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="ab7ff-110">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="ab7ff-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="ab7ff-111">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="ab7ff-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-a-column-using-the-designer"></a><span data-ttu-id="ab7ff-112">Aby dodać kolumnę przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="ab7ff-112">To add a column using the designer</span></span>  
  
1.  <span data-ttu-id="ab7ff-113">Kliknij symbol tagu inteligentnego (![symbol tagu inteligentnego](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) w prawym górnym rogu <xref:System.Windows.Forms.DataGridView> sterowania, a następnie wybierz **Dodaj kolumnę**.</span><span class="sxs-lookup"><span data-stu-id="ab7ff-113">Click the smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Add Column**.</span></span>  
  
2.  <span data-ttu-id="ab7ff-114">W **Dodaj kolumnę** okna dialogowego wybierz **kolumnę z danymi** opcję i wybierz kolumny ze źródła danych lub wybierz **niepowiązanych kolumn** opcji, a kolumna jest definiowana przy użyciu odpowiednich polach.</span><span class="sxs-lookup"><span data-stu-id="ab7ff-114">In the **Add Column** dialog box, choose the **Databound Column** option and select a column from the data source, or choose the **Unbound Column** option and define the column using the fields provided.</span></span>  
  
3.  <span data-ttu-id="ab7ff-115">Kliknij przycisk **Dodaj** przycisk, aby dodać kolumnę, co powoduje pojawiają się w projektancie, jeśli istniejące kolumny już nie wypełnia obszaru wyświetlania kontrolki.</span><span class="sxs-lookup"><span data-stu-id="ab7ff-115">Click the **Add** button to add the column, causing it to appear in the designer if the existing columns do not already fill the control display area.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ab7ff-116">Można zmodyfikować właściwości kolumny w **Edytowanie kolumn** okno dialogowe, które można wywołać z tagu kontrolki.</span><span class="sxs-lookup"><span data-stu-id="ab7ff-116">You can modify column properties in the **Edit Columns** dialog box, which you can access from the control's smart tag.</span></span>  
  
### <a name="to-remove-a-column-using-the-designer"></a><span data-ttu-id="ab7ff-117">Aby usunąć kolumnę przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="ab7ff-117">To remove a column using the designer</span></span>  
  
1.  <span data-ttu-id="ab7ff-118">Wybierz **Edytowanie kolumn** z tagu kontrolki.</span><span class="sxs-lookup"><span data-stu-id="ab7ff-118">Choose **Edit Columns** from the control's smart tag.</span></span>  
  
2.  <span data-ttu-id="ab7ff-119">Wybierz kolumnę z **wybrane kolumny** listy.</span><span class="sxs-lookup"><span data-stu-id="ab7ff-119">Select a column from the **Selected Columns** list.</span></span>  
  
3.  <span data-ttu-id="ab7ff-120">Kliknij przycisk **Usuń** przycisk, aby usunąć kolumny, które wymusi są usuwane z projektanta.</span><span class="sxs-lookup"><span data-stu-id="ab7ff-120">Click the **Remove** button to delete the column, causing it to disappear from the designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab7ff-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ab7ff-121">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="ab7ff-122">Porady: Tworzenie projektu aplikacji Windows</span><span class="sxs-lookup"><span data-stu-id="ab7ff-122">How to: Create a Windows Application Project</span></span>](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [<span data-ttu-id="ab7ff-123">Instrukcje: dodawanie kontrolek do formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ab7ff-123">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
