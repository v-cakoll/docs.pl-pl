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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139738"
---
# <a name="how-to-use-joinblock-to-read-data-from-multiple-sources"></a>Porady: Korzystanie z klasy JoinBlock do odczytywania danych z wielu źródeł
W tym dokumencie wyjaśniono, jak używać <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> klasy do wykonywania operacji, gdy dane są dostępne z wielu źródeł. Pokazuje również, jak używać trybu niechciwego, aby umożliwić wiele bloków sprzężenia do bardziej efektywnego udostępniania źródła danych.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano `FileResource`trzy `MemoryResource`typy zasobów, `NetworkResource`, i , i wykonuje operacje, gdy zasoby stają się dostępne. W tym `NetworkResource` przykładzie `MemoryResource` wymaga i pary w celu `FileResource` `MemoryResource` wykonania pierwszej operacji i i pary w celu wykonania drugiej operacji. Aby włączyć te operacje, które występują, gdy wszystkie <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> wymagane zasoby są dostępne, w tym przykładzie używa klasy. Gdy <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> obiekt odbiera dane ze wszystkich źródeł, propaguje te dane do <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> jego docelowego, który w tym przykładzie jest obiektem. Oba <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> obiekty odczytywane z `MemoryResource` udostępnionej puli obiektów.  
  
 [!code-csharp[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_nongreedyjoin/cs/nongreedyjoin.cs#1)]
 [!code-vb[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_nongreedyjoin/vb/nongreedyjoin.vb#1)]  
  
 Aby umożliwić efektywne wykorzystanie udostępnionej `MemoryResource` puli obiektów, <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions> w tym <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions.Greedy%2A> przykładzie określono `False` obiekt, który ma właściwość ustawioną do tworzenia <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> obiektów, które działają w trybie niechciwym. Niechciwy blok sprzężenia odracza wszystkie wiadomości przychodzące, dopóki nie będzie dostępny z każdego źródła. Jeśli którykolwiek z odłożonych wiadomości zostały zaakceptowane przez inny blok, blok sprzężenia ponownie uruchamia proces. Tryb niechciwy umożliwia bloki sprzężenia, które współużytkują jeden lub więcej bloków źródłowych, aby postęp do przodu, jak inne bloki czekać na dane. W tym przykładzie `MemoryResource` jeśli obiekt zostanie `memoryResources` dodany do puli, pierwszy blok sprzężenia, aby otrzymać jego drugie źródło danych można dokonać postępu do przodu. Jeśli w tym przykładzie było użycie trybu chciwy, który `MemoryResource` jest domyślny, jeden blok sprzężenia może podjąć obiektu i czekać na drugi zasób, aby stać się dostępne. Jednak jeśli inny blok sprzężenia ma swoje drugie źródło danych `MemoryResource` dostępne, nie można dokonać postępu do przodu, ponieważ obiekt został przejęty przez inny blok sprzężenia.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Użycie sprzężeń niechciwych może również pomóc w zapobieganiu zakleszczenie w aplikacji. W aplikacji *zakleszczenie* występuje, gdy dwa lub więcej procesów każdy posiada zasób i wzajemnie czekać na inny proces, aby zwolnić inny zasób. Należy wziąć pod uwagę <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> aplikację, która definiuje dwa obiekty. Oba obiekty każdy odczytdanych z dwóch bloków źródła udostępnionego. W trybie chciwym, jeśli jeden blok sprzężenia odczytuje z pierwszego źródła, a drugi blok sprzężenia odczytuje z drugiego źródła, aplikacja może zakleszczenie, ponieważ oba bloki sprzężenia wzajemnie czekać na inne do zwolnienia jego zasobów. W trybie niechciwym każdy blok sprzężenia odczytuje ze swoich źródeł tylko wtedy, gdy wszystkie dane są dostępne, a zatem ryzyko zakleszczenia jest eliminowane.  
  
## <a name="see-also"></a>Zobacz też

- [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
