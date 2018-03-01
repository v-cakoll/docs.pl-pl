---
title: Kontrakty kodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Code contracts
ms.assetid: 84526045-496f-489d-8517-a258cf76f040
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4a7f6dd2f97f7d57cdaa59d1420a34409804f9dd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="code-contracts"></a>Kontrakty kodu
Kontrakty kodu zapewniają możliwość określenia warunków wstępnych, postconditions i invariants obiektu w kodzie. Warunki wstępne są wymagania, które muszą zostać spełnione, wprowadzając metody lub właściwości. Postconditions opisano oczekiwań w czasie, który zamyka kodu metody lub właściwości. Obiekt invariants opisano oczekiwanym stanem dla klasy, która jest w dobrym stanie.  
  
 Kontrakty kodu obejmują klasy znakowania kodu, statyczne Analizator do analizy w czasie kompilacji i analizatora czasu wykonywania. Klasy dla kontraktów kodu można znaleźć w <xref:System.Diagnostics.Contracts> przestrzeni nazw.  
  
 Korzyści wynikające z kontraktów kodu są następujące:  
  
-   Ulepszone testowanie: kontraktów kodu zapewniają weryfikacji statycznych kontraktu, sprawdzanie środowiska uruchomieniowego i generowania dokumentacji.  
  
-   Automatyczne narzędzia do testowania: kontraktów kodu można użyć, aby wygenerować bardziej zrozumiałej testów jednostkowych przez filtrowanie znaczenia testu argumenty, które nie spełniają warunków wstępnych.  
  
-   Weryfikacja statycznych: statyczne sprawdzania można zdecydować, czy istnieją wszelkie naruszenia Umowy, bez konieczności uruchamiania programu. Sprawdza niejawne umów, takich jak null wyłuskań i Tablica granice i kontrakty jawnego.  
  
