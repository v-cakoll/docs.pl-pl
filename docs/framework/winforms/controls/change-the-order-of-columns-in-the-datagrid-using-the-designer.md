---
title: 'Instrukcje: Zmienianie kolejności kolumn w formancie DataGridView formularzy Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], order of
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- data [Windows Forms], displaying
ms.assetid: 7fe52a98-75d6-448c-97a5-65ca2c568c1a
ms.openlocfilehash: 58a92b4f5f604bba0da4b5a42ff25b0122b6f01e
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57702948"
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="35a57-102">Instrukcje: Zmienianie kolejności kolumn w formancie DataGridView formularzy Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="35a57-102">How to: Change the Order of Columns in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="35a57-103">Po powiązaniu formularze Windows <xref:System.Windows.Forms.DataGridView> formant ze źródłem danych, kolejność wyświetlania kolumn automatycznie generowany jest zależna od źródła danych.</span><span class="sxs-lookup"><span data-stu-id="35a57-103">When you bind a Windows Forms <xref:System.Windows.Forms.DataGridView> control to a data source, the display order of the automatically generated columns is dictated by the data source.</span></span> <span data-ttu-id="35a57-104">Jeśli ta kolejność jest nie chcesz, możesz zmienić kolejność kolumn za pomocą projektanta.</span><span class="sxs-lookup"><span data-stu-id="35a57-104">If this order is not what you prefer, you can change the order of the columns using the designer.</span></span> <span data-ttu-id="35a57-105">Można również dodawanie niepowiązanych kolumn do kontrolki i ich kolejność wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="35a57-105">You may also want to add unbound columns to the control and change their display order.</span></span> <span data-ttu-id="35a57-106">Aby dowiedzieć się, jak programowo zmienić kolejność kolumn, zobacz [jak: Zmienianie kolejności kolumn w formancie DataGridView formularzy Windows](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="35a57-106">For information about how to change the column order programmatically, see [How to: Change the Order of Columns in the Windows Forms DataGridView Control](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="35a57-107">Poniższa procedura wymaga **aplikacji Windows** projektu za pomocą zawierający formularz <xref:System.Windows.Forms.DataGridView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="35a57-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="35a57-108">Aby uzyskać informacje o konfigurowaniu taki projekt, zobacz [jak: Utwórz projekt aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [jak: Dodawanie formantów do formularzy Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="35a57-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="35a57-109">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="35a57-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="35a57-110">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="35a57-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="35a57-111">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide)</span><span class="sxs-lookup"><span data-stu-id="35a57-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)</span></span>  
  
### <a name="to-change-the-column-order-using-the-designer"></a><span data-ttu-id="35a57-112">Aby zmienić kolejność kolumn przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="35a57-112">To change the column order using the designer</span></span>  
  
1.  <span data-ttu-id="35a57-113">Kliknij symbol tagu inteligentnego (![symbol tagu inteligentnego](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) w prawym górnym rogu <xref:System.Windows.Forms.DataGridView> sterowania, a następnie wybierz **Edytowanie kolumn**.</span><span class="sxs-lookup"><span data-stu-id="35a57-113">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>  
  
2.  <span data-ttu-id="35a57-114">Wybierz kolumnę z **wybrane kolumny** listy.</span><span class="sxs-lookup"><span data-stu-id="35a57-114">Select a column from the **Selected Columns** list.</span></span>  
  
3.  <span data-ttu-id="35a57-115">Kliknij w górę lub dół po prawej stronie **wybranych kolumn** listy, dopóki nie zaznaczonej kolumnie znajduje się w odpowiednie miejsce.</span><span class="sxs-lookup"><span data-stu-id="35a57-115">Click the up or down arrow to the right of the **Selected Columns** list until the selected column is in the position you want.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35a57-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="35a57-116">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="35a57-117">Instrukcje: Dodawanie i usuwanie kolumn w formancie DataGridView formularzy Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="35a57-117">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="35a57-118">Instrukcje: Utwórz projekt aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="35a57-118">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="35a57-119">Instrukcje: Dodawanie formantów do formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="35a57-119">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
