---
title: Architektura i projekt
ms.date: 03/30/2017
ms.assetid: bd738d39-00e2-4bab-b387-90aac1a014bd
ms.openlocfilehash: 35fbc39db23a2b08ab926e122d2f1eb1806a369b
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040024"
---
# <a name="architecture-and-design"></a>Architektura i projekt

Moduł generowania kodu SQL w ramach [dostawcy przykładu](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) jest zaimplementowany jako gość w drzewie wyrażenia, który reprezentuje drzewo poleceń. Generowanie jest wykonywane w jednym przebiegu w drzewie wyrażenia.

Węzły drzewa są przetwarzane od dołu do góry. Najpierw jest generowana struktura pośrednia: SqlSelectStatement lub SqlBuilder, implementująca ISqlFragment. Następnie instrukcja SQL String jest generowana z tej struktury. Istnieją dwie przyczyny dla struktury pośredniej:

- Logicznie instrukcja SELECT języka SQL jest wypełniana poza kolejnością. Węzły, które uczestniczą w klauzuli FROM, są odwiedzane przed węzłami, które uczestniczą w klauzuli WHERE, GROUP BY i ORDER BY.

- Aby zmienić nazwy aliasów, należy zidentyfikować wszystkie używane aliasy, aby uniknąć kolizji podczas zmiany nazwy. Aby odroczyć opcje zmiany nazwy w elemencie SqlBuilder, Użyj obiektów symboli do reprezentowania kolumn, które są kandydatami do zmiany nazwy.

![4b](./media/de1ca705-4f7c-4d2d-ace5-afefc6d3cefa.gif "de1ca705-4f7c-4d2d-ace5-afefc6d3cefa")

W pierwszej fazie, podczas odwiedzania drzewa wyrażenia, wyrażenia są pogrupowane w SqlSelectStatements, sprzężenia są spłaszczone i aliasy sprzężenia są spłaszczone. W trakcie tego przebiegu obiekty symboli reprezentują kolumny lub aliasy wejściowe, których nazwy można zmienić.

W drugiej fazie podczas tworzenia rzeczywistego ciągu aliasy są zmieniane.

## <a name="data-structures"></a>Struktury danych

W tej sekcji omówiono typy używane w [przykładowym dostawcy](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) , który służy do tworzenia instrukcji SQL.

### <a name="isqlfragment"></a>ISqlFragment

Ta sekcja obejmuje klasy implementujące interfejs ISqlFragment, który służy do dwóch celów:

- Wspólny typ zwracany dla wszystkich metod odwiedzających.

- Zwraca metodę zapisu końcowego ciągu SQL.

```csharp
internal interface ISqlFragment {
   void WriteSql(SqlWriter writer, SqlGenerator sqlGenerator);
}
```

#### <a name="sqlbuilder"></a>SqlBuilder

SqlBuilder to urządzenie zbierające dla końcowego ciągu SQL, podobne do StringBuilder. Składa się z ciągów, które składają się na końcowy kod SQL, wraz z ISqlFragments, które mogą być konwertowane na ciągi.

```csharp
internal sealed class SqlBuilder : ISqlFragment {
   public void Append(object s)
   public void AppendLine()
   public bool IsEmpty
}
```

#### <a name="sqlselectstatement"></a>SqlSelectStatement

SqlSelectStatement przedstawia kanoniczną instrukcję SQL SELECT kształtu "SELECT... Z.. GDZIE... GRUPUJ WEDŁUG... ORDER BY ".

Każda klauzula SQL jest reprezentowana przez element StringBuilder. Ponadto śledzi, czy określono różne i czy instrukcja jest najwyższej wartości. Jeśli instrukcja nie jest najwyższej strony, klauzula ORDER BY jest pomijana, chyba że instrukcja ma również klauzulę TOP.

FromExtents zawiera listę wejść dla instrukcji SELECT. W tym miejscu znajduje się zazwyczaj tylko jeden element. Instrukcje SELECT dla sprzężeń mogą tymczasowo mieć więcej niż jeden element.

