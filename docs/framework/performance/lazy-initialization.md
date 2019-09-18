---
title: Inicjalizacja z opóźnieniem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lazy initialization in .NET, introduction
ms.assetid: 56b4ae5c-4745-44ff-ad78-ffe4fcde6b9b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 549030b7e5f7544f593e5aa481a6dc85d5a85329
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046413"
---
# <a name="lazy-initialization"></a>Inicjalizacja z opóźnieniem
*Inicjalizacja* z opóźnieniem obiektu oznacza, że jego tworzenie jest odroczone do czasu jego pierwszego użycia. (W tym temacie warunki inicjalizacji z opóźnieniem i *utworzenia wystąpienia* z opóźnieniem są równoznaczne). Inicjalizacja z opóźnieniem służy głównie do poprawy wydajności, unikania obliczeń wasteful i zmniejszania wymagań dotyczących pamięci programu. Są to najczęstsze scenariusze:  
  
- Gdy masz obiekt, który jest kosztowny do utworzenia i program może go nie używać. Załóżmy na przykład, że masz w pamięci `Customer` obiekt, który `Orders` ma właściwość, która `Order` zawiera dużą tablicę obiektów, która ma zostać zainicjowana, wymaga połączenia z bazą danych. Jeśli użytkownik nigdy nie monituje o wyświetlenie zamówień lub użycie danych w obliczeniach, nie istnieje powód, aby użyć pamięci systemowej lub cykle obliczeniowe do jego utworzenia. Za pomocą `Lazy<Orders>` do deklarowania `Orders` obiektu do inicjowania z opóźnieniem można uniknąć marnowania zasobów systemowych, gdy obiekt nie jest używany.  
  
- Gdy masz obiekt, który jest kosztowny do utworzenia, i chcesz odroczyć jego tworzenie do momentu ukończenia innych kosztownych operacji. Załóżmy na przykład, że program ładuje kilka wystąpień obiektów podczas uruchamiania, ale tylko niektóre z nich są wymagane od razu. Wydajność uruchamiania programu można poprawić, odwołując inicjalizację obiektów, które nie są wymagane do momentu utworzenia wymaganych obiektów.  
  
 Chociaż można napisać własny kod w celu wykonania inicjalizacji z opóźnieniem, zalecamy użycie <xref:System.Lazy%601> zamiast tego. <xref:System.Lazy%601>i powiązane typy obsługują również bezpieczeństwo wątków i zapewniają zasady propagacji spójnych wyjątków.  
  
 Poniższa tabela zawiera listę typów, które zawiera .NET Framework w wersji 4, aby włączyć inicjalizację z opóźnieniem w różnych scenariuszach.  
  
|Typ|Opis|  
|----------|-----------------|  
|<xref:System.Lazy%601>|Klasa otoki, która zapewnia semantykę inicjacji z opóźnieniem dla każdej biblioteki klas lub typu zdefiniowanego przez użytkownika.|  
|<xref:System.Threading.ThreadLocal%601>|<xref:System.Lazy%601> Przypomina z tą różnicą, że zapewnia semantykę inicjacji z opóźnieniem w zależności od wątku. Każdy wątek ma dostęp do własnej unikatowej wartości.|  
|<xref:System.Threading.LazyInitializer>|Zapewnia zaawansowane `static` metody`Shared` inicjacji obiektów (w Visual Basic) w odniesieniu do opóźnionej inicjalizacji obiektu bez nakładu pracy klasy.|  
  
