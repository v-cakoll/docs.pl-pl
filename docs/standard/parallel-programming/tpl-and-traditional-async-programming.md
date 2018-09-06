---
title: Programowanie asynchroniczne w TPL i standardowym .NET Framework
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, with other asynchronous models
ms.assetid: e7b31170-a156-433f-9f26-b1fc7cd1776f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8024fe6673b39a611c55eb55742bcfd981300e7e
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43883951"
---
# <a name="tpl-and-traditional-net-framework-asynchronous-programming"></a>Programowanie asynchroniczne w TPL i standardowym .NET Framework
Program .NET Framework zawiera następujące dwa standardowe wzorce do wykonywania operacji asynchronicznych I/O-granicę i powiązany obliczeniowych:  
  
-   Modelu programowania asynchronicznego (APM), w której operacje asynchroniczne są reprezentowane przez parę początek/koniec metody takie jak <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> i <xref:System.IO.Stream.EndRead%2A?displayProperty=nameWithType>.  
  
-   Oparte na zdarzeniach wzorca asynchronicznego (EAP), w której operacje asynchroniczne są reprezentowane przez parę metody lub zdarzenia, które noszą *OperationName*Async i *OperationName*ukończone, na przykład <xref:System.Net.WebClient.DownloadStringAsync%2A?displayProperty=nameWithType> i <xref:System.Net.WebClient.DownloadStringCompleted?displayProperty=nameWithType>. (EAP została wprowadzona w .NET Framework w wersji 2.0).  
  
 Biblioteka zadań równoległych (TPL) może służyć w różny sposób w połączeniu z oboma wzorami asynchronicznymi. Należy udostępnić operacje zarówno APM, jak i EAP jako zadania dla konsumentów biblioteki lub udostępnić wzorców APM, ale ich wewnętrznego wdrażania za pomocą obiektów zadań. W obu przypadkach za pomocą obiektów zadań można uprościć kod i korzystać z zalet przydatne następujące funkcje:  
  
-   Rejestrowanie wywołań zwrotnych, w postaci kontynuacji zadań, w dowolnym momencie po uruchomieniu zadania.  
  
-   Koordynowanie wielu operacji, które są wykonywane w odpowiedzi na `Begin_` metody, używając <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> i <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> metod, lub <xref:System.Threading.Tasks.Task.WaitAll%2A> metody lub <xref:System.Threading.Tasks.Task.WaitAny%2A> metody.  
  
-   Hermetyzuj operacji asynchronicznych I/O-granicę i powiązany obliczeniowych w tym samym obiekcie zadania.  
  
-   Monitorowanie stanu obiektu zadania.  
  
-   Kieruj stan operacji do obiektu zadania przy użyciu <xref:System.Threading.Tasks.TaskCompletionSource%601>.  
  
