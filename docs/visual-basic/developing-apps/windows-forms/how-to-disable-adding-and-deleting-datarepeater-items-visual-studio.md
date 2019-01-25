---
title: 'Instrukcje: Wyłączanie dodawania i usuwania elementów DataRepeater (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, disabling delete
- DataRepeater, disabling add
ms.assetid: 298d8f60-ddfe-4361-ab66-cf76d0df5220
ms.openlocfilehash: 3a304132d0514da4c19811be2536c9516e2838f0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54618545"
---
# <a name="how-to-disable-adding-and-deleting-datarepeater-items-visual-studio"></a>Instrukcje: Wyłączanie dodawania i usuwania elementów DataRepeater (Visual Studio)
Domyślnie użytkownicy mogą dodawać i usuwać elementy w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli. Użytkownicy mogą dodawać nowych elementów, naciskając klawisze CTRL + N przy <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> fokusie lub klikając **AddNewItem** znajdujący się na <xref:System.Windows.Forms.BindingNavigator> kontroli. Użytkownicy mogą usunąć element, naciskając klawisz usunięcia, kiedy <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> fokusie lub klikając **DeleteItem** znajdujący się na <xref:System.Windows.Forms.BindingNavigator> kontroli.  
  
 Można wyłączyć, dodawania i/lub usuwania w czasie projektowania lub w czasie wykonywania.  
  
### <a name="to-disable-adding-and-deleting-at-design-time"></a>Aby wyłączyć, dodawania i usuwania w czasie projektowania  
  
1.  W programie Windows Forms Designer wybierz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.  
  
    > [!NOTE]
    >  Musisz wybrać dolnej części kontrolki. Jeśli wybierzesz element sekcji szablonu, pojawi się inny zbiór właściwości.  
  
2.  W oknie właściwości ustaw <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToAddItems%2A> właściwości **False**.  
  
3.  Ustaw <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToDeleteItems%2A> właściwości **False**.  
  
4.  W programie Windows Forms Designer wybierz <xref:System.Windows.Forms.BindingNavigator> sterowania, a następnie kliknij przycisk **AddNewItem** (przycisk ze znakiem plus na nim).  
  
5.  W oknie właściwości ustaw <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> właściwości **False**.  
  
6.  W programie Windows Forms Designer wybierz <xref:System.Windows.Forms.BindingNavigator> sterowania, a następnie kliknij przycisk **DeleteItem** (przycisk z czerwonym symbolem X na nim).  
  
7.  W oknie właściwości ustaw <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> właściwości **False**.  
  
8.  W zasobniku składnika wybierz <xref:System.Windows.Forms.BindingSource> do której <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> jest powiązany.  
  
9. W oknie właściwości ustaw <xref:System.Windows.Forms.BindingSource.AllowNew%2A> właściwości **False**.  
  
10. W Windows Forms Designer, kliknij dwukrotnie **DeleteItem** przycisk, aby otworzyć Edytor kodu.  
  
11. Na liście rozwijanej zdarzenia wybierz `BindingNavigatorDeleteItem_EnabledChanged` zdarzeń.  
  
12. Dodaj następujący kod do `BindingNavigatorDeleteItem_EnabledChanged` program obsługi zdarzeń:  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]  
  
    > [!NOTE]
    >  Ten krok jest niezbędny, ponieważ <xref:System.Windows.Forms.BindingSource> umożliwi **DeleteItem** przycisk ilekroć dany zmiany bieżącego rekordu.  
  
### <a name="to-disable-adding-and-deleting-at-run-time"></a>Aby wyłączyć, dodawania i usuwania w czasie wykonywania  
  
1.  W Windows Forms Designer kliknij dwukrotnie formularza, aby otworzyć Edytor kodu.  
  
2.  Dodaj następujący kod do `Form_Load` zdarzeń:  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.vb)]  
  
3.  Dodaj następujący kod do `BindingNavigatorDeleteItem_EnabledChanged` program obsługi zdarzeń:  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]  
  
    > [!NOTE]
    >  Ten krok jest niezbędny, ponieważ <xref:System.Windows.Forms.BindingSource> umożliwi **DeleteItem** przycisk ilekroć dany zmiany bieżącego rekordu.  
  
## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>
- [Wprowadzenie do kontrolki DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [Rozwiązywanie problemów z kontrolką DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
