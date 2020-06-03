---
title: 'Przewodnik: Tworzenie potoku przepływu danych'
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
ms.openlocfilehash: cfe3296815dc344b0d9d1f7bad1ab4a130380e2b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84284614"
---
# <a name="walkthrough-creating-a-dataflow-pipeline"></a>Przewodnik: Tworzenie potoku przepływu danych
Chociaż można używać <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A?displayProperty=nameWithType> metod, i <xref:System.Threading.Tasks.Dataflow.DataflowBlock.TryReceive%2A?displayProperty=nameWithType> do odbierania komunikatów z bloków źródłowych, można także połączyć bloki komunikatów, aby utworzyć *potok przepływu danych*. Potok przepływu danych to szereg składników lub *bloków przepływu danych*, z których każdy wykonuje konkretne zadanie, które przyczynia się do większego celu. Każdy blok przepływu danych w potoku przepływu danych wykonuje działanie, gdy odbierze komunikat z innego bloku przepływu danych. Analogicznie do tego jest linia montażowa dla produkcji samochodów. Gdy każdy pojazd przechodzi przez linię zestawu, jedna stacja składa się z ramki, a następna z nich instaluje aparat i tak dalej. Ponieważ linia zestawu umożliwia łączenie wielu pojazdów w tym samym czasie, zapewnia lepszą przepływność niż Montaż kompletnych pojazdów pojedynczo.

 W tym dokumencie przedstawiono potok przepływu danych, który pobiera książkę *Iliader* z witryny sieci Web i przeszukuje tekst w celu dopasowania do poszczególnych wyrazów, które odwracają znaki pierwszego wyrazu. Utworzenie potoku przepływu danych w tym dokumencie obejmuje następujące kroki:  
  
1. Utwórz bloki przepływu danych, które uczestniczą w potoku.  
  
2. Połącz każdy blok przepływu danych z następnym blokiem w potoku. Każdy blok odbiera jako dane wyjściowe poprzedniego bloku w potoku.  
  
3. Dla każdego bloku przepływu danych Utwórz zadanie kontynuacji ustawiające następny blok do stanu ukończenia po zakończeniu poprzedniego bloku.  
  
4. Publikuj dane w nagłówku potoku.  
  
5. Oznacz wierzchołek potoku jako zakończony.  
  
6. Poczekaj na zakończenie pracy potoku.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Przeczytaj [przepływu danych](dataflow-task-parallel-library.md) przed rozpoczęciem tego instruktażu.  
  
