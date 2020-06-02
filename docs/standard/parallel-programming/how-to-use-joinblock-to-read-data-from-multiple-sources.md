---
title: 'Instrukcje: Korzystanie z klasy JoinBlock do odczytywania danych z wielu źródeł'
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
ms.openlocfilehash: cd2f5c65f45d83ef23643dcc747a748bb8ba89d9
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290827"
---
# <a name="how-to-use-joinblock-to-read-data-from-multiple-sources"></a>Instrukcje: Korzystanie z klasy JoinBlock do odczytywania danych z wielu źródeł
W tym dokumencie wyjaśniono, jak używać <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> klasy do wykonywania operacji, gdy dane są dostępne z wielu źródeł. Pokazano również, jak używać trybu zachłanne, aby umożliwić wiele bloków sprzężeń, aby bardziej efektywnie współużytkować źródło danych.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano trzy typy zasobów,, `NetworkResource` `FileResource` , i `MemoryResource` wykonuje operacje, gdy zasoby staną się dostępne. Ten przykład wymaga `NetworkResource` pary i, `MemoryResource` Aby wykonać pierwszą operację i `FileResource` `MemoryResource` parę i w celu wykonania drugiej operacji. Aby włączyć te operacje, gdy wszystkie wymagane zasoby są dostępne, w tym przykładzie zostanie użyta <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> Klasa. Gdy <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> obiekt odbiera dane ze wszystkich źródeł, propaguje te dane do obiektu docelowego, co w tym przykładzie jest <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiektem. Oba <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> obiekty odczytają się z udostępnionej puli `MemoryResource` obiektów.  
  
 [!code-csharp[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_nongreedyjoin/cs/nongreedyjoin.cs#1)]
 [!code-vb[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_nongreedyjoin/vb/nongreedyjoin.vb#1)]  
  
 Aby umożliwić efektywne wykorzystanie udostępnionej puli `MemoryResource` obiektów, w tym przykładzie określa <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions> obiekt, który ma <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions.Greedy%2A> Właściwość ustawioną na `False` do tworzenia <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> obiektów, które działają w trybie innym niż zachłanne. Blok Join inny niż zachłanne umożliwia odłożenie wszystkich komunikatów przychodzących do momentu, gdy jeden z nich będzie dostępny z każdego źródła. Jeśli dowolny z odroczonych komunikatów został zaakceptowany przez inny blok, blok sprzężenia ponownie uruchamia proces. Tryb inny niż zachłanne umożliwia blokom sprzężenia, które współdzielą jeden lub więcej bloków źródłowych, aby postępować dalej, ponieważ inne bloki oczekują na dane. W tym przykładzie, jeśli `MemoryResource` obiekt zostanie dodany do `memoryResources` puli, pierwszy blok sprzężenia, aby otrzymać drugie źródło danych, może postępować dalej. Jeśli w tym przykładzie był używany tryb zachłanne, który jest domyślnym, jeden blok sprzężenia może przyjąć `MemoryResource` obiekt i poczekać, aż drugi zasób stanie się dostępny. Jeśli jednak inny blok sprzężenia ma dostępne drugie źródło danych, nie może postępować dalej, ponieważ obiekt został `MemoryResource` wykonany przez inny blok sprzężenia.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Użycie sprzężeń innych niż zachłanne może również pomóc w zapobieganiu zakleszczeniom w aplikacji. W aplikacji oprogramowania *zakleszczenie* występuje, gdy co najmniej dwa procesy przechowują zasób i wzajemnie czekają na inny proces zwolnienia innego zasobu. Rozważmy aplikację, która definiuje dwa <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> obiekty. Oba obiekty odczytają dane z dwóch udostępnionych bloków źródłowych. W trybie zachłanne, jeśli jeden blok sprzężenia odczytuje z pierwszego źródła, a drugi blok sprzężenia odczytuje z drugiego źródła, aplikacja może zakleszczać, ponieważ oba bloki sprzężenia wzajemnie zaczekają na inne, aby zwolnić zasób. W trybie innym niż zachłanne każdy blok sprzężenia odczytuje ze źródeł tylko wtedy, gdy wszystkie dane są dostępne i w związku z tym ryzyko zakleszczenia jest eliminowane.  
  
## <a name="see-also"></a>Zobacz także

- [Przepływ danych](dataflow-task-parallel-library.md)
