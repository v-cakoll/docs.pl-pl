---
title: Architektura i projekt
ms.date: 03/30/2017
ms.assetid: bd738d39-00e2-4bab-b387-90aac1a014bd
ms.openlocfilehash: 50fc643fecf4b188123c556d754b3cbfa529e5e9
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251716"
---
# <a name="architecture-and-design"></a><span data-ttu-id="b2301-102">Architektura i projekt</span><span class="sxs-lookup"><span data-stu-id="b2301-102">Architecture and Design</span></span>

<span data-ttu-id="b2301-103">Moduł generowania kodu SQL w ramach [dostawcy przykładu](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) jest zaimplementowany jako gość w drzewie wyrażenia, który reprezentuje drzewo poleceń.</span><span class="sxs-lookup"><span data-stu-id="b2301-103">The SQL generation module in the [Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) is implemented as a visitor on the expression tree that represents the command tree.</span></span> <span data-ttu-id="b2301-104">Generowanie jest wykonywane w jednym przebiegu w drzewie wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="b2301-104">The generation is done in a single pass over the expression tree.</span></span>

<span data-ttu-id="b2301-105">Węzły drzewa są przetwarzane od dołu do góry.</span><span class="sxs-lookup"><span data-stu-id="b2301-105">The nodes of the tree are processed from the bottom up.</span></span> <span data-ttu-id="b2301-106">Najpierw jest generowana struktura pośrednia: SqlSelectStatement lub SqlBuilder, zarówno implementujące ISqlFragment.</span><span class="sxs-lookup"><span data-stu-id="b2301-106">First, an intermediate structure is produced: SqlSelectStatement or SqlBuilder, both implementing ISqlFragment.</span></span> <span data-ttu-id="b2301-107">Następnie instrukcja SQL String jest generowana z tej struktury.</span><span class="sxs-lookup"><span data-stu-id="b2301-107">Next, the string SQL statement is produced from that structure.</span></span> <span data-ttu-id="b2301-108">Istnieją dwie przyczyny dla struktury pośredniej:</span><span class="sxs-lookup"><span data-stu-id="b2301-108">There are two reasons for the intermediate structure:</span></span>

- <span data-ttu-id="b2301-109">Logicznie instrukcja SELECT języka SQL jest wypełniana poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="b2301-109">Logically, a SQL SELECT statement is populated out of order.</span></span> <span data-ttu-id="b2301-110">Węzły, które uczestniczą w klauzuli FROM, są odwiedzane przed węzłami, które uczestniczą w klauzuli WHERE, GROUP BY i ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="b2301-110">The nodes that participate in the FROM clause are visited before the nodes that participate in the WHERE, GROUP BY, and the ORDER BY clause.</span></span>

- <span data-ttu-id="b2301-111">Aby zmienić nazwy aliasów, należy zidentyfikować wszystkie używane aliasy, aby uniknąć kolizji podczas zmiany nazwy.</span><span class="sxs-lookup"><span data-stu-id="b2301-111">To rename aliases, you must identify all used aliases to avoid collisions during renaming.</span></span> <span data-ttu-id="b2301-112">Aby odroczyć opcje zmiany nazwy w elemencie SqlBuilder, Użyj obiektów symboli do reprezentowania kolumn, które są kandydatami do zmiany nazwy.</span><span class="sxs-lookup"><span data-stu-id="b2301-112">To defer the renaming choices in SqlBuilder, use Symbol objects to represent the columns that are candidates for renaming.</span></span>

<span data-ttu-id="b2301-113">![Diagram](./media/de1ca705-4f7c-4d2d-ace5-afefc6d3cefa.gif "de1ca705-4f7c-4d2d-ace5-afefc6d3cefa")</span><span class="sxs-lookup"><span data-stu-id="b2301-113">![Diagram](./media/de1ca705-4f7c-4d2d-ace5-afefc6d3cefa.gif "de1ca705-4f7c-4d2d-ace5-afefc6d3cefa")</span></span>

<span data-ttu-id="b2301-114">W pierwszej fazie, podczas odwiedzania drzewa wyrażenia, wyrażenia są pogrupowane w SqlSelectStatements, sprzężenia są spłaszczone i aliasy sprzężenia są spłaszczone.</span><span class="sxs-lookup"><span data-stu-id="b2301-114">In the first phase, while visiting the expression tree, expressions are grouped into SqlSelectStatements, joins are flattened, and join aliases are flattened.</span></span> <span data-ttu-id="b2301-115">W trakcie tego przebiegu obiekty symboli reprezentują kolumny lub aliasy wejściowe, których nazwy można zmienić.</span><span class="sxs-lookup"><span data-stu-id="b2301-115">During this pass, Symbol objects represent columns or input aliases that may be renamed.</span></span>

<span data-ttu-id="b2301-116">W drugiej fazie podczas tworzenia rzeczywistego ciągu aliasy są zmieniane.</span><span class="sxs-lookup"><span data-stu-id="b2301-116">In the second phase, while producing the actual string, aliases are renamed.</span></span>

## <a name="data-structures"></a><span data-ttu-id="b2301-117">Struktury danych</span><span class="sxs-lookup"><span data-stu-id="b2301-117">Data Structures</span></span>

<span data-ttu-id="b2301-118">W tej sekcji omówiono typy używane w [przykładowym dostawcy](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) , który służy do tworzenia instrukcji SQL.</span><span class="sxs-lookup"><span data-stu-id="b2301-118">This section discusses the types used in the [Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) that you use to build a SQL statement.</span></span>

### <a name="isqlfragment"></a><span data-ttu-id="b2301-119">ISqlFragment</span><span class="sxs-lookup"><span data-stu-id="b2301-119">ISqlFragment</span></span>

<span data-ttu-id="b2301-120">Ta sekcja obejmuje klasy implementujące interfejs ISqlFragment, który służy do dwóch celów:</span><span class="sxs-lookup"><span data-stu-id="b2301-120">This section covers the classes that implement the ISqlFragment interface, which serves two purposes:</span></span>

- <span data-ttu-id="b2301-121">Wspólny typ zwracany dla wszystkich metod odwiedzających.</span><span class="sxs-lookup"><span data-stu-id="b2301-121">A common return type for all the visitor methods.</span></span>

- <span data-ttu-id="b2301-122">Zwraca metodę zapisu końcowego ciągu SQL.</span><span class="sxs-lookup"><span data-stu-id="b2301-122">Gives a method to write the final SQL string.</span></span>

```csharp
internal interface ISqlFragment {
   void WriteSql(SqlWriter writer, SqlGenerator sqlGenerator);
}
```

#### <a name="sqlbuilder"></a><span data-ttu-id="b2301-123">SqlBuilder</span><span class="sxs-lookup"><span data-stu-id="b2301-123">SqlBuilder</span></span>

<span data-ttu-id="b2301-124">SqlBuilder to urządzenie zbierające dla końcowego ciągu SQL, podobne do StringBuilder.</span><span class="sxs-lookup"><span data-stu-id="b2301-124">SqlBuilder is a gathering device for the final SQL string, similar to StringBuilder.</span></span> <span data-ttu-id="b2301-125">Składa się z ciągów, które składają się na końcowy kod SQL, wraz z ISqlFragments, które mogą być konwertowane na ciągi.</span><span class="sxs-lookup"><span data-stu-id="b2301-125">It consists of the strings that make up the final SQL, along with ISqlFragments that can be converted into strings.</span></span>

```csharp
internal sealed class SqlBuilder : ISqlFragment {
   public void Append(object s)
   public void AppendLine()
   public bool IsEmpty
}
```

#### <a name="sqlselectstatement"></a><span data-ttu-id="b2301-126">SqlSelectStatement</span><span class="sxs-lookup"><span data-stu-id="b2301-126">SqlSelectStatement</span></span>

<span data-ttu-id="b2301-127">SqlSelectStatement przedstawia kanoniczną instrukcję SQL SELECT kształtu "SELECT...</span><span class="sxs-lookup"><span data-stu-id="b2301-127">SqlSelectStatement represents a canonical SQL SELECT statement of the shape "SELECT …</span></span> <span data-ttu-id="b2301-128">Z..</span><span class="sxs-lookup"><span data-stu-id="b2301-128">FROM  ..</span></span> <span data-ttu-id="b2301-129">GDZIE...</span><span class="sxs-lookup"><span data-stu-id="b2301-129">WHERE …</span></span> <span data-ttu-id="b2301-130">GRUPUJ WEDŁUG...</span><span class="sxs-lookup"><span data-stu-id="b2301-130">GROUP BY …</span></span> <span data-ttu-id="b2301-131">ORDER BY ".</span><span class="sxs-lookup"><span data-stu-id="b2301-131">ORDER BY".</span></span>

