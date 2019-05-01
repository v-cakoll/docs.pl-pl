---
title: 'Przewodnik: Tworzenie niestandardowego typu bloku przepływu danych'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, creating custom dataflow blocks
- dataflow blocks, creating custom in TPL
ms.assetid: a6147146-0a6a-4d9b-ab0f-237b3c1ac691
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 380bcb6d2a2846d09267eeb3a0d637469ce9fba5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61909457"
---
# <a name="walkthrough-creating-a-custom-dataflow-block-type"></a>Przewodnik: Tworzenie niestandardowego typu bloku przepływu danych
Mimo że biblioteka przepływu danych TPL udostępnia kilka typów bloku przepływu danych, które umożliwiają wykonywanie różnych funkcji, można również utworzyć typów bloków niestandardowych. Ten dokument zawiera opis sposobu tworzenia typu bloku przepływu danych, który implementuje niestandardowe zachowanie.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Odczyt [przepływu danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) przed przeczytaniem tego dokumentu.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="defining-the-sliding-window-dataflow-block"></a>Definiowanie przewijania bloku przepływu danych w oknie  
 Należy wziąć pod uwagę aplikacji przepływu danych, która wymaga, że wartości wejściowe być buforowane, a następnie dane wyjściowe w sposób ciągły, lub wartość okna. Na przykład dla wartości wejściowych {0, 1, 2, 3, 4, 5} i rozmiaru okna w trzech tablic danych wyjściowych {0, 1, 2}, tworzy przewijania bloku przepływu danych w oknie {1, 2, 3}, {2, 3, 4}, a {3, 4, 5}. W poniższych sekcjach opisano dwa sposoby tworzenia typu bloku przepływu danych, który implementuje to zachowanie niestandardowe. Pierwszą techniką używa <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> metodę, aby połączyć funkcje <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> obiektu i <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> obiektu w blok propagatora jeden. Druga metoda definiuje klasę pochodzącą od <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> i łączy istniejące funkcje, aby wykonać niestandardowe zachowanie.  
  
## <a name="using-the-encapsulate-method-to-define-the-sliding-window-dataflow-block"></a>Przy użyciu hermetyzacji metodę, aby zdefiniować przewijania bloku przepływu danych w oknie  
 W poniższym przykładzie użyto <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> metodę w celu utworzenia blok propagatora z elementem docelowym i źródłowym. Blok propagatora umożliwia blok źródłowy i blok docelowy jako odbiorca i nadawca danych.  
  
 Ta technika jest przydatna, gdy wymagają przepływu danych niestandardowych funkcji równoważenia obciążenia, ale nie wymagają, aby typ, który zawiera dodatkowe metody, właściwości lub pola.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#1)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#1)]  
  
## <a name="deriving-from-ipropagatorblock-to-define-the-sliding-window-dataflow-block"></a>Wyprowadzanie z IPropagatorBlock do definiowania bloku przepływu danych okna przewijania  
 W poniższym przykładzie przedstawiono `SlidingWindowBlock` klasy. Ta klasa jest pochodną <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> , dzięki czemu może działać jako źródło i obiekt docelowy danych. Co w poprzednim przykładzie `SlidingWindowBlock` klasy jest oparty na istniejących typów bloków przepływu danych. Jednak `SlidingWindowBlock` klasa implementuje również metody, które są wymagane przez <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>, <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>, i <xref:System.Threading.Tasks.Dataflow.IDataflowBlock> interfejsów. Metody te wszystkie do przodu działa do elementów członkowskich typu bloku przepływu danych wstępnie zdefiniowane. Na przykład `Post` metoda odracza pracy `m_target` element członkowski danych, która jest również <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> obiektu.  
  
 Ta technika jest przydatna, gdy wymagają przepływu danych niestandardowych funkcji równoważenia obciążenia, a także wymagają typ, który zawiera dodatkowe metody, właściwości lub pola. Na przykład `SlidingWindowBlock` również pochodną klasy <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601> tak, aby udostępnić funkcje <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> i <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceiveAll%2A> metody. `SlidingWindowBlock` Klasa przedstawia również rozszerzeń, zapewniając `WindowSize` właściwość, która pobiera liczbę elementów w ramach przesuwającego się okna.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#2)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#2)]  
  
## <a name="the-complete-example"></a>Kompletny przykład  
 Poniższy przykład pokazuje kompletny kod dla tego przewodnika. Ilustruje też sposób użycia obu bloki okna przewijania w metodzie, która zapisuje do bloku, odczytuje z niego i drukuje wyniki do konsoli.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#100)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#100)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Kopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `SlidingWindowBlock.cs` (`SlidingWindowBlock.vb` dla języka Visual Basic), a następnie uruchom następujące polecenie w wierszu polecenia dla deweloperów programu Visual Studio okna.  
  
 Visual C#  
  
 **csc.exe /r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.cs**  
  
 Visual Basic  
  
 **vbc.exe /r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.vb**  

## <a name="see-also"></a>Zobacz także

- [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