## <a name="creating-a-console-application"></a>Tworzenie aplikacji konsoli  
 W programie Visual Studio Utwórz projekt aplikacji konsolowej Visual C# lub Visual Basic. Zainstaluj pakiet NuGet system. Threading. Tasks. przepływu danych.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

 Dodaj następujący kod do projektu, aby utworzyć podstawową aplikację.  
  
 [!code-csharp[TPLDataflow_Palindromes#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#2)]
 [!code-vb[TPLDataflow_Palindromes#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromesemptymain.vb#2)]  
  
## <a name="creating-the-dataflow-blocks"></a>Tworzenie bloków przepływu danych  
 Dodaj następujący kod do metody, `Main` Aby utworzyć bloki przepływu danych, które uczestniczą w potoku. W poniższej tabeli zestawiono rolę każdego elementu członkowskiego potoku.  
  
 [!code-csharp[TPLDataflow_Palindromes#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#3)]
 [!code-vb[TPLDataflow_Palindromes#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#3)]  
  
|Członek|Typ|Opis|  
|------------|----------|-----------------|  
|`downloadString`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Pobiera tekst książki z sieci Web.|  
|`createWordList`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Oddziela tekst książki do tablicy wyrazów.|  
|`filterWordList`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Usuwa krótkie słowa i duplikaty z tablicy wyrazów.|  
|`findReversedWords`|<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>|Znajduje wszystkie słowa w filtrowanej kolekcji tablic programu Word, których odwrócenie również występuje w tablicy wyrazów.|  
|`printReversedWords`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|Wyświetla wyrazy i odpowiednie słowa zwrotne do konsoli.|  
  
 Mimo że można połączyć wiele kroków w potoku przepływu danych w tym przykładzie do jednego kroku, przykład ilustruje koncepcję tworzenia wielu niezależnych zadań przepływu danych, aby wykonać większe zadanie. W przykładzie zastosowano, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> Aby umożliwić każdemu elementowi członkowskiemu potoku wykonywanie operacji na danych wejściowych i wysłanie wyników do następnego kroku w potoku. `findReversedWords`Element członkowski potoku jest <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> obiektem, ponieważ produkuje wiele niezależnych danych wyjściowych dla każdego z nich. Ogon potoku, `printReversedWords` , jest <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiektem, ponieważ wykonuje akcję na wejściu i nie tworzy wyniku.  
  
## <a name="forming-the-pipeline"></a>Tworzenie potoku  
 Dodaj następujący kod, aby połączyć każdy blok z następnym blokiem w potoku.  
  
 Po wywołaniu <xref:System.Threading.Tasks.Dataflow.DataflowBlock.LinkTo%2A> metody w celu połączenia źródłowego bloku przepływu danych z docelowym blokiem przepływu danych źródłowy blok przepływu danych propaguje dane do bloku docelowego, ponieważ dane staną się dostępne. Jeśli podano również <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions> <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions.PropagateCompletion> wartość true, pomyślne lub nieudane zakończenie jednego bloku w potoku spowoduje zakończenie następnego bloku w potoku.
  
 [!code-csharp[TPLDataflow_Palindromes#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#4)]
 [!code-vb[TPLDataflow_Palindromes#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#4)]  
  
## <a name="posting-data-to-the-pipeline"></a>Ogłaszanie danych w potoku  
 Dodaj następujący kod, aby ogłosić adres URL książki *Iliader* do szefa potoku przepływu danych.  
  
 [!code-csharp[TPLDataflow_Palindromes#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#6)]
 [!code-vb[TPLDataflow_Palindromes#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#6)]  
  
 Ten przykład używa <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A?displayProperty=nameWithType> do synchronicznego wysyłania danych do szefa potoku. Użyj <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A?displayProperty=nameWithType> metody, gdy musisz asynchronicznie wysyłać dane do węzła przepływu danych.  
  
## <a name="completing-pipeline-activity"></a>Wykonywanie działania potoku  
 Dodaj następujący kod, aby oznaczyć wierzchołek potoku jako zakończony. Przed przetworzeniem wszystkich buforowanych komunikatów szef potoku propaguje jego zakończenie.
  
 [!code-csharp[TPLDataflow_Palindromes#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#7)]
 [!code-vb[TPLDataflow_Palindromes#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#7)]  
  
 Ten przykład wysyła jeden adres URL za pomocą potoku przepływu danych, który ma zostać przetworzony. W przypadku wysyłania więcej niż jednego danych wejściowych za pomocą potoku należy wywołać <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A?displayProperty=nameWithType> metodę po przesłaniu wszystkich danych wejściowych. Możesz pominąć ten krok, jeśli aplikacja nie ma dobrze zdefiniowanego punktu, w którym dane nie są już dostępne lub aplikacja nie musi czekać na zakończenie potoku.  
  
## <a name="waiting-for-the-pipeline-to-finish"></a>Oczekiwanie na zakończenie potoku  
 Dodaj następujący kod, aby poczekać na zakończenie potoku. Operacja ogólna zostanie zakończona po zakończeniu końca potoku.  
  
 [!code-csharp[TPLDataflow_Palindromes#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#8)]
 [!code-vb[TPLDataflow_Palindromes#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#8)]  
  
 Możesz poczekać na zakończenie przepływu danych z dowolnego wątku lub z wielu wątków w tym samym czasie.  
  
## <a name="the-complete-example"></a>Kompletny przykład  
 Poniższy przykład pokazuje kompletny kod dla tego przewodnika.  
  
 [!code-csharp[TPLDataflow_Palindromes#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#1)]
 [!code-vb[TPLDataflow_Palindromes#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#1)]  
  
## <a name="next-steps"></a>Następne kroki  
 Ten przykład wysyła jeden adres URL do przetworzenia przez potok przepływu danych. Jeśli wyślesz więcej niż jedną wartość wejściową za pomocą potoku, możesz wprowadzić równoległą postać do aplikacji przypominającą, jak części mogą być przenoszone przez fabrykę samochodów. Gdy pierwszy element członkowski potoku wysyła swój wynik do drugiego elementu członkowskiego, może przetwarzać inny element równolegle, gdy drugi element członkowski przetwarza pierwszy wynik.  
  
 Równoległość osiągnięta przy użyciu potoków przepływu danych jest określana jako liczba *równoległa* , ponieważ zazwyczaj składa się z mniej i większych zadań. Można również użyć bardziej *precyzyjnie równoległych* zadań o mniejszych, krótkich działaniach w potoku przepływu danych. W tym przykładzie `findReversedWords` element członkowski potoku używa [PLINQ](introduction-to-plinq.md) do przetwarzania wielu elementów na liście zadań równolegle. Użycie precyzyjnych równoległych potoków w powyższej potoku może zwiększyć ogólną przepływność.  
  
 Istnieje również możliwość połączenia źródłowego bloku przepływu danych z wieloma blokami docelowymi w celu utworzenia *sieci przepływu danych*. Przeciążona wersja <xref:System.Threading.Tasks.Dataflow.DataflowBlock.LinkTo%2A> metody przyjmuje <xref:System.Predicate%601> obiekt, który określa, czy blok docelowy akceptuje każdy komunikat na podstawie jego wartości. Większość typów bloków przepływu danych, które pełnią funkcję źródła wiadomości do wszystkich połączonych bloków docelowych w kolejności, w jakiej były połączone, dopóki jeden z bloków nie zaakceptuje tego komunikatu. Korzystając z tego mechanizmu filtrowania, można tworzyć systemy połączonych bloków przepływu danych, które kierują określone dane za pośrednictwem jednej ścieżki i innych danych za pośrednictwem innej ścieżki. Aby uzyskać przykład, który używa filtrowania do tworzenia sieci przepływu danych, zobacz [Przewodnik: używanie przepływu danych w aplikacji Windows Forms](walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
## <a name="see-also"></a>Zobacz też

- [Przepływ danych](dataflow-task-parallel-library.md)
