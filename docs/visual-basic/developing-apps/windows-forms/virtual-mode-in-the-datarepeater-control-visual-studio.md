---
title: Tryb wirtualny w formancie DataRepeater (Visual Studio)
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- virtual data binding [Visual Basic]
- DataRepeater
- DataRepeater, virtual mode
ms.assetid: 5fb805dc-2d8b-4139-b1e3-86e4c2667221
ms.openlocfilehash: 7aa462f670c95f2d5996cf04b676bf09e9ec62b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="virtual-mode-in-the-datarepeater-control-visual-studio"></a>Tryb wirtualny w formancie DataRepeater (Visual Studio)
Jeśli chcesz wyświetlić dużych ilości danych tabelarycznych w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli, może zwiększyć wydajność, ustawiając <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> właściwości `True` i zarządzanie jawnie interakcji formantu ze źródłem danych. <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Kontrola zapewnia kilka zdarzeń, które może obsłużyć do interakcji z źródła danych i wyświetlić dane, zgodnie z potrzebami w czasie wykonywania.  
  
## <a name="how-virtual-mode-works"></a>Działa jak wirtualne tryb  
 Najbardziej typowym scenariuszem dla <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formant jest powiązanie formantów podrzędnych z <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> dane źródła w czasie projektowania i umożliwić <xref:System.Windows.Forms.BindingSource> do przekazywania danych i z powrotem w razie potrzeby. Podczas korzystania z trybu wirtualnego formanty nie są powiązane ze źródłem danych, a dane są przekazywane i z powrotem do źródła danych w czasie wykonywania.  
  
 Gdy <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> właściwość jest ustawiona na `True`, Utwórz interfejs użytkownika, dodając formantów z **przybornika** zamiast opcji dodawania formanty powiązane z **źródeł danych** okna.  
  
 Zdarzenia są generowane na podstawie kontroli przez formant i należy dodać kodu do obsługi wyświetlania danych. Podczas tworzenia nowego <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> jest wyświetlony w wyniku przewijania, <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> zdarzenie jest wywoływane jeden raz dla każdego formantu i podaj wartości dla każdego formantu w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> obsługi zdarzeń.  
  
 Jeśli dane w jednym z kontrolki zostanie zmienione przez użytkownika, <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> zdarzenia i musi sprawdzić poprawność danych i zapisać ją w źródle danych.  
  
 Jeśli użytkownik dodaje nowy element <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded> zdarzenia. Użyj obsługi tego zdarzenia, aby utworzyć nowy rekord w źródle danych. Aby zapobiec niezamierzone zmiany, należy również monitorować <xref:System.Windows.Forms.Control.KeyDown> zdarzeń dla każdego formantu i wywołanie <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A> gdy użytkownik naciśnie klawisz ESC.  
  
 Jeśli źródło danych zmiany, należy odświeżyć <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli przez wywołanie metody <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A> i <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A> metody. Obie metody musi zostać wywołany w kolejności.  
  
 Na koniec należy zaimplementować obsługi zdarzeń <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved> zdarzenie, które występuje, gdy element zostanie usunięty i opcjonalnie dla <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletingItems> i <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletedItems> zdarzenia, które występuje zawsze, gdy użytkownik usuwa element naciskając klawisz DELETE.  
  
## <a name="implementing-virtual-mode"></a>Implementowanie trybu wirtualnego  
 Poniżej przedstawiono kroki, które są wymagane do wdrożenia w trybie wirtualnym.  
  
#### <a name="to-implement-virtual-mode"></a>Aby zaimplementować tryb wirtualny  
  
1.  Przeciągnij <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontrolować z **Visual Basic PowerPacks** karcie **przybornika** formularza lub kontenera formantu. Ustaw <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> właściwości `True`.  
  
2.  Przeciągnij formanty z **przybornika** na region szablonu elementu (górnej) z <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu. Konieczne będzie jeden formant dla każdego pola w źródle danych, które mają być wyświetlane.  
  
3.  Implementowanie obsługi dla <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> zdarzenie, aby podać wartości dla każdego formantu. To zdarzenie jest wywoływane podczas tworzenia nowego <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> jest wyświetlony w wyniku przewijania. Kod będzie podobne do następującego przykładu, czyli dla źródła danych o nazwie `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_1.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_1.cs)]  
  
4.  Implementowanie obsługi dla <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> zdarzeń do przechowywania danych. To zdarzenie jest wywoływane, gdy użytkownik zatwierdza zmiany do formantu podrzędnego <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>. Kod będzie podobne do następującego przykładu, czyli dla źródła danych o nazwie `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_2.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_2.cs)]  
  
5.  Implementowanie obsługi dla każdego formantu podrzędnego <xref:System.Windows.Forms.Control.KeyDown> zdarzeń i monitor klawisz ESC. Wywołanie <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A> metodę, aby zapobiec <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> zdarzenia z są zgłaszane. Ten kod będzie podobne do następującego przykładu.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_3.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_3.cs)]  
  
6.  Implementowanie obsługi dla <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded> zdarzeń. To zdarzenie jest wywoływane, gdy użytkownik dodaje nowy element do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu. Kod będzie podobne do następującego przykładu, czyli dla źródła danych o nazwie `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_4.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_4.cs)]  
  
7.  Implementowanie obsługi dla <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved> zdarzeń. To zdarzenie występuje, gdy użytkownik usuwa istniejący element. Kod będzie podobne do następującego przykładu, czyli dla źródła danych o nazwie `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_5.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_5.cs)]  
  
8.  Sprawdzanie poprawności poziom kontroli, opcjonalnie zaimplementować programy obsługi dla <xref:System.Windows.Forms.Control.Validating> zdarzenia formantów podrzędnych. Ten kod będzie podobne do następującego przykładu.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#6](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_6.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#6](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_6.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded>  
 [Wprowadzenie do kontrolki DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
