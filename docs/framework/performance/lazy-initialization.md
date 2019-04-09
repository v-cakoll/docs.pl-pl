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
ms.openlocfilehash: ce217e2ed8e542ad0f7122970655aa32a353f51a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59182302"
---
# <a name="lazy-initialization"></a>Inicjalizacja z opóźnieniem
*Inicjalizacja z opóźnieniem* obiektu oznacza, że jego utworzenia jest odroczone do czasu jej pierwszym użyciu. (W tym temacie warunki *inicjowania z opóźnieniem* i *wystąpienia z opóźnieniem* oznaczają to samo.) Inicjalizacja z opóźnieniem służy głównie do zwiększenia wydajności, należy unikać marnotrawstwa obliczeń i zmniejszyć wymagania dotyczące pamięci programu. Poniżej przedstawiono najbardziej typowych scenariuszy:  
  
-   Gdy ma obiekt, który jest kosztowne, a program nie może używać. Na przykład załóżmy, że masz w pamięci `Customer` obiekt, który ma `Orders` właściwość, która zawiera dużą tablicę liczb `Order` obiekty, które zainicjowana, wymaga połączenia z bazą danych. Jeśli użytkownik nigdy nie prosi do wyświetlania zamówień lub użyć danych w obliczeń, następnie nie ma powodu ją utworzyć za pomocą pamięci systemowej lub cykli obliczeniowych. Za pomocą `Lazy<Orders>` do deklarowania `Orders` obiektu inicjowania z opóźnieniem, możesz uniknąć marnowania zasobów systemowych, jeśli obiekt nie jest używany.  
  
-   Gdy obiekt, która jest kosztowna utworzyć i mają być odroczone jej tworzenia, aż po innych kosztowne operacje zostały zakończone. Załóżmy na przykład, czy program ładuje kilka wystąpień obiektu po jego uruchomieniu, ale tylko niektóre z nich wymagane jest od razu. Aby zwiększyć wydajność uruchamiania programów, należy Opóźnienie inicjowania obiektów, które nie są wymagane, dopóki nie zostały utworzone wymagane obiekty.  
  
 Mimo że można napisać własny kod, aby wykonać inicjowania z opóźnieniem, firma Microsoft zaleca użycie <xref:System.Lazy%601> zamiast tego. <xref:System.Lazy%601> oraz jego powiązanych typów również obsługuje bezpieczeństwo wątków i zasady propagacji wyjątku spójne.  
  
 W poniższej tabeli wymieniono typy, które zapewnia .NET Framework w wersji 4, umożliwiające inicjowanie z opóźnieniem w różnych scenariuszach.  
  
|Typ|Opis|  
|----------|-----------------|  
|<xref:System.Lazy%601>|Klasa otoki, która zapewnia semantykę, inicjowania z opóźnieniem dla biblioteki klas lub typ zdefiniowany przez użytkownika.|  
|<xref:System.Threading.ThreadLocal%601>|Przypomina <xref:System.Lazy%601> z tą różnicą, że zapewnia semantykę inicjowania z opóźnieniem na podstawie lokalnej wątku. Każdy wątek ma dostęp do jego własnej unikatowe wartości.|  
|<xref:System.Threading.LazyInitializer>|Zapewnia zaawansowane `static` (`Shared` w języku Visual Basic) metody incjalizacji obiektów bez konieczności klasy.|  
  
