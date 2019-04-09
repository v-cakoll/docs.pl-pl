---
title: Architektura i projekt
ms.date: 03/30/2017
ms.assetid: bd738d39-00e2-4bab-b387-90aac1a014bd
ms.openlocfilehash: 42d06fd04ae0459d23961a48ab5ccc0d55695ceb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59096140"
---
# <a name="architecture-and-design"></a>Architektura i projekt
Moduł generowania SQL w [dostawcy próbki](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) jest implementowany jako obiekt odwiedzający na drzewo wyrażenia, który reprezentuje drzewo poleceń. Generowanie odbywa się w jednym przebiegu za pośrednictwem drzewa wyrażeń.  
  
 Węzły drzewa są przetwarzane od dołu w górę. Po pierwsze jest generowany strukturę pośredniego: SqlSelectStatement lub SqlBuilder, zarówno ISqlFragment implementującej. Następnie ciąg instrukcja SQL jest generowany z tej struktury. Istnieją dwa powody, dla struktury pośredniego:  
  
-   Logicznie instrukcję SQL SELECT jest wypełniana poza kolejnością. Węzły, które uczestniczą w klauzuli FROM są odwiedzi przed tymi, które uczestniczą w WHERE, GROUP BY i ORDER BY — klauzula.  
  
-   Aby zmienić nazwę aliasy, należy zidentyfikować aliasy wszystkie używane w celu uniknięcia konfliktów podczas zmiany nazwy. Mają być odroczone możliwości zmiany nazw w SqlBuilder, należy użyć symbolu obiektów do reprezentowania kolumn, które są kandydatami do zmiany nazwy.  
  
 ![Diagram](../../../../../docs/framework/data/adonet/ef/media/de1ca705-4f7c-4d2d-ace5-afefc6d3cefa.gif "de1ca705-4f7c-4d2d-ace5-afefc6d3cefa")  
  
 W pierwszej fazie podczas odwiedzania drzewa wyrażeń wyrażeń są grupowane w SqlSelectStatements sprzężeń są spłaszczone i są spłaszczone aliasy sprzężenia. W trakcie tego przebiegu Symbol obiekty reprezentują kolumn ani aliasy danych wejściowych, które mogą zostać zmienione.  
  
 W drugim etapie, podczas produkcji rzeczywistego ciągu aliasy zostały zmienione.  
  
## <a name="data-structures"></a>Struktury danych  
 W tej sekcji opisano typy używane w [dostawcy próbki](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) umożliwia tworzenie instrukcji SQL.  
  
### <a name="isqlfragment"></a>ISqlFragment  
 W tej sekcji omówiono klasy, które implementują interfejs ISqlFragment, który służy do dwóch celów:  
  
-   Typowe typ zwracany dla wszystkich metod obiektu odwiedzającego.  
  
-   Zapewnia metodę, aby zapisać ciąg końcowy SQL.  
  
```  
internal interface ISqlFragment {  
   void WriteSql(SqlWriter writer, SqlGenerator sqlGenerator);  
}  
```  
  
#### <a name="sqlbuilder"></a>SqlBuilder  
 SqlBuilder jest urządzenie zbieranie, ostatni ciąg SQL, podobnie jak StringBuilder. Składa się z ciągów, które tworzą końcowego program SQL oraz ISqlFragments, które mogą być konwertowane na ciągi.  
  
```  
internal sealed class SqlBuilder : ISqlFragment {  
   public void Append(object s)  
   public void AppendLine()  
   public bool IsEmpty  
}  
```  
  
