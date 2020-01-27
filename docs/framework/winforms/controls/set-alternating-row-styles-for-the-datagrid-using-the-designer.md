---
title: Ustawianie stylów wierszy przemiennych dla formantu DataGridView przy użyciu narzędzia Projektant
ms.date: 03/30/2017
helpviewer_keywords:
- ledger-like formats
- DataGridView control [Windows Forms], row style alternation
- Windows Forms, rows
- rows [Windows Forms], alternating
- data [Windows Forms], displaying
ms.assetid: 02373442-bf94-4470-9f8a-e44c4a9d5b88
ms.openlocfilehash: 74f65d03a359136de943f8a2937ed5e5f1e62519
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743051"
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control-using-the-designer"></a>Porady: ustawianie przemiennych wierszy dla formantu DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant

Dane tabelaryczne często są prezentowane w formacie podobnym do księgi, w którym przemienne wiersze mają różne kolory tła. Ten format ułatwia użytkownikom informowanie, które komórki znajdują się w każdym wierszu, szczególnie w przypadku szerokich tabel z wieloma kolumnami.

Za pomocą kontrolki <xref:System.Windows.Forms.DataGridView> można określić pełne informacje o stylu dla przemiennych wierszy. Możesz użyć cech stylu, takich jak kolor i czcionka pierwszego planu, oprócz koloru tła w celu odróżnienia przemiennych wierszy. Aby uzyskać więcej informacji, zobacz [style komórek w kontrolce DataGridView Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).

Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym formant <xref:System.Windows.Forms.DataGridView>. Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Create a Windows Forms Project Application](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [How to: Add controls to Windows Forms](how-to-add-controls-to-windows-forms.md).

### <a name="define-styles-for-alternating-rows"></a>Definiowanie stylów dla przemiennych wierszy

1. Wybierz kontrolkę <xref:System.Windows.Forms.DataGridView> w projektancie.

2. W oknie **Właściwości** kliknij przycisk wielokropka (![przycisk wielokropka (...) w okno właściwości programu Visual Studio.](./media/visual-studio-ellipsis-button.png)) obok właściwości <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A>.

3. W oknie dialogowym **Konstruktor komórek** Zdefiniuj styl, ustawiając właściwości, a następnie użyj okienka **podglądu** , aby potwierdzić wybór. Określone style są używane dla każdego innego wiersza wyświetlanego w kontrolce, rozpoczynając od drugiego.

4. Aby zdefiniować Style dla pozostałych wierszy, powtórz kroki 2 i 3 przy użyciu właściwości <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>.

    > [!NOTE]
    > Komórki są wyświetlane przy użyciu stylów dziedziczonych z wielu właściwości. Aby uzyskać więcej informacji na temat dziedziczenia stylu, zobacz [style komórek w kontrolce DataGridView Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- [Style komórki w kontrolce DataGridView formularzy Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Podstawowe formatowanie i style w kontrolce DataGridView formularzy Windows Forms](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Używanie narzędzia Projektant z kontrolką DataGridView formularzy Windows Forms](using-the-designer-with-the-windows-forms-datagridview-control.md)
- [Instrukcje: Tworzenie projektu aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Instrukcje: dodawanie kontrolek do formularzy Windows Forms](how-to-add-controls-to-windows-forms.md)
