---
title: 'Instrukcje: projektowanie układu formularzy systemu Windows dobrze reagującego na lokalizację'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms]
- application design [Windows Forms], localization
- Windows Forms, localization
- localization [Windows Forms], Windows Forms layout
ms.assetid: d13eff2d-701c-4b6e-8838-3885cbfb7223
ms.openlocfilehash: c1aa62413e1c9cc29507b7b0ed5cbf1c5fcea26a
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928568"
---
# <a name="how-to-design-a-windows-forms-layout-that-responds-well-to-localization"></a>Instrukcje: projektowanie układu formularzy systemu Windows dobrze reagującego na lokalizację
Tworzenie formularzy, które są gotowe do zlokalizowania znacznie przyspiesza rozwój dla rynków międzynarodowych. Można użyć <xref:System.Windows.Forms.TableLayoutPanel> kontrolki do implementacji układów, które reagują bezproblemowo w miarę zmieniania rozmiaru, <xref:System.Windows.Forms.Control.Text%2A> ze względu na zmiany wartości właściwości.  
  
## <a name="example"></a>Przykład  
 Ten formularz pokazuje, jak utworzyć układ, który zmienia się proporcjonalnie w przypadku tłumaczenia wyświetlanych wartości ciągu na inne języki. Ten proces tłumaczenia nazywa się *lokalizacją*. Aby uzyskać więcej informacji, zobacz [Lokalizacja](../../../standard/globalization-localization/localization.md).  
  
 W programie Visual Studio jest dostępna szeroka pomoc techniczna dla tego zadania.  Zobacz również [Przewodnik: Tworzenie układu dostosowującego proporcję lokalizacji](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100)).  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/CS/localizableform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/VB/localizableform.vb#1)]  
  
## <a name="additional-resources"></a>Dodatkowe zasoby

1. [Instrukcje: Wyrównywanie i rozciąganie kontrolki w kontrolce TableLayoutPanel](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2. [Przewodnik: Rozmieszczanie kontrolek na Windows Forms przy użyciu FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  

3. [Instrukcje: Rozciągaj wiersze i kolumny w kontrolce TableLayoutPanel](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
4. [Instrukcje: Edytowanie kolumn i wierszy w kontrolce TableLayoutPanel](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
5. [Przewodnik: Wykonywanie typowych zadań przy użyciu tagów inteligentnych w kontrolkach Windows Forms](performing-common-tasks-using-smart-tags-on-wf-controls.md)  
  
6. [Przewodnik: Rozmieszczanie kontrolek na Windows Forms przy użyciu TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  

7. [Przewodnik: Określanie układu formantów Windows Forms z dopełnieniem, marginesami i właściwością AutoSize](windows-forms-controls-padding-autosize.md)  
  
8. [Instrukcje: Obsługa lokalizacji na Windows Forms przy użyciu funkcji AutoSize i kontrolki TableLayoutPanel](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/1zkt8b33(v=vs.100))  
  
9. [Przewodnik: Tworzenie formularza systemu Windows o zmiennym rozmiarze na potrzeby wprowadzania danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów system, system. Data, system. Drawing i system. Windows. Forms.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
- [Lokalizacja](../../../standard/globalization-localization/localization.md)
