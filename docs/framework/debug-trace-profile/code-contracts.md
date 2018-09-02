---
title: Kontrakty kodu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Code contracts
ms.assetid: 84526045-496f-489d-8517-a258cf76f040
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a444b7eace18fa579324f540e8cf7537c420a6a8
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43425759"
---
# <a name="code-contracts"></a>Kontrakty kodu
Kontrakty kodu zapewniają możliwość określenia warunków wstępnych, warunków końcowych i invariants obiektu w kodzie. Są one wymagania, które muszą zostać spełnione, podczas wprowadzania metodę lub właściwość. Warunków końcowych opisują oczekiwania w czasie, który zamyka kodu metody lub właściwości. Obiekt invariants opisują oczekiwany stan dla klasy, która jest w dobrym stanie.  
  
 Kontrakty kodu zawierają klasy służące do oznaczania kodu, statycznej Analizator do analizy w czasie kompilacji i analizatora środowiska uruchomieniowego. Klasy dla kontraktów kodu można znaleźć w <xref:System.Diagnostics.Contracts> przestrzeni nazw.  
  
 Kontrakty kodu zalety następujące czynności:  
  
-   Ulepszone testowania: kontrakty kodu zapewniają weryfikacji statyczne kontraktu, sprawdzanie w czasie wykonywania i generowanie dokumentacji.  
  
-   Automatyczne narzędzia do testowania: kontrakty kodu można użyć, aby wygenerować bardziej zrozumiały testy jednostkowe odfiltrowując argumenty znaczenia testów, które nie spełniają warunków wstępnych.  
  
-   Weryfikacja statyczne: statyczne sprawdzania można zdecydować, czy istnieją wszelkie naruszenia Umowy, bez konieczności uruchamiania programu. Sprawdza niejawne zamówień, takie jak wartości null wyłuskań i tablicy granice i jawne umów.  
  
