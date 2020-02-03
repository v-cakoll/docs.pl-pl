---
title: Zmiana kolejności kolumn w formancie DataGridView przy użyciu narzędzia Projektant
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], order of
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- data [Windows Forms], displaying
ms.assetid: 7fe52a98-75d6-448c-97a5-65ca2c568c1a
ms.openlocfilehash: be4f67ca6530b74fc90cb50a10463b2378edb933
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743159"
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="ffbbc-102">Porady: zmienianie kolejności kolumn w formancie DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="ffbbc-102">How to: Change the Order of Columns in the Windows Forms DataGridView Control Using the Designer</span></span>

<span data-ttu-id="ffbbc-103">Po powiązaniu kontrolki <xref:System.Windows.Forms.DataGridView> Windows Forms ze źródłem danych zostanie wyświetlona kolejność wyświetlania automatycznie generowanych kolumn.</span><span class="sxs-lookup"><span data-stu-id="ffbbc-103">When you bind a Windows Forms <xref:System.Windows.Forms.DataGridView> control to a data source, the display order of the automatically generated columns is dictated by the data source.</span></span> <span data-ttu-id="ffbbc-104">Jeśli ta kolejność nie jest preferowana, można zmienić kolejność kolumn za pomocą narzędzia Projektant.</span><span class="sxs-lookup"><span data-stu-id="ffbbc-104">If this order is not what you prefer, you can change the order of the columns using the designer.</span></span> <span data-ttu-id="ffbbc-105">Możesz również dodać niepowiązane kolumny do kontrolki i zmienić ich kolejność wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="ffbbc-105">You may also want to add unbound columns to the control and change their display order.</span></span> <span data-ttu-id="ffbbc-106">Informacje o sposobie zmiany kolejności kolumn w programie można znaleźć w temacie [How to: zmiana kolejności kolumn w kontrolce DataGridView Windows Forms](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="ffbbc-106">For information about how to change the column order programmatically, see [How to: Change the Order of Columns in the Windows Forms DataGridView Control](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md).</span></span>

<span data-ttu-id="ffbbc-107">Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym formant <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="ffbbc-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="ffbbc-108">Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Create a Windows Forms Project Application](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [How to: Add controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="ffbbc-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-change-the-column-order-using-the-designer"></a><span data-ttu-id="ffbbc-109">Aby zmienić kolejność kolumn przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="ffbbc-109">To change the column order using the designer</span></span>

1. <span data-ttu-id="ffbbc-110">Kliknij symbol taga inteligentnego (![symbol tagu inteligentnego](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) w prawym górnym rogu kontrolki <xref:System.Windows.Forms.DataGridView>, a następnie wybierz pozycję **Edytuj kolumny**.</span><span class="sxs-lookup"><span data-stu-id="ffbbc-110">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>

2. <span data-ttu-id="ffbbc-111">Wybierz kolumnę z listy **wybrane kolumny** .</span><span class="sxs-lookup"><span data-stu-id="ffbbc-111">Select a column from the **Selected Columns** list.</span></span>

3. <span data-ttu-id="ffbbc-112">Kliknij strzałkę w górę lub w dół znajdującą się po prawej stronie listy **wybrane kolumny** , dopóki wybrana kolumna nie znajduje się w pożądanej pozycji.</span><span class="sxs-lookup"><span data-stu-id="ffbbc-112">Click the up or down arrow to the right of the **Selected Columns** list until the selected column is in the position you want.</span></span>

## <a name="see-also"></a><span data-ttu-id="ffbbc-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ffbbc-113">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="ffbbc-114">Instrukcje: dodawanie i usuwanie kolumn do kontrolki DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="ffbbc-114">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="ffbbc-115">Instrukcje: Tworzenie projektu aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ffbbc-115">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="ffbbc-116">Instrukcje: dodawanie kontrolek do formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ffbbc-116">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