Jeśli instrukcja SELECT jest tworzona przez węzeł sprzężenia, SqlSelectStatement utrzymuje listę wszystkich zakresów, które zostały spłaszczone w sprzężeniu w AllJoinExtents. OuterExtents reprezentuje zewnętrzne odwołania SqlSelectStatement i służy do zmiany nazwy aliasu wejściowego.

```csharp
internal sealed class SqlSelectStatement : ISqlFragment {
   internal bool IsDistinct { get, set };
   internal bool IsTopMost

   internal List<Symbol> AllJoinExtents { get, set };
   internal List<Symbol> FromExtents { get};
   internal Dictionary<Symbol, bool> OuterExtents { get};

   internal TopClause Top { get, set };

   internal SqlBuilder Select {get};
   internal SqlBuilder From
   internal SqlBuilder Where
   internal SqlBuilder GroupBy
   public SqlBuilder OrderBy
}
```

#### <a name="topclause"></a>TopClause

TopClause reprezentuje wyrażenie TOP w SqlSelectStatement. Właściwość TopCount wskazuje liczbę GÓRNych wierszy, które powinny być zaznaczone.  Gdy WithTies ma wartość true, TopClause została skompilowana z DbLimitExpression.

```csharp
class TopClause : ISqlFragment {
   internal bool WithTies {get}
   internal ISqlFragment TopCount {get}
   internal TopClause(ISqlFragment topCount, bool withTies)
   internal TopClause(int topCount, bool withTies)
}
```

### <a name="symbols"></a>Symbole

Klasy związane z symbolami i tabela symboli wykonują zmiany nazw aliasów wejściowych, spłaszczania aliasów i aliasów kolumn.

Klasa symbol reprezentuje zakres, zagnieżdżoną instrukcję SELECT lub kolumnę. Jest ona używana zamiast rzeczywistego aliasu, aby umożliwić zmianę nazwy po jej użyciu i zawiera również dodatkowe informacje o artefaktie, który reprezentuje (podobnie jak typ).

```csharp
class Symbol : ISqlFragment {
   internal Dictionary<string, Symbol> Columns {get}
   internal bool NeedsRenaming {get, set}
   internal bool IsUnnest {get, set}   //not used

   public string Name{get}
   public string NewName {get,set}
   internal TypeUsage Type {get, set}

   public Symbol(string name, TypeUsage type)
}
```

Nazwa przechowuje oryginalny alias dla reprezentowanego zakresu, zagnieżdżonej instrukcji SELECT lub kolumny.

NewName przechowuje alias, który będzie używany w instrukcji SELECT języka SQL. Początkowo została ustawiona nazwa i w razie potrzeby jest zmieniana tylko w przypadku generowania końcowego zapytania ciągu.

Typ jest przydatny tylko w przypadku symboli reprezentujących zakresy i zagnieżdżone instrukcje SELECT.

#### <a name="symbolpair"></a>SymbolPair

Klasa SymbolPair usuwa spłaszczone rekordy.

Rozważ wyrażenie właściwości D (v, "J3. j2. J1. a. x"), gdzie v jest VarRef, J1, j2, J3 jest przyłączaniem, a jest zakresem, a x jest kolumnami.

Ten element musi zostać przetłumaczony na {j '}. {x '}. Pole Source reprezentuje niezależny element sqlstateer reprezentujący wyrażenie join (Powiedz J2); jest to zawsze symbol sprzężenia. Pole kolumny jest przenoszone z jednego symbolu sprzężenia do następnego, dopóki nie zostanie zatrzymane na symbolu bez sprzężenia. Jest on zwracany podczas odwiedzania elementu DbPropertyExpression, ale nigdy nie jest dodawany do elementu SqlBuilder.

```csharp
class SymbolPair : ISqlFragment {
   public Symbol Source;
   public Symbol Column;
   public SymbolPair(Symbol source, Symbol column)
}
```

