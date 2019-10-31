---
title: 'Porady: Korzystanie z klasy JoinBlock do odczytywania danych z wielu źródeł'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, joining blocks in
- dataflow blocks, joining in TPL
ms.assetid: e9c1ada4-ac57-4704-87cb-2f5117f8151d
ms.openlocfilehash: 66fd7ed7a98b8be8f88f65ecb52710a1e40af778
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139738"
---
# <a name="how-to-use-joinblock-to-read-data-from-multiple-sources"></a>Porady: Korzystanie z klasy JoinBlock do odczytywania danych z wielu źródeł
W tym dokumencie wyjaśniono, jak używać klasy <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> do wykonywania operacji, gdy dane są dostępne z wielu źródeł. Pokazano również, jak używać trybu zachłanne, aby umożliwić wiele bloków sprzężeń, aby bardziej efektywnie współużytkować źródło danych.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano trzy typy zasobów, `NetworkResource`, `FileResource`i `MemoryResource`oraz wykonuje operacje, gdy zasoby staną się dostępne. Ten przykład wymaga pary `NetworkResource` i `MemoryResource` w celu wykonania pierwszej operacji i pary `FileResource` i `MemoryResource` w celu wykonania drugiej operacji. Aby włączyć te operacje, gdy wszystkie wymagane zasoby są dostępne, w tym przykładzie zostanie użyta Klasa <xref:System.Threading.Tasks.Dataflow.JoinBlock%602>. Gdy obiekt <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> odbiera dane ze wszystkich źródeł, propaguje te dane do obiektu docelowego, co w tym przykładzie jest obiektem <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>. Oba obiekty <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> odczytywać z udostępnionej puli obiektów `MemoryResource`.  
  
 [!code-csharp[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_nongreedyjoin/cs/nongreedyjoin.cs#1)]
 [!code-vb[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_nongreedyjoin/vb/nongreedyjoin.vb#1)]  
  
 Aby umożliwić efektywne wykorzystanie udostępnionej puli `MemoryResource` obiektów, w tym przykładzie określa obiekt <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions>, który ma właściwość <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions.Greedy%2A> ustawioną na `False` do tworzenia <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> obiektów, które działają w trybie innym niż zachłanne. Blok Join inny niż zachłanne umożliwia odłożenie wszystkich komunikatów przychodzących do momentu, gdy jeden z nich będzie dostępny z każdego źródła. Jeśli dowolny z odroczonych komunikatów został zaakceptowany przez inny blok, blok sprzężenia ponownie uruchamia proces. Tryb inny niż zachłanne umożliwia blokom sprzężenia, które współdzielą jeden lub więcej bloków źródłowych, aby postępować dalej, ponieważ inne bloki oczekują na dane. W tym przykładzie, jeśli do puli `memoryResources` zostanie dodany obiekt `MemoryResource`, pierwszy blok sprzężenia, aby otrzymać drugie źródło danych, może postępować dalej. Jeśli w tym przykładzie był używany tryb zachłanne, który jest domyślnym, jeden blok sprzężenia może przyjmować `MemoryResource` obiektu i czekać, aż drugi zasób stanie się dostępny. Jeśli jednak inny blok sprzężenia ma dostęp do drugiego źródła danych, nie może postępować dalej, ponieważ obiekt `MemoryResource` został wykonany przez inny blok sprzężenia.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Użycie sprzężeń innych niż zachłanne może również pomóc w zapobieganiu zakleszczeniom w aplikacji. W aplikacji oprogramowania *zakleszczenie* występuje, gdy co najmniej dwa procesy przechowują zasób i wzajemnie czekają na inny proces zwolnienia innego zasobu. Rozważmy aplikację, która definiuje dwa <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> obiekty. Oba obiekty odczytają dane z dwóch udostępnionych bloków źródłowych. W trybie zachłanne, jeśli jeden blok sprzężenia odczytuje z pierwszego źródła, a drugi blok sprzężenia odczytuje z drugiego źródła, aplikacja może zakleszczać, ponieważ oba bloki sprzężenia wzajemnie zaczekają na inne, aby zwolnić zasób. W trybie innym niż zachłanne każdy blok sprzężenia odczytuje ze źródeł tylko wtedy, gdy wszystkie dane są dostępne i w związku z tym ryzyko zakleszczenia jest eliminowane.  
  
## <a name="see-also"></a>Zobacz także

- [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
