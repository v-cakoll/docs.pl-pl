---
title: Inicjalizacja z opóźnieniem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lazy initialization in .NET, introduction
ms.assetid: 56b4ae5c-4745-44ff-ad78-ffe4fcde6b9b
ms.openlocfilehash: 54776304e484fc7f1db2c56b102034ed0e8650c0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130319"
---
# <a name="lazy-initialization"></a>Inicjalizacja z opóźnieniem
*Inicjalizacja z opóźnieniem* obiektu oznacza, że jego tworzenie jest odroczone do czasu jego pierwszego użycia. (W tym temacie warunki *inicjalizacji z opóźnieniem* i *utworzenia wystąpienia z opóźnieniem* są równoznaczne). Inicjalizacja z opóźnieniem służy głównie do poprawy wydajności, unikania obliczeń wasteful i zmniejszania wymagań dotyczących pamięci programu. Są to najczęstsze scenariusze:  
  
- Gdy masz obiekt, który jest kosztowny do utworzenia i program może go nie używać. Załóżmy na przykład, że masz w pamięci obiekt `Customer`, który ma właściwość `Orders`, która zawiera dużą tablicę obiektów `Order`, które mają być inicjowane, wymaga połączenia z bazą danych. Jeśli użytkownik nigdy nie monituje o wyświetlenie zamówień lub użycie danych w obliczeniach, nie istnieje powód, aby użyć pamięci systemowej lub cykle obliczeniowe do jego utworzenia. Przy użyciu `Lazy<Orders>` do deklarowania obiektu `Orders` do inicjowania z opóźnieniem można uniknąć marnowania zasobów systemowych, gdy obiekt nie jest używany.  
  
- Gdy masz obiekt, który jest kosztowny do utworzenia, i chcesz odroczyć jego tworzenie do momentu ukończenia innych kosztownych operacji. Załóżmy na przykład, że program ładuje kilka wystąpień obiektów podczas uruchamiania, ale tylko niektóre z nich są wymagane od razu. Wydajność uruchamiania programu można poprawić, odwołując inicjalizację obiektów, które nie są wymagane do momentu utworzenia wymaganych obiektów.  
  
 Chociaż można napisać własny kod w celu wykonania inicjowania z opóźnieniem, zalecamy użycie <xref:System.Lazy%601> zamiast tego. <xref:System.Lazy%601> i powiązane typy obsługują również bezpieczne dla wątków i zapewniają zasady propagacji spójnych wyjątków.  
  
 Poniższa tabela zawiera listę typów, które zawiera .NET Framework w wersji 4, aby włączyć inicjalizację z opóźnieniem w różnych scenariuszach.  
  
|Typ|Opis|  
|----------|-----------------|  
|<xref:System.Lazy%601>|Klasa otoki, która zapewnia semantykę inicjacji z opóźnieniem dla każdej biblioteki klas lub typu zdefiniowanego przez użytkownika.|  
|<xref:System.Threading.ThreadLocal%601>|Przypomina <xref:System.Lazy%601>, z tą różnicą, że zapewnia semantykę inicjacji z opóźnieniem w zależności od wątku. Każdy wątek ma dostęp do własnej unikatowej wartości.|  
|<xref:System.Threading.LazyInitializer>|Zapewnia zaawansowane metody `static` (`Shared` w Visual Basic) dla inicjowania opóźnionych obiektów bez nakładu pracy klasy.|  
  