-   Dokumentację referencyjną: generator dokumentacji rozszerza istniejące pliki dokumentacji XML przy użyciu informacje na temat umowy. Dostępne są także arkuszy stylów, które mogą być używane z [Sandcastle](https://github.com/EWSoftware/SHFB) tak, aby strony wygenerowaną dokumentację zawierają sekcje kontraktu.  
  
 Wszystkie języki .NET Framework od razu korzystać z zalet umów. nie trzeba napisać specjalny analizator lub kompilatora. Dodatek programu Visual Studio pozwala określić poziom analizy kontraktu kodu do wykonania. Analizatorów można potwierdzić, że kontrakty te są poprawnie sformułowane (kontrola typów i rozpoznawanie nazw) i może wywoływać skompilowanej formy kontraktów w formacie języka intermediate language (MSIL) firmy Microsoft. Tworzenie umów w programie Visual Studio pozwala korzystać ze standardowych funkcji IntelliSense są udostępniane przez narzędzie.  
  
 Większość metod w klasie umowy są warunkowo skompilowany; oznacza to, kompilator generuje wywołania tych metod tylko wtedy, gdy zdefiniować symbol specjalny CONTRACTS_FULL, za pomocą `#define` dyrektywy. CONTRACTS_FULL umożliwia zapisanie kontraktów w kodzie, bez użycia `#ifdef` dyrektyw; można tworzyć różne kompilacje, niektóre z kontraktami i niektóre bez.  
  
 Narzędzia i szczegółowe instrukcje dotyczące korzystania z kontraktów kodu, zobacz [kontrakty kodu](https://go.microsoft.com/fwlink/?LinkId=152461) w witrynie MSDN DevLabs w sieci Web.  
  
## <a name="preconditions"></a>Warunki wstępne  
 Warunki wstępne można wyrazić za pomocą <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType> metody. Warunki wstępne Określ stan przypadku wywołania metody. Zwykle służą one do określenia prawidłowymi wartościami parametrów. Wszystkie elementy członkowskie, które są wymienione w warunkach wstępnych musi być co najmniej tak samo dostępna jak metoda. w przeciwnym razie warunek wstępny może nie być zrozumiała dla wszystkich obiektów wywołujących metodę. Warunek musi mieć nie efektów ubocznych. Zachowania w czasie wykonywania nie powiodło się warunki wstępne jest określany przez analizator środowiska uruchomieniowego.  
  
 Na przykład, następujący warunek wstępny wyraża tego parametru `x` musi być równa null.  
  
 `Contract.Requires( x != null );`  
  
 Jeśli Twój kod musi zgłosić określony wyjątek na niepowodzenie warunku wstępnego, możesz użyć przeciążenia ogólne <xref:System.Diagnostics.Contracts.Contract.Requires%2A> w następujący sposób.  
  
 `Contract.Requires<ArgumentNullException>( x != null, "x" );`  
  
### <a name="legacy-requires-statements"></a>Instrukcji #requires starszej wersji  
 Większość kodu zawiera niektóre poprawność parametrów w formie `if` - `then` - `throw` kodu. Narzędzia kontraktu rozpoznać te instrukcje jako warunki wstępne w następujących przypadkach:  
  
-   Instrukcje są wyświetlane przed wszystkimi innymi instrukcjami w metodzie.  
  
-   Cały zestaw instrukcji takich następuje jawnego <xref:System.Diagnostics.Contracts.Contract> wywołania metody, takie jak wywołanie <xref:System.Diagnostics.Contracts.Contract.Requires%2A>, <xref:System.Diagnostics.Contracts.Contract.Ensures%2A>, <xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>, lub <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A> metody.  
  
 Gdy `if` - `then` - `throw` instrukcje pojawiają się w tym formularzu narzędzia rozpoznaje je jako starszy `requires` instrukcji. Jeśli nie ma innych umów `if` - `then` - `throw` sekwencji, end kodu za pomocą <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A?displayProperty=nameWithType> metody.  
  
```  
if ( x == null ) throw new ...  
Contract.EndContractBlock(); // All previous "if" checks are preconditions  
```  
  
 Należy pamiętać, że warunek w poprzednim teście zanegowanych warunku wstępnego. (Będzie rzeczywiste wstępnym `x != null`.) Zanegowanych warunku wstępnego jest zastrzeżonych: musi być napisana, jak pokazano w poprzednim przykładzie; oznacza to, że powinien on zawierać nie `else` klauzule i treści `then` klauzula musi mieć pojedynczy `throw` instrukcji. `if` Testu podlega reguł czystości i widoczności (zobacz [wytyczne dotyczące użycia](#usage_guidelines)), ale `throw` wyrażenie podlega wyłącznie czystości reguły. Jednak typem wyjątku musi być jako widoczny jako metody, w której występuje umowy.  
  
## <a name="postconditions"></a>Warunków końcowych  
 Warunków końcowych są kontrakty dla stanu metody, kończąc działanie. Postcondition jest sprawdzany tuż przed Kończenie wykonywania metody. Zachowania w czasie wykonywania nie powiodło się warunków końcowych jest określany przez analizator środowiska uruchomieniowego.  
  
 W odróżnieniu od warunków wstępnych warunków końcowych mogą odwoływać się do elementów członkowskich z mniejszą widoczność. Klient nie może być można zrozumieć, lub wprowadzić korzystanie z niektórych informacji wyrażona postcondition, przy użyciu prywatnego stanu, ale nie ma to wpływu na możliwość klienta przy użyciu metody poprawnie.  
  
### <a name="standard-postconditions"></a>Standardowa warunków końcowych  
 Standardowa warunków końcowych można wyrazić za pomocą <xref:System.Diagnostics.Contracts.Contract.Ensures%2A> metody. Warunków końcowych express warunek, który musi być `true` na normalne zakończenie metody.  
  
 `Contract.Ensures( this.F > 0 );`  
  
### <a name="exceptional-postconditions"></a>Wyjątkowych warunków końcowych  
 Wyjątkowych warunków końcowych są warunków końcowych, które powinny być `true` gdy określony wyjątek jest zgłaszany przez metodę. Należy określić tych warunków końcowych, za pomocą <xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A?displayProperty=nameWithType> metody, jak w poniższym przykładzie pokazano.  
  
 `Contract.EnsuresOnThrow<T>( this.F > 0 );`  
  
 Argument jest warunek, który musi być `true` zawsze wtedy, gdy wyjątek, który jest podtypem `T` zgłaszany.  
  
 Brak niektórych typów wyjątków, które są trudne do użycia w wyjątkowych postcondition. Na przykład przy użyciu typu <xref:System.Exception> dla `T` wymaga metody w celu zagwarantowania warunku, bez względu na typ wyjątku, który jest zgłaszany, nawet jeśli jest on przepełnienie stosu lub innych wyjątków niemożliwe do sterowania. Tylko dla określonych wyjątków, które mogą być zgłaszany, gdy członek jest wywoływany, na przykład, kiedy należy używać wyjątkowych warunków końcowych <xref:System.InvalidTimeZoneException> jest generowany dla <xref:System.TimeZoneInfo> wywołania metody.  
  
### <a name="special-postconditions"></a>Specjalne warunków końcowych  
 Poniższych metod można stosować tylko w ramach warunków końcowych:  
  
-   Mogą odwoływać się do wartości zwracane metody w warunków końcowych przy użyciu wyrażenia `Contract.Result<T>()`, gdzie `T` jest zastępowany przez zwracany typ metody. Gdy kompilator nie może wywnioskować typ, należy je jawnie określić. Na przykład nie można wywnioskować typów, metod, które nie przyjmują żadnych argumentów, dzięki czemu wymaga następujących postcondition to kompilator języka C#: `Contract.Ensures(0 <Contract.Result<int>())` metod z typem zwrotnym `void` nie może odwoływać się do `Contract.Result<T>()` w swoich warunków końcowych.  
  
-   Wartość prestate postcondition odnosi się do wartości wyrażenia na początku metody lub właściwości. Używa wyrażenia `Contract.OldValue<T>(e)`, gdzie `T` jest typem `e`. Można pominąć argument typu ogólnego, zawsze wtedy, gdy kompilator może wywnioskować jej typu. (Na przykład, kompilator języka C# zawsze wnioskuje typ z powodu argumentu.) Ma kilka ograniczeń dotyczących co może mieć miejsce w `e` i konteksty, w których może występować wyrażenie stary. Stare wyrażenie nie może zawierać innego wyrażenia stary. Co najważniejsze stare wyrażenie musi odwoływać się do wartości, które istniały w stanie wstępnym metody. Innymi słowy, musi być wyrażenie, które mogą być obliczane tak długo, jak jest warunkiem wstępnym metody `true`. Poniżej przedstawiono kilka wystąpień tej reguły.  
  
    -   Wartość musi istnieć w stanie wstępnym metody. Aby można było odwoływać się do pola w obiekcie warunki wstępne musi gwarantować, czy ten obiekt zawsze jest różna od null.  
  
    -   Nie można odwołać się do wartości zwracanej metody w wyrażeniu stare:  
  
        ```  
        Contract.OldValue(Contract.Result<int>() + x) // ERROR  
        ```  
  
    -   Nie można odwołać się `out` parametrów w wyrażeniu stary.  
  
    -   Stare wyrażenie nie może zależeć od zmiennej powiązanej kwantyfikator, jeśli wartość zwracaną metody zależy od zakresu kwantyfikator:  
  
        ```  
        Contract. ForAll (0,Contract. Result<int>(),  
        i => Contract.OldValue(xs[i]) > 3); // ERROR  
        ```  
  
    -   Stare wyrażenie nie może odwoływać się do parametru delegata anonimowego w <xref:System.Diagnostics.Contracts.Contract.ForAll%2A> lub <xref:System.Diagnostics.Contracts.Contract.Exists%2A> wywołania, chyba że jest ona używana jako indeksatora lub argument wywołania metody:  
  
        ```  
        Contract. ForAll (0, xs .Length, i => Contract.OldValue(xs[i]) > 3); // OK  
        Contract. ForAll (0, xs .Length, i => Contract.OldValue(i) > 3); // ERROR  
        ```  
  
    -   Stare wyrażenie nie może wystąpić w treści delegata anonimowego Jeśli wartość wyrażenia stare jest zależna od dowolny z parametrów delegata anonimowego, chyba że argument do delegata anonimowego <xref:System.Diagnostics.Contracts.Contract.ForAll%2A> lub <xref:System.Diagnostics.Contracts.Contract.Exists%2A> metody:  
  
        ```  
        Method( ... (T t) => Contract.OldValue(... t ...) ... ); // ERROR  
        ```  
  
    -   `Out` Parametry powodują problemu, ponieważ kontrakty następować przed elementem treści metody, a większość kompilatorów zezwala na odwołania do `out` parametry warunków końcowych. Aby rozwiązać ten problem, <xref:System.Diagnostics.Contracts.Contract> klasa udostępnia <xref:System.Diagnostics.Contracts.Contract.ValueAtReturn%2A> metody, która umożliwia postcondition, na podstawie `out` parametru.  
  
        ```  
        public void OutParam(out int x) f  
        Contract.Ensures(Contract.ValueAtReturn(out x) == 3);  
        x = 3;  
        ```  
  
         Podobnie jak w przypadku <xref:System.Diagnostics.Contracts.Contract.OldValue%2A> metody, można pominąć parametr typu ogólnego zawsze wtedy, gdy kompilator może wywnioskować jej typu. Dysków kontraktu zastępuje wywołanie metody z wartością `out` parametru. <xref:System.Diagnostics.Contracts.Contract.ValueAtReturn%2A> Metoda może występować tylko w warunków końcowych. Argument do metody musi być `out` parametru lub pola struktury `out` parametru. Drugim jest również przydatne przy odwoływaniu się do pól w postcondition konstruktora struktury.  
  
        > [!NOTE]
        >  Obecnie narzędzi analizy kodu kontraktu sprawdza, czy `out` parametry są inicjowane poprawnie i pominąć ich wzmiankę w postcondition. W związku z tym, w poprzednim przykładzie, jeśli wiersza po kontrakt gdyby użyto wartości `x` zamiast przypisywać całkowitą do niego, kompilatora nie będzie wystawiać usunąć błąd. Jednakże w przypadku kompilacji, w której symbol preprocesora CONTRACTS_FULL jest niezdefiniowana (takie kompilacji wydania asa), kompilator zgłosi błąd.  
  
## <a name="invariants"></a>Invariants  
 Obiekt invariants są warunki, które powinny być prawdziwe dla każdego wystąpienia klasy, zawsze wtedy, gdy ten obiekt jest widoczny dla klienta. Warunki, w których obiekt jest uważany za prawidłowy one express.  
  
 Niezmienna metody są identyfikowane za pomocą oznaczony za pomocą <xref:System.Diagnostics.Contracts.ContractInvariantMethodAttribute> atrybutu. Niezmienna metody muszą zawierać żadnego kodu, z wyjątkiem sekwencję wywołań <xref:System.Diagnostics.Contracts.Contract.Invariant%2A> metody, z których każdy określa poszczególnych niezmiennej, jak pokazano w poniższym przykładzie.  
  
```  
[ContractInvariantMethod]  
protected void ObjectInvariant ()   
{  
Contract.Invariant(this.y >= 0);  
Contract.Invariant(this.x > this.y);  
...  
}  
```  
  
 Invariants warunkowo są definiowane przez symbol preprocesora CONTRACTS_FULL. Podczas sprawdzania czasu wykonywania, invariants są sprawdzane na końcu każdej metody publiczne. Jeśli niezmiennej nazwa publicznej metody z tej samej klasy, niezmienna Sprawdź, czy zwykle sytuacja może mieć miejsce na końcu metody publicznej jest wyłączona. Zamiast tego sprawdzanie jest wykonywane tylko na końcu wywołania metody prowadzące do tej klasy. Dzieje się również, jeśli klasa jest ponowne wprowadzenie ze względu na wywołanie metody w innej klasy. Invariants nie są sprawdzane dla obiektu finalizatory lub dowolnej metody, które implementują <xref:System.IDisposable.Dispose%2A> metody.  
  
<a name="usage_guidelines"></a>   
## <a name="usage-guidelines"></a>Wytyczne dotyczące użycia  
  
### <a name="contract-ordering"></a>Kolejność kontraktu  
 W poniższej tabeli przedstawiono kolejność elementów, którego należy używać podczas pisania metoda umów.  
  
|`If-then-throw statements`|Warunki wstępne publicznych zgodne z poprzednimi wersjami|  
|-|-|  
|<xref:System.Diagnostics.Contracts.Contract.Requires%2A>|Wszystkie warunki wstępne publicznych.|  
|<xref:System.Diagnostics.Contracts.Contract.Ensures%2A>|Wszystkich warunków końcowych publiczny (normalne).|  
|<xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>|Wszystkich warunków końcowych publicznych wyjątkowych.|  
|<xref:System.Diagnostics.Contracts.Contract.Ensures%2A>|Wszystkich warunków końcowych prywatne/wewnętrzny (normalne).|  
|<xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>|Wszystkich warunków końcowych prywatne/wewnętrzny wyjątkowych.|  
|<xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A>|Jeśli przy użyciu `if` - `then` - `throw` stylu warunki wstępne bez żadnych innych umów, Umieść wywołanie <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A> z informacją, że wszystkie poprzednie, w przypadku sprawdzania warunków wstępnych.|  
  
<a name="purity"></a>   
### <a name="purity"></a>Czystość  
 Wszystkie metody, które są wywoływane w ramach kontraktu musi być czysty; oznacza to nie muszą zaktualizować dowolny stan przeniosła istniejące wcześniej. Czystej metody może modyfikować obiekty, które zostały utworzone po wejściu w czystej metody.  
  
 Obecnie narzędzia kontraktu kodu założono, czy czystego następujących elementów kodu:  
  
-   Metody, które są oznaczone <xref:System.Diagnostics.Contracts.PureAttribute>.  
  
-   Typy, które są oznaczone <xref:System.Diagnostics.Contracts.PureAttribute> (atrybut ma zastosowanie do wszystkich typów, metod).  
  
-   Właściwość metody dostępu get.  
  
-   Operatory (metody statyczne, których nazwy rozpoczynają się od "op" oraz że masz jeden lub dwa parametry oraz zwracany typ inny niż void).  
  
-   Każda metoda, której w pełni kwalifikowana nazwa zaczyna się od "System.Diagnostics.Contracts.Contract", "System.String", "System.IO.Path" lub "System.Type".  
  
-   Dowolny wywoływany delegat, pod warunkiem, że sam typ delegata jest związana z <xref:System.Diagnostics.Contracts.PureAttribute>. Typy delegatów <xref:System.Predicate%601?displayProperty=nameWithType> i <xref:System.Comparison%601?displayProperty=nameWithType> są traktowane jako czysty.  
  
<a name="visibility"></a>   
### <a name="visibility"></a>Widoczność  
 Wszystkie elementy członkowskie wymienione w kontraktu musi być co najmniej jako widoczny jako metody, w jakiej są wyświetlane. Na przykład pola prywatnego nie może być wymienione w wstępnym publiczną metodę; Klienci nie można zweryfikować takie umowy, zanim wywołują metodę. Jednakże jeśli pole jest oznaczona atrybutem <xref:System.Diagnostics.Contracts.ContractPublicPropertyNameAttribute>, jest wykluczony z tych reguł.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje użycie kontrakty kodu.  
  
 [!code-csharp[ContractExample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/contractexample/cs/program.cs#1)]
 [!code-vb[ContractExample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/contractexample/vb/program.vb#1)]