<span data-ttu-id="b2301-132">Każda klauzula SQL jest reprezentowana przez element StringBuilder.</span><span class="sxs-lookup"><span data-stu-id="b2301-132">Each of the SQL clauses is represented by a StringBuilder.</span></span> <span data-ttu-id="b2301-133">Ponadto śledzi, czy określono różne i czy instrukcja jest najwyższej wartości.</span><span class="sxs-lookup"><span data-stu-id="b2301-133">In addition, it tracks whether Distinct has been specified and whether the statement is topmost.</span></span> <span data-ttu-id="b2301-134">Jeśli instrukcja nie jest najwyższej strony, klauzula ORDER BY jest pomijana, chyba że instrukcja ma również klauzulę TOP.</span><span class="sxs-lookup"><span data-stu-id="b2301-134">If the statement is not topmost, the ORDER BY clause is omitted unless the statement also has a TOP clause.</span></span>

<span data-ttu-id="b2301-135">FromExtents zawiera listę wejść dla instrukcji SELECT.</span><span class="sxs-lookup"><span data-stu-id="b2301-135">FromExtents contains the list of inputs for the SELECT statement.</span></span> <span data-ttu-id="b2301-136">W tym miejscu znajduje się zazwyczaj tylko jeden element.</span><span class="sxs-lookup"><span data-stu-id="b2301-136">There is usually just one element in this.</span></span> <span data-ttu-id="b2301-137">Instrukcje SELECT dla sprzężeń mogą tymczasowo mieć więcej niż jeden element.</span><span class="sxs-lookup"><span data-stu-id="b2301-137">SELECT statements for joins may temporarily have more than one element.</span></span>

<span data-ttu-id="b2301-138">Jeśli instrukcja SELECT jest tworzona przez węzeł sprzężenia, SqlSelectStatement utrzymuje listę wszystkich zakresów, które zostały spłaszczone w sprzężeniu w AllJoinExtents.</span><span class="sxs-lookup"><span data-stu-id="b2301-138">If the SELECT statement is created by a Join node, SqlSelectStatement maintains a list of all the extents that have been flattened in the join in AllJoinExtents.</span></span> <span data-ttu-id="b2301-139">OuterExtents reprezentuje zewnętrzne odwołania SqlSelectStatement i służy do zmiany nazwy aliasu wejściowego.</span><span class="sxs-lookup"><span data-stu-id="b2301-139">OuterExtents represents outer references of the SqlSelectStatement and is used for input alias renaming.</span></span>

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

#### <a name="topclause"></a><span data-ttu-id="b2301-140">TopClause</span><span class="sxs-lookup"><span data-stu-id="b2301-140">TopClause</span></span>

<span data-ttu-id="b2301-141">TopClause reprezentuje wyrażenie TOP w SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="b2301-141">TopClause represents the TOP expression in a SqlSelectStatement.</span></span> <span data-ttu-id="b2301-142">Właściwość TopCount wskazuje liczbę GÓRNych wierszy, które powinny być zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="b2301-142">The TopCount property indicates how many TOP rows should be selected.</span></span>  <span data-ttu-id="b2301-143">Gdy WithTies ma wartość true, TopClause została skompilowana z DbLimitExpression.</span><span class="sxs-lookup"><span data-stu-id="b2301-143">When WithTies is true, the TopClause was built from a DbLimitExpression.</span></span>

```csharp
class TopClause : ISqlFragment {
   internal bool WithTies {get}
   internal ISqlFragment TopCount {get}
   internal TopClause(ISqlFragment topCount, bool withTies)
   internal TopClause(int topCount, bool withTies)
}
```

### <a name="symbols"></a><span data-ttu-id="b2301-144">Symbole</span><span class="sxs-lookup"><span data-stu-id="b2301-144">Symbols</span></span>

<span data-ttu-id="b2301-145">Klasy związane z symbolami i tabela symboli wykonują zmiany nazw aliasów wejściowych, spłaszczania aliasów i aliasów kolumn.</span><span class="sxs-lookup"><span data-stu-id="b2301-145">The Symbol-related classes and the symbol table perform input alias renaming, join alias flattening, and column alias renaming.</span></span>

<span data-ttu-id="b2301-146">Klasa symbol reprezentuje zakres, zagnieżdżoną instrukcję SELECT lub kolumnę.</span><span class="sxs-lookup"><span data-stu-id="b2301-146">The Symbol class represents an extent, a nested SELECT statement, or a column.</span></span> <span data-ttu-id="b2301-147">Jest ona używana zamiast rzeczywistego aliasu, aby umożliwić zmianę nazwy po jej użyciu i zawiera również dodatkowe informacje o artefaktie, który reprezentuje (podobnie jak typ).</span><span class="sxs-lookup"><span data-stu-id="b2301-147">It is used instead of an actual alias to allow for renaming after it has been used and it also carries additional information for the artifact it represents (like the type).</span></span>

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

<span data-ttu-id="b2301-148">Nazwa przechowuje oryginalny alias dla reprezentowanego zakresu, zagnieżdżonej instrukcji SELECT lub kolumny.</span><span class="sxs-lookup"><span data-stu-id="b2301-148">Name stores the original alias for the represented extent, nested SELECT statement, or a column.</span></span>

<span data-ttu-id="b2301-149">NewName przechowuje alias, który będzie używany w instrukcji SELECT języka SQL.</span><span class="sxs-lookup"><span data-stu-id="b2301-149">NewName stores the alias that will be used in the SQL SELECT statement.</span></span> <span data-ttu-id="b2301-150">Początkowo została ustawiona nazwa i w razie potrzeby jest zmieniana tylko w przypadku generowania końcowego zapytania ciągu.</span><span class="sxs-lookup"><span data-stu-id="b2301-150">It is originally set to Name, and only renamed if needed when generating the final string query.</span></span>

<span data-ttu-id="b2301-151">Typ jest przydatny tylko w przypadku symboli reprezentujących zakresy i zagnieżdżone instrukcje SELECT.</span><span class="sxs-lookup"><span data-stu-id="b2301-151">Type is only useful for symbols representing extents and nested SELECT statements.</span></span>

#### <a name="symbolpair"></a><span data-ttu-id="b2301-152">SymbolPair</span><span class="sxs-lookup"><span data-stu-id="b2301-152">SymbolPair</span></span>

<span data-ttu-id="b2301-153">Klasa SymbolPair usuwa spłaszczone rekordy.</span><span class="sxs-lookup"><span data-stu-id="b2301-153">The SymbolPair class addresses record flattening.</span></span>

<span data-ttu-id="b2301-154">Rozważ wyrażenie właściwości D (v, "J3. j2. J1. a. x"), gdzie v jest VarRef, J1, j2, J3 jest przyłączaniem, a jest zakresem, a x jest kolumnami.</span><span class="sxs-lookup"><span data-stu-id="b2301-154">Consider a property expression D(v, "j3.j2.j1.a.x") where v is a VarRef, j1, j2, j3 are joins, a is an extent, and x is a columns.</span></span>

<span data-ttu-id="b2301-155">Ten element musi zostać przetłumaczony na {j '}. {x '}.</span><span class="sxs-lookup"><span data-stu-id="b2301-155">This has to be translated eventually into {j'}.{x'}.</span></span> <span data-ttu-id="b2301-156">Pole Source reprezentuje niezależny element sqlstateer reprezentujący wyrażenie join (Powiedz J2); jest to zawsze symbol sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="b2301-156">The source field represents the outermost SqlStatement, representing a join expression (say j2); this is always a Join symbol.</span></span> <span data-ttu-id="b2301-157">Pole kolumny jest przenoszone z jednego symbolu sprzężenia do następnego, dopóki nie zostanie zatrzymane na symbolu bez sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="b2301-157">The column field moves from one join symbol to the next until it stops at a non-join symbol.</span></span> <span data-ttu-id="b2301-158">Jest on zwracany podczas odwiedzania elementu DbPropertyExpression, ale nigdy nie jest dodawany do elementu SqlBuilder.</span><span class="sxs-lookup"><span data-stu-id="b2301-158">This is returned when visiting a DbPropertyExpression but is never added to a SqlBuilder.</span></span>

```csharp
class SymbolPair : ISqlFragment {
   public Symbol Source;
   public Symbol Column;
   public SymbolPair(Symbol source, Symbol column)
}
```

#### <a name="joinsymbol"></a><span data-ttu-id="b2301-159">JoinSymbol</span><span class="sxs-lookup"><span data-stu-id="b2301-159">JoinSymbol</span></span>

<span data-ttu-id="b2301-160">Symbol sprzężenia jest symbolem, który reprezentuje zagnieżdżoną instrukcję SELECT z przyłączeniem lub wejściem sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="b2301-160">A Join symbol is a Symbol that represents a nested SELECT statement with a join or a join input.</span></span>

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

