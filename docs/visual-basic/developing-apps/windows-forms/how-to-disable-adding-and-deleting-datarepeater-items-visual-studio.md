---
title: 'Porady: wyłączanie dodawania i usuwania elementów DataRepeater (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, disabling delete
- DataRepeater, disabling add
ms.assetid: 298d8f60-ddfe-4361-ab66-cf76d0df5220
ms.openlocfilehash: e3d0d2a8d422054e269ee92df1fdfcb5acb96eac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590812"
---
# <a name="how-to-disable-adding-and-deleting-datarepeater-items-visual-studio"></a>Porady: wyłączanie dodawania i usuwania elementów DataRepeater (Visual Studio)
Domyślnie użytkownicy mogą dodawać i usuwać elementy w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu. Użytkownicy mogą dodać nowy element przez naciśnięcie klawiszy CTRL + N podczas <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> ma fokus lub przez kliknięcie przycisku **AddNewItem** znajdującego się na <xref:System.Windows.Forms.BindingNavigator> formantu. Użytkownicy mogą usuwać elementu przez naciśnięcie przycisku usuwania, kiedy <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> ma fokus lub przez kliknięcie przycisku **DeleteItem** znajdującego się na <xref:System.Windows.Forms.BindingNavigator> formantu.  
  
 Można wyłączyć, dodawanie lub usuwanie w czasie projektowania lub w czasie wykonywania.  
  
### <a name="to-disable-adding-and-deleting-at-design-time"></a>Aby wyłączyć dodawania i usuwania w czasie projektowania  
  
1.  W narzędziu Projektant dla formularzy systemu Windows wybierz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.  
  
    > [!NOTE]
    >  Musisz wybrać dolnej części kontrolki. W przypadku wybrania sekcji szablonu elementu pojawi się zestaw właściwości.  
  
2.  W oknie właściwości ustaw <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToAddItems%2A> właściwości **False**.  
  
3.  Ustaw <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToDeleteItems%2A> właściwości **False**.  
  
4.  W narzędziu Projektant dla formularzy systemu Windows wybierz <xref:System.Windows.Forms.BindingNavigator> kontroli, a następnie kliknij przycisk **AddNewItem** (przycisk ze znakiem plus na nim).  
  
5.  W oknie właściwości ustaw <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> właściwości **False**.  
  
6.  W narzędziu Projektant dla formularzy systemu Windows wybierz <xref:System.Windows.Forms.BindingNavigator> kontroli, a następnie kliknij przycisk **DeleteItem** (przycisk z czerwonym symbolem X w niej).  
  
7.  W oknie właściwości ustaw <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> właściwości **False**.  
  
8.  Na pasku składnika wybierz <xref:System.Windows.Forms.BindingSource> do którego <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> jest powiązany.  
  
9. W oknie właściwości ustaw <xref:System.Windows.Forms.BindingSource.AllowNew%2A> właściwości **False**.  
  
10. W narzędziu Projektant dla formularzy systemu Windows, kliknij dwukrotnie **DeleteItem** przycisk, aby otworzyć edytora kodu.  
  
11. Na liście rozwijanej zdarzenia wybierz `BindingNavigatorDeleteItem_EnabledChanged` zdarzeń.  
  
12. Dodaj następujący kod do `BindingNavigatorDeleteItem_EnabledChanged` obsługi zdarzeń:  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]  
  
    > [!NOTE]
    >  Ten krok jest niezbędny, ponieważ <xref:System.Windows.Forms.BindingSource> spowoduje włączenie **DeleteItem** przycisk zawsze zmiany bieżącego rekordu.  
  
### <a name="to-disable-adding-and-deleting-at-run-time"></a>Aby wyłączyć dodawania i usuwania w czasie wykonywania  
  
1.  W narzędziu Projektant dla formularzy systemu Windows kliknij dwukrotnie formularza, aby otworzyć edytora kodu.  
  
2.  Dodaj następujący kod do `Form_Load` zdarzeń:  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.vb)]  
  
3.  Dodaj następujący kod do `BindingNavigatorDeleteItem_EnabledChanged` obsługi zdarzeń:  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]  
  
    > [!NOTE]
    >  Ten krok jest niezbędny, ponieważ <xref:System.Windows.Forms.BindingSource> spowoduje włączenie **DeleteItem** przycisk zawsze zmiany bieżącego rekordu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [Wprowadzenie do kontrolki DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Rozwiązywanie problemów z kontrolką DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