#### <a name="sqlselectstatement"></a>SqlSelectStatement  
 SqlSelectStatement reprezentuje canonical instrukcję SQL SELECT kształtu "Wybierz... OD... WHERE... GRUPUJ WEDŁUG... ORDER BY".  
  
 Każdy z klauzul SQL jest reprezentowany przez StringBuilder. Ponadto śledzi, czy określono Distinct oraz czy instrukcja jest najwyższego poziomu. Jeśli instrukcja jest najwyższego poziomu, w klauzuli ORDER BY jest pomijana, chyba, że instrukcja ma również klauzuli TOP.  
  
 FromExtents zawiera listę danych wejściowych dla instrukcji SELECT. W tym zazwyczaj jest tylko jeden element. Instrukcji "SELECT" dla sprzężeń tymczasowo może mieć więcej niż jeden element.  
  
 Jeśli instrukcja SELECT jest tworzony przez węzeł sprzężenia, SqlSelectStatement utrzymuje listę wszystkie zakresy, które zostały spłaszczone sprzężenia w AllJoinExtents. OuterExtents reprezentuje zewnętrzne odwołań SqlSelectStatement i służy do zmiany nazwy alias danych wejściowych.  
  
```  
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
 TopClause reprezentuje wyrażenia TOP w SqlSelectStatement. Właściwość TopCount wskazuje, ile PIERWSZYCH wierszy powinna być wybrana.  Gdy WithTies ma wartość true, TopClause została opracowana od DbLimitExpession.  
  
```  
class TopClause : ISqlFragment {  
   internal bool WithTies {get}  
   internal ISqlFragment TopCount {get}  
   internal TopClause(ISqlFragment topCount, bool withTies)  
   internal TopClause(int topCount, bool withTies)  
}  
```  
  
### <a name="symbols"></a>Symbole  
 Klasy związane z platformą symboli i tabeli symboli należy wykonać, zmiana nazwy alias danych wejściowych, spłaszczanie alias sprzężenia i zmiana nazwy aliasu kolumny.  
  
 Klasa Symbol reprezentuje zakres, zagnieżdżonych instrukcji SELECT lub kolumny. Jest używana zamiast rzeczywistego alias umożliwia zmianę, gdy został on użyty i są dodatkowe informacje dotyczące artefaktów, które reprezentuje (takich jak typ).  
  
```  
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
  
 Nazwa przechowuje oryginalnego alias reprezentowana zakresu lub kolumna zagnieżdżonej instrukcji SELECT.  
  
 Nowa nazwa przechowuje alias, który będzie używany w instrukcji SQL SELECT. Jest początkowo ustawiona na nazwę i nazwę zmienić tylko w razie potrzeby podczas generowania zapytania ciąg końcowy.  
  
 Typ jest przydatna dla symboli reprezentujących zakresów i zagnieżdżonych instrukcji "SELECT".  
  