#### <a name="joinsymbol"></a>JoinSymbol

Symbol sprzężenia jest symbolem, który reprezentuje zagnieżdżoną instrukcję SELECT z przyłączeniem lub wejściem sprzężenia.

```csharp
internal sealed class JoinSymbol : Symbol {
   internal List<Symbol> ColumnList {get, set}
   internal List<Symbol> ExtentList {get}
   internal List<Symbol> FlattenedExtentList {get, set}
   internal Dictionary<string, Symbol> NameToExtent {get}
   internal bool IsNestedJoin {get, set}

   public JoinSymbol(string name, TypeUsage type, List<Symbol> extents)
}
```

ColumnList reprezentuje listę kolumn w klauzuli SELECT, jeśli ten symbol reprezentuje instrukcję SELECT języka SQL. ExtentList jest listą zakresów w klauzuli SELECT. Jeśli sprzężenie ma wiele zakresów spłaszczonych na najwyższego poziomu, FlattenedExtentList śledzi zakres, aby upewnić się, że nazwy aliasów zakresów zostały poprawnie zmienione.

NameToExtent ma wszystkie zakresy w ExtentList jako słownik. IsNestedJoin służy do określenia, czy JoinSymbol jest zwykłym symbolem sprzężenia, czy taki, który ma odpowiednie SqlSelectStatement.

Wszystkie listy są ustawiane dokładnie raz, a następnie używane do wyszukiwania lub wyliczania.

#### <a name="symboltable"></a>Symbol

Symbol jest używany do rozpoznawania nazw zmiennych do symboli. Symbol jest zaimplementowany jako stos z nowym wpisem dla każdego zakresu. Wyszukiwania wyszukują od góry stosu do dołu do momentu znalezienia wpisu.

```csharp
internal sealed class SymbolTable {
   internal void EnterScope()
   internal void ExitScope()
   internal void Add(string name, Symbol value)
   internal Symbol Lookup(string name)
}
```

Istnieje tylko jeden symbol w jednym wystąpieniu modułu generacji SQL. Zakresy są wprowadzane i zamykane dla każdego węzła relacyjnego. Wszystkie symbole we wcześniejszych zakresach są widoczne dla nowszych zakresów, chyba że są ukryte przez inne symbole o tej samej nazwie.

### <a name="global-state-for-the-visitor"></a>Globalny stan dla gościa

Aby ułatwić zmianę nazwy aliasów i kolumn, należy zachować listę wszystkich nazw kolumn (AllColumnNames) i aliasów zakresów (AllExtentNames), które zostały użyte podczas pierwszego przekazywania drzewa zapytań.  Tabela symboli rozpoznaje nazwy zmiennych do symboli. IsVarRefSingle jest używane tylko na potrzeby weryfikacji, nie jest to absolutnie konieczne.

Dwa stosy używane przez CurrentSelectStatement i IsParentAJoin są używane do przekazywania "parametrów" z węzłów nadrzędnych do elementów podrzędnych, ponieważ wzorzec gościa nie zezwala nam na przekazywanie parametrów.

```csharp
internal Dictionary<string, int> AllExtentNames {get}
internal Dictionary<string, int> AllColumnNames {get}
SymbolTable symbolTable = new SymbolTable();
bool isVarRefSingle = false;

Stack<SqlSelectStatement> selectStatementStack;
private SqlSelectStatement CurrentSelectStatement{get}

Stack<bool> isParentAJoinStack;
private bool IsParentAJoin{get}
```

## <a name="common-scenarios"></a>Typowe scenariusze

W tej sekcji omówiono typowe scenariusze dostawcy.

### <a name="grouping-expression-nodes-into-sql-statements"></a>Grupowanie węzłów wyrażenia w instrukcjach SQL

SqlSelectStatement jest tworzony podczas napotkania pierwszego węzła relacyjnego (zazwyczaj jest to DbScanExpression zakres) podczas odwiedzania drzewa od dołu. Aby utworzyć instrukcję SELECT języka SQL z jak najmniejszej liczby zagnieżdżonych zapytań, należy agregować jako wiele węzłów nadrzędnych, jak to możliwe w tym SqlSelectStatement.

