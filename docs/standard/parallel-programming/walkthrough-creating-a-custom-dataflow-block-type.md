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
ms.openlocfilehash: 37857e465bf4089dbeecc4cfd532d0702f795495
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84284705"
---
# <a name="walkthrough-creating-a-custom-dataflow-block-type"></a>Przewodnik: Tworzenie niestandardowego typu bloku przepływu danych
Chociaż biblioteka TPL przepływu danych zawiera kilka typów bloków przepływu danych, które umożliwiają różne funkcje, można również utworzyć niestandardowe typy bloków. W tym dokumencie opisano sposób tworzenia typu bloku przepływu danych, który implementuje zachowanie niestandardowe.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Przeczytaj [przepływu danych](dataflow-task-parallel-library.md) przed odczytaniem tego dokumentu.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="defining-the-sliding-window-dataflow-block"></a>Definiowanie bloku przesuwanego okna przepływu danych  
 Rozważ użycie aplikacji przepływu danych, która wymaga buforowania wartości wejściowych, a następnie wyprowadzania danych wyjściowych w ruchomym oknie. Na przykład w przypadku wartości wejściowych {0, 1, 2, 3, 4, 5} i o rozmiarze okna z trzema, przesuwanym oknem przepływu danych jest tworzenie tablic wyjściowych {0, 1, 2}, {1, 2, 3}, {2, 3, 4} i {3, 4, 5}. W poniższych sekcjach opisano dwa sposoby tworzenia typu bloku przepływu danych implementującego to zachowanie niestandardowe. Pierwsza technika używa <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> metody do łączenia funkcji <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> obiektu i <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> obiektu w jeden blok propagacji. Druga technika definiuje klasę, która dziedziczy z <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> i łączy istniejące funkcje do wykonywania niestandardowych zachowań.  
  
## <a name="using-the-encapsulate-method-to-define-the-sliding-window-dataflow-block"></a>Użycie metody hermetyzowania w celu zdefiniowania bloku przesuwanego okna przepływu danych  
 W poniższym przykładzie zastosowano <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> metodę, aby utworzyć blok propagacji z obiektu docelowego i źródła. Blok propagacji umożliwia blok źródłowy i blok docelowy do działania jako odbiornik i nadawca danych.  
  
 Ta technika jest przydatna, gdy wymagana jest funkcja Custom przepływu danych, ale nie jest wymagany typ, który zapewnia dodatkowe metody, właściwości lub pola.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#1)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#1)]  
  
## <a name="deriving-from-ipropagatorblock-to-define-the-sliding-window-dataflow-block"></a>Wyprowadzanie z IPropagatorBlock w celu zdefiniowania bloku przesuwanego okna przepływu danych  
 W poniższym przykładzie pokazano `SlidingWindowBlock` klasę. Ta klasa pochodzi od <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> tak, aby mogła działać zarówno jako źródło, jak i element docelowy danych. Jak w poprzednim przykładzie, `SlidingWindowBlock` Klasa jest oparta na istniejących typach bloków przepływu danych. Jednak `SlidingWindowBlock` Klasa implementuje również metody, które są wymagane przez <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> , <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> i <xref:System.Threading.Tasks.Dataflow.IDataflowBlock> interfejsy. Te metody wszystkie do przodu pracują ze wstępnie zdefiniowanymi elementami członkowskimi typu bloku przepływu danych. Na przykład `Post` Metoda odkłada pracy do `m_target` elementu członkowskiego danych, który jest również <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> obiektem.  
  
 Ta technika jest przydatna, gdy wymagana jest funkcja Custom przepływu danych, a także wymagany jest typ, który zapewnia dodatkowe metody, właściwości lub pola. Na przykład `SlidingWindowBlock` Klasa pochodzi z tego, <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601> że może dostarczyć <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceiveAll%2A> metody i. `SlidingWindowBlock`Klasa ilustruje także rozszerzalność `WindowSize` , dostarczając właściwość, która pobiera liczbę elementów w oknie przesuwania.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#2)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#2)]  
  
## <a name="the-complete-example"></a>Kompletny przykład  
 Poniższy przykład pokazuje kompletny kod dla tego przewodnika. Pokazano w nim także, jak używać obu przesuwanych bloków okna w metodzie, która zapisuje je w bloku, odczytuje z niego i drukuje wyniki do konsoli.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#100)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#100)]  
  
## <a name="see-also"></a>Zobacz także

- [Przepływ danych](dataflow-task-parallel-library.md)
