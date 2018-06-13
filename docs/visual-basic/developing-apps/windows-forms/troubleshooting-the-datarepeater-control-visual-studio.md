---
title: Rozwiązywanie problemów z formantem DataRepeater (Visual Studio)
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, troubleshooting
ms.assetid: c0ab9469-eced-4f52-aa18-4bd8dd4f1a9a
ms.openlocfilehash: 092bbe89bb73a40dee7161f014d40a581b0ddc06
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591901"
---
# <a name="troubleshooting-the-datarepeater-control-visual-studio"></a>Rozwiązywanie problemów z formantem DataRepeater (Visual Studio)
Ten temat zawiera listę typowych problemów, które mogą wystąpić podczas pracy z <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.  
  
## <a name="datarepeater-keyboard-and-mouse-events-are-not-raised"></a>DataRepeater klawiatury i myszy zdarzenia nie są wywoływane.  
 Niektóre <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> zdarzeń kontrolowania, takich jak zdarzenia klawiatury i myszy, nie są zgłaszane. To jest celowe. <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Sam formant jest kontenerem dla <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> obiektów i nie są dostępne w czasie wykonywania. <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> Nie ujawnia zdarzenia w czasie projektowania. W związku z tym elementu kliknięcie lub naciśnięcie klawisza, gdy element ma fokus nie wygenerował zdarzenie.  
  
 Wyjątkiem jest, gdy <xref:System.Windows.Forms.Control.Padding%2A> właściwość jest ustawiona na dużej wystarczającej liczby wartości do udostępnienia krawędzi <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu. W takim przypadku kliknięcie na marginesie narażonych zgłosi zdarzeń myszy.  
  
 Aby rozwiązać ten problem, Dodaj <xref:System.Windows.Forms.Panel> formant <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> sekcji <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli, a następnie Dodaj pozostałe formanty <xref:System.Windows.Forms.Panel>. Następnie można dodać kod, aby <xref:System.Windows.Forms.Panel> formantu obsługi zdarzeń dla zdarzenia klawiatury i myszy.  
  
## <a name="the-datarepeater-is-partially-hidden-behind-the-binding-navigator"></a>DataRepeater częściowo będzie Zasłaniana przez nawigatora powiązania  
 Po dodaniu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> sterowania do formularza, a następnie dodaj formanty powiązane z danymi z **źródeł danych** okna, <xref:System.Windows.Forms.BindingNavigator> sterowania może pojawić się nad <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu. Jest to znane ograniczenie **źródeł danych** okna i jest zgodna z zachowaniem inne formanty, takie jak <xref:System.Windows.Forms.DataGridView> formantu.  
  
 Można albo przenieś <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> niższa niż <xref:System.Windows.Forms.BindingNavigator> kontroli w czasie projektowania, lub Dodaj kod podobne do następującego `Load` obsługi zdarzeń.  
  
```vb  
DataRepeater1.Top = ProductsBindingNavigator.Height  
```  
  
```csharp  
dataRepeater1.Top = productsBindingNavigator.Height;  
```  
  
## <a name="controls-are-not-displayed-correctly-at-run-time"></a>Formanty nie są wyświetlane poprawnie w czasie wykonywania  
 Niektóre formanty w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli mogą nie być wyświetlane zgodnie z oczekiwaniami w czasie wykonywania. Proces używany do klonowania formantów z <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> zawsze nie można określić właściwości wszystkich kontrolek. Na przykład, jeśli dodasz niezwiązanego <xref:System.Windows.Forms.ListBox> formant <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli w czasie projektowania i wypełnić jego <xref:System.Windows.Forms.ListBox.Items%2A> kolekcji z listą parametrów, <xref:System.Windows.Forms.ListBox> będzie pusty w czasie wykonywania. Wynika to z faktu w klonowania nie można uwzględniać <xref:System.Windows.Forms.ListBox.Items%2A> właściwości.  
  
 Możesz rozwiązać problemów, takich jak ta, przywracanie Brak właściwości w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemCloned> zdarzenie, które występuje po ukończeniu klonowania domyślne. W poniższym przykładzie pokazano sposób naprawić <xref:System.Windows.Forms.ListBox.Items%2A> Kolekcja <xref:System.Windows.Forms.ListBox> kontroli w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemCloned> obsługi zdarzeń.  
  
 [!code-csharp[VbPowerPacksDataRepeaterItemCloned#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/troubleshooting-the-datarepeater-control-visual-studio_1.cs)]
 [!code-vb[VbPowerPacksDataRepeaterItemCloned#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/troubleshooting-the-datarepeater-control-visual-studio_1.vb)]  
  
## <a name="the-selection-symbol-on-the-item-header-is-missing"></a>Brakuje symbolu zaznaczenia w nagłówku elementu  
 Po zmianie <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> właściwości nagłówka elementu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli, niektóre kolorów może spowodować znikają symbol zaznaczenia. Zmiana <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> właściwości może także powodować znikają symbol zaznaczenia.  
  
 Nie można zmienić kolor i rozmiar symbolu zaznaczenia.  
  
-   Jeśli ustawisz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> do <xref:System.Drawing.Color.White%2A>, symbol zaznaczenia nie będą widoczne w przypadku wybrania elementu.  
  
-   Jeśli ustawisz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> do <xref:System.Drawing.Color.Black%2A>, symbol zaznaczenia nie będą widoczne, gdy formant jest zaznaczone, a symbol ołówka nie będą widoczne, gdy formant jest w trybie edycji.  
  
-   Jeśli <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> właściwość jest ustawiona na wartość, która jest mniejsza niż 11, symbole wskaźnika nagłówka elementu nie będą wyświetlane.  
  
 Możesz podać własne symbol nagłówka i Wybieranie elementu za pomocą <xref:System.Windows.Forms.PictureBox> kontroli i monitorowania <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A> właściwość <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> zdarzenie <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do kontrolki DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Instrukcje: wyświetlanie powiązanych danych w kontrolce DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [Instrukcje: wyświetlanie niepowiązanych kontrolek w kontrolce DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)  
 [Instrukcje: zmienianie układu kontrolki DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)  
 [Instrukcje: zmienianie wyglądu kontrolki DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [Instrukcje: wyświetlanie nagłówków elementów w kontrolce DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)  
 [Instrukcje: wyłączanie dodawania i usuwania elementów DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md)  
 [Instrukcje: wyszukiwanie danych w kontrolce DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md)  
 [Porady: Tworzenie formularza wzorzec/szczegół za pomocą dwóch formantów DataRepeater (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)
