---
title: Dodawanie i usuwanie kolumn w formancie DataGridView przy użyciu narzędzia Projektant
ms.date: 03/30/2017
f1_keywords:
- vs.DataGridViewAddColumnDialog
helpviewer_keywords:
- DataGridView control [Windows Forms], adding columns
- DataGridView control [Windows Forms], removing columns
ms.assetid: 9e709f35-0a8c-4e7e-b4c4-bacb7a834077
ms.openlocfilehash: 8843b1d30f3e5f31a060e27b41b0105e6584f155
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628608"
---
# <a name="how-to-add-and-remove-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="c086d-102">Porady: dodawanie i usuwanie kolumn do formantu DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="c086d-102">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="c086d-103">Kontrolka <xref:System.Windows.Forms.DataGridView> Windows Forms musi zawierać kolumny, aby można było wyświetlić dane.</span><span class="sxs-lookup"><span data-stu-id="c086d-103">The Windows Forms <xref:System.Windows.Forms.DataGridView> control must contain columns in order to display data.</span></span> <span data-ttu-id="c086d-104">Jeśli planujesz ręcznie wypełnić formant, musisz dodać kolumny samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="c086d-104">If you plan to populate the control manually, you must add the columns yourself.</span></span> <span data-ttu-id="c086d-105">Alternatywnie można powiązać formant ze źródłem danych, które generuje i wypełnia kolumny automatycznie.</span><span class="sxs-lookup"><span data-stu-id="c086d-105">Alternately, you can bind the control to a data source, which generates and populates the columns automatically.</span></span> <span data-ttu-id="c086d-106">Jeśli źródło danych zawiera więcej kolumn niż ma być wyświetlanych, można usunąć niepożądane kolumny.</span><span class="sxs-lookup"><span data-stu-id="c086d-106">If the data source contains more columns than you want to display, you can remove the unwanted columns.</span></span>

 <span data-ttu-id="c086d-107">Poniższe procedury wymagają projektu **aplikacji systemu Windows** z formularzem zawierającym formant <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="c086d-107">The following procedures require a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="c086d-108">Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Create a Windows Forms Project Application](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [How to: Add controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="c086d-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-add-a-column-using-the-designer"></a><span data-ttu-id="c086d-109">Aby dodać kolumnę przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="c086d-109">To add a column using the designer</span></span>

1. <span data-ttu-id="c086d-110">Kliknij symbol akcji projektanta (![małą czarną strzałkę](./media/designer-actions-glyph.gif)) w prawym górnym rogu kontrolki <xref:System.Windows.Forms.DataGridView>, a następnie wybierz pozycję **Dodaj kolumnę**.</span><span class="sxs-lookup"><span data-stu-id="c086d-110">Click the designer actions glyph (![Small black arrow](./media/designer-actions-glyph.gif)) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Add Column**.</span></span>

2. <span data-ttu-id="c086d-111">W oknie dialogowym **Dodawanie kolumny** wybierz opcję **kolumny** z danymi i wybierz kolumnę ze źródła danych lub wybierz opcję **kolumny niepowiązane** i zdefiniuj kolumnę przy użyciu udostępnionych pól.</span><span class="sxs-lookup"><span data-stu-id="c086d-111">In the **Add Column** dialog box, choose the **Databound Column** option and select a column from the data source, or choose the **Unbound Column** option and define the column using the fields provided.</span></span>

3. <span data-ttu-id="c086d-112">Kliknij przycisk **Dodaj** , aby dodać kolumnę, powodując pojawienie się w projektancie, jeśli istniejące kolumny nie wypełniają jeszcze obszaru wyświetlania formantu.</span><span class="sxs-lookup"><span data-stu-id="c086d-112">Click the **Add** button to add the column, causing it to appear in the designer if the existing columns do not already fill the control display area.</span></span>

    > [!NOTE]
    > <span data-ttu-id="c086d-113">Właściwości kolumny można modyfikować w oknie dialogowym **Edytowanie kolumn** , do którego można uzyskać dostęp za pomocą tagu inteligentnego kontrolki.</span><span class="sxs-lookup"><span data-stu-id="c086d-113">You can modify column properties in the **Edit Columns** dialog box, which you can access from the control's smart tag.</span></span>

## <a name="to-remove-a-column-using-the-designer"></a><span data-ttu-id="c086d-114">Aby usunąć kolumnę przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="c086d-114">To remove a column using the designer</span></span>

1. <span data-ttu-id="c086d-115">Wybierz pozycję **Edytuj kolumny** z tagu inteligentnego kontrolki.</span><span class="sxs-lookup"><span data-stu-id="c086d-115">Choose **Edit Columns** from the control's smart tag.</span></span>

2. <span data-ttu-id="c086d-116">Wybierz kolumnę z listy **wybrane kolumny** .</span><span class="sxs-lookup"><span data-stu-id="c086d-116">Select a column from the **Selected Columns** list.</span></span>

3. <span data-ttu-id="c086d-117">Kliknij przycisk **Usuń** , aby usunąć kolumnę, powodując zniknięcie jej z projektanta.</span><span class="sxs-lookup"><span data-stu-id="c086d-117">Click the **Remove** button to delete the column, causing it to disappear from the designer.</span></span>

## <a name="see-also"></a><span data-ttu-id="c086d-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c086d-118">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="c086d-119">Instrukcje: Tworzenie projektu aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c086d-119">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="c086d-120">Instrukcje: dodawanie kontrolek do formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c086d-120">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