-   Odwołanie dokumentacji: generator dokumentacji wspomaga istniejące pliki dokumentacji XML z informacjami o kontraktu. Dostępne są także arkusze stylów, które mogą być używane z [Sandcastle](https://github.com/EWSoftware/SHFB) tak, aby stron wygenerowanych dokumentacji zawierać sekcji kontraktu.  
  
 We wszystkich językach .NET Framework można od razu korzystać z umów. nie trzeba napisać specjalny analizator lub kompilatora. Dodatek Visual Studio umożliwia określenie poziomu analizy kontraktu kodu do wykonania. Analizatory można potwierdzić, że kontrakty te są poprawnie sformułowanym (kontrola typów i rozpoznawanie nazw) i może wywoływać skompilowanej postaci kontraktów w formacie język pośredni (MSIL) firmy Microsoft. Tworzenie umów w programie Visual Studio umożliwia wykorzystanie standardu IntelliSense dostarczanych przez narzędzie.  
  
 Większości metod w klasie kontraktu są warunkowo skompilowany; oznacza to, że kompilator emituje wywołania tych metod, tylko wtedy, gdy zdefiniować szczególne symbol CONTRACTS_FULL, przy użyciu `#define` dyrektywy. CONTRACTS_FULL umożliwia zapisanie kontraktów w kodzie bez użycia `#ifdef` dyrektywy; może utworzyć różne kompilacje, niektóre z kontraktami i niektóre bez.  
  
 Narzędzia i szczegółowe instrukcje dotyczące używania kontraktów kodu, zobacz [kontraktów kodu](http://go.microsoft.com/fwlink/?LinkId=152461) w witrynie MSDN DevLabs.  
  
## <a name="preconditions"></a>Warunki wstępne  
 Warunki wstępne można wyrazić przy użyciu <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType> metody. Warunki wstępne Określ stan po wywołaniu metody. Zwykle są one używane do określenia prawidłowymi wartościami parametrów. Wszystkie elementy członkowskie, które są wymienione w warunkach wstępnych muszą być co najmniej jako dostępne jako metoda. w przeciwnym razie warunki wstępne nie może być rozpoznawany przez wszystkich wywołań metody. Warunek musi mieć żadnych efektów ubocznych. Zachowanie środowiska wykonawczego nie powiodło się warunki wstępne jest określana przez analizator środowiska wykonawczego.  
  
 Na przykład następujący warunek wstępny wyraża parametru `x` musi mieć wartości null.  
  
 `Contract.Requires( x != null );`  
  
 Jeśli kodu musi zgłosić wyjątek określonego w przypadku niepowodzenia warunku wstępnego, można użyć ogólnego przeciążenia <xref:System.Diagnostics.Contracts.Contract.Requires%2A> w następujący sposób.  
  
 `Contract.Requires<ArgumentNullException>( x != null, "x" );`  
  
### <a name="legacy-requires-statements"></a>Starsza wersja wymaga deklaracji  
 Większość kodu zawiera niektóre sprawdzanie poprawności parametru w postaci `if` - `then` - `throw` kodu. Narzędzia kontraktu rozpoznać te instrukcje jako warunki wstępne w następujących przypadkach:  
  
-   Instrukcje występować przed wszystkimi innymi instrukcjami w metodzie.  
  
-   Cały zestaw takich instrukcji następuje jawnego <xref:System.Diagnostics.Contracts.Contract> wywołania metody, takie jak wywołanie <xref:System.Diagnostics.Contracts.Contract.Requires%2A>, <xref:System.Diagnostics.Contracts.Contract.Ensures%2A>, <xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>, lub <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A> metody.  
  
 Gdy `if` - `then` - `throw` instrukcje pojawiają się w tym formularzu narzędzia rozpoznaje je jako starszych `requires` instrukcje. Jeśli nie inne umowy wykonaj `if` - `then` - `throw` sekwencji, kod zakończenia <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A?displayProperty=nameWithType> metody.  
  
```  
if ( x == null ) throw new ...  
Contract.EndContractBlock(); // All previous "if" checks are preconditions  
```  
  
 Należy pamiętać, że warunek w poprzednim teście zanegowaną warunek wstępny. (Będzie rzeczywiste warunek wstępny `x != null`.) Zanegowaną warunku wstępnego jest bardzo ograniczoną: musi być napisana, jak pokazano w poprzednim przykładzie; oznacza to, że powinien on zawierać nie `else` klauzule i treści `then` klauzuli musi być pojedynczym `throw` instrukcji. `if` Testu podlega reguły zarówno czystości i widoczności (zobacz [wskazówki dotyczące użycia](#usage_guidelines)), ale `throw` wyrażenie podlega tylko czystości reguły. Jednak należy jako widoczna jako metody, w którym występuje kontrakt typ zgłoszono wyjątek.  
  
## <a name="postconditions"></a>Postconditions  
 Postconditions są kontrakty stanu metody, gdy zostaje zakończone. Warunku końcowego zaznaczono tylko zakończeniem metody. Zachowanie środowiska wykonawczego nie powiodło się postconditions jest określana przez analizator środowiska wykonawczego.  
  
 W odróżnieniu od warunki wstępne postconditions może odwoływać się do elementów członkowskich z mniejszą widoczność. Klient nie może być można zrozumieć lub wprowadzić używać niektórych informacji wyrażone w warunku końcowego przy użyciu prywatnych stanu, ale nie ma to wpływu na możliwość klienta przy użyciu metody poprawnie.  
  
### <a name="standard-postconditions"></a>Standardowe Postconditions  
 Standardowe postconditions można wyrazić przy użyciu <xref:System.Diagnostics.Contracts.Contract.Ensures%2A> metody. Postconditions express warunek, który musi być `true` po zakończeniu normalne metody.  
  
 `Contract.Ensures( this.F > 0 );`  
  
### <a name="exceptional-postconditions"></a>Wyjątkowych Postconditions  
 Wyjątkowych postconditions są postconditions, które powinny być `true` podczas określonego wyjątku przez metodę. Można określić te postconditions przy użyciu <xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A?displayProperty=nameWithType> metody, jak przedstawiono na poniższym przykładzie.  
  
 `Contract.EnsuresOnThrow<T>( this.F > 0 );`  
  
 Argument jest warunek, który musi być `true` zawsze, gdy wyjątek, który jest podtypem `T` jest generowany.  
  
 Brak niektórych typów wyjątków, które są trudne do użycia w wyjątkowych warunku końcowego. Na przykład przy użyciu typu <xref:System.Exception> dla `T` wymaga metody zagwarantowanie warunku bez względu na typ wyjątku, który jest zgłaszany, nawet jeśli jest przepełnienie stosu lub innych wyjątku niemożliwe do formantu. Tylko dla określonych wyjątków, które może zostać zgłoszony, gdy element członkowski jest wywoływana, na przykład kiedy należy używać wyjątkowych postconditions <xref:System.InvalidTimeZoneException> jest generowany dla <xref:System.TimeZoneInfo> wywołania metody.  
  
### <a name="special-postconditions"></a>Specjalne Postconditions  
 Następujących metod można stosować tylko w obrębie postconditions:  
  
-   Może się odwoływać do wartości zwracanych metody w postconditions przy użyciu wyrażenia `Contract.Result<T>()`, gdzie `T` zastępuje zwracany typ metody. Kompilator jest nie można wywnioskować typu, należy jawnie określić go. Na przykład nie można wywnioskować typów dla metod, które nie przyjmują żadnych argumentów, dzięki czemu wymaga następujących warunku końcowego jest kompilatora C#: `Contract.Ensures(0 <Contract.Result<int>())` metod z typem zwracanym `void` nie może odwoływać się do `Contract.Result<T>()` w ich postconditions.  
  
-   Wartość prestate w warunku końcowego odwołuje się do wartości wyrażenia na początku metody lub właściwości. Używa wyrażenia `Contract.OldValue<T>(e)`, gdzie `T` jest typem `e`. W przypadku pominięcia argumentu typu ogólnego, zawsze, gdy kompilator jest w stanie wywnioskować jej typu. (Na przykład kompilatora C# zawsze wnioskuje typ z powodu argumentu.) Istnieje kilka ograniczeń na to, co może wystąpić w `e` i konteksty, w których mogą występować wyrażenie stary. Stare wyrażenie nie może zawierać innego wyrażenia stary. Przede wszystkim stare wyrażenie musi odwoływać się do wartości, który istniał w stanie warunek wstępny — metoda. Innymi słowy, musi być wyrażenie, które może przyjąć tak długo, jak jest warunek wstępny metody `true`. Poniżej przedstawiono kilka wystąpień tej reguły.  
  
    -   Wartość musi istnieć w stanie warunek wstępny metody. W celu odwoływania się do pola w obiekcie, warunki wstępne musi gwarancji, że dany obiekt jest zawsze inną niż null.  
  
    -   Nie można odwołać się do wartości zwracanej metody w wyrażeniu starego:  
  
        ```  
        Contract.OldValue(Contract.Result<int>() + x) // ERROR  
        ```  
  
    -   Nie można odwołać się do `out` parametrów w wyrażeniu stary.  
  
    -   Stare wyrażenie nie może zależeć od zmiennej powiązanej kwantyfikatora, jeśli zakres kwantyfikatora zależy od wartość zwracaną przez metodę:  
  
        ```  
        Contract. ForAll (0,Contract. Result<int>(),  
        i => Contract.OldValue(xs[i]) > 3); // ERROR  
        ```  
  
    -   Stare wyrażenie nie może odwoływać się do parametru anonimowe delegata <xref:System.Diagnostics.Contracts.Contract.ForAll%2A> lub <xref:System.Diagnostics.Contracts.Contract.Exists%2A> wywołania, chyba że jest on używany jako indeksatora lub argument wywołania metody:  
  
        ```  
        Contract. ForAll (0, xs .Length, i => Contract.OldValue(xs[i]) > 3); // OK  
        Contract. ForAll (0, xs .Length, i => Contract.OldValue(i) > 3); // ERROR  
        ```  
  
    -   Stare wyrażenie nie może wystąpić w treści anonimowe delegata Jeśli wartość wyrażenia starego zależy od żadnego parametrów anonimowej delegata, chyba że anonimowe delegat jest argument <xref:System.Diagnostics.Contracts.Contract.ForAll%2A> lub <xref:System.Diagnostics.Contracts.Contract.Exists%2A> metody:  
  
        ```  
        Method( ... (T t) => Contract.OldValue(... t ...) ... ); // ERROR  
        ```  
  
    -   `Out`Parametry powodują problemu, ponieważ kontrakty występować przed treści metody, a większość kompilatory nie zezwalaj na odwołania do `out` parametrów w postconditions. Aby rozwiązać ten problem, <xref:System.Diagnostics.Contracts.Contract> klasa udostępnia <xref:System.Diagnostics.Contracts.Contract.ValueAtReturn%2A> metodę, która umożliwia warunku końcowego, na podstawie `out` parametru.  
  
        ```  
        public void OutParam(out int x) f  
        Contract.Ensures(Contract.ValueAtReturn(out x) == 3);  
        x = 3;  
        ```  
  
         Jak <xref:System.Diagnostics.Contracts.Contract.OldValue%2A> metody, można pominąć parametr typu ogólnego zawsze, gdy kompilator jest w stanie wywnioskować jej typu. Kontrakt funkcji ponownego zapisu zastępuje wywołanie metody wartość `out` parametru. <xref:System.Diagnostics.Contracts.Contract.ValueAtReturn%2A> Metody może występować tylko w postconditions. Argument do metody musi być `out` pola struktury lub parametr `out` parametru. Drugie polecenie jest również przydatne podczas odwoływania się do pól w warunku końcowego konstruktora struktury.  
  
        > [!NOTE]
        >  Obecnie narzędzi analizy kodu kontraktu nie sprawdzaj czy `out` parametry są poprawnie zainicjowane i pominąć ich wymienionej w warunku końcowego. W związku z tym w poprzednim przykładzie, jeśli wiersz po kontraktu ma wartość `x` zamiast przypisywać całkowitą go, kompilator nie będzie wystawiać Napraw błąd. Jednakże w przypadku kompilacji, w którym symbol preprocesora CONTRACTS_FULL jest niezdefiniowana (takie kompilacji wydania asa), kompilator zgłosi błąd.  
  
## <a name="invariants"></a>Invariants  
 Obiekt invariants są warunki, które powinien mieć wartość PRAWDA dla każdego wystąpienia klasy, gdy ten obiekt jest widoczny dla klienta. One express warunków, w których obiekt jest uznawane za prawidłowe.  
  
 Niezmienna metody są identyfikowane za pomocą oznaczana z <xref:System.Diagnostics.Contracts.ContractInvariantMethodAttribute> atrybutu. Niezmienna metody muszą zawierać żadnego kodu z wyjątkiem sekwencję wywołań <xref:System.Diagnostics.Contracts.Contract.Invariant%2A> metody, z których każdy określa niezmiennej pojedynczych, jak pokazano w poniższym przykładzie.  
  
```  
[ContractInvariantMethod]  
protected void ObjectInvariant ()   
{  
Contract.Invariant(this.y >= 0);  
Contract.Invariant(this.x > this.y);  
...  
}  
```  
  
 Invariants warunkowo są definiowane przez preprocesora symbol CONTRACTS_FULL. Podczas sprawdzania czasu wykonywania, invariants są sprawdzane na końcu każdej metody publicznej. Jeśli niezmiennej nazwa publiczną metodę w tej samej klasie, niezmiennej Sprawdź, czy czy zwykle odbywa się na końcu metody publicznej jest wyłączona. Zamiast tego sprawdzanie jest wykonywane tylko na końcu wywołania metody zewnętrznych do tej klasy. Dzieje się również, jeśli klasa jest wprowadzono ponownie z powodu wywołanie do metody w klasie innej. Invariants nie są sprawdzane dla obiekt finalizatory lub żadnych metod, które implementują <xref:System.IDisposable.Dispose%2A> metody.  
  
<a name="usage_guidelines"></a>   
## <a name="usage-guidelines"></a>Wskazówki dotyczące użycia  
  
### <a name="contract-ordering"></a>Umowy zamawiania  
 W poniższej tabeli przedstawiono kolejność elementów, które powinny być używane podczas zapisywania kontraktów — metoda.  
  
|`If-then-throw statements`|Warunki wstępne publicznego starszymi wersjami|  
|-|-|  
|<xref:System.Diagnostics.Contracts.Contract.Requires%2A>|Wszystkie warunki wstępne publicznego.|  
|<xref:System.Diagnostics.Contracts.Contract.Ensures%2A>|Wszystkie publiczne postconditions (normalne).|  
|<xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>|Wszystkie publiczne postconditions wyjątkowych.|  
|<xref:System.Diagnostics.Contracts.Contract.Ensures%2A>|Wszystkie prywatne/wewnętrznego postconditions (normalne).|  
|<xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>|Wszystkie prywatne/wewnętrznego postconditions wyjątkowych.|  
|<xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A>|Jeśli przy użyciu `if` - `then` - `throw` styl warunki wstępne bez innych umów, Umieść wywołanie <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A> z informacją, że wszystkie poprzednie, jeśli sprawdzanie warunków wstępnych.|  
  
<a name="purity"></a>   
### <a name="purity"></a>Czystości  
 Wszystkie metody, które są wywoływane w ramach kontraktu musi być czysty; oznacza to nie należy ich zaktualizować żadnych istniejących stanu. Czystej metody może modyfikować obiekty, które zostały utworzone po wejściu w czystej metody.  
  
 Obecnie narzędzia kontraktu kodu założono, że czysty są następujące elementy kodu:  
  
-   Metody, które są oznaczone ikoną z <xref:System.Diagnostics.Contracts.PureAttribute>.  
  
-   Typy, które są oznaczone ikoną z <xref:System.Diagnostics.Contracts.PureAttribute> (atrybut dotyczy wszystkich typów metod).  
  
-   Metody dostępu get właściwości.  
  
-   Operatory (metod statycznych, których nazwy rozpoczynają się od "op" oraz że mają jeden lub dwa parametry oraz zwracany typ inny niż void).  
  
-   Wszystkie metody, której w pełni kwalifikowana nazwa zaczyna się od "System.Diagnostics.Contracts.Contract", "System.String", "System.IO.Path" lub "System.Type".  
  
-   Wszelkie wywoływane delegata, pod warunkiem, że ma atrybut samego typu delegowanego <xref:System.Diagnostics.Contracts.PureAttribute>. Typy delegatów <xref:System.Predicate%601?displayProperty=nameWithType> i <xref:System.Comparison%601?displayProperty=nameWithType> są traktowane jako czysty.  
  
<a name="visibility"></a>   
### <a name="visibility"></a>Widoczność  
 Wszystkie elementy członkowskie wspomnianego kontraktu musi być co najmniej jako widoczny jako metody, w jakiej widnieją. Na przykład pole prywatne nie może być wspomnianego warunkiem wstępnym publiczną metodę; Klienci nie można sprawdzić poprawności taką umowę przed ich wywołania metody. Jednak jeśli pole jest oznaczony atrybutem <xref:System.Diagnostics.Contracts.ContractPublicPropertyNameAttribute>, jest wykluczone z tych reguł.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie kontraktów kodu.  
  
 [!code-csharp[ContractExample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/contractexample/cs/program.cs#1)]
 [!code-vb[ContractExample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/contractexample/vb/program.vb#1)]
