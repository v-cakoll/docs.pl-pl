---
title: 'Instrukcje: włączanie zmiany układu kolumn w kontrolce DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- columns [Windows Forms], reordering
- data [Windows Forms], displaying
ms.assetid: d82bd69c-6799-4439-a32c-91139c5901d1
ms.openlocfilehash: 3864ce70f058259b597df904311bd4a48218b151
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040344"
---
# <a name="how-to-enable-column-reordering-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="2b0e2-102">Instrukcje: włączanie zmiany układu kolumn w kontrolce DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="2b0e2-102">How to: Enable Column Reordering in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="2b0e2-103">Podczas wyświetlania danych wyświetlanych w kontrolce Windows Forms <xref:System.Windows.Forms.DataGridView> użytkownicy czasami chcą porównać wartości w określonych kolumnach.</span><span class="sxs-lookup"><span data-stu-id="2b0e2-103">When viewing data displayed in a Windows Forms <xref:System.Windows.Forms.DataGridView> control, users sometimes want to compare the values in specific columns.</span></span> <span data-ttu-id="2b0e2-104">Może to być niewygodne, jeśli kolumny są szeroko oddzielone w kontrolce, szczególnie jeśli użytkownicy muszą przewinąć w dół i w dół w celu wyświetlenia wszystkich interesujących Cię kolumn.</span><span class="sxs-lookup"><span data-stu-id="2b0e2-104">This can be inconvenient if the columns are widely separated in the control, especially if users must scroll back and forth horizontally in order to see all the columns they are interested in.</span></span> <span data-ttu-id="2b0e2-105">Zadanie porównywania wartości kolumn można ułatwić, umożliwiając użytkownikom zmianę kolejności kolumn.</span><span class="sxs-lookup"><span data-stu-id="2b0e2-105">You can make the task of comparing column values easier by enabling your users to reorder the columns.</span></span> <span data-ttu-id="2b0e2-106">Po włączeniu zmiany kolejności kolumn użytkownicy mogą przenieść kolumnę do nowej pozycji, przeciągając nagłówek kolumny za pomocą myszy.</span><span class="sxs-lookup"><span data-stu-id="2b0e2-106">When you enable column reordering, users can move a column to a new position by dragging the column header with the mouse.</span></span>

 <span data-ttu-id="2b0e2-107">Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym <xref:System.Windows.Forms.DataGridView> kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="2b0e2-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="2b0e2-108">Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Utwórz projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikacji Windows Forms i [instrukcje: Dodaj formanty do Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="2b0e2-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-enable-column-reordering"></a><span data-ttu-id="2b0e2-109">Aby włączyć Zmienianie kolejności kolumn</span><span class="sxs-lookup"><span data-stu-id="2b0e2-109">To enable column reordering</span></span>

- <span data-ttu-id="2b0e2-110">Kliknij symbol taga inteligentnego (![tag inteligentny](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) w prawym górnym <xref:System.Windows.Forms.DataGridView> rogu kontrolki, a następnie wybierz pozycję **Włącz zmienianie kolejności kolumn**.</span><span class="sxs-lookup"><span data-stu-id="2b0e2-110">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Enable Column Reordering**.</span></span>

## <a name="see-also"></a><span data-ttu-id="2b0e2-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2b0e2-111">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType>
- [<span data-ttu-id="2b0e2-112">Instrukcje: Zablokuj kolumny w kontrolce DataGridView Windows Forms przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="2b0e2-112">How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](freeze-columns-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="2b0e2-113">Instrukcje: Tworzenie projektu aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2b0e2-113">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="2b0e2-114">Instrukcje: Dodawanie formantów do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2b0e2-114">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