<span data-ttu-id="b2301-161">ColumnList reprezentuje listę kolumn w klauzuli SELECT, jeśli ten symbol reprezentuje instrukcję SELECT języka SQL.</span><span class="sxs-lookup"><span data-stu-id="b2301-161">ColumnList represents the list of columns in the SELECT clause if this symbol represents a SQL SELECT statement.</span></span> <span data-ttu-id="b2301-162">ExtentList jest listą zakresów w klauzuli SELECT.</span><span class="sxs-lookup"><span data-stu-id="b2301-162">ExtentList is the list of extents in the SELECT clause.</span></span> <span data-ttu-id="b2301-163">Jeśli sprzężenie ma wiele zakresów spłaszczonych na najwyższego poziomu, FlattenedExtentList śledzi zakres, aby upewnić się, że nazwy aliasów zakresów zostały poprawnie zmienione.</span><span class="sxs-lookup"><span data-stu-id="b2301-163">If the join has multiple extents flattened at the top level, FlattenedExtentList tracks the extents to ensure that extent aliases are renamed correctly.</span></span>

<span data-ttu-id="b2301-164">NameToExtent ma wszystkie zakresy w ExtentList jako słownik.</span><span class="sxs-lookup"><span data-stu-id="b2301-164">NameToExtent has all the extents in ExtentList as a dictionary.</span></span> <span data-ttu-id="b2301-165">IsNestedJoin służy do określenia, czy JoinSymbol jest zwykłym symbolem sprzężenia, czy taki, który ma odpowiednie SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="b2301-165">IsNestedJoin is used to determine whether a JoinSymbol is an ordinary join symbol or one that has a corresponding SqlSelectStatement.</span></span>

<span data-ttu-id="b2301-166">Wszystkie listy są ustawiane dokładnie raz, a następnie używane do wyszukiwania lub wyliczania.</span><span class="sxs-lookup"><span data-stu-id="b2301-166">All the lists are set exactly once and then used for lookups or enumeration.</span></span>

#### <a name="symboltable"></a><span data-ttu-id="b2301-167">SymbolTable</span><span class="sxs-lookup"><span data-stu-id="b2301-167">SymbolTable</span></span>

<span data-ttu-id="b2301-168">Symbol jest używany do rozpoznawania nazw zmiennych do symboli.</span><span class="sxs-lookup"><span data-stu-id="b2301-168">SymbolTable is used to resolve variable names to Symbols.</span></span> <span data-ttu-id="b2301-169">Symbol jest zaimplementowany jako stos z nowym wpisem dla każdego zakresu.</span><span class="sxs-lookup"><span data-stu-id="b2301-169">SymbolTable is implemented as a stack with a new entry for each scope.</span></span> <span data-ttu-id="b2301-170">Wyszukiwania wyszukują od góry stosu do dołu do momentu znalezienia wpisu.</span><span class="sxs-lookup"><span data-stu-id="b2301-170">Lookups search from the top of the stack to the bottom until an entry is found.</span></span>

```csharp
internal sealed class SymbolTable {
   internal void EnterScope()
   internal void ExitScope()
   internal void Add(string name, Symbol value)
   internal Symbol Lookup(string name)
}
```

<span data-ttu-id="b2301-171">Istnieje tylko jeden symbol w jednym wystąpieniu modułu generacji SQL.</span><span class="sxs-lookup"><span data-stu-id="b2301-171">There is only one SymbolTable per one instance of the Sql Generation module.</span></span> <span data-ttu-id="b2301-172">Zakresy są wprowadzane i zamykane dla każdego węzła relacyjnego.</span><span class="sxs-lookup"><span data-stu-id="b2301-172">Scopes are entered and exited for each relational node.</span></span> <span data-ttu-id="b2301-173">Wszystkie symbole we wcześniejszych zakresach są widoczne dla nowszych zakresów, chyba że są ukryte przez inne symbole o tej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="b2301-173">All symbols in earlier scopes are visible to later scopes unless hidden by other symbols with the same name.</span></span>

### <a name="global-state-for-the-visitor"></a><span data-ttu-id="b2301-174">Globalny stan dla gościa</span><span class="sxs-lookup"><span data-stu-id="b2301-174">Global State for the Visitor</span></span>

<span data-ttu-id="b2301-175">Aby ułatwić zmianę nazwy aliasów i kolumn, należy zachować listę wszystkich nazw kolumn (AllColumnNames) i aliasów zakresów (AllExtentNames), które zostały użyte podczas pierwszego przekazywania drzewa zapytań.</span><span class="sxs-lookup"><span data-stu-id="b2301-175">To assist in renaming of aliases and columns, maintain a list of all the column names (AllColumnNames) and extent aliases (AllExtentNames) that have been used in the first pass over the query tree.</span></span>  <span data-ttu-id="b2301-176">Tabela symboli rozpoznaje nazwy zmiennych do symboli.</span><span class="sxs-lookup"><span data-stu-id="b2301-176">The symbol table resolves variable names to Symbols.</span></span> <span data-ttu-id="b2301-177">IsVarRefSingle jest używane tylko na potrzeby weryfikacji, nie jest to absolutnie konieczne.</span><span class="sxs-lookup"><span data-stu-id="b2301-177">IsVarRefSingle is only used for verification purposes, it is not strictly necessary.</span></span>

<span data-ttu-id="b2301-178">Dwa stosy używane przez CurrentSelectStatement i IsParentAJoin są używane do przekazywania "parametrów" z węzłów nadrzędnych do elementów podrzędnych, ponieważ wzorzec gościa nie zezwala nam na przekazywanie parametrów.</span><span class="sxs-lookup"><span data-stu-id="b2301-178">The two stacks used via CurrentSelectStatement and IsParentAJoin are used to pass "parameters" from parent to child nodes, since the visitor pattern does not allow us to pass parameters.</span></span>

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

## <a name="common-scenarios"></a><span data-ttu-id="b2301-179">Typowe scenariusze</span><span class="sxs-lookup"><span data-stu-id="b2301-179">Common Scenarios</span></span>

<span data-ttu-id="b2301-180">W tej sekcji omówiono typowe scenariusze dostawcy.</span><span class="sxs-lookup"><span data-stu-id="b2301-180">This section discusses common provider scenarios.</span></span>

### <a name="grouping-expression-nodes-into-sql-statements"></a><span data-ttu-id="b2301-181">Grupowanie węzłów wyrażenia w instrukcjach SQL</span><span class="sxs-lookup"><span data-stu-id="b2301-181">Grouping Expression Nodes into SQL Statements</span></span>

<span data-ttu-id="b2301-182">SqlSelectStatement jest tworzony podczas napotkania pierwszego węzła relacyjnego (zazwyczaj jest to DbScanExpression zakres) podczas odwiedzania drzewa od dołu.</span><span class="sxs-lookup"><span data-stu-id="b2301-182">A SqlSelectStatement is created when the first relational node is encountered (typically a DbScanExpression extent) when visiting the tree from the bottom up.</span></span> <span data-ttu-id="b2301-183">Aby utworzyć instrukcję SELECT języka SQL z jak najmniejszej liczby zagnieżdżonych zapytań, należy agregować jako wiele węzłów nadrzędnych, jak to możliwe w tym SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="b2301-183">To produce a SQL SELECT statement with as few nested queries as possible, aggregate as many of its parent nodes as possible in that SqlSelectStatement.</span></span>

<span data-ttu-id="b2301-184">Decyzja o tym, czy dany węzeł (relacyjny) może zostać dodany do bieżącej SqlSelectStatement (zwracany podczas odwiedzania danych wejściowych) lub czy nowa instrukcja musi być uruchomiona jest obliczana przez metodę iscompatibled i zależy od tego, co jest już w SqlSelectStatement, który zależy od tego, jakie węzły znajdowały się poniżej danego węzła.</span><span class="sxs-lookup"><span data-stu-id="b2301-184">The decision of whether a given (relational) node can be added to the current SqlSelectStatement (the one returned when visiting the input) or if a new statement needs to be started is computed by the method IsCompatible and depends on what is already in the SqlSelectStatement, which depends on what nodes were below the given node.</span></span>

<span data-ttu-id="b2301-185">Zazwyczaj jeśli klauzule instrukcji SQL są oceniane po klauzulach, w których węzły uważane za scalanie nie są puste, nie można dodać węzła do bieżącej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="b2301-185">Typically, if SQL statement clauses are evaluated after clauses where the nodes being considered for merging are not empty, the node cannot be added to the current statement.</span></span> <span data-ttu-id="b2301-186">Na przykład jeśli następny węzeł jest filtrem, ten węzeł może być dołączany do bieżącego SqlSelectStatement tylko wtedy, gdy spełnione są następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="b2301-186">For example, if the next node is a Filter, that node can be incorporated into the current SqlSelectStatement only if the following is true:</span></span>

