---
title: 'Instrukcje: Analizuj atrament za pomocą wskazówek analizy'
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
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57375483"
---
# <a name="how-to-analyze-ink-with-analysis-hints"></a><span data-ttu-id="bc4ba-102">Instrukcje: Analizuj atrament za pomocą wskazówek analizy</span><span class="sxs-lookup"><span data-stu-id="bc4ba-102">How to: Analyze Ink with Analysis Hints</span></span>
<span data-ttu-id="bc4ba-103">[System.Windows.Ink.AnalysisHintNode](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms610344(v=vs.90)) stanowi wskazówkę dla [System.Windows.Ink.InkAnalyzer](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms616754(v=vs.90)) do której jest dołączona.</span><span class="sxs-lookup"><span data-stu-id="bc4ba-103">An [System.Windows.Ink.AnalysisHintNode](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms610344(v=vs.90)) provides a hint for the [System.Windows.Ink.InkAnalyzer](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms616754(v=vs.90)) to which it is attached.</span></span>  <span data-ttu-id="bc4ba-104">Wskazówka ma zastosowanie do obszaru, który został określony przez [System.Windows.Ink.ContextNode.Location%2A](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms594508(v=vs.90)) właściwość [System.Windows.Ink.AnalysisHintNode](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms610344(v=vs.90)) i tworzy dodatkowy kontekst do analizator pisma odręcznego Zwiększ dokładność rozpoznawania.</span><span class="sxs-lookup"><span data-stu-id="bc4ba-104">The hint applies to the area specified by the [System.Windows.Ink.ContextNode.Location%2A](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms594508(v=vs.90)) property of the [System.Windows.Ink.AnalysisHintNode](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms610344(v=vs.90)) and provides extra context to the ink analyzer to improve recognition accuracy.</span></span> <span data-ttu-id="bc4ba-105">[System.Windows.Ink.InkAnalyzer](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms616754(v=vs.90)) stosuje te informacje kontekstu, gdy analizowanie pisma odręcznego uzyskany z obszaru wskazówki.</span><span class="sxs-lookup"><span data-stu-id="bc4ba-105">The [System.Windows.Ink.InkAnalyzer](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms616754(v=vs.90)) applies this context information when analyzing ink obtained from within the hint's area.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc4ba-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="bc4ba-106">Example</span></span>  
 <span data-ttu-id="bc4ba-107">Poniższy przykład jest aplikacja, która korzysta z wielu [System.Windows.Ink.AnalysisHintNode](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms610344(v=vs.90)) obiektów w formularzu, który akceptuje dane wejściowe pisma odręcznego.</span><span class="sxs-lookup"><span data-stu-id="bc4ba-107">The following example is an application that uses multiple [System.Windows.Ink.AnalysisHintNode](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms610344(v=vs.90)) objects on a form that accepts ink input.</span></span> <span data-ttu-id="bc4ba-108">Aplikacja używa [System.Windows.Ink.AnalysisHintNode.Factoid%2A](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms594341(v=vs.90)) właściwości, aby zapewnić informacje o kontekście dla każdego wpisu w formularzu.</span><span class="sxs-lookup"><span data-stu-id="bc4ba-108">The application uses the [System.Windows.Ink.AnalysisHintNode.Factoid%2A](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms594341(v=vs.90)) property to provide context information for each entry on the form.</span></span>  <span data-ttu-id="bc4ba-109">Aplikacja analizowanie pisma odręcznego za pomocą analizy w tle i czyści formularza całe pismo odręczne pięciu sekund po użytkownik zatrzymuje Dodawanie pisma odręcznego.</span><span class="sxs-lookup"><span data-stu-id="bc4ba-109">The application uses background analysis to analyze the ink and clears the form of all ink five seconds after the user stops adding ink.</span></span>  
  
 [!code-xaml[HowToAnalyzeInk#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToAnalyzeInk/CSharp/FormAnalyzer.xaml#1)]  
  
 [!code-csharp[HowToAnalyzeInk#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToAnalyzeInk/CSharp/FormAnalyzer.xaml.cs#2)]
 [!code-vb[HowToAnalyzeInk#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToAnalyzeInk/VisualBasic/FormAnalyzer.xaml.vb#2)]
