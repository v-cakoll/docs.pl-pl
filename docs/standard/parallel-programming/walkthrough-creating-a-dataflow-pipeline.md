---
title: 'Wskazówki: Tworzenie potoku przepływu danych'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dataflow pipelines, creating with TPL
- Task Parallel Library, dataflows
- TPL dataflow library, creating dataflow pipeline
ms.assetid: 69308f82-aa22-4ac5-833d-e748533b58e8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b74e60daced88050413855070c880cd6c1cebfb1
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46569254"
---
# <a name="walkthrough-creating-a-dataflow-pipeline"></a>Wskazówki: Tworzenie potoku przepływu danych
Chociaż można używać <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A?displayProperty=nameWithType>, i <xref:System.Threading.Tasks.Dataflow.DataflowBlock.TryReceive%2A?displayProperty=nameWithType> metody do odbierania komunikatów ze źródła bloki, bloki komunikatów można też połączyć do formularza *potoku przepływu danych*. Potoku przepływu danych to zbiór składników, lub *bloków przepływu danych*, z których każdy wykonuje określone zadanie, które przyczynia się do ogólnego celu. Każdy blok przepływu danych w potoku przepływu danych wykonuje pracę, gdy odbiera wiadomości z innego bloku przepływu danych. Odpowiednio do tego jest do linii montażowej dla samochodów produkcji. Każdego pojazdu korzystał z linii montażowej, jedna stacja składa ramki, kolejny instaluje aparatu i tak dalej. Ponieważ do linii montażowej umożliwia wielu pojazdów do montażu w tym samym czasie, zapewnia większą przepustowość niż łączenie pojazdów kompletnych jednego naraz.

 W tym dokumencie przedstawiono potoku przepływu danych, która pobiera książkę *Iliad Homer* z witryny sieci Web oraz wyszukiwania tekstu, aby dopasować poszczególnych wyrazów za pomocą wyrazów tego odwrotnej kolejności znaków pierwszy wyraz. Tworzenie potoku przepływu danych w tym dokumencie składa się z następujących czynności:  
  
1.  Utwórz bloków przepływu danych, które uczestniczą w potoku.  
  
2.  Połącz każdy blok przepływu danych do następnego bloku w potoku. Każdy blok odbiera jako dane wejściowe dane wyjściowe poprzedniego bloku w potoku.  
  
3.  Dla każdego bloku przepływu danych Utwórz zadanie typu kontynuacja, ustawia kolejny blok do stanu ukończenia, po zakończeniu poprzedniego bloku.  
  
4.  Opublikuj dane do głowy potoku.  
  
5.  Nagłówek potoku należy oznaczyć jako ukończone.  
  
6.  Poczekaj, aż potoku tak, aby wykonać całą pracę.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Odczyt [przepływu danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) przed rozpoczęciem tego instruktażu.  
  
