---
title: Kontrakty kodu
description: Eksploruj kontrakty kodu, które umożliwiają określenie warunków wstępnych, warunki końcowe i niezmiennych obiektów w kodzie .NET.
ms.date: 09/05/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Code contracts
ms.assetid: 84526045-496f-489d-8517-a258cf76f040
ms.openlocfilehash: 60f794373af75bd3f745c224e0a8c7a84192e4c4
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904146"
---
# <a name="code-contracts"></a>Kontrakty kodu

Kontrakty kodu umożliwiają określenie nieokreślonych warunków wstępnych, warunki końcowe i niezmiennych obiektów w kodzie. Warunki wstępne to wymagania, które muszą zostać spełnione podczas wprowadzania metody lub właściwości. Warunki końcowe opisują oczekiwania w czasie, gdy metoda lub kod właściwości zostanie zakończony. Nieposiadające obiektu opisują oczekiwany stan klasy, która jest w dobrym stanie.

Umowy code obejmują klasy do oznaczania kodu, Analizator statyczny dla analizy czasu kompilowania i Analizator środowiska uruchomieniowego. Klasy kontraktów kodu można znaleźć w <xref:System.Diagnostics.Contracts> przestrzeni nazw.

Zalety kontraktów kodu obejmują następujące elementy:

- Ulepszone testowanie: kontrakty kodu zapewniają weryfikację kontraktu statycznego, sprawdzanie środowiska uruchomieniowego i generowanie dokumentacji.

- Narzędzia do automatycznego testowania: można użyć kontraktów kodu do wygenerowania bardziej zrozumiałych testów jednostkowych przez odfiltrowanie niezgodnych argumentów testowych niespełniających warunków wstępnych.

- Weryfikacja statyczna: kontroler statyczny może zdecydować, czy istnieją naruszenia umowy bez uruchamiania programu. Sprawdza niejawne kontrakty, takie jak odwołania do wartości null i granice tablicy oraz jawne umowy.