#### <a name="symbolpair"></a>SymbolPair  
 Klasa SymbolPair adresów spłaszczanie rekordów.  
  
 Należy wziąć pod uwagę wyrażenie właściwości D (v, "j3.j2.j1.a.x"), gdzie v jest VarRef j1, j2, j3 sprzężenia, jest zakres, a x kolumn.  
  
 Musi to być przetłumaczyć po pewnym czasie {"j" "}. {x'}. Pole źródłowe reprezentuje SqlStatement najbardziej zewnętrznej, reprezentujący wyrażeniu join (np. j2); zawsze jest symbolem sprzężenia. Pole kolumny przenosi się z jeden symbol sprzężenia do następnej do czasu zatrzymuje się na symbol innego niż sprzężenia. To jest zwracana, gdy użytkownik odwiedzi DbPropertyExpression, ale nigdy nie jest dodawane do SqlBuilder.  
  
```  
class SymbolPair : ISqlFragment {  
   public Symbol Source;  
   public Symbol Column;  
   public SymbolPair(Symbol source, Symbol column)  
}  
```  
  
#### <a name="joinsymbol"></a>JoinSymbol  
 Symbol sprzężenia jest Symbol, który reprezentuje zagnieżdżonych instrukcji SELECT z sprzężenia lub sprzężenia danych wejściowych.  
  
```  
internal sealed class JoinSymbol : Symbol {  
   internal List<Symbol> ColumnList {get, set}  
   internal List<Symbol> ExtentList {get}  
   internal List<Symbol> FlattenedExtentList {get, set}  
   internal Dictionary<string, Symbol> NameToExtent {get}  
   internal bool IsNestedJoin {get, set}  
  
   public JoinSymbol(string name, TypeUsage type, List<Symbol> extents)  
}  
```  
  
 ColumnList reprezentuje listę kolumn w klauzuli SELECT, jeśli ten symbol reprezentuje instrukcję SQL SELECT. ExtentList znajduje się lista zakresów w klauzuli SELECT. W przypadku sprzężenia ma wiele zakresów spłaszczone na najwyższym poziomie, FlattenedExtentList śledzi zakresy, aby zapewnić tym zakresie, którego aliasy zostały zmienione poprawnie.  
  
 NameToExtent ma wszystkie zakresy w ExtentList w formie słownika. IsNestedJoin jest używany do określenia, czy JoinSymbol jest symbol sprzężenia zwykłej lub taki, który ma odpowiedni SqlSelectStatement.  
  
 Wszystkie listy są ustawiane w dokładnie jeden raz i następnie używany na potrzeby wyszukiwania lub wyliczenia.  
  
#### <a name="symboltable"></a>SymbolTable  
 SymbolTable jest używany do rozpoznawania nazwy zmiennych do symboli. SymbolTable jest implementowany jako stosu z nowy wpis dla każdego zakresu. Wyszukiwań wyszukiwania w górnej części stosu w dół aż do znalezienia wpis.  
  
```  
internal sealed class SymbolTable {  
   internal void EnterScope()  
   internal void ExitScope()  
   internal void Add(string name, Symbol value)  
   internal Symbol Lookup(string name)  
}  
```  
  
 Istnieje tylko jeden SymbolTable na jedno wystąpienie modułu generowanie kodu Sql. Wprowadzone zakresy i zakończył się dla każdego węzła relacyjnych. Wszystkie symbole w starszych zakresy są widoczne zakresy nowsze chyba że ukryte przez inne symbole o takiej samej nazwie.  
  
### <a name="global-state-for-the-visitor"></a>Stan globalny dla obiektu odwiedzającego  
 Aby ułatwić zmiana nazwy kolumny i aliasy, utrzymywać listę wszystkich nazw kolumn (AllColumnNames) i aliasy zakresu (AllExtentNames), które zostały użyte w pierwszym przekazywany przez drzewo zapytań.  Tabela symboli jest rozpoznawany jako nazwy zmiennych symboli. IsVarRefSingle służy wyłącznie do celów weryfikacji nie jest bezwzględnie konieczne.  
  
 Dwóch stosów używane za pośrednictwem CurrentSelectStatement i IsParentAJoin są używane do przekazania "parameters" z elementu nadrzędnego do węzłów podrzędnych, ponieważ wzorzec gości nie zezwalają na przekazywanie parametrów.  
  
```  
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
  
### <a name="grouping-expression-nodes-into-sql-statements"></a>Grupowanie węzłów wyrażenie w instrukcji SQL  
 SqlSelectStatement jest tworzony po napotkaniu pierwszego węzła relacyjnych (zazwyczaj w zakresie DbScanExpression) podczas odwiedzania drzewa od dołu w górę. Do tworzenia instrukcji SQL SELECT z few zagnieżdżonych zapytań, jak to możliwe, agregacji jako wiele z jego węzłów nadrzędnych, jak to możliwe, w tym SqlSelectStatement.  
  
 Decyzję, czy podany węzeł (relacyjnych) można dodać do bieżącej SqlSelectStatement (jedna zwrócone podczas przeglądania danych wejściowych) lub nowego raportu musi być uruchomiona jest obliczana przez metodę IsCompatible, a także od tego, co znajduje się już w SqlSelectStatement, która zależy od węzły zostały poniżej danego węzła.  
  
 Zazwyczaj klauzule instrukcji SQL są oceniane po klauzulach, gdzie węzły są traktowane jako scalania nie są puste, nie można dodać do bieżącej instrukcji węzła. Na przykład jeśli kolejnego węzła jest filtrem, tego węzła można zintegrować bieżącego SqlSelectStatement tylko wtedy, gdy są spełnione następujące warunki:  
  
-   Wybierz pozycję Lista jest pusta. Jeśli lista wyboru nie jest pusty, listy wyboru został wyprodukowany przez węzła poprzedzającej filtr i predykatu może odwoływać się do kolumny zwracane przez tej listy wyboru.  
  
-   GROUPBY jest pusty. Jeśli GRUPOWANIA nie jest pusty, dodając filtr będzie oznaczać filtrowanie przed grupowania, który nie jest prawidłowy.  
  
-   Klauzula TOP jest pusty. Jeśli klauzuli TOP nie jest pusty, dodając filtr będzie oznaczać filtrowanie przed wykonaniem GÓRNEJ, który nie jest prawidłowy.  
  
 To nie ma zastosowania do węzłów nierelacyjnych, takich jak DbConstantExpression lub wyrażeniach arytmetycznych ponieważ te są zawsze dołączane jako część istniejącej SqlSelectStatement.  
  
 Ponadto gdy wystąpią drzewa sprzężenia (sprzężenia węzeł, który nie ma elementu nadrzędnego join), nowe SqlSelectStatement został uruchomiony. Wszystkie jego elementy podrzędne sprzężenia grzbietu po lewej stronie są agregowane w tym SqlSelectStatement.  
  
 Zawsze, gdy nowy SqlSelectStatement została uruchomiona, a bieżąca jest dodawany do danych wejściowych, bieżący SqlSelectStatement może być konieczne można wykonać przez dodanie kolumny projekcji (klauzuli SELECT), jeśli nie istnieje. Można to zrobić za pomocą metody AddDefaultColumns, który patrzy na FromExtents z SqlSelectStatement i dodaje wszystkie kolumny, która listę zakresów, reprezentowane przez FromExtents łączy w zakresie do listy kolumn przewidywany. Jest to wykonywane, ponieważ w tym momencie jest nieznany kolumny, które są przywoływane przez inne węzły. To może być zoptymalizowana pod kątem projektu kolumny, które mogą być później użyte.  
  
### <a name="join-flattening"></a>Dołącz do spłaszczania  
 Właściwość IsParentAJoin pomaga ustalić, czy dany sprzężenia mogą spłaszczenia. W szczególności zwraca IsParentAJoin `true` tylko w przypadku podrzędnych po lewej stronie, sprzężenia i dla każdego DbScanExpression, który jest bezpośrednim danych wejściowych w celu sprzężenia, w którym to przypadku ten węzeł podrzędny ponownie używa tego samego SqlSelectStatement, używanego przez nadrzędne będzie później. Aby uzyskać więcej informacji zobacz "Dołącz do wyrażenia".  
  
### <a name="input-alias-redirecting"></a>Wprowadź Alias przekierowania folderu  
 Alias wejściowy przekierowywanie odbywa się z tabelą symboli.  
  
 Aby wyjaśnić, przekierowywanie alias danych wejściowych, należy zapoznać się z pierwszego przykładu w [generowania SQL z drzew poleceń — najlepsze rozwiązania](../../../../../docs/framework/data/adonet/ef/generating-sql-from-command-trees-best-practices.md).  Brak "" konieczne nastąpi przekierowanie do "b" w projekcji.  
  
 Po utworzeniu obiektu SqlSelectStatement zakres, który stanowi dane wejściowe do węzła jest umieścić we właściwości From SqlSelectStatement. Symbol (< symbol_b >) jest tworzony na podstawie nazwy powiązania danych wejściowych ("b") do reprezentowania w tym zakresie i "AS" + < symbol_b > jest dołączany do klauzuli From.  Symbol jest także dodawane do właściwości FromExtents.  
  
 Symbol jest także dodawane do tabeli symboli do połączenia nazwa powiązania danych wejściowych ("b", < symbol_b >).  
  
 Jeśli kolejne węzła ponownie używa tego SqlSelectStatement, wpisy są dodawane do tabeli symboli do łączenia nazwy powiązania danych wejściowych do tego symbolu. W naszym przykładzie DbProjectExpression o nazwie powiązania danych wejściowych, znaku "a" spowoduje ponowne użycie SqlSelectStatement i Dodaj ("" \< symbol_b >) do tabeli.  
  
 Gdy wyrażeń odwoływać się do nazwy powiązania danych wejściowych węzła, który jest ponowne SqlSelectStatement, nie zostanie rozwiązany, przy użyciu tabeli symboli na poprawne symbol przekierowanego tego odwołania. Gdy "" z "a.x""" zostanie rozwiązany podczas odwiedzania reprezentujący DbVariableReferenceExpression "" it rozwiąże symbol < symbol_b >.  
  
### <a name="join-alias-flattening"></a>Dołącz do spłaszczanie aliasu  
 Spłaszczanie alias sprzężenia jest osiągana, gdy odwiedzający DbPropertyExpression zgodnie z opisem w sekcji zatytułowanej DbPropertyExpression.  
  
### <a name="column-name-and-extent-alias-renaming"></a>Nazwa kolumny i zakresu, Alias zmiana nazwy  
 Ten problem, nazwa kolumny i zmiana nazwy aliasu w zakresie jest skierowana przy użyciu symboli, które tylko pobieranie zastępowane z aliasami w drugim etapie generowania opisane w sekcji drugiej fazy generowanie kodu SQL: Generowanie ciągu polecenia.  
  
## <a name="first-phase-of-the-sql-generation-visiting-the-expression-tree"></a>Pierwsza faza generowanie kodu SQL: Odwiedzający drzewa wyrażeń  
 W tej sekcji opisano pierwszą fazę generowanie kodu SQL, gdy reprezentujący wyrażenie, które odwiedzeniu zapytania i pośredniego struktury jest generowany, albo SqlSelectStatement lub SqlBuilder.  
  
 W tej sekcji opisano zasad zaproszonych innego wyrażenia węzeł kategorii i szczegółowe informacje o odwiedzenie typy określonego wyrażenia.  
  
### <a name="relational-non-join-nodes"></a>Relacyjne węzłów (bez połączenie)  
 Następujące typy wyrażeń obsługują bez łączenia węzłów:  
  
-   DbDistinctExpression  
  
-   DbFilterExpression  
  
-   DbGroupByExpression  
  
-   DbLimitExpession  
  
-   DbProjectExpression  
  
-   DbSkipExpression  
  
-   DbSortExpression  
  
 Odwiedzenie tych węzłów jest zgodny ze wzorcem następujące:  
  
1.  Odwiedź stronę relacyjnych danych wejściowych i pobieranie wynikowy SqlSelectStatement. Dane wejściowe do relacyjnych węzła może być jedną z następujących czynności:  
  
    -   Relacyjne węzła, w tym zakresie (przykład DbScanExpression). Odwiedzający takim węzłem zwraca SqlSelectStatement.  
  
    -   Operacja wyrażenie (UNION ALL, na przykład). Wynik zawiera opakowane w nawiasach kwadratowych i umieścić w klauzuli FROM SqlSelectStatement nowe.  
  
2.  Sprawdź, czy bieżący węzeł może być dodany do SqlSelectStatement produkowane przez danych wejściowych. Sekcji wyrażenia grupowania na instrukcje w tym artykule opisano to. W przeciwnym razie  
  
    -   POP bieżący obiekt SqlSelectStatement.  
  
    -   Utwórz nowy obiekt SqlSelectStatement i Dodaj popped SqlSelectStatement jako FROM nowego obiektu SqlSelectStatement.  
  
    -   Umieścić nowy obiekt na górze stosu.  
  
3.  Przekierowanie powiązania wyrażenia wejściowego do poprawne symboli z danych wejściowych. Te informacje są przechowywane w obiekcie SqlSelectStatement.  
  
4.  Dodaj nowy zakres SymbolTable.  
  
5.  Odwiedź stronę bez wprowadzania część wyrażenia (na przykład, rzutowania i predykatu).  
  
6.  Wyświetl wszystkie obiekty, które są dodawane do globalnego stosów.  
  
 DbSkipExpression ma bezpośredni odpowiednik w języku SQL. Logicznie jest tłumaczony na:  
  
```  
SELECT Y.x1, Y.x2, ..., Y.xn  
FROM (  
   SELECT X.x1, X.x2, ..., X.xn, row_number() OVER (ORDER BY sk1, sk2, ...) AS [row_number]   
   FROM input as X   
   ) as Y  
WHERE Y.[row_number] > count   
ORDER BY sk1, sk2, ...  
```  
  
### <a name="join-expressions"></a>Dołącz do wyrażeń  
 Poniżej są traktowane jako wyrażeniach sprzężenia, a następnie są przetwarzane przez metodę VisitJoinExpression w typowy sposób:  
  
-   DbApplyExpression  
  
-   DbJoinExpression  
  
-   DbCrossJoinExpression  
  
 Poniżej przedstawiono kroki odwiedź stronę:  
  
 Najpierw przed odwiedzający elementy podrzędne, IsParentAJoin jest wywoływana, aby sprawdzić, czy węzeł sprzężenia jest elementem podrzędnym sprzężenia wzdłuż lewej grzbietu. Jeśli zostanie zwrócona wartość false, nowe SqlSelectStatement został uruchomiony. W tym sensie sprzężeń są odwiedzone inaczej z pozostałych węzłów, ponieważ element nadrzędny (węzeł join) tworzy SqlSelectStatement dla dzieci w miarę możliwości używać.  
  
 Po drugie przetwarzać dane wejściowe co jednocześnie. Dla każdego dane wejściowe:  
  
1.  Można znaleźć w danych wejściowych.  
  
2.  Proces wpis wynik odwiedzający danych wejściowych, wywołując ProcessJoinInputResult, który jest odpowiedzialny za prowadzenie tabeli symboli po odwiedzający element podrzędny w wyrażeniu join i prawdopodobnie zakończeniem SqlSelectStatement produkowane przez dziecko. Wynik elementu podrzędnego, może być jedną z następujących czynności:  
  
    -   SqlSelectStatement niż ten, do którego zostanie dodany element nadrzędny. W takim przypadku może musi on zostać wykonane przez dodanie kolumn domyślnych. Jeśli dane wejściowe sprzężenia, musisz utworzyć nowy symbol sprzężenia. W przeciwnym razie Utwórz symbol normalny.  
  
    -   Zakres (DbScanExpression, na przykład), w którego przypadku, gdy po prostu zostanie dodany do listy danych wejściowych elementu nadrzędnego użytkownika SqlSelectStatement.  
  
    -   Nie SqlSelectStatement, w których przypadku, gdy jest jest ujęte w nawiasy kwadratowe.  
  
    -   Tym samym SqlSelectStatement, do którego zostanie dodany element nadrzędny. W takim przypadku symboli na liście FromExtents konieczne można zastąpić za pomocą pojedynczego JoinSymbol nowe reprezentujący je wszystkie.  
  
    -   W pierwszych trzech przypadkach AddFromSymbol jest wywoływana, aby dodać klauzulę AS i aktualizowanie tabeli symboli.  
  
 Po trzecie warunek sprzężenia (jeśli istnieje) jest odwiedzany.  
  
### <a name="set-operations"></a>Operacje na zestawie  
 Operacje na zestawie DbUnionAllExpression, wyrażenia DbExceptExpression i DbIntersectExpression są przetwarzane przez metodę VisitSetOpExpression. Tworzy SqlBuilder kształtu  
  
```xml  
<leftSqlSelectStatement> <setOp> <rightSqlSelectStatement>  
```  
  
 Gdzie \<leftSqlSelectStatement > i \<rightSqlSelectStatement > są SqlSelectStatements uzyskać, odwiedzając poszczególne z wprowadzonymi danymi, a \<setOp > jest odpowiednia operacja (UNION ALL w przykładzie).  
  
### <a name="dbscanexpression"></a>DbScanExpression  
 Jeśli w kontekście dołączania (jako dane wejściowe do sprzężenia, na które jest elementem podrzędnym lewego sprzężenia innego), DbScanExpression zwraca SqlBuilder z elementem docelowym SQL dla odpowiedniego obiektu docelowego, czyli Definiowanie zapytań, tabeli lub widoku. W przeciwnym razie nowy SqlSelectStatement jest tworzony za pomocą pola FROM równa odnoszą się do odpowiedniego obiektu docelowego.  
  
### <a name="dbvariablereferenceexpression"></a>DbVariableReferenceExpression  
 Odwiedziny DbVariableReferenceExpression zwraca Symbol odpowiadający to wyrażenie odwołanie do zmiennej, w oparciu o wyszukiwania w tabeli symboli.  
  
### <a name="dbpropertyexpression"></a>DbPropertyExpression  
 Spłaszczanie alias sprzężenia jest zidentyfikowany i przetwarzane, gdy użytkownik odwiedzi DbPropertyExpression.  
  
 Najpierw odwiedzeniu Właściwość wystąpienia, a wynik jest Symbol, JoinSymbol lub SymbolPair. Poniżej przedstawiono sposób obsługi tych trzech przypadkach:  
  
-   Jeśli zwracana jest JoinSymbol, niż jego NameToExtent właściwość zawiera symbol dla wymaganych właściwości. Jeśli symbol sprzężenia reprezentuje zagnieżdżonego sprzężenia, nową parę Symbol jest zwracany za pomocą symbolu sprzężenia do śledzenia symbol, który będzie służyć jako alias wystąpienia i symbol reprezentujące właściwość dalsze rozwiązywanie.  
  
-   Jeśli część kolumny to symbol sprzężenia SymbolPair jest zwracany, zwracany jest ponownie symbol sprzężenia, ale teraz jako wartość właściwości column zostanie zaktualizowany w celu wskaż właściwość reprezentowana przez wyrażenie właściwości bieżącego. W przeciwnym razie SqlBuilder jest zwracany ze źródłem SymbolPair jako alias i symboli dla bieżącej właściwości jako kolumnę.  
  
-   Jeśli Symbol jest zwracana, metoda odwiedziny zwraca metoda SqlBuilder z tego wystąpienia jako alias i nazwę właściwości jako nazwa kolumny.  
  
### <a name="dbnewinstanceexpression"></a>DbNewInstanceExpression  
 Gdy jest używana jako właściwość projekcji DbProjectExpression, obiekt DbNewInstanceExpression tworzy przecinkami lista argumentów do reprezentowania przewidywany kolumn.  
  
 Gdy obiekt DbNewInstanceExpression ma typ zwracany kolekcji definiuje nową kolekcję wyrażeń dostarczone jako argumenty, są obsługiwane osobno trzech następujących przypadkach:  
  
-   Jeśli obiekt DbNewInstanceExpression DbElementExpression jako jedynego argumentu, jest tłumaczony w następujący sposób:  
  
    ```  
    NewInstance(Element(X)) =>  SELECT TOP 1 …FROM X  
    ```  
  
 Jeśli obiekt DbNewInstanceExpression nie ma argumentów (reprezentuje pustą tabelę), obiekt DbNewInstanceExpression są tłumaczone na:  
  
```  
SELECT CAST(NULL AS <primitiveType>) as X  
FROM (SELECT 1) AS Y WHERE 1=0  
```  
  
 W przeciwnym razie obiekt DbNewInstanceExpression kompilacje drabiny union all, argumenty:  
  
```  
SELECT <visit-result-arg1> as X  
UNION ALL SELECT <visit-result-arg2> as X  
UNION ALL …  
UNION ALL SELECT <visit-result-argN> as X  
```  
  
### <a name="dbfunctionexpression"></a>DbFunctionExpression  
 Canonical i wbudowane funkcje są przetwarzane tak samo: jeśli wymagają specjalnej obsługi (TRIM(string) do LTRIM(RTRIM(string), na przykład), odpowiedni program obsługi zostanie wywołana. W przeciwnym razie są tłumaczone na FunctionName (arg1, arg2,..., argn).  
  
 Słowniki są używane do śledzenia funkcji, które potrzebują specjalnej obsługi i ich odpowiednie programy obsługi.  
  
 Funkcje zdefiniowane przez użytkownika są tanslated do NamespaceName.FunctionName (arg1, arg2,..., argn).  
  
### <a name="dbelementexpression"></a>DbElementExpression  
 Metody, które odwiedza DbElementExpression jest wywoływana tylko do odwiedzania DbElementExpression, gdy jest używana do reprezentowania skalarne podzapytania. Dlatego DbElementExpression przekłada się na zakończenie SqlSelectStatement i dodaje je w nawiasach.  
  
### <a name="dbquantifierexpression"></a>DbQuantifierExpression  
 W zależności od typu wyrażenia (dowolne lub wszystkie) jest tłumaczony DbQuantifierExpression go jako:  
  
```  
Any(input, x) => Exists(Filter(input,x))  
All(input, x) => Not Exists(Filter(input, not(x))  
```  
  
### <a name="dbnotexpression"></a>DbNotExpression  
 W niektórych przypadkach istnieje możliwość Zwiń tłumaczenia obiekt DbNotExpression z jej wyrażenia wejściowego. Na przykład:  
  
```  
Not(IsNull(a)) =>  "a IS NOT NULL"  
Not(All(input, x) => Not (Not Exists(Filter(input, not(x))) => Exists(Filter(input, not(x))  
```  
  
 Powodów, dla którego jest wykonywane w drugim zwijanie jest, ponieważ nieefektywności zostały wprowadzone przez dostawcę podczas tłumaczenia DbQuantifierExpression z wpisz wszystkie. Ten sposób programu Entity Framework nie może mieć wykonana uproszczenia.  
  
### <a name="dbisemptyexpression"></a>DbIsEmptyExpression  
 DbIsEmptyExpression jest tłumaczony jako:  
  
```  
IsEmpty(inut) = Not Exists(input)  
```  
  
## <a name="second-phase-of-sql-generation-generating-the-string-command"></a>Drugi etap generowanie kodu SQL: Generowanie ciągu polecenia  
 Podczas generowania ciąg polecenia SQL, SqlSelectStatement tworzy rzeczywistych aliasów dla symboli, który dotyczy ten problem, nazwa kolumny i zmiana nazwy aliasu w zakresie.  
  
 Zmiana nazwy aliasu w zakresie występuje podczas zapisywania obiektu SqlSelectStatement na ciąg. Najpierw utwórz listę wszystkie aliasy, które są używane przez zewnętrzne zakresów. Każdy symbol w FromExtents (lub AllJoinExtents, jeśli jest inna niż null), pobiera zmieniona, jeśli powoduje ona konflikt z żadnym z zakresów zewnętrznych. Jeśli potrzebna jest zmiana nazwy, nie spowoduje ona konflikt z żadnym z zakresów, zbierane w AllExtentNames.  
  
 Zmiana nazwy kolumny występuje podczas zapisywania Symbol — obiekt na ciąg. AddDefaultColumns w pierwszej fazie stwierdził, jeśli symbol kolumny musi ulec zmianie. W drugim etapie występuje tylko zmiany nazwy, upewniając się, czy nazwa produkowane nie powoduje konfliktu z dowolną nazwę używaną w AllColumnNames  
  
 Aby tworzyć unikatowe nazwy dla zakresu aliasów i kolumn, należy użyć _n < existing_name >, gdzie n to najmniejsza alias, który nie został jeszcze użyty. Globalną listę wszystkie aliasy podkreśla konieczność kaskadowych zmienia nazwę.  
  
## <a name="see-also"></a>Zobacz także

- [Generowanie kodu SQL w dostawcy próbki](../../../../../docs/framework/data/adonet/ef/sql-generation-in-the-sample-provider.md)
