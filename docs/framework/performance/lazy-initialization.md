---
title: Inicjalizacja z opóźnieniem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lazy initialization in .NET, introduction
ms.assetid: 56b4ae5c-4745-44ff-ad78-ffe4fcde6b9b
ms.openlocfilehash: 4f2b585dded6e20bb604f623217c6d1f1505c097
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180566"
---
# <a name="lazy-initialization"></a>Inicjalizacja z opóźnieniem
*Z opóźnieniem inicjowania* obiektu oznacza, że jego tworzenie jest odroczone, dopóki nie zostanie po raz pierwszy użyty. (W tym temacie *terminy inicjalizacji z opóźnieniem* i wystąpienia *z* opóźnieniem są synonimami). Inicjalizacja z opóźnieniem jest używana przede wszystkim w celu zwiększenia wydajności, uniknięcia marnotrawstwa obliczeń i zmniejszenia wymagań dotyczących pamięci programu. Są to najbardziej typowe scenariusze:  
  
- Jeśli masz obiekt, który jest kosztowne do utworzenia, a program może nie używać go. Załóżmy na przykład, że `Customer` masz w `Orders` pamięci obiekt, który `Order` ma właściwość, która zawiera dużą tablicę obiektów, które mają być zainicjowane, wymaga połączenia z bazą danych. Jeśli użytkownik nigdy nie prosi o wyświetlenie zamówień lub użycie danych w obliczeniach, nie ma powodu, aby używać pamięci systemowej lub cykli obliczeniowych do jego utworzenia. Za `Lazy<Orders>` pomocą do `Orders` deklarowania obiektu dla z opóźnieniem inicjowania, można uniknąć marnowania zasobów systemowych, gdy obiekt nie jest używany.  
  
- Jeśli masz obiekt, który jest kosztowne do utworzenia i chcesz odroczyć jego tworzenie, aż po zakończeniu innych kosztownych operacji. Załóżmy na przykład, że program ładuje kilka wystąpień obiektów po uruchomieniu, ale tylko niektóre z nich są wymagane natychmiast. Wydajność uruchamiania programu można poprawić, odraczając inicjowanie obiektów, które nie są wymagane, dopóki nie zostaną utworzone wymagane obiekty.  
  
 Chociaż można napisać własny kod do wykonywania inicjowania <xref:System.Lazy%601> z opóźnieniem, zaleca się zamiast tego użyć. <xref:System.Lazy%601>i jego powiązane typy również obsługiwać bezpieczeństwo wątków i zapewnić spójne zasady propagacji wyjątków.  
  
 W poniższej tabeli wymieniono typy, które zapewnia program .NET Framework w wersji 4, aby włączyć inicjowanie z opóźnieniem w różnych scenariuszach.  
  
|Typ|Opis|  
|----------|-----------------|  
|<xref:System.Lazy%601>|Klasa otoki, która zapewnia semantyka inicjowania z opóźnieniem dla dowolnej biblioteki klas lub typu zdefiniowanego przez użytkownika.|  
|<xref:System.Threading.ThreadLocal%601>|Przypomina <xref:System.Lazy%601> z tą różnicą, że zapewnia semantyka inicjowania z opóźnieniem na podstawie lokalnego wątku. Każdy wątek ma dostęp do własnej unikatowej wartości.|  
|<xref:System.Threading.LazyInitializer>|Zapewnia `static` zaawansowane`Shared` (w języku Visual Basic) metody z opóźnieniem inicjowania obiektów bez narzutu klasy.|  
  
