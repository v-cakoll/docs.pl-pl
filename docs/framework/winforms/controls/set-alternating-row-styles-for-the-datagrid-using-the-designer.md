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
ms.openlocfilehash: 1be746d4cce36344e034692a0e2e8e6a9e9320d5
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040438"
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control-using-the-designer"></a>Instrukcje: ustawianie przemiennych wierszy dla kontrolki DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant

Dane tabelaryczne często są prezentowane w formacie podobnym do księgi, w którym przemienne wiersze mają różne kolory tła. Ten format ułatwia użytkownikom informowanie, które komórki znajdują się w każdym wierszu, szczególnie w przypadku szerokich tabel z wieloma kolumnami.

Za pomocą <xref:System.Windows.Forms.DataGridView> kontrolki można określić pełne informacje o stylu dla przemiennych wierszy. Możesz użyć cech stylu, takich jak kolor i czcionka pierwszego planu, oprócz koloru tła w celu odróżnienia przemiennych wierszy. Aby uzyskać więcej informacji, zobacz [style komórek w kontrolce DataGridView Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).

Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym <xref:System.Windows.Forms.DataGridView> kontrolkę. Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Utwórz projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikacji Windows Forms i [instrukcje: Dodaj formanty do Windows Forms](how-to-add-controls-to-windows-forms.md).


### <a name="define-styles-for-alternating-rows"></a>Definiowanie stylów dla przemiennych wierszy

1. <xref:System.Windows.Forms.DataGridView> Wybierz kontrolkę w projektancie.

2. W oknie **Właściwości** kliknij przycisk wielokropka (![przycisk wielokropka (...) w okno właściwości programu Visual Studio.](./media/visual-studio-ellipsis-button.png)) obok <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> właściwości.

3. W oknie dialogowym **Konstruktor komórek** Zdefiniuj styl, ustawiając właściwości, a następnie użyj okienka **podglądu** , aby potwierdzić wybór. Określone style są używane dla każdego innego wiersza wyświetlanego w kontrolce, rozpoczynając od drugiego.

4. Aby zdefiniować Style dla pozostałych wierszy, powtórz kroki 2 i 3 przy użyciu <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> właściwości.

    > [!NOTE]
    > Komórki są wyświetlane przy użyciu stylów dziedziczonych z wielu właściwości. Aby uzyskać więcej informacji na temat dziedziczenia stylu, zobacz [style komórek w kontrolce DataGridView Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- [Style komórki w kontrolce DataGridView formularzy Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Podstawowe formatowanie i style w kontrolce DataGridView formularzy Windows Forms](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Używanie narzędzia Projektant z kontrolką DataGridView formularzy Windows Forms](using-the-designer-with-the-windows-forms-datagridview-control.md)
- [Instrukcje: Tworzenie projektu aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Instrukcje: Dodawanie formantów do Windows Forms](how-to-add-controls-to-windows-forms.md)