## <a name="creating-a-console-application"></a>Tworzenie aplikacji konsoli  
 W programie Visual Studio Utwórz projekt Visual C# lub Visual Basic aplikacji konsoli. Zainstaluj pakiet System.Threading.Tasks.Dataflow NuGet.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

 Dodaj następujący kod do projektu, aby utworzyć podstawową aplikację.  
  
 [!code-csharp[TPLDataflow_Palindromes#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#2)]
 [!code-vb[TPLDataflow_Palindromes#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromesemptymain.vb#2)]  
  
## <a name="creating-the-dataflow-blocks"></a>Tworzenie bloków przepływu danych  
 Dodaj następujący kod do `Main` metodę w celu utworzenia bloków przepływu danych, które uczestniczą w potoku. Tabela poniżej zawiera podsumowanie rolę każdego członka tego potoku.  
  
 [!code-csharp[TPLDataflow_Palindromes#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#3)]
 [!code-vb[TPLDataflow_Palindromes#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#3)]  
  
|Element członkowski|Typ|Opis|  
|------------|----------|-----------------|  
|`downloadString`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Pobiera tekst książki z sieci Web.|  
|`createWordList`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Dzieli tekst książki na tablicę słów.|  
|`filterWordList`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Usuwa krótkich wyrazów i duplikaty z tablicy programu word.|  
|`findReversedWords`|<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>|Znajduje wszystkie wyrazy w kolekcji tablicy filtrowane programu word, którego wstecznego występuje także w tablicy programu word.|  
|`printReversedWords`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|Wyświetla wyrazów i odpowiednie wyrazów odwrotnej do konsoli.|  
  
 Mimo że można połączyć wiele kroków w potoku przepływu danych w tym przykładzie w jednym kroku, w przykładzie pokazano koncepcji tworzenie wielu zadań niezależnie od przepływu danych w przypadku większych zadań. W przykładzie użyto <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> umożliwiające każdy element członkowski potoku do wykonywania operacji na dane wejściowe i wysyłać wyniki do następnego kroku w potoku. `findReversedWords` Potoku jest <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> obiektu, ponieważ generuje wiele niezależnych danych wyjściowych dla każdej danych wejściowych. Tail potoku, `printReversedWords`, jest <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiektu, ponieważ wykonuje jakąś akcję na dane wejściowe, a nie rezultatów.  
  
## <a name="forming-the-pipeline"></a>Tworzenie potoku  
 Dodaj następujący kod do łączenia każdego bloku do następnego bloku w potoku.  
  
 Gdy wywołujesz <xref:System.Threading.Tasks.Dataflow.DataflowBlock.LinkTo%2A> metodę, aby połączyć z bloku przepływu danych źródłowych do bloku przepływu danych docelowego źródła bloku przepływu danych propaguje dane, aby blok docelowy danych staje się dostępna. Jeśli podasz również <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions> z <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions.PropagateCompletion> ustawiona na wartość true, pomyślnie lub niepowodzeniem zakończenia w potoku jednym bloku ukończenia kolejny blok spowoduje, że w potoku.
  
 [!code-csharp[TPLDataflow_Palindromes#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#4)]
 [!code-vb[TPLDataflow_Palindromes#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#4)]  
  
## <a name="posting-data-to-the-pipeline"></a>Publikowanie danych z potokiem  
 Dodaj następujący kod do opublikowania adresu URL książki *Iliad Homer* do głowy potoku przepływu danych.  
  
 [!code-csharp[TPLDataflow_Palindromes#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#6)]
 [!code-vb[TPLDataflow_Palindromes#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#6)]  
  
 W tym przykładzie użyto <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A?displayProperty=nameWithType> synchronicznie wysyłać dane do głowy potoku. Użyj <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A?displayProperty=nameWithType> metody, gdy asynchronicznie musi wysyłać dane do węzła przepływu danych.  
  
## <a name="completing-pipeline-activity"></a>Kończenie działania potoku  
 Dodaj następujący kod, aby oznaczyć nagłówek potoku jako ukończone. Nagłówek potoku propaguje jego zakończenie, po przetwarza wszystkie buforowane wiadomości.
  
 [!code-csharp[TPLDataflow_Palindromes#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#7)]
 [!code-vb[TPLDataflow_Palindromes#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#7)]  
  
 W tym przykładzie wysyła jednego adresu URL za pośrednictwem potoku przepływu danych do przetworzenia. Jeśli wyślesz więcej niż jeden zestaw danych wejściowych za pomocą potoku, wywołaj <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A?displayProperty=nameWithType> metoda po przesłaniu wszystkie dane wejściowe. Możesz pominąć ten krok, jeśli aplikacja nie ma dobrze zdefiniowanego punktu jaką dane nie są już dostępne lub aplikacja nie ma czekać na potoku zakończyć.  
  
## <a name="waiting-for-the-pipeline-to-finish"></a>Oczekiwanie na potoku do zakończenia  
 Dodaj następujący kod, aby czekać na potoku zakończyć. Ogólny operacja została zakończona, po zakończeniu tail potoku.  
  
 [!code-csharp[TPLDataflow_Palindromes#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#8)]
 [!code-vb[TPLDataflow_Palindromes#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#8)]  
  
 Możesz poczekać na zakończenie przepływu danych z żadnym z wątków, lub z wielu wątków w tym samym czasie.  
  
## <a name="the-complete-example"></a>Kompletny przykład  
 Poniższy przykład pokazuje kompletny kod dla tego przewodnika.  
  
 [!code-csharp[TPLDataflow_Palindromes#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#1)]
 [!code-vb[TPLDataflow_Palindromes#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#1)]  
  
## <a name="next-steps"></a>Następne kroki  
 W tym przykładzie wysyła jeden adres URL do przetwarzania za pośrednictwem potoku przepływu danych. Jeśli wyślesz więcej niż jedną wartość danych wejściowych za pomocą potoku, można wprowadzać formularza równoległości do aplikacji, który jest podobny, jak przenieść części za pomocą fabryki samochodów. Podczas pierwszego elementu członkowskiego potok wysyła jego wynik do drugiego elementu członkowskiego, może przetwarzać inny element równocześnie, jak drugi element członkowski przetwarza pierwszego wyniku.  
  
 Równoległość, które odbywa się za pomocą potoków przepływu danych jest znany jako *gruboziarnistych równoległości* ponieważ zwykle składa się z mniejszej liczby, bardziej złożone zadania. Możesz również użyć bardziej *równoległość drobnoziarnistą* mniejsze, krótko działających zadań w potoku przepływu danych. W tym przykładzie `findReversedWords` potoku używa [PLINQ](parallel-linq-plinq.md) do przetworzenia wiele elementów na liście zadań w sposób równoległy. Użycie równoległość drobnoziarnistą w potoku gruboziarnistych może zwiększyć ogólną przepływność.  
  
 Możesz również nawiązać bloku przepływu danych źródłowych wiele bloków docelowych, aby utworzyć *przepływu danych sieci*. Przeciążona wersja <xref:System.Threading.Tasks.Dataflow.DataflowBlock.LinkTo%2A> metoda przyjmuje <xref:System.Predicate%601> obiekt, który definiuje, czy blok docelowy akceptuje każdy komunikat na podstawie jej wartości. Większość przepływu danych typów bloku, które działają jako źródła oferują wiadomości do wszystkich bloków docelowym, w kolejności, w których były one połączone, dopóki jeden z bloków akceptuje tej wiadomości. Za pomocą tego mechanizmu filtrowania, można utworzyć systemów bloków przepływu danych w połączonych, które bezpośrednie niektórych danych za pomocą ścieżek i innych danych za pośrednictwem inną ścieżkę. Na przykład, który używa filtrowania, aby utworzyć sieć przepływu danych, zobacz [wskazówki: Korzystanie z przepływu danych w aplikacji Windows Forms](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
## <a name="see-also"></a>Zobacz także

- [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
