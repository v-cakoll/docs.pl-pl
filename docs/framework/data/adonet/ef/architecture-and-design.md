---
title: Architektury i projektu
ms.date: 03/30/2017
ms.assetid: bd738d39-00e2-4bab-b387-90aac1a014bd
ms.openlocfilehash: c2e8ff5f21a2941d75b21915552e6935a1423978
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="architecture-and-design"></a>Architektury i projektu
W module generowania SQL w [dostawcy próbki](http://go.microsoft.com/fwlink/?LinkId=180616) jest zaimplementowany jako obiekt odwiedzający na drzewo wyrażenia, który reprezentuje drzewo poleceń. Generowanie odbywa się w jednym przebiegu za pośrednictwem drzewa wyrażenia.  
  
 Węzły drzewa są przetwarzane od dołu w górę. Najpierw jest tworzony pośredni struktury: SqlSelectStatement lub SqlBuilder, zarówno ISqlFragment implementującej. Następnie ciąg instrukcja SQL jest tworzony z tej struktury. Istnieją pośredniego struktury z dwóch powodów:  
  
-   Logicznie instrukcję SQL SELECT jest wypełniana poza kolejnością. Węzły, które uczestniczą w klauzuli FROM są odwiedzana węzłów, które uczestniczą w klauzuli WHERE, GROUP BY i klauzuli ORDER BY.  
  
-   Aby zmienić nazwę aliasy, należy określić używane wszystkie aliasy, aby uniknąć kolizji podczas zmiany nazwy. Odroczenia możliwości zmiany nazwy w SqlBuilder, należy użyć obiektów Symbol do reprezentowania kolumny, które są kandydatów do zmiany nazwy.  
  
 ![Diagram](../../../../../docs/framework/data/adonet/ef/media/de1ca705-4f7c-4d2d-ace5-afefc6d3cefa.gif "de1ca705-4f7c-4d2d-ace5-afefc6d3cefa")  
  
 W pierwszej fazie podczas odwiedzania drzewa wyrażenia wyrażenia są zgrupowane w SqlSelectStatements sprzężeń są spłaszczane i są spłaszczane aliasy sprzężenia. W trakcie tego przebiegu Symbol reprezentować kolumn ani aliasy wejściowych, które mogą zostać zmienione.  
  
 W drugim etapie podczas produkowania rzeczywisty ciąg aliasy zostały zmienione.  
  
## <a name="data-structures"></a>Struktury danych  
 W tej sekcji omówiono typów używanych w [dostawcy próbki](http://go.microsoft.com/fwlink/?LinkId=180616) umożliwia tworzenie instrukcji SQL.  
  
### <a name="isqlfragment"></a>ISqlFragment  
 W tej sekcji opisano klasy, które implementują interfejs ISqlFragment, który służy do dwóch celów:  
  
-   Typowe typ zwracany dla wszystkich metod obiekt odwiedzający.  
  
-   Zapewnia metody do zapisania ostatni ciąg SQL.  
  
```  
internal interface ISqlFragment {  
   void WriteSql(SqlWriter writer, SqlGenerator sqlGenerator);  
}  
```  
  
#### <a name="sqlbuilder"></a>SqlBuilder  
 SqlBuilder to urządzenie zbierania końcowego ciągu SQL, podobnie jak StringBuilder. Składa się z ciągów, które tworzą końcowego SQL, wraz z ISqlFragments, które mogą być konwertowane na ciągi.  
  
```  
internal sealed class SqlBuilder : ISqlFragment {  
   public void Append(object s)  
   public void AppendLine()  
   public bool IsEmpty  
}  
```  
  
#### <a name="sqlselectstatement"></a>SqlSelectStatement  
 SqlSelectStatement reprezentuje canonical instrukcję SQL SELECT kształtu "Wybierz... Z... GDZIE... GRUPUJ WEDŁUG... ORDER BY".  
  
 Każdy klauzul SQL jest reprezentowany przez StringBuilder. Ponadto śledzi, czy określono Distinct oraz czy instrukcja jest najwyższego poziomu. Jeśli instrukcja nie jest najwyższego poziomu, w klauzuli ORDER BY zostanie pominięty, chyba że instrukcja ma również klauzuli TOP.  
  
 FromExtents zawiera listę danych wejściowych dla instrukcji SELECT. W tym zazwyczaj jest tylko jeden element. Instrukcji "SELECT" dla sprzężeń tymczasowo może mieć więcej niż jeden element.  
  
 Jeśli instrukcja SELECT jest tworzony przez węzeł sprzężenia, SqlSelectStatement przechowuje listę wszystkie zakresy, które zostały spłaszczone sprzężenia w AllJoinExtents. OuterExtents reprezentuje zewnętrznych odwołań SqlSelectStatement i służy do zmiany nazwy alias wejściowy.  
  
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
 TopClause reprezentuje wyrażenia TOP w SqlSelectStatement. Właściwość TopCount wskazuje, ile GÓRNYCH wierszy powinna być zaznaczona.  Jeśli WithTies ma wartość true, TopClause został skompilowany z DbLimitExpession.  
  
```  
class TopClause : ISqlFragment {  
   internal bool WithTies {get}  
   internal ISqlFragment TopCount {get}  
   internal TopClause(ISqlFragment topCount, bool withTies)  
   internal TopClause(int topCount, bool withTies)  
}  
```  
  
### <a name="symbols"></a>Symbole  
 Klasy związane z symboli i tabeli symboli wykonać alias wejściowy zmiana nazwy, spłaszczanie alias sprzężenia i zmiana nazwy aliasu kolumny.  
  
 Klasa Symbol reprezentuje stopniu, zagnieżdżonych instrukcji SELECT lub kolumny. Aby umożliwić zmianę po został użyty, a także zawiera dodatkowe informacje dotyczące artefaktu, który reprezentuje (na przykład typ) służy zamiast rzeczywistej alias.  
  
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
  
 Nazwa przechowuje oryginalny alias reprezentowanego zakresu, zagnieżdżonych instrukcji SELECT lub kolumny.  
  
 NewName przechowuje alias, który będzie używany w instrukcji SQL SELECT. Jest początkowo ustawiona nazwa i nazwę zmienić tylko w razie potrzeby podczas generowania ostatni ciąg zapytania.  
  
 Typ jest przydatna dla symboli reprezentujący zakresy i zagnieżdżonych instrukcji "SELECT".  
  
#### <a name="symbolpair"></a>SymbolPair  
 Klasa SymbolPair adresów spłaszczanie rekordów.  
  
 Należy wziąć pod uwagę wyrażenia właściwości D (v, "j3.j2.j1.a.x"), gdzie v jest VarRef, j1, j2, j3 są sprzężenia, ma zakres, a x kolumn.  
  
 Musi to być przetłumaczyć po pewnym czasie {j "}. {x "}. Pole źródła reprezentuje SqlStatement peryferyjnych, reprezentujący wyrażeniu join (Powiedz j2); jest to zawsze symbol sprzężenia. Pole kolumny są przenoszone z jednego symbolu sprzężenia do następnego dopóki zatrzymuje się na symbolu bez sprzężeń. To jest zwracany, gdy użytkownik odwiedzi DbPropertyExpression, ale nigdy nie jest dodawane do SqlBuilder.  
  
```  
class SymbolPair : ISqlFragment {  
   public Symbol Source;  
   public Symbol Column;  
   public SymbolPair(Symbol source, Symbol column)  
}  
```  
  
#### <a name="joinsymbol"></a>JoinSymbol  
 Symbol sprzężenia to Symbol, który reprezentuje zagnieżdżonych instrukcji SELECT z sprzężenia lub sprzężenia danych wejściowych.  
  
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
  
 ColumnList reprezentuje na liście kolumn w klauzuli SELECT, jeśli ta ikona reprezentuje instrukcję SQL SELECT. ExtentList znajduje się lista zakresów w klauzuli SELECT. Jeśli sprzężenie ma wiele zakresów spłaszczone na najwyższym poziomie, FlattenedExtentList śledzi zakresy, aby upewnić się, że zakresie aliasy zostały prawidłowo zmienione.  
  
 NameToExtent ma wszystkie zakresy w ExtentList w formie słownika. IsNestedJoin służy do ustalenia, czy JoinSymbol jest symbol zwykłej sprzężenia, lub takie, które ma odpowiednie SqlSelectStatement.  
  
 Wszystkie listy są ustawić tylko raz i następnie używane do wyszukiwania lub wyliczenia.  
  
#### <a name="symboltable"></a>SymbolTable  
 SymbolTable jest używany do rozpoznawania nazwy zmiennych do symboli. SymbolTable jest implementowany jako stosu z nowy wpis dla każdego zakresu. Z góry stosu w dół wyszukiwanie wyszukiwań, aż do znalezienia wpis.  
  
```  
internal sealed class SymbolTable {  
   internal void EnterScope()  
   internal void ExitScope()  
   internal void Add(string name, Symbol value)  
   internal Symbol Lookup(string name)  
}  
```  
  
 Istnieje tylko jeden SymbolTable na jedno wystąpienie modułu generowanie kodu Sql. Wprowadzone zakresy i zakończył działanie dla każdego węzła relacyjne. Wszystkie symbole w zakresach wcześniejszych są widoczne w do nowszej zakresów, chyba że ukryty przez inne symbole o takiej samej nazwie.  
  
### <a name="global-state-for-the-visitor"></a>Stan globalny dla obiektu odwiedzającego  
 Aby pomóc w zmienianie nazw aliasów i kolumn, utrzymywać listę wszystkich nazw kolumn (AllColumnNames) i aliasy zakresu (AllExtentNames), które zostały już użyte w pierwszym przekazywane za pośrednictwem drzewa zapytania.  Tabela symbol rozpoznawany jako nazwy zmiennych symboli. IsVarRefSingle jest używana tylko na potrzeby weryfikacji nie jest bezwzględnie konieczne.  
  
 Stosy dwóch używane za pośrednictwem CurrentSelectStatement i IsParentAJoin są używane do przekazania "Parametry" z elementu nadrzędnego do węzłów podrzędnych, ponieważ wzorzec odwiedzający nie zezwalają na przekazywanie parametrów.  
  
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
 SqlSelectStatement jest tworzony po napotkaniu pierwszego węzła relacyjnych (zwykle w zakresie DbScanExpression) podczas odwiedzania drzewa od dołu w górę. Do tworzenia instrukcji SQL SELECT z jako kilku zagnieżdżone zapytania, jak to możliwe, łączny jako wiele z jego węzłów nadrzędnych, jak to możliwe, w tym SqlSelectStatement.  
  
 Decyzji, czy podany węzeł (relacyjne) można dodać do bieżącej SqlSelectStatement (jeden zwrócony podczas przeglądania danych wejściowych) lub nowe oświadczenie musi być uruchomiona jest obliczana przez metodę IsCompatible, a także od tego, co to jest już SqlSelectStatement, która jest zależna od węzły zostały poniżej Podany węzeł.  
  
 Zazwyczaj klauzul instrukcji SQL są oceniane po klauzulach, gdzie węzły są traktowane jako scalania nie są puste, nie można dodać do bieżącej instrukcji węzła. Na przykład jeśli węzeł next jest filtr, tego węzła można zintegrować bieżącego SqlSelectStatement tylko wtedy, gdy są spełnione następujące warunki:  
  
-   Wybierz OPCJĘ lista jest pusta. Jeśli lista wyboru nie jest pusta, lista wyboru wygenerowany za pomocą węzła poprzedzających filtr i predykatu może odwoływać się do kolumn utworzonego przez tej listy wyboru.  
  
-   GROUPBY jest pusta. Jeśli GROUPBY nie jest pusta, Dodawanie filtru oznaczałoby filtrowania przed grupowania, który nie jest prawidłowa.  
  
-   Klauzuli TOP jest pusta. Jeśli w klauzuli TOP nie jest pusta, Dodawanie filtru oznaczałoby filtrowania przed wykonaniem TOP, który nie jest prawidłowa.  
  
 Nie dotyczy węzłom nierelacyjnych DbConstantExpression lub wyrażenia arytmetyczne, ponieważ są one zawsze dołączane jako część istniejącego SqlSelectStatement.  
  
 Ponadto gdy wystąpią korzeń drzewa sprzężenia (sprzężenia węzeł, który nie ma nadrzędnego sprzężenia), nowy SqlSelectStatement jest uruchomiona. Wszystkie jego elementy podrzędne sprzężenia kręgosłupa po lewej stronie są agregowane w tym SqlSelectStatement.  
  
 Zawsze, gdy nowy SqlSelectStatement jest uruchomiona, a bieżąca zostanie dodany do danych wejściowych, bieżący SqlSelectStatement może muszą być wykonane przez dodanie kolumny projekcji (klauzuli SELECT), jeśli jeszcze nie istnieje. Można to zrobić za pomocą metody AddDefaultColumns, która analizuje FromExtents z SqlSelectStatement i dodaje wszystkie kolumny, które na liście zakresów reprezentowany przez FromExtents łączy w zakresie do listy kolumn, planowane. Tej operacji, ponieważ w tym momencie jest nieznany kolumny, które odwołują się w innych węzłach. To może być zoptymalizowana pod kątem tylko projektu kolumn, które później mogą być używane.  
  
### <a name="join-flattening"></a>Dołącz spłaszczania  
 Właściwość IsParentAJoin pomaga ustalić, czy można spłaszczenia danego sprzężenia. W szczególności zwraca IsParentAJoin `true` tylko dla lewy element podrzędny sprzężenia i dla każdej DbScanExpression, który jest natychmiastowe wejście do sprzężenia, w którym to przypadku tego węzła podrzędnego ponownie używa tego samego SqlSelectStatement, który później użyty element nadrzędny. Aby uzyskać więcej informacji zobacz "Dołącz do wyrażenia".  
  
### <a name="input-alias-redirecting"></a>Wprowadź Alias przekierowania folderu  
 Alias wejściowy przekierowywanie odbywa się z tabelą symboli.  
  
 Aby wyjaśnić, przekierowywanie alias wejściowy, należy zapoznać się z pierwszym przykładzie w [generowania SQL z drzew poleceń — najlepsze praktyki](../../../../../docs/framework/data/adonet/ef/generating-sql-from-command-trees-best-practices.md).  Brak "" musiał zostać przekierowane na "b" w projekcji.  
  
 Gdy tworzony jest obiekt SqlSelectStatement, jakim jest danych wejściowych do węzła jest umieszczany we właściwości From SqlSelectStatement. Symbol (< symbol_b >) jest tworzony na podstawie powiązania wejściowego name ("b") do reprezentowania w tym zakresie i "AS" + < symbol_b > jest dołączany do klauzuli From.  Symbol jest także dodawane do właściwości FromExtents.  
  
 Symbol jest także dodawane do tabeli symboli do połączenia nazwa powiązania wejściowego ("b", < symbol_b >).  
  
 Jeśli kolejne węzeł ponownie używa tego SqlSelectStatement, dodaje wpis do tabeli symboli do jego nazwę powiązania wejściowego łącza do tego symbolu. W naszym przykładzie spowoduje ponowne użycie SqlSelectStatement i Dodaj DbProjectExpression o nazwie powiązania wejściowego "a" ("," \< symbol_b >) do tabeli.  
  
 Jeśli wyrażenia odwoływać się do nazwy powiązania wejściowego węzła, który jest ponowne SqlSelectStatement, odwołanie zostanie rozwiązany, za pomocą tabeli symboli poprawne symbol przekierowane. Gdy "" z "a.x""" nie zostanie rozwiązany podczas odwiedzania reprezentujący DbVariableReferenceExpression "" it rozwiąże symbol < symbol_b >.  
  
### <a name="join-alias-flattening"></a>Dołącz spłaszczanie aliasu  
 Spłaszczanie alias sprzężenia jest osiągana, gdy odwiedzający DbPropertyExpression zgodnie z opisem w sekcji zatytułowany DbPropertyExpression.  
  
### <a name="column-name-and-extent-alias-renaming"></a>Nazwa kolumny i zakres Alias zmiana nazwy  
 Wydanie nazwy kolumny oraz zmiana nazwy aliasu w zakresie zostanie rozwiązana przy użyciu symboli, które tylko pobrać zastępowane z aliasami w drugim etapie generowania opisane w sekcji drugiej fazy generowanie kodu SQL: generowanie polecenie String.  
  
## <a name="first-phase-of-the-sql-generation-visiting-the-expression-tree"></a>Pierwszą fazę generowanie kodu SQL: odwiedzający wyrażenie drzewa  
 W tej sekcji opisano pierwszą fazę generowanie kodu SQL, gdy jest tworzony reprezentujący wyrażenie, które odwiedzenia zapytania i pośredniego struktury, albo SqlSelectStatement lub SqlBuilder.  
  
 W tej sekcji opisano zasady zaproszonych wyrażenie inny węzeł kategorii i szczegóły odwiedzający typy określonego wyrażenia.  
  
### <a name="relational-non-join-nodes"></a>Relacyjne węzłów (bez sprzężeń)  
 Następujące typy wyrażeń obsługują węzłów z systemem innym niż sprzężenia:  
  
-   DbDistinctExpression  
  
-   DbFilterExpression  
  
-   DbGroupByExpression  
  
-   DbLimitExpession  
  
-   DbProjectExpression  
  
-   DbSkipExpression  
  
-   DbSortExpression  
  
 Te węzły odwiedzający jest zgodny ze wzorcem następujące:  
  
1.  Odwiedź relacyjne dane wejściowe i uzyskać SqlSelectStatement wynikowy. Dane wejściowe relacyjne węzeł może być jedną z następujących czynności:  
  
    -   Relacyjne węzła, w tym zakresie (DbScanExpression, na przykład). Węzeł takich odwiedzania zwraca SqlSelectStatement.  
  
    -   Operacja wyrażenie (UNION ALL, na przykład). Wynik musi być ujęte w nawiasy i umieścić w klauzuli FROM SqlSelectStatement nowe.  
  
2.  Sprawdź, czy bieżący węzeł może być dodany do SqlSelectStatement produkowane przez danych wejściowych. Treścią wyrażenia grupowania w instrukcji SQL sekcji opisano to. Jeśli nie,  
  
    -   POP bieżącego obiektu SqlSelectStatement.  
  
    -   Utwórz nowy obiekt SqlSelectStatement i Dodaj popped SqlSelectStatement jako od nowego obiektu SqlSelectStatement.  
  
    -   Umieść nowy obiekt na szczycie stosu.  
  
3.  Przekierowanie powiązania wyrażenie wejściowe poprawne symbol z danych wejściowych. Te informacje są przechowywane w obiekcie SqlSelectStatement.  
  
4.  Dodaj nowy zakres SymbolTable.  
  
5.  Odwiedź stronę z systemem innym niż dane wejściowe część wyrażenia (na przykład projekcji i predykatu).  
  
6.  Wyświetl wszystkie obiekty dodane do stosów globalnego.  
  
 DbSkipExpression nie ma bezpośredniego odpowiednika w języku SQL. Logicznie jest przekształcana na:  
  
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
 Poniżej są uznawane za wyrażeniach sprzężenia i są przetwarzane w typowy sposób, przy użyciu metody VisitJoinExpression:  
  
-   Metody DbApplyExpression  
  
-   DbJoinExpression  
  
-   DbCrossJoinExpression  
  
 Poniżej przedstawiono kroki, odwiedź stronę:  
  
 Najpierw przed odwiedzenie elementów podrzędnych, IsParentAJoin jest wywoływana, aby sprawdzić, czy węzeł sprzężenia jest elementem podrzędnym sprzężenia wzdłuż lewej kręgosłupa. Jeśli zwraca wartość false, nowe SqlSelectStatement jest uruchomiona. W tym sensie sprzężeń są odwiedzane inaczej z pozostałych węzłów, ponieważ element nadrzędny (węzeł sprzężenia) tworzy SqlSelectStatement dla dzieci, być może używać.  
  
 Po drugie przetworzyć wejść jeden naraz. Dla każdego danych wejściowych:  
  
1.  Można znaleźć w danych wejściowych.  
  
2.  Proces POST wynik odwiedzający danych wejściowych, wywołując ProcessJoinInputResult, który jest odpowiedzialny za konserwację tabeli symboli po odwiedzając podrzędnych wyrażenia sprzężenia i prawdopodobnie Kończenie SqlSelectStatement utworzonego przez obiekt podrzędny. Wynik dziecka może być jedną z następujących czynności:  
  
    -   SqlSelectStatement niż ten, który zostanie dodany element nadrzędny. W takim przypadku mogą musi zostać wykonane przez dodawanie kolumn. Jeśli wprowadzono sprzężenia, musisz utworzyć nowy symbol sprzężenia. W przeciwnym razie utwórz normalne symbolu.  
  
    -   Zakres (DbScanExpression, na przykład), w których przypadku wystarczy dodać go do listy składników elementu nadrzędnego obiektu SqlSelectStatement.  
  
    -   Nie SqlSelectStatement, w którym przypadku, gdy jest on ujęte w nawiasy.  
  
    -   Tym samym SqlSelectStatement, do którego jest dodawany element nadrzędny. W takim przypadku symbole na liście FromExtents konieczne zastąpione pojedynczego JoinSymbol nowe reprezentujący je wszystkie.  
  
    -   W pierwszych trzech przypadkach AddFromSymbol nazywa się dodać klauzulę AS i zaktualizować tabeli symboli.  
  
 Trzecie odwiedzenia warunek sprzężenia (jeśli istnieje).  
  
### <a name="set-operations"></a>Operacje na zestawie  
 Operacje na zestawie DbUnionAllExpression wyrażenia DbExceptExpression i DbIntersectExpression są przetwarzane przez metodę VisitSetOpExpression. Tworzy SqlBuilder kształtu  
  
```xml  
<leftSqlSelectStatement> <setOp> <rightSqlSelectStatement>  
```  
  
 Gdzie \<leftSqlSelectStatement > i \<rightSqlSelectStatement > są SqlSelectStatements uzyskane wszystkich danych wejściowych, odwiedzając i \<setOp > jest odpowiadająca mu operacja (UNION ALL na przykład).  
  
### <a name="dbscanexpression"></a>DbScanExpression  
 Po odwiedzeniu w kontekście sprzężenia (jako dane wejściowe sprzężenia, które jest elementem podrzędnym lewego sprzężenia innego), DbScanExpression zwraca SqlBuilder z elementem docelowym SQL dla odpowiedniego obiektu docelowego, definiującego zapytania, tabeli lub widoku. W przeciwnym razie nowy SqlSelectStatement jest tworzony z pole od ustawioną odnoszą się do odpowiedniego obiektu docelowego.  
  
### <a name="dbvariablereferenceexpression"></a>DbVariableReferenceExpression  
 Odwiedziny DbVariableReferenceExpression zwraca Symbol odpowiadający tego wyrażenia odwołanie do zmiennej, oparte na wyszukiwanie w tabeli symboli.  
  
### <a name="dbpropertyexpression"></a>DbPropertyExpression  
 Spłaszczanie alias sprzężenia jest identyfikowane i przetworzone podczas odwiedzania DbPropertyExpression.  
  
 Właściwości wystąpienia jest najpierw odwiedzi i wynik jest Symbol, JoinSymbol lub SymbolPair. Poniżej przedstawiono sposób obsługi tych trzech przypadkach:  
  
-   Jeśli JoinSymbol jest zwracany, właściwość niż jego NameToExtent zawiera symbol wymagane właściwości. Jeśli symbol sprzężenia reprezentuje zagnieżdżonych sprzężenia, nową parę Symbol jest zwracany za symbolu sprzężenia, aby śledzić symbol, który będzie służyć jako alias wystąpienia i symbol reprezentujące właściwość dalszego rozpoznawania.  
  
-   Część kolumny jest symbol sprzężenia SymbolPair jest zwracany, zwracany jest ponownie symbol sprzężenia, ale teraz jako wartość właściwości column jest aktualizowane wskaż właściwości reprezentowanego przez wyrażenie bieżącej właściwości. W przeciwnym razie SqlBuilder jest zwracana ze źródłem SymbolPair jako alias i symbol dla bieżącej właściwości jako kolumnę.  
  
-   Jeśli Symbol jest zwracany, metoda odwiedziny zwraca SqlBuilder metodę z tego wystąpienia jako alias i nazwę właściwości jako nazwa kolumny.  
  
### <a name="dbnewinstanceexpression"></a>DbNewInstanceExpression  
 Gdy jest używany jako właściwość projekcji DbProjectExpression, DbNewInstanceExpression tworzy rozdzielana przecinkami lista argumentów do reprezentowania planowanego kolumn.  
  
 Gdy obiekt DbNewInstanceExpression ma typ zwracany kolekcji i definiuje nową kolekcję wyrażeń podane jako argumenty, oddzielnie obsługi następujących trzech przypadkach:  
  
-   Jeśli DbNewInstanceExpression DbElementExpression jako jedynego argumentu, jest translacja w następujący sposób:  
  
    ```  
    NewInstance(Element(X)) =>  SELECT TOP 1 …FROM X  
    ```  
  
 Jeśli obiekt DbNewInstanceExpression nie ma argumentów (reprezentuje pusta tabela), DbNewInstanceExpression jest przekształcana na:  
  
```  
SELECT CAST(NULL AS <primitiveType>) as X  
FROM (SELECT 1) AS Y WHERE 1=0  
```  
  
 W przeciwnym razie DbNewInstanceExpression kompilacje drabinę union all, argumentów:  
  
```  
SELECT <visit-result-arg1> as X  
UNION ALL SELECT <visit-result-arg2> as X  
UNION ALL …  
UNION ALL SELECT <visit-result-argN> as X  
```  
  
### <a name="dbfunctionexpression"></a>Obiekcie DbFunctionExpression  
 Canonical i wbudowane funkcje są przetwarzane tak samo: Jeśli potrzebna jest obsługa specjalnej (TRIM(string) do LTRIM(RTRIM(string), na przykład), odpowiedni program obsługi jest wywoływany. W przeciwnym razie są tłumaczone na FunctionName (arg1, arg2,... argn).  
  
 Słowniki są używane do śledzenia funkcje, które wymagają specjalnej obsługi i ich odpowiednie programy obsługi.  
  
 Funkcje zdefiniowane przez użytkownika są tanslated do NamespaceName.FunctionName (arg1, arg2,... argn).  
  
### <a name="dbelementexpression"></a>DbElementExpression  
 Tylko metody, które odwiedza DbElementExpression jest wywołane odwiedzający DbElementExpression, gdy jest używany do reprezentowania skalarne podzapytania. W związku z tym DbElementExpression przekłada się na pełną SqlSelectStatement i dodaje je w nawiasach.  
  
### <a name="dbquantifierexpression"></a>DbQuantifierExpression  
 W zależności od typu wyrażenia (dowolne), jest translacja DbQuantifierExpression go jako:  
  
```  
Any(input, x) => Exists(Filter(input,x))  
All(input, x) => Not Exists(Filter(input, not(x))  
```  
  
### <a name="dbnotexpression"></a>Obiekt DbNotExpression  
 W niektórych przypadkach prawdopodobnie Zwiń tłumaczenia obiekt DbNotExpression z jego wyrażenie wejściowe. Na przykład:  
  
```  
Not(IsNull(a)) =>  "a IS NOT NULL"  
Not(All(input, x) => Not (Not Exists(Filter(input, not(x))) => Exists(Filter(input, not(x))  
```  
  
 Zwiń drugi jest wykonywane przyczyną jest to ponieważ wydajność zostały wprowadzone przez dostawcę podczas tłumaczenia DbQuantifierExpression z type All. W związku z tym Entity Framework nie może być wykonana uproszczenia.  
  
### <a name="dbisemptyexpression"></a>DbIsEmptyExpression  
 DbIsEmptyExpression jest translacja jako:  
  
```  
IsEmpty(inut) = Not Exists(input)  
```  
  
## <a name="second-phase-of-sql-generation-generating-the-string-command"></a>Drugi etap generowanie kodu SQL: generowanie polecenie String  
 Podczas generowania ciąg polecenia SQL, SqlSelectStatement tworzy rzeczywiste aliasów dla symboli, którego dotyczy nazwy kolumny oraz zmiana nazwy aliasu w zakresie.  
  
 Zmiana nazwy aliasu zakres występuje podczas zapisu obiektu SqlSelectStatement na ciąg. Najpierw utwórz listę zawierającą wszystkie aliasy, które są używane przez zewnętrzne zakresów. Każdy symbol w FromExtents (lub AllJoinExtents, jeśli jest inne niż null), pobiera zmieniono jego nazwę, jeśli powoduje ona konflikt z jednym z zakresów zewnętrzne. Jeśli zmiana nazwy jest potrzebny, nie spowoduje ona konflikt z jednym z zakresów zebrane w AllExtentNames.  
  
 Zmiana nazwy kolumny występuje podczas zapisywania obiektu Symbol na ciąg. AddDefaultColumns w pierwszej fazie określi, czy można zmienić nazwy symbolu kolumny. W drugim etapie występuje tylko zmiany nazwy, upewniając się, że nazwa wyprodukowanych nie powoduje konfliktu z dowolną nazwę używaną w AllColumnNames  
  
 Do tworzenia unikatowych nazw zarówno dla zakresu aliasy i dla kolumn, należy użyć _n < existing_name >, gdzie n to najmniejsza alias, który nie został jeszcze użyty. Globalna lista wszystkie aliasy podkreśla konieczność zmiany nazw w kaskadowego.  
  
## <a name="see-also"></a>Zobacz też  
 [Generowanie kodu SQL w dostawcy próbki](../../../../../docs/framework/data/adonet/ef/sql-generation-in-the-sample-provider.md)