Decyzja o tym, czy dany węzeł (relacyjny) może zostać dodany do bieżącej SqlSelectStatement (zwracany podczas odwiedzania danych wejściowych) lub czy nowa instrukcja musi być uruchomiona jest obliczana przez metodę iscompatibled i zależy od tego, co jest już w SqlSelectStatement, który zależy od tego, jakie węzły znajdowały się poniżej danego węzła.

Zazwyczaj jeśli klauzule instrukcji SQL są oceniane po klauzulach, w których węzły uważane za scalanie nie są puste, nie można dodać węzła do bieżącej instrukcji. Na przykład jeśli następny węzeł jest filtrem, ten węzeł może być dołączany do bieżącego SqlSelectStatement tylko wtedy, gdy spełnione są następujące warunki:

- Lista wyboru jest pusta. Jeśli lista wyboru nie jest pusta, lista wyboru została utworzona przez węzeł poprzedzający filtr, a predykat może odwoływać się do kolumn utworzonych przez tę listę wyboru.

- Wartość GROUPBY jest pusta. Jeśli wartość GROUPBY nie jest pusta, dodanie filtru oznacza filtrowanie przed zgrupowaniem, co jest niepoprawne.

- Klauzula TOP jest pusta. Jeśli klauzula TOP nie jest pusta, dodanie filtru oznacza filtrowanie przed wykonaniem góry, co jest niepoprawne.

Nie dotyczy to węzłów nierelacyjnych, takich jak DbConstantExpression lub Expressions, ponieważ są one zawsze uwzględniane jako część istniejącej SqlSelectStatement.

Ponadto w przypadku napotkania głównego drzewa sprzężenia (węzłem sprzężenia, który nie ma nadrzędnego elementu join), jest uruchamiany nowy SqlSelectStatement. Wszystkie lewe pokrętło dołączania do elementów podrzędnych są agregowane w tym SqlSelectStatement.

Za każdym razem, gdy nowa SqlSelectStatement jest uruchomiona, a bieżąca jest dodawana do danych wejściowych, może być konieczne ukończenie bieżącego SqlSelectStatement przez dodanie kolumn projekcji (klauzula SELECT), jeśli taka nie istnieje. Jest to realizowane przy użyciu metody AddDefaultColumns, która przegląda FromExtents SqlSelectStatement i dodaje wszystkie kolumny, które lista zakresów reprezentowana przez FromExtents znajduje się w zakresie do listy rzutowanych kolumn. Dzieje się tak, ponieważ w tym momencie jest nieznane, do których kolumn odwołują się inne węzły. Można to zoptymalizować tylko w celu zaprojektowania kolumn, które mogą być później używane.

### <a name="join-flattening"></a>Przyłączanie spłaszczania

Właściwość IsParentAJoin pomaga określić, czy dany element Join może być spłaszczony. W szczególności IsParentAJoin zwraca `true` tylko dla lewego elementu podrzędnego sprzężenia i dla każdego DbScanExpression, który jest bezpośrednim wejściem do sprzężenia, w takim przypadku ten węzeł podrzędny ponownie używa tego samego SqlSelectStatement, którego obiekt nadrzędny mógłby później użyć. Aby uzyskać więcej informacji, zobacz "wyrażenia sprzężenia".

### <a name="input-alias-redirecting"></a>Przekierowanie wejściowej aliasu

Przekierowanie aliasu wejściowego jest realizowane przy użyciu tabeli symboli.

Aby wyjaśnić Przekierowywanie aliasów wejściowych, zapoznaj się z pierwszym przykładem [generowania kodu SQL z drzew poleceń — najlepsze rozwiązania](generating-sql-from-command-trees-best-practices.md).  W projekcji należy przekierować "a" do "b".

