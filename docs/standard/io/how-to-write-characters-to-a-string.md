---
title: 'Jak: Zapisywać znaki do ciągu'
ms.date: 01/21/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data streams, writing characters to string
- writing characters to strings
- streams, writing characters to strings
- I/O [.NET Framework], writing characters to strings
ms.assetid: 1222cbeb-0760-44bf-9888-914a2a37174b
ms.openlocfilehash: ecbfa2de2c21ff79df269f74eeddfa0738e7e25c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160286"
---
# <a name="how-to-write-characters-to-a-string"></a>Jak: Zapisywać znaki do ciągu
Poniższe przykłady kodu zapisują znaki synchronicznie lub asynchronicznie z tablicy znaków do ciągu.  
  
## <a name="example-write-characters-synchronously-in-a-console-app"></a>Przykład: synchronicznie zapisuj znaki w aplikacji konsoli  
 W poniższym <xref:System.IO.StringWriter> przykładzie użyto do zapisu <xref:System.Text.StringBuilder> pięciu znaków synchronicznie do obiektu.
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example-write-characters-asynchronously-in-a-wpf-app"></a>Przykład: Pisanie znaków asynchronicznie w aplikacji WPF
 Następnym przykładem jest kod za aplikacją WPF. Na obciążenie okna przykład asynchronicznie odczytuje <xref:System.Windows.Controls.TextBox> wszystkie znaki z formantu i przechowuje je w tablicy. Następnie asynchronicznie zapisuje każdą literę lub znak odstępu <xref:System.Windows.Controls.TextBlock> do osobnego wiersza formantu.  
  
 [!code-csharp[StreamReaderWriter](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[StreamReaderWriter](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IO.StringWriter>  
- <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>  
- <xref:System.Text.StringBuilder>  
- [Plik i strumień we/wy](../../../docs/standard/io/index.md)  
- [We/Wy pliku asynchronicznego](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [Jak: Wyliczanie katalogów i plików](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [Jak: Odczytywanie i zapisywanie w nowo utworzonym pliku danych](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Jak: Otwieranie i dołączanie do pliku dziennika](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [Jak: Odczytywanie tekstu z pliku](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [Jak: Napisać tekst do pliku](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Jak: Odczytywanie znaków z ciągu](../../../docs/standard/io/how-to-read-characters-from-a-string.md)