## <a name="basic-lazy-initialization"></a>Podstawowe inicjowanie z opóźnieniem  
 Aby zdefiniować typ z opóźnieniem, `MyType`na `Lazy<MyType>` przykład`Lazy(Of MyType)` , użyj (w języku Visual Basic), jak pokazano w poniższym przykładzie. Jeśli żaden delegat nie <xref:System.Lazy%601> jest przekazywany w konstruktorze, opakowany typ jest tworzony przy użyciu, <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> gdy właściwość value jest po raz pierwszy dostępny. Jeśli typ nie ma konstruktora bez parametrów, wyjątek w czasie wykonywania jest zgłaszany.  
  
 W poniższym przykładzie `Orders` załóżmy, że `Order` jest to klasa, która zawiera tablicę obiektów pobranych z bazy danych. Obiekt `Customer` zawiera wystąpienie `Orders`, ale w zależności od `Orders` akcji użytkownika, dane z obiektu mogą nie być wymagane.  
  
 [!code-csharp[Lazy#1](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#1)]
 [!code-vb[Lazy#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#1)]  
  
 Można również przekazać delegata <xref:System.Lazy%601> w konstruktorze, który wywołuje przeciążenie konstruktora na opakowane typu w czasie tworzenia i wykonać inne kroki inicjowania, które są wymagane, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Lazy#2](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#2)]
 [!code-vb[Lazy#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#2)]  
  
 Po utworzeniu obiektu z opóźnieniem `Orders` nie jest <xref:System.Lazy%601.Value%2A> tworzone żadne wystąpienie, dopóki właściwość zmiennej z opóźnieniem nie zostanie po raz pierwszy dostępna. Przy pierwszym dostępie opakowany typ jest tworzony i zwracany i przechowywany dla każdego przyszłego dostępu.  
  
 [!code-csharp[Lazy#3](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#3)]
 [!code-vb[Lazy#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#3)]  
  
 Obiekt <xref:System.Lazy%601> zawsze zwraca ten sam obiekt lub wartość, z którą został zainicjowany. W związku <xref:System.Lazy%601.Value%2A> z tym właściwość jest tylko do odczytu. Jeśli <xref:System.Lazy%601.Value%2A> przechowuje typ odwołania, nie można przypisać do niego nowego obiektu. (Można jednak zmienić wartość jego ustawionych pól publicznych i właściwości). Jeśli <xref:System.Lazy%601.Value%2A> przechowuje typ wartości, nie można zmodyfikować jego wartości. Niemniej jednak można utworzyć nową zmienną, wywołując konstruktor zmiennych ponownie przy użyciu nowych argumentów.  
  
 [!code-csharp[Lazy#4](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#4)]
 [!code-vb[Lazy#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#4)]  
  
 Nowe wystąpienie z opóźnieniem, podobnie jak wcześniejsze, nie zawiera wystąpienia, `Orders` dopóki jego <xref:System.Lazy%601.Value%2A> właściwość nie zostanie po raz pierwszy uzyskiczona.  
  
### <a name="thread-safe-initialization"></a>Inicjowanie bezpieczne dla wątków  
 Domyślnie <xref:System.Lazy%601> obiekty są bezpieczne dla wątków. Oznacza to, że jeśli konstruktor nie określa <xref:System.Lazy%601> rodzaju bezpieczeństwa wątku, obiekty, które tworzy są bezpieczne dla wątków. W scenariuszach wielowątkowych pierwszy wątek dostępu <xref:System.Lazy%601.Value%2A> do <xref:System.Lazy%601> właściwości obiektu bezpiecznego wątku inicjuje go dla wszystkich kolejnych dostępów we wszystkich wątkach, a wszystkie wątki współużytkują te same dane. W związku z tym nie ma znaczenia, który wątek inicjuje obiekt, a warunki wyścigu są łagodne.  
  
> [!NOTE]
> Tę spójność można rozszerzyć na warunki błędu przy użyciu buforowania wyjątków. Aby uzyskać więcej informacji, zobacz następną sekcję [Wyjątki w obiektach z opóźnieniem](lazy-initialization.md#ExceptionsInLazyObjects).  
  
 Poniższy przykład pokazuje, `Lazy<int>` że to samo wystąpienie ma taką samą wartość dla trzech oddzielnych wątków.  
  
 [!code-csharp[Lazy#8](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#8)]
 [!code-vb[Lazy#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#8)]  
  
 Jeśli potrzebujesz oddzielnych danych w <xref:System.Threading.ThreadLocal%601> każdym wątku, należy użyć typu, zgodnie z opisem w dalszej części tego tematu.  
  
 Niektóre <xref:System.Lazy%601> konstruktory mają `isThreadSafe` parametr logiczny o <xref:System.Lazy%601.Value%2A> nazwie, który jest używany do określenia, czy właściwość będzie dostępna z wielu wątków. Jeśli zamierzasz uzyskać dostęp do właściwości z `false` jednego wątku, przekaż, aby uzyskać skromną korzyść wydajności. Jeśli zamierzasz uzyskać dostęp do właściwości z `true` wielu <xref:System.Lazy%601> wątków, przekazać, aby poinstruować wystąpienie, aby poprawnie obsługiwać warunki wyścigu, w którym jeden wątek zgłasza wyjątek w czasie inicjowania.  
  
 Niektóre <xref:System.Lazy%601> konstruktory mają <xref:System.Threading.LazyThreadSafetyMode> parametr o nazwie `mode`. Konstruktory te zapewniają dodatkowy tryb bezpieczeństwa gwintu. W poniższej tabeli przedstawiono, jak na bezpieczeństwo wątku <xref:System.Lazy%601> obiektu wpływają parametry konstruktora określające bezpieczeństwo wątku. Każdy konstruktor ma co najwyżej jeden taki parametr.  
  
|Bezpieczeństwo gwintu obiektu|`LazyThreadSafetyMode``mode` parametr|Parametr `isThreadSafe` logiczny|Brak parametrów bezpieczeństwa gwintu|  
|---------------------------------|---------------------------------------------|--------------------------------------|---------------------------------|  
|W pełni bezpieczne dla gwintów; tylko jeden wątek naraz próbuje zainicjować wartość.|<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>|`true`|Tak.|  
|Nie jest bezpieczny dla wątków.|<xref:System.Threading.LazyThreadSafetyMode.None>|`false`|Nie dotyczy.|  
|W pełni bezpieczne dla gwintów; wątki ścigają się, aby zainicjować wartość.|<xref:System.Threading.LazyThreadSafetyMode.PublicationOnly>|Nie dotyczy.|Nie dotyczy.|  
  
 Jak pokazuje tabela, <xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication?displayProperty=nameWithType> określenie `mode` parametru jest takie `true` samo `isThreadSafe` jak określenie <xref:System.Threading.LazyThreadSafetyMode.None?displayProperty=nameWithType> parametru, a `false`określenie jest takie samo jak określenie .  
  
 Określenie <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly?displayProperty=nameWithType> umożliwia wiele wątków, aby <xref:System.Lazy%601> spróbować zainicjować wystąpienie. Tylko jeden wątek może wygrać ten wyścig, a wszystkie inne wątki otrzymują wartość, która została zainicjowana przez udany wątek. Jeśli wyjątek jest zgłaszany na wątku podczas inicjowania, ten wątek nie otrzymuje wartość ustawioną przez pomyślny wątek. Wyjątki nie są buforowane, więc kolejna próba uzyskania dostępu do <xref:System.Lazy%601.Value%2A> właściwości może spowodować pomyślne zainicjowanie. Różni się to od sposobu traktowania wyjątków w innych trybach, co opisano w poniższej sekcji. Aby uzyskać więcej <xref:System.Threading.LazyThreadSafetyMode> informacji, zobacz wyliczenie.  
  
<a name="ExceptionsInLazyObjects"></a>
## <a name="exceptions-in-lazy-objects"></a>Wyjątki w obiektach z opóźnieniem  
 Jak wspomniano wcześniej, <xref:System.Lazy%601> obiekt zawsze zwraca ten sam obiekt lub wartość, <xref:System.Lazy%601.Value%2A> który został zainicjowany z, a zatem właściwość jest tylko do odczytu. Jeśli włączysz buforowanie wyjątków, ta niezmienność rozciąga się również na zachowanie wyjątku. Jeśli obiekt zainicjowany z opóźnieniem ma włączoną buforowanie wyjątków i zgłasza <xref:System.Lazy%601.Value%2A> wyjątek od metody inicjowania, gdy właściwość <xref:System.Lazy%601.Value%2A> jest po raz pierwszy dostępna, ten sam wyjątek jest zgłaszany przy każdej kolejnej próbie uzyskania dostępu do właściwości. Innymi słowy konstruktora typu zawinięte nigdy nie jest wywoływana ponownie, nawet w scenariuszach wielowątkowych. W związku <xref:System.Lazy%601> z tym obiekt nie może zgłosić wyjątek na jeden dostęp i zwrócić wartość na kolejny dostęp.  
  
 Buforowanie wyjątków jest włączone, <xref:System.Lazy%601?displayProperty=nameWithType> gdy używany jest dowolny konstruktor, który przyjmuje metodę inicjowania (parametr);`valueFactory` na przykład jest włączona podczas `Lazy(T)(Func(T))`korzystania z konstruktora. Jeśli konstruktor przyjmuje <xref:System.Threading.LazyThreadSafetyMode> również`mode` wartość <xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication?displayProperty=nameWithType> ( <xref:System.Threading.LazyThreadSafetyMode.None?displayProperty=nameWithType>parametr), należy określić lub . Określenie metody inicjowania umożliwia buforowanie wyjątków dla tych dwóch trybów. Metoda inicjowania może być bardzo prosta. Na przykład może wywołać konstruktora `new Lazy<Contents>(() => new Contents(), mode)` bez parametrów `New Lazy(Of Contents)(Function() New Contents())` dla `T`: w języku C# lub w języku Visual Basic. Jeśli używasz <xref:System.Lazy%601?displayProperty=nameWithType> konstruktora, który nie określa metody inicjowania, wyjątki, które są generowane przez konstruktora bez parametrów dla `T` nie są buforowane. Aby uzyskać więcej <xref:System.Threading.LazyThreadSafetyMode> informacji, zobacz wyliczenie.  
  
> [!NOTE]
> Jeśli tworzysz <xref:System.Lazy%601> obiekt `isThreadSafe` z parametrem `false` konstruktora ustawionym na , lub parametrem `mode` konstruktora ustawionym na <xref:System.Threading.LazyThreadSafetyMode.None?displayProperty=nameWithType>, należy uzyskać dostęp do <xref:System.Lazy%601> obiektu z pojedynczego wątku lub zapewnić własną synchronizację. Dotyczy to wszystkich aspektów obiektu, w tym buforowania wyjątków.  
  
 Jak wspomniano w poprzedniej <xref:System.Lazy%601> sekcji, obiekty <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly?displayProperty=nameWithType> utworzone przez określenie traktować wyjątki inaczej. Z <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly>, wiele wątków może <xref:System.Lazy%601> konkurować, aby zainicjować wystąpienie. W takim przypadku wyjątki nie są buforowane <xref:System.Lazy%601.Value%2A> i próby dostępu do właściwości można kontynuować, dopóki inicjowanie zakończy się pomyślnie.  
  
 W poniższej tabeli <xref:System.Lazy%601> podsumowano sposób, w jaki konstruktorzy kontrolują buforowanie wyjątków.  
  
|Konstruktor|Tryb bezpieczeństwa gwintu|Używa metody inicjowania|Wyjątki są buforowane|  
|-----------------|------------------------|--------------------------------|---------------------------|  
|Z opóźnieniem()|(<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>)|Nie|Nie|  
|Leniwy(T)(Func(T))|(<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>)|Tak|Tak|  
|Lazy(T)(logiczny)|`True`(<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>) `false` <xref:System.Threading.LazyThreadSafetyMode.None>lub ( )|Nie|Nie|  
|Lazy(T)(Func(T), logiczny)|`True`(<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>) `false` <xref:System.Threading.LazyThreadSafetyMode.None>lub ( )|Tak|Tak|  
|Lazy(T)(LazyThreadSafetyMode)|Określone przez użytkownika|Nie|Nie|  
|Lazy(T)(Func(T), LazyThreadSafetyMode)|Określone przez użytkownika|Tak|Nie, jeśli <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly>użytkownik określa ; w przeciwnym razie tak.|  
  
## <a name="implementing-a-lazy-initialized-property"></a>Implementowanie właściwości z opóźnieniem  
 Aby zaimplementować właściwość publiczną przy użyciu inicjowania z opóźnieniem, należy zdefiniować pole zapasowe <xref:System.Lazy%601>właściwości jako , i zwrócić <xref:System.Lazy%601.Value%2A> właściwość z `get` akcesora właściwości.  
  
 [!code-csharp[Lazy#5](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#5)]
 [!code-vb[Lazy#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#5)]  
  
 Właściwość <xref:System.Lazy%601.Value%2A> jest tylko do odczytu; w związku z tym właściwość, `set` która udostępnia go nie ma akcesora. Jeśli wymagana jest właściwość odczytu/zapisu, która jest tworzęana <xref:System.Lazy%601> przez obiekt, `set` akcesor musi utworzyć nowy <xref:System.Lazy%601> obiekt i przypisać go do magazynu zapasowego. Akcesor `set` musi utworzyć wyrażenie lambda, który zwraca `set` nową wartość właściwości, która została przekazana do akcesora i przekazać to wyrażenie lambda do konstruktora dla nowego <xref:System.Lazy%601> obiektu. Następny dostęp do <xref:System.Lazy%601.Value%2A> właściwości spowoduje inicjalizację <xref:System.Lazy%601> <xref:System.Lazy%601.Value%2A> nowego , a jego właściwość zwróci następnie nową wartość, która została przypisana do właściwości. Powodem tego zawiłego układu jest zachowanie wbudowanych <xref:System.Lazy%601>zabezpieczeń wielowątkowych. W przeciwnym razie akcesory właściwości musiałby <xref:System.Lazy%601.Value%2A> buforować pierwszą wartość zwróconą przez właściwość i tylko zmodyfikować wartość buforowaną i trzeba napisać własny kod wątku, aby to zrobić. Ze względu na dodatkowe inicjalizowania wymagane przez <xref:System.Lazy%601> właściwość odczytu/zapisu wspierane przez obiekt, wydajność może być nie do przyjęcia. Ponadto, w zależności od konkretnego scenariusza, dodatkowa koordynacja może być wymagana w celu uniknięcia warunków wyścigu między ustawiających i getters.  
  
## <a name="thread-local-lazy-initialization"></a>Inicjowanie lokalne wątku  
 W niektórych scenariuszach wielowątkowych można nadać każdemu wątkowi własne dane prywatne. Takie dane nazywane są *danymi lokalnymi wątków*. W .NET Framework w wersji 3.5 i `ThreadStatic` wcześniejszych można zastosować atrybut do zmiennej statycznej, aby uczynić go lokalnym wątku. Jednak za `ThreadStatic` pomocą atrybutu może prowadzić do błędów subtelne. Na przykład nawet podstawowe instrukcje inicjowania spowoduje, że zmienna ma być inicjowane tylko w pierwszym wątku, który uzyskuje do niego dostęp, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Lazy#6](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#6)]
 [!code-vb[Lazy#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#6)]  
  
 We wszystkich innych wątkach zmienna zostanie zainicjowana przy użyciu jej wartości domyślnej (zero). Alternatywnie w programie .NET Framework w wersji <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> 4 można użyć tego typu do utworzenia zmiennej lokalnej opartej na wystąpieniu, która jest inicjowana we wszystkich wątkach przez <xref:System.Action%601> pełnomocnika, który podasz. W poniższym przykładzie wszystkie `counter` wątki, do których dostęp będzie widzieć jego wartość początkową jako 1.  
  
 [!code-csharp[Lazy#7](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#7)]
 [!code-vb[Lazy#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#7)]  
  
 <xref:System.Threading.ThreadLocal%601>owija swój obiekt w <xref:System.Lazy%601>taki sam sposób jak , z tymi istotnymi różnicami:  
  
- Każdy wątek inicjuje zmienną lokalną wątku przy użyciu własnych danych prywatnych, które nie są dostępne z innych wątków.  
  
- Właściwość <xref:System.Threading.ThreadLocal%601.Value%2A?displayProperty=nameWithType> jest odczyt i zapis i może być modyfikowany dowolną liczbę razy. Może to mieć wpływ na propagację wyjątków, na przykład jedna `get` operacja może zgłosić wyjątek, ale następna może pomyślnie zainicjować wartość.  
  
- Jeśli nie podano delegata <xref:System.Threading.ThreadLocal%601> inicjowania, zainisl jego typ opakowane przy użyciu domyślnej wartości typu. W związku <xref:System.Threading.ThreadLocal%601> z tym <xref:System.ThreadStaticAttribute> jest zgodne z atrybutem.  
  
 Poniższy przykład pokazuje, że każdy `ThreadLocal<int>` wątek, który uzyskuje dostęp do wystąpienia pobiera własną unikatową kopię danych.  
  
 [!code-csharp[Lazy#9](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#9)]
 [!code-vb[Lazy#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#9)]  
  
## <a name="thread-local-variables-in-parallelfor-and-foreach"></a>Zmienne lokalne wątku w parallel.For i ForEach  
 Korzystając z <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> metody <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> lub metody do iteracji za pomocą źródeł danych równolegle, można użyć przeciążenia, które mają wbudowaną obsługę danych lokalnych wątku. W tych metodach lokalizacja wątku jest osiągana przy użyciu delegatów lokalnych do tworzenia, uzyskiwania dostępu i czyszczenia danych. Aby uzyskać więcej informacji, zobacz [Jak: Napisz Parallel.For Pętli z wątku zmiennych lokalnych](../../standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md) i [jak: Napisz Parallel.ForEach pętli z partycji zmiennych lokalnych](../../standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-partition-local-variables.md).  
  
## <a name="using-lazy-initialization-for-low-overhead-scenarios"></a>Używanie inicjowania z opóźnieniem dla scenariuszy o niskim napowietrzniu  
 W scenariuszach, w których trzeba z opóźnieniem zainicjować dużą liczbę obiektów, <xref:System.Lazy%601> można zdecydować, że zawijania każdego obiektu w wymaga zbyt dużo pamięci lub zbyt wiele zasobów obliczeniowych. Lub może mieć rygorystyczne wymagania dotyczące jak z opóźnieniem inicjowania jest narażony. W takich przypadkach można `static` użyć`Shared` (w języku Visual <xref:System.Threading.LazyInitializer?displayProperty=nameWithType> Basic) metody klasy do z opóźnieniem inicjować każdy obiekt bez zawijania go w wystąpieniu <xref:System.Lazy%601>.  
  
 W poniższym przykładzie załóżmy, że `Orders` zamiast <xref:System.Lazy%601> zawijanie całego obiektu w `Order` jednym obiekcie, masz z opóźnieniem zainicjowane poszczególne obiekty tylko wtedy, gdy są one wymagane.  
  
 [!code-csharp[Lazy#10](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#10)]
 [!code-vb[Lazy#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#10)]  
  
 W tym przykładzie należy zauważyć, że procedura inicjowania jest wywoływana na każdej iteracji pętli. W scenariuszach wielowątkowych pierwszy wątek do wywołania procedury inicjowania jest ten, którego wartość jest widoczna dla wszystkich wątków. Późniejsze wątki również wywołać procedurę inicjowania, ale ich wyniki nie są używane. Jeśli tego rodzaju potencjalnego stanu wyścigu nie <xref:System.Threading.LazyInitializer.EnsureInitialized%2A?displayProperty=nameWithType> jest dopuszczalne, należy użyć przeciążenie, który przyjmuje argument logiczny i obiekt synchronizacji.  
  
## <a name="see-also"></a>Zobacz też

- [Zarządzana wątkowość — podstawy](../../standard/threading/managed-threading-basics.md)
- [Wątki i wątkowość](../../standard/threading/threads-and-threading.md)
- [Biblioteka zadań równoległych (TPL)](../../standard/parallel-programming/task-parallel-library-tpl.md)
- [Porady: wykonywanie incjalizacji obiektów z opóźnieniem](how-to-perform-lazy-initialization-of-objects.md)