- Dokumentacja referencyjna: generator dokumentacji rozszerza istniejące pliki dokumentacji XML o informacje o kontrakcie. Istnieją również arkusze stylów, które mogą być używane z [Sandcastle](https://github.com/EWSoftware/SHFB) , aby wygenerowane strony dokumentacji zawierały sekcje kontraktu.

Wszystkie języki .NET Framework mogą natychmiast korzystać z umów. nie trzeba pisać specjalnego parsera ani kompilatora. Dodatek Visual Studio umożliwia określenie poziomu analizy kontraktu kodu do wykonania. Analizatory mogą potwierdzić, że umowy są dobrze sformułowane (sprawdzanie typu i rozpoznawanie nazw) i mogą generować skompilowaną postać umów w formacie języka pośredniego (MSIL) firmy Microsoft. Kontrakty tworzenia w programie Visual Studio umożliwiają skorzystanie z standardowej technologii IntelliSense dostępnej przez narzędzie.

Większość metod w klasie kontraktu jest warunkowo kompilowane; oznacza to, że kompilator emituje wywołania tych metod tylko wtedy, gdy definiujesz symbol specjalny, CONTRACTS_FULL, za pomocą `#define` dyrektywy. CONTRACTS_FULL pozwala pisać kontrakty w kodzie bez stosowania `#ifdef` dyrektyw. można generować różne kompilacje, niektóre z kontraktami i niektóre z nich.

Aby poznać narzędzia i szczegółowe instrukcje dotyczące korzystania z kontraktów kodu, zobacz temat [kontrakty kodu](https://marketplace.visualstudio.com/items?itemName=RiSEResearchinSoftwareEngineering.CodeContractsforNET) w witrynie Visual Studio Marketplace.

## <a name="preconditions"></a>Warunki wstępne

Warunki wstępne można wyrazić za pomocą <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType> metody. Warunki wstępne określają stan, gdy wywoływana jest metoda. Są one zwykle używane do określania prawidłowych wartości parametrów. Wszystkie składowe, które są wymienione w warunkach wstępnych, muszą być co najmniej tak samo samo jak metoda; w przeciwnym razie warunek wstępny może nie być zrozumiały dla wszystkich wywołujących metod. Warunek nie może mieć efektów ubocznych. Zachowanie warunków wstępnych zakończonych niepowodzeniem jest określane przez analizator czasu wykonywania.

Na przykład następujący warunek wstępny oznacza, że parametr `x` nie może mieć wartości null.

```csharp
Contract.Requires(x != null);
```

Jeśli kod musi zgłosić konkretny wyjątek w przypadku niepowodzenia warunku wstępnego, można użyć ogólnego przeciążenia <xref:System.Diagnostics.Contracts.Contract.Requires%2A> w następujący sposób.

```csharp
Contract.Requires<ArgumentNullException>(x != null, "x");
```

### <a name="legacy-requires-statements"></a>Starsze instrukcje wymagają instrukcji

Większość kodu zawiera weryfikację parametrów w postaci `if` - `then` - `throw` kodu. Narzędzia kontraktowe rozpoznają te instrukcje jako warunki wstępne w następujących przypadkach:

- Instrukcje są wyświetlane przed innymi instrukcjami w metodzie.

- W całym zestawie takich instrukcji następuje jawne <xref:System.Diagnostics.Contracts.Contract> wywołanie metody, takie jak wywołanie <xref:System.Diagnostics.Contracts.Contract.Requires%2A> metody,, <xref:System.Diagnostics.Contracts.Contract.Ensures%2A> <xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A> lub <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A> .

Gdy `if` - `then` - `throw` w tym formularzu pojawiają się instrukcje, narzędzia te rozpoznają je jako starsze `requires` instrukcje. Jeśli żadna inna umowa nie jest zgodna z `if` - `then` - `throw` sekwencją, należy zakończyć kod przy użyciu <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A?displayProperty=nameWithType> metody.

```csharp
if (x == null) throw new ...
Contract.EndContractBlock(); // All previous "if" checks are preconditions
```

Należy zauważyć, że warunek w poprzednim teście to Negacja warunku wstępnego. (Rzeczywisty warunek wstępny to `x != null` ). Negacja warunku wstępnego jest wysoce ograniczony: musi być zapisany, jak pokazano w poprzednim przykładzie; oznacza to, że nie powinien zawierać `else` klauzul, a treść `then` klauzuli musi być pojedynczą `throw` instrukcją. `if`Test podlega obu regułom czystości i widoczności (zobacz [wskazówki dotyczące użycia](#usage_guidelines)), ale `throw` wyrażenie jest poddawane tylko regułom czystości. Jednak typ zgłoszonego wyjątku musi być tak widoczny jak metoda, w której występuje kontrakt.

## <a name="postconditions"></a>Warunki końcowe

Warunki końcowe są kontraktami dla stanu metody po jej zakończeniu. Błąd warunku końcowego jest sprawdzany tuż przed opuszczeniem metody. Zachowanie w czasie wykonywania zakończone niepowodzeniem warunki końcowe jest określane przez analizator czasu wykonywania.

W przeciwieństwie do warunków wstępnych, warunki końcowe może odwoływać się do członków z mniej widocznymi elementami. Klient może nie być w stanie zrozumieć ani korzystać z niektórych informacji wyrażonych przez błąd warunku końcowego przy użyciu stanu prywatnego, ale nie ma to wpływu na zdolność klienta do poprawnego używania metody.

### <a name="standard-postconditions"></a>Standardowa warunki końcowe

Standardową warunki końcowe można wyrazić za pomocą <xref:System.Diagnostics.Contracts.Contract.Ensures%2A> metody. Warunki końcowe Express warunek, który musi być `true` przy normalnym zakończeniu metody.

```csharp
Contract.Ensures(this.F > 0);
```

### <a name="exceptional-postconditions"></a>Wyjątkowe warunki końcowe

Wyjątkowe warunki końcowe są warunki końcowe, które powinny być w `true` sytuacji, gdy konkretny wyjątek jest zgłaszany przez metodę. Możesz określić te warunki końcowe przy użyciu <xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A?displayProperty=nameWithType> metody, jak pokazano w poniższym przykładzie.

```csharp
Contract.EnsuresOnThrow<T>(this.F > 0);
```

Argument jest warunkiem, który musi być `true` zawsze, gdy zostanie zgłoszony wyjątek, który jest podtypem `T` .

Istnieją pewne typy wyjątków, których trudno użyć w wyjątkowych błąd warunku końcowego. Na przykład użycie typu <xref:System.Exception> dla `T` wymaga metody do zagwarantowania warunku niezależnie od typu zgłoszonego wyjątku, nawet jeśli jest to przepełnienie stosu lub inny wyjątek niemożliwy do kontroli. Należy używać wyjątkowych warunki końcowe tylko dla określonych wyjątków, które mogą być zgłaszane, gdy element członkowski jest wywoływany, na przykład gdy <xref:System.InvalidTimeZoneException> zostanie zgłoszony dla <xref:System.TimeZoneInfo> wywołania metody.

### <a name="special-postconditions"></a>Specjalne warunki końcowe

Następujące metody mogą być używane tylko w warunki końcowe:

- Można odwołać się do wartości zwracanych przez metodę w warunki końcowe przy użyciu wyrażenia `Contract.Result<T>()` , gdzie `T` jest zastępowane zwracanym typem metody. Gdy kompilator nie może wywnioskować typu, należy go jawnie udostępnić. Na przykład kompilator języka C# nie może wywnioskować typów dla metod, które nie przyjmują żadnych argumentów, dlatego wymaga następujących błąd warunku końcowego: `Contract.Ensures(0 <Contract.Result<int>())` metody z typem zwracanym `void` nie mogą odwoływać się do `Contract.Result<T>()` warunki końcowe.

- Wartość stanu początkowego w błąd warunku końcowego odwołuje się do wartości wyrażenia na początku metody lub właściwości. Używa wyrażenia `Contract.OldValue<T>(e)` , gdzie `T` jest typem `e` . Argument typu ogólnego można pominąć zawsze, gdy kompilator może wywnioskować swój typ. (Na przykład kompilator języka C# zawsze wnioskuje typ, ponieważ przyjmuje argument). Istnieją pewne ograniczenia dotyczące tego, co może wystąpić w programie `e` oraz konteksty, w których może się pojawić stare wyrażenie. Stare wyrażenie nie może zawierać innego starego wyrażenia. Co najważniejsze, stare wyrażenie musi odwoływać się do wartości, która istniała w stanie warunku wstępnego metody. Innymi słowy, musi być wyrażeniem, które może być oceniane tak długo, jak warunek wstępny metody `true` . Oto kilka wystąpień tej reguły.

  - Wartość musi istnieć w stanie warunku wstępnego metody. Aby można było odwołać się do pola w obiekcie, warunki wstępne muszą zagwarantować, że obiekt jest zawsze inny niż null.

  - Nie można odwołać się do wartości zwracanej metody w starym wyrażeniu:

      ```csharp
      Contract.OldValue(Contract.Result<int>() + x) // ERROR
      ```

  - Nie można odwołać się do `out` parametrów w starym wyrażeniu.

  - Stare wyrażenie nie może zależeć od zmiennej powiązanej kwantyfikatora, jeśli zakres kwantyfikatora zależy od wartości zwracanej przez metodę:

      ```csharp
      Contract.ForAll(0, Contract.Result<int>(), i => Contract.OldValue(xs[i]) > 3); // ERROR
      ```

  - Stare wyrażenie nie może odwoływać się do parametru delegata anonimowego w <xref:System.Diagnostics.Contracts.Contract.ForAll%2A> wywołaniu lub, <xref:System.Diagnostics.Contracts.Contract.Exists%2A> chyba że jest używany jako indeksator lub argument wywołania metody:

      ```csharp
      Contract.ForAll(0, xs.Length, i => Contract.OldValue(xs[i]) > 3); // OK
      Contract.ForAll(0, xs.Length, i => Contract.OldValue(i) > 3); // ERROR
      ```

  - Stare wyrażenie nie może wystąpić w treści delegata anonimowego, jeśli wartość starego wyrażenia zależy od któregokolwiek z parametrów delegata anonimowego, chyba że delegat anonimowy jest argumentem <xref:System.Diagnostics.Contracts.Contract.ForAll%2A> <xref:System.Diagnostics.Contracts.Contract.Exists%2A> metody lub:

      ```csharp
      Method(... (T t) => Contract.OldValue(... t ...) ...); // ERROR
      ```

  - `Out`parametry powodują problem, ponieważ kontrakty są wyświetlane przed treścią metody, a większość kompilatorów nie zezwala na odwołania do `out` parametrów w warunki końcowe. Aby rozwiązać ten problem, <xref:System.Diagnostics.Contracts.Contract> Klasa udostępnia <xref:System.Diagnostics.Contracts.Contract.ValueAtReturn%2A> metodę, która umożliwia błąd warunku końcowego na podstawie `out` parametru.

      ```csharp
      public void OutParam(out int x)
      {
          Contract.Ensures(Contract.ValueAtReturn(out x) == 3);
          x = 3;
      }
      ```

      Podobnie jak w przypadku <xref:System.Diagnostics.Contracts.Contract.OldValue%2A> metody, można pominąć parametr typu generycznego za każdym razem, gdy kompilator może wywnioskować swój typ. Zastąpienie kontraktu zastępuje wywołanie metody wartością `out` parametru. <xref:System.Diagnostics.Contracts.Contract.ValueAtReturn%2A>Metoda może występować tylko w warunki końcowe. Argument metody musi być `out` parametrem lub polem `out` parametru struktury. Ta ostatnia jest również przydatna w przypadku odwoływania się do pól w błąd warunku końcowego konstruktora struktury.

      > [!NOTE]
      > Obecnie narzędzia do analizy kontraktu kodu nie sprawdzają, czy `out` Parametry są inicjowane prawidłowo, i nie należy ignorować ich wzmianki w błąd warunku końcowego. W związku z tym w poprzednim przykładzie, jeśli wiersz po kontrakcie używał wartości `x` zamiast przypisywania liczby całkowitej do niej, kompilator nie wystawia poprawnego błędu. Jednak w przypadku kompilacji, w której nie jest zdefiniowany symbol preprocesora CONTRACTS_FULL (takie jak kompilacja w wersji ASA), kompilator wygeneruje błąd.

## <a name="invariants"></a>Nieposiadające wariantów

Niewarianty obiektu to warunki, które powinny być spełnione dla każdego wystąpienia klasy, gdy ten obiekt jest widoczny dla klienta. Wyrażają one warunki, zgodnie z którymi obiekt jest uznawany za poprawny.

Niezmienne metody są identyfikowane za pomocą <xref:System.Diagnostics.Contracts.ContractInvariantMethodAttribute> atrybutu. Metody niezmiennej nie mogą zawierać kodu z wyjątkiem sekwencji wywołań <xref:System.Diagnostics.Contracts.Contract.Invariant%2A> metody, z których każdy określa indywidualną niezmienną, jak pokazano w poniższym przykładzie.

```csharp
[ContractInvariantMethod]
protected void ObjectInvariant ()
{
    Contract.Invariant(this.y >= 0);
    Contract.Invariant(this.x > this.y);
    ...
}
```

Niewarianty są warunkowo definiowane przez symbol preprocesora CONTRACTS_FULL. Podczas sprawdzania w czasie wykonywania, nieposiadanie wariantów jest sprawdzane na końcu każdej metody publicznej. Jeśli niezmienna wymienia metodę publiczną w tej samej klasie, sprawdzenie niezmiennej, które zwykle występuje na końcu tej metody publicznej, jest wyłączone. Zamiast tego sprawdzanie odbywa się tylko na końcu najbardziej zewnętrznego wywołania metody do tej klasy. Dzieje się tak, jeśli Klasa zostanie dodana z powodu wywołania metody w innej klasie. Nie sprawdzono wariantów dla finalizatora obiektu i <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementacji.

<a name="usage_guidelines"></a>

## <a name="usage-guidelines"></a>Zalecenia dotyczące użytkowania

### <a name="contract-ordering"></a>Porządkowanie kontraktu

W poniższej tabeli przedstawiono kolejność elementów, które powinny być używane podczas pisania kontraktów metod.

|`If-then-throw statements`|Publiczne warunki wstępne zgodne z poprzednimi wersjami|
|-|-|
|<xref:System.Diagnostics.Contracts.Contract.Requires%2A>|Wszystkie publiczne warunki wstępne.|
|<xref:System.Diagnostics.Contracts.Contract.Ensures%2A>|Wszystkie publiczne (normalne) warunki końcowe.|
|<xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>|Wszystkie publiczne wyjątkowe warunki końcowe.|
|<xref:System.Diagnostics.Contracts.Contract.Ensures%2A>|Wszystkie prywatne/wewnętrzne (normalne) warunki końcowe.|
|<xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>|Wszystkie prywatne/wewnętrzne wyjątkowe warunki końcowe.|
|<xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A>|Jeśli używasz `if` - `then` - `throw` warunków wstępnych stylu bez żadnych innych umów, umieść wywołanie do <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A> , aby wskazać, że wszystkie poprzednie testy są warunkiem wstępnym.|

<a name="purity"></a>

### <a name="purity"></a>Czystości

Wszystkie metody, które są wywoływane w ramach kontraktu, muszą być czyste; oznacza to, że nie mogą zaktualizować żadnego istniejącego stanu. Czysta Metoda pozwala modyfikować obiekty, które zostały utworzone po wprowadzeniu do czystej metody.

Narzędzia kontraktu kodu założono, że następujące elementy kodu są czyste:

- Metody oznaczone przy użyciu <xref:System.Diagnostics.Contracts.PureAttribute> .

- Typy, które są oznaczone <xref:System.Diagnostics.Contracts.PureAttribute> atrybutem (ma zastosowanie do wszystkich metod typu).

- Metody dostępu get właściwości.

- Operatory (metody static, których nazwy zaczynają się od "op" i mają jeden lub dwa parametry i typ zwracany non-void).

- Każda metoda, której w pełni kwalifikowana nazwa zaczyna się od "System. Diagnostics. Contracts. kontrakcie", "System. String", "System. IO. Path" lub "System. Type".

- Każdy wywołany delegat, pod warunkiem, że typ delegata jest przypisany do <xref:System.Diagnostics.Contracts.PureAttribute> . Typy delegatów <xref:System.Predicate%601?displayProperty=nameWithType> i <xref:System.Comparison%601?displayProperty=nameWithType> są uważane za czyste.

<a name="visibility"></a>

### <a name="visibility"></a>Widoczność

Wszystkie elementy członkowskie wymienione w kontrakcie muszą być co najmniej widoczne jako metody, w której się pojawiają. Na przykład pole prywatne nie może być wymienione w warunku wstępnego dla metody publicznej; Klienci nie mogą sprawdzić poprawności takiego kontraktu przed wywołaniem metody. Jeśli jednak pole jest oznaczone przy użyciu <xref:System.Diagnostics.Contracts.ContractPublicPropertyNameAttribute> , jest ono wykluczone z tych reguł.

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono użycie kontraktów kodu.

[!code-csharp[ContractExample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/contractexample/cs/program.cs#1)]
[!code-vb[ContractExample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/contractexample/vb/program.vb#1)]