## <a name="wrapping-apm-operations-in-a-task"></a>Zawijanie operacje APM w zadaniu  
 Zarówno <xref:System.Threading.Tasks.TaskFactory?displayProperty=nameWithType> i <xref:System.Threading.Tasks.TaskFactory%601?displayProperty=nameWithType> klasy zapewniają kilka przeciążeń <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> metod, które pozwalają na hermetyzację parę APM początek/koniec metody w jednym <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> wystąpienia. Różne przeciążenia pomieścić wszystkie pary metoda początek/koniec mających od zera do trzech parametrów wejściowych.  
  
 Dla pary, które mają `End` metody, które zwracają wartość (`Function` w języku Visual Basic), należy użyć metod w <xref:System.Threading.Tasks.TaskFactory%601> które tworzą <xref:System.Threading.Tasks.Task%601>. Dla `End` metody, które zwracają void (`Sub` w języku Visual Basic), należy użyć metod w <xref:System.Threading.Tasks.TaskFactory> które tworzą <xref:System.Threading.Tasks.Task>.  
  
 Dla tych kilka przypadków, w którym `Begin` metoda ma więcej niż trzech parametrów lub zawiera `ref` lub `out` Parametry dodatkowe `FromAsync` przeciążenia, które hermetyzują tylko `End` metody są dostarczane.  
  
 W poniższym przykładzie pokazano podpis dla `FromAsync` przeciążenia, które odpowiada <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> i <xref:System.IO.FileStream.EndRead%2A?displayProperty=nameWithType> metody. To przeciążenie przyjmuje trzy parametry wejściowe, w następujący sposób.  
  
 [!code-csharp[FromAsync#01](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#01)]
 [!code-vb[FromAsync#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#01)]  
  
 Pierwszy parametr jest <xref:System.Func%606> delegat, który pasuje do podpisu <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> metody. Drugi parametr jest <xref:System.Func%602> delegata, która przyjmuje <xref:System.IAsyncResult> i zwraca `TResult`. Ponieważ <xref:System.IO.FileStream.EndRead%2A> zwraca jako liczba całkowita, kompilator wnioskuje typ `TResult` jako <xref:System.Int32> i typ tworzonego zadania jako <xref:System.Threading.Tasks.Task>. Cztery ostatnie parametry są identyczne z tymi w <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> metody:  
  
-   Bufor do przechowywania danych plików.  
  
-   Przesunięcie w buforze, od którego należy rozpocząć zapisywanie danych.  
  
-   Maksymalna ilość danych do odczytu z pliku.  
  
-   Opcjonalnie obiekt, który przechowuje dane o stanie zdefiniowane przez użytkownika do przekazania do wywołania zwrotnego.  
  
### <a name="using-continuewith-for-the-callback-functionality"></a>Za pomocą ContinueWith dla funkcji wywołania zwrotnego  
 Jeśli potrzebujesz dostępu do danych w pliku, a nie tylko liczbę bajtów, <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> metoda nie jest wystarczające. Zamiast tego należy użyć <xref:System.Threading.Tasks.Task>, którego `Result` właściwość zawiera dane pliku. Można to zrobić, dodając kontynuacja z oryginalnym zadaniem. Kontynuacja wykonuje pracę, która może być zwykle przeprowadzona przez <xref:System.AsyncCallback> delegować. Jest wywoływana po ukończeniu zadania poprzedzającego i bufor danych została wypełniona. ( <xref:System.IO.FileStream> Obiekt powinien zostać zamknięty przed zwróceniem.)  
  
 Poniższy przykład przedstawia sposób zwrócenia <xref:System.Threading.Tasks.Task> która hermetyzuje pary BeginRead/EndRead można wywołać <xref:System.IO.FileStream> klasy.  
  
 [!code-csharp[FromAsync#03](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#03)]
 [!code-vb[FromAsync#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#03)]  
  
 Metoda może następnie być wywoływana, w następujący sposób.  
  
 [!code-csharp[FromAsync#04](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#04)]
 [!code-vb[FromAsync#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#04)]  
  
### <a name="providing-custom-state-data"></a>Zapewniając dane o stanie niestandardowe  
 W przypadku typowych <xref:System.IAsyncResult> operacji, jeśli Twoje <xref:System.AsyncCallback> delegata wymaga niektóre dane stanów niestandardowych, trzeba przekazać go za pośrednictwem ostatnim parametrem `Begin` metody, tak, aby dane mogą być umieszczone w <xref:System.IAsyncResult> obiekt, który jest po pewnym czasie przekazywany do metody wywołania zwrotnego. Zazwyczaj nie jest wymagane podczas `FromAsync` metody są używane. Jeśli dane niestandardowe jest znany do kontynuacji, następnie go mogą być przechwytywane bezpośrednio w delegacie kontynuacji. Poniższy przykład jest podobny do poprzedniego przykładu, ale zamiast badanie `Result` właściwości zadania poprzedzającego, kontynuacja sprawdza dane stanów niestandardowych, które jest dostępne do pełnomocnika użytkownika kontynuacji.  
  
 [!code-csharp[FromAsync#05](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#05)]
 [!code-vb[FromAsync#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#05)]  
  
### <a name="synchronizing-multiple-fromasync-tasks"></a>Synchronizowanie wielu zadań FromAsync  
 Statyczne <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> i <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> metody zapewniają dodatkową elastyczność, gdy jest używana w połączeniu z `FromAsync` metody. Poniższy przykład pokazuje, jak zainicjować wiele operacji asynchronicznych operacji We/Wy, a następnie poczekaj, aż wszystkie z nich na ukończenie wykonywania kontynuację.  
  
 [!code-csharp[FromAsync#06](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#06)]
 [!code-vb[FromAsync#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#06)]  
  
### <a name="fromasync-tasks-for-only-the-end-method"></a>Zadania FromAsync tylko metody End  
 Dla tych kilka przypadków, w którym `Begin` metoda wymaga więcej niż trzy parametry wejściowe, albo `ref` lub `out` parametry, można użyć `FromAsync` przeciążenia, na przykład <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%28System.IAsyncResult%2CSystem.Func%7BSystem.IAsyncResult%2C%600%7D%29?displayProperty=nameWithType>, reprezentujące tylko `End`metody. Metody te można również w każdym scenariuszu, w którym są przekazywane <xref:System.IAsyncResult> i chcesz hermetyzować go w zadaniu.  
  
 [!code-csharp[FromAsync#07](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#07)]
 [!code-vb[FromAsync#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#07)]  
  
### <a name="starting-and-canceling-fromasync-tasks"></a>Uruchamianie i anulowanie zadań FromAsync  
 Zadanie zwrócone przez `FromAsync` metoda ma stan WaitingForActivation i po utworzeniu zadania zostanie uruchomiony w systemie w pewnym momencie. Jeśli użytkownik podejmie próbę wywołania uruchomienie takiego zadania, zostanie wygenerowany wyjątek.  
  
 Nie można anulować `FromAsync` zadania, ponieważ podstawowych interfejsów API .NET Framework aktualnie nie obsługuje anulowanie w toku pliku lub we/wy sieci. Można dodawać funkcjonalność odwołania do metody, która hermetyzuje `FromAsync` wywołanie, ale może odpowiedzieć tylko anulowania przed `FromAsync` o nazwie lub po jej zakończeniu (na przykład w zadanie kontynuacji).  
  
 Niektórych klas, które obsługują protokół EAP, na przykład <xref:System.Net.WebClient>, obsługują anulowania i można zintegrować tę funkcjonalność natywnych anulowania przy użyciu tokenów anulowania.  
  
## <a name="exposing-complex-eap-operations-as-tasks"></a>Udostępnianie EAP złożone operacje jako zadania  
 Używanie biblioteki TPL nie zapewnia żadnych metod, które zostały zaprojektowane specjalnie w celu hermetyzacji oparte na zdarzeniach operację asynchroniczną w tym samym sposób `FromAsync` rodziny zawijania metody <xref:System.IAsyncResult> wzorca. Zapewnia jednak TPL <xref:System.Threading.Tasks.TaskCompletionSource%601?displayProperty=nameWithType> klasy, która może służyć do reprezentowania każdego dowolnego zestawu operacji co <xref:System.Threading.Tasks.Task%601>. Operacje mogą być synchroniczna lub asynchroniczna i może być powiązana We/Wy i/lub powiązany obliczeniowych.  
  
 Poniższy przykład pokazuje, jak używać <xref:System.Threading.Tasks.TaskCompletionSource%601> do udostępnienia zestawu asynchronicznego <xref:System.Net.WebClient> operacje dla kodu klienta jako podstawowy <xref:System.Threading.Tasks.Task%601>. Metoda pozwala wprowadzić tablicę adresów URL sieci Web i termin lub nazwę do wyszukania, a następnie zwraca liczbę przypadków, gdy wyszukiwany termin występuje w każdej lokacji.  
  
 [!code-csharp[FromAsync#10](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/snippet10.cs#10)]
 [!code-vb[FromAsync#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/snippet10.vb#10)]  
  
 Aby uzyskać pełniejszy przykład, który zawiera dodatkowe wyjątków i pokazuje, jak wywołać metodę z poziomu kodu klienta, zobacz [porady: zawijanie wzorów EAP w zadaniu](../../../docs/standard/parallel-programming/how-to-wrap-eap-patterns-in-a-task.md).  
  
 Należy pamiętać, że dowolne zadanie, które jest tworzony przez <xref:System.Threading.Tasks.TaskCompletionSource%601> zostanie uruchomione przez tego TaskCompletionSource i, w związku z tym, kod użytkownika nie powinien wywoływać metodę uruchamiania dla tego zadania.  
  
## <a name="implementing-the-apm-pattern-by-using-tasks"></a>Implementacja wzorca APM przy użyciu zadań  
 W niektórych scenariuszach może być pożądane, aby udostępnić bezpośrednio <xref:System.IAsyncResult> wzorca za pomocą pary metoda początek/koniec w interfejsie API. Na przykład możesz chcieć zachować spójność z istniejących interfejsów API lub zautomatyzowane narzędzia, które wymagają tego wzorca. W takich przypadkach można użyć zadania uprościć, jak wzorzec APM są implementowane wewnętrznie.  
  
 Poniższy przykład pokazuje sposób wykorzystania zadań do zaimplementowania parę APM początek/koniec metody dla metoda długotrwałych powiązany obliczeniowych.  
  
 [!code-csharp[FromAsync#09](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#09)]
 [!code-vb[FromAsync#09](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#09)]  
  
## <a name="using-the-streamextensions-sample-code"></a>Za pomocą StreamExtensions przykładowy kod  
 W pliku Streamextensions.cs [przykłady dotyczące programowania równoległego za pomocą programu .NET Framework 4](https://code.msdn.microsoft.com/ParExtSamples), zawiera kilka implementacji odwołania, które używają obiektów zadań asynchronicznych pliku i we/wy sieci.  
  
## <a name="see-also"></a>Zobacz także

- [Biblioteka zadań równoległych (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
