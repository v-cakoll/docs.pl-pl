---
title: 'Porady: ustawianie przemiennych wierszy dla formantu DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- ledger-like formats
- DataGridView control [Windows Forms], row style alternation
- Windows Forms, rows
- rows [Windows Forms], alternating
- data [Windows Forms], displaying
ms.assetid: 02373442-bf94-4470-9f8a-e44c4a9d5b88
ms.openlocfilehash: 5807df6d11580c22f2b754faf44fb3aa63dee14e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43538857"
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control-using-the-designer"></a>Porady: ustawianie przemiennych wierszy dla formantu DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant
Dane tabelaryczne często są prezentowane w formacie jak rejestr, gdzie przemienne wiersze mają różnych kolorów tła. Ten format ułatwia użytkownikom Poinformuj komórki, które są w każdym wierszu, szczególnie w przypadku szerokich tabel, które mają wiele kolumn.  
  
 Za pomocą <xref:System.Windows.Forms.DataGridView> kontrolę, można określić dotycząca pełną styl naprzemiennych wierszach. Właściwości stylu, takich jak kolor pierwszego planu i czcionek, oprócz kolor tła, można użyć do odróżnienia przemienne wiersze. Aby uzyskać więcej informacji, zobacz [style komórki w formancie DataGridView formularzy Windows](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).  
  
 Poniższa procedura wymaga **aplikacji Windows** projektu za pomocą zawierający formularz <xref:System.Windows.Forms.DataGridView> kontroli. Uzyskać informacji o konfigurowaniu taki projekt, zobacz [jak: Tworzenie projektu aplikacji Windows](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) i [porady: dodawanie formantów do formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="define-styles-for-alternating-rows"></a>Zdefiniuj style przemienne wiersze  
  
1.  Wybierz <xref:System.Windows.Forms.DataGridView> formantu w projektancie.  
  
2.  W **właściwości** okna, kliknij przycisk oznaczony wielokropkiem (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) obok pozycji <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> właściwości.  
  
3.  W **CellStyle Konstruktor —** okno dialogowe definiowania stylu przez ustawienie właściwości i używania **Podgląd** okienko, aby potwierdzić wybór. Style, które określisz są używane dla każdego wiersza wyświetlany w formancie, począwszy od drugiej.  
  
4.  Aby zdefiniować style dla pozostałych wierszy, powtórz kroki 2 i 3, za pomocą <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> właściwości.  
  
    > [!NOTE]
    >  Komórki są wyświetlane przy użyciu stylów dziedziczone z wieloma właściwościami. Aby uzyskać więcej informacji na temat dziedziczenie stylów, zobacz [style komórki w formancie DataGridView formularzy Windows](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 [Style komórki w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [Podstawowe formatowanie i style w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [Używanie narzędzia Projektant z kontrolką DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/using-the-designer-with-the-windows-forms-datagridview-control.md)  
 [Porady: Tworzenie projektu aplikacji Windows](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [Instrukcje: dodawanie kontrolek do formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
