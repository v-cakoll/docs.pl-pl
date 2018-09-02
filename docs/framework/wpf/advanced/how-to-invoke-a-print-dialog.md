---
title: Jak wywołać okno dialogowe drukowania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking print dialogs [WPF]
- print dialogs [WPF], invoking
ms.assetid: e3a2c84c-74fe-45a4-8501-5813f9dbfed2
ms.openlocfilehash: 271652fe9e98f9a381da5655bd313e12f8ee917d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43465671"
---
# <a name="how-to-invoke-a-print-dialog"></a>Jak wywołać okno dialogowe drukowania
Aby zapewnić możliwość drukowania z aplikacji, można po prostu utworzyć i otworzyć <xref:System.Windows.Controls.PrintDialog> obiektu.  
  
## <a name="example"></a>Przykład  
 <xref:System.Windows.Controls.PrintDialog> Kontrola zapewnia jeden punkt wejścia dla [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], konfiguracji i [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] przesyłania zadania. Kontrolka jest łatwa w użyciu i mogą być utworzone przy użyciu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] znaczników lub innego kodu. Poniższy przykład pokazuje, jak do tworzenia instancji i otwórz kontrolki w kodzie i jak go wydrukować. Pokazano również, jak upewnić się, że okno dialogowe będzie przyznać użytkownikowi możliwość ustawiania określony zakres stron. Przykładowy kod zakłada, że jest plikiem FixedDocumentSequence.xps w folderze głównym dysku C:.  
  
 [!code-csharp[printdialog#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 Po otwarciu okna dialogowego, użytkownicy będą mogli wybierać drukarek zainstalowanych na komputerze. Mają również możliwość wyboru [modułu zapisywania dokumentów XPS firmy Microsoft](https://go.microsoft.com/fwlink/?LinkId=147319) utworzyć [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] zamiast drukowania pliku.  
  
> [!NOTE]
>  <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> Kontrolę nad [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], która została omówiona w tym temacie, nie należy mylić z <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> składnika Windows Forms.  
  
 Ściśle rzecz ujmując, możesz użyć <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> metody bez konieczności otwierania okna dialogowego. W tym sensie formant może służyć jako składnika niewidzianych drukowania. Jednak ze względu na wydajność będzie lepiej używać albo <xref:System.Printing.PrintQueue.AddJob%2A> metody lub jednego z wielu <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> i <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> metody <xref:System.Windows.Xps.XpsDocumentWriter>. Aby uzyskać więcej informacji na ten temat, zobacz [programowe drukowanie plików XPS](../../../../docs/framework/wpf/advanced/how-to-programmatically-print-xps-files.md) i.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.PrintDialog>  
 [Dokumenty w WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Przegląd drukowania](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [Moduł zapisywania dokumentów XPS firmy Microsoft](https://go.microsoft.com/fwlink/?LinkId=147319)
