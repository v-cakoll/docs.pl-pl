---
title: 'Instrukcje: zapobieganie dodawaniu i usuwaniu rzędów do kontrolki DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], preventing row addition or deletion
ms.assetid: a17722bd-9400-41e6-8dcc-c9c151f0a749
ms.openlocfilehash: 9f78068597edb616017876c9c72b01d44111f6f0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59220555"
---
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="c7ff4-102">Instrukcje: zapobieganie dodawaniu i usuwaniu rzędów do kontrolki DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="c7ff4-102">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="c7ff4-103">Czasami można uniemożliwić użytkownikom wprowadzanie nowych wierszy danych lub usunięcie istniejących wierszy w swojej <xref:System.Windows.Forms.DataGridView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="c7ff4-103">Sometimes you will want to prevent users from entering new rows of data or deleting existing rows in your <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="c7ff4-104">Nowe wiersze są wprowadzane w specjalnych wiersza dla nowych rekordów w dolnej części kontrolki.</span><span class="sxs-lookup"><span data-stu-id="c7ff4-104">New rows are entered in the special row for new records at the bottom of the control.</span></span> <span data-ttu-id="c7ff4-105">Po wyłączeniu wierszy wiersza dla nowych rekordów nie jest wyświetlana.</span><span class="sxs-lookup"><span data-stu-id="c7ff4-105">When you disable row addition, the row for new records is not displayed.</span></span> <span data-ttu-id="c7ff4-106">Formant może następnie wprowadzić całkowicie tylko do odczytu, wyłączając usunięcia wiersza i edytowanie komórki.</span><span class="sxs-lookup"><span data-stu-id="c7ff4-106">You can then make the control entirely read-only by disabling row deletion and cell editing.</span></span>  
  
 <span data-ttu-id="c7ff4-107">Poniższa procedura wymaga **aplikacji Windows** projektu za pomocą zawierający formularz <xref:System.Windows.Forms.DataGridView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="c7ff4-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="c7ff4-108">Aby uzyskać informacje o konfigurowaniu taki projekt, zobacz [jak: Utwórz projekt aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [jak: Dodawanie formantów do formularzy Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="c7ff4-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c7ff4-109">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="c7ff4-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="c7ff4-110">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="c7ff4-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="c7ff4-111">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="c7ff4-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-prevent-row-addition-and-deletion"></a><span data-ttu-id="c7ff4-112">Aby zapobiec wierszy i usuwanie</span><span class="sxs-lookup"><span data-stu-id="c7ff4-112">To prevent row addition and deletion</span></span>  
  
-   <span data-ttu-id="c7ff4-113">Kliknij symbol tagu inteligentnego (![symbol tagu inteligentnego](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) w prawym górnym rogu <xref:System.Windows.Forms.DataGridView> sterowania, a następnie wyczyść **Włącz dodawanie** i **Włącz usuwanie** pola wyboru.</span><span class="sxs-lookup"><span data-stu-id="c7ff4-113">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then clear the **Enable Adding** and **Enable Deleting** check boxes.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c7ff4-114">Aby sprawić, że formant całkowicie tylko do odczytu, wyczyść **Włącz edytowanie** również pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="c7ff4-114">To make the control entirely read-only, clear the **Enable Editing** check box as well.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7ff4-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c7ff4-115">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- [<span data-ttu-id="c7ff4-116">Instrukcje: Utwórz projekt aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c7ff4-116">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="c7ff4-117">Instrukcje: Dodawanie formantów do formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c7ff4-117">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
