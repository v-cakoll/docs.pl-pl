---
title: 'Instrukcje: ustawianie przemiennych wierszy dla kontrolki DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- ledger-like formats
- DataGridView control [Windows Forms], row style alternation
- Windows Forms, rows
- rows [Windows Forms], alternating
- data [Windows Forms], displaying
ms.assetid: 02373442-bf94-4470-9f8a-e44c4a9d5b88
ms.openlocfilehash: fb338a3616bc20542ec940db5977c4ffdab9654c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59335631"
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control-using-the-designer"></a>Instrukcje: ustawianie przemiennych wierszy dla kontrolki DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant
Dane tabelaryczne często są prezentowane w formacie jak rejestr, gdzie przemienne wiersze mają różnych kolorów tła. Ten format ułatwia użytkownikom Poinformuj komórki, które są w każdym wierszu, szczególnie w przypadku szerokich tabel, które mają wiele kolumn.  
  
 Za pomocą <xref:System.Windows.Forms.DataGridView> kontrolę, można określić dotycząca pełną styl naprzemiennych wierszach. Właściwości stylu, takich jak kolor pierwszego planu i czcionek, oprócz kolor tła, można użyć do odróżnienia przemienne wiersze. Aby uzyskać więcej informacji, zobacz [style komórki w formancie DataGridView formularzy Windows](cell-styles-in-the-windows-forms-datagridview-control.md).  
  
 Poniższa procedura wymaga **aplikacji Windows** projektu za pomocą zawierający formularz <xref:System.Windows.Forms.DataGridView> kontroli. Aby uzyskać informacje o konfigurowaniu taki projekt, zobacz [jak: Utwórz projekt aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [jak: Dodawanie formantów do formularzy Windows Forms](how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="define-styles-for-alternating-rows"></a>Zdefiniuj style przemienne wiersze  
  
1. Wybierz <xref:System.Windows.Forms.DataGridView> formantu w projektancie.  
  
2. W **właściwości** okna, kliknij przycisk oznaczony wielokropkiem (![VisualStudioEllipsesButton — zrzut ekranu](../media/vbellipsesbutton.png "vbEllipsesButton")) obok pozycji <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> właściwości.  
  
3. W **CellStyle Konstruktor —** okno dialogowe definiowania stylu przez ustawienie właściwości i używania **Podgląd** okienko, aby potwierdzić wybór. Style, które określisz są używane dla każdego wiersza wyświetlany w formancie, począwszy od drugiej.  
  
4. Aby zdefiniować style dla pozostałych wierszy, powtórz kroki 2 i 3, za pomocą <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> właściwości.  
  
    > [!NOTE]
    >  Komórki są wyświetlane przy użyciu stylów dziedziczone z wieloma właściwościami. Aby uzyskać więcej informacji na temat dziedziczenie stylów, zobacz [style komórki w formancie DataGridView formularzy Windows](cell-styles-in-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- [Style komórki w kontrolce DataGridView formularzy Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Podstawowe formatowanie i style w kontrolce DataGridView formularzy Windows Forms](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Używanie narzędzia Projektant z kontrolką DataGridView formularzy Windows Forms](using-the-designer-with-the-windows-forms-datagridview-control.md)
- [Instrukcje: Utwórz projekt aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Instrukcje: Dodawanie formantów do formularzy Windows Forms](how-to-add-controls-to-windows-forms.md)