- <span data-ttu-id="b2301-187">Lista wyboru jest pusta.</span><span class="sxs-lookup"><span data-stu-id="b2301-187">The SELECT list is empty.</span></span> <span data-ttu-id="b2301-188">Jeśli lista wyboru nie jest pusta, lista wyboru została utworzona przez węzeł poprzedzający filtr, a predykat może odwoływać się do kolumn utworzonych przez tę listę wyboru.</span><span class="sxs-lookup"><span data-stu-id="b2301-188">If the SELECT list is not empty, the select list was produced by a node preceding the filter and the predicate may refer to columns produced by that SELECT list.</span></span>

- <span data-ttu-id="b2301-189">Wartość GROUPBY jest pusta.</span><span class="sxs-lookup"><span data-stu-id="b2301-189">The GROUPBY is empty.</span></span> <span data-ttu-id="b2301-190">Jeśli wartość GROUPBY nie jest pusta, dodanie filtru oznacza filtrowanie przed zgrupowaniem, co jest niepoprawne.</span><span class="sxs-lookup"><span data-stu-id="b2301-190">If the GROUPBY is not empty, adding the filter would mean filtering before grouping, which is not correct.</span></span>

- <span data-ttu-id="b2301-191">Klauzula TOP jest pusta.</span><span class="sxs-lookup"><span data-stu-id="b2301-191">The TOP clause is empty.</span></span> <span data-ttu-id="b2301-192">Jeśli klauzula TOP nie jest pusta, dodanie filtru oznacza filtrowanie przed wykonaniem góry, co jest niepoprawne.</span><span class="sxs-lookup"><span data-stu-id="b2301-192">If the TOP clause is not empty, adding the filter would mean filtering before doing TOP, which is not correct.</span></span>

<span data-ttu-id="b2301-193">Nie dotyczy to węzłów nierelacyjnych, takich jak DbConstantExpression lub Expressions, ponieważ są one zawsze uwzględniane jako część istniejącej SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="b2301-193">This does not apply to non-relational nodes like DbConstantExpression or arithmetic expressions, because these are always included as part of an existing SqlSelectStatement.</span></span>

<span data-ttu-id="b2301-194">Ponadto w przypadku napotkania głównego drzewa sprzężenia (węzłem sprzężenia, który nie ma nadrzędnego elementu join), jest uruchamiany nowy SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="b2301-194">Also, when encountering the root of join tree (a join node that does not have a join parent), a new SqlSelectStatement is started.</span></span> <span data-ttu-id="b2301-195">Wszystkie lewe pokrętło dołączania do elementów podrzędnych są agregowane w tym SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="b2301-195">All of its left spine join children are aggregated into that SqlSelectStatement.</span></span>

<span data-ttu-id="b2301-196">Za każdym razem, gdy nowa SqlSelectStatement jest uruchomiona, a bieżąca jest dodawana do danych wejściowych, może być konieczne ukończenie bieżącego SqlSelectStatement przez dodanie kolumn projekcji (klauzula SELECT), jeśli taka nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="b2301-196">Whenever a new SqlSelectStatement is started, and the current one is added to the input, the current SqlSelectStatement may need to be completed by adding projection columns (a SELECT clause) if one does not exist.</span></span> <span data-ttu-id="b2301-197">Jest to realizowane przy użyciu metody AddDefaultColumns, która przegląda FromExtents SqlSelectStatement i dodaje wszystkie kolumny, które lista zakresów reprezentowana przez FromExtents znajduje się w zakresie do listy rzutowanych kolumn.</span><span class="sxs-lookup"><span data-stu-id="b2301-197">This is done with the method AddDefaultColumns, which looks at the FromExtents of the SqlSelectStatement and adds all the columns that the list of extents represented by FromExtents brings in scope to the list of projected columns.</span></span> <span data-ttu-id="b2301-198">Dzieje się tak, ponieważ w tym momencie jest nieznane, do których kolumn odwołują się inne węzły.</span><span class="sxs-lookup"><span data-stu-id="b2301-198">This is done, because at that point, it is unknown which columns are referenced by the other nodes.</span></span> <span data-ttu-id="b2301-199">Można to zoptymalizować tylko w celu zaprojektowania kolumn, które mogą być później używane.</span><span class="sxs-lookup"><span data-stu-id="b2301-199">This can be optimized to only project the columns that can later be used.</span></span>

### <a name="join-flattening"></a><span data-ttu-id="b2301-200">Przyłączanie spłaszczania</span><span class="sxs-lookup"><span data-stu-id="b2301-200">Join Flattening</span></span>

<span data-ttu-id="b2301-201">Właściwość IsParentAJoin pomaga określić, czy dany element Join może być spłaszczony.</span><span class="sxs-lookup"><span data-stu-id="b2301-201">The IsParentAJoin property helps determine whether a given join can be flattened.</span></span> <span data-ttu-id="b2301-202">W szczególności IsParentAJoin zwraca `true` tylko dla lewego elementu podrzędnego sprzężenia i dla każdego DbScanExpression, który jest bezpośrednim wejściem do sprzężenia, w takim przypadku węzeł podrzędny ponownie używa tego samego SqlSelectStatement, którego element nadrzędny mógłby później użyć.</span><span class="sxs-lookup"><span data-stu-id="b2301-202">In particular, IsParentAJoin returns `true` only for the left child of a join and for each DbScanExpression that is an immediate input to a join, in which case that child node reuses the same SqlSelectStatement that the parent would later use.</span></span> <span data-ttu-id="b2301-203">Aby uzyskać więcej informacji, zobacz "wyrażenia sprzężenia".</span><span class="sxs-lookup"><span data-stu-id="b2301-203">For more information, see "Join Expressions".</span></span>

### <a name="input-alias-redirecting"></a><span data-ttu-id="b2301-204">Przekierowanie wejściowej aliasu</span><span class="sxs-lookup"><span data-stu-id="b2301-204">Input Alias Redirecting</span></span>

<span data-ttu-id="b2301-205">Przekierowanie aliasu wejściowego jest realizowane przy użyciu tabeli symboli.</span><span class="sxs-lookup"><span data-stu-id="b2301-205">Input alias redirecting is accomplished with the symbol table.</span></span>

<span data-ttu-id="b2301-206">Aby wyjaśnić Przekierowywanie aliasów wejściowych, zapoznaj się z pierwszym przykładem [generowania kodu SQL z drzew poleceń — najlepsze rozwiązania](generating-sql-from-command-trees-best-practices.md).</span><span class="sxs-lookup"><span data-stu-id="b2301-206">To explain input alias redirecting, refer to the first example in [Generating SQL from Command Trees - Best Practices](generating-sql-from-command-trees-best-practices.md).</span></span>  <span data-ttu-id="b2301-207">W projekcji należy przekierować "a" do "b".</span><span class="sxs-lookup"><span data-stu-id="b2301-207">There "a" needed to be redirected to "b" in the projection.</span></span>

<span data-ttu-id="b2301-208">Po utworzeniu obiektu SqlSelectStatement zakres, który jest wejściem do węzła, jest umieszczany we właściwości From SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="b2301-208">When a SqlSelectStatement object is created, the extent that is the input to the node is put in the From property of the SqlSelectStatement.</span></span> <span data-ttu-id="b2301-209">Symbol (\<symbol_b >) jest tworzony na podstawie nazwy powiązania wejściowego ("b"), aby reprezentować ten zakres i "AS \<" + symbol_b > jest dołączany do klauzuli FROM.</span><span class="sxs-lookup"><span data-stu-id="b2301-209">A Symbol (\<symbol_b>) is created based on the input binding name ("b") to represent that extent and "AS  " + \<symbol_b> is appended to the From Clause.</span></span>  <span data-ttu-id="b2301-210">Symbol jest również dodawany do właściwości FromExtents.</span><span class="sxs-lookup"><span data-stu-id="b2301-210">The symbol is also added to the FromExtents property.</span></span>

<span data-ttu-id="b2301-211">Symbol jest również dodawany do tabeli symboli, aby połączyć nazwę powiązania wejściowego ("b", \<symbol_b >).</span><span class="sxs-lookup"><span data-stu-id="b2301-211">The symbol is also added to the symbol table to link the input binding name to it ("b", \<symbol_b>).</span></span>

<span data-ttu-id="b2301-212">Jeśli kolejny węzeł ponownie używa tego SqlSelectStatement, dodaje wpis do tabeli symboli, aby połączyć jego nazwę powiązania wejściowego z tym symbolem.</span><span class="sxs-lookup"><span data-stu-id="b2301-212">If a subsequent node reuses that SqlSelectStatement, it adds an entry to the symbol table to link its input binding name to that symbol.</span></span> <span data-ttu-id="b2301-213">W naszym przykładzie DbProjectExpression z nazwą powiązania wejściowego "a" spowoduje ponowne użycie SqlSelectStatement i dodanie ("a", \< symbol_b >) do tabeli.</span><span class="sxs-lookup"><span data-stu-id="b2301-213">In our example, the DbProjectExpression with the input binding name of "a" would reuse the SqlSelectStatement and add ("a", \< symbol_b>) to the table.</span></span>

