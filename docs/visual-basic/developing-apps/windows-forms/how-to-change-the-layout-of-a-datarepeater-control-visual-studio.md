---
title: 'Instrukcje: Zmienianie układu formantu DataRepeater (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, changing layout style
- DataRepeater, changing orientation
ms.assetid: 33aa8fd5-ac63-4bd0-ba13-8c2ab17e7824
ms.openlocfilehash: 3389daa6383444b48faab4c5383b281e44349bce
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54625604"
---
# <a name="how-to-change-the-layout-of-a-datarepeater-control-visual-studio"></a>Instrukcje: Zmienianie układu formantu DataRepeater (Visual Studio)
<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Kontrolki mogą być wyświetlane w pionie (elementy przewijania w pionie) lub w poziomie (elementy przewijania w poziomie) orientacji. Można zmienić orientację w czasie projektowania lub w czasie wykonywania, zmieniając <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> właściwości. Jeśli zmienisz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> właściwość w czasie wykonywania, możesz zmienić rozmiar <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> i zmienić położenie formantów podrzędnych.  
  
> [!NOTE]
>  Jeśli zmiana położenia kontrolki na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> w czasie wykonywania, musisz wywołać <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A> i <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A> metody na początku i końca bloku kodu, który zmienia położenie kontrolki.  
  
### <a name="to-change-the-layout-at-design-time"></a>Aby zmienić układ w czasie projektowania  
  
1.  W programie Windows Forms Designer wybierz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.  
  
    > [!NOTE]
    >  Musisz wybrać zewnętrznymi krawędziami <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> sterowania, klikając w dolnego regionu formantu nie znajduje się w prawym górnym <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> regionu.  
  
2.  W oknie właściwości ustaw <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> właściwości albo <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Vertical> lub <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>.  
  
### <a name="to-change-the-layout-at-run-time"></a>Aby zmienić układ w czasie wykonywania  
  
1.  Dodaj następujący kod do przycisku lub menu `Click` program obsługi zdarzeń:  
  
     [!code-csharp[VbPowerPacksDataRepeaterLayout#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterLayout#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_1.vb)]  
  
2.  W większości przypadków należy dodać kod, podobnie jak pokazano w sekcji z przykładowym, aby zmienić rozmiar <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> i rozmieszczanie formantów w celu dopasowania nowej orientacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak reagować na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyleChanged> zdarzeń w obsłudze zdarzeń. W tym przykładzie wymaga, że masz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu o nazwie `DataRepeater1` na formularzu oraz że jego <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> zawierać dwa <xref:System.Windows.Forms.TextBox> kontrolki o nazwie `TextBox1` i `TextBox2`.  
  
 [!code-csharp[VbPowerPacksDataRepeaterLayout#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_2.cs)]
 [!code-vb[VbPowerPacksDataRepeaterLayout#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_2.vb)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A>
- [Wprowadzenie do kontrolki DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [Rozwiązywanie problemów z kontrolką DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
- [Instrukcje: Zmienianie wyglądu formantu DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
