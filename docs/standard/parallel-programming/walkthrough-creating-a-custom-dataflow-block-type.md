---
title: 'Wskazówki: Tworzenie niestandardowego typu bloku przepływu danych'
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
ms.openlocfilehash: cb953952bbed90edd2db799e92d44ec9f062babf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139881"
---
# <a name="walkthrough-creating-a-custom-dataflow-block-type"></a>Wskazówki: Tworzenie niestandardowego typu bloku przepływu danych
Chociaż biblioteka przepływu danych TPL zawiera kilka typów bloków przepływu danych, które umożliwiają różne funkcje, można również utworzyć niestandardowe typy bloków. W tym dokumencie opisano sposób tworzenia typu bloku przepływu danych, który implementuje zachowanie niestandardowe.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Przeczytaj [przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) przed przeczytaniem tego dokumentu.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="defining-the-sliding-window-dataflow-block"></a>Definiowanie bloku przepływu danych okna przesuwnego  
 Należy wziąć pod uwagę aplikacji przepływu danych, która wymaga, że wartości wejściowe być buforowane, a następnie dane wyjściowe w sposób okna przesuwne. Na przykład dla wartości wejściowych {0, 1, 2, 3, 4, 5} i rozmiarokna trzech, blok przepływu danych okna przesuwnego tworzy tablice wyjściowe {0, 1, 2}, {1, 2, 3}, {2, 3, 4} i {3, 4, 5}. W poniższych sekcjach opisano dwa sposoby tworzenia typu bloku przepływu danych, który implementuje to zachowanie niestandardowe. Pierwsza technika <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> używa metody, aby połączyć <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> funkcjonalność <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> obiektu i obiektu w jeden blok propagatora. Druga technika definiuje klasę, która <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> pochodzi od i łączy istniejące funkcje do wykonywania niestandardowych zachowanie.  
  
## <a name="using-the-encapsulate-method-to-define-the-sliding-window-dataflow-block"></a>Używanie metody hermetyzacji do definiowania bloku przepływu danych okna przesuwnego  
 W poniższym <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> przykładzie użyto metody do utworzenia bloku propagatora z obiektu docelowego i źródła. Blok propagatora umożliwia bloku źródłowego i bloku docelowego do działania jako odbiorca i nadawca danych.  
  
 Ta technika jest przydatna, gdy wymagane są niestandardowe funkcje przepływu danych, ale nie jest wymagany typ, który zapewnia dodatkowe metody, właściwości lub pola.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#1)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#1)]  
  
## <a name="deriving-from-ipropagatorblock-to-define-the-sliding-window-dataflow-block"></a>Wynikające z IPropagatorBlock do definiowania bloku przepływu danych okna przesuwnego  
 W poniższym `SlidingWindowBlock` przykładzie przedstawiono klasę. Ta klasa pochodzi <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> z tak, że może działać jako źródło i miejsce docelowe danych. Podobnie jak w poprzednim `SlidingWindowBlock` przykładzie klasa jest zbudowana na istniejących typach bloków przepływu danych. `SlidingWindowBlock` Jednak klasa implementuje również metody, które są <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>wymagane <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>przez <xref:System.Threading.Tasks.Dataflow.IDataflowBlock> , , i interfejsów. Wszystkie te metody działają do przodu do wstępnie zdefiniowanych elementów członkowskich typu bloku przepływu danych. Na przykład `Post` odracza metody `m_target` pracy do elementu członkowskiego danych, który jest również obiektem. <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>  
  
 Ta technika jest przydatna, gdy wymagane są niestandardowe funkcje przepływu danych, a także wymagają typu, który zapewnia dodatkowe metody, właściwości lub pola. Na przykład `SlidingWindowBlock` klasa również pochodzi <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601> z tak, <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> że <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceiveAll%2A> może dostarczyć i metody. Klasa `SlidingWindowBlock` demonstruje również rozszerzalność, zapewniając `WindowSize` właściwość, która pobiera liczbę elementów w oknie przesuwnym.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#2)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#2)]  
  
## <a name="the-complete-example"></a>Kompletny przykład  
 W poniższym przykładzie przedstawiono pełny kod dla tego instruktaże. Pokazuje również, jak używać obu przesuwnych bloków okien w metodzie, która zapisuje do bloku, odczytuje z niego i drukuje wyniki do konsoli.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#100)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#100)]  
  
## <a name="see-also"></a>Zobacz też

- [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
