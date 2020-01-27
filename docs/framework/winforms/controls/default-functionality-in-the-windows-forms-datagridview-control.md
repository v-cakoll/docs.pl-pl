---
title: Domyślna funkcjonalność w formancie DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], default functionality in DataGridView control
- DataGridView control [Windows Forms], default functionality
ms.assetid: 4405f697-cad1-4839-9bcd-8ddb09d9f00e
ms.openlocfilehash: b695883ac7ec3fb0c459adb66214b0eceab3a128
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746137"
---
# <a name="default-functionality-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="0a034-102">Funkcje domyślne w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="0a034-102">Default Functionality in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="0a034-103">Kontrolka <xref:System.Windows.Forms.DataGridView> Windows Forms zapewnia użytkownikom znaczną liczbę domyślnych funkcji.</span><span class="sxs-lookup"><span data-stu-id="0a034-103">The Windows Forms <xref:System.Windows.Forms.DataGridView> control provides users with a significant amount of default functionality.</span></span>  
  
## <a name="default-functionality"></a><span data-ttu-id="0a034-104">Domyślna funkcjonalność</span><span class="sxs-lookup"><span data-stu-id="0a034-104">Default Functionality</span></span>  
 <span data-ttu-id="0a034-105">Domyślnie formant <xref:System.Windows.Forms.DataGridView>:</span><span class="sxs-lookup"><span data-stu-id="0a034-105">By default, a <xref:System.Windows.Forms.DataGridView> control:</span></span>  
  
- <span data-ttu-id="0a034-106">Automatycznie wyświetla nagłówki kolumn i nagłówki wierszy, które pozostaną widoczne, gdy tabela jest przewijana pionowo.</span><span class="sxs-lookup"><span data-stu-id="0a034-106">Automatically displays column headers and row headers that remain visible as the table scrolls vertically.</span></span>  
  
- <span data-ttu-id="0a034-107">Zawiera nagłówek wiersza, który zawiera wskaźnik wyboru dla bieżącego wiersza.</span><span class="sxs-lookup"><span data-stu-id="0a034-107">Has a row header that contains a selection indicator for the current row.</span></span>  
  
- <span data-ttu-id="0a034-108">Zawiera prostokąt wyboru w pierwszej komórce.</span><span class="sxs-lookup"><span data-stu-id="0a034-108">Has a selection rectangle in the first cell.</span></span>  
  
- <span data-ttu-id="0a034-109">Ma kolumny, których rozmiar można zmienić automatycznie, gdy użytkownik kliknie dwukrotnie linię podziału kolumn.</span><span class="sxs-lookup"><span data-stu-id="0a034-109">Has columns that can be automatically resized when the user double-clicks the column dividers.</span></span>  
  
- <span data-ttu-id="0a034-110">Program automatycznie obsługuje style wizualne w systemach Windows XP i Windows Server 2003, gdy metoda <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> jest wywoływana z metody `Main` aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0a034-110">Automatically supports visual styles on Windows XP and the Windows Server 2003 family when the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method is called from the application's `Main` method.</span></span>  
  
 <span data-ttu-id="0a034-111">Ponadto zawartość kontrolki <xref:System.Windows.Forms.DataGridView> można edytować domyślnie:</span><span class="sxs-lookup"><span data-stu-id="0a034-111">Additionally, the contents of a <xref:System.Windows.Forms.DataGridView> control can be edited by default:</span></span>  
  
- <span data-ttu-id="0a034-112">Jeśli użytkownik kliknie dwukrotnie lub naciśnie klawisz F2 w komórce, formant automatycznie umieści komórkę w trybie edycji i zaktualizuje zawartość komórki jako typy użytkowników.</span><span class="sxs-lookup"><span data-stu-id="0a034-112">If the user double-clicks or presses F2 in a cell, the control automatically puts the cell into edit mode and updates the contents of the cell as the user types.</span></span>  
  
- <span data-ttu-id="0a034-113">Jeśli użytkownik przejdzie do końca siatki, zobaczysz, że jest dostępny wiersz służący do dodawania nowych rekordów.</span><span class="sxs-lookup"><span data-stu-id="0a034-113">If the user scrolls to the end of the grid, the user will see that a row for adding new records is present.</span></span> <span data-ttu-id="0a034-114">Gdy użytkownik kliknie ten wiersz, do kontrolki <xref:System.Windows.Forms.DataGridView> zostanie dodany nowy wiersz z wartościami domyślnymi.</span><span class="sxs-lookup"><span data-stu-id="0a034-114">When the user clicks this row, a new row is added to the <xref:System.Windows.Forms.DataGridView> control, with default values.</span></span> <span data-ttu-id="0a034-115">Gdy użytkownik naciśnie klawisz ESC, ten nowy wiersz zniknie.</span><span class="sxs-lookup"><span data-stu-id="0a034-115">When the user presses ESC, this new row disappears.</span></span>  
  
- <span data-ttu-id="0a034-116">Jeśli użytkownik kliknie nagłówek wiersza, zostanie wybrany cały wiersz.</span><span class="sxs-lookup"><span data-stu-id="0a034-116">If the user clicks a row header, the whole row is selected.</span></span>  
  
 <span data-ttu-id="0a034-117">Po powiązaniu formantu <xref:System.Windows.Forms.DataGridView> ze źródłem danych przez ustawienie jego właściwości <xref:System.Windows.Forms.DataGridView.DataSource%2A> kontrolka:</span><span class="sxs-lookup"><span data-stu-id="0a034-117">When you bind a <xref:System.Windows.Forms.DataGridView> control to a data source by setting its <xref:System.Windows.Forms.DataGridView.DataSource%2A> property, the control:</span></span>  
  
- <span data-ttu-id="0a034-118">Automatycznie używa nazw kolumn źródła danych jako tekstu nagłówka kolumny.</span><span class="sxs-lookup"><span data-stu-id="0a034-118">Automatically uses the names of the data source's columns as the column header text.</span></span>  
  
- <span data-ttu-id="0a034-119">Jest wypełniana zawartością źródła danych.</span><span class="sxs-lookup"><span data-stu-id="0a034-119">Is populated with the contents of the data source.</span></span> <span data-ttu-id="0a034-120">kolumny <xref:System.Windows.Forms.DataGridView> są tworzone automatycznie dla każdej kolumny w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="0a034-120"><xref:System.Windows.Forms.DataGridView> columns are automatically created for each column in the data source.</span></span>  
  
- <span data-ttu-id="0a034-121">Tworzy wiersz dla każdego widocznego wiersza w tabeli.</span><span class="sxs-lookup"><span data-stu-id="0a034-121">Creates a row for each visible row in the table.</span></span>  
  
- <span data-ttu-id="0a034-122">Automatycznie sortuje wiersze na podstawie danych źródłowych, gdy użytkownik kliknie nagłówek kolumny.</span><span class="sxs-lookup"><span data-stu-id="0a034-122">Automatically sorts the rows based on the underlying data when the user clicks a column header.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a034-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0a034-123">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="0a034-124">DataGridView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="0a034-124">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
