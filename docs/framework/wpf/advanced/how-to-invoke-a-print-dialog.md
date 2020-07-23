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
ms.openlocfilehash: 75a4160366766efbd19d6e8ae26fbec102e7f95b
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86924503"
---
# <a name="how-to-invoke-a-print-dialog"></a>Jak wywołać okno dialogowe drukowania
Aby umożliwić drukowanie z poziomu aplikacji, można po prostu utworzyć i otworzyć <xref:System.Windows.Controls.PrintDialog> obiekt.  
  
## <a name="example"></a>Przykład  
 <xref:System.Windows.Controls.PrintDialog>Kontrolka zawiera pojedynczy punkt wejścia dla [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , konfiguracji i dla każdego zadania XPS. Kontrolka jest łatwa w użyciu i można ją utworzyć przy użyciu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] znacznika lub kodu. W poniższym przykładzie pokazano, jak utworzyć wystąpienie i otworzyć formant w kodzie oraz jak drukować z niego. Przedstawiono w nim również, jak upewnić się, że w oknie dialogowym zostanie wyświetlona opcja ustawienia określonego zakresu stron. Przykładowy kod założono, że w katalogu głównym dysku C: znajduje się plik FixedDocumentSequence. XPS.  
  
 [!code-csharp[printdialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 Po otwarciu okna dialogowego użytkownicy będą mogli wybierać spośród drukarek zainstalowanych na komputerze. Będą również mieć możliwość wyboru [składnika zapisywania dokumentów XPS firmy Microsoft](/windows/win32/printdocs/microsoft-xps-document-writer) w celu utworzenia pliku specyfikacji XML Paper Specification (XPS) zamiast drukowania.  
  
> [!NOTE]
> <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>Kontrolka WPF, która została omówiona w tym temacie, nie należy mylić ze <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> składnikiem Windows Forms.  
  
 Dokładnie mówiąc, można użyć <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> metody bez konieczności otwierania okna dialogowego. W tym sensie formant może być używany jako niewidoczny składnik drukowania. Jednak ze względu na wydajność lepszym rozwiązaniem jest użycie <xref:System.Printing.PrintQueue.AddJob%2A> metody lub jednej z wielu <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> metod <xref:System.Windows.Xps.XpsDocumentWriter> . Aby uzyskać więcej informacji na ten temat, zobacz programowe [Drukowanie plików XPS](how-to-programmatically-print-xps-files.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.PrintDialog>
- [Dokumenty w WPF](documents-in-wpf.md)
- [Przegląd Drukowanie](printing-overview.md)
- [Moduł zapisywania dokumentów XPS firmy Microsoft](/windows/win32/printdocs/microsoft-xps-document-writer)
