---
title: "Porady: projektowanie układu formularzy systemu Windows dobrze reagującego na lokalizację"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms]
- application design [Windows Forms], localization
- Windows Forms, localization
- localization [Windows Forms], Windows Forms layout
ms.assetid: d13eff2d-701c-4b6e-8838-3885cbfb7223
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 072d0694b3e92d9bf4bd8d0cf118b2f4af024af6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-design-a-windows-forms-layout-that-responds-well-to-localization"></a>Porady: projektowanie układu formularzy systemu Windows dobrze reagującego na lokalizację
Tworzenie formularzy, które są gotowe do przeniesienia znacznie zlokalizowane szybkości rozwoju na rynkach międzynarodowych. Można użyć <xref:System.Windows.Forms.TableLayoutPanel> formantu do zaimplementowania układów reagujące bezpiecznie zgodnie z powodu zmian w zmiana rozmiaru formantów ich <xref:System.Windows.Forms.Control.Text%2A> wartości właściwości.  
  
## <a name="example"></a>Przykład  
 Ten formularz pokazuje, jak utworzyć układ proporcjonalnie dopasowuje podczas translacji wartości ciągu wyświetlanego w innych językach. Po wywołaniu tego procesu tłumaczenia *lokalizacja*. Aby uzyskać więcej informacji, zobacz [lokalizacja](../../../../docs/standard/globalization-localization/localization.md).  
  
 Brak kompleksową obsługę tego zadania w programie Visual Studio.  Zobacz też [wskazówki: tworzenia układu, który dostosowuje część lokalizacji](http://msdn.microsoft.com/library/7k9fa71y\(v=vs.110\)).  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/CS/localizableform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/VB/localizableform.vb#1)]  
  
1.  [Instrukcje: wyrównywanie i rozciąganie kontrolki w kontrolce TableLayoutPanel](http://msdn.microsoft.com/library/ms171688\(v=vs.110\))  
  
2.  [Przewodnik: rozmieszczanie kontrolek w formularzach Windows Forms za pomocą kontrolki FlowLayoutPanel](http://msdn.microsoft.com/library/z9w7ek2f\(v=vs.110\))  
  
3.  [Instrukcje: obejmowanie rzędów i kolumn w kontrolce TableLayoutPanel](http://msdn.microsoft.com/library/ms171687\(v=vs.110\))  
  
4.  [Instrukcje: edytowanie rzędów i kolumn w kontrolce TableLayoutPanel](http://msdn.microsoft.com/library/ms171686\(v=vs.110\))  
  
5.  [Przewodnik: przeprowadzanie typowych zadań z tagami inteligentnymi na kontrolkach formularzy Windows Forms](http://msdn.microsoft.com/library/xhz359sc\(v=vs.110\))  
  
6.  [Przewodnik: rozmieszczanie kontrolek w aplikacji Windows Forms za pomocą kontrolki TableLayoutPanel](http://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))  
  
7.  [Przewodnik: tworzenie kontrolek formularzy Windows Forms z uzupełnieniem, marginesami oraz właściwościami AutoSize](http://msdn.microsoft.com/library/3z3f9e8b\(v=vs.110\))  
  
8.  [Porady: Obsługa lokalizacji w formularzach systemu Windows za pomocą AutoSize i TableLayoutPanel — formant](http://msdn.microsoft.com/library/1zkt8b33\(v=vs.110\))  
  
9. [Wskazówki: Tworzenie formularza systemu Windows o zmiennych rozmiarach do wpisywania danych](http://msdn.microsoft.com/library/991eahec\(v=vs.110\))  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu, dane systemowe, System.Drawing i System.Windows.Forms.  
  
 Informacji dotyczących tworzenia tego przykładu z wiersza polecenia dla [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] lub [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tym przykładzie [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] przez wklejenie kodu do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 [Lokalizacja](../../../../docs/standard/globalization-localization/localization.md)
