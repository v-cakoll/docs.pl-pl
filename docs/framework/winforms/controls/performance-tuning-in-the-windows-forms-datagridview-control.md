---
title: Dostrajanie wydajności w formancie DataGridView formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], performance tuning
- performance [Windows Forms], DataGridView control
- performance tuning [Windows Forms], data grids
ms.assetid: 6ccbff28-a0ff-41e4-b601-61b31b61851d
ms.openlocfilehash: 97bf6f36ce029f879c3524fa92df08a483c2cb77
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536985"
---
# <a name="performance-tuning-in-the-windows-forms-datagridview-control"></a>Dostrajanie wydajności w formancie DataGridView formularzy systemu Windows
Podczas pracy z dużą ilością danych, `DataGridView` kontroli może używać dużej ilości pamięci w obciążenie, chyba że ostrożnie korzystaj. Na komputerach klienckich z ograniczoną pamięcią można uniknąć niektórych ten narzut, unikając funkcje, które mają pamięci wysokiej kosztów. Można również zarządzać niektórych lub wszystkich danych konserwacji i pobieranie zadań samodzielnie przy użyciu trybu wirtualnego w celu dostosowania użycia pamięci dla danego scenariusza.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Najlepsze praktyki dotyczące skalowania kontrolki DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 Informacje dotyczące używania `DataGridView` formantu w taki sposób, aby uniknąć kar użycia i wydajności pamięci niepotrzebnych podczas pracy z dużą ilością danych.  
  
 [Tryb wirtualny w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)  
 Informacje dotyczące używania trybu wirtualnego do uzupełnienia lub zastąpienia standardowego mechanizmu powiązania danych.  
  
 [Przewodnik: implementowanie trybu wirtualnego w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)  
 Opisuje sposób wdrożenia obsługi kilka zdarzeń w trybie wirtualnym. Również przedstawiono sposób wykonania wycofywania na poziomie wiersza i zatwierdzenie dla użytkownika.  
  
 [Implementowanie trybu wirtualnego przy użyciu ładowania danych Just-In-Time w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 Opisuje sposób ładowania danych na żądanie, co jest przydatne, jeśli masz więcej danych do wyświetlenia nie mogą być przechowywane w pamięci dostępne klienta.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Windows.Forms.DataGridView>  
 Zawiera dokumentacja referencyjna dla <xref:System.Windows.Forms.DataGridView> formantu.  
  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 Zawiera dokumentacja referencyjna dla <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 [DataGridView, kontrolka](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [Tryby wyświetlania danych w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)
