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
ms.openlocfilehash: 339365381b1fa2c777cead3c75bfe783f7af800e
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588290"
---
# <a name="walkthrough-creating-a-dataflow-pipeline"></a>Wskazówki: Tworzenie potoku przepływu danych
Chociaż można użyć <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A?displayProperty=nameWithType>programu <xref:System.Threading.Tasks.Dataflow.DataflowBlock.TryReceive%2A?displayProperty=nameWithType> , i metod do odbierania wiadomości z bloków źródłowych, można również połączyć bloki wiadomości w celu utworzenia *potoku przepływu danych.* Potok przepływu danych to seria składników lub *bloków przepływu danych,* z których każdy wykonuje określone zadanie, które przyczynia się do większego celu. Każdy blok przepływu danych w potoku przepływu danych wykonuje pracę po odebraniu wiadomości z innego bloku przepływu danych. Analogią do tego jest linia montażowa do produkcji samochodów. Gdy każdy pojazd przechodzi przez linię montażową, jedna stacja montuje ramę, następna instaluje silnik i tak dalej. Ponieważ linia montażowa umożliwia montaż wielu pojazdów w tym samym czasie, zapewnia lepszą przepustowość niż montaż kompletnych pojazdów po jednym na raz.

 Ten dokument pokazuje potok przepływu danych, który pobiera książkę *Iliady Homera* ze strony internetowej i przeszukuje tekst, aby dopasować poszczególne słowa do słów, które odwracają znaki pierwszego słowa. Tworzenie potoku przepływu danych w tym dokumencie składa się z następujących kroków:  
  
1. Tworzenie bloków przepływu danych, które uczestniczą w potoku.  
  
2. Połącz każdy blok przepływu danych z następnym blokiem w potoku. Każdy blok odbiera jako dane wejściowe dane wyjściowe poprzedniego bloku w potoku.  
  
3. Dla każdego bloku przepływu danych utwórz zadanie kontynuacji, które ustawia następny blok w stanie ukończonym po zakończeniu poprzedniego bloku.  
  
4. Opublikuj dane do głowicy rurociągu.  
  
5. Oznacz głowicę rurociągu jako ukończoną.  
  
6. Poczekaj, aż potok zakończy wszystkie prace.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Przed rozpoczęciem tego przewodnika należy przeczytać [przepływ](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) danych.  
  
