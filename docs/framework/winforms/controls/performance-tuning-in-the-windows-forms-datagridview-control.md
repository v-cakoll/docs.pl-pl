---
title: "Dostrajanie wydajności w formancie DataGridView formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], performance tuning
- performance [Windows Forms], DataGridView control
- performance tuning [Windows Forms], data grids
ms.assetid: 6ccbff28-a0ff-41e4-b601-61b31b61851d
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 452c55d38a896ec96e0992a4b9826f08dc4caa0e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="performance-tuning-in-the-windows-forms-datagridview-control"></a>Dostrajanie wydajności w formancie DataGridView formularzy systemu Windows
Podczas pracy z dużą ilością danych, `DataGridView` kontroli może używać dużej ilości pamięci w obciążenie, chyba że ostrożnie korzystaj. Na komputerach klienckich z ograniczoną pamięcią można uniknąć niektórych ten narzut, unikając funkcje, które mają pamięci wysokiej kosztów. Można również zarządzać niektórych lub wszystkich danych konserwacji i pobieranie zadań samodzielnie przy użyciu trybu wirtualnego w celu dostosowania użycia pamięci dla danego scenariusza.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Najlepsze praktyki dotyczące skalowania formantu DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 Informacje dotyczące używania `DataGridView` formantu w taki sposób, aby uniknąć kar użycia i wydajności pamięci niepotrzebnych podczas pracy z dużą ilością danych.  
  
 [Tryb wirtualny w systemie Windows do formantu DataGridView formularzy](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)  
 Informacje dotyczące używania trybu wirtualnego do uzupełnienia lub zastąpienia standardowego mechanizmu powiązania danych.  
  
 [Wskazówki: Implementowanie trybu wirtualnego w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)  
 Opisuje sposób wdrożenia obsługi kilka zdarzeń w trybie wirtualnym. Również przedstawiono sposób wykonania wycofywania na poziomie wiersza i zatwierdzenie dla użytkownika.  
  
 [Implementowanie trybu wirtualnego przy użyciu w czasie ładowania danych w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 Opisuje sposób ładowania danych na żądanie, co jest przydatne, jeśli masz więcej danych do wyświetlenia nie mogą być przechowywane w pamięci dostępne klienta.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Windows.Forms.DataGridView>  
 Zawiera dokumentacja referencyjna dla <xref:System.Windows.Forms.DataGridView> formantu.  
  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 Zawiera dokumentacja referencyjna dla <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 [DataGridView — formant](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [Tryby wyświetlania danych w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)
