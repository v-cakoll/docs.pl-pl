---
title: "Wskazówki: Tworzenie potoku przepływu danych"
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
- dataflow pipelines, creating with TPL
- Task Parallel Library, dataflows
- TPL dataflow library, creating dataflow pipeline
ms.assetid: 69308f82-aa22-4ac5-833d-e748533b58e8
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d63fb872382bfc0a3ba3b8637c7357ab65c58fbf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-creating-a-dataflow-pipeline"></a>Wskazówki: Tworzenie potoku przepływu danych
Chociaż można używać <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A?displayProperty=nameWithType>, i <xref:System.Threading.Tasks.Dataflow.DataflowBlock.TryReceive%2A?displayProperty=nameWithType> metod do odbierania wiadomości z źródło bloków, możesz również nawiązać bloki komunikatów formularza *potoku przepływu danych*. Potoku przepływu danych jest szeregu składników, lub *bloków przepływu danych*, z których każdy wykonuje określone zadanie, która wspiera większy cel. Każdy blok przepływu danych w potoku przepływu danych wykonuje pracę po otrzymaniu komunikatu od innego bloku przepływu danych. Odpowiednio do tego zestawu dla jest wiersz samochodów produkcyjnym. Każdy vehicle przechodzi przez wiersz zestawu, jednej stacji składana ramki, kolejny instaluje aparat i tak dalej. Ponieważ wiersza zestawu umożliwia wielu pojazdów odbywać się w tym samym czasie, zapewnia lepszą przepustowość niż zebrania pojazdów kompletnych jednym naraz.  
  
