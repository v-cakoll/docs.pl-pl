---
title: "Porady: ustawianie przemiennych wierszy dla formantu DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ledger-like formats
- DataGridView control [Windows Forms], row style alternation
- Windows Forms, rows
- rows [Windows Forms], alternating
- data [Windows Forms], displaying
ms.assetid: 02373442-bf94-4470-9f8a-e44c4a9d5b88
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e8d78509a7d088511096d2e02e8e6603ba5fe5c0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control-using-the-designer"></a>Porady: ustawianie przemiennych wierszy dla formantu DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant
Dane tabelaryczne często są prezentowane w księdze postaci której przemiennych wierszy mają różnych kolorów tła. Ten format ułatwia użytkownikom Poinformuj komórek, które są w każdym wierszu, szczególnie w przypadku szerokie tabele, które mają wiele kolumn.  
  
 Z <xref:System.Windows.Forms.DataGridView> sterowania, można określić informacji o pełną stylu dla wierszy zmiennych. Właściwości stylu, takich jak kolor pierwszego planu i czcionek, oprócz kolor tła, można użyć do odróżnienia przemiennych wierszy. Aby uzyskać więcej informacji, zobacz [style komórki w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).  
  
 Poniższa procedura wymaga **aplikacji systemu Windows** projekt zawierający formularz <xref:System.Windows.Forms.DataGridView> formantu. Informacje o konfigurowaniu tych projektu, zobacz [jak: utworzyć projekt aplikacji systemu Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) i [porady: dodawanie formantów do formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="define-styles-for-alternating-rows"></a>Zdefiniuj style wierszy zmiennych  
  
1.  Wybierz <xref:System.Windows.Forms.DataGridView> kontroli w projektancie.  
  
2.  W **właściwości** okna, kliknij przycisk oznaczony wielokropkiem (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) obok pozycji <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> właściwości.  
  
3.  W **konstruktora elementu CellStyle** okno dialogowe, zdefiniuj styl przez ustawienie właściwości i użyj **Podgląd** okienko, aby uzgodnić wybrane opcje. Style, które określisz są używane dla każdego wiersza wyświetlany w formancie, począwszy od drugiej.  
  
4.  Aby zdefiniować style dla pozostałych wierszy, powtórz kroki 2 i 3 przy użyciu <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> właściwości.  
  
    > [!NOTE]
    >  Komórki są wyświetlane przy użyciu stylów odziedziczone wiele właściwości. Aby uzyskać więcej informacji o stylu dziedziczenia, zobacz [style komórki w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 [Style komórki w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [Podstawowe formatowanie i style w oknach formantu DataGridView formularzy](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [Za pomocą formantu DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant](../../../../docs/framework/winforms/controls/using-the-designer-with-the-windows-forms-datagridview-control.md)  
 [Porady: Tworzenie projektu aplikacji systemu Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [Porady: dodawanie formantów do formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
