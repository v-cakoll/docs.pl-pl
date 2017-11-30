---
title: "Jak wywołać okno dialogowe drukowania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking print dialogs [WPF]
- print dialogs [WPF], invoking
ms.assetid: e3a2c84c-74fe-45a4-8501-5813f9dbfed2
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2ba541b367e56a809fa444528dccd69860c4de46
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-invoke-a-print-dialog"></a>Jak wywołać okno dialogowe drukowania
Aby zapewnić możliwość drukowania z aplikacji, możesz po prostu utworzyć i otworzyć <xref:System.Windows.Controls.PrintDialog> obiektu.  
  
## <a name="example"></a>Przykład  
 <xref:System.Windows.Controls.PrintDialog> Kontrola zapewnia jeden punkt wejścia dla [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], konfiguracji i [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] przesyłania zadania. Kontrolka jest łatwy w użyciu i mogą zostać utworzone przy użyciu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] znaczników lub kodu. W poniższym przykładzie pokazano, jak utworzyć wystąpienia, a następnie otwórz formantu w kodzie i drukowania z niego. Widoczny jest również sposób upewnij się, że okno dialogowe zapewni użytkownika ustawianie określonego zakresu stron. Przykład kodu zakłada, że plik FixedDocumentSequence.xps w folderze głównym dysku C:.  
  
 [!code-csharp[printdialog#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 Po otwarciu okna dialogowego, użytkownicy będą mogli wybrać z drukarek zainstalowanych na komputerze. Mają również możliwość wyboru [modułu zapisywania dokumentów XPS firmy Microsoft](http://go.microsoft.com/fwlink/?LinkId=147319) utworzyć [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] zamiast drukowania pliku.  
  
> [!NOTE]
>  <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> Kontrolę nad [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], która została szczegółowo opisana w tym temacie nie należy mylić z <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> składnika [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)].  
  
 Mówiąc ściślej, można użyć <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> metody bez konieczności otwierania okna dialogowego. W tym sensie formant może służyć jako niewidocznym składnik drukowania. Jednak ze względu na wydajność, byłoby lepiej użyć <xref:System.Printing.PrintQueue.AddJob%2A> metody lub jedną z wielu <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> i <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> metody <xref:System.Windows.Xps.XpsDocumentWriter>. Aby uzyskać więcej informacji na ten temat, zobacz [programowo plików XPS drukowania](../../../../docs/framework/wpf/advanced/how-to-programmatically-print-xps-files.md) i.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.PrintDialog>  
 [Dokumentów na platformie WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Omówienie drukowania](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [Moduł zapisywania dokumentów XPS firmy Microsoft](http://go.microsoft.com/fwlink/?LinkId=147319)
