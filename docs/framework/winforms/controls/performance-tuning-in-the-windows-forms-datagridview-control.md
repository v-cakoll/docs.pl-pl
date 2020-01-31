---
title: Dostrajanie wydajności w formancie DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], performance tuning
- performance [Windows Forms], DataGridView control
- performance tuning [Windows Forms], data grids
ms.assetid: 6ccbff28-a0ff-41e4-b601-61b31b61851d
ms.openlocfilehash: 77ad86c4cd606bcf074473c97371ec27bcc5605b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744278"
---
# <a name="performance-tuning-in-the-windows-forms-datagridview-control"></a>Dostrajanie wydajności w formancie DataGridView formularzy systemu Windows
Podczas pracy z dużymi ilościami danych kontrolka `DataGridView` może zużywać dużą ilość pamięci, chyba że jest używana uważnie. Na klientach z ograniczoną ilością pamięci można uniknąć niektórych obciążeń, unikając funkcji mających koszt dużej ilości pamięci. Możesz również zarządzać niektórymi lub wszystkimi zadaniami konserwacji i pobierania danych samodzielnie przy użyciu trybu wirtualnego, aby dostosować użycie pamięci dla danego scenariusza.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Najlepsze praktyki dotyczące skalowania kontrolki DataGridView formularzy Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 Opisuje sposób używania kontrolki `DataGridView` w sposób, który pozwala uniknąć niepotrzebnego użycia pamięci i kar wydajności podczas pracy z dużymi ilościami danych.  
  
 [Tryb wirtualny w kontrolce DataGridView formularzy Windows Forms](virtual-mode-in-the-windows-forms-datagridview-control.md)  
 Opisuje, jak używać trybu wirtualnego do uzupełniania lub zastępowania standardowego mechanizmu powiązania danych.  
  
 [Przewodnik: implementowanie trybu wirtualnego w kontrolce DataGridView formularzy Windows Forms](implementing-virtual-mode-wf-datagridview-control.md)  
 Opisuje sposób wdrażania programów obsługi dla kilku zdarzeń w trybie wirtualnym. Ilustruje także sposób implementacji wycofywania i zatwierdzania na poziomie wierszy na potrzeby edycji użytkowników.  
  
 [Implementowanie trybu wirtualnego przy użyciu ładowania danych Just-In-Time w kontrolce DataGridView formularzy Windows Forms](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 Opisuje sposób ładowania danych na żądanie, co jest przydatne, gdy masz więcej danych do wyświetlenia niż dostępna pamięć klienta może być przechowywana.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Windows.Forms.DataGridView>  
 Zawiera dokumentację referencyjną dla kontrolki <xref:System.Windows.Forms.DataGridView>.  
  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 Zawiera dokumentację referencyjną dla właściwości <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>.  
  
## <a name="see-also"></a>Zobacz także

- [DataGridView, kontrolka](datagridview-control-windows-forms.md)
- [Tryby wyświetlania danych w kontrolce DataGridView formularzy Windows Forms](data-display-modes-in-the-windows-forms-datagridview-control.md)
