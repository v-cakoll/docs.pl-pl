---
title: 'Porady: wyświetlanie nagłówków elementów w formancie DataRepeater (Visual Studio)'
ms.date: 07/20/2015
helpviewer_keywords:
- DataRepeater, item headers
- DataRepeater, selection indicators
ms.assetid: 37321447-0ffa-43e1-bdc9-0480e392b90f
ms.openlocfilehash: 07f6a7e06c5b1e91597ab6b6d816407a2c172278
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-display-item-headers-in-a-datarepeater-control-visual-studio"></a>Porady: wyświetlanie nagłówków elementów w formancie DataRepeater (Visual Studio)
Nagłówek elementu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontrola zapewnia wizualne wskaźnika podczas <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> jest zaznaczone. Gdy <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> właściwość jest ustawiona na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Vertical> (domyślnie), nagłówek elementu jest wyświetlany z lewej strony każdego elementu. Gdy <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> właściwość jest ustawiona na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>, nagłówek elementu jest wyświetlany w górnej części każdego elementu.  
  
 Gdy pierwszy jest zaznaczona, nagłówek elementu jest wyświetlane w kolorze określonym przez <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> właściwości i ikonę strzałki białe są wyświetlane.  
  
> [!NOTE]
>  Jeśli ustawisz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> do <xref:System.Drawing.Color.White%2A>, symbol zaznaczenia nie będą widoczne, gdy najpierw jest zaznaczony element.  
  
 Pola w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> ma fokus, kolor zmiany nagłówka elementu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> koloru i zmiany ikonę strzałki na kolor czarny w tle. Jeśli dane są zmieniane, symbol ołówka jest wyświetlany w nagłówku elementu.  
  
 Domyślna szerokość (lub wysokość podczas <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> właściwość jest ustawiona na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>) elementu nagłówek jest 15 pikseli. Szerokość można zmienić, określając <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> właściwości.  
  
> [!NOTE]
>  Jeśli <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> właściwość jest ustawiona na wartość, która jest mniejsza niż 11, symbole wskaźnika nagłówka elementu nie będą wyświetlane.  
  
 Nagłówki elementów można ukryć, ustawiając <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> właściwości **False**. Gdy <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> ustawiono **False**, jedyną reakcją, że element jest zaznaczony jest przerywana linia na obwodzie <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.  
  
> [!NOTE]
>  Można też podać wskaźnika zaznaczenia przez monitorowanie <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A> właściwość <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> zdarzenie <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>.  
  
### <a name="to-change-the-appearance-of-item-headers"></a>Aby zmienić wygląd nagłówków elementów  
  
1.  W narzędziu Projektant dla formularzy systemu Windows wybierz region niższe <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.  
  
    > [!NOTE]
    >  Należy wybrać region na dole formantu. W przypadku wybrania sekcji szablonu elementu inny zestaw właściwości zostaną wyświetlone w oknie właściwości.  
  
2.  W oknie właściwości użyj <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> właściwości, aby zmienić kolor nagłówków elementów.  
  
    > [!NOTE]
    >  Jeśli ustawisz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> do <xref:System.Drawing.Color.White%2A>, symbol zaznaczenia nie będą widoczne, gdy najpierw jest zaznaczony element.  
  
3.  Użyj <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> właściwości do zmiany szerokości (lub wysokości) nagłówków elementów.  
  
    > [!NOTE]
    >  Jeśli <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> właściwość jest ustawiona na wartość, która jest mniejsza niż 11, symbole wskaźnika nagłówka elementu nie będą wyświetlane.  
  
### <a name="to-hide-item-headers"></a>Aby ukryć nagłówków elementów  
  
1.  W narzędziu Projektant dla formularzy systemu Windows wybierz region niższe <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.  
  
    > [!NOTE]
    >  Należy wybrać region na dole formantu. W przypadku wybrania sekcji szablonu elementu inny zestaw właściwości zostaną wyświetlone w oknie właściwości.  
  
2.  W oknie właściwości ustaw <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> właściwości **False**.  
  
     Gdy element <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> jest zaznaczone, jedyną reakcją będzie przerywana linia na obwodzie <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [Wprowadzenie do kontrolki DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Instrukcje: zmienianie wyglądu kontrolki DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [Instrukcje: zmienianie układu kontrolki DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)  
 [Rozwiązywanie problemów z kontrolką DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