## <a name="basic-lazy-initialization"></a>Podstawowa Inicjalizacja z opóźnieniem  
 Aby zdefiniować typ inicjowania z opóźnieniem, na przykład `MyType`, użyj `Lazy<MyType>` (`Lazy(Of MyType)` w Visual Basic), jak pokazano w poniższym przykładzie. Jeśli w <xref:System.Lazy%601> konstruktorze nie zostanie przesłany delegat, opakowany typ jest tworzony przy <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> użyciu, gdy zostanie uzyskany pierwszy raz. Jeśli typ nie ma konstruktora bez parametrów, zgłaszany jest wyjątek czasu wykonywania.  
  
 W poniższym przykładzie Załóżmy, że `Orders` jest klasą zawierającą `Order` tablicę obiektów pobranych z bazy danych. Obiekt zawiera wystąpienie, ale w zależności od akcji użytkownika `Orders` , dane z obiektu mogą nie być wymagane. `Orders` `Customer`  
  
 [!code-csharp[Lazy#1](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#1)]
 [!code-vb[Lazy#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#1)]  
  
 Można również przekazać delegata w <xref:System.Lazy%601> konstruktorze, który wywołuje określone przeciążenie konstruktora dla opakowanego typu podczas tworzenia, i wykonać wszelkie inne wymagane kroki inicjowania, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Lazy#2](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#2)]
 [!code-vb[Lazy#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#2)]  
  
 Po utworzeniu obiektu z opóźnieniem żadne wystąpienie elementu `Orders` nie zostanie utworzone <xref:System.Lazy%601.Value%2A> do momentu uzyskania dostępu do właściwości zmiennej opóźnionej po raz pierwszy. Przy pierwszym dostępie opakowany typ jest tworzony i zwracany i przechowywany dla dowolnego przyszłego dostępu.  
  
 [!code-csharp[Lazy#3](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#3)]
 [!code-vb[Lazy#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#3)]  
  
 <xref:System.Lazy%601> Obiekt zawsze zwraca ten sam obiekt lub wartość, z którą została zainicjowana. W związku z <xref:System.Lazy%601.Value%2A> tym właściwość jest tylko do odczytu. W <xref:System.Lazy%601.Value%2A> przypadku przechowywania typu referencyjnego nie można przypisać do niego nowego obiektu. (Można jednak zmienić wartość jego pól publicznych i właściwości.). W <xref:System.Lazy%601.Value%2A> przypadku przechowywania typu wartości nie można zmodyfikować jego wartości. Niemniej jednak można utworzyć nową zmienną, wywołując Konstruktor zmiennej ponownie przy użyciu nowych argumentów.  
  
 [!code-csharp[Lazy#4](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#4)]
 [!code-vb[Lazy#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#4)]  
  
 Nowe wystąpienie z opóźnieniem, takie jak wcześniejszy, nie tworzy `Orders` wystąpienia przed <xref:System.Lazy%601.Value%2A> pierwszym uzyskaniem dostępu do jego właściwości.  
  
### <a name="thread-safe-initialization"></a>Inicjacja bezpieczna wątkowo  
 Domyślnie <xref:System.Lazy%601> obiekty są bezpieczne wątkowo. Oznacza to, że jeśli Konstruktor nie określi rodzaju bezpieczeństwa wątków, <xref:System.Lazy%601> tworzone obiekty są bezpieczne wątkowo. W scenariuszach wielowątkowych pierwszy wątek uzyskuje dostęp <xref:System.Lazy%601.Value%2A> do właściwości obiektu bezpiecznego <xref:System.Lazy%601> wątkowo inicjuje go dla wszystkich kolejnych operacji dostępu we wszystkich wątkach, a wszystkie wątki współużytkują te same dane. W związku z tym nie ma znaczenia, który wątek inicjuje obiekt, a warunki wyścigu są niegroźne.  
  
> [!NOTE]
> Tę spójność można zwiększyć do warunków błędów przy użyciu buforowania wyjątków. Aby uzyskać więcej informacji, zobacz następną sekcję [wyjątki w odniesieniu do obiektów z opóźnieniem](lazy-initialization.md#ExceptionsInLazyObjects).  
  
 Poniższy przykład pokazuje, że to samo `Lazy<int>` wystąpienie ma tę samą wartość dla trzech oddzielnych wątków.  
  
 [!code-csharp[Lazy#8](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#8)]
 [!code-vb[Lazy#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#8)]  
  
 Jeśli wymagane są osobne dane w każdym wątku, użyj <xref:System.Threading.ThreadLocal%601> typu, zgodnie z opisem w dalszej części tego tematu.  
  
 Niektóre <xref:System.Lazy%601> konstruktory mają parametr logiczny o `isThreadSafe` nazwie, który <xref:System.Lazy%601.Value%2A> służy do określenia, czy właściwość będzie dostępna z wielu wątków. Jeśli zamierzasz uzyskać dostęp do właściwości z tylko jednego wątku, Przekaż `false` , aby uzyskać nieznacznie korzyść wydajności. Jeśli zamierzasz uzyskać dostęp do właściwości z wielu wątków, Przekaż `true` , aby <xref:System.Lazy%601> poinstruować wystąpienie o prawidłowym obsłudze warunków wyścigu, w których jeden wątek zgłasza wyjątek w czasie inicjacji.  
  
 Niektóre <xref:System.Lazy%601> konstruktory <xref:System.Threading.LazyThreadSafetyMode> mają parametr o `mode`nazwie. Konstruktory te zapewniają dodatkowy tryb zabezpieczeń wątków. W poniższej tabeli przedstawiono, w jaki sposób bezpieczeństwo <xref:System.Lazy%601> wątku obiektu ma wpływ na parametry konstruktora, które określają bezpieczeństwo wątku. Każdy Konstruktor ma co najwyżej jeden taki parametr.  
  
|Bezpieczeństwo wątku obiektu|`LazyThreadSafetyMode``mode` parametr|Parametr `isThreadSafe` logiczny|Brak parametrów zabezpieczeń wątku|  
|---------------------------------|---------------------------------------------|--------------------------------------|---------------------------------|  
|W pełni bezpieczny wątkowo; tylko jeden wątek w czasie próbuje zainicjować wartość.|<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>|`true`|Tak.|  
|Nie jest bezpieczny dla wątków.|<xref:System.Threading.LazyThreadSafetyMode.None>|`false`|Nie dotyczy.|  
|W pełni bezpieczny wątkowo; możliwość zainicjowania wartości przez rasę wątków.|<xref:System.Threading.LazyThreadSafetyMode.PublicationOnly>|Nie dotyczy.|Nie dotyczy.|  
  
 Jak tabela pokazuje <xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication?displayProperty=nameWithType> , określanie `mode` dla parametru jest `isThreadSafe` taka sama jak określenie `true` parametru, i określenie <xref:System.Threading.LazyThreadSafetyMode.None?displayProperty=nameWithType> jest taka sama jak określanie `false`.  
  
 Określenie <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly?displayProperty=nameWithType> zezwala wielu wątkom na próbę <xref:System.Lazy%601> zainicjowania wystąpienia. Tylko jeden wątek może wygrać ten wyścigu, a wszystkie pozostałe wątki odbierają wartość, która została zainicjowana przez wątek zakończony powodzeniem. Jeśli wyjątek jest zgłaszany w wątku podczas inicjowania, ten wątek nie otrzymuje wartości ustawionej przez wątek zakończony powodzeniem. Wyjątki nie są buforowane, dlatego kolejna próba uzyskania dostępu <xref:System.Lazy%601.Value%2A> do właściwości może skutkować pomyślnym zainicjowaniem. Różni się to od sposobu traktowania wyjątków w innych trybach, które opisano w następnej sekcji. Aby uzyskać więcej informacji, zobacz <xref:System.Threading.LazyThreadSafetyMode> Wyliczenie.  
  
<a name="ExceptionsInLazyObjects"></a>   
## <a name="exceptions-in-lazy-objects"></a>Wyjątki w obiektach z opóźnieniem  
 Jak wspomniano wcześniej, <xref:System.Lazy%601> obiekt zawsze zwraca ten sam obiekt lub wartość, która została zainicjowana, i w <xref:System.Lazy%601.Value%2A> związku z tym właściwość jest tylko do odczytu. W przypadku włączenia buforowania wyjątków ten niezmienności również rozszerza na zachowanie wyjątków. Jeśli obiekt zainicjowany z opóźnieniem ma włączone buforowanie wyjątków i zgłasza wyjątek z metody inicjującej podczas <xref:System.Lazy%601.Value%2A> pierwszego dostępu do właściwości, ten sam wyjątek jest zgłaszany przy każdej kolejnej próbie <xref:System.Lazy%601.Value%2A> uzyskania dostępu do właściwości . Innymi słowy, Konstruktor opakowanego typu nigdy nie jest ponownie wywoływany, nawet w scenariuszach wielowątkowych. W związku z tym obiektniemożezgłosićwyjątkudlajednegodostępuizwrócićwartościwkolejnymdostępie.<xref:System.Lazy%601>  
  
 Buforowanie wyjątków jest włączane w przypadku użycia <xref:System.Lazy%601?displayProperty=nameWithType> dowolnego konstruktora, który przyjmuje metodę inicjującą (`valueFactory` parametr); na przykład jest on `Lazy(T)(Func(T))`włączony w przypadku użycia konstruktora. Jeśli Konstruktor pobiera <xref:System.Threading.LazyThreadSafetyMode> również wartość (`mode` parametr), określ <xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication?displayProperty=nameWithType> lub <xref:System.Threading.LazyThreadSafetyMode.None?displayProperty=nameWithType>. Określenie metody inicjującej umożliwia buforowanie wyjątków dla tych dwóch trybów. Metoda inicjacji może być bardzo prosta. Na przykład może wywołać konstruktora bez parametrów `T`dla: `new Lazy<Contents>(() => new Contents(), mode)` w C#, lub `New Lazy(Of Contents)(Function() New Contents())` w Visual Basic. Jeśli używasz <xref:System.Lazy%601?displayProperty=nameWithType> konstruktora, który nie określa metody inicjacji, wyjątki, które są zgłaszane przez konstruktora bez parametrów dla `T` nie są buforowane. Aby uzyskać więcej informacji, zobacz <xref:System.Threading.LazyThreadSafetyMode> Wyliczenie.  
  
> [!NOTE]
> Jeśli <xref:System.Lazy%601> utworzysz obiekt <xref:System.Threading.LazyThreadSafetyMode.None?displayProperty=nameWithType> `false` `isThreadSafe` <xref:System.Lazy%601> z`mode` parametrem konstruktora ustawionym na lub parametrem konstruktora ustawionym na, musisz uzyskać dostęp do obiektu z pojedynczego wątku lub podać własny synchronizacji. Dotyczy to wszystkich aspektów obiektu, w tym buforowania wyjątków.  
  
 Jak wskazano w poprzedniej sekcji, <xref:System.Lazy%601> obiekty utworzone przez określanie <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly?displayProperty=nameWithType> wyjątków traktują się inaczej. W <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly>przypadku wielu wątków może konkurować, aby <xref:System.Lazy%601> zainicjować wystąpienie. W takim przypadku wyjątki nie są buforowane, a próby uzyskania dostępu <xref:System.Lazy%601.Value%2A> do właściwości mogą być kontynuowane do momentu pomyślnego inicjalizacji.  
  
 Poniższa tabela zawiera podsumowanie sposobu, w <xref:System.Lazy%601> jaki konstruktory kontrolują buforowanie wyjątków.  
  
|Konstruktor|Tryb bezpieczny wątku|Używa metody inicjującej|Wyjątki są buforowane|  
|-----------------|------------------------|--------------------------------|---------------------------|  
|Opóźnione (T) ()|(<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>)|Nie|Nie|  
|Opóźniony (T) (Func (T))|(<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>)|Tak|Tak|  
|Opóźniony (T) (wartość logiczna)|`True`(<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>) lub `false` (<xref:System.Threading.LazyThreadSafetyMode.None>)|Nie|Nie|  
|Opóźniony (T) (Func (T), wartość logiczna)|`True`(<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>) lub `false` (<xref:System.Threading.LazyThreadSafetyMode.None>)|Tak|Tak|  
|Lazy(T)(LazyThreadSafetyMode)|Określony przez użytkownika|Nie|Nie|  
|Opóźniony (T) (Func (T), LazyThreadSafetyMode)|Określony przez użytkownika|Tak|Nie, jeśli użytkownik <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly>określi; w przeciwnym razie, tak.|  
  
## <a name="implementing-a-lazy-initialized-property"></a>Implementowanie właściwości inicjowania z opóźnieniem  
 Aby zaimplementować Właściwość publiczną przy użyciu inicjowania z opóźnieniem, Zdefiniuj pole zapasowe właściwości jako <xref:System.Lazy%601>i <xref:System.Lazy%601.Value%2A> Zwróć właściwość z `get` metody dostępu do właściwości.  
  
 [!code-csharp[Lazy#5](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#5)]
 [!code-vb[Lazy#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#5)]  
  
 Właściwość <xref:System.Lazy%601.Value%2A> jest tylko do odczytu; w związku z tym właściwość, która ujawnia ją, `set` nie ma metody dostępu. Jeśli wymagana jest właściwość <xref:System.Lazy%601> odczytu/zapisu dla obiektu `set` , metoda dostępu musi utworzyć nowy <xref:System.Lazy%601> obiekt i przypisać go do magazynu zapasowego. Metoda dostępu musi utworzyć wyrażenie lambda zwracające nową wartość właściwości, która została przekazana `set` do metody dostępu, i przekazać do konstruktora wyrażenie lambda dla nowego <xref:System.Lazy%601> obiektu. `set` Następny dostęp <xref:System.Lazy%601.Value%2A> do właściwości spowoduje zainicjowanie nowej <xref:System.Lazy%601>, a jej <xref:System.Lazy%601.Value%2A> właściwość zwróci nową wartość, która została przypisana do właściwości. Przyczyną tego rozmieszczenia zawiłe jest zachowanie ochrony wielowątkowości wbudowanej <xref:System.Lazy%601>. W przeciwnym razie metody dostępu do właściwości będą musiały buforować pierwszą wartość zwróconą <xref:System.Lazy%601.Value%2A> przez właściwość i modyfikować tylko buforowaną wartość i należy napisać własny kod bezpieczny dla wątków, aby to zrobić. Ze względu na dodatkowe inicjalizacje wymagane przez właściwość odczytu/zapisu, które są <xref:System.Lazy%601> obsługiwane przez obiekt, wydajność może nie być akceptowalna. Ponadto w zależności od konkretnego scenariusza może być wymagana dodatkowa koordynacja, aby uniknąć sytuacji wyścigu między metodami tworzenia i pobierania.  
  
## <a name="thread-local-lazy-initialization"></a>Inicjalizacja z opóźnieniem wątku lokalnego  
 W niektórych scenariuszach wielowątkowych można przydzielić każdemu wątkowi swoje prywatne dane. Takie dane są nazywane *danymi lokalnymi wątku*. W .NET Framework w wersji 3,5 i starszych można zastosować `ThreadStatic` atrybut do zmiennej statycznej w celu ustawienia jej jako wątku lokalnego. Jednak użycie `ThreadStatic` atrybutu może prowadzić do delikatnych błędów. Na przykład nawet podstawowe instrukcje inicjowania spowodują, że zmienna zostanie zainicjowana tylko na pierwszym wątku, który uzyskuje do niego dostęp, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Lazy#6](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#6)]
 [!code-vb[Lazy#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#6)]  
  
 We wszystkich innych wątkach zmienna zostanie zainicjowana przy użyciu wartości domyślnej (zero). Alternatywnie w .NET Framework w wersji 4, można użyć <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> typu, aby utworzyć zmienną lokalną wątku, która jest inicjowana we wszystkich wątkach <xref:System.Action%601> przez podaną delegata. W poniższym przykładzie wszystkie wątki, do których uzyskuje dostęp `counter` , będą widzieć wartość początkową 1.  
  
 [!code-csharp[Lazy#7](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#7)]
 [!code-vb[Lazy#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#7)]  
  
 <xref:System.Threading.ThreadLocal%601>Zawija swój obiekt w taki sam sposób jak <xref:System.Lazy%601>w przypadku następujących zasadniczych różnic:  
  
- Każdy wątek inicjuje zmienną lokalną wątku przy użyciu własnych danych prywatnych, które nie są dostępne z innych wątków.  
  
- <xref:System.Threading.ThreadLocal%601.Value%2A?displayProperty=nameWithType> Właściwość jest do odczytu i zapisu i może być modyfikowana dowolną liczbę razy. Może to mieć wpływ na propagację wyjątku, na przykład `get` jedna operacja może zgłosić wyjątek, ale następny z nich może pomyślnie zainicjować wartość.  
  
- Jeśli nie podano delegata inicjalizacji, <xref:System.Threading.ThreadLocal%601> program zainicjuje swój opakowany typ przy użyciu wartości domyślnej typu. W tym przypadku <xref:System.Threading.ThreadLocal%601> jest spójny <xref:System.ThreadStaticAttribute> z atrybutem.  
  
 Poniższy przykład pokazuje, że każdy wątek, który uzyskuje `ThreadLocal<int>` dostęp do wystąpienia, pobiera własną unikatową kopię danych.  
  
 [!code-csharp[Lazy#9](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#9)]
 [!code-vb[Lazy#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#9)]  
  
## <a name="thread-local-variables-in-parallelfor-and-foreach"></a>Zmienne lokalne wątku równolegle. dla i ForEach  
 W przypadku użycia <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> metody lub <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> metody do iteracji równolegle ze źródłami danych można użyć przeciążenia, które mają wbudowaną obsługę danych wątku lokalnego. W tych metodach można uzyskać dostęp do zasobów lokalnych przy użyciu lokalnych delegatów do tworzenia, uzyskiwania dostępu i czyszczenia danych. Aby uzyskać więcej informacji, zobacz [jak: Napisz Parallel. for — pętla ze zmiennymi](../../standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md) lokalnymi wątku i [instrukcje: Napisz równoległą pętlę. ForEach ze zmiennymi](../../standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-partition-local-variables.md)lokalnymi partycji.  
  
## <a name="using-lazy-initialization-for-low-overhead-scenarios"></a>Korzystanie z inicjowania z opóźnieniem dla scenariuszy o niskim obciążeniu  
 W scenariuszach, w których konieczne jest zainicjowanie dużej liczby obiektów z opóźnieniem, można zdecydować, że opakowanie każdego obiektu <xref:System.Lazy%601> w wymaga zbyt dużej ilości pamięci lub zbyt wielu zasobów obliczeniowych. Można też mieć rygorystyczne wymagania dotyczące sposobu, w jaki jest ujawniane Inicjowanie z opóźnieniem. W takich `static` przypadkach można użyć metod (`Shared` w <xref:System.Threading.LazyInitializer?displayProperty=nameWithType> Visual Basic) klasy do opóźnionego inicjowania każdego <xref:System.Lazy%601>obiektu bez zawijania go w wystąpieniu.  
  
 W poniższym przykładzie Załóżmy, że zamiast zawijać cały `Orders` obiekt w jednym <xref:System.Lazy%601> obiekcie, są inicjowane z opóźnieniem pojedyncze `Order` obiekty tylko wtedy, gdy są wymagane.  
  
 [!code-csharp[Lazy#10](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#10)]
 [!code-vb[Lazy#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#10)]  
  
 W tym przykładzie należy zauważyć, że procedura inicjacji jest wywoływana na każdej iteracji pętli. W scenariuszach wielowątkowych pierwszy wątek do wywołania procedury inicjowania jest taki, którego wartość jest widoczna dla wszystkich wątków. Późniejsze wątki również wywołują procedurę inicjowania, ale ich wyniki nie są używane. Jeśli ten rodzaj potencjalnego warunku wyścigu nie jest akceptowalny, Użyj przeciążenia <xref:System.Threading.LazyInitializer.EnsureInitialized%2A?displayProperty=nameWithType> , które przyjmuje argument logiczny i obiekt synchronizacji.  
  
## <a name="see-also"></a>Zobacz także

- [Zarządzana wątkowość — podstawy](../../standard/threading/managed-threading-basics.md)
- [Wątki i wątkowość](../../standard/threading/threads-and-threading.md)
- [Biblioteka zadań równoległych (TPL)](../../standard/parallel-programming/task-parallel-library-tpl.md)
- [Instrukcje: Wykonaj opóźnione inicjowanie obiektów](how-to-perform-lazy-initialization-of-objects.md)