Po utworzeniu obiektu SqlSelectStatement zakres, który jest wejściem do węzła, jest umieszczany we właściwości From SqlSelectStatement. Symbol (\<symbol_b >) jest tworzony na podstawie nazwy powiązania wejściowego ("b"), aby reprezentować ten zakres i "AS" + \<symbol_b > jest dołączany do klauzuli FROM.  Symbol jest również dodawany do właściwości FromExtents.

Symbol jest również dodawany do tabeli symboli, aby połączyć nazwę powiązania wejściowego ("b", \<symbol_b >).

Jeśli kolejny węzeł ponownie używa tego SqlSelectStatement, dodaje wpis do tabeli symboli, aby połączyć jego nazwę powiązania wejściowego z tym symbolem. W naszym przykładzie DbProjectExpression z nazwą powiązania wejściowego "a" spowoduje ponowne użycie SqlSelectStatement i dodanie ("a", \< symbol_b >) do tabeli.

Gdy wyrażenia odwołują się do nazwy powiązania wejściowego węzła, który jest używany SqlSelectStatement, odwołanie jest rozwiązane przy użyciu tabeli symboli do prawidłowego przekierowanego symbolu. Gdy "a" z "a. x" jest rozpoznawany podczas odwiedzania DbVariableReferenceExpression reprezentującego "a", zostanie on rozpoznany jako symbol \<symbol_b >.

### <a name="join-alias-flattening"></a>Przyłączanie spłaszczania aliasów

Spłaszczanie aliasów sprzężenia jest osiągane podczas odwiedzania DbPropertyExpression zgodnie z opisem w sekcji DbPropertyExpression.

### <a name="column-name-and-extent-alias-renaming"></a>Zmiana nazwy kolumny i zakresu aliasu

Nazwa kolumny i alias zakresu zmiany nazwy są rozwiązywane przy użyciu symboli, które są zastępowane aliasami w drugiej fazie generacji opisanej w sekcji druga faza generowania kodu SQL: generowanie ciągu polecenia.

## <a name="first-phase-of-the-sql-generation-visiting-the-expression-tree"></a>Pierwsza faza generowania kodu SQL: odwiedzanie drzewa wyrażeń

W tej sekcji opisano pierwszą fazę generowania kodu SQL, gdy wyrażenie reprezentujące zapytanie jest odwiedzane i jest generowana struktura pośrednia (SqlSelectStatement lub SqlBuilder).

W tej sekcji opisano zasady odwiedzające różne kategorie węzłów wyrażenia oraz szczegóły odwiedzające określone typy wyrażeń.

### <a name="relational-non-join-nodes"></a>Węzły relacyjne (bez sprzężenia)

Następujące typy wyrażeń obsługują węzły, które nie są przyłączane:

- DbDistinctExpression

- DbFilterExpression

- DbGroupAggregate

- DbLimitExpression

- DbProjectExpression

- DbSkipExpression

- DbSortExpression

Odwiedzanie tych węzłów jest zgodne z następującym wzorcem:

1. Odwiedź dane wejściowe relacyjne i uzyskaj wyniki SqlSelectStatement. Wejście do węzła relacyjnego może być jedną z następujących:

    - Węzeł relacyjny, w tym zakres (na przykład DbScanExpression). Odwiedzenie takiego węzła zwraca SqlSelectStatement.

    - Wyrażenie zestawu operacji (na przykład UNION ALL). Wynik musi być opakowany w nawiasy i umieszczany w klauzuli FROM nowego SqlSelectStatement.

2. Sprawdź, czy bieżący węzeł można dodać do SqlSelectStatement utworzonego przez dane wejściowe. Sekcja zatytułowana wyrażenia grupowania w instrukcjach SQL zawiera opis. Jeśli nie,

    - Wyskakujący bieżący obiekt SqlSelectStatement.

    - Utwórz nowy obiekt SqlSelectStatement i Dodaj zdjęte SqlSelectStatement jako z nowego obiektu SqlSelectStatement.

    - Umieść nowy obiekt na szczycie stosu.