<span data-ttu-id="b2301-214">Gdy wyrażenia odwołują się do nazwy powiązania wejściowego węzła, który jest używany SqlSelectStatement, odwołanie jest rozwiązane przy użyciu tabeli symboli do prawidłowego przekierowanego symbolu.</span><span class="sxs-lookup"><span data-stu-id="b2301-214">When expressions reference the input binding name of the node that is reusing the SqlSelectStatement, that reference is resolved using the symbol table to the correct redirected symbol.</span></span> <span data-ttu-id="b2301-215">Gdy "a" z "a. x" jest rozpoznawany podczas odwiedzania DbVariableReferenceExpression reprezentującego "a", zostanie on \<rozpoznany jako symbol symbol_b >.</span><span class="sxs-lookup"><span data-stu-id="b2301-215">When "a" from "a.x" is resolved while visiting the DbVariableReferenceExpression representing "a" it will resolve to the Symbol \<symbol_b>.</span></span>

### <a name="join-alias-flattening"></a><span data-ttu-id="b2301-216">Przyłączanie spłaszczania aliasów</span><span class="sxs-lookup"><span data-stu-id="b2301-216">Join Alias Flattening</span></span>

<span data-ttu-id="b2301-217">Spłaszczanie aliasów sprzężenia jest osiągane podczas odwiedzania DbPropertyExpression zgodnie z opisem w sekcji DbPropertyExpression.</span><span class="sxs-lookup"><span data-stu-id="b2301-217">Join alias flattening is achieved when visiting a DbPropertyExpression as described in the section titled DbPropertyExpression.</span></span>

### <a name="column-name-and-extent-alias-renaming"></a><span data-ttu-id="b2301-218">Zmiana nazwy kolumny i zakresu aliasu</span><span class="sxs-lookup"><span data-stu-id="b2301-218">Column Name and Extent Alias Renaming</span></span>

<span data-ttu-id="b2301-219">Nazwa kolumny i alias zakresu zmiany nazwy są rozwiązywane przy użyciu symboli, które są zastępowane aliasami w drugiej fazie generacji opisanej w sekcji druga faza generowania kodu SQL: Generowanie ciągu polecenia.</span><span class="sxs-lookup"><span data-stu-id="b2301-219">The issue of column name and extent alias renaming is addressed by using symbols that only get substituted with aliases in the second phase of the generation described in the section titled Second Phase of SQL Generation: Generating the String Command.</span></span>

## <a name="first-phase-of-the-sql-generation-visiting-the-expression-tree"></a><span data-ttu-id="b2301-220">Pierwsza faza generowania kodu SQL: Odwiedzanie drzewa wyrażeń</span><span class="sxs-lookup"><span data-stu-id="b2301-220">First Phase of the SQL Generation: Visiting the Expression Tree</span></span>

<span data-ttu-id="b2301-221">W tej sekcji opisano pierwszą fazę generowania kodu SQL, gdy wyrażenie reprezentujące zapytanie jest odwiedzane i jest generowana struktura pośrednia (SqlSelectStatement lub SqlBuilder).</span><span class="sxs-lookup"><span data-stu-id="b2301-221">This section describes the first phase of SQL generation, when the expression representing the query is visited and an intermediate structure is produced, either a SqlSelectStatement or a SqlBuilder.</span></span>

<span data-ttu-id="b2301-222">W tej sekcji opisano zasady odwiedzające różne kategorie węzłów wyrażenia oraz szczegóły odwiedzające określone typy wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="b2301-222">This section describes the principles of visiting different expression node categories, and details of visiting specific expression types.</span></span>

### <a name="relational-non-join-nodes"></a><span data-ttu-id="b2301-223">Węzły relacyjne (bez sprzężenia)</span><span class="sxs-lookup"><span data-stu-id="b2301-223">Relational (Non-Join) Nodes</span></span>

<span data-ttu-id="b2301-224">Następujące typy wyrażeń obsługują węzły, które nie są przyłączane:</span><span class="sxs-lookup"><span data-stu-id="b2301-224">The following expression types support non-join nodes:</span></span>

- <span data-ttu-id="b2301-225">DbDistinctExpression</span><span class="sxs-lookup"><span data-stu-id="b2301-225">DbDistinctExpression</span></span>

- <span data-ttu-id="b2301-226">DbFilterExpression</span><span class="sxs-lookup"><span data-stu-id="b2301-226">DbFilterExpression</span></span>

- <span data-ttu-id="b2301-227">DbGroupByExpression</span><span class="sxs-lookup"><span data-stu-id="b2301-227">DbGroupByExpression</span></span>

- <span data-ttu-id="b2301-228">DbLimitExpression</span><span class="sxs-lookup"><span data-stu-id="b2301-228">DbLimitExpression</span></span>

- <span data-ttu-id="b2301-229">DbProjectExpression</span><span class="sxs-lookup"><span data-stu-id="b2301-229">DbProjectExpression</span></span>

- <span data-ttu-id="b2301-230">DbSkipExpression</span><span class="sxs-lookup"><span data-stu-id="b2301-230">DbSkipExpression</span></span>

- <span data-ttu-id="b2301-231">DbSortExpression</span><span class="sxs-lookup"><span data-stu-id="b2301-231">DbSortExpression</span></span>

<span data-ttu-id="b2301-232">Odwiedzanie tych węzłów jest zgodne z następującym wzorcem:</span><span class="sxs-lookup"><span data-stu-id="b2301-232">Visiting these nodes follows the following pattern:</span></span>

1. <span data-ttu-id="b2301-233">Odwiedź dane wejściowe relacyjne i uzyskaj wyniki SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="b2301-233">Visit the relational input and get the resulting SqlSelectStatement.</span></span> <span data-ttu-id="b2301-234">Wejście do węzła relacyjnego może być jedną z następujących:</span><span class="sxs-lookup"><span data-stu-id="b2301-234">The input to a relational node could be one of the following:</span></span>

    - <span data-ttu-id="b2301-235">Węzeł relacyjny, w tym zakres (na przykład DbScanExpression).</span><span class="sxs-lookup"><span data-stu-id="b2301-235">A relational node, including an extent (a DbScanExpression, for example).</span></span> <span data-ttu-id="b2301-236">Odwiedzenie takiego węzła zwraca SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="b2301-236">Visiting such a node returns a SqlSelectStatement.</span></span>

    - <span data-ttu-id="b2301-237">Wyrażenie zestawu operacji (na przykład UNION ALL).</span><span class="sxs-lookup"><span data-stu-id="b2301-237">A set operation expression (UNION ALL, for example).</span></span> <span data-ttu-id="b2301-238">Wynik musi być opakowany w nawiasy i umieszczany w klauzuli FROM nowego SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="b2301-238">The result has to be wrapped in brackets and put in the FROM clause of a new SqlSelectStatement.</span></span>

2. <span data-ttu-id="b2301-239">Sprawdź, czy bieżący węzeł można dodać do SqlSelectStatement utworzonego przez dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="b2301-239">Check whether the current node can be added to the SqlSelectStatement produced by the input.</span></span> <span data-ttu-id="b2301-240">Sekcja zatytułowana wyrażenia grupowania w instrukcjach SQL zawiera opis.</span><span class="sxs-lookup"><span data-stu-id="b2301-240">The section titled Grouping Expressions into SQL Statements describes this.</span></span> <span data-ttu-id="b2301-241">Jeśli nie,</span><span class="sxs-lookup"><span data-stu-id="b2301-241">If not,</span></span>

    - <span data-ttu-id="b2301-242">Wyskakujący bieżący obiekt SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="b2301-242">Pop the current SqlSelectStatement object.</span></span>

    - <span data-ttu-id="b2301-243">Utwórz nowy obiekt SqlSelectStatement i Dodaj zdjęte SqlSelectStatement jako z nowego obiektu SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="b2301-243">Create a new SqlSelectStatement object and add the popped SqlSelectStatement as the FROM of the new SqlSelectStatement object.</span></span>

    - <span data-ttu-id="b2301-244">Umieść nowy obiekt na szczycie stosu.</span><span class="sxs-lookup"><span data-stu-id="b2301-244">Put the new object on top of the stack.</span></span>

3. <span data-ttu-id="b2301-245">Przekieruj powiązanie wyrażenia wejściowego do poprawnego symbolu z danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="b2301-245">Redirect the input expression binding to the correct symbol from the input.</span></span> <span data-ttu-id="b2301-246">Te informacje są przechowywane w obiekcie SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="b2301-246">This information is maintained in the SqlSelectStatement object.</span></span>

4. <span data-ttu-id="b2301-247">Dodaj nowy zakres symboli.</span><span class="sxs-lookup"><span data-stu-id="b2301-247">Add a new SymbolTable scope.</span></span>

