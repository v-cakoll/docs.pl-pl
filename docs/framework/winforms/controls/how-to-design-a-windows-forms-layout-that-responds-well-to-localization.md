---
title: Projektowanie układu przyjazny dla lokalizacji
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
ms.openlocfilehash: 9556c03699713b7d14f81a6eacc8e4ab337e869b
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628634"
---
# <a name="how-to-design-a-windows-forms-layout-that-responds-well-to-localization"></a>Porady: projektowanie układu formularzy systemu Windows dobrze reagującego na lokalizację
Tworzenie formularzy, które są gotowe do zlokalizowania znacznie przyspiesza rozwój dla rynków międzynarodowych. Za pomocą kontrolki <xref:System.Windows.Forms.TableLayoutPanel> można zaimplementować układy, które reagują bezproblemowo w miarę zmieniania rozmiaru formantów ze względu na zmiany wartości właściwości <xref:System.Windows.Forms.Control.Text%2A>.

## <a name="example"></a>Przykład
 Ten formularz pokazuje, jak utworzyć układ, który zmienia się proporcjonalnie w przypadku tłumaczenia wyświetlanych wartości ciągu na inne języki. Ten proces tłumaczenia nazywa się *lokalizacją*. Aby uzyskać więcej informacji, zobacz [Lokalizacja](../../../standard/globalization-localization/localization.md).

 W programie Visual Studio jest dostępna szeroka pomoc techniczna dla tego zadania.  Zobacz również [Przewodnik: tworzenie układu, który dostosowuje proporcje dla lokalizacji](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100)).

 [!code-csharp[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/CS/localizableform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/VB/localizableform.vb#1)]

## <a name="additional-resources"></a>Dodatkowe zasoby

1. [Instrukcje: wyrównywanie i rozciąganie kontrolki w kontrolce TableLayoutPanel](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)

2. [Przewodnik: rozmieszczanie kontrolek w formularzach Windows Forms za pomocą kontrolki FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)

3. [Instrukcje: obejmowanie rzędów i kolumn w kontrolce TableLayoutPanel](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)

4. [Instrukcje: edytowanie rzędów i kolumn w kontrolce TableLayoutPanel](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)

5. [Przewodnik: wykonywanie typowych zadań przy użyciu akcji projektanta](perform-common-tasks-design-actions.md)

6. [Przewodnik: rozmieszczanie kontrolek w aplikacji Windows Forms za pomocą kontrolki TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)

7. [Przewodnik: tworzenie kontrolek formularzy Windows Forms z uzupełnieniem, marginesami oraz właściwościami AutoSize](windows-forms-controls-padding-autosize.md)

8. [Instrukcje: obsługa lokalizacji na Windows Forms przy użyciu funkcji Autodopasowanie rozmiaru i formantu TableLayoutPanel](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/1zkt8b33(v=vs.100))

9. [Przewodnik: Tworzenie formularza systemu Windows o zmiennym rozmiarze na potrzeby wprowadzania danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))

## <a name="compiling-the-code"></a>Kompilowanie kodu
 Ten przykład wymaga:

- Odwołania do zestawów system, system. Data, system. Drawing i system. Windows. Forms.

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
- [Lokalizacja](../../../standard/globalization-localization/localization.md)