3. Przekieruj powiązanie wyrażenia wejściowego do poprawnego symbolu z danych wejściowych. Te informacje są przechowywane w obiekcie SqlSelectStatement.

4. Dodaj nowy zakres symboli.

5. Sprawdź część niewejściową wyrażenia (na przykład projekcję i predykat).

6. Wyskakujące wszystkie obiekty dodane do stosów globalnych.

 DbSkipExpression nie mają bezpośredniego odpowiednika w SQL. Logicznie, jest tłumaczony na:

```sql
SELECT Y.x1, Y.x2, ..., Y.xn
FROM (
   SELECT X.x1, X.x2, ..., X.xn, row_number() OVER (ORDER BY sk1, sk2, ...) AS [row_number]
   FROM input as X
   ) as Y
WHERE Y.[row_number] > count
ORDER BY sk1, sk2, ...
```

### <a name="join-expressions"></a>Wyrażenia sprzężenia

Następujące są uznawane za wyrażenia sprzężenia i są przetwarzane w typowy sposób przez metodę VisitJoinExpression:

- DbApplyExpression

- DbJoinExpression

- Obiekt DbCrossJoinExpression

Poniżej przedstawiono kroki przedstawione poniżej:

Przed odwiedzeniem elementów podrzędnych IsParentAJoin jest wywoływana w celu sprawdzenia, czy węzeł sprzężenia jest elementem podrzędnym sprzężenia wzdłuż lewego grzbietu. Jeśli zwraca wartość false, zostanie uruchomione nowe SqlSelectStatement. W tym sensie sprzężenia są odwiedzane inaczej niż pozostałe węzły, ponieważ element nadrzędny (węzeł sprzężenia) tworzy SqlSelectStatement dla elementów podrzędnych, które mogą być używane.

Następnie przetwórz dane wejściowe pojedynczo. Dla każdego danych wejściowych:

1. Przejdź do danych wejściowych.

2. Proces post w wyniku odwiedzania danych wejściowych przez wywołanie ProcessJoinInputResult, który jest odpowiedzialny za utrzymanie tabeli symboli po odwiedzeniu elementu podrzędnego wyrażenia sprzężenia i prawdopodobnie kończący SqlSelectStatement utworzony przez element podrzędny. Wynik dziecka może mieć jedną z następujących wartości:

    - SqlSelectStatement różni się od elementu, do którego zostanie dodany element nadrzędny. W takim przypadku może być konieczne ukończenie dodawania kolumn domyślnych. Jeśli dane wejściowe były przyłączone, należy utworzyć nowy symbol sprzężenia. W przeciwnym razie Utwórz symbol normalny.

    - Zakres (na przykład DbScanExpression), w którym to przypadku jest po prostu dodawany do listy danych wejściowych SqlSelectStatement elementu nadrzędnego.

    - To nie jest SqlSelectStatement, w którym to przypadku jest opakowany w nawiasy klamrowe.

    - Ten sam SqlSelectStatement, do którego zostanie dodany element nadrzędny. W takim przypadku Symbole znajdujące się na liście FromExtents muszą zostać zastąpione jednym nowym JoinSymbol, reprezentującym je wszystkie.

    - W pierwszych trzech przypadkach AddFromSymbol jest wywoływana w celu dodania klauzuli AS i zaktualizowania tabeli symboli.

Trzeci, warunek sprzężenia (jeśli istnieje) jest odwiedzany.

### <a name="set-operations"></a>Operacje na zestawie

Zestawy Operations DbUnionAllExpression, wyrażenia DbExceptExpression i DbIntersectExpression są przetwarzane przez metodę VisitSetOpExpression. Tworzy element SqlBuilder kształtu

```xml
<leftSqlSelectStatement> <setOp> <rightSqlSelectStatement>
```

