---
title: 'Instrukcje: włączanie widoku Tile w kontrolce ListView formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- tile view feature
- ListView control [Windows Forms], tile view
- tiling [Windows Forms], Windows Forms, controls
ms.assetid: 12f0816a-52b8-41ee-a6d9-ded3a8a5817a
ms.openlocfilehash: 8a45a8a484bd373f53585b1b113a51e59b30fca2
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040364"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control-using-the-designer"></a>Instrukcje: włączanie widoku Tile w kontrolce ListView formularzy systemu Windows przy użyciu narzędzia Projektant
Funkcja widok kafelka <xref:System.Windows.Forms.ListView> kontrolki umożliwia zapewnienie balansu wizualnego między informacjami graficznymi i tekstowymi. Informacje tekstowe wyświetlane dla elementu w widoku kafelków są takie same, jak informacje o kolumnie zdefiniowane dla widoku szczegółów. Funkcje widoku kafelków w połączeniu z funkcjami grupowania lub wstawiania znaczników w <xref:System.Windows.Forms.ListView> formancie.

 Widok kafelka używa ikony 32 x 32 i kilku wierszy tekstu, jak pokazano na poniższej ilustracji.

 ![Widok kafelka w kontrolce ListView](./media/enable-tile-view-in-a-wf-listview-control-using-the-designer/tile-view-in-listview-control.gif "Wyświetlanie ikon i tekstu kafelków")

 Właściwości widoku kafelków i metody umożliwiają określenie pól kolumn, które mają być wyświetlane dla każdego elementu, oraz zbiorcze kontrolowanie rozmiaru i wyglądu wszystkich elementów w oknie widoku kafelków. Dla jasności pierwszy wiersz tekstu na kafelku jest zawsze nazwą elementu; nie można go zmienić.

 Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym <xref:System.Windows.Forms.ListView> kontrolkę. Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Utwórz projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikacji Windows Forms i [instrukcje: Dodaj formanty do Windows Forms](how-to-add-controls-to-windows-forms.md).

> [!NOTE]
> Widok kafelków jest dostępny tylko [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] wtedy, gdy aplikacja <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> wywołuje metodę. We wcześniejszych systemach operacyjnych każdy kod związany z widokiem kafelka nie ma żadnego efektu, a <xref:System.Windows.Forms.ListView> kontrolka zostanie wyświetlona w widoku dużych ikon. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.

## <a name="to-set-tile-view-in-the-designer"></a>Aby ustawić widok kafelków w projektancie

1. W programie Visual Studio zaznacz <xref:System.Windows.Forms.ListView> kontrolkę w formularzu.

2. W oknie **Właściwości** wybierz <xref:System.Windows.Forms.ListView.View%2A> właściwość, a następnie wybierz pozycję **kafelek**.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [ListView, kontrolka — omówienie](listview-control-overview-windows-forms.md)