5. <span data-ttu-id="b2301-248">Sprawdź część niewejściową wyrażenia (na przykład projekcję i predykat).</span><span class="sxs-lookup"><span data-stu-id="b2301-248">Visit the non-input part of the expression (for example, Projection and Predicate).</span></span>

6. <span data-ttu-id="b2301-249">Wyskakujące wszystkie obiekty dodane do stosów globalnych.</span><span class="sxs-lookup"><span data-stu-id="b2301-249">Pop all the objects added to the global stacks.</span></span>

 <span data-ttu-id="b2301-250">DbSkipExpression nie mają bezpośredniego odpowiednika w SQL.</span><span class="sxs-lookup"><span data-stu-id="b2301-250">DbSkipExpression not have a direct equivalent in SQL.</span></span> <span data-ttu-id="b2301-251">Logicznie, jest tłumaczony na:</span><span class="sxs-lookup"><span data-stu-id="b2301-251">Logically, it is translated into:</span></span>

```sql
SELECT Y.x1, Y.x2, ..., Y.xn
FROM (
   SELECT X.x1, X.x2, ..., X.xn, row_number() OVER (ORDER BY sk1, sk2, ...) AS [row_number]
   FROM input as X
   ) as Y
WHERE Y.[row_number] > count
ORDER BY sk1, sk2, ...
```

### <a name="join-expressions"></a><span data-ttu-id="b2301-252">Wyrażenia sprzężenia</span><span class="sxs-lookup"><span data-stu-id="b2301-252">Join Expressions</span></span>

<span data-ttu-id="b2301-253">Następujące są uznawane za wyrażenia sprzężenia i są przetwarzane w typowy sposób przez metodę VisitJoinExpression:</span><span class="sxs-lookup"><span data-stu-id="b2301-253">The following are considered join expressions and they are processed in a common way, by the VisitJoinExpression method:</span></span>

- <span data-ttu-id="b2301-254">DbApplyExpression</span><span class="sxs-lookup"><span data-stu-id="b2301-254">DbApplyExpression</span></span>

- <span data-ttu-id="b2301-255">DbJoinExpression</span><span class="sxs-lookup"><span data-stu-id="b2301-255">DbJoinExpression</span></span>

- <span data-ttu-id="b2301-256">DbCrossJoinExpression</span><span class="sxs-lookup"><span data-stu-id="b2301-256">DbCrossJoinExpression</span></span>

<span data-ttu-id="b2301-257">Poniżej przedstawiono kroki przedstawione poniżej:</span><span class="sxs-lookup"><span data-stu-id="b2301-257">The following are the visit steps:</span></span>

<span data-ttu-id="b2301-258">Przed odwiedzeniem elementów podrzędnych IsParentAJoin jest wywoływana w celu sprawdzenia, czy węzeł sprzężenia jest elementem podrzędnym sprzężenia wzdłuż lewego grzbietu.</span><span class="sxs-lookup"><span data-stu-id="b2301-258">First, before visiting the children, IsParentAJoin is invoked to check whether the join node is a child of a join along a left spine.</span></span> <span data-ttu-id="b2301-259">Jeśli zwraca wartość false, zostanie uruchomione nowe SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="b2301-259">If it returns false, a new SqlSelectStatement is started.</span></span> <span data-ttu-id="b2301-260">W tym sensie sprzężenia są odwiedzane inaczej niż pozostałe węzły, ponieważ element nadrzędny (węzeł sprzężenia) tworzy SqlSelectStatement dla elementów podrzędnych, które mogą być używane.</span><span class="sxs-lookup"><span data-stu-id="b2301-260">In that sense, joins are visited differently from the rest of the nodes, as the parent (the join node) creates the SqlSelectStatement for the children to possibly use.</span></span>

<span data-ttu-id="b2301-261">Następnie przetwórz dane wejściowe pojedynczo.</span><span class="sxs-lookup"><span data-stu-id="b2301-261">Second, process the inputs one at a time.</span></span> <span data-ttu-id="b2301-262">Dla każdego danych wejściowych:</span><span class="sxs-lookup"><span data-stu-id="b2301-262">For each input:</span></span>

1. <span data-ttu-id="b2301-263">Przejdź do danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="b2301-263">Visit the input.</span></span>

2. <span data-ttu-id="b2301-264">Proces post w wyniku odwiedzania danych wejściowych przez wywołanie ProcessJoinInputResult, który jest odpowiedzialny za utrzymanie tabeli symboli po odwiedzeniu elementu podrzędnego wyrażenia sprzężenia i prawdopodobnie kończący SqlSelectStatement utworzony przez element podrzędny.</span><span class="sxs-lookup"><span data-stu-id="b2301-264">Post process the result of visiting the input by invoking ProcessJoinInputResult, which is responsible for maintaining the symbol table after visiting a child of a join expression and possibly finishing the SqlSelectStatement produced by the child.</span></span> <span data-ttu-id="b2301-265">Wynik dziecka może mieć jedną z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="b2301-265">The child's result could be one of the following:</span></span>

    - <span data-ttu-id="b2301-266">SqlSelectStatement różni się od elementu, do którego zostanie dodany element nadrzędny.</span><span class="sxs-lookup"><span data-stu-id="b2301-266">A SqlSelectStatement different from the one to which the parent will be added.</span></span> <span data-ttu-id="b2301-267">W takim przypadku może być konieczne ukończenie dodawania kolumn domyślnych.</span><span class="sxs-lookup"><span data-stu-id="b2301-267">In such case, it may need to be completed by adding default columns.</span></span> <span data-ttu-id="b2301-268">Jeśli dane wejściowe były przyłączone, należy utworzyć nowy symbol sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="b2301-268">If the input was a Join, you need to create a new join symbol.</span></span> <span data-ttu-id="b2301-269">W przeciwnym razie Utwórz symbol normalny.</span><span class="sxs-lookup"><span data-stu-id="b2301-269">Otherwise, create a normal symbol.</span></span>

    - <span data-ttu-id="b2301-270">Zakres (na przykład DbScanExpression), w którym to przypadku jest po prostu dodawany do listy danych wejściowych SqlSelectStatement elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="b2301-270">An extent (a DbScanExpression, for example), in which case it is simply added to the list of inputs of the parent’s SqlSelectStatement.</span></span>

    - <span data-ttu-id="b2301-271">To nie jest SqlSelectStatement, w którym to przypadku jest opakowany w nawiasy klamrowe.</span><span class="sxs-lookup"><span data-stu-id="b2301-271">Not a SqlSelectStatement, in which case it is wrapped with brackets.</span></span>

    - <span data-ttu-id="b2301-272">Ten sam SqlSelectStatement, do którego zostanie dodany element nadrzędny.</span><span class="sxs-lookup"><span data-stu-id="b2301-272">The same SqlSelectStatement to which the parent is added.</span></span> <span data-ttu-id="b2301-273">W takim przypadku Symbole znajdujące się na liście FromExtents muszą zostać zastąpione jednym nowym JoinSymbol, reprezentującym je wszystkie.</span><span class="sxs-lookup"><span data-stu-id="b2301-273">In such case, the symbols in the FromExtents list need to be replaced with a single new JoinSymbol representing them all.</span></span>

    - <span data-ttu-id="b2301-274">W pierwszych trzech przypadkach AddFromSymbol jest wywoływana w celu dodania klauzuli AS i zaktualizowania tabeli symboli.</span><span class="sxs-lookup"><span data-stu-id="b2301-274">For the first three cases, AddFromSymbol is called to add the AS clause, and update the symbol table.</span></span>

<span data-ttu-id="b2301-275">Trzeci, warunek sprzężenia (jeśli istnieje) jest odwiedzany.</span><span class="sxs-lookup"><span data-stu-id="b2301-275">Third, the join condition (if any) is visited.</span></span>

### <a name="set-operations"></a><span data-ttu-id="b2301-276">Operacje na zestawie</span><span class="sxs-lookup"><span data-stu-id="b2301-276">Set Operations</span></span>

<span data-ttu-id="b2301-277">Zestawy Operations DbUnionAllExpression, wyrażenia DbExceptExpression i DbIntersectExpression są przetwarzane przez metodę VisitSetOpExpression.</span><span class="sxs-lookup"><span data-stu-id="b2301-277">The set operations DbUnionAllExpression, DbExceptExpression, and DbIntersectExpression are processed by the method VisitSetOpExpression.</span></span> <span data-ttu-id="b2301-278">Tworzy element SqlBuilder kształtu</span><span class="sxs-lookup"><span data-stu-id="b2301-278">It creates a SqlBuilder of the shape</span></span>

```xml
<leftSqlSelectStatement> <setOp> <rightSqlSelectStatement>
```