## <a name="creating-a-console-application"></a>Tworzenie aplikacji konsoli  
 W programie Visual Studio utwórz projekt aplikacji konsoli Visual C# lub Visual Basic. Zainstaluj pakiet System.Threading.Tasks.Dataflow NuGet.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

 Dodaj następujący kod do projektu, aby utworzyć podstawową aplikację.  
  
 [!code-csharp[TPLDataflow_Palindromes#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#2)]
 [!code-vb[TPLDataflow_Palindromes#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromesemptymain.vb#2)]  
  
## <a name="creating-the-dataflow-blocks"></a>Tworzenie bloków przepływu danych  
 Dodaj następujący kod `Main` do metody, aby utworzyć bloki przepływu danych, które uczestniczą w potoku. Poniższa tabela podsumowuje rolę każdego członka potoku.  
  
 [!code-csharp[TPLDataflow_Palindromes#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#3)]
 [!code-vb[TPLDataflow_Palindromes#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#3)]  
  
|Członek|Typ|Opis|  
|------------|----------|-----------------|  
|`downloadString`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Pobiera tekst książki z sieci Web.|  
|`createWordList`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Oddziela tekst książki na tablicę słów.|  
|`filterWordList`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Usuwa krótkie wyrazy i duplikaty z tablicy wyrazów.|  
|`findReversedWords`|<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>|Znajduje wszystkie wyrazy w kolekcji tablicy rozfiltrowanego wyrazu, których odwrotność występuje również w tablicy wyrazów.|  
|`printReversedWords`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|Wyświetla wyrazy i odpowiadające im słowa wsteczne do konsoli.|  
  
 Chociaż można połączyć wiele kroków w potoku przepływu danych w tym przykładzie w jeden krok, w przykładzie ilustruje koncepcję tworzenia wielu zadań niezależnego przepływu danych w celu wykonania większego zadania. W przykładzie <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> użyto do włączenia każdego elementu członkowskiego potoku do wykonywania operacji na jego danych wejściowych i wysyłania wyników do następnego kroku w potoku. Element `findReversedWords` członkowski potoku <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> jest obiektem, ponieważ generuje wiele niezależnych wyjść dla każdego wejścia. Ogon potoku , `printReversedWords`jest <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiektem, ponieważ wykonuje akcję na jego danych wejściowych i nie daje wynik.  
  
## <a name="forming-the-pipeline"></a>Tworzenie potoku  
 Dodaj następujący kod, aby połączyć każdy blok z następnym blokiem w potoku.  
  
 Po wywołaniu <xref:System.Threading.Tasks.Dataflow.DataflowBlock.LinkTo%2A> metody łączenia bloku przepływu danych źródłowych z docelowym blokiem przepływu danych blok przepływu danych źródłowego propaguje dane do bloku docelowego w miarę udostępniania danych. Jeśli podasz <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions> <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions.PropagateCompletion> również ustawioną wartość true, pomyślne lub nieudane ukończenie jednego bloku w potoku spowoduje ukończenie następnego bloku w potoku.
  
 [!code-csharp[TPLDataflow_Palindromes#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#4)]
 [!code-vb[TPLDataflow_Palindromes#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#4)]  
  
## <a name="posting-data-to-the-pipeline"></a>Księgowanie danych w potoku  
 Dodaj poniższy kod, aby opublikować adres URL książki *Iliad homer* do szefa potoku przepływu danych.  
  
 [!code-csharp[TPLDataflow_Palindromes#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#6)]
 [!code-vb[TPLDataflow_Palindromes#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#6)]  
  
 W tym <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A?displayProperty=nameWithType> przykładzie użyto do synchronicznie wysyłać dane do głowicy potoku. Użyj <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A?displayProperty=nameWithType> metody, gdy należy asynchronicznie wysłać dane do węzła przepływu danych.  
  
## <a name="completing-pipeline-activity"></a>Ukończenie działania potoku  
 Dodaj następujący kod, aby oznaczyć głowicę potoku jako ukończoną. Szef potoku propaguje jego ukończenie po przetwarzaniu wszystkich buforowanych komunikatów.
  
 [!code-csharp[TPLDataflow_Palindromes#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#7)]
 [!code-vb[TPLDataflow_Palindromes#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#7)]  
  
 W tym przykładzie wysyła jeden adres URL za pośrednictwem potoku przepływu danych do przetworzenia. Jeśli wyślesz więcej niż jedno dane <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A?displayProperty=nameWithType> wejściowe za pośrednictwem potoku, wywołaj metodę po przesłaniu wszystkich danych wejściowych. Ten krok można pominąć, jeśli aplikacja nie ma dobrze zdefiniowanego punktu, w którym dane nie są już dostępne lub aplikacja nie musi czekać na zakończenie potoku.  
  
## <a name="waiting-for-the-pipeline-to-finish"></a>Oczekiwanie na zakończenie potoku  
 Dodaj następujący kod, aby poczekać na zakończenie potoku. Operacja ogólna jest zakończona po zakończeniu ogona potoku.  
  
 [!code-csharp[TPLDataflow_Palindromes#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#8)]
 [!code-vb[TPLDataflow_Palindromes#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#8)]  
  
 Można czekać na ukończenie przepływu danych z dowolnego wątku lub z wielu wątków w tym samym czasie.  
  
## <a name="the-complete-example"></a>Kompletny przykład  
 W poniższym przykładzie przedstawiono pełny kod dla tego przewodnika.  
  
 [!code-csharp[TPLDataflow_Palindromes#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#1)]
 [!code-vb[TPLDataflow_Palindromes#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#1)]  
  
## <a name="next-steps"></a>Następne kroki  
 W tym przykładzie wysyła jeden adres URL do przetwarzania za pośrednictwem potoku przepływu danych. Jeśli wyślesz więcej niż jedną wartość wejściową za pośrednictwem potoku, można wprowadzić formę równoległości do aplikacji, która przypomina, jak części mogą poruszać się po fabryce samochodów. Gdy pierwszy element członkowski potoku wysyła jego wynik do drugiego elementu członkowskiego, może przetwarzać inny element równolegle jako drugi element członkowski przetwarza pierwszy wynik.  
  
 Równoległość, która jest osiągana przy użyciu potoków przepływu danych jest znany jako *równoległości gruboziarnistej,* ponieważ zazwyczaj składa się z mniejszej liczby większych zadań. Można również użyć bardziej *szczegółowe równoległości* mniejszych, krótko działających zadań w potoku przepływu danych. W tym przykładzie element członkowski `findReversedWords` potoku używa [PLINQ](introduction-to-plinq.md) do przetwarzania wielu elementów na liście pracy równolegle. Zastosowanie drobnoziarnistego równoległości w rurociągu gruboziarnistym może poprawić ogólną przepustowość.  
  
 Można również połączyć źródłowy blok przepływu danych z wieloma blokami docelowymi, aby utworzyć *sieć przepływu danych*. Przeciążona wersja <xref:System.Threading.Tasks.Dataflow.DataflowBlock.LinkTo%2A> metody przyjmuje <xref:System.Predicate%601> obiekt, który definiuje, czy blok docelowy akceptuje każdą wiadomość na podstawie jego wartości. Większość typów bloków przepływu danych, które działają jako źródła oferują wiadomości do wszystkich połączonych bloków docelowych, w kolejności, w jakiej zostały połączone, dopóki jeden z bloków nie zaakceptuje tej wiadomości. Za pomocą tego mechanizmu filtrowania można utworzyć systemy połączonych bloków przepływu danych, które kierują określone dane przez jedną ścieżkę i inne dane przez inną ścieżkę. Na przykład, który używa filtrowania do tworzenia sieci przepływu danych, zobacz [Przewodnik: Korzystanie z przepływu danych w aplikacji formularzy systemu Windows](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
## <a name="see-also"></a>Zobacz też

- [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
