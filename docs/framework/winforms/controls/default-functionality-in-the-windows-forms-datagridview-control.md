---
title: "Funkcje domyślne w formancie DataGridView formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data grids [Windows Forms], default functionality in DataGridView control
- DataGridView control [Windows Forms], default functionality
ms.assetid: 4405f697-cad1-4839-9bcd-8ddb09d9f00e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ecb8cdaa4e8eb0498259c597e0de3f80c3106549
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="default-functionality-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="5bc1d-102">Funkcje domyślne w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="5bc1d-102">Default Functionality in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="5bc1d-103">Formularze systemu Windows <xref:System.Windows.Forms.DataGridView> kontroli udostępnia użytkownikom znaczną ilość domyślna funkcjonalność.</span><span class="sxs-lookup"><span data-stu-id="5bc1d-103">The Windows Forms <xref:System.Windows.Forms.DataGridView> control provides users with a significant amount of default functionality.</span></span>  
  
## <a name="default-functionality"></a><span data-ttu-id="5bc1d-104">Domyślna funkcjonalność</span><span class="sxs-lookup"><span data-stu-id="5bc1d-104">Default Functionality</span></span>  
 <span data-ttu-id="5bc1d-105">Domyślnie <xref:System.Windows.Forms.DataGridView> sterowania:</span><span class="sxs-lookup"><span data-stu-id="5bc1d-105">By default, a <xref:System.Windows.Forms.DataGridView> control:</span></span>  
  
-   <span data-ttu-id="5bc1d-106">Automatycznie Wyświetla nagłówki kolumn i nagłówki wierszy, które są widoczne jako tabeli Przewija w pionie.</span><span class="sxs-lookup"><span data-stu-id="5bc1d-106">Automatically displays column headers and row headers that remain visible as the table scrolls vertically.</span></span>  
  
-   <span data-ttu-id="5bc1d-107">Zawiera nagłówek zawierający wskaźnik wybór dla bieżącego wiersza.</span><span class="sxs-lookup"><span data-stu-id="5bc1d-107">Has a row header that contains a selection indicator for the current row.</span></span>  
  
-   <span data-ttu-id="5bc1d-108">Ma prostokąta zaznaczenia w pierwszej komórki.</span><span class="sxs-lookup"><span data-stu-id="5bc1d-108">Has a selection rectangle in the first cell.</span></span>  
  
-   <span data-ttu-id="5bc1d-109">Zawiera kolumny, które można automatycznie dopasowane, gdy użytkownik kliknie dwukrotnie separator kolumn.</span><span class="sxs-lookup"><span data-stu-id="5bc1d-109">Has columns that can be automatically resized when the user double-clicks the column dividers.</span></span>  
  
-   <span data-ttu-id="5bc1d-110">Automatycznie obsługuje style wizualne w systemie Windows XP i z rodziny Windows Server 2003 podczas <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metoda jest wywoływana z poziomu aplikacji `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="5bc1d-110">Automatically supports visual styles on Windows XP and the Windows Server 2003 family when the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method is called from the application's `Main` method.</span></span>  
  
 <span data-ttu-id="5bc1d-111">Ponadto zawartość <xref:System.Windows.Forms.DataGridView> domyślnie można edytować kontrolki:</span><span class="sxs-lookup"><span data-stu-id="5bc1d-111">Additionally, the contents of a <xref:System.Windows.Forms.DataGridView> control can be edited by default:</span></span>  
  
-   <span data-ttu-id="5bc1d-112">Jeśli użytkownik kliknie dwukrotnie lub naciśnie klawisz F2 w komórce, formantu umieszcza komórki w trybie edycji i automatycznie aktualizuje zawartość komórki jako typy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5bc1d-112">If the user double-clicks or presses F2 in a cell, the control automatically puts the cell into edit mode and updates the contents of the cell as the user types.</span></span>  
  
-   <span data-ttu-id="5bc1d-113">Jeśli użytkownik przewija widok w celu siatki, użytkownik zobaczy, czy wiersz dodawania nowych rekordów jest obecny.</span><span class="sxs-lookup"><span data-stu-id="5bc1d-113">If the user scrolls to the end of the grid, the user will see that a row for adding new records is present.</span></span> <span data-ttu-id="5bc1d-114">Jeśli użytkownik kliknie ten wiersz, jest dodawany nowy wiersz <xref:System.Windows.Forms.DataGridView> kontroli z wartościami domyślnymi.</span><span class="sxs-lookup"><span data-stu-id="5bc1d-114">When the user clicks this row, a new row is added to the <xref:System.Windows.Forms.DataGridView> control, with default values.</span></span> <span data-ttu-id="5bc1d-115">Gdy użytkownik naciśnie klawisz ESC, zniknie tego nowego wiersza.</span><span class="sxs-lookup"><span data-stu-id="5bc1d-115">When the user presses ESC, this new row disappears.</span></span>  
  
-   <span data-ttu-id="5bc1d-116">Gdy użytkownik kliknie nagłówek, cały wiersz jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="5bc1d-116">If the user clicks a row header, the whole row is selected.</span></span>  
  
 <span data-ttu-id="5bc1d-117">Po powiązaniu <xref:System.Windows.Forms.DataGridView> formantu ze źródłem danych, ustawiając jego <xref:System.Windows.Forms.DataGridView.DataSource%2A> właściwości, formant:</span><span class="sxs-lookup"><span data-stu-id="5bc1d-117">When you bind a <xref:System.Windows.Forms.DataGridView> control to a data source by setting its <xref:System.Windows.Forms.DataGridView.DataSource%2A> property, the control:</span></span>  
  
-   <span data-ttu-id="5bc1d-118">Automatycznie używa nazwy kolumn źródła danych jako tekst nagłówka kolumny.</span><span class="sxs-lookup"><span data-stu-id="5bc1d-118">Automatically uses the names of the data source's columns as the column header text.</span></span>  
  
-   <span data-ttu-id="5bc1d-119">Jest wypełniana zawartość źródła danych.</span><span class="sxs-lookup"><span data-stu-id="5bc1d-119">Is populated with the contents of the data source.</span></span> <span data-ttu-id="5bc1d-120"><xref:System.Windows.Forms.DataGridView>kolumny są tworzone automatycznie dla każdej kolumny w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="5bc1d-120"><xref:System.Windows.Forms.DataGridView> columns are automatically created for each column in the data source.</span></span>  
  
-   <span data-ttu-id="5bc1d-121">Tworzy wiersz dla każdego wiersza widoczny w tabeli.</span><span class="sxs-lookup"><span data-stu-id="5bc1d-121">Creates a row for each visible row in the table.</span></span>  
  
-   <span data-ttu-id="5bc1d-122">Automatycznie sortuje wiersze oparte na danych, gdy użytkownik kliknie nagłówek kolumny.</span><span class="sxs-lookup"><span data-stu-id="5bc1d-122">Automatically sorts the rows based on the underlying data when the user clicks a column header.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bc1d-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5bc1d-123">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="5bc1d-124">DataGridView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="5bc1d-124">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
