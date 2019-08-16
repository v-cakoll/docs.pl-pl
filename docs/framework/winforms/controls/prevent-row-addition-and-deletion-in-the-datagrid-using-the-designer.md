---
title: 'Instrukcje: zapobieganie dodawaniu i usuwaniu rzędów do kontrolki DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], preventing row addition or deletion
ms.assetid: a17722bd-9400-41e6-8dcc-c9c151f0a749
ms.openlocfilehash: 20f9b85dc48ccd634468d0fed000120723f8ee5c
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038187"
---
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="6780c-102">Instrukcje: zapobieganie dodawaniu i usuwaniu rzędów do kontrolki DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="6780c-102">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="6780c-103">Czasami chcesz uniemożliwić użytkownikom wprowadzanie nowych wierszy danych lub usuwanie istniejących wierszy w <xref:System.Windows.Forms.DataGridView> kontrolce.</span><span class="sxs-lookup"><span data-stu-id="6780c-103">Sometimes you will want to prevent users from entering new rows of data or deleting existing rows in your <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="6780c-104">Nowe wiersze są wprowadzane w specjalnym wierszu dla nowych rekordów w dolnej części formantu.</span><span class="sxs-lookup"><span data-stu-id="6780c-104">New rows are entered in the special row for new records at the bottom of the control.</span></span> <span data-ttu-id="6780c-105">Po wyłączeniu dodawania wierszy nie jest wyświetlany wiersz dla nowych rekordów.</span><span class="sxs-lookup"><span data-stu-id="6780c-105">When you disable row addition, the row for new records is not displayed.</span></span> <span data-ttu-id="6780c-106">Następnie można sprawić, aby formant całkowicie tylko do odczytu przez wyłączenie usuwania wierszy i edytowanie komórek.</span><span class="sxs-lookup"><span data-stu-id="6780c-106">You can then make the control entirely read-only by disabling row deletion and cell editing.</span></span>

 <span data-ttu-id="6780c-107">Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym <xref:System.Windows.Forms.DataGridView> kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="6780c-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="6780c-108">Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Utwórz projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikacji Windows Forms i [instrukcje: Dodaj formanty do Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="6780c-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-prevent-row-addition-and-deletion"></a><span data-ttu-id="6780c-109">Aby zapobiec dodawaniu i usuwaniu wierszy</span><span class="sxs-lookup"><span data-stu-id="6780c-109">To prevent row addition and deletion</span></span>

- <span data-ttu-id="6780c-110">Kliknij symbol taga inteligentnego (![tag inteligentny](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) w prawym górnym <xref:System.Windows.Forms.DataGridView> rogu kontrolki, a następnie wyczyść pola wyboru **Włącz Dodawanie** i **Włączanie usuwania** .</span><span class="sxs-lookup"><span data-stu-id="6780c-110">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then clear the **Enable Adding** and **Enable Deleting** check boxes.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="6780c-111">Aby formant można było całkowicie tylko do odczytu, usuń zaznaczenie pola wyboru **Włącz edycję** .</span><span class="sxs-lookup"><span data-stu-id="6780c-111">To make the control entirely read-only, clear the **Enable Editing** check box as well.</span></span>

## <a name="see-also"></a><span data-ttu-id="6780c-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6780c-112">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- [<span data-ttu-id="6780c-113">Instrukcje: Tworzenie projektu aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6780c-113">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="6780c-114">Instrukcje: Dodawanie formantów do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6780c-114">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
