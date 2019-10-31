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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139881"
---
# <a name="walkthrough-creating-a-custom-dataflow-block-type"></a>Wskazówki: Tworzenie niestandardowego typu bloku przepływu danych
Chociaż biblioteka TPL przepływu danych zawiera kilka typów bloków przepływu danych, które umożliwiają różne funkcje, można również utworzyć niestandardowe typy bloków. W tym dokumencie opisano sposób tworzenia typu bloku przepływu danych, który implementuje zachowanie niestandardowe.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Przeczytaj [przepływu danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) przed odczytaniem tego dokumentu.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="defining-the-sliding-window-dataflow-block"></a>Definiowanie bloku przesuwanego okna przepływu danych  
 Rozważ użycie aplikacji przepływu danych, która wymaga buforowania wartości wejściowych, a następnie wyprowadzania danych wyjściowych w ruchomym oknie. Na przykład w przypadku wartości wejściowych {0, 1, 2, 3, 4, 5} i o rozmiarze okna z trzema, przesuwanym oknem przepływu danych jest tworzenie tablic wyjściowych {0, 1, 2}, {1, 2, 3}, {2, 3, 4} i {3, 4, 5}. W poniższych sekcjach opisano dwa sposoby tworzenia typu bloku przepływu danych implementującego to zachowanie niestandardowe. Pierwsza technika używa metody <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> do łączenia funkcji obiektu <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> i obiektu <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> w jeden blok propagacji. Druga technika definiuje klasę, która pochodzi od <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> i łączy istniejące funkcje do wykonywania niestandardowych zachowań.  
  
## <a name="using-the-encapsulate-method-to-define-the-sliding-window-dataflow-block"></a>Użycie metody hermetyzowania w celu zdefiniowania bloku przesuwanego okna przepływu danych  
 W poniższym przykładzie zastosowano metodę <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A>, aby utworzyć blok propagacji z elementu docelowego i źródła. Blok propagacji umożliwia blok źródłowy i blok docelowy do działania jako odbiornik i nadawca danych.  
  
 Ta technika jest przydatna, gdy wymagana jest funkcja Custom przepływu danych, ale nie jest wymagany typ, który zapewnia dodatkowe metody, właściwości lub pola.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#1)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#1)]  
  
## <a name="deriving-from-ipropagatorblock-to-define-the-sliding-window-dataflow-block"></a>Wyprowadzanie z IPropagatorBlock w celu zdefiniowania bloku przesuwanego okna przepływu danych  
 W poniższym przykładzie pokazano klasę `SlidingWindowBlock`. Ta klasa pochodzi od <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602>, dzięki czemu może działać zarówno jako źródło, jak i element docelowy danych. Jak w poprzednim przykładzie, Klasa `SlidingWindowBlock` jest oparta na istniejących typach bloków przepływu danych. Jednak Klasa `SlidingWindowBlock` implementuje także metody, które są wymagane przez interfejsy <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>, <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>i <xref:System.Threading.Tasks.Dataflow.IDataflowBlock>. Te metody wszystkie do przodu pracują ze wstępnie zdefiniowanymi elementami członkowskimi typu bloku przepływu danych. Na przykład Metoda `Post` odkłada pracy do `m_target` elementu członkowskiego danych, który jest również obiektem <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>.  
  
 Ta technika jest przydatna, gdy wymagana jest funkcja Custom przepływu danych, a także wymagany jest typ, który zapewnia dodatkowe metody, właściwości lub pola. Na przykład Klasa `SlidingWindowBlock` dziedziczy również z <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601>, aby można było udostępnić metody <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> i <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceiveAll%2A>. Klasa `SlidingWindowBlock` ilustruje także rozszerzalność, dostarczając Właściwość `WindowSize`, która pobiera liczbę elementów w oknie przesuwania.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#2)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#2)]  
  
## <a name="the-complete-example"></a>Kompletny przykład  
 Poniższy przykład pokazuje kompletny kod dla tego przewodnika. Pokazano w nim także, jak używać obu przesuwanych bloków okna w metodzie, która zapisuje je w bloku, odczytuje z niego i drukuje wyniki do konsoli.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#100)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#100)]  
  
## <a name="see-also"></a>Zobacz także

- [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