> [!TIP]
>  Biblioteka przepływu danych tpl (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> przestrzeni nazw) nie jest rozpowszechniana z [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Aby zainstalować <xref:System.Threading.Tasks.Dataflow> przestrzeni nazw, otwórz projekt w [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], wybierz **Zarządzaj pakietami NuGet** z menu projektu i wyszukaj w trybie online `Microsoft.Tpl.Dataflow` pakietu.  
  
 W tym dokumencie przedstawiono potoku przepływu danych, który pobiera książkę *Iliad Homer* z witryny sieci Web i wyszukiwania tekstu do dopasowania poszczególnych wyrazów z wyrazów tego wstecznego pierwsze słowo znaków. Tworzenie potoku przepływu danych, w tym dokumencie obejmuje następujące kroki:  
  
1.  Utwórz bloków przepływu danych, które uczestniczą w potoku.  
  
2.  Każdy blok przepływu danych nawiązać połączenia z kolejnego bloku w potoku. Każdy blok odbiera jako dane wejściowe dane wyjściowe poprzedniego bloku w potoku.  
  
3.  Dla każdego bloku przepływu danych należy utworzyć zadania kontynuacji, która ustawia kolejnego bloku stanu ukończenia po ukończeniu poprzedniego bloku.  
  
4.  Dane do head potoku POST.  
  
5.  Head potoku należy oznaczyć jako ukończone.  
  
6.  Poczekaj, aż potoku do ukończenia pracy.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Odczyt [przepływu danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) przed skorzystaniem z tego przewodnika.  
  
## <a name="creating-a-console-application"></a>Tworzenie aplikacji konsoli  
 W [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], Utwórz [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] lub [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] projekt aplikacji konsoli. Dodaj odwołanie do System.Threading.Tasks.Dataflow.dll.  
  
 Można również utworzyć plik i nadaj mu nazwę `ReverseWords.cs` (`ReverseWords.vb` dla [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio, aby skompilować projekt.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **CSC.exe /r:System.Threading.Tasks.Dataflow.dll ReverseWords.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe /r:System.Threading.Tasks.Dataflow.dll ReverseWords.vb**  
  
 Dodaj następujący kod do projektu do tworzenia aplikacji w warstwie podstawowa.  
  
 [!code-csharp[TPLDataflow_Palindromes#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#2)]
 [!code-vb[TPLDataflow_Palindromes#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#2)]  
  
## <a name="creating-the-dataflow-blocks"></a>Tworzenie bloków przepływu danych  
 Dodaj następujący kod do `Main` metodę w celu utworzenia bloków przepływu danych, które uczestniczą w potoku. Tabela poniżej zawiera podsumowanie roli dla każdego elementu członkowskiego potoku.  
  
 [!code-csharp[TPLDataflow_Palindromes#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#3)]
 [!code-vb[TPLDataflow_Palindromes#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#3)]  
  
|Element członkowski|Typ|Opis|  
|------------|----------|-----------------|  
|`downloadString`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Pobiera tekst książki z sieci Web.|  
|`createWordList`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Dzieli tekst książki na tablicę słów.|  
|`filterWordList`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Usuwa krótkich wyrazów w wyrazie tablicy, zamówienia wynikowy słowa alfabetycznie i Usuń duplikaty.|  
|`findReversedWords`|<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>|Znajduje wszystkie słowa w kolekcji tablicy filtrowane word którego wstecznego występuje także w tablicy programu word.|  
|`printReversedWords`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|Wyświetla słów i odpowiednie wyrazów odwrotna do konsoli.|  
  
 Mimo że można połączyć wiele czynności ułożonych w potoku przepływu danych w tym przykładzie w jednym kroku, w przykładzie zilustrowano pojęcie tworzenie wielu niezależnych przepływu danych zadania do wykonania zadania większy. W przykładzie użyto <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> umożliwiające każdy element członkowski potoku wykonać operację na jej danych wejściowych i wysyłać wyniki do następnego kroku w potoku. `findReversedWords` Element członkowski potoku jest <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> obiektu, ponieważ generuje wiele niezależnych wyjść dla każdego danych wejściowych. Tail potoku, `printReversedWords`, jest <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiektu, ponieważ wykonuje akcję na jego dane wejściowe i dać wynik.  
  
## <a name="forming-the-pipeline"></a>Tworzenie potoku  
 Dodaj następujący kod, aby połączyć każdy blok do kolejnego bloku w potoku.  
  
 Podczas wywoływania <xref:System.Threading.Tasks.Dataflow.DataflowBlock.LinkTo%2A> metody nawiązywania połączenia z docelowym bloku przepływu danych, bloku przepływu danych źródła bloku przepływu danych źródła propaguje danych blok docelowy wraz ze wzrostem dostępności danych.  
  
 [!code-csharp[TPLDataflow_Palindromes#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#4)]
 [!code-vb[TPLDataflow_Palindromes#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#4)]  
  
## <a name="creating-the-completion-tasks"></a>Tworzenie zadań zakończenia  
 Dodaj następujący kod, aby włączyć każdego bloku przepływu danych umożliwić wykonywanie akcji końcowego po przetwarza wszystkie dane.  
  
 [!code-csharp[TPLDataflow_Palindromes#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#5)]
 [!code-vb[TPLDataflow_Palindromes#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#5)]  
  
 Propagacja uzupełniania za pośrednictwem potoku, każde zadanie ukończenia ustawia kolejnego bloku przepływu danych stanu ukończenia. Na przykład gdy head potoku stanu ukończenia go przetwarza komunikaty buforowanego pozostałych i następnie uruchamia zadanie jego zakończenia, który określa drugi element członkowski potoku do stanu ukończenia. Drugi element członkowski potoku z kolei przetwarza wszystkie pozostałe komunikaty buforowanego i następnie uruchamia zadanie jego zakończenia, który ustawia trzeci element członkowski potoku do stanu ukończenia. Ten proces jest kontynuowany do momentu zakończenia wszystkich elementów członkowskich w potoku. W tym przykładzie użyto `delegate` — słowo kluczowe (`Function` w [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) do definiowania zadań kontynuacji.  
  
## <a name="posting-data-to-the-pipeline"></a>Przesyłanie danych do potoku  
 Dodaj następujący kod do publikowania adresu URL książki *Iliad Homer* nagłówek potoku przepływu danych.  
  
 [!code-csharp[TPLDataflow_Palindromes#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#6)]
 [!code-vb[TPLDataflow_Palindromes#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#6)]  
  
 W tym przykładzie użyto <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A?displayProperty=nameWithType> synchronicznie wysyłać dane do head potoku. Użyj <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A?displayProperty=nameWithType> metody muszą asynchronicznie wysyłania danych do węzła przepływu danych.  
  
## <a name="completing-pipeline-activity"></a>Kończenie działania potoku  
 Dodaj następujący kod, aby oznaczyć head potoku jako ukończone. Head potoku uruchamia jego zadania kontynuacji po przetwarza wszystkie buforowane wiadomości. To zadanie kontynuacji propaguje stanu ukończenia za pośrednictwem potoku.  
  
 [!code-csharp[TPLDataflow_Palindromes#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#7)]
 [!code-vb[TPLDataflow_Palindromes#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#7)]  
  
 W tym przykładzie wysyła jednego adresu URL za pośrednictwem potoku przepływu danych do przetworzenia. W przypadku wysłania więcej niż jedno wejście za pośrednictwem potoku, należy wywołać <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A?displayProperty=nameWithType> metody po przesłaniu wszystkie dane wejściowe. Ten krok można pominąć, jeśli aplikacja nie ma dobrze zdefiniowanego punktu jaką danych nie jest już dostępny lub aplikacja nie ma czekać na zakończenie procesu.  
  
## <a name="waiting-for-the-pipeline-to-finish"></a>Oczekiwanie na zakończenie procesu  
 Dodaj następujący kod, aby czekać na zakończenie procesu. Ponieważ w tym przykładzie użyto zadań kontynuacji propagację uzupełniania za pośrednictwem potoku, ogólną zakończeniu operacji po zakończeniu tail potoku.  
  
 [!code-csharp[TPLDataflow_Palindromes#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#8)]
 [!code-vb[TPLDataflow_Palindromes#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#8)]  
  
 Możesz poczekać na zakończenie przepływu danych z dowolnego wątku lub wiele wątków jednocześnie.  
  
## <a name="the-complete-example"></a>Kompletny przykład  
 Poniższy przykład przedstawia kompletny kod dla tego przewodnika.  
  
 [!code-csharp[TPLDataflow_Palindromes#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#1)]
 [!code-vb[TPLDataflow_Palindromes#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#1)]  
  
## <a name="next-steps"></a>Następne kroki  
 W tym przykładzie wysyła jeden adres URL do przetworzenia za pośrednictwem potoku przepływu danych. Po wysłaniu więcej niż jedną wartość wejściowa za pośrednictwem potoku można wprowadzać formularza równoległości do aplikacji, która jest podobny jak części może przenieść przez fabrykę samochodów. Podczas pierwszego elementu członkowskiego potoku wysyła jego wynik do drugiego elementu członkowskiego, może przetwarzać innego elementu równolegle, jak drugi element członkowski przetwarza pierwszego wyniku.  
  
 Równoległość, który jest realizowane za pośrednictwem potoki przepływu danych jest nazywany *coarse-grained równoległości* ponieważ zazwyczaj składa się z mniej, bardziej złożone zadania. Można również użyć bardziej *szczegółowych równoległości* mniejsze, wykonywania short zadań w potoku przepływu danych. W tym przykładzie `findReversedWords` używa elementu członkowskiego potoku <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> metody w celu przetworzenia wielu elementów na liście zadań równolegle. Stosowanie szczegółowych równoległości w potoku coarse-grained może zwiększyć ogólną przepustowość.  
  
 Możesz również nawiązać połączenie bloku przepływu danych źródła wiele bloków docelowej do utworzenia *przepływu danych sieci*. Przeciążone wersja <xref:System.Threading.Tasks.Dataflow.DataflowBlock.LinkTo%2A> ma metodę <xref:System.Predicate%601> obiektu, który definiuje, czy blok docelowy akceptuje każdy komunikat na podstawie jego wartości. Większość przepływu danych bloku typy, które pełnić rolę źródła oferują komunikaty, aby wszystkie bloki docelowym, w kolejności, w jakiej były one połączone, dopóki jeden bloków akceptuje tej wiadomości. Za pomocą tego mechanizmu filtrowania, można utworzyć systemów bloków przepływu danych połączonych bezpośrednie niektórych danych za pośrednictwem jednej ścieżki i innych danych za pomocą innej ścieżki. Na przykład, który używa filtrowania, aby utworzyć sieć przepływu danych, zobacz [wskazówki: Korzystanie z przepływu danych w aplikacji formularzy systemu Windows](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka przepływu danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
