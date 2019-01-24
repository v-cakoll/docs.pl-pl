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
ms.openlocfilehash: 3988c16746606de9f20f9a66b87539b6cea04758
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54700809"
---
# <a name="virtual-mode-in-the-datarepeater-control-visual-studio"></a>Tryb wirtualny w formancie DataRepeater (Visual Studio)
Jeśli chcesz wyświetlić dużą ilość danych tabelarycznych w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontrolki, może poprawić wydajność, ustawiając <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> właściwość `True` i jawnie zarządzania kontrolki interakcji ze źródłem danych. <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Kontrola zapewnia kilka zdarzeń, które może obsłużyć do interakcji z źródła danych i wyświetlić dane, stosownie do potrzeb w czasie wykonywania.  
  
## <a name="how-virtual-mode-works"></a>Działa jak wirtualny tryb  
 Najbardziej typowym scenariuszem dla <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formant jest do powiązania kontrolki podrzędne <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> do danych źródła w czasie projektowania i umożliwić <xref:System.Windows.Forms.BindingSource> do przekazywania danych i z powrotem zgodnie z potrzebami. Korzystając z trybu wirtualnego formanty nie są powiązane ze źródłem danych, a dane są przekazywane i z powrotem do bazowego źródła danych w czasie wykonywania.  
  
 Gdy <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> właściwość jest ustawiona na `True`, tworzymy interfejs użytkownika przez dodanie formantów z **przybornika** zamiast opcji dodawania formantów powiązanych z **źródeł danych** okna.  
  
 Zdarzenia są wywoływane na podstawie kontroli kontroli, a następnie należy dodać kod do obsługi wyświetlania danych. Gdy nowy <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> jest przewijane do widoku, <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> zdarzenie jest wywoływane jeden raz dla każdego formantu i należy podać wartości dla każdej kontrolki <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> programu obsługi zdarzeń.  
  
 Jeśli dane w jednej z kontrolek zostanie zmieniony przez użytkownika, <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> zdarzenie jest zgłaszane, i należy sprawdzić poprawność danych i zapisz go ze źródłem danych.  
  
 Jeśli użytkownik doda nowy element <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded> zdarzenie jest wywoływane. Aby utworzyć nowy rekord w źródle danych, należy użyć obsługi tego zdarzenia. Aby zapobiegać niezamierzonym zmianom, należy również monitorować <xref:System.Windows.Forms.Control.KeyDown> zdarzeń dla każdego formantu i wywołaniu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A> gdy użytkownik naciśnie klawisz ESC.  
  
 Jeśli zmiany źródła danych, można odświeżyć <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli przez wywołanie metody <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A> i <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A> metody. Obie metody musi zostać wywołany w kolejności.  
  
 Na koniec należy zaimplementować obsługę zdarzeń dla <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved> zdarzenie, które występuje, gdy element zostanie usunięty i, opcjonalnie <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletingItems> i <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletedItems> zdarzenia, które występują, gdy użytkownik usuwa element, naciskając klawisz DELETE.  
  
## <a name="implementing-virtual-mode"></a>Implementowanie trybu wirtualnego  
 Poniżej przedstawiono kroki, które są wymagane do Implementowanie trybu wirtualnego.  
  
#### <a name="to-implement-virtual-mode"></a>Aby zaimplementować trybu wirtualnego  
  
1.  Przeciągnij <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> z kontrolować **Visual Basic PowerPacks** karcie **przybornika** formularza lub kontener formantu. Ustaw <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> właściwość `True`.  
  
2.  Przeciągnij formanty z **przybornika** na element szablonu region (górnego regionu) <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli. Konieczne będzie jeden formant dla każdego pola w źródle danych, które mają być wyświetlane.  
  
3.  Implementowanie obsługi dla <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> zdarzenie, aby podać wartości dla każdego formantu. To zdarzenie jest wywoływane, gdy nowy <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> jest przewijane do widoku. Kod będzie podobne do następującego przykładu, który jest źródłem danych o nazwie `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_1.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_1.cs)]  
  
4.  Implementowanie obsługi dla <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> zdarzeń do przechowywania danych. To zdarzenie jest wywoływane, gdy użytkownik zatwierdzenia zmian w kontrolki podrzędnej z <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>. Kod będzie podobne do następującego przykładu, który jest źródłem danych o nazwie `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_2.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_2.cs)]  
  
5.  Implementowanie obsługi dla każdego formantu podrzędnego <xref:System.Windows.Forms.Control.KeyDown> zdarzeń i monitor klawisz ESC. Wywołaj <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A> metodę, aby zapobiec <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> zdarzenia są zgłaszane. Ten kod będzie wyglądać następująco.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_3.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_3.cs)]  
  
6.  Implementowanie obsługi dla <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded> zdarzeń. To zdarzenie jest wywoływane, gdy użytkownik dodaje nowy element do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli. Kod będzie podobne do następującego przykładu, który jest źródłem danych o nazwie `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_4.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_4.cs)]  
  
7.  Implementowanie obsługi dla <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved> zdarzeń. To zdarzenie występuje, gdy użytkownik usuwa istniejący element. Kod będzie podobne do następującego przykładu, który jest źródłem danych o nazwie `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_5.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_5.cs)]  
  
8.  Sprawdzanie poprawności poziom kontroli, opcjonalnie zaimplementować programy obsługi dla <xref:System.Windows.Forms.Control.Validating> zdarzeń formantów podrzędnych. Ten kod będzie wyglądać następująco.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#6](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_6.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#6](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_6.cs)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded>
- [Wprowadzenie do kontrolki DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
