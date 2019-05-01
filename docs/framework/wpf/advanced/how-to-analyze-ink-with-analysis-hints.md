---
title: 'Instrukcje: Analizowanie pisma odręcznego za pomocą wskazówek analizy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ink [WPF], analyzing
- analyzing ink [WPF]
- ink [WPF], AnalysisHintNode objects [WPF]
- AnalysisHintNode objects [WPF]
ms.assetid: d4421ed4-77f5-4640-829e-9f1de50b2ff2
ms.openlocfilehash: a4c38ddf52e9054fe9126df4b7e172548617b90d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777003"
---
# <a name="how-to-analyze-ink-with-analysis-hints"></a>Instrukcje: Analizowanie pisma odręcznego za pomocą wskazówek analizy
[System.Windows.Ink.AnalysisHintNode](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms610344(v=vs.90)) stanowi wskazówkę dla [System.Windows.Ink.InkAnalyzer](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms616754(v=vs.90)) do której jest dołączona.  Wskazówka ma zastosowanie do obszaru, który został określony przez [System.Windows.Ink.ContextNode.Location%2A](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms594508(v=vs.90)) właściwość [System.Windows.Ink.AnalysisHintNode](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms610344(v=vs.90)) i tworzy dodatkowy kontekst do analizator pisma odręcznego Zwiększ dokładność rozpoznawania. [System.Windows.Ink.InkAnalyzer](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms616754(v=vs.90)) stosuje te informacje kontekstu, gdy analizowanie pisma odręcznego uzyskany z obszaru wskazówki.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład jest aplikacja, która korzysta z wielu [System.Windows.Ink.AnalysisHintNode](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms610344(v=vs.90)) obiektów w formularzu, który akceptuje dane wejściowe pisma odręcznego. Aplikacja używa [System.Windows.Ink.AnalysisHintNode.Factoid%2A](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms594341(v=vs.90)) właściwości, aby zapewnić informacje o kontekście dla każdego wpisu w formularzu.  Aplikacja analizowanie pisma odręcznego za pomocą analizy w tle i czyści formularza całe pismo odręczne pięciu sekund po użytkownik zatrzymuje Dodawanie pisma odręcznego.  
  
 [!code-xaml[HowToAnalyzeInk#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToAnalyzeInk/CSharp/FormAnalyzer.xaml#1)]  
  
 [!code-csharp[HowToAnalyzeInk#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToAnalyzeInk/CSharp/FormAnalyzer.xaml.cs#2)]
 [!code-vb[HowToAnalyzeInk#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToAnalyzeInk/VisualBasic/FormAnalyzer.xaml.vb#2)]