Gdzie \<leftSqlSelectStatement > i \<rightSqlSelectStatement > są SqlSelectStatements uzyskane przez odwiedzenie poszczególnych danych wejściowych, a \<setOp > jest odpowiednią operacją (UNION ALL na przykład).

### <a name="dbscanexpression"></a>DbScanExpression

Jeśli jest odwiedzony w kontekście sprzężenia (jako dane wejściowe do sprzężenia, które jest lewym elementem podrzędnym innego sprzężenia), DbScanExpression zwraca element SqlBuilder z docelowym SQL dla odpowiadającego mu elementu docelowego, który jest wyrażeniem definiującym zapytanie, tabelę lub widok. W przeciwnym razie zostanie utworzona nowa SqlSelectStatement z ustawionym polem FROM, aby odpowiadała odpowiedniemu elementowi docelowemu.

### <a name="dbvariablereferenceexpression"></a>DbVariableReferenceExpression

Odwiedzanie DbVariableReferenceExpression zwraca symbol odpowiadający temu wyrażeniu odwołania do zmiennej na podstawie wyszukiwania w tabeli symboli.

### <a name="dbpropertyexpression"></a>DbPropertyExpression

Spłaszczanie aliasów sprzężenia jest identyfikowane i przetwarzane podczas odwiedzania DbPropertyExpression.

Właściwość instance jest najpierw odwiedzana, a wynikiem jest symbol, JoinSymbol lub SymbolPair. Poniżej przedstawiono sposób obsługi tych trzech przypadków:

- Jeśli zostanie zwrócona wartość JoinSymbol, niż jej Właściwość NameToExtent zawiera symbol dla wymaganej właściwości. Jeśli symbol sprzężenia reprezentuje zagnieżdżoną sprzężenie, Nowa para symboli jest zwracana z symbolem sprzężenia, aby śledzić symbol, który będzie używany jako alias wystąpienia, i symbol reprezentujący rzeczywistą właściwość w celu dodatkowego rozwiązania.

- Jeśli SymbolPair jest zwracany, a część kolumny jest symbolem sprzężenia, zwracany jest symbol sprzężenia, ale teraz Właściwość Column zostanie zaktualizowana tak, aby wskazywała Właściwość reprezentowaną przez bieżące wyrażenie właściwości. W przeciwnym razie element SqlBuilder jest zwracany ze źródłem SymbolPair jako alias i symbol dla bieżącej właściwości jako kolumnę.

- Jeśli symbol jest zwracany, Metoda odwiedzania zwraca metodę SqlBuilder z tym wystąpieniem jako alias oraz nazwę właściwości jako nazwę kolumny.

### <a name="dbnewinstanceexpression"></a>Obiekt DbNewInstanceExpression

Gdy jest używana jako właściwość projekcji elementu DbProjectExpression, obiekt DbNewInstanceExpression tworzy listę oddzielonych przecinkami argumentów do reprezentowania prognozowanych kolumn.

Gdy obiekt DbNewInstanceExpression ma zwracany typ kolekcji i definiuje nową kolekcję wyrażeń dostarczonych jako argumenty, następujące trzy przypadki są obsługiwane osobno:

- Jeśli obiekt DbNewInstanceExpression ma DbElementExpression jako jedyny argument, jest przetłumaczony w następujący sposób:

```sql
NewInstance(Element(X)) =>  SELECT TOP 1 …FROM X
```

Jeśli obiekt DbNewInstanceExpression nie ma argumentów (reprezentuje pustą tabelę), obiekt DbNewInstanceExpression jest przetłumaczony na:

```sql
SELECT CAST(NULL AS <primitiveType>) as X
FROM (SELECT 1) AS Y WHERE 1=0
```

W przeciwnym razie obiekt DbNewInstanceExpression tworzy element Union-All dla argumentów:

```sql
SELECT <visit-result-arg1> as X
UNION ALL SELECT <visit-result-arg2> as X
UNION ALL …
UNION ALL SELECT <visit-result-argN> as X
```

### <a name="dbfunctionexpression"></a>Obiekcie DbFunctionExpression

