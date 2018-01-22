---
title: "Porady: włączanie widoku Tile w formancie ListView formularzy systemu Windows przy użyciu narzędzia Projektant"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tile view feature
- ListView control [Windows Forms], tile view
- tiling [Windows Forms], Windows Forms, controls
ms.assetid: 12f0816a-52b8-41ee-a6d9-ded3a8a5817a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 72fc1212e6e154cf3459d9ae6b94b6a8965fb151
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control-using-the-designer"></a>Porady: włączanie widoku Tile w formancie ListView formularzy systemu Windows przy użyciu narzędzia Projektant
Funkcja widoku kafelków <xref:System.Windows.Forms.ListView> kontroli umożliwia podanie visual równowagi między informacji graficznych i tekstowych. Wyświetlane dla elementu w widoku tile informacji tekstowych jest taka sama jak informacji o kolumnie zdefiniowanych w widoku szczegółów. Funkcje widoku kafelków w połączeniu z grupowania lub wstawiania oznaczyć funkcje <xref:System.Windows.Forms.ListView> formantu.  
  
 Widoku tile używa ikonę 32 x 32 i kilka wierszy tekstu, jak pokazano na poniższej ilustracji.  
  
 ![Widok sąsiadujący w formancie ListView](../../../../docs/framework/winforms/controls/media/listviewtile.gif "ListViewTile")  
  
 Widok się, że właściwości i metody umożliwiają określenie pola, które kolumny do wyświetlenia dla każdego elementu i zbiorczo kontrolować rozmiar i wyglądu wszystkich elementów w obrębie kafelka okno widoku kafelków. Dla uzyskania przejrzystości pierwszy wiersz tekstu na kafelku jest zawsze nazwę elementu; Nie można zmienić.  
  
 Poniższa procedura wymaga **aplikacji systemu Windows** projekt zawierający formularz <xref:System.Windows.Forms.ListView> formantu. Informacje o konfigurowaniu tych projektu, zobacz [jak: utworzyć projekt aplikacji systemu Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) i [porady: dodawanie formantów do formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Jest dostępna tylko w widoku tile [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] podczas wywołania aplikacji <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metody. W starszych systemach operacyjnych, dowolny kod związane z widoku tile nie obowiązuje, a <xref:System.Windows.Forms.ListView> kontrolka ma być wyświetlana w widoku dużych ikon. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.  
>   
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-set-tile-view-in-the-designer"></a>Aby ustawić widoku tile w Projektancie  
  
1.  Wybierz <xref:System.Windows.Forms.ListView> kontrolkę w formularzu.  
  
2.  W **właściwości** wybierz <xref:System.Windows.Forms.ListView.View%2A> właściwości i wybierz polecenie **Kafelek**.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ListView.TileSize%2A>  
 [Funkcje systemu Windows XP i formantów formularzy systemu Windows](http://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)  
 [ListView, kontrolka — omówienie](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
