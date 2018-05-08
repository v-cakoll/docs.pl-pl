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
ms.openlocfilehash: a826121a7f22d1db7287171c5add28e5fcd690cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="lazy-initialization"></a>Inicjalizacja z opóźnieniem
*Inicjalizacja z opóźnieniem* obiektu oznacza, że jej tworzenia została odroczona aż najpierw jest używany. (W tym temacie warunki *incjalizacji* i *opóźnieniem wystąpienia* to samo.) Inicjalizacja z opóźnieniem służy głównie w celu zwiększenia wydajności, uniknąć niepotrzebne obliczeń i zmniejszyć wymagania dotyczące pamięci programu. Są to najbardziej typowych scenariuszy:  
  
-   Gdy został wybrany obiekt, który jest kosztowne, a program nie może używać. Załóżmy na przykład, że masz w pamięci `Customer` obiektu, który ma `Orders` właściwość, która zawiera dużą tablicę `Order` obiekty, które, aby można było zainicjować wymaga połączenia z bazą danych. Jeśli użytkownik nigdy nie żąda umożliwia wyświetlanie zamówień lub użyć danych w obliczeniach, to nie ma żadnych powód użycia pamięci lub obliczeniowych cykle go utworzyć. Za pomocą `Lazy<Orders>` Aby zadeklarować `Orders` obiekt do inicjowania z opóźnieniem, możesz uniknąć traci zasobów systemowych, jeśli obiekt nie jest używany.  
  
-   Gdy został wybrany obiekt, który jest kosztowne i chcesz odroczenie jego tworzenia, aż do zakończenia inne kosztowne operacje. Załóżmy na przykład, że program ładuje kilka wystąpień obiektu podczas uruchamiania, ale tylko niektóre z nich są wymagane natychmiast. Aby zwiększyć wydajność uruchamiania programów, należy odkładanie Inicjowanie obiektów, które nie są wymagane do czasu utworzenia wymaganych obiektów.  
  
 Mimo że można napisać własny kod do wykonania inicjowania z opóźnieniem, zaleca się używanie <xref:System.Lazy%601> zamiast tego. <xref:System.Lazy%601> oraz jego powiązanych typów również obsługuje bezpieczeństwo wątków i zasad propagacji spójne wyjątku.  
  
 Poniższa tabela zawiera listę typów, które .NET Framework w wersji 4 udostępnia umożliwiające Inicjalizacja z opóźnieniem w różnych scenariuszy.  
  
|Typ|Opis|  
|----------|-----------------|  
|<xref:System.Lazy%601>|Klasa otoki, która zapewnia semantyki Inicjalizacja z opóźnieniem biblioteki klas lub typ zdefiniowany przez użytkownika.|  
|<xref:System.Threading.ThreadLocal%601>|Podobny <xref:System.Lazy%601> z tym, że zapewnia semantyki Inicjalizacja z opóźnieniem na zasadzie lokalnej wątku. Każdy wątek ma dostęp do własnej unikatowe wartości.|  
|<xref:System.Threading.LazyInitializer>|Udostępnia zaawansowane `static` (`Shared` w języku Visual Basic) metody incjalizacji obiektów bez nakładów związanych z klasą.|  
  
