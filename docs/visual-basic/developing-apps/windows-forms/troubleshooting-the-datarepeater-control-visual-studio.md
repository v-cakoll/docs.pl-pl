---
title: Rozwiązywanie problemów z formantem DataRepeater (Visual Studio)
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, troubleshooting
ms.assetid: c0ab9469-eced-4f52-aa18-4bd8dd4f1a9a
ms.openlocfilehash: 7b045e1c45221cbde82c88286da8e698a763d844
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580606"
---
# <a name="troubleshooting-the-datarepeater-control-visual-studio"></a>Rozwiązywanie problemów z formantem DataRepeater (Visual Studio)
Ten temat zawiera listę typowych problemów, które mogą wystąpić podczas pracy z <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.  
  
## <a name="datarepeater-keyboard-and-mouse-events-are-not-raised"></a>DataRepeater klawiatury i myszy zdarzenia nie są zgłaszane.  
 Niektóre <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> zdarzenia kontrolki, takie jak zdarzenia klawiatury i myszy, nie są zgłaszane. To jest celowe. <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Sama kontrolka jest kontenerem dla <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> obiektów i nie są dostępne w czasie wykonywania. <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> Nie uwidacznia zdarzenia w czasie projektowania. W związku z tym element kliknięcie lub naciśnięcie klawisza, gdy element ma fokus nie wywołać zdarzenie.  
  
 Wyjątkiem jest, gdy <xref:System.Windows.Forms.Control.Padding%2A> zostaje ustalona dużą wystarczającej liczby wartości do udostępnienia krawędzi <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli. W tym przypadku kliknięcie marginesu narażonych zgłosi zdarzeń myszy.  
  
 Aby rozwiązać ten problem, należy dodać <xref:System.Windows.Forms.Panel> kontrolę <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> części <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> sterowania, a następnie Dodaj pozostałe formanty <xref:System.Windows.Forms.Panel>. Następnie możesz dodać kod, aby <xref:System.Windows.Forms.Panel> kontrolki obsługi zdarzeń dla zdarzenia klawiatury i myszy.  
  
## <a name="the-datarepeater-is-partially-hidden-behind-the-binding-navigator"></a>DataRepeater częściowo będzie Zasłaniana przez Nawigator powiązań  
 Po dodaniu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> sterowania do formularza, a następnie dodać formanty powiązane z danymi z **źródeł danych** oknie <xref:System.Windows.Forms.BindingNavigator> sterowania może pojawić się w górnej części <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli. Jest to znane ograniczenie **źródeł danych** okna i zgodne z zachowaniem inne formanty, takie jak <xref:System.Windows.Forms.DataGridView> kontroli.  
  
 Możesz albo przenieś <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> niższa niż <xref:System.Windows.Forms.BindingNavigator> kontroli w czasie projektowania lub Dodaj kod, podobne do następujących czynności w `Load` programu obsługi zdarzeń.  
  
```vb  
DataRepeater1.Top = ProductsBindingNavigator.Height  
```  
  
```csharp  
dataRepeater1.Top = productsBindingNavigator.Height;  
```  
  
## <a name="controls-are-not-displayed-correctly-at-run-time"></a>Formanty nie są wyświetlane poprawnie w czasie wykonywania  
 Niektóre formanty w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontrolki nie mogą być wyświetlane, zgodnie z oczekiwaniami w czasie wykonywania. Proces używany do klonowania formantów z <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> zawsze nie może ustalić wszystkich właściwości wszystkich kontrolek. Na przykład jeśli dodasz niepowiązanych <xref:System.Windows.Forms.ListBox> kontrolę <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli w czasie projektowania i wypełnić jego <xref:System.Windows.Forms.ListBox.Items%2A> kolekcji z listą ciągów, <xref:System.Windows.Forms.ListBox> będzie pusty w czasie wykonywania. Jest to spowodowane procesu klonowania nie może wziąć pod uwagę <xref:System.Windows.Forms.ListBox.Items%2A> właściwości.  
  
 Możesz rozwiązać problemy, takie jak ta, przywracając brakuje właściwości w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemCloned> zdarzenie, które występuje po ukończeniu klonowania domyślne. W poniższym przykładzie pokazano, jak naprawić <xref:System.Windows.Forms.ListBox.Items%2A> zbiór <xref:System.Windows.Forms.ListBox> w kontrolce <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemCloned> programu obsługi zdarzeń.  
  
 [!code-csharp[VbPowerPacksDataRepeaterItemCloned#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/troubleshooting-the-datarepeater-control-visual-studio_1.cs)]
 [!code-vb[VbPowerPacksDataRepeaterItemCloned#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/troubleshooting-the-datarepeater-control-visual-studio_1.vb)]  
  
## <a name="the-selection-symbol-on-the-item-header-is-missing"></a>Brak Symbol zaznaczenia w nagłówku elementu  
 Po zmianie <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> właściwość Element nagłówka w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontrolki, niektóre kolory może spowodować, że symbol zaznaczenia zniknąć. Zmiana <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> właściwości mogą również spowodować symbol zaznaczenia zniknąć.  
  
 Nie można zmienić kolor i rozmiar symbol zaznaczenia.  
  
-   Jeśli ustawisz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> do <xref:System.Drawing.Color.White%2A>, symbol zaznaczenia nie będą widoczne, jeśli najpierw wybrano element.  
  
-   Jeśli ustawisz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> do <xref:System.Drawing.Color.Black%2A>, symbol zaznaczenia nie będą widoczne po wybraniu kontrolki i symbol ołówka nie będą widoczne, gdy kontrolka jest w trybie edycji.  
  
-   Jeśli <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> właściwość jest ustawiona na wartość, która jest mniejsza niż 11, symbole wskaźników w nagłówku elementu nie będą wyświetlane.  
  
 Możesz podać własne symbol nagłówka i Wybieranie elementu za pomocą <xref:System.Windows.Forms.PictureBox> kontrolę i monitorowanie <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A> właściwość <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> zdarzenia <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>.  
  
## <a name="see-also"></a>Zobacz także
- [Wprowadzenie do kontrolki DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [Instrukcje: Wyświetlanie powiązanych danych w formancie DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)
- [Instrukcje: Wyświetlanie formantów niepowiązanych w formancie DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)
- [Instrukcje: Zmienianie układu formantu DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)
- [Instrukcje: Zmienianie wyglądu formantu DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
- [Instrukcje: Wyświetlanie nagłówków elementów w formancie DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)
- [Instrukcje: Wyłączanie dodawania i usuwania elementów DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md)
- [Instrukcje: Wyszukiwanie danych w formancie DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md)
- [Instrukcje: Tworzenie formularza wzorzec/szczegół za pomocą dwóch formantów DataRepeater (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)