## <a name="basic-lazy-initialization"></a>Podstawowa Inicjalizacja z opóźnieniem  
 Aby zdefiniować typ inicjowania z opóźnieniem, na przykład `MyType`, użyj `Lazy<MyType>` (`Lazy(Of MyType)` w Visual Basic), jak pokazano w poniższym przykładzie. Jeśli delegat nie zostanie przesłany w konstruktorze <xref:System.Lazy%601>, opakowany typ jest tworzony przy użyciu <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> podczas pierwszego dostępu do właściwości Value. Jeśli typ nie ma konstruktora bez parametrów, zgłaszany jest wyjątek czasu wykonywania.  
  
 W poniższym przykładzie Załóżmy, że `Orders` jest klasą zawierającą tablicę obiektów `Order` pobranych z bazy danych. Obiekt `Customer` zawiera wystąpienie `Orders`, ale w zależności od akcji użytkownika dane z obiektu `Orders` mogą nie być wymagane.  
  
 [!code-csharp[Lazy#1](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#1)]
 [!code-vb[Lazy#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#1)]  
  
 Można również przekazać delegata w konstruktorze <xref:System.Lazy%601>, który wywołuje określone przeciążenie konstruktora dla opakowanego typu podczas tworzenia, i wykonać wszelkie inne wymagane kroki inicjowania, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Lazy#2](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#2)]
 [!code-vb[Lazy#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#2)]  
  
 Po utworzeniu obiektu z opóźnieniem żadne wystąpienie `Orders` jest tworzone do momentu uzyskania dostępu do właściwości <xref:System.Lazy%601.Value%2A> zmiennej opóźnionej po raz pierwszy. Przy pierwszym dostępie opakowany typ jest tworzony i zwracany i przechowywany dla dowolnego przyszłego dostępu.  
  
 [!code-csharp[Lazy#3](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#3)]
 [!code-vb[Lazy#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#3)]  
  
 Obiekt <xref:System.Lazy%601> zawsze zwraca ten sam obiekt lub wartość, z którą została zainicjowana. W związku z tym Właściwość <xref:System.Lazy%601.Value%2A> jest tylko do odczytu. Jeśli <xref:System.Lazy%601.Value%2A> przechowuje typ referencyjny, nie można przypisać do niego nowego obiektu. (Można jednak zmienić wartość jego pól publicznych i właściwości.). Jeśli <xref:System.Lazy%601.Value%2A> przechowuje typ wartości, nie można zmodyfikować jego wartości. Niemniej jednak można utworzyć nową zmienną, wywołując Konstruktor zmiennej ponownie przy użyciu nowych argumentów.  
  
 [!code-csharp[Lazy#4](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#4)]
 [!code-vb[Lazy#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#4)]  
  
 Nowe wystąpienie z opóźnieniem, takie jak wcześniejszy, nie tworzy wystąpienia `Orders` do momentu uzyskania dostępu do jego właściwości <xref:System.Lazy%601.Value%2A>.  
  
### <a name="thread-safe-initialization"></a>Inicjacja bezpieczna wątkowo  
 Domyślnie obiekty <xref:System.Lazy%601> są bezpieczne wątkowo. Oznacza to, że jeśli Konstruktor nie określi rodzaju bezpieczeństwa wątków, tworzone <xref:System.Lazy%601> obiekty są bezpieczne wątkowo. W scenariuszach wielowątkowych pierwszy wątek, aby uzyskać dostęp do właściwości <xref:System.Lazy%601.Value%2A> obiektu <xref:System.Lazy%601> bezpiecznego wątkowo inicjuje go dla wszystkich kolejnych dostępu we wszystkich wątkach, a wszystkie wątki współużytkują te same dane. W związku z tym nie ma znaczenia, który wątek inicjuje obiekt, a warunki wyścigu są niegroźne.  
  
> [!NOTE]
> Tę spójność można zwiększyć do warunków błędów przy użyciu buforowania wyjątków. Aby uzyskać więcej informacji, zobacz następną sekcję [wyjątki w odniesieniu do obiektów z opóźnieniem](lazy-initialization.md#ExceptionsInLazyObjects).  
  
 Poniższy przykład pokazuje, że to samo wystąpienie `Lazy<int>` ma taką samą wartość dla trzech oddzielnych wątków.  
  
 [!code-csharp[Lazy#8](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#8)]
 [!code-vb[Lazy#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#8)]  
  
 Jeśli wymagane są osobne dane w każdym wątku, użyj typu <xref:System.Threading.ThreadLocal%601>, zgodnie z opisem w dalszej części tego tematu.  
  
 Niektóre konstruktory <xref:System.Lazy%601> mają parametr logiczny o nazwie `isThreadSafe`, który służy do określenia, czy właściwość <xref:System.Lazy%601.Value%2A> będzie dostępna z wielu wątków. Jeśli zamierzasz uzyskać dostęp do właściwości z tylko jednego wątku, Przekaż `false`, aby uzyskać niewielkie korzyści z wydajności. Jeśli zamierzasz uzyskać dostęp do właściwości z wielu wątków, Przekaż `true`, aby poinstruować wystąpienie <xref:System.Lazy%601> o prawidłowo obsłużyć warunki wyścigu, w których jeden wątek zgłasza wyjątek w czasie inicjacji.  
  
 Niektóre konstruktory <xref:System.Lazy%601> mają parametr <xref:System.Threading.LazyThreadSafetyMode> o nazwie `mode`. Konstruktory te zapewniają dodatkowy tryb zabezpieczeń wątków. W poniższej tabeli przedstawiono, w jaki sposób bezpieczeństwo wątku obiektu <xref:System.Lazy%601> ma wpływ na parametry konstruktora, które określają bezpieczeństwo wątku. Każdy Konstruktor ma co najwyżej jeden taki parametr.  
  
|Bezpieczeństwo wątku obiektu|`LazyThreadSafetyMode` parametr `mode`|Wartość parametru Boolean `isThreadSafe`|Brak parametrów zabezpieczeń wątku|  
|---------------------------------|---------------------------------------------|--------------------------------------|---------------------------------|  
|W pełni bezpieczny wątkowo; tylko jeden wątek w czasie próbuje zainicjować wartość.|<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>|`true`|Tak.|  
|Nie jest bezpieczny dla wątków.|<xref:System.Threading.LazyThreadSafetyMode.None>|`false`|Nie dotyczy.|  
|W pełni bezpieczny wątkowo; możliwość zainicjowania wartości przez rasę wątków.|<xref:System.Threading.LazyThreadSafetyMode.PublicationOnly>|Nie dotyczy.|Nie dotyczy.|  
  
 Jak tabela pokazuje, określanie <xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication?displayProperty=nameWithType> dla parametru `mode` jest taka sama jak określenie `true` dla parametru `isThreadSafe`, a określenie <xref:System.Threading.LazyThreadSafetyMode.None?displayProperty=nameWithType> jest taka sama jak w przypadku określenia `false`.  
  
 Określenie <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly?displayProperty=nameWithType> umożliwia wielu wątkom próba zainicjowania wystąpienia <xref:System.Lazy%601>. Tylko jeden wątek może wygrać ten wyścigu, a wszystkie pozostałe wątki odbierają wartość, która została zainicjowana przez wątek zakończony powodzeniem. Jeśli wyjątek jest zgłaszany w wątku podczas inicjowania, ten wątek nie otrzymuje wartości ustawionej przez wątek zakończony powodzeniem. Wyjątki nie są buforowane, dlatego kolejna próba uzyskania dostępu do właściwości <xref:System.Lazy%601.Value%2A> może spowodować pomyślne zainicjowanie. Różni się to od sposobu traktowania wyjątków w innych trybach, które opisano w następnej sekcji. Aby uzyskać więcej informacji, zobacz Wyliczenie <xref:System.Threading.LazyThreadSafetyMode>.  
  
<a name="ExceptionsInLazyObjects"></a>   
## <a name="exceptions-in-lazy-objects"></a>Wyjątki w obiektach z opóźnieniem  
 Jak wspomniano wcześniej, obiekt <xref:System.Lazy%601> zawsze zwraca ten sam obiekt lub wartość, która została zainicjowana, i w związku z tym Właściwość <xref:System.Lazy%601.Value%2A> jest tylko do odczytu. W przypadku włączenia buforowania wyjątków ten niezmienności również rozszerza na zachowanie wyjątków. Jeśli obiekt zainicjowany z opóźnieniem ma włączone buforowanie wyjątków i zgłasza wyjątek z metody inicjującej podczas pierwszego dostępu do właściwości <xref:System.Lazy%601.Value%2A>, ten sam wyjątek jest zgłaszany przy każdej kolejnej próbie uzyskania dostępu do właściwości <xref:System.Lazy%601.Value%2A>. Innymi słowy, Konstruktor opakowanego typu nigdy nie jest ponownie wywoływany, nawet w scenariuszach wielowątkowych. W związku z tym obiekt <xref:System.Lazy%601> nie może zgłosić wyjątku dla jednego dostępu i zwrócić wartości przy kolejnym dostępie.  
  
 Buforowanie wyjątków jest włączone w przypadku korzystania z dowolnego konstruktora <xref:System.Lazy%601?displayProperty=nameWithType>, który przyjmuje metodę inicjującą (`valueFactory` parametr); na przykład jest włączona, gdy używasz konstruktora `Lazy(T)(Func(T))`. Jeśli Konstruktor przyjmuje również wartość <xref:System.Threading.LazyThreadSafetyMode> (parametr`mode`), określ <xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication?displayProperty=nameWithType> lub <xref:System.Threading.LazyThreadSafetyMode.None?displayProperty=nameWithType>. Określenie metody inicjującej umożliwia buforowanie wyjątków dla tych dwóch trybów. Metoda inicjacji może być bardzo prosta. Na przykład może wywołać konstruktora bez parametrów dla `T`: `new Lazy<Contents>(() => new Contents(), mode)` w C#, lub `New Lazy(Of Contents)(Function() New Contents())` w Visual Basic. Jeśli używasz konstruktora <xref:System.Lazy%601?displayProperty=nameWithType>, który nie określa metody inicjacji, wyjątki, które są zgłaszane przez konstruktora bez parametrów dla `T` nie są buforowane. Aby uzyskać więcej informacji, zobacz Wyliczenie <xref:System.Threading.LazyThreadSafetyMode>.  
  
> [!NOTE]
> Jeśli utworzysz obiekt <xref:System.Lazy%601> z parametrem konstruktora `isThreadSafe` ustawionym na `false` lub parametr konstruktora `mode` ustawiony na <xref:System.Threading.LazyThreadSafetyMode.None?displayProperty=nameWithType>, musisz uzyskać dostęp do obiektu <xref:System.Lazy%601> z pojedynczego wątku lub udostępnić własną synchronizację. Dotyczy to wszystkich aspektów obiektu, w tym buforowania wyjątków.  
  
 Jak wskazano w poprzedniej sekcji, <xref:System.Lazy%601> obiekty utworzone przez określenie <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly?displayProperty=nameWithType> Traktuj wyjątki inaczej. W przypadku <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly>wiele wątków może konkurować do inicjowania wystąpienia <xref:System.Lazy%601>. W takim przypadku wyjątki nie są buforowane, a próby uzyskania dostępu do właściwości <xref:System.Lazy%601.Value%2A> mogą być kontynuowane do momentu pomyślnego inicjalizacji.  
  
 Poniższa tabela zawiera podsumowanie sposobu, w jaki konstruktory <xref:System.Lazy%601> sterują buforowaniem wyjątków.  
  
|Konstruktor|Tryb bezpieczny wątku|Używa metody inicjującej|Wyjątki są buforowane|  
|-----------------|------------------------|--------------------------------|---------------------------|  
|Opóźnione (T) ()|(<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>)|Nie|Nie|  
|Opóźniony (T) (Func (T))|(<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>)|Tak|Tak|  
|Opóźniony (T) (wartość logiczna)|`True` (<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>) lub `false` (<xref:System.Threading.LazyThreadSafetyMode.None>)|Nie|Nie|  
|Opóźniony (T) (Func (T), wartość logiczna)|`True` (<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>) lub `false` (<xref:System.Threading.LazyThreadSafetyMode.None>)|Tak|Tak|  
|Opóźnione (T) (LazyThreadSafetyMode)|Określony przez użytkownika|Nie|Nie|  
|Opóźniony (T) (Func (T), LazyThreadSafetyMode)|Określony przez użytkownika|Tak|Nie, jeśli użytkownik określi <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly>; w przeciwnym razie, tak.|  
  
## <a name="implementing-a-lazy-initialized-property"></a>Implementowanie właściwości inicjowania z opóźnieniem  
 Aby zaimplementować Właściwość publiczną przy użyciu inicjowania z opóźnieniem, Zdefiniuj pole zapasowe właściwości jako <xref:System.Lazy%601>i zwróć Właściwość <xref:System.Lazy%601.Value%2A> z metody dostępu `get` właściwości.  
  
 [!code-csharp[Lazy#5](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#5)]
 [!code-vb[Lazy#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#5)]  
  
 Właściwość <xref:System.Lazy%601.Value%2A> jest tylko do odczytu; w związku z tym właściwość, która uwidacznia jej nie ma dostępu `set`. Jeśli wymagana jest właściwość odczytu/zapisu dla obiektu <xref:System.Lazy%601>, metoda dostępu `set` musi utworzyć nowy obiekt <xref:System.Lazy%601> i przypisać go do magazynu zapasowego. Metoda dostępu `set` musi utworzyć wyrażenie lambda zwracające nową wartość właściwości, która została przekazana do metody dostępu `set` i przekazać wyrażenie lambda do konstruktora dla nowego obiektu <xref:System.Lazy%601>. Kolejne dostęp do właściwości <xref:System.Lazy%601.Value%2A> spowoduje zainicjowanie nowej <xref:System.Lazy%601>, a jej Właściwość <xref:System.Lazy%601.Value%2A> następnie zwróci nową wartość, która została przypisana do właściwości. Przyczyną tego rozmieszczenia zawiłe jest zachowanie ochrony wielowątkowości wbudowanej w <xref:System.Lazy%601>. W przeciwnym razie metody dostępu do właściwości będą musiały buforować pierwszą wartość zwróconą przez właściwość <xref:System.Lazy%601.Value%2A> i modyfikować tylko buforowaną wartość i należy napisać własny kod bezpieczny dla wątków, aby to zrobić. Ze względu na dodatkowe inicjalizacje wymagane przez właściwość odczytu/zapisu, które są obsługiwane przez obiekt <xref:System.Lazy%601>, wydajność może nie być akceptowalna. Ponadto w zależności od konkretnego scenariusza może być wymagana dodatkowa koordynacja, aby uniknąć sytuacji wyścigu między metodami tworzenia i pobierania.  
  
## <a name="thread-local-lazy-initialization"></a>Inicjalizacja z opóźnieniem wątku lokalnego  
 W niektórych scenariuszach wielowątkowych można przydzielić każdemu wątkowi swoje prywatne dane. Takie dane są nazywane *danymi lokalnymi wątku*. W .NET Framework w wersji 3,5 i starszych można zastosować atrybut `ThreadStatic` do zmiennej statycznej w celu ustawienia jej jako wątku lokalnego. Jednak użycie atrybutu `ThreadStatic` może prowadzić do delikatnych błędów. Na przykład nawet podstawowe instrukcje inicjowania spowodują, że zmienna zostanie zainicjowana tylko na pierwszym wątku, który uzyskuje do niego dostęp, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Lazy#6](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#6)]
 [!code-vb[Lazy#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#6)]  
  
 We wszystkich innych wątkach zmienna zostanie zainicjowana przy użyciu wartości domyślnej (zero). Jako alternatywę w .NET Framework w wersji 4, można użyć typu <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType>, aby utworzyć zmienną lokalną wątku, która jest inicjowana we wszystkich wątkach przez podaną delegata <xref:System.Action%601>. W poniższym przykładzie wszystkie wątki, do których uzyskuje dostęp `counter` będzie widziały wartość początkową 1.  
  
 [!code-csharp[Lazy#7](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#7)]
 [!code-vb[Lazy#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#7)]  
  
 <xref:System.Threading.ThreadLocal%601> zawija swój obiekt w taki sam sposób jak <xref:System.Lazy%601>, z następującymi istotnymi różnicami:  
  
- Każdy wątek inicjuje zmienną lokalną wątku przy użyciu własnych danych prywatnych, które nie są dostępne z innych wątków.  
  
- Właściwość <xref:System.Threading.ThreadLocal%601.Value%2A?displayProperty=nameWithType> jest do odczytu i zapisu i może być modyfikowana dowolną liczbę razy. Może to mieć wpływ na propagację wyjątków, na przykład jedna operacja `get` może zgłosić wyjątek, ale następny z nich może pomyślnie zainicjować wartość.  
  
- Jeśli nie podano delegata inicjowania, <xref:System.Threading.ThreadLocal%601> zainicjuje swój opakowany typ przy użyciu wartości domyślnej typu. W tym względzie <xref:System.Threading.ThreadLocal%601> jest spójny z atrybutem <xref:System.ThreadStaticAttribute>.  
  
 Poniższy przykład pokazuje, że każdy wątek, który uzyskuje dostęp do wystąpienia `ThreadLocal<int>` pobiera własną unikatową kopię danych.  
  
 [!code-csharp[Lazy#9](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#9)]
 [!code-vb[Lazy#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#9)]  
  
## <a name="thread-local-variables-in-parallelfor-and-foreach"></a>Zmienne lokalne wątku równolegle. dla i ForEach  
 Korzystając z metody <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> lub <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> do iteracji równolegle ze źródłami danych, można użyć przeciążenia, które mają wbudowaną obsługę danych wątku lokalnego. W tych metodach można uzyskać dostęp do zasobów lokalnych przy użyciu lokalnych delegatów do tworzenia, uzyskiwania dostępu i czyszczenia danych. Aby uzyskać więcej informacji, zobacz [How to: Write a Parallel. for ze zmiennymi lokalnymi wątku](../../standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md) i [instrukcje: pisanie pętli Parallel. Foreach ze zmiennymi lokalnymi partycji](../../standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-partition-local-variables.md).  
  
## <a name="using-lazy-initialization-for-low-overhead-scenarios"></a>Korzystanie z inicjowania z opóźnieniem dla scenariuszy o niskim obciążeniu  
 W scenariuszach, w których konieczne jest zainicjowanie dużej liczby obiektów z opóźnieniem, można zdecydować, że opakowanie każdego obiektu w <xref:System.Lazy%601> wymaga zbyt dużej ilości pamięci lub zbyt wielu zasobów obliczeniowych. Można też mieć rygorystyczne wymagania dotyczące sposobu, w jaki jest ujawniane Inicjowanie z opóźnieniem. W takich przypadkach można użyć metod `static` (`Shared` w Visual Basic) klasy <xref:System.Threading.LazyInitializer?displayProperty=nameWithType> do opóźnionego inicjowania każdego obiektu bez zawijania go w wystąpieniu <xref:System.Lazy%601>.  
  
 W poniższym przykładzie przyjęto założenie, że zamiast zawijania całego obiektu `Orders` w jednym obiekcie <xref:System.Lazy%601>, są inicjowane opóźniono pojedyncze obiekty `Order` tylko wtedy, gdy są one wymagane.  
  
 [!code-csharp[Lazy#10](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#10)]
 [!code-vb[Lazy#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#10)]  
  
 W tym przykładzie należy zauważyć, że procedura inicjacji jest wywoływana na każdej iteracji pętli. W scenariuszach wielowątkowych pierwszy wątek do wywołania procedury inicjowania jest taki, którego wartość jest widoczna dla wszystkich wątków. Późniejsze wątki również wywołują procedurę inicjowania, ale ich wyniki nie są używane. Jeśli ten rodzaj potencjalnego warunku wyścigu nie jest akceptowalny, Użyj przeciążenia <xref:System.Threading.LazyInitializer.EnsureInitialized%2A?displayProperty=nameWithType>, które przyjmuje argument logiczny i obiekt synchronizacji.  
  
## <a name="see-also"></a>Zobacz także

- [Zarządzana wątkowość — podstawy](../../standard/threading/managed-threading-basics.md)
- [Wątki i wątkowość](../../standard/threading/threads-and-threading.md)
- [Biblioteka zadań równoległych (TPL)](../../standard/parallel-programming/task-parallel-library-tpl.md)
- [Instrukcje: wykonywanie inicjowania obiektów z opóźnieniem](how-to-perform-lazy-initialization-of-objects.md)
