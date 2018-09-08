---
title: 'Porady: zawijanie formantu formularzy systemu Windows za pomocą elementu ToolStripControlHost'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolStrip control [Windows Forms], wrapping controls
- toolbars [Windows Forms], wrapping controls
- ToolStrip control [Windows Forms], hosting controls
ms.assetid: e2ce4990-661d-4882-a116-8a9eb575dc84
ms.openlocfilehash: b502890fcad051d2393bb175bb0795acee2df613
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44209974"
---
# <a name="how-to-wrap-a-windows-forms-control-with-toolstripcontrolhost"></a>Porady: zawijanie formantu formularzy systemu Windows za pomocą elementu ToolStripControlHost
<xref:System.Windows.Forms.ToolStripControlHost> zaprojektowana w celu umożliwienia obsługi dowolnego kontrolek Windows Forms przy użyciu <xref:System.Windows.Forms.ToolStripControlHost> konstruktora lub rozszerzając <xref:System.Windows.Forms.ToolStripControlHost> sam. Ułatwia to zawijanie formantu, rozszerzając <xref:System.Windows.Forms.ToolStripControlHost> i implementowanie właściwości i metod, które uwidaczniają często używane, właściwości i metod formantu. Można również udostępnić zdarzeń dla formantu w <xref:System.Windows.Forms.ToolStripControlHost> poziom.  
  
### <a name="to-host-a-control-in-a-toolstripcontrolhost-by-derivation"></a>Do hostowania kontrolki w pomocą elementu ToolStripControlHost przez tworzenie wartości pochodnych  
  
1.  Rozszerzanie <xref:System.Windows.Forms.ToolStripControlHost>. Implementuje domyślnego konstruktora wywołuje przekazywanie konstruktora klasy bazowej odpowiednią kontrolę.  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#10](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#10)]  
  
2.  Deklarowanie właściwości z tego samego typu co opakowana kontroli i zwracają `Control` jako poprawny typ kontrolki w właściwości metody dostępu.  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#11](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#11)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#11)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#11)]  
  
3.  Uwidacznianie innych często używanych właściwości i metod kontroli opakowanej za pomocą właściwości i metody w klasie rozszerzonej.  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#12](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#12)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#12)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#12)]  
  
4.  Opcjonalnie można zastąpić <xref:System.Windows.Forms.ToolStripControlHost.OnSubscribeControlEvents%2A>, i <xref:System.Windows.Forms.ToolStripControlHost.OnUnsubscribeControlEvents%2A> metod i dodawaj zdarzenia kontroli, chcesz udostępnić.  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#16](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#16)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#16](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#16)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#16](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#16)]  
  
5.  Podaj niezbędne zawijania dla zdarzeń, które chcesz udostępnić.  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#17](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#17)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#17](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#17)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#17](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#17)]  
  
## <a name="example"></a>Przykład  
 [!code-cpp[System.Windows.Forms.ToolStripControlHost#13](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#13)]
 [!code-csharp[System.Windows.Forms.ToolStripControlHost#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#13)]
 [!code-vb[System.Windows.Forms.ToolStripControlHost#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#13)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Ten przykład wymaga:  
  
-   Odwołania do zestawów System i przestrzeń nazw System.Windows.Forms.  
  
 Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows Forms kodu przykładzie przy użyciu programu Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ToolStripControlHost>  
 [ToolStrip, kontrolka — omówienie](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [ToolStrip, kontrolka — architektura](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [ToolStrip — podsumowanie informacji o technologii](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
