---
title: Funkcje domyślne w formancie DataGridView formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], default functionality in DataGridView control
- DataGridView control [Windows Forms], default functionality
ms.assetid: 4405f697-cad1-4839-9bcd-8ddb09d9f00e
ms.openlocfilehash: b84d5a279bfe7cd99262ca904daeceabc9d0355d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648067"
---
# <a name="default-functionality-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="8ae21-102">Funkcje domyślne w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="8ae21-102">Default Functionality in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="8ae21-103">Formularze Windows <xref:System.Windows.Forms.DataGridView> kontroli udostępnia użytkownikom znacznej ilości funkcje domyślne.</span><span class="sxs-lookup"><span data-stu-id="8ae21-103">The Windows Forms <xref:System.Windows.Forms.DataGridView> control provides users with a significant amount of default functionality.</span></span>  
  
## <a name="default-functionality"></a><span data-ttu-id="8ae21-104">Domyślna funkcjonalność</span><span class="sxs-lookup"><span data-stu-id="8ae21-104">Default Functionality</span></span>  
 <span data-ttu-id="8ae21-105">Domyślnie <xref:System.Windows.Forms.DataGridView> sterowania:</span><span class="sxs-lookup"><span data-stu-id="8ae21-105">By default, a <xref:System.Windows.Forms.DataGridView> control:</span></span>  
  
- <span data-ttu-id="8ae21-106">Automatycznie Wyświetla nagłówki kolumn i nagłówki wierszy, które pozostają widoczne, ponieważ tabela przewijać w pionie.</span><span class="sxs-lookup"><span data-stu-id="8ae21-106">Automatically displays column headers and row headers that remain visible as the table scrolls vertically.</span></span>  
  
- <span data-ttu-id="8ae21-107">Zawiera nagłówek wiersza, który zawiera wskaźnik zaznaczenia bieżącego wiersza.</span><span class="sxs-lookup"><span data-stu-id="8ae21-107">Has a row header that contains a selection indicator for the current row.</span></span>  
  
- <span data-ttu-id="8ae21-108">Nie ma prostokąta zaznaczenia w pierwszej komórki.</span><span class="sxs-lookup"><span data-stu-id="8ae21-108">Has a selection rectangle in the first cell.</span></span>  
  
- <span data-ttu-id="8ae21-109">Zawiera kolumny, które można automatycznie dopasowane, gdy użytkownik kliknie dwukrotnie separator kolumn.</span><span class="sxs-lookup"><span data-stu-id="8ae21-109">Has columns that can be automatically resized when the user double-clicks the column dividers.</span></span>  
  
- <span data-ttu-id="8ae21-110">Automatycznie obsługuje stylów wizualnych Windows XP i rodziny Windows Server 2003 podczas <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metoda jest wywoływana z aplikacji `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="8ae21-110">Automatically supports visual styles on Windows XP and the Windows Server 2003 family when the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method is called from the application's `Main` method.</span></span>  
  
 <span data-ttu-id="8ae21-111">Ponadto zawartość <xref:System.Windows.Forms.DataGridView> kontrolki mogą być edytowane przez domyślny:</span><span class="sxs-lookup"><span data-stu-id="8ae21-111">Additionally, the contents of a <xref:System.Windows.Forms.DataGridView> control can be edited by default:</span></span>  
  
- <span data-ttu-id="8ae21-112">Jeśli użytkownik kliknie dwukrotnie lub naciśnie klawisz F2 w komórce, formant umieszcza komórkę w trybie edycji i automatycznie aktualizuje zawartość komórki, gdy użytkownik wpisuje.</span><span class="sxs-lookup"><span data-stu-id="8ae21-112">If the user double-clicks or presses F2 in a cell, the control automatically puts the cell into edit mode and updates the contents of the cell as the user types.</span></span>  
  
- <span data-ttu-id="8ae21-113">Jeśli użytkownik przewija widok w celu siatki, użytkownik będzie widział występuje wiersz do dodawania nowych rekordów.</span><span class="sxs-lookup"><span data-stu-id="8ae21-113">If the user scrolls to the end of the grid, the user will see that a row for adding new records is present.</span></span> <span data-ttu-id="8ae21-114">Gdy użytkownik kliknie ten wiersz, nowego wiersza zostanie dodane do <xref:System.Windows.Forms.DataGridView> kontrolki z wartościami domyślnymi.</span><span class="sxs-lookup"><span data-stu-id="8ae21-114">When the user clicks this row, a new row is added to the <xref:System.Windows.Forms.DataGridView> control, with default values.</span></span> <span data-ttu-id="8ae21-115">Gdy użytkownik naciśnie klawisz ESC, zniknie tego nowego wiersza.</span><span class="sxs-lookup"><span data-stu-id="8ae21-115">When the user presses ESC, this new row disappears.</span></span>  
  
- <span data-ttu-id="8ae21-116">Jeśli użytkownik kliknie nagłówek wiersza, zostanie wybrany cały wiersz.</span><span class="sxs-lookup"><span data-stu-id="8ae21-116">If the user clicks a row header, the whole row is selected.</span></span>  
  
 <span data-ttu-id="8ae21-117">Po powiązaniu <xref:System.Windows.Forms.DataGridView> formant ze źródłem danych, ustawiając jego <xref:System.Windows.Forms.DataGridView.DataSource%2A> właściwość, formant:</span><span class="sxs-lookup"><span data-stu-id="8ae21-117">When you bind a <xref:System.Windows.Forms.DataGridView> control to a data source by setting its <xref:System.Windows.Forms.DataGridView.DataSource%2A> property, the control:</span></span>  
  
- <span data-ttu-id="8ae21-118">Automatycznie używa nazwy kolumn źródła danych jako tekst nagłówka kolumny.</span><span class="sxs-lookup"><span data-stu-id="8ae21-118">Automatically uses the names of the data source's columns as the column header text.</span></span>  
  
- <span data-ttu-id="8ae21-119">Jest wypełniana na podstawie zawartości źródła danych.</span><span class="sxs-lookup"><span data-stu-id="8ae21-119">Is populated with the contents of the data source.</span></span> <span data-ttu-id="8ae21-120"><xref:System.Windows.Forms.DataGridView> kolumny są tworzone automatycznie dla każdej kolumny w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="8ae21-120"><xref:System.Windows.Forms.DataGridView> columns are automatically created for each column in the data source.</span></span>  
  
- <span data-ttu-id="8ae21-121">Tworzy wiersz dla każdego wiersza widoczny w tabeli.</span><span class="sxs-lookup"><span data-stu-id="8ae21-121">Creates a row for each visible row in the table.</span></span>  
  
- <span data-ttu-id="8ae21-122">Automatycznie sortuje wierszy oparte na danych bazowych, gdy użytkownik kliknie nagłówek kolumny.</span><span class="sxs-lookup"><span data-stu-id="8ae21-122">Automatically sorts the rows based on the underlying data when the user clicks a column header.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ae21-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8ae21-123">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="8ae21-124">DataGridView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="8ae21-124">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
