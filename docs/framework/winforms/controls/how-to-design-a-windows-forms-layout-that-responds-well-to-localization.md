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
ms.openlocfilehash: 15f290f7d076eede7a8092d7295df810e4e51bf3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54563525"
---
# <a name="how-to-design-a-windows-forms-layout-that-responds-well-to-localization"></a>Instrukcje: Projektowanie układu formularzy Windows dobrze reagującego na lokalizację
Tworzenie formularzy, które są gotowe do przeniesienia poza zlokalizowany znacznie rozwoju szybkości na rynki międzynarodowe. Możesz użyć <xref:System.Windows.Forms.TableLayoutPanel> formantu do zaimplementowania układy odpowiadać bez problemu zmieniała jak formanty zmiany rozmiaru z powodu zmian w ich <xref:System.Windows.Forms.Control.Text%2A> wartości właściwości.  
  
## <a name="example"></a>Przykład  
 Ten formularz, pokazuje, jak utworzyć układ, który proporcjonalnie dostosowuje podczas translacji wartości ciągu wyświetlanego w innych językach. Ten proces tłumaczenia jest nazywany *lokalizacji*. Aby uzyskać więcej informacji, zobacz [lokalizacji](../../../../docs/standard/globalization-localization/localization.md).  
  
 Brak zaawansowaną obsługę dla tego zadania w programie Visual Studio.  Zobacz też [instruktażu: Tworzenie układu, który dostosowuje proporcje dla lokalizacji](https://msdn.microsoft.com/library/7k9fa71y\(v=vs.110\)).  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/CS/localizableform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/VB/localizableform.vb#1)]  
  
1.  [Instrukcje: Wyrównaj i rozciągnij kontrolki w kontrolce TableLayoutPanel](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2.  [Przewodnik: Rozmieszczanie kontrolek na formularzach Windows Forms za pomocą FlowLayoutPanel](https://msdn.microsoft.com/library/z9w7ek2f\(v=vs.110\))  
  
3.  [Instrukcje: Obejmowanie rzędów i kolumn w formancie TableLayoutPanel](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
4.  [Instrukcje: Edytowanie rzędów i kolumn w formancie TableLayoutPanel](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
5.  [Przewodnik: Wykonywania typowych zadań przy użyciu inteligentnych tagów w Windows Forms, formanty](https://msdn.microsoft.com/library/xhz359sc\(v=vs.110\))  
  
6.  [Przewodnik: Rozmieszczanie kontrolek na formularzach Windows Forms za pomocą TableLayoutPanel](https://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))  
  
7.  [Przewodnik: Układania Windows formantów formularzy przy użyciu dopełnienie, marginesy oraz właściwościami AutoSize](https://msdn.microsoft.com/library/3z3f9e8b\(v=vs.110\))  
  
8.  [Instrukcje: Obsługiwanie lokalizacji na Windows Forms przy użyciu AutoSize i TableLayoutPanel](https://msdn.microsoft.com/library/1zkt8b33\(v=vs.110\))  
  
9. [Przewodnik: Tworzenie formularza Windows o zmiennych rozmiarach dla wpisywania danych](https://msdn.microsoft.com/library/991eahec\(v=vs.110\))  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu, dane systemowe i System.Drawing oraz przestrzeń nazw System.Windows.Forms.  
  
 Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.  Zobacz też [jak: Skompilować i uruchomić przykładowy kod pełną Windows Forms przy użyciu programu Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
- [Lokalizacja](../../../../docs/standard/globalization-localization/localization.md)
