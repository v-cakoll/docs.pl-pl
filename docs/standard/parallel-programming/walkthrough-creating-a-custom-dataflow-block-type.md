---
title: 'Wskazówki: Tworzenie niestandardowego typu bloku przepływu danych'
ms.date: 03/30/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
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
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: fdb6bde99ac5e15fb07010f3a73aba7c09bd4834
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-creating-a-custom-dataflow-block-type"></a>Wskazówki: Tworzenie niestandardowego typu bloku przepływu danych
Biblioteka przepływu danych tpl zapewnia kilka typów bloku przepływu danych, które umożliwiają wykonywanie różnych funkcji, jednak można również utworzyć niestandardowe bloku typów. Ten dokument zawiera opis sposobu tworzenia typu bloku przepływu danych, który implementuje zachowanie niestandardowych.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Odczyt [przepływu danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) przed przeczytaniem tego dokumentu.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="defining-the-sliding-window-dataflow-block"></a>Definiowanie przesuwanego okna bloku przepływu danych  
 Należy wziąć pod uwagę aplikacji przepływu danych, która wymaga buforowane wartości wejściowe i następnie dane wyjściowe w sposób przesuwanego okna. Na przykład dla wartości wejściowych {0, 1, 2, 3, 4, 5} i rozmiar okna trzech przesuwanego okna bloku przepływu danych tworzy tablic danych wyjściowych {0, 1, 2}, {1, 2, 3}, {2, 3, 4} i {3, 4, 5}. W poniższych sekcjach opisano dwa sposoby tworzenia typu bloku przepływu danych, który implementuje to zachowanie niestandardowych. Używa pierwszego technika <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> metodę, aby połączyć funkcjonalność <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> obiektu i <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> obiektu do propagator jednego bloku. Druga metoda definiuje klasę pochodzącą z <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> i łączy istniejące funkcje do wykonania działania niestandardowego.  
  
## <a name="using-the-encapsulate-method-to-define-the-sliding-window-dataflow-block"></a>Przy użyciu Hermetyzowanie metodę, aby zdefiniować przesuwanego okna bloku przepływu danych  
 W poniższym przykładzie użyto <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> metodę w celu utworzenia bloku propagator z źródłowe i docelowe. Blok propagator umożliwia bloku źródłowy i docelowy blok do działania jako odbiornik i nadawcy danych.  
  
 Ta technika jest przydatne, gdy potrzebujesz funkcji niestandardowych przepływu danych, ale nie wymagają, aby typ, który udostępnia dodatkowe metody, właściwości lub pól.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#1)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#1)]  
  
## <a name="deriving-from-ipropagatorblock-to-define-the-sliding-window-dataflow-block"></a>Wyprowadzanie z IPropagatorBlock do definiowania przesuwanego okna bloku przepływu danych  
 W poniższym przykładzie przedstawiono `SlidingWindowBlock` klasy. Ta klasa pochodzi od <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> tak, aby mógł działać jako źródło i element docelowy danych. Tak jak w poprzednim przykładzie `SlidingWindowBlock` klasy powstała w oparciu o istniejących typów bloku przepływu danych. Jednak `SlidingWindowBlock` klasa implementuje również metody, które są wymagane przez <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>, <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>, i <xref:System.Threading.Tasks.Dataflow.IDataflowBlock> interfejsów. Przekazuj wszystkie te metody pracy do elementów członkowskich typu bloku przepływu danych wstępnie zdefiniowane. Na przykład `Post` metoda różni się pracy `m_target` danych elementu członkowskiego, który jest także <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> obiektu.  
  
 Ta technika jest przydatne, gdy wymagają funkcji niestandardowych przepływu danych, a także wymagać typu, który udostępnia dodatkowe metody, właściwości lub pól. Na przykład `SlidingWindowBlock` również pochodną klasy <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601> , dzięki czemu umożliwia ona <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> i <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceiveAll%2A> metody. `SlidingWindowBlock` Klasy przedstawiono również rozszerzalności zapewniając `WindowSize` właściwość, która pobiera liczbę elementów w metodzie przesuwanego okna.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#2)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#2)]  
  
## <a name="the-complete-example"></a>Kompletny przykład  
 Poniższy przykład przedstawia kompletny kod dla tego przewodnika. Ilustruje też sposób użycia obu przesuwanego bloki okna w metodzie, która zapisuje do bloku, odczytuje z niego i wyświetla wyniki w konsoli programu.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#100)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#100)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `SlidingWindowBlock.cs` (`SlidingWindowBlock.vb` w języku Visual Basic), a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 Visual C#  
  
 **CSC.exe /r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.cs**  
  
 Visual Basic  
  
 **vbc.exe /r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.vb**  

## <a name="see-also"></a>Zobacz też  
 [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
