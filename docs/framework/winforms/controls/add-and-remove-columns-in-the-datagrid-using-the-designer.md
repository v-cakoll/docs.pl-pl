---
title: 'Instrukcje: dodawanie i usuwanie kolumn do kontrolki DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
f1_keywords:
- vs.DataGridViewAddColumnDialog
helpviewer_keywords:
- DataGridView control [Windows Forms], adding columns
- DataGridView control [Windows Forms], removing columns
ms.assetid: 9e709f35-0a8c-4e7e-b4c4-bacb7a834077
ms.openlocfilehash: 80ede9b7bc5bf667e03dc0a745fbc0b5f6c2663a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59343288"
---
# <a name="how-to-add-and-remove-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="924fb-102">Instrukcje: dodawanie i usuwanie kolumn do kontrolki DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="924fb-102">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="924fb-103">Formularze Windows <xref:System.Windows.Forms.DataGridView> kontroli musi zawierać kolumny, aby wyświetlić dane.</span><span class="sxs-lookup"><span data-stu-id="924fb-103">The Windows Forms <xref:System.Windows.Forms.DataGridView> control must contain columns in order to display data.</span></span> <span data-ttu-id="924fb-104">Jeśli użytkownik chce ręcznie wypełnić kontrolki, należy dodać kolumny samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="924fb-104">If you plan to populate the control manually, you must add the columns yourself.</span></span> <span data-ttu-id="924fb-105">Alternatywnie można powiązać formant ze źródłem danych, która generuje i automatycznie wypełnia kolumny.</span><span class="sxs-lookup"><span data-stu-id="924fb-105">Alternately, you can bind the control to a data source, which generates and populates the columns automatically.</span></span> <span data-ttu-id="924fb-106">Jeśli źródło danych zawiera więcej kolumn niż mają być wyświetlane, można usunąć zbędne kolumny.</span><span class="sxs-lookup"><span data-stu-id="924fb-106">If the data source contains more columns than you want to display, you can remove the unwanted columns.</span></span>  
  
 <span data-ttu-id="924fb-107">Poniższe procedury wymagają **aplikacji Windows** projektu za pomocą zawierający formularz <xref:System.Windows.Forms.DataGridView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="924fb-107">The following procedures require a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="924fb-108">Aby uzyskać informacje o konfigurowaniu taki projekt, zobacz [jak: Utwórz projekt aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [jak: Dodawanie formantów do formularzy Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="924fb-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="924fb-109">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="924fb-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="924fb-110">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="924fb-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="924fb-111">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="924fb-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-a-column-using-the-designer"></a><span data-ttu-id="924fb-112">Aby dodać kolumnę przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="924fb-112">To add a column using the designer</span></span>  
  
1. <span data-ttu-id="924fb-113">Kliknij symbol tagu inteligentnego (![symbol tagu inteligentnego](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) w prawym górnym rogu <xref:System.Windows.Forms.DataGridView> sterowania, a następnie wybierz **Dodaj kolumnę**.</span><span class="sxs-lookup"><span data-stu-id="924fb-113">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Add Column**.</span></span>  
  
2. <span data-ttu-id="924fb-114">W **Dodaj kolumnę** okna dialogowego wybierz **kolumnę z danymi** opcję i wybierz kolumny ze źródła danych lub wybierz **niepowiązanych kolumn** opcji, a kolumna jest definiowana przy użyciu odpowiednich polach.</span><span class="sxs-lookup"><span data-stu-id="924fb-114">In the **Add Column** dialog box, choose the **Databound Column** option and select a column from the data source, or choose the **Unbound Column** option and define the column using the fields provided.</span></span>  
  
3. <span data-ttu-id="924fb-115">Kliknij przycisk **Dodaj** przycisk, aby dodać kolumnę, co powoduje pojawiają się w projektancie, jeśli istniejące kolumny już nie wypełnia obszaru wyświetlania kontrolki.</span><span class="sxs-lookup"><span data-stu-id="924fb-115">Click the **Add** button to add the column, causing it to appear in the designer if the existing columns do not already fill the control display area.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="924fb-116">Można zmodyfikować właściwości kolumny w **Edytowanie kolumn** okno dialogowe, które można wywołać z tagu kontrolki.</span><span class="sxs-lookup"><span data-stu-id="924fb-116">You can modify column properties in the **Edit Columns** dialog box, which you can access from the control's smart tag.</span></span>  
  
### <a name="to-remove-a-column-using-the-designer"></a><span data-ttu-id="924fb-117">Aby usunąć kolumnę przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="924fb-117">To remove a column using the designer</span></span>  
  
1. <span data-ttu-id="924fb-118">Wybierz **Edytowanie kolumn** z tagu kontrolki.</span><span class="sxs-lookup"><span data-stu-id="924fb-118">Choose **Edit Columns** from the control's smart tag.</span></span>  
  
2. <span data-ttu-id="924fb-119">Wybierz kolumnę z **wybrane kolumny** listy.</span><span class="sxs-lookup"><span data-stu-id="924fb-119">Select a column from the **Selected Columns** list.</span></span>  
  
3. <span data-ttu-id="924fb-120">Kliknij przycisk **Usuń** przycisk, aby usunąć kolumny, które wymusi są usuwane z projektanta.</span><span class="sxs-lookup"><span data-stu-id="924fb-120">Click the **Remove** button to delete the column, causing it to disappear from the designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="924fb-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="924fb-121">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="924fb-122">Instrukcje: Utwórz projekt aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="924fb-122">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="924fb-123">Instrukcje: dodawanie kontrolek do formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="924fb-123">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
