---
title: Dostrajanie wydajności w formancie DataGridView formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], performance tuning
- performance [Windows Forms], DataGridView control
- performance tuning [Windows Forms], data grids
ms.assetid: 6ccbff28-a0ff-41e4-b601-61b31b61851d
ms.openlocfilehash: d425488adb8569a48333de4f8c0312143029fbe0
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703178"
---
# <a name="performance-tuning-in-the-windows-forms-datagridview-control"></a>Dostrajanie wydajności w formancie DataGridView formularzy systemu Windows
Podczas pracy z dużymi ilościami danych, `DataGridView` kontroli może zużywać dużą ilość pamięci w koszty, chyba że ostrożne korzystanie. Na komputerach klienckich z ograniczoną ilością pamięci można uniknąć niektórych to obciążenie, unikając funkcje, które mają dużą ilość pamięci, kosztów. Można również zarządzać niektórych lub wszystkich funkcji obsługi danych i pobierania zadania samodzielnie przy użyciu trybu wirtualnego w celu dostosowania użycia pamięci dla danego scenariusza.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Najlepsze praktyki dotyczące skalowania kontrolki DataGridView formularzy Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 Opisuje sposób używania `DataGridView` formantu w taki sposób, aby uniknąć kar pamięci niepotrzebne użycia i wydajności, podczas pracy z dużymi ilościami danych.  
  
 [Tryb wirtualny w kontrolce DataGridView formularzy Windows Forms](virtual-mode-in-the-windows-forms-datagridview-control.md)  
 W tym artykule opisano sposób użycia trybu wirtualnego w celu uzupełnienia lub zastąpienia standardowego mechanizmu wiązania danych.  
  
 [Przewodnik: Implementowanie trybu wirtualnego w kontrolce DataGridView formularzy Windows Forms](implementing-virtual-mode-wf-datagridview-control.md)  
 W tym artykule opisano, jak zaimplementować obsługę dla kilku zdarzenia trybu wirtualnego. Ilustruje też sposób wdrażać wycofywania na poziomie wiersza i zatwierdzenia do edycji użytkownika.  
  
 [Implementowanie trybu wirtualnego przy użyciu ładowania danych Just-In-Time w kontrolce DataGridView formularzy Windows Forms](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 W tym artykule opisano sposób ładowania danych na żądanie, co jest przydatne, jeśli masz więcej danych do wyświetlenia, nie mogą być przechowywane w pamięci dostępne klienta.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Windows.Forms.DataGridView>  
 Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.DataGridView> kontroli.  
  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> właściwości.  
  
## <a name="see-also"></a>Zobacz także
- [DataGridView, kontrolka](datagridview-control-windows-forms.md)
- [Tryby wyświetlania danych w kontrolce DataGridView formularzy Windows Forms](data-display-modes-in-the-windows-forms-datagridview-control.md)