<span data-ttu-id="b2301-279">Gdzie \<leftSqlSelectStatement > i \<rightSqlSelectStatement > są SqlSelectStatements uzyskane przez odwiedzenie poszczególnych danych wejściowych, \<a setOp > jest odpowiednią operacją (Union All na przykład).</span><span class="sxs-lookup"><span data-stu-id="b2301-279">Where \<leftSqlSelectStatement> and \<rightSqlSelectStatement> are SqlSelectStatements obtained by visiting each of the inputs, and \<setOp> is the corresponding operation (UNION ALL for example).</span></span>

### <a name="dbscanexpression"></a><span data-ttu-id="b2301-280">DbScanExpression</span><span class="sxs-lookup"><span data-stu-id="b2301-280">DbScanExpression</span></span>

<span data-ttu-id="b2301-281">Jeśli jest odwiedzony w kontekście sprzężenia (jako dane wejściowe do sprzężenia, które jest lewym elementem podrzędnym innego sprzężenia), DbScanExpression zwraca element SqlBuilder z docelowym SQL dla odpowiadającego mu elementu docelowego, który jest wyrażeniem definiującym zapytanie, tabelę lub widok.</span><span class="sxs-lookup"><span data-stu-id="b2301-281">If visited in a join context (as an input to a join that is a left child of another join), DbScanExpression returns a SqlBuilder with the target SQL for the corresponding target, which is either a defining query, table, or a view.</span></span> <span data-ttu-id="b2301-282">W przeciwnym razie zostanie utworzona nowa SqlSelectStatement z ustawionym polem FROM, aby odpowiadała odpowiedniemu elementowi docelowemu.</span><span class="sxs-lookup"><span data-stu-id="b2301-282">Otherwise, a new SqlSelectStatement is created with the FROM field set to correspond to the corresponding target.</span></span>

### <a name="dbvariablereferenceexpression"></a><span data-ttu-id="b2301-283">DbVariableReferenceExpression</span><span class="sxs-lookup"><span data-stu-id="b2301-283">DbVariableReferenceExpression</span></span>

<span data-ttu-id="b2301-284">Odwiedzanie DbVariableReferenceExpression zwraca symbol odpowiadający temu wyrażeniu odwołania do zmiennej na podstawie wyszukiwania w tabeli symboli.</span><span class="sxs-lookup"><span data-stu-id="b2301-284">The visit of a DbVariableReferenceExpression returns the Symbol corresponding to that variable reference expression based on a look up in the symbol table.</span></span>

### <a name="dbpropertyexpression"></a><span data-ttu-id="b2301-285">DbPropertyExpression</span><span class="sxs-lookup"><span data-stu-id="b2301-285">DbPropertyExpression</span></span>

<span data-ttu-id="b2301-286">Spłaszczanie aliasów sprzężenia jest identyfikowane i przetwarzane podczas odwiedzania DbPropertyExpression.</span><span class="sxs-lookup"><span data-stu-id="b2301-286">Join alias flattening is identified and processed when visiting a DbPropertyExpression.</span></span>

<span data-ttu-id="b2301-287">Właściwość instance jest najpierw odwiedzana, a wynikiem jest symbol, JoinSymbol lub SymbolPair.</span><span class="sxs-lookup"><span data-stu-id="b2301-287">The Instance property is first visited and the result is a Symbol, a JoinSymbol, or a SymbolPair.</span></span> <span data-ttu-id="b2301-288">Poniżej przedstawiono sposób obsługi tych trzech przypadków:</span><span class="sxs-lookup"><span data-stu-id="b2301-288">Here is how these three cases are handled:</span></span>

- <span data-ttu-id="b2301-289">Jeśli zostanie zwrócona wartość JoinSymbol, niż jej Właściwość NameToExtent zawiera symbol dla wymaganej właściwości.</span><span class="sxs-lookup"><span data-stu-id="b2301-289">If a JoinSymbol is returned, than its NameToExtent property contains a symbol for the needed property.</span></span> <span data-ttu-id="b2301-290">Jeśli symbol sprzężenia reprezentuje zagnieżdżoną sprzężenie, Nowa para symboli jest zwracana z symbolem sprzężenia, aby śledzić symbol, który będzie używany jako alias wystąpienia, i symbol reprezentujący rzeczywistą właściwość w celu dodatkowego rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="b2301-290">If the join symbol represents a nested join, a new Symbol pair is returned with the join symbol to track the symbol that would be used as the instance alias, and the symbol representing the actual property for further resolving.</span></span>

- <span data-ttu-id="b2301-291">Jeśli SymbolPair jest zwracany, a część kolumny jest symbolem sprzężenia, zwracany jest symbol sprzężenia, ale teraz Właściwość Column zostanie zaktualizowana tak, aby wskazywała Właściwość reprezentowaną przez bieżące wyrażenie właściwości.</span><span class="sxs-lookup"><span data-stu-id="b2301-291">If a SymbolPair is returned and the Column part is a join symbol, a join symbol is again returned, but now the column property is updated to point to the property represented by the current property expression.</span></span> <span data-ttu-id="b2301-292">W przeciwnym razie element SqlBuilder jest zwracany ze źródłem SymbolPair jako alias i symbol dla bieżącej właściwości jako kolumnę.</span><span class="sxs-lookup"><span data-stu-id="b2301-292">Otherwise a SqlBuilder is returned with the SymbolPair source as the alias, and the symbol for the current property as the column.</span></span>

- <span data-ttu-id="b2301-293">Jeśli symbol jest zwracany, Metoda odwiedzania zwraca metodę SqlBuilder z tym wystąpieniem jako alias oraz nazwę właściwości jako nazwę kolumny.</span><span class="sxs-lookup"><span data-stu-id="b2301-293">If a Symbol is returned, the Visit method returns a SqlBuilder method with that instance as the alias, and the property name as column name.</span></span>

### <a name="dbnewinstanceexpression"></a><span data-ttu-id="b2301-294">DbNewInstanceExpression</span><span class="sxs-lookup"><span data-stu-id="b2301-294">DbNewInstanceExpression</span></span>

<span data-ttu-id="b2301-295">Gdy jest używana jako właściwość projekcji elementu DbProjectExpression, obiekt DbNewInstanceExpression tworzy listę oddzielonych przecinkami argumentów do reprezentowania prognozowanych kolumn.</span><span class="sxs-lookup"><span data-stu-id="b2301-295">When used as the Projection property of DbProjectExpression, DbNewInstanceExpression produces a comma-separated list of the arguments to represent the projected columns.</span></span>

<span data-ttu-id="b2301-296">Gdy obiekt DbNewInstanceExpression ma zwracany typ kolekcji i definiuje nową kolekcję wyrażeń dostarczonych jako argumenty, następujące trzy przypadki są obsługiwane osobno:</span><span class="sxs-lookup"><span data-stu-id="b2301-296">When DbNewInstanceExpression has a collection return type, and defines a new collection of the expressions provided as arguments, the following three cases are handled separately:</span></span>

- <span data-ttu-id="b2301-297">Jeśli obiekt DbNewInstanceExpression ma DbElementExpression jako jedyny argument, jest przetłumaczony w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="b2301-297">If DbNewInstanceExpression has DbElementExpression as the only argument, it is translated as follows:</span></span>

    ```
    NewInstance(Element(X)) =>  SELECT TOP 1 …FROM X
    ```

<span data-ttu-id="b2301-298">Jeśli obiekt DbNewInstanceExpression nie ma argumentów (reprezentuje pustą tabelę), obiekt DbNewInstanceExpression jest przetłumaczony na:</span><span class="sxs-lookup"><span data-stu-id="b2301-298">If DbNewInstanceExpression has no arguments (represents an empty table), DbNewInstanceExpression is translated into:</span></span>

```sql
SELECT CAST(NULL AS <primitiveType>) as X
FROM (SELECT 1) AS Y WHERE 1=0
```

<span data-ttu-id="b2301-299">W przeciwnym razie obiekt DbNewInstanceExpression tworzy element Union-All dla argumentów:</span><span class="sxs-lookup"><span data-stu-id="b2301-299">Otherwise DbNewInstanceExpression builds a union-all ladder of the arguments:</span></span>

```sql
SELECT <visit-result-arg1> as X
UNION ALL SELECT <visit-result-arg2> as X
UNION ALL …
UNION ALL SELECT <visit-result-argN> as X
```

### <a name="dbfunctionexpression"></a><span data-ttu-id="b2301-300">DbFunctionExpression</span><span class="sxs-lookup"><span data-stu-id="b2301-300">DbFunctionExpression</span></span>