## <a name="basic-lazy-initialization"></a>Inicjalizacja z opóźnieniem podstawowe  
 Aby zdefiniować opóźnieniem zainicjowany typem, na przykład `MyType`, użyj `Lazy<MyType>` (`Lazy(Of MyType)` w języku Visual Basic), jak pokazano w poniższym przykładzie. Jeśli delegat nie jest przekazywany w <xref:System.Lazy%601> opakowanej typu konstruktora, jest tworzona przy użyciu <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> kiedy najpierw dostępu do właściwości value. Jeśli typ nie ma domyślnego konstruktora, zwracany jest wyjątek czasu wykonywania.  
  
 W poniższym przykładzie przyjęto założenie, że `Orders` jest klasa, która zawiera tablicę `Order` obiekt pobrany z bazy danych. A `Customer` obiekt zawiera wystąpienie `Orders`, ale w zależności od działań użytkownika, danych z `Orders` obiekt nie może być wymagane.  
  
 [!code-csharp[Lazy#1](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#1)]
 [!code-vb[Lazy#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#1)]  
  
 Można również przekazać delegata w <xref:System.Lazy%601> Konstruktor, który wywołuje konstruktor określonego przeciążenia opakowanej typu w czasie tworzenia i wykonaj pozostałe kroki inicjowania, które są wymagane, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Lazy#2](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#2)]
 [!code-vb[Lazy#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#2)]  
  
 Po utworzeniu obiektu opóźnieniem, żadne wystąpienie elementu `Orders` jest tworzony, dopóki <xref:System.Lazy%601.Value%2A> właściwość opóźnieniem zmiennej jest dostępny po raz pierwszy. Na pierwszym dostępie opakowanej typu jest utworzony i zwracane, a następnie przechowywane dla przyszłych dostęp.  
  
 [!code-csharp[Lazy#3](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#3)]
 [!code-vb[Lazy#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#3)]  
  
 A <xref:System.Lazy%601> obiektu zawsze zwraca tego samego obiektu lub wartości, który został zainicjowany. W związku z tym <xref:System.Lazy%601.Value%2A> właściwość jest tylko do odczytu. Jeśli <xref:System.Lazy%601.Value%2A> typ zapisuje odwołanie, nie można przypisać nowy obiekt do niego. (Jednak można zmienić wartość można ustawić pola publiczne i właściwości.) Jeśli <xref:System.Lazy%601.Value%2A> zapisuje wartość typ, nie można zmodyfikować jego wartości. Niemniej jednak można utworzyć nową zmienną za pomocą zmiennej konstruktora ponownie przy użyciu nowych argumentów.  
  
 [!code-csharp[Lazy#4](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#4)]
 [!code-vb[Lazy#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#4)]  
  
 Nowe wystąpienie opóźnieniem, tak jak wcześniej, nie tworzy wystąpienia `Orders` do momentu jego <xref:System.Lazy%601.Value%2A> najpierw dostępu do właściwości.  
  
### <a name="thread-safe-initialization"></a>Inicjowanie obsługujące wielowątkowość  
 Domyślnie <xref:System.Lazy%601> obiekty są wątkowo. Oznacza to, gdy Konstruktor nie został określony rodzaj bezpieczeństwo wątków <xref:System.Lazy%601> tworzy obiekty są wątkowo. W scenariuszach wielowątkowych pierwszym wątkiem dostępu do <xref:System.Lazy%601.Value%2A> właściwości obsługującej wielowątkowość <xref:System.Lazy%601> obiektu inicjowane dla wszystkich kolejnych dostęp na wszystkie wątki i wszystkie wątki udostępnianie tych samych danych. W związku z tym nie ma znaczenia, który wątek inicjuje obiekt i niegroźne są warunki wyścigu.  
  
> [!NOTE]
>  Ten zgodność warunki błędów można rozszerzyć przy użyciu buforowania wyjątek. Aby uzyskać więcej informacji, zobacz następną sekcję, [wyjątków w obiektach opóźnieniem](../../../docs/framework/performance/lazy-initialization.md#ExceptionsInLazyObjects).  
  
 W poniższym przykładzie pokazano, że takie same `Lazy<int>` wystąpienie ma taką samą wartość dla trzech oddzielnych wątkach.  
  
 [!code-csharp[Lazy#8](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#8)]
 [!code-vb[Lazy#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#8)]  
  
 Jeśli potrzebujesz oddzielnych danych na każdy wątek, użyj <xref:System.Threading.ThreadLocal%601> typ, zgodnie z opisem w dalszej części tego tematu.  
  
 Niektóre <xref:System.Lazy%601> konstruktorów mieć parametrów typu Boolean o nazwie `isThreadSafe` używany do określenia czy <xref:System.Lazy%601.Value%2A> właściwość będą mieli dostęp wiele wątków. Jeśli planujesz dostęp do właściwości z tylko jednego wątku, Przekaż `false` korzyści niewielkie wydajności. Jeśli planujesz dostęp do właściwości wiele wątków, Przekaż `true` nakazać programowi <xref:System.Lazy%601> wystąpienia poprawnie obsłużyć wyścigu, w których jeden wątek zgłasza wyjątek w czasie inicjowania.  
  
 Niektóre <xref:System.Lazy%601> mieć konstruktorów <xref:System.Threading.LazyThreadSafetyMode> parametru o nazwie `mode`. Konstruktory te zapewniają tryb awaryjny wątku dodatkowe. W poniższej tabeli przedstawiono, jak bezpieczeństwo wątku <xref:System.Lazy%601> obiektu dotyczy parametrami konstruktora, które określają bezpieczeństwo wątków. Każdy Konstruktor ma co najwyżej jeden taki parametr.  
  
|Bezpieczeństwo wątków obiektu|`LazyThreadSafetyMode` `mode` Parametr|Wartość logiczna `isThreadSafe` parametru|Brak parametrów bezpieczeństwa wątków|  
|---------------------------------|---------------------------------------------|--------------------------------------|---------------------------------|  
|Pełni wątkowo; tylko jeden wątek jednocześnie umożliwia podjęcie próby zainicjowania wartość.|<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>|`true`|Tak.|  
|Nie wątkowo.|<xref:System.Threading.LazyThreadSafetyMode.None>|`false`|Nie dotyczy.|  
|Pełni wątkowo; wątki wyścigu zainicjować wartość.|<xref:System.Threading.LazyThreadSafetyMode.PublicationOnly>|Nie dotyczy.|Nie dotyczy.|  
  
 Jak widać w tabeli, określając <xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication?displayProperty=nameWithType> dla `mode` parametr jest taki sam jak określenie `true` dla `isThreadSafe` parametru i określając <xref:System.Threading.LazyThreadSafetyMode.None?displayProperty=nameWithType> jest taka sama jak określanie `false`.  
  
 Określanie <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly?displayProperty=nameWithType> zezwala na wiele wątków próbuje zainicjować <xref:System.Lazy%601> wystąpienia. Tylko jeden wątek można kupić tej wyścigu i inne wątki wyświetlony wartość, która została zainicjowana przez wątek powiodło się. Jeśli w wątku jest zgłaszany wyjątek podczas inicjowania, wątek nie otrzyma wartość ustawioną przez wątek powiodło się. Wyjątki nie są buforowane, dlatego kolejna próba dostępu do <xref:System.Lazy%601.Value%2A> właściwości może spowodować powiodło się inicjowanie. To różni się od sposobu wyjątki są traktowane w innych trybów, opisany w następnej sekcji. Aby uzyskać więcej informacji, zobacz <xref:System.Threading.LazyThreadSafetyMode> wyliczenia.  
  
<a name="ExceptionsInLazyObjects"></a>   
## <a name="exceptions-in-lazy-objects"></a>Wyjątki w obiektach opóźnieniem  
 Jak wspomniano wcześniej, <xref:System.Lazy%601> obiektu zawsze zwraca tego samego obiektu lub wartości, który został zainicjowany, i w związku z tym <xref:System.Lazy%601.Value%2A> właściwość jest tylko do odczytu. Po włączeniu buforowanie wyjątek, to immutability uwzględniającą zachowanie wyjątku. Jeśli obiekt opóźnieniem zainicjować jest włączone buforowanie wyjątku i zgłasza wyjątek jej metodę inicjowania podczas <xref:System.Lazy%601.Value%2A> najpierw dostępu do właściwości, tego samego wyjątek na każdym kolejne próby dostępu do <xref:System.Lazy%601.Value%2A> właściwości . Innymi słowy, Konstruktor opakowanej typu nigdy nie zostanie ponownie wywołana, nawet w scenariuszach wielowątkowych. W związku z tym <xref:System.Lazy%601> obiektu nie można zgłosić wyjątek na dostęp do jednego i zwracać wartość kolejnych dostępu.  
  
 Wyjątek buforowanie jest włączone, jeśli korzystasz z dowolnych <xref:System.Lazy%601?displayProperty=nameWithType> Konstruktor, który pobiera metodę inicjalizacji (`valueFactory` parametru), na przykład jest włączona, gdy używasz `Lazy(T)(Func(T))`konstruktora. Jeśli konstruktora również przyjmuje <xref:System.Threading.LazyThreadSafetyMode> wartość (`mode` parametru), określ <xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication?displayProperty=nameWithType> lub <xref:System.Threading.LazyThreadSafetyMode.None?displayProperty=nameWithType>. Określanie metody inicjującej umożliwia buforowanie wyjątku dla tych dwóch trybów. Metoda inicjująca może być bardzo proste. Na przykład może wywołać konstruktora domyślnego dla `T`: `new Lazy<Contents>(() => new Contents(), mode)` w języku C# lub `New Lazy(Of Contents)(Function() New Contents())` w języku Visual Basic. Jeśli używasz <xref:System.Lazy%601?displayProperty=nameWithType> Konstruktor, który nie określa metodę inicjalizacji, wyjątki, które są generowane przez domyślny konstruktor `T` nie są buforowane. Aby uzyskać więcej informacji, zobacz <xref:System.Threading.LazyThreadSafetyMode> wyliczenia.  
  
> [!NOTE]
>  W przypadku utworzenia <xref:System.Lazy%601> obiekt z `isThreadSafe` wartość parametru konstruktora `false` lub `mode` wartość parametru konstruktora <xref:System.Threading.LazyThreadSafetyMode.None?displayProperty=nameWithType>, muszą uzyskać dostęp do <xref:System.Lazy%601> obiektu z jednego wątku lub Podaj własny Synchronizacja. Dotyczy to wszystkich aspektów obiektu, włączając buforowanie wyjątku.  
  
 Jak wspomniano w poprzedniej sekcji, <xref:System.Lazy%601> obiekty utworzone przez określenie <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly?displayProperty=nameWithType> Traktuj wyjątki inaczej. Z <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly>, wiele wątków konkurować można zainicjować <xref:System.Lazy%601> wystąpienia. W takim przypadku nie są buforowane wyjątki i próbuje uzyskać dostęp do <xref:System.Lazy%601.Value%2A> właściwości można kontynuować przed pomyślnym zakończeniem inicjowania.  
  
 W poniższej tabeli przedstawiono sposób <xref:System.Lazy%601> konstruktorów kontrolować buforowanie wyjątku.  
  
|Konstruktor|Tryb awaryjny wątku|Używa metody inicjowania|Wyjątki są buforowane.|  
|-----------------|------------------------|--------------------------------|---------------------------|  
|Lazy(T)()|(<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>)|Nie|Nie|  
|Lazy(T)(FUNC(T))|(<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>)|Tak|Tak|  
|Lazy(T)(Boolean)|`True` (<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>) lub `false` (<xref:System.Threading.LazyThreadSafetyMode.None>)|Nie|Nie|  
|Lazy(T)(FUNC(T), wartość logiczna)|`True` (<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>) lub `false` (<xref:System.Threading.LazyThreadSafetyMode.None>)|Tak|Tak|  
|Lazy(T)(LazyThreadSafetyMode)|Określone przez użytkownika|Nie|Nie|  
|Lazy(T)(FUNC(T), LazyThreadSafetyMode)|Określone przez użytkownika|Tak|Nie, jeśli użytkownik określi <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly>; w przeciwnym razie tak.|  
  
## <a name="implementing-a-lazy-initialized-property"></a>Implementowanie właściwości opóźnieniem zainicjowany  
 Aby zaimplementować właściwości publicznej przy użyciu inicjowania z opóźnieniem, zdefiniuj pola zapasowy właściwości jako <xref:System.Lazy%601>i zwróć <xref:System.Lazy%601.Value%2A> właściwości z `get` metody dostępu właściwości.  
  
 [!code-csharp[Lazy#5](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#5)]
 [!code-vb[Lazy#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#5)]  
  
 <xref:System.Lazy%601.Value%2A> Właściwość jest tylko do odczytu; w związku z tym nie ma właściwość, która udostępnia go `set` metody dostępu. Jeśli wymagane jest obsługiwana przez właściwości odczytu/zapisu <xref:System.Lazy%601> obiektu `set` dostępu należy utworzyć nowy <xref:System.Lazy%601> obiektu i przypisz go do magazynu zapasowego. `set` Dostępu należy utworzyć wyrażenie lambda, które zwraca nową wartość właściwości, która została przekazana do `set` metody dostępu i przekazać tego wyrażenia lambda do konstruktora dla nowego <xref:System.Lazy%601> obiektu. Następny dostęp <xref:System.Lazy%601.Value%2A> właściwość spowoduje zainicjowanie nowej <xref:System.Lazy%601>i jego <xref:System.Lazy%601.Value%2A> właściwości następnie zwraca nową wartość, która została przypisana do właściwości. Przyczyna to rozmieszczenie zwichrowanych jest zachowanie wielowątkowość zabezpieczenia, wbudowane <xref:System.Lazy%601>. W przeciwnym razie musi akcesorach właściwości pamięci podręcznej pierwsza wartość zwrócona przez <xref:System.Lazy%601.Value%2A> właściwości i modyfikować tylko wartość w pamięci podręcznej i trzeba napisać własny kod wątkowo, w tym celu. Ze względu na dodatkowe operacji inicjowania wymagane przez właściwości odczytu/zapisu przez <xref:System.Lazy%601> obiektu wydajności nie może być akceptowane. Ponadto w zależności od danego scenariusza dodatkowe koordynacji może być konieczne w celu uniknięcia wyścigu między metody ustawiające i metody pobierające.  
  
## <a name="thread-local-lazy-initialization"></a>Inicjalizacja z opóźnieniem Thread-Local  
 W niektórych scenariuszach wielowątkowe możesz nadać każdy wątek prywatnych danych. Tych danych jest nazywany *danych lokalnych wątku*. W programie .NET Framework w wersji 3.5 lub starszy, można zastosować `ThreadStatic` atrybutu zmienną statyczną aby była lokalnej wątku. Jednak przy użyciu `ThreadStatic` atrybut może prowadzić do błędów niewielkie. Na przykład inicjowania nawet podstawowe instrukcje spowoduje, że zmienna można było zainicjować tylko na pierwszym wątku, który uzyskuje dostęp do, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Lazy#6](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#6)]
 [!code-vb[Lazy#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#6)]  
  
 Na inne wątki zmiennej zostaną zainicjowane przy użyciu jego wartość domyślna (zero). Alternatywnie w programie .NET Framework w wersji 4, można użyć <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> typ, aby utworzyć zmienną na podstawie wystąpienia, lokalnej wątku, który jest inicjowana na wszystkie wątki przez <xref:System.Action%601> delegata, który podasz. W poniższym przykładzie wszystkie wątki, który dostępu `counter` spowoduje wyświetlenie jej początkowej wartości 1.  
  
 [!code-csharp[Lazy#7](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#7)]
 [!code-vb[Lazy#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#7)]  
  
 <xref:System.Threading.ThreadLocal%601> otacza znacznie taki sam sposób jak jego obiekt <xref:System.Lazy%601>, z tych podstawowych różnic:  
  
-   Każdy wątek inicjuje zmiennej lokalnej wątku przy użyciu własnego dane prywatne, który nie jest dostępny z innych wątków.  
  
-   <xref:System.Threading.ThreadLocal%601.Value%2A?displayProperty=nameWithType> Jest do odczytu / zapisu i może być modyfikowany dowolną liczbę razy. Może to mieć wpływ na propagacji wyjątków, na przykład jeden `get` operacji może zgłosić wyjątek, ale kolejnego może zostać pomyślnie zainicjowany wartość.  
  
-   Jeśli delegat inicjowania, nie zostanie podany, <xref:System.Threading.ThreadLocal%601> zainicjuje opakowanej typu przy użyciu wartości domyślnej tego typu. W tym zakresie <xref:System.Threading.ThreadLocal%601> jest zgodna z <xref:System.ThreadStaticAttribute> atrybutu.  
  
 W poniższym przykładzie pokazano, że każdy wątek który uzyskuje dostęp do `ThreadLocal<int>` wystąpienia pobiera własną unikatową kopię danych.  
  
 [!code-csharp[Lazy#9](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#9)]
 [!code-vb[Lazy#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#9)]  
  
## <a name="thread-local-variables-in-parallelfor-and-foreach"></a>Zmienne lokalne wątków w równoległej i ForEach  
 Jeśli używasz <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> metody lub <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> metody iteracyjne źródeł danych równolegle, korzystając z przeciążeń, które mają wbudowaną obsługę danych lokalnych wątku. W tych metod umiejscowienie wątku jest realizowane za pośrednictwem lokalnego delegatów do tworzenia, dostępu i wyczyścić dane. Aby uzyskać więcej informacji, zobacz [porady: zapisywanie równoległej pętli for ze zmiennymi lokalnymi wątku](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md) i [porady: zapisywanie równoległej pętli Foreach ze zmiennymi lokalnymi wątku](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-thread-local-variables.md).  
  
## <a name="using-lazy-initialization-for-low-overhead-scenarios"></a>W scenariuszach niskiego obciążenia przy użyciu inicjowania z opóźnieniem  
 W scenariuszach, w których konieczne opóźnieniem zainicjować dużą liczbę obiektów, możesz określić zawijania każdego obiektu w <xref:System.Lazy%601> wymaga zbyt dużej ilości pamięci lub zbyt wiele zasobów obliczeniowych. Lub może być rygorystycznych wymagań o jak incjalizacji jest widoczna. W takich przypadkach można użyć `static` (`Shared` w języku Visual Basic) metody <xref:System.Threading.LazyInitializer?displayProperty=nameWithType> opóźnieniem inicjalizacji każdego obiektu bez zawijania go w wystąpieniu klasy <xref:System.Lazy%601>.  
  
 W poniższym przykładzie przyjęto założenie, że, zamiast zawijania cały `Orders` obiektu w jednym <xref:System.Lazy%601> obiektu, mieć indywidualne opóźnieniem zainicjować `Order` obiektów tylko, jeśli są one wymagane.  
  
 [!code-csharp[Lazy#10](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#10)]
 [!code-vb[Lazy#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#10)]  
  
 W tym przykładzie należy zauważyć, że procedura inicjowania została wywołana w każdej iteracji pętli. W scenariuszach wielowątkowych pierwszym wątkiem do wywołania procedury inicjowania jest to, którego wartość jest odebrane przez wszystkie wątki. Nowsze wątków także wywoływać procedury inicjowania, ale jego wyniki nie są używane. Jeśli tego rodzaju potencjalnych sytuacji wyścigu nie jest dopuszczalne, użyj przeciążenia <xref:System.Threading.LazyInitializer.EnsureInitialized%2A?displayProperty=nameWithType> pobierająca logiczną argumentu i obiekt synchronizacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzana wątkowość — podstawy](../../../docs/standard/threading/managed-threading-basics.md)  
 [Wątki i wątkowość](../../../docs/standard/threading/threads-and-threading.md)  
 [Biblioteka zadań równoległych (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 [Instrukcje: wykonywanie inicjowania obiektów z opóźnieniem](../../../docs/framework/performance/how-to-perform-lazy-initialization-of-objects.md)
