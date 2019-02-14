---
title: 'Instrukcje: Projektowanie układu formularzy Windows dobrze reagującego na lokalizację'
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
ms.openlocfilehash: a4d0b19698a5f7fd4980fe1e945ee64c7f527ece
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2019
ms.locfileid: "56261820"
---
# <a name="how-to-design-a-windows-forms-layout-that-responds-well-to-localization"></a>Instrukcje: Projektowanie układu formularzy Windows dobrze reagującego na lokalizację
Tworzenie formularzy, które są gotowe do przeniesienia poza zlokalizowany znacznie rozwoju szybkości na rynki międzynarodowe. Możesz użyć <xref:System.Windows.Forms.TableLayoutPanel> formantu do zaimplementowania układy odpowiadać bez problemu zmieniała jak formanty zmiany rozmiaru z powodu zmian w ich <xref:System.Windows.Forms.Control.Text%2A> wartości właściwości.  
  
## <a name="example"></a>Przykład  
 Ten formularz, pokazuje, jak utworzyć układ, który proporcjonalnie dostosowuje podczas translacji wartości ciągu wyświetlanego w innych językach. Ten proces tłumaczenia jest nazywany *lokalizacji*. Aby uzyskać więcej informacji, zobacz [lokalizacji](../../../../docs/standard/globalization-localization/localization.md).  
  
 Brak zaawansowaną obsługę dla tego zadania w programie Visual Studio.  Zobacz też [instruktażu: Tworzenie układu, który dostosowuje proporcje dla lokalizacji](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100)).  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/CS/localizableform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/VB/localizableform.vb#1)]  
  
## <a name="additional-resources"></a>Dodatkowe zasoby
1.  [Instrukcje: Wyrównaj i rozciągnij kontrolki w kontrolce TableLayoutPanel](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2.  [Przewodnik: Rozmieszczanie kontrolek na formularzach Windows Forms za pomocą FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  

3.  [Instrukcje: Obejmowanie rzędów i kolumn w formancie TableLayoutPanel](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
4.  [Instrukcje: Edytowanie rzędów i kolumn w formancie TableLayoutPanel](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
5.  [Przewodnik: Wykonywania typowych zadań przy użyciu inteligentnych tagów w Windows Forms, formanty](performing-common-tasks-using-smart-tags-on-wf-controls.md)  
  
6.  [Przewodnik: Rozmieszczanie kontrolek na formularzach Windows Forms za pomocą TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  

7.  [Przewodnik: Układania Windows formantów formularzy przy użyciu dopełnienie, marginesy oraz właściwościami AutoSize](windows-forms-controls-padding-autosize.md)  
  
8.  [Instrukcje: Obsługiwanie lokalizacji na Windows Forms przy użyciu AutoSize i TableLayoutPanel](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/1zkt8b33(v=vs.100))  
  
9. [Przewodnik: Tworzenie formularza Windows o zmiennych rozmiarach dla wpisywania danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu, dane systemowe i System.Drawing oraz przestrzeń nazw System.Windows.Forms.  
  
 Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
- [Lokalizacja](../../../../docs/standard/globalization-localization/localization.md)