<span data-ttu-id="b2301-301">Funkcje kanoniczne i wbudowane są przetwarzane w taki sam sposób: Jeśli potrzebują specjalnej obsługi (przecinanie (String) do LTRIM (RTRIM (String), na przykład, zostanie wywołana odpowiednia procedura obsługi.</span><span class="sxs-lookup"><span data-stu-id="b2301-301">Canonical and built-in functions are processed the same way: if they need special handling (TRIM(string) to  LTRIM(RTRIM(string), for example), the appropriate handler is invoked.</span></span> <span data-ttu-id="b2301-302">W przeciwnym razie są tłumaczone na FunctionName (arg1, arg2,..., argn).</span><span class="sxs-lookup"><span data-stu-id="b2301-302">Otherwise they are translated to FunctionName(arg1, arg2, ..., argn).</span></span>

<span data-ttu-id="b2301-303">Słowniki są używane do śledzenia, które funkcje potrzebują specjalnej obsługi i odpowiednich programów obsługi.</span><span class="sxs-lookup"><span data-stu-id="b2301-303">Dictionaries are used to keep track of which functions need special handling and their appropriate handlers.</span></span>

<span data-ttu-id="b2301-304">Funkcje zdefiniowane przez użytkownika są tłumaczone na przestrzeń Nazwname. FunctionName (arg1, arg2,..., argn).</span><span class="sxs-lookup"><span data-stu-id="b2301-304">User-defined functions are translated to NamespaceName.FunctionName(arg1, arg2, ..., argn).</span></span>

### <a name="dbelementexpression"></a><span data-ttu-id="b2301-305">DbElementExpression</span><span class="sxs-lookup"><span data-stu-id="b2301-305">DbElementExpression</span></span>

<span data-ttu-id="b2301-306">Metoda, która odwiedza DbElementExpression, jest wywoływana tylko do odwiedzania DbElementExpression, gdy jest używana do reprezentowania podzapytania skalarnego.</span><span class="sxs-lookup"><span data-stu-id="b2301-306">The method that visits DbElementExpression is only invoked for visiting a DbElementExpression when used to represent a scalar subquery.</span></span> <span data-ttu-id="b2301-307">W związku z tym DbElementExpression Wykonuje translację do kompletnego SqlSelectStatement i dodaje do niego nawiasy klamrowe.</span><span class="sxs-lookup"><span data-stu-id="b2301-307">Therefore, DbElementExpression translates into a complete SqlSelectStatement and adds brackets around it.</span></span>

### <a name="dbquantifierexpression"></a><span data-ttu-id="b2301-308">DbQuantifierExpression</span><span class="sxs-lookup"><span data-stu-id="b2301-308">DbQuantifierExpression</span></span>

<span data-ttu-id="b2301-309">W zależności od typu wyrażenia (dowolne lub wszystkie) DbQuantifierExpression jest przetłumaczony jako:</span><span class="sxs-lookup"><span data-stu-id="b2301-309">Depending on the expression type (Any or All), DbQuantifierExpression is translated it as:</span></span>

```
Any(input, x) => Exists(Filter(input,x))
All(input, x) => Not Exists(Filter(input, not(x))
```

### <a name="dbnotexpression"></a><span data-ttu-id="b2301-310">DbNotExpression</span><span class="sxs-lookup"><span data-stu-id="b2301-310">DbNotExpression</span></span>

<span data-ttu-id="b2301-311">W niektórych przypadkach można zwinąć tłumaczenie obiekt DbNotExpression z wyrażeniem wejściowym.</span><span class="sxs-lookup"><span data-stu-id="b2301-311">In some cases it is possible to collapse the translation of DbNotExpression with its input expression.</span></span> <span data-ttu-id="b2301-312">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="b2301-312">For example:</span></span>

```
Not(IsNull(a)) =>  "a IS NOT NULL"
Not(All(input, x) => Not (Not Exists(Filter(input, not(x))) => Exists(Filter(input, not(x))
```

<span data-ttu-id="b2301-313">Przyczyną jest to, że drugi zwinięty jest wykonywany, ponieważ podczas tłumaczenia DbQuantifierExpression typu all przez dostawcę wprowadzono nieefektywność.</span><span class="sxs-lookup"><span data-stu-id="b2301-313">The reason the second collapse is performed is because inefficiencies were introduced by the provider when translating DbQuantifierExpression of type All.</span></span> <span data-ttu-id="b2301-314">W tym celu Entity Framework nie mógł wykonać uproszczenia.</span><span class="sxs-lookup"><span data-stu-id="b2301-314">Thus the Entity Framework could not have done the simplification.</span></span>

### <a name="dbisemptyexpression"></a><span data-ttu-id="b2301-315">DbIsEmptyExpression</span><span class="sxs-lookup"><span data-stu-id="b2301-315">DbIsEmptyExpression</span></span>

<span data-ttu-id="b2301-316">DbIsEmptyExpression jest przetłumaczony jako:</span><span class="sxs-lookup"><span data-stu-id="b2301-316">DbIsEmptyExpression is translated as:</span></span>

```
IsEmpty(input) = Not Exists(input)
```

## <a name="second-phase-of-sql-generation-generating-the-string-command"></a><span data-ttu-id="b2301-317">Druga faza generowania kodu SQL: Generowanie ciągu polecenia</span><span class="sxs-lookup"><span data-stu-id="b2301-317">Second Phase of SQL Generation: Generating the String Command</span></span>

<span data-ttu-id="b2301-318">Podczas generowania ciągu polecenia SQL, SqlSelectStatement tworzy rzeczywiste aliasy dla symboli, które odnoszą się do błędu zmiany nazwy kolumny i zakresu aliasu.</span><span class="sxs-lookup"><span data-stu-id="b2301-318">When generating a string SQL command, the SqlSelectStatement produces actual aliases for the symbols, which addresses the issue of column name and extent alias renaming.</span></span>

<span data-ttu-id="b2301-319">Zmiana nazwy aliasu zakresu występuje podczas zapisywania obiektu SqlSelectStatement w ciągu.</span><span class="sxs-lookup"><span data-stu-id="b2301-319">Extent alias renaming occurs while writing the SqlSelectStatement object into a string.</span></span> <span data-ttu-id="b2301-320">Najpierw utwórz listę wszystkich aliasów używanych przez zakresy zewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="b2301-320">First create a list of all the aliases used by the outer extents.</span></span> <span data-ttu-id="b2301-321">Każdy symbol w FromExtents (lub AllJoinExtents, jeśli ma wartość inną niż null), otrzymuje nazwę, jeśli koliduje z dowolnym zakresem zewnętrznym.</span><span class="sxs-lookup"><span data-stu-id="b2301-321">Each symbol in the FromExtents (or AllJoinExtents if it is non-null), gets renamed if it collides with any of the outer extents.</span></span> <span data-ttu-id="b2301-322">Jeśli zmiana nazwy jest konieczna, nie będzie konfliktu z żadnym z zakresów zebranych w AllExtentNames.</span><span class="sxs-lookup"><span data-stu-id="b2301-322">If renaming is needed, it will not conflict with any of the extents collected in AllExtentNames.</span></span>

<span data-ttu-id="b2301-323">Zmiana nazwy kolumny występuje podczas zapisywania obiektu symbol w ciągu.</span><span class="sxs-lookup"><span data-stu-id="b2301-323">Column renaming occurs while writing a Symbol object to a string.</span></span> <span data-ttu-id="b2301-324">AddDefaultColumns w pierwszej fazie ustalił, czy nazwa określonego symbolu kolumny jest konieczna.</span><span class="sxs-lookup"><span data-stu-id="b2301-324">AddDefaultColumns in the first phase has determined if a certain column symbol has to be renamed.</span></span> <span data-ttu-id="b2301-325">W drugiej fazie tylko zmiana nazwy odbywa się w celu upewnienia się, że nazwa utworzona nie powoduje konfliktu z żadną nazwą używaną w AllColumnNames</span><span class="sxs-lookup"><span data-stu-id="b2301-325">In the second phase only the rename occurs making sure that the name produced does not conflict with any name used in AllColumnNames</span></span>

<span data-ttu-id="b2301-326">Aby utworzyć unikatowe nazwy zarówno dla aliasów zakresu, jak i dla \<kolumn, należy użyć existing_name > _N, gdzie n jest najmniejszym aliasem, który nie był jeszcze używany.</span><span class="sxs-lookup"><span data-stu-id="b2301-326">To produce unique names both for extent aliases and for columns, use \<existing_name>_n where n is the smallest alias that has not been used yet.</span></span> <span data-ttu-id="b2301-327">Globalna lista wszystkich aliasów zwiększa potrzebę operacji kaskadowych.</span><span class="sxs-lookup"><span data-stu-id="b2301-327">The global list of all aliases increases the need for cascading renames.</span></span>

## <a name="see-also"></a><span data-ttu-id="b2301-328">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b2301-328">See also</span></span>

- [<span data-ttu-id="b2301-329">Generowanie kodu SQL w dostawcy próbki</span><span class="sxs-lookup"><span data-stu-id="b2301-329">SQL Generation in the Sample Provider</span></span>](sql-generation-in-the-sample-provider.md)
