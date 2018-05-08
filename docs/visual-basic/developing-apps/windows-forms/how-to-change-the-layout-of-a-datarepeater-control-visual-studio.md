---
title: 'Porady: zmienianie układu formantu DataRepeater (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, changing layout style
- DataRepeater, changing orientation
ms.assetid: 33aa8fd5-ac63-4bd0-ba13-8c2ab17e7824
ms.openlocfilehash: fa780ee40171143c17b5bdbda4a97179ed5f2151
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-change-the-layout-of-a-datarepeater-control-visual-studio"></a>Porady: zmienianie układu formantu DataRepeater (Visual Studio)
<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Kontroli mogą być wyświetlane w pionie (przewijania elementów w pionie) lub pozioma (elementy przewijania w poziomie) orientacji. Orientacja w czasie projektowania lub w czasie wykonywania można zmienić, zmieniając <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> właściwości. Jeśli zmienisz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> właściwości w czasie wykonywania, może również chcesz zmienić <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> i położenia formantów podrzędnych.  
  
> [!NOTE]
>  Jeśli zmiana położenia kontrolki na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> w czasie wykonywania, należy wywołać <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A> i <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A> metody na początku i na końcu bloku kodu, który zmienia położenie kontrolki.  
  
### <a name="to-change-the-layout-at-design-time"></a>Aby zmienić układ w czasie projektowania  
  
1.  W narzędziu Projektant dla formularzy systemu Windows wybierz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.  
  
    > [!NOTE]
    >  Musisz wybrać zewnętrzną krawędzią <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> sterowania, klikając w region na dole formantu, nie znajduje się w prawym górnym <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> regionu.  
  
2.  W oknie właściwości ustaw <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> właściwości albo <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Vertical> lub <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>.  
  
### <a name="to-change-the-layout-at-run-time"></a>Aby zmienić układ w czasie wykonywania  
  
1.  Dodaj następujący kod do menu lub przycisku `Click` obsługi zdarzeń:  
  
     [!code-csharp[VbPowerPacksDataRepeaterLayout#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterLayout#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_1.vb)]  
  
2.  W większości przypadków należy dodać kod, podobnie jak pokazano w sekcji przykład, aby zmienić rozmiar <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> i rozmieszczanie formantów w celu dopasowania nowej orientacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak odpowiedzieć na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyleChanged> zdarzeń w obsłudze zdarzeń. W tym przykładzie wymaga <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu o nazwie `DataRepeater1` na formularzu oraz że jego <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> zawierać dwa <xref:System.Windows.Forms.TextBox> formantów `TextBox1` i `TextBox2`.  
  
 [!code-csharp[VbPowerPacksDataRepeaterLayout#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_2.cs)]
 [!code-vb[VbPowerPacksDataRepeaterLayout#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_2.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A>  
 [Wprowadzenie do kontrolki DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Rozwiązywanie problemów z kontrolką DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [Instrukcje: zmienianie wyglądu kontrolki DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
