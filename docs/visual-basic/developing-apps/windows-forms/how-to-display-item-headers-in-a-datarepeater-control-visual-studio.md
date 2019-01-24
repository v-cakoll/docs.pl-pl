---
title: 'Instrukcje: Wyświetlanie nagłówków elementów w formancie DataRepeater (Visual Studio)'
ms.date: 07/20/2015
helpviewer_keywords:
- DataRepeater, item headers
- DataRepeater, selection indicators
ms.assetid: 37321447-0ffa-43e1-bdc9-0480e392b90f
ms.openlocfilehash: eccac1b3b02da41a34d47072be267f6c51a7d490
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54504564"
---
# <a name="how-to-display-item-headers-in-a-datarepeater-control-visual-studio"></a>Instrukcje: Wyświetlanie nagłówków elementów w formancie DataRepeater (Visual Studio)
Element nagłówka w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control oferuje wizualny wskaźnik informujący podczas <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> jest zaznaczone. Gdy <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> właściwość jest ustawiona na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Vertical> (ustawienie domyślne), nagłówek elementu jest wyświetlany na lewo od każdego elementu. Gdy <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> właściwość jest ustawiona na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>, nagłówek elementu jest wyświetlany w górnej części każdego elementu.  
  
 Jeśli najpierw wybrano, nagłówek elementu jest wyświetlany kolor, który jest określony przez <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> wyświetlane są właściwości i ikona biały strzałek.  
  
> [!NOTE]
>  Jeśli ustawisz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> do <xref:System.Drawing.Color.White%2A>, symbol zaznaczenia nie będą widoczne po wybraniu elementu.  
  
 Gdy pole w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> ma fokus, kolor elementu nagłówka zmiany w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> w tle koloru i zmiany ikony strzałki na czarny. Jeśli dane są zmieniane, symbol ołówka jest wyświetlany w nagłówku elementu.  
  
 Domyślna szerokość (lub wysokość podczas <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> właściwość jest ustawiona na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>) elementu nagłówka to 15 pikseli. Możesz zmienić szerokość, ustawiając <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> właściwości.  
  
> [!NOTE]
>  Jeśli <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> właściwość jest ustawiona na wartość, która jest mniejsza niż 11, symbole wskaźników w nagłówku elementu nie będą wyświetlane.  
  
 Nagłówki elementów można ukryć, ustawiając <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> właściwości **False**. Gdy <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> ustawiono **False**, jedyną reakcją, czy element jest wybrany jest linia kropkowana na obwodzie <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.  
  
> [!NOTE]
>  Możesz też podać Wskaźnik zaznaczenia, monitorując <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A> właściwość <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> zdarzenia <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>.  
  
### <a name="to-change-the-appearance-of-item-headers"></a>Aby zmienić wygląd nagłówki elementów  
  
1.  W programie Windows Forms Designer wybierz dolnego regionu z <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.  
  
    > [!NOTE]
    >  Musisz wybrać dolnego regionu formantu. Po wybraniu sekcji szablon elementu inny zestaw właściwości będą wyświetlane w oknie dialogowym właściwości.  
  
2.  W oknie dialogowym właściwości użyj <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> właściwości, aby zmienić kolor nagłówki elementów.  
  
    > [!NOTE]
    >  Jeśli ustawisz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> do <xref:System.Drawing.Color.White%2A>, symbol zaznaczenia nie będą widoczne po wybraniu elementu.  
  
3.  Użyj <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> właściwości, aby zmienić szerokość (lub wysokość) nagłówki elementów.  
  
    > [!NOTE]
    >  Jeśli <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> właściwość jest ustawiona na wartość, która jest mniejsza niż 11, symbole wskaźników w nagłówku elementu nie będą wyświetlane.  
  
### <a name="to-hide-item-headers"></a>Aby ukryć nagłówki elementów  
  
1.  W programie Windows Forms Designer wybierz dolnego regionu z <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.  
  
    > [!NOTE]
    >  Musisz wybrać dolnego regionu formantu. Po wybraniu sekcji szablon elementu inny zestaw właściwości będą wyświetlane w oknie dialogowym właściwości.  
  
2.  W oknie właściwości ustaw <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> właściwości **False**.  
  
     Gdy element <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> jest zaznaczone, jedyną reakcją będzie linia kropkowana na obwodzie <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.  
  
## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>
- [Wprowadzenie do kontrolki DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [Instrukcje: Zmienianie wyglądu formantu DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
- [Instrukcje: Zmienianie układu formantu DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)
- [Rozwiązywanie problemów z kontrolką DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
