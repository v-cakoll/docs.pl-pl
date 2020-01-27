---
title: Włącz widok kafelków w formancie ListView przy użyciu narzędzia Projektant
ms.date: 03/30/2017
helpviewer_keywords:
- tile view feature
- ListView control [Windows Forms], tile view
- tiling [Windows Forms], Windows Forms, controls
ms.assetid: 12f0816a-52b8-41ee-a6d9-ded3a8a5817a
ms.openlocfilehash: a0429efaab14995ab1e3f3b0dfd91db61de72fbf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745805"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control-using-the-designer"></a>Porady: włączanie widoku Tile w formancie ListView formularzy systemu Windows przy użyciu narzędzia Projektant
Funkcja widok kafelka kontrolki <xref:System.Windows.Forms.ListView> umożliwia zapewnienie równowagi wizualnej między informacjami graficznymi i tekstowymi. Informacje tekstowe wyświetlane dla elementu w widoku kafelków są takie same, jak informacje o kolumnie zdefiniowane dla widoku szczegółów. Funkcje widoku kafelków w połączeniu z funkcjami grupowania lub wstawiania znaczników w kontrolce <xref:System.Windows.Forms.ListView>.

 Widok kafelka używa ikony 32 x 32 i kilku wierszy tekstu, jak pokazano na poniższej ilustracji.

 ![Widok kafelka w kontrolce ListView](./media/enable-tile-view-in-a-wf-listview-control-using-the-designer/tile-view-in-listview-control.gif "Wyświetlanie ikon i tekstu kafelków")

 Właściwości widoku kafelków i metody umożliwiają określenie pól kolumn, które mają być wyświetlane dla każdego elementu, oraz zbiorcze kontrolowanie rozmiaru i wyglądu wszystkich elementów w oknie widoku kafelków. Dla jasności pierwszy wiersz tekstu na kafelku jest zawsze nazwą elementu; nie można go zmienić.

 Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym formant <xref:System.Windows.Forms.ListView>. Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Create a Windows Forms Project Application](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [How to: Add controls to Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="to-set-tile-view-in-the-designer"></a>Aby ustawić widok kafelków w projektancie

1. W programie Visual Studio Wybierz kontrolkę <xref:System.Windows.Forms.ListView> w formularzu.

2. W oknie **Właściwości** wybierz właściwość <xref:System.Windows.Forms.ListView.View%2A> i wybierz pozycję **kafelek**.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [ListView, kontrolka — omówienie](listview-control-overview-windows-forms.md)
