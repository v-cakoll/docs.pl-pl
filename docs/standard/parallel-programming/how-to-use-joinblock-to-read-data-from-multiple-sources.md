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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0031e352fea845ca4831b4df3a67c9cc6b67e876
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2019
ms.locfileid: "54222288"
---
# <a name="how-to-use-joinblock-to-read-data-from-multiple-sources"></a>Instrukcje: Korzystanie z klasy JoinBlock do odczytywania danych z wielu źródeł
W tym dokumencie wyjaśniono, jak używać <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> klasy w celu wykonania operacji, gdy dane są dostępne z wielu źródeł. Ilustruje też sposób do używania trybu niezachłanne, aby włączyć wiele bloków sprzężenia wydajniej udostępnianie źródła danych.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano trzy typy zasobów, `NetworkResource`, `FileResource`, i `MemoryResource`i wykonuje operacje, gdy zasoby będą dostępne. W tym przykładzie wymaga `NetworkResource` i `MemoryResource` pary w celu wykonywania pierwszej operacji i `FileResource` i `MemoryResource` pary w celu wykonywania drugą operację. Aby włączyć te operacje po wszystkich wymaganych zasobów są dostępne, w tym przykładzie użyto <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> klasy. Gdy <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> obiekt otrzymuje dane ze wszystkich źródeł, rozprzestrzenia się te dane uwzględniają cel, czyli w tym przykładzie <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiektu. Zarówno <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> obiektów odczytywać współużytkowanej puli `MemoryResource` obiektów.  
  
 [!code-csharp[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_nongreedyjoin/cs/nongreedyjoin.cs#1)]
 [!code-vb[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_nongreedyjoin/vb/nongreedyjoin.vb#1)]  
  
 Umożliwia efektywne korzystanie z obszaru udostępnionej puli `MemoryResource` obiektów, w tym przykładzie określa <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions> obiekt, który ma <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions.Greedy%2A> właściwością `False` utworzyć <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> obiekty, które działają w trybie niezachłanne. Blok niezachłanne złączenia odłoży wszystkie wiadomości przychodzące, dopóki nie jest dostępny z każdego źródła. Jeśli dowolny z komunikatów odroczone zostały zaakceptowane przez inny blok, w bloku sprzężenia powoduje ponowne uruchomienie procesu. Tryb bez zachłanne umożliwia bloki sprzężenia, współdzielących jeden lub więcej bloków źródła kompromis postęp czekać innych bloków danych. W tym przykładzie Jeśli `MemoryResource` obiekt jest dodawany do `memoryResources` puli pierwszy sprzężenia mogą robić postępów do przodu w bloku, aby otrzymać jej drugiego źródła danych. Jeśli były w tym przykładzie do używania trybu zachłannego, co jest ustawieniem domyślnym jeden blok sprzężenia może potrwać `MemoryResource` obiektu i poczekaj na drugi zasób stanie się dostępny. Jednakże, jeśli w bloku sprzężenia drugiego źródła danych dostępne, nie powiedzie się postęp ponieważ `MemoryResource` obiektu jest już zajęta przez inne blok sprzężenia.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Kopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `DataflowNonGreedyJoin.cs` (`DataflowNonGreedyJoin.vb` dla języka Visual Basic), a następnie uruchom następujące polecenie w wierszu polecenia dla deweloperów programu Visual Studio okna.  
  
 Visual C#  
  
 **CSC.exe /r:System.Threading.Tasks.Dataflow.dll DataflowNonGreedyJoin.cs**  
  
 Visual Basic  
  
 **vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowNonGreedyJoin.vb**  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Użycie niezachłanne może również pomóc uniknięcia zakleszczenia w aplikacji. W przypadku aplikacji oprogramowania *zakleszczenia* występuje, gdy dwa lub więcej procesów każdego zasobu do przechowywania i wzajemnie poczekaj, aż inny proces zwolnić innego zasobu. Rozważmy aplikację, która definiuje dwa <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> obiektów. Oba obiekty każdego odczytywać dane z dwóch bloków źródłowy udostępniony. W trybie zachłannego Jeśli jeden blok sprzężenia odczytuje z pierwszego źródła, a drugi blok sprzężenia odczytuje z drugiego źródła aplikacji może być do zakleszczenia, ponieważ oba bloki sprzężenia wzajemnie oczekiwania dla siebie zwolnić jego zasobów. W trybie niezachłanne każdy blok sprzężenia operacje odczytu od jej źródeł, tylko wtedy, gdy wszystkie dane będą dostępne i w związku z tym, ryzyko zakleszczenia zostanie wyeliminowany.  
  
## <a name="see-also"></a>Zobacz także

- [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