Funkcje kanoniczne i wbudowane są przetwarzane w taki sam sposób: Jeśli potrzebują specjalnej obsługi (przecinanie (String) do LTRIM (RTRIM (String), na przykład, zostanie wywołana odpowiednia procedura obsługi. W przeciwnym razie są tłumaczone na FunctionName (arg1, arg2,..., argn).

Słowniki są używane do śledzenia, które funkcje potrzebują specjalnej obsługi i odpowiednich programów obsługi.

Funkcje zdefiniowane przez użytkownika są tłumaczone na przestrzeń Nazwname. FunctionName (arg1, arg2,..., argn).

### <a name="dbelementexpression"></a>DbElementExpression

Metoda, która odwiedza DbElementExpression, jest wywoływana tylko do odwiedzania DbElementExpression, gdy jest używana do reprezentowania podzapytania skalarnego. W związku z tym DbElementExpression Wykonuje translację do kompletnego SqlSelectStatement i dodaje do niego nawiasy klamrowe.

### <a name="dbquantifierexpression"></a>DbQuantifierExpression

W zależności od typu wyrażenia (dowolne lub wszystkie) DbQuantifierExpression jest przetłumaczony jako:

```sql
Any(input, x) => Exists(Filter(input,x))
All(input, x) => Not Exists(Filter(input, not(x))
```

### <a name="dbnotexpression"></a>Obiekt DbNotExpression

W niektórych przypadkach można zwinąć tłumaczenie obiekt DbNotExpression z wyrażeniem wejściowym. Na przykład:

```sql
Not(IsNull(a)) =>  "a IS NOT NULL"
Not(All(input, x) => Not (Not Exists(Filter(input, not(x))) => Exists(Filter(input, not(x))
```

Przyczyną jest to, że drugi zwinięty jest wykonywany, ponieważ podczas tłumaczenia DbQuantifierExpression typu all przez dostawcę wprowadzono nieefektywność. W tym celu Entity Framework nie mógł wykonać uproszczenia.

### <a name="dbisemptyexpression"></a>DbIsEmptyExpression

DbIsEmptyExpression jest przetłumaczony jako:

```sql
IsEmpty(input) = Not Exists(input)
```

## <a name="second-phase-of-sql-generation-generating-the-string-command"></a>Druga faza generowania kodu SQL: generowanie ciągu polecenia

Podczas generowania ciągu polecenia SQL, SqlSelectStatement tworzy rzeczywiste aliasy dla symboli, które odnoszą się do błędu zmiany nazwy kolumny i zakresu aliasu.

Zmiana nazwy aliasu zakresu występuje podczas zapisywania obiektu SqlSelectStatement w ciągu. Najpierw utwórz listę wszystkich aliasów używanych przez zakresy zewnętrzne. Każdy symbol w FromExtents (lub AllJoinExtents, jeśli ma wartość inną niż null), otrzymuje nazwę, jeśli koliduje z dowolnym zakresem zewnętrznym. Jeśli zmiana nazwy jest konieczna, nie będzie konfliktu z żadnym z zakresów zebranych w AllExtentNames.

Zmiana nazwy kolumny występuje podczas zapisywania obiektu symbol w ciągu. AddDefaultColumns w pierwszej fazie ustalił, czy nazwa określonego symbolu kolumny jest konieczna. W drugiej fazie tylko zmiana nazwy odbywa się w celu upewnienia się, że nazwa utworzona nie powoduje konfliktu z żadną nazwą używaną w AllColumnNames

Aby utworzyć unikatowe nazwy zarówno dla aliasów zakresu, jak i dla kolumn, użyj \<existing_name > _N, gdzie n jest najmniejszym aliasem, który nie był jeszcze używany. Globalna lista wszystkich aliasów zwiększa potrzebę operacji kaskadowych.

## <a name="see-also"></a>Zobacz także

- [Generowanie kodu SQL w dostawcy próbki](sql-generation-in-the-sample-provider.md)
