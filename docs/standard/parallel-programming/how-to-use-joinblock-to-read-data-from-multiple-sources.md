---
title: "Porady: Korzystanie z klasy JoinBlock do odczytywania danych z wielu źródeł"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, joining blocks in
- dataflow blocks, joining in TPL
ms.assetid: e9c1ada4-ac57-4704-87cb-2f5117f8151d
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 41445e4874b94809840ecf9ebda6f27ccc955c9b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-use-joinblock-to-read-data-from-multiple-sources"></a>Porady: Korzystanie z klasy JoinBlock do odczytywania danych z wielu źródeł
W tym dokumencie opisano sposób użycia <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> klasę, aby wykonać operację, gdy dane są dostępne z wielu źródeł. On również pokazano, jak w trybie niezachłanne włączyć wiele bloków sprzężenia wydajniej udostępnianie źródła danych.  
  
> [!TIP]
>  Biblioteka przepływu danych tpl (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> przestrzeni nazw) nie jest rozpowszechniana z [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Aby zainstalować <xref:System.Threading.Tasks.Dataflow> przestrzeni nazw, otwórz projekt w [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], wybierz **Zarządzaj pakietami NuGet** z menu projektu i wyszukaj w trybie online `Microsoft.Tpl.Dataflow` pakietu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano trzy typy zasobów, `NetworkResource`, `FileResource`, i `MemoryResource`i wykonuje operacje, gdy zasoby będą dostępne. W tym przykładzie wymaga `NetworkResource` i `MemoryResource` pary w celu przeprowadzenia pierwszej operacji i `FileResource` i `MemoryResource` pary w celu wykonania drugiej operacji. Aby włączyć te operacje nastąpić, gdy wszystkie wymagane zasoby są dostępne, w tym przykładzie użyto <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> klasy. Gdy <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> obiektu odbiera dane ze wszystkich źródeł, propaguje on danych do jej obiekt docelowy, który w tym przykładzie jest <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiektu. Zarówno <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> odczytywać obiekty z udostępnionej puli `MemoryResource` obiektów.  
  
 [!code-csharp[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_nongreedyjoin/cs/nongreedyjoin.cs#1)]
 [!code-vb[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_nongreedyjoin/vb/nongreedyjoin.vb#1)]  
  
 Umożliwia efektywne korzystanie z obszaru udostępnionej puli `MemoryResource` obiekty, w tym przykładzie określa <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions> obiektu, który ma <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions.Greedy%2A> ustawioną właściwość `False` utworzyć <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> obiektów, które działają w trybie niezachłanne. Blok niezachłanne złączenia odłoży wszystkie wiadomości przychodzących, dopóki nie jest dostępny z każdego źródła. Jeśli dowolny z komunikatów przełożonych zostały zaakceptowane przez innego bloku, blok sprzężenia powoduje ponowne uruchomienie procesu. Zachłanne innym niż tryb umożliwia bloki sprzężenia, które mają co najmniej jeden bloki źródła aby postęp czekać innych bloków danych. W tym przykładzie Jeśli `MemoryResource` obiekt jest dodawany do `memoryResources` puli sprzężenia pierwszy blok do odbierania drugiego źródła danych można wprowadzić postęp. Gdyby w tym przykładzie do używania trybu intensywnie, co jest ustawieniem domyślnym jeden blok sprzężenia może potrwać `MemoryResource` obiektów i poczekaj, aż drugi zasób stanie się dostępne. Jednak jeśli bloku sprzężenia drugiego źródła danych dostępne, nie powiedzie się postęp ponieważ `MemoryResource` obiektu jest zajęta przez bloku sprzężenia.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `DataflowNonGreedyJoin.cs` (`DataflowNonGreedyJoin.vb` dla [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **CSC.exe /r:System.Threading.Tasks.Dataflow.dll DataflowNonGreedyJoin.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowNonGreedyJoin.vb**  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Użycie złączenia niezachłanne może również pomóc zapobiegać zakleszczenie w aplikacji. W aplikacji *zakleszczenie* występuje, gdy dwie lub więcej procesów każdego przechowywania zasobu i wzajemnie poczekaj, aż inny proces zwolnić innego zasobu. Należy wziąć pod uwagę aplikacji, który definiuje dwa <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> obiektów. Oba obiekty każdego odczytywać dane z dwóch bloków udostępnionego źródła. W trybie intensywnie Jeśli jeden blok sprzężenia odczytuje z pierwszego źródła, a w drugim bloku sprzężenia odczytuje z drugie źródło aplikacji może do zakleszczenia, ponieważ zarówno bloki sprzężenia wzajemnie oczekiwania dla pozostałych zwolnić jego zasobów. W trybie niezachłanne każdy blok sprzężenia odczyty źródła tylko wtedy, gdy wszystkie dane są dostępne i w związku z tym ryzyko zakleszczenia wyeliminowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka przepływu danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