## <a name="basic-lazy-initialization"></a>Podstawowe inicjowania z opóźnieniem  
 Do zdefiniowania z opóźnieniem zainicjowany typem, na przykład `MyType`, użyj `Lazy<MyType>` (`Lazy(Of MyType)` w języku Visual Basic), jak pokazano w poniższym przykładzie. Jeśli delegowanie nie jest przekazywany w <xref:System.Lazy%601> opakowany typ konstruktora, jest tworzona przy użyciu <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> podczas pierwszego otwarcia właściwości value. Jeśli typ nie ma domyślnego konstruktora, zwracany jest wyjątek czasu wykonywania.  
  
 W poniższym przykładzie przyjęto założenie, że `Orders` to klasa, która zawiera tablicę `Order` obiekty są pobierane z bazy danych. A `Customer` obiekt zawiera wystąpienie `Orders`, ale w zależności od działań użytkownika, danych z `Orders` obiekt nie może być wymagane.  
  
 [!code-csharp[Lazy#1](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#1)]
 [!code-vb[Lazy#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#1)]  
  
 Można również przekazać delegata w <xref:System.Lazy%601> Konstruktor, który wywołuje konstruktora określonego przeciążenia opakowanej typu w czasie tworzenia i wykonać pozostałe kroki inicjowania, które są wymagane, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Lazy#2](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#2)]
 [!code-vb[Lazy#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#2)]  
  
 Po utworzeniu obiektu z opóźnieniem, żadne wystąpienie elementu `Orders` jest tworzony, dopóki <xref:System.Lazy%601.Value%2A> właściwości zmiennej z opóźnieniem odbywa się po raz pierwszy. Na pierwszym dostępie opakowany typ jest utworzony i zwracane, a także przechowywane, aby uzyskać dostęp do wszystkich przyszłych.  
  
 [!code-csharp[Lazy#3](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#3)]
 [!code-vb[Lazy#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#3)]  
  
 A <xref:System.Lazy%601> zawsze zwraca ten sam obiekt lub wartość, która została zainicjowana przy użyciu. W związku z tym <xref:System.Lazy%601.Value%2A> właściwość jest tylko do odczytu. Jeśli <xref:System.Lazy%601.Value%2A> zapisuje odwołanie do typu, nie można przypisać nowy obiekt do niego. (Jednak można zmienić wartość można ustawić pola publiczne i właściwości.) Jeśli <xref:System.Lazy%601.Value%2A> zapisuje wartość typu, nie można zmodyfikować jego wartości. Niemniej jednak można utworzyć nową zmienną za pomocą wywołania konstruktora zmiennej ponownie przy użyciu nowe argumenty.  
  
 [!code-csharp[Lazy#4](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#4)]
 [!code-vb[Lazy#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#4)]  
  
 Nowe wystąpienie z opóźnieniem, tak jak wcześniej, nie tworzy wystąpienia `Orders` do momentu jego <xref:System.Lazy%601.Value%2A> najpierw dostęp do właściwości.  
  
### <a name="thread-safe-initialization"></a>Wątkowo inicjowanie  
 Domyślnie <xref:System.Lazy%601> obiekty są odporne na wątki. Oznacza to, jeśli Konstruktor nie określa rodzaj bezpieczeństwo wątków <xref:System.Lazy%601> tworzy obiekty są odporne na wątki. W scenariuszach wielowątkowych, pierwszym wątkiem w celu uzyskania dostępu do <xref:System.Lazy%601.Value%2A> właściwość obsługujące wielowątkowość <xref:System.Lazy%601> obiektu inicjuje go dla wszystkich kolejnych dostępy do we wszystkich wątkach i wszystkie wątki udostępnianie tych samych danych. Dlatego nie ma znaczenia, który wątek inicjuje obiekt i sytuacje wyścigu sygnalizują poważnych problemów.  
  
> [!NOTE]
>  Ten spójności w warunkach błędu można rozszerzyć za pomocą pamięci podręcznej wyjątek. Aby uzyskać więcej informacji, zobacz następną sekcję, [wyjątków w obiektów z opóźnieniem](../../../docs/framework/performance/lazy-initialization.md#ExceptionsInLazyObjects).  
  
 Poniższy przykład pokazuje, że takie same `Lazy<int>` wystąpienie ma taką samą wartość dla trzech oddzielnych wątkach.  
  
 [!code-csharp[Lazy#8](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#8)]
 [!code-vb[Lazy#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#8)]  
  
 Jeśli wymagane są osobne dane dla każdego wątku, należy użyć <xref:System.Threading.ThreadLocal%601> typ, zgodnie z opisem w dalszej części tego tematu.  
  
 Niektóre <xref:System.Lazy%601> konstruktorów mają parametrem logicznym o nazwie `isThreadSafe` używany do określenia czy <xref:System.Lazy%601.Value%2A> właściwości będą uzyskiwać dostęp z wielu wątków. Jeśli planujesz dostęp do właściwości z tylko jednego wątku, Przekaż `false` korzyści skromną wydajności. Jeśli planujesz dostęp do właściwości z wielu wątków, Przekaż `true` nakazać <xref:System.Lazy%601> wystąpienia poprawnie obsługuje sytuacje wyścigu, w których jeden wątek zgłasza wyjątek w czasie inicjowania.  
  
 Niektóre <xref:System.Lazy%601> mają konstruktory <xref:System.Threading.LazyThreadSafetyMode> parametr o nazwie `mode`. Te konstruktory zapewniają tryb awaryjny wątku dodatkowe. W poniższej tabeli przedstawiono, jak bezpieczeństwo wątku <xref:System.Lazy%601> obiektu jest zależna od parametry konstruktora, które określają bezpieczeństwo wątkowe. Każdy Konstruktor ma co najwyżej jeden taki parametr.  
  
|Bezpieczeństwo wątków obiektu|`LazyThreadSafetyMode` `mode` parametr|Wartość logiczna `isThreadSafe` parametru|Brak parametrów bezpieczeństwa wątków|  
|---------------------------------|---------------------------------------------|--------------------------------------|---------------------------------|  
|W pełni wątkowo; tylko jeden wątek jednocześnie próbuje zainicjować wartości.|<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>|`true`|Tak.|  
|Nie metodą o bezpiecznych wątkach.|<xref:System.Threading.LazyThreadSafetyMode.None>|`false`|Nie dotyczy.|  
|W pełni wątkowo; Wyścig wątków do inicjacji wartości.|<xref:System.Threading.LazyThreadSafetyMode.PublicationOnly>|Nie dotyczy.|Nie dotyczy.|  
  
 Jak widać w tabeli, określając <xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication?displayProperty=nameWithType> dla `mode` parametru jest taka sama jak określanie `true` dla `isThreadSafe` parametru i określając <xref:System.Threading.LazyThreadSafetyMode.None?displayProperty=nameWithType> jest taka sama jak określanie `false`.  
  
 Określanie <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly?displayProperty=nameWithType> zezwala na wiele wątków próbuje zainicjować <xref:System.Lazy%601> wystąpienia. Tylko jeden wątek może wygrać Wyścig, a inne wątki otrzymują wartość, która została zainicjowana przez wątek się pomyślnie. Jeśli w wątku, jest zgłaszany wyjątek podczas inicjowania, wątek nie otrzymuje wartość ustawioną przy użyciu pomyślne wątku. Wyjątki nie są buforowane, dlatego kolejna próba uzyskania dostępu <xref:System.Lazy%601.Value%2A> właściwość może doprowadzić do prawidłowego zainicjowania. To różni się od sposobu wyjątki są traktowane w innych trybach, który jest opisany w poniższej sekcji. Aby uzyskać więcej informacji, zobacz <xref:System.Threading.LazyThreadSafetyMode> wyliczenia.  
  
<a name="ExceptionsInLazyObjects"></a>   
## <a name="exceptions-in-lazy-objects"></a>Wyjątki w obiektów z opóźnieniem  
 Jak wspomniano wcześniej, <xref:System.Lazy%601> zawsze zwraca ten sam obiekt lub wartość, która została zainicjowana, i w związku z tym <xref:System.Lazy%601.Value%2A> właściwość jest tylko do odczytu. Po włączeniu buforowania wyjątek, wyjątek zachowanie rozszerzają to niezmienności. Jeśli obiekt inicjowany z opóźnieniem jest włączone buforowanie wyjątek i zgłasza wyjątek z jego metody inicjującej podczas <xref:System.Lazy%601.Value%2A> najpierw dostęp do właściwości, ten sam wyjątek jest zgłaszany w każdej kolejnej próby dostępu do <xref:System.Lazy%601.Value%2A> właściwości . Innymi słowy, Konstruktor opakowany typ nigdy nie zostanie ponownie wywołana, nawet w scenariuszach wielowątkowych. W związku z tym <xref:System.Lazy%601> obiektu nie można zgłosić wyjątek na jednym dostępu i zwraca wartości na kolejny dostęp.  
  
 Wyjątek jest włączone buforowanie przy użyciu jednej <xref:System.Lazy%601?displayProperty=nameWithType> konstruktora przyjmującego metodę inicjalizacji (`valueFactory` parametru), na przykład jest włączona, gdy używasz `Lazy(T)(Func(T))`konstruktora. Jeśli Konstruktor przyjmuje liczbę również <xref:System.Threading.LazyThreadSafetyMode> wartość (`mode` parametru), określ <xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication?displayProperty=nameWithType> lub <xref:System.Threading.LazyThreadSafetyMode.None?displayProperty=nameWithType>. Określanie metody inicjującej umożliwia wyjątek buforowania dla tych dwóch trybów. Metoda inicjująca może być bardzo proste. Na przykład może wywołać konstruktora domyślnego dla `T`: `new Lazy<Contents>(() => new Contents(), mode)` w języku C# lub `New Lazy(Of Contents)(Function() New Contents())` w języku Visual Basic. Jeśli używasz <xref:System.Lazy%601?displayProperty=nameWithType> Konstruktor, który nie określa metodę inicjalizacji, wyjątki wyrzucane przez domyślny konstruktor dla `T` nie są buforowane. Aby uzyskać więcej informacji, zobacz <xref:System.Threading.LazyThreadSafetyMode> wyliczenia.  
  
> [!NOTE]
>  Jeśli tworzysz <xref:System.Lazy%601> obiekt z `isThreadSafe` parametr konstruktora równa `false` lub `mode` parametr konstruktora równa <xref:System.Threading.LazyThreadSafetyMode.None?displayProperty=nameWithType>, musi mieć dostęp <xref:System.Lazy%601> obiektu z jednego wątku lub podać własne Synchronizacja. Dotyczy to wszystkich aspektów obiektu, w tym usługi pamięć podręczna wyjątek.  
  
 Jak wspomniano w poprzedniej sekcji <xref:System.Lazy%601> obiekty utworzone przez określenie <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly?displayProperty=nameWithType> inaczej traktują wyjątków. Za pomocą <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly>, mogą konkurować wiele wątków, aby zainicjować <xref:System.Lazy%601> wystąpienia. W tym przypadku wyjątki nie są buforowane i próbuje uzyskać dostęp do <xref:System.Lazy%601.Value%2A> właściwości można kontynuować przed pomyślnym zakończeniem inicjowania.  
  
 Poniższa tabela zawiera podsumowanie sposobu <xref:System.Lazy%601> konstruktory kontrolowanie buforowania wyjątku.  
  
|Konstruktor|Tryb awaryjny wątku|Używa metody inicjującej|Wyjątki są buforowane.|  
|-----------------|------------------------|--------------------------------|---------------------------|  
|Lazy(T)()|(<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>)|Nie|Nie|  
|Lazy(T)(FUNC(T))|(<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>)|Yes|Tak|  
|Lazy(T)(Boolean)|`True` (<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>) lub `false` (<xref:System.Threading.LazyThreadSafetyMode.None>)|Nie|Nie|  
|Lazy(T)(FUNC(T), atrybut typu wartość logiczna)|`True` (<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>) lub `false` (<xref:System.Threading.LazyThreadSafetyMode.None>)|Tak|Tak|  
|Lazy(T)(LazyThreadSafetyMode)|Określone przez użytkownika|Nie|Nie|  
|Lazy(T)(Func(T), LazyThreadSafetyMode)|Określone przez użytkownika|Tak|Nie, gdy użytkownik poda <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly>; w przeciwnym razie tak.|  
  
## <a name="implementing-a-lazy-initialized-property"></a>Implementowanie właściwości inicjowany z opóźnieniem  
 Aby zaimplementować właściwości publicznej przy użyciu inicjowania z opóźnieniem, zdefiniuj do pola pomocniczego właściwości jako <xref:System.Lazy%601>i zwróć <xref:System.Lazy%601.Value%2A> właściwość `get` metody dostępu właściwości.  
  
 [!code-csharp[Lazy#5](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#5)]
 [!code-vb[Lazy#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#5)]  
  
 <xref:System.Lazy%601.Value%2A> Właściwość jest tylko do odczytu; w związku z tym, nie ma właściwość, która udostępniła je `set` metody dostępu. Jeśli potrzebujesz właściwości odczytu/zapisu, wspierane przez <xref:System.Lazy%601> obiektu `set` dostępu należy utworzyć nowy <xref:System.Lazy%601> obiektu i przypisz je do magazynu zapasowego. `set` Dostępu należy utworzyć wyrażenie lambda, które zwraca nową wartość właściwości, który został przekazany do `set` metody dostępu i przekazać to wyrażenie lambda do konstruktora dla nowego <xref:System.Lazy%601> obiektu. Następny dostęp <xref:System.Lazy%601.Value%2A> właściwość spowoduje, że inicjowania nowego <xref:System.Lazy%601>i jego <xref:System.Lazy%601.Value%2A> właściwości po tej dacie zwróci nową wartość, która została przypisana do właściwości. Przyczyna to zawiłe rozmieszczenie jest zachowanie wielowątkowość ochronę wbudowaną <xref:System.Lazy%601>. W przeciwnym razie Akcesory właściwości musiałaby pierwszą wartość zwrócona przez obiekt w pamięci podręcznej <xref:System.Lazy%601.Value%2A> właściwości i modyfikować tylko wartość w pamięci podręcznej i trzeba napisać własny kod metodą o bezpiecznych wątkach, aby to zrobić. Ze względu na dodatkowe inicjalizacje, wymagane przez właściwości odczytu/zapisu, wspierane przez <xref:System.Lazy%601> obiektu wydajności nie może być akceptowalne. Ponadto w zależności od konkretnego scenariusza dodatkowe koordynacji może być konieczne w celu uniknięcia wyścigu między metody ustawiające i metod pobierających.  
  
## <a name="thread-local-lazy-initialization"></a>Inicjalizacja z opóźnieniem Thread-Local  
 W niektórych scenariuszach wielowątkowych można nadać każdy wątek prywatnych danych. Takie dane są nazywane *wątków lokalnych danych*. W .NET Framework w wersji 3.5 i starszych, można zastosować `ThreadStatic` atrybutu ze zmienną statycznej charakteryzowanych lokalnej wątku. Jednak przy użyciu `ThreadStatic` atrybut może prowadzić do powstawania błędów. Na przykład instrukcje inicjowania nawet podstawowe spowoduje, że zmienną można zainicjować tylko na pierwszym wątkiem, który uzyskuje dostęp do niego, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Lazy#6](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#6)]
 [!code-vb[Lazy#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#6)]  
  
 W innych wątkach zmienna zostaną zainicjowane przy użyciu wartości domyślnej (zero). Jako alternatywę w .NET Framework w wersji 4, możesz użyć <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> typ, aby utworzyć zmienną oparta na wystąpieniach, lokalnej wątku, który jest inicjowany we wszystkich wątkach, <xref:System.Action%601> delegat, który należy podać. W poniższym przykładzie wszystkie wątki dostęp `counter` zostanie wyświetlona jego wartość początkową jako 1.  
  
 [!code-csharp[Lazy#7](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#7)]
 [!code-vb[Lazy#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#7)]  
  
 <xref:System.Threading.ThreadLocal%601> opakowuje jego obiekt w podobny sposób jak <xref:System.Lazy%601>, za pomocą tych podstawowych różnic:  
  
-   Każdy wątek inicjuje zmienną lokalną wątku, przy użyciu własnych danych prywatnego, który nie jest dostępny z innych wątków.  
  
-   <xref:System.Threading.ThreadLocal%601.Value%2A?displayProperty=nameWithType> Właściwość jest odczytu / zapisu i dowolną liczbę razy może być modyfikowany. Może to wpłynąć na Propagacja wyjątków, na przykład jeden `get` operacji może zgłosić wyjątek, ale następny może zostać pomyślnie zainicjowany wartość.  
  
-   Jeśli nie podano żadnych delegata inicjowania, <xref:System.Threading.ThreadLocal%601> zainicjuje jego typ opakowany przy użyciu wartości domyślnej typu. W tym zakresie <xref:System.Threading.ThreadLocal%601> jest spójna z <xref:System.ThreadStaticAttribute> atrybutu.  
  
 W poniższym przykładzie pokazano, że każdy wątek, uzyskuje dostęp do `ThreadLocal<int>` wystąpienie zyskuje własną unikatową kopię danych.  
  
 [!code-csharp[Lazy#9](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#9)]
 [!code-vb[Lazy#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#9)]  
  
## <a name="thread-local-variables-in-parallelfor-and-foreach"></a>Thread-Local zmiennych Parallel.For i ForEach  
 Kiedy używasz <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> metody lub <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> metody do wykonywania iteracji źródeł danych w sposób równoległy, możesz użyć przeciążenia, które ma wbudowaną obsługę danych lokalnej wątku. W tych metodach umiejscowienie wątku jest realizowane za pośrednictwem lokalnego delegatów do tworzenia, dostęp i wyczyścić dane. Aby uzyskać więcej informacji, zobacz [jak: Zapisywanie pętli Parallel.For ze zmiennymi lokalnymi wątku](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md) i [jak: Zapisywanie pętli Parallel.ForEach ze zmiennymi lokalnymi partycji](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-partition-local-variables.md).  
  
## <a name="using-lazy-initialization-for-low-overhead-scenarios"></a>Przy użyciu inicjowania z opóźnieniem dla scenariuszy małym obciążeniem  
 W scenariuszach, w którym trzeba z opóźnieniem zainicjować dużą liczbę obiektów, można zdecydować o zawijania każdego obiektu w <xref:System.Lazy%601> wymaga zbyt dużej ilości pamięci lub zbyt wiele zasobów obliczeniowych. Lub możesz mieć rygorystyczne wymagania dotyczące sposobu incjalizacji jest widoczna. W takich przypadkach można użyć `static` (`Shared` w języku Visual Basic) metody <xref:System.Threading.LazyInitializer?displayProperty=nameWithType> klasy z opóźnieniem inicjalizacji każdego obiektu bez opakowującego aplikacje dostępnego w wystąpieniu <xref:System.Lazy%601>.  
  
 W poniższym przykładzie przyjęto założenie, że, zamiast zawijania cały `Orders` obiektu w jednym <xref:System.Lazy%601> obiektu jest inicjowany z opóźnieniem osoba `Order` obiektów tylko wtedy, gdy są one wymagane.  
  
 [!code-csharp[Lazy#10](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#10)]
 [!code-vb[Lazy#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#10)]  
  
 W tym przykładzie należy zauważyć, że procedura inicjowania została wywołana w każdej iteracji pętli. W scenariuszach wielowątkowych pierwszym wątku do wywołania procedury inicjowania jest ten, którego wartość jest widoczna dla wszystkich wątków. Nowsze wątków także wywoływać procedury inicjowania, ale jego wyniki nie są używane. Jeśli tego rodzaju potencjalnych sytuacji wyścigu nie jest dopuszczalne, użyj przeciążenia <xref:System.Threading.LazyInitializer.EnsureInitialized%2A?displayProperty=nameWithType> która przyjmuje argument logiczny i obiekt synchronizacji.  
  
## <a name="see-also"></a>Zobacz także

- [Zarządzana wątkowość — podstawy](../../../docs/standard/threading/managed-threading-basics.md)
- [Wątki i wątkowość](../../../docs/standard/threading/threads-and-threading.md)
- [Biblioteka zadań równoległych (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
- [Instrukcje: wykonywanie inicjalizacji obiektów z opóźnieniem](../../../docs/framework/performance/how-to-perform-lazy-initialization-of-objects.md)
