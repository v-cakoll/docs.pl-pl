---
title: 'Instrukcje: Włączanie widoku Tile w formancie ListView formularzy Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- tile view feature
- ListView control [Windows Forms], tile view
- tiling [Windows Forms], Windows Forms, controls
ms.assetid: 12f0816a-52b8-41ee-a6d9-ded3a8a5817a
ms.openlocfilehash: b365ada2d38f8fca97b66bb3d46b2c8e93d7cb1d
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2019
ms.locfileid: "57676242"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control-using-the-designer"></a>Instrukcje: Włączanie widoku Tile w formancie ListView formularzy Windows przy użyciu narzędzia Projektant
Funkcja widoku kafelków z <xref:System.Windows.Forms.ListView> kontroli umożliwia wizualne równowagi między informacje graficzne i tekstowe. Tekstowe informacje wyświetlane dla elementu w widoku kafelków jest taka sama jak informacji o kolumnie zdefiniowane dla widoku szczegółów. Funkcje widoku kafelków w połączeniu z grupowania lub wstawiania oznaczyć funkcji <xref:System.Windows.Forms.ListView> kontroli.  
  
 Wyświetlanie kafelka używa ikonę 32 x 32 i kilka wierszy tekstu, jak pokazano na poniższej ilustracji.  
  
 ![Widok w kontrolce ListView kafelków](./media/enable-tile-view-in-a-wf-listview-control-using-the-designer/tile-view-in-listview-control.gif "Kafelek widoku ikon i tekstu")  
  
 Kafelek służy do wyświetlania właściwości i metody umożliwiają określenie, które pola kolumny do wyświetlenia dla każdego elementu i zbiorczo kontrolowanie rozmiaru i wyglądu wszystkich elementów w obrębie okna widoku kafelków. W celu uściślenia pierwszy wiersz tekstu we fragmencie jest zawsze nazwę elementu; Nie można zmienić.  
  
 Poniższa procedura wymaga **aplikacji Windows** projektu za pomocą zawierający formularz <xref:System.Windows.Forms.ListView> kontroli. Aby uzyskać informacje o konfigurowaniu taki projekt, zobacz [jak: Utwórz projekt aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [jak: Dodawanie formantów do formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Widoku kafelków jest dostępna tylko na [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] gdy Twoja aplikacja wywołuje <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metody. W starszych systemach operacyjnych, dowolnego kodu, powiązany z widoku kafelków nie obowiązuje oraz <xref:System.Windows.Forms.ListView> kontrolka wyświetla się w Widok dużych ikon. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.  
>   
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-set-tile-view-in-the-designer"></a>Aby ustawić widoku tile w Projektancie  
  
1.  Wybierz <xref:System.Windows.Forms.ListView> kontrolkę w formularzu.  
  
2.  W **właściwości** wybierz <xref:System.Windows.Forms.ListView.View%2A> właściwości i wybierz polecenie **Kafelek**.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [ListView, kontrolka — omówienie](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
