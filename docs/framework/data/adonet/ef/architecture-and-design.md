---
title: Architektury i projektu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bd738d39-00e2-4bab-b387-90aac1a014bd
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f0dcad5d6287d5399dac6cea38b10984781770f9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="architecture-and-design"></a><span data-ttu-id="e7280-102">Architektury i projektu</span><span class="sxs-lookup"><span data-stu-id="e7280-102">Architecture and Design</span></span>
<span data-ttu-id="e7280-103">W module generowania SQL w [dostawcy próbki](http://go.microsoft.com/fwlink/?LinkId=180616) jest zaimplementowany jako obiekt odwiedzający na drzewo wyrażenia, który reprezentuje drzewo poleceń.</span><span class="sxs-lookup"><span data-stu-id="e7280-103">The SQL generation module in the [Sample Provider](http://go.microsoft.com/fwlink/?LinkId=180616) is implemented as a visitor on the expression tree that represents the command tree.</span></span> <span data-ttu-id="e7280-104">Generowanie odbywa się w jednym przebiegu za pośrednictwem drzewa wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="e7280-104">The generation is done in a single pass over the expression tree.</span></span>  
  
 <span data-ttu-id="e7280-105">Węzły drzewa są przetwarzane od dołu w górę.</span><span class="sxs-lookup"><span data-stu-id="e7280-105">The nodes of the tree are processed from the bottom up.</span></span> <span data-ttu-id="e7280-106">Najpierw jest tworzony pośredni struktury: SqlSelectStatement lub SqlBuilder, zarówno ISqlFragment implementującej.</span><span class="sxs-lookup"><span data-stu-id="e7280-106">First, an intermediate structure is produced: SqlSelectStatement or SqlBuilder, both implementing ISqlFragment.</span></span> <span data-ttu-id="e7280-107">Następnie ciąg instrukcja SQL jest tworzony z tej struktury.</span><span class="sxs-lookup"><span data-stu-id="e7280-107">Next, the string SQL statement is produced from that structure.</span></span> <span data-ttu-id="e7280-108">Istnieją pośredniego struktury z dwóch powodów:</span><span class="sxs-lookup"><span data-stu-id="e7280-108">There are two reasons for the intermediate structure:</span></span>  
  
-   <span data-ttu-id="e7280-109">Logicznie instrukcję SQL SELECT jest wypełniana poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="e7280-109">Logically, a SQL SELECT statement is populated out of order.</span></span> <span data-ttu-id="e7280-110">Węzły, które uczestniczą w klauzuli FROM są odwiedzana węzłów, które uczestniczą w klauzuli WHERE, GROUP BY i klauzuli ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="e7280-110">The nodes that participate in the FROM clause are visited before the nodes that participate in the WHERE, GROUP BY, and the ORDER BY clause.</span></span>  
  
-   <span data-ttu-id="e7280-111">Aby zmienić nazwę aliasy, należy określić używane wszystkie aliasy, aby uniknąć kolizji podczas zmiany nazwy.</span><span class="sxs-lookup"><span data-stu-id="e7280-111">To rename aliases, you must identify all used aliases to avoid collisions during renaming.</span></span> <span data-ttu-id="e7280-112">Odroczenia możliwości zmiany nazwy w SqlBuilder, należy użyć obiektów Symbol do reprezentowania kolumny, które są kandydatów do zmiany nazwy.</span><span class="sxs-lookup"><span data-stu-id="e7280-112">To defer the renaming choices in SqlBuilder, use Symbol objects to represent the columns that are candidates for renaming.</span></span>  
  
 <span data-ttu-id="e7280-113">![Diagram](../../../../../docs/framework/data/adonet/ef/media/de1ca705-4f7c-4d2d-ace5-afefc6d3cefa.gif "de1ca705-4f7c-4d2d-ace5-afefc6d3cefa")</span><span class="sxs-lookup"><span data-stu-id="e7280-113">![Diagram](../../../../../docs/framework/data/adonet/ef/media/de1ca705-4f7c-4d2d-ace5-afefc6d3cefa.gif "de1ca705-4f7c-4d2d-ace5-afefc6d3cefa")</span></span>  
  
 <span data-ttu-id="e7280-114">W pierwszej fazie podczas odwiedzania drzewa wyrażenia wyrażenia są zgrupowane w SqlSelectStatements sprzężeń są spłaszczane i są spłaszczane aliasy sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="e7280-114">In the first phase, while visiting the expression tree, expressions are grouped into SqlSelectStatements, joins are flattened, and join aliases are flattened.</span></span> <span data-ttu-id="e7280-115">W trakcie tego przebiegu Symbol reprezentować kolumn ani aliasy wejściowych, które mogą zostać zmienione.</span><span class="sxs-lookup"><span data-stu-id="e7280-115">During this pass, Symbol objects represent columns or input aliases that may be renamed.</span></span>  
  
 <span data-ttu-id="e7280-116">W drugim etapie podczas produkowania rzeczywisty ciąg aliasy zostały zmienione.</span><span class="sxs-lookup"><span data-stu-id="e7280-116">In the second phase, while producing the actual string, aliases are renamed.</span></span>  
  
## <a name="data-structures"></a><span data-ttu-id="e7280-117">Struktury danych</span><span class="sxs-lookup"><span data-stu-id="e7280-117">Data Structures</span></span>  
 <span data-ttu-id="e7280-118">W tej sekcji omówiono typów używanych w [dostawcy próbki](http://go.microsoft.com/fwlink/?LinkId=180616) umożliwia tworzenie instrukcji SQL.</span><span class="sxs-lookup"><span data-stu-id="e7280-118">This section discusses the types used in the [Sample Provider](http://go.microsoft.com/fwlink/?LinkId=180616) that you use to build a SQL statement.</span></span>  
  
### <a name="isqlfragment"></a><span data-ttu-id="e7280-119">ISqlFragment</span><span class="sxs-lookup"><span data-stu-id="e7280-119">ISqlFragment</span></span>  
 <span data-ttu-id="e7280-120">W tej sekcji opisano klasy, które implementują interfejs ISqlFragment, który służy do dwóch celów:</span><span class="sxs-lookup"><span data-stu-id="e7280-120">This section covers the classes that implement the ISqlFragment interface, which serves two purposes:</span></span>  
  
-   <span data-ttu-id="e7280-121">Typowe typ zwracany dla wszystkich metod obiekt odwiedzający.</span><span class="sxs-lookup"><span data-stu-id="e7280-121">A common return type for all the visitor methods.</span></span>  
  
-   <span data-ttu-id="e7280-122">Zapewnia metody do zapisania ostatni ciąg SQL.</span><span class="sxs-lookup"><span data-stu-id="e7280-122">Gives a method to write the final SQL string.</span></span>  
  
```  
internal interface ISqlFragment {  
   void WriteSql(SqlWriter writer, SqlGenerator sqlGenerator);  
}  
```  
  
#### <a name="sqlbuilder"></a><span data-ttu-id="e7280-123">SqlBuilder</span><span class="sxs-lookup"><span data-stu-id="e7280-123">SqlBuilder</span></span>  
 <span data-ttu-id="e7280-124">SqlBuilder to urządzenie zbierania końcowego ciągu SQL, podobnie jak StringBuilder.</span><span class="sxs-lookup"><span data-stu-id="e7280-124">SqlBuilder is a gathering device for the final SQL string, similar to StringBuilder.</span></span> <span data-ttu-id="e7280-125">Składa się z ciągów, które tworzą końcowego SQL, wraz z ISqlFragments, które mogą być konwertowane na ciągi.</span><span class="sxs-lookup"><span data-stu-id="e7280-125">It consists of the strings that make up the final SQL, along with ISqlFragments that can be converted into strings.</span></span>  
  
```  
internal sealed class SqlBuilder : ISqlFragment {  
   public void Append(object s)  
   public void AppendLine()  
   public bool IsEmpty  
}  
```  
  
#### <a name="sqlselectstatement"></a><span data-ttu-id="e7280-126">SqlSelectStatement</span><span class="sxs-lookup"><span data-stu-id="e7280-126">SqlSelectStatement</span></span>  
 <span data-ttu-id="e7280-127">SqlSelectStatement reprezentuje canonical instrukcję SQL SELECT kształtu "Wybierz...</span><span class="sxs-lookup"><span data-stu-id="e7280-127">SqlSelectStatement represents a canonical SQL SELECT statement of the shape "SELECT …</span></span> <span data-ttu-id="e7280-128">Z...</span><span class="sxs-lookup"><span data-stu-id="e7280-128">FROM  ..</span></span> <span data-ttu-id="e7280-129">GDZIE...</span><span class="sxs-lookup"><span data-stu-id="e7280-129">WHERE …</span></span> <span data-ttu-id="e7280-130">GRUPUJ WEDŁUG...</span><span class="sxs-lookup"><span data-stu-id="e7280-130">GROUP BY …</span></span> <span data-ttu-id="e7280-131">ORDER BY".</span><span class="sxs-lookup"><span data-stu-id="e7280-131">ORDER BY".</span></span>  
  
 <span data-ttu-id="e7280-132">Każdy klauzul SQL jest reprezentowany przez StringBuilder.</span><span class="sxs-lookup"><span data-stu-id="e7280-132">Each of the SQL clauses is represented by a StringBuilder.</span></span> <span data-ttu-id="e7280-133">Ponadto śledzi, czy określono Distinct oraz czy instrukcja jest najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="e7280-133">In addition, it tracks whether Distinct has been specified and whether the statement is topmost.</span></span> <span data-ttu-id="e7280-134">Jeśli instrukcja nie jest najwyższego poziomu, w klauzuli ORDER BY zostanie pominięty, chyba że instrukcja ma również klauzuli TOP.</span><span class="sxs-lookup"><span data-stu-id="e7280-134">If the statement is not topmost, the ORDER BY clause is omitted unless the statement also has a TOP clause.</span></span>  
  
 <span data-ttu-id="e7280-135">FromExtents zawiera listę danych wejściowych dla instrukcji SELECT.</span><span class="sxs-lookup"><span data-stu-id="e7280-135">FromExtents contains the list of inputs for the SELECT statement.</span></span> <span data-ttu-id="e7280-136">W tym zazwyczaj jest tylko jeden element.</span><span class="sxs-lookup"><span data-stu-id="e7280-136">There is usually just one element in this.</span></span> <span data-ttu-id="e7280-137">Instrukcji "SELECT" dla sprzężeń tymczasowo może mieć więcej niż jeden element.</span><span class="sxs-lookup"><span data-stu-id="e7280-137">SELECT statements for joins may temporarily have more than one element.</span></span>  
  
 <span data-ttu-id="e7280-138">Jeśli instrukcja SELECT jest tworzony przez węzeł sprzężenia, SqlSelectStatement przechowuje listę wszystkie zakresy, które zostały spłaszczone sprzężenia w AllJoinExtents.</span><span class="sxs-lookup"><span data-stu-id="e7280-138">If the SELECT statement is created by a Join node, SqlSelectStatement maintains a list of all the extents that have been flattened in the join in AllJoinExtents.</span></span> <span data-ttu-id="e7280-139">OuterExtents reprezentuje zewnętrznych odwołań SqlSelectStatement i służy do zmiany nazwy alias wejściowy.</span><span class="sxs-lookup"><span data-stu-id="e7280-139">OuterExtents represents outer references of the SqlSelectStatement and is used for input alias renaming.</span></span>  
  
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
  
#### <a name="topclause"></a><span data-ttu-id="e7280-140">TopClause</span><span class="sxs-lookup"><span data-stu-id="e7280-140">TopClause</span></span>  
 <span data-ttu-id="e7280-141">TopClause reprezentuje wyrażenia TOP w SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="e7280-141">TopClause represents the TOP expression in a SqlSelectStatement.</span></span> <span data-ttu-id="e7280-142">Właściwość TopCount wskazuje, ile GÓRNYCH wierszy powinna być zaznaczona.</span><span class="sxs-lookup"><span data-stu-id="e7280-142">The TopCount property indicates how many TOP rows should be selected.</span></span>  <span data-ttu-id="e7280-143">Jeśli WithTies ma wartość true, TopClause został skompilowany z DbLimitExpession.</span><span class="sxs-lookup"><span data-stu-id="e7280-143">When WithTies is true, the TopClause was built from a DbLimitExpession.</span></span>  
  
```  
class TopClause : ISqlFragment {  
   internal bool WithTies {get}  
   internal ISqlFragment TopCount {get}  
   internal TopClause(ISqlFragment topCount, bool withTies)  
   internal TopClause(int topCount, bool withTies)  
}  
```  
  
### <a name="symbols"></a><span data-ttu-id="e7280-144">Symbole</span><span class="sxs-lookup"><span data-stu-id="e7280-144">Symbols</span></span>  
 <span data-ttu-id="e7280-145">Klasy związane z symboli i tabeli symboli wykonać alias wejściowy zmiana nazwy, spłaszczanie alias sprzężenia i zmiana nazwy aliasu kolumny.</span><span class="sxs-lookup"><span data-stu-id="e7280-145">The Symbol-related classes and the symbol table perform input alias renaming, join alias flattening, and column alias renaming.</span></span>  
  
 <span data-ttu-id="e7280-146">Klasa Symbol reprezentuje stopniu, zagnieżdżonych instrukcji SELECT lub kolumny.</span><span class="sxs-lookup"><span data-stu-id="e7280-146">The Symbol class represents an extent, a nested SELECT statement, or a column.</span></span> <span data-ttu-id="e7280-147">Aby umożliwić zmianę po został użyty, a także zawiera dodatkowe informacje dotyczące artefaktu, który reprezentuje (na przykład typ) służy zamiast rzeczywistej alias.</span><span class="sxs-lookup"><span data-stu-id="e7280-147">It is used instead of an actual alias to allow for renaming after it has been used and it also carries additional information for the artifact it represents (like the type).</span></span>  
  
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
  
 <span data-ttu-id="e7280-148">Nazwa przechowuje oryginalny alias reprezentowanego zakresu, zagnieżdżonych instrukcji SELECT lub kolumny.</span><span class="sxs-lookup"><span data-stu-id="e7280-148">Name stores the original alias for the represented extent, nested SELECT statement, or a column.</span></span>  
  
 <span data-ttu-id="e7280-149">NewName przechowuje alias, który będzie używany w instrukcji SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="e7280-149">NewName stores the alias that will be used in the SQL SELECT statement.</span></span> <span data-ttu-id="e7280-150">Jest początkowo ustawiona nazwa i nazwę zmienić tylko w razie potrzeby podczas generowania ostatni ciąg zapytania.</span><span class="sxs-lookup"><span data-stu-id="e7280-150">It is originally set to Name, and only renamed if needed when generating the final string query.</span></span>  
  
 <span data-ttu-id="e7280-151">Typ jest przydatna dla symboli reprezentujący zakresy i zagnieżdżonych instrukcji "SELECT".</span><span class="sxs-lookup"><span data-stu-id="e7280-151">Type is only useful for symbols representing extents and nested SELECT statements.</span></span>  
  
#### <a name="symbolpair"></a><span data-ttu-id="e7280-152">SymbolPair</span><span class="sxs-lookup"><span data-stu-id="e7280-152">SymbolPair</span></span>  
 <span data-ttu-id="e7280-153">Klasa SymbolPair adresów spłaszczanie rekordów.</span><span class="sxs-lookup"><span data-stu-id="e7280-153">The SymbolPair class addresses record flattening.</span></span>  
  
 <span data-ttu-id="e7280-154">Należy wziąć pod uwagę wyrażenia właściwości D (v, "j3.j2.j1.a.x"), gdzie v jest VarRef, j1, j2, j3 są sprzężenia, ma zakres, a x kolumn.</span><span class="sxs-lookup"><span data-stu-id="e7280-154">Consider a property expression D(v, "j3.j2.j1.a.x") where v is a VarRef, j1, j2, j3 are joins, a is an extent, and x is a columns.</span></span>  
  
 <span data-ttu-id="e7280-155">Musi to być przetłumaczyć po pewnym czasie {j "}. {x "}.</span><span class="sxs-lookup"><span data-stu-id="e7280-155">This has to be translated eventually into {j'}.{x'}.</span></span> <span data-ttu-id="e7280-156">Pole źródła reprezentuje SqlStatement peryferyjnych, reprezentujący wyrażeniu join (Powiedz j2); jest to zawsze symbol sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="e7280-156">The source field represents the outermost SqlStatement, representing a join expression (say j2); this is always a Join symbol.</span></span> <span data-ttu-id="e7280-157">Pole kolumny są przenoszone z jednego symbolu sprzężenia do następnego dopóki zatrzymuje się na symbolu bez sprzężeń.</span><span class="sxs-lookup"><span data-stu-id="e7280-157">The column field moves from one join symbol to the next until it stops at a non-join symbol.</span></span> <span data-ttu-id="e7280-158">To jest zwracany, gdy użytkownik odwiedzi DbPropertyExpression, ale nigdy nie jest dodawane do SqlBuilder.</span><span class="sxs-lookup"><span data-stu-id="e7280-158">This is returned when visiting a DbPropertyExpression but is never added to a SqlBuilder.</span></span>  
  
```  
class SymbolPair : ISqlFragment {  
   public Symbol Source;  
   public Symbol Column;  
   public SymbolPair(Symbol source, Symbol column)  
}  
```  
  
#### <a name="joinsymbol"></a><span data-ttu-id="e7280-159">JoinSymbol</span><span class="sxs-lookup"><span data-stu-id="e7280-159">JoinSymbol</span></span>  
 <span data-ttu-id="e7280-160">Symbol sprzężenia to Symbol, który reprezentuje zagnieżdżonych instrukcji SELECT z sprzężenia lub sprzężenia danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="e7280-160">A Join symbol is a Symbol that represents a nested SELECT statement with a join or a join input.</span></span>  
  
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
  
 <span data-ttu-id="e7280-161">ColumnList reprezentuje na liście kolumn w klauzuli SELECT, jeśli ta ikona reprezentuje instrukcję SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="e7280-161">ColumnList represents the list of columns in the SELECT clause if this symbol represents a SQL SELECT statement.</span></span> <span data-ttu-id="e7280-162">ExtentList znajduje się lista zakresów w klauzuli SELECT.</span><span class="sxs-lookup"><span data-stu-id="e7280-162">ExtentList is the list of extents in the SELECT clause.</span></span> <span data-ttu-id="e7280-163">Jeśli sprzężenie ma wiele zakresów spłaszczone na najwyższym poziomie, FlattenedExtentList śledzi zakresy, aby upewnić się, że zakresie aliasy zostały prawidłowo zmienione.</span><span class="sxs-lookup"><span data-stu-id="e7280-163">If the join has multiple extents flattened at the top level, FlattenedExtentList tracks the extents to ensure that extent aliases are renamed correctly.</span></span>  
  
 <span data-ttu-id="e7280-164">NameToExtent ma wszystkie zakresy w ExtentList w formie słownika.</span><span class="sxs-lookup"><span data-stu-id="e7280-164">NameToExtent has all the extents in ExtentList as a dictionary.</span></span> <span data-ttu-id="e7280-165">IsNestedJoin służy do ustalenia, czy JoinSymbol jest symbol zwykłej sprzężenia, lub takie, które ma odpowiednie SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="e7280-165">IsNestedJoin is used to determine whether a JoinSymbol is an ordinary join symbol or one that has a corresponding SqlSelectStatement.</span></span>  
  
 <span data-ttu-id="e7280-166">Wszystkie listy są ustawić tylko raz i następnie używane do wyszukiwania lub wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="e7280-166">All the lists are set exactly once and then used for lookups or enumeration.</span></span>  
  
#### <a name="symboltable"></a><span data-ttu-id="e7280-167">SymbolTable</span><span class="sxs-lookup"><span data-stu-id="e7280-167">SymbolTable</span></span>  
 <span data-ttu-id="e7280-168">SymbolTable jest używany do rozpoznawania nazwy zmiennych do symboli.</span><span class="sxs-lookup"><span data-stu-id="e7280-168">SymbolTable is used to resolve variable names to Symbols.</span></span> <span data-ttu-id="e7280-169">SymbolTable jest implementowany jako stosu z nowy wpis dla każdego zakresu.</span><span class="sxs-lookup"><span data-stu-id="e7280-169">SymbolTable is implemented as a stack with a new entry for each scope.</span></span> <span data-ttu-id="e7280-170">Z góry stosu w dół wyszukiwanie wyszukiwań, aż do znalezienia wpis.</span><span class="sxs-lookup"><span data-stu-id="e7280-170">Lookups search from the top of the stack to the bottom until an entry is found.</span></span>  
  
```  
internal sealed class SymbolTable {  
   internal void EnterScope()  
   internal void ExitScope()  
   internal void Add(string name, Symbol value)  
   internal Symbol Lookup(string name)  
}  
```  
  
 <span data-ttu-id="e7280-171">Istnieje tylko jeden SymbolTable na jedno wystąpienie modułu generowanie kodu Sql.</span><span class="sxs-lookup"><span data-stu-id="e7280-171">There is only one SymbolTable per one instance of the Sql Generation module.</span></span> <span data-ttu-id="e7280-172">Wprowadzone zakresy i zakończył działanie dla każdego węzła relacyjne.</span><span class="sxs-lookup"><span data-stu-id="e7280-172">Scopes are entered and exited for each relational node.</span></span> <span data-ttu-id="e7280-173">Wszystkie symbole w zakresach wcześniejszych są widoczne w do nowszej zakresów, chyba że ukryty przez inne symbole o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="e7280-173">All symbols in earlier scopes are visible to later scopes unless hidden by other symbols with the same name.</span></span>  
  
### <a name="global-state-for-the-visitor"></a><span data-ttu-id="e7280-174">Stan globalny dla obiektu odwiedzającego</span><span class="sxs-lookup"><span data-stu-id="e7280-174">Global State for the Visitor</span></span>  
 <span data-ttu-id="e7280-175">Aby pomóc w zmienianie nazw aliasów i kolumn, utrzymywać listę wszystkich nazw kolumn (AllColumnNames) i aliasy zakresu (AllExtentNames), które zostały już użyte w pierwszym przekazywane za pośrednictwem drzewa zapytania.</span><span class="sxs-lookup"><span data-stu-id="e7280-175">To assist in renaming of aliases and columns, maintain a list of all the column names (AllColumnNames) and extent aliases (AllExtentNames) that have been used in the first pass over the query tree.</span></span>  <span data-ttu-id="e7280-176">Tabela symbol rozpoznawany jako nazwy zmiennych symboli.</span><span class="sxs-lookup"><span data-stu-id="e7280-176">The symbol table resolves variable names to Symbols.</span></span> <span data-ttu-id="e7280-177">IsVarRefSingle jest używana tylko na potrzeby weryfikacji nie jest bezwzględnie konieczne.</span><span class="sxs-lookup"><span data-stu-id="e7280-177">IsVarRefSingle is only used for verification purposes, it is not strictly necessary.</span></span>  
  
 <span data-ttu-id="e7280-178">Stosy dwóch używane za pośrednictwem CurrentSelectStatement i IsParentAJoin są używane do przekazania "Parametry" z elementu nadrzędnego do węzłów podrzędnych, ponieważ wzorzec odwiedzający nie zezwalają na przekazywanie parametrów.</span><span class="sxs-lookup"><span data-stu-id="e7280-178">The two stacks used via CurrentSelectStatement and IsParentAJoin are used to pass "parameters" from parent to child nodes, since the visitor pattern does not allow us to pass parameters.</span></span>  
  
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
  
## <a name="common-scenarios"></a><span data-ttu-id="e7280-179">Typowe scenariusze</span><span class="sxs-lookup"><span data-stu-id="e7280-179">Common Scenarios</span></span>  
 <span data-ttu-id="e7280-180">W tej sekcji omówiono typowe scenariusze dostawcy.</span><span class="sxs-lookup"><span data-stu-id="e7280-180">This section discusses common provider scenarios.</span></span>  
  
### <a name="grouping-expression-nodes-into-sql-statements"></a><span data-ttu-id="e7280-181">Grupowanie węzłów wyrażenie w instrukcji SQL</span><span class="sxs-lookup"><span data-stu-id="e7280-181">Grouping Expression Nodes into SQL Statements</span></span>  
 <span data-ttu-id="e7280-182">SqlSelectStatement jest tworzony po napotkaniu pierwszego węzła relacyjnych (zwykle w zakresie DbScanExpression) podczas odwiedzania drzewa od dołu w górę.</span><span class="sxs-lookup"><span data-stu-id="e7280-182">A SqlSelectStatement is created when the first relational node is encountered (typically a DbScanExpression extent) when visiting the tree from the bottom up.</span></span> <span data-ttu-id="e7280-183">Do tworzenia instrukcji SQL SELECT z jako kilku zagnieżdżone zapytania, jak to możliwe, łączny jako wiele z jego węzłów nadrzędnych, jak to możliwe, w tym SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="e7280-183">To produce a SQL SELECT statement with as few nested queries as possible, aggregate as many of its parent nodes as possible in that SqlSelectStatement.</span></span>  
  
 <span data-ttu-id="e7280-184">Decyzji, czy podany węzeł (relacyjne) można dodać do bieżącej SqlSelectStatement (jeden zwrócony podczas przeglądania danych wejściowych) lub nowe oświadczenie musi być uruchomiona jest obliczana przez metodę IsCompatible, a także od tego, co to jest już SqlSelectStatement, która jest zależna od węzły zostały poniżej Podany węzeł.</span><span class="sxs-lookup"><span data-stu-id="e7280-184">The decision of whether a given (relational) node can be added to the current SqlSelectStatement (the one returned when visiting the input) or if a new statement needs to be started is computed by the method IsCompatible and depends on what is already in the SqlSelectStatement, which depends on what nodes were below the given node.</span></span>  
  
 <span data-ttu-id="e7280-185">Zazwyczaj klauzul instrukcji SQL są oceniane po klauzulach, gdzie węzły są traktowane jako scalania nie są puste, nie można dodać do bieżącej instrukcji węzła.</span><span class="sxs-lookup"><span data-stu-id="e7280-185">Typically, if SQL statement clauses are evaluated after clauses where the nodes being considered for merging are not empty, the node cannot be added to the current statement.</span></span> <span data-ttu-id="e7280-186">Na przykład jeśli węzeł next jest filtr, tego węzła można zintegrować bieżącego SqlSelectStatement tylko wtedy, gdy są spełnione następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="e7280-186">For example, if the next node is a Filter, that node can be incorporated into the current SqlSelectStatement only if the following is true:</span></span>  
  
-   <span data-ttu-id="e7280-187">Wybierz OPCJĘ lista jest pusta.</span><span class="sxs-lookup"><span data-stu-id="e7280-187">The SELECT list is empty.</span></span> <span data-ttu-id="e7280-188">Jeśli lista wyboru nie jest pusta, lista wyboru wygenerowany za pomocą węzła poprzedzających filtr i predykatu może odwoływać się do kolumn utworzonego przez tej listy wyboru.</span><span class="sxs-lookup"><span data-stu-id="e7280-188">If the SELECT list is not empty, the select list was produced by a node preceding the filter and the predicate may refer to columns produced by that SELECT list.</span></span>  
  
-   <span data-ttu-id="e7280-189">GROUPBY jest pusta.</span><span class="sxs-lookup"><span data-stu-id="e7280-189">The GROUPBY is empty.</span></span> <span data-ttu-id="e7280-190">Jeśli GROUPBY nie jest pusta, Dodawanie filtru oznaczałoby filtrowania przed grupowania, który nie jest prawidłowa.</span><span class="sxs-lookup"><span data-stu-id="e7280-190">If the GROUPBY is not empty, adding the filter would mean filtering before grouping, which is not correct.</span></span>  
  
-   <span data-ttu-id="e7280-191">Klauzuli TOP jest pusta.</span><span class="sxs-lookup"><span data-stu-id="e7280-191">The TOP clause is empty.</span></span> <span data-ttu-id="e7280-192">Jeśli w klauzuli TOP nie jest pusta, Dodawanie filtru oznaczałoby filtrowania przed wykonaniem TOP, który nie jest prawidłowa.</span><span class="sxs-lookup"><span data-stu-id="e7280-192">If the TOP clause is not empty, adding the filter would mean filtering before doing TOP, which is not correct.</span></span>  
  
 <span data-ttu-id="e7280-193">Nie dotyczy węzłom nierelacyjnych DbConstantExpression lub wyrażenia arytmetyczne, ponieważ są one zawsze dołączane jako część istniejącego SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="e7280-193">This does not apply to non-relational nodes like DbConstantExpression or arithmetic expressions, because these are always included as part of an existing SqlSelectStatement.</span></span>  
  
 <span data-ttu-id="e7280-194">Ponadto gdy wystąpią korzeń drzewa sprzężenia (sprzężenia węzeł, który nie ma nadrzędnego sprzężenia), nowy SqlSelectStatement jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="e7280-194">Also, when encountering the root of join tree (a join node that does not have a join parent), a new SqlSelectStatement is started.</span></span> <span data-ttu-id="e7280-195">Wszystkie jego elementy podrzędne sprzężenia kręgosłupa po lewej stronie są agregowane w tym SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="e7280-195">All of its left spine join children are aggregated into that SqlSelectStatement.</span></span>  
  
 <span data-ttu-id="e7280-196">Zawsze, gdy nowy SqlSelectStatement jest uruchomiona, a bieżąca zostanie dodany do danych wejściowych, bieżący SqlSelectStatement może muszą być wykonane przez dodanie kolumny projekcji (klauzuli SELECT), jeśli jeszcze nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="e7280-196">Whenever a new SqlSelectStatement is started, and the current one is added to the input, the current SqlSelectStatement may need to be completed by adding projection columns (a SELECT clause) if one does not exist.</span></span> <span data-ttu-id="e7280-197">Można to zrobić za pomocą metody AddDefaultColumns, która analizuje FromExtents z SqlSelectStatement i dodaje wszystkie kolumny, które na liście zakresów reprezentowany przez FromExtents łączy w zakresie do listy kolumn, planowane.</span><span class="sxs-lookup"><span data-stu-id="e7280-197">This is done with the method AddDefaultColumns, which looks at the FromExtents of the SqlSelectStatement and adds all the columns that the list of extents represented by FromExtents brings in scope to the list of projected columns.</span></span> <span data-ttu-id="e7280-198">Tej operacji, ponieważ w tym momencie jest nieznany kolumny, które odwołują się w innych węzłach.</span><span class="sxs-lookup"><span data-stu-id="e7280-198">This is done, because at that point, it is unknown which columns are referenced by the other nodes.</span></span> <span data-ttu-id="e7280-199">To może być zoptymalizowana pod kątem tylko projektu kolumn, które później mogą być używane.</span><span class="sxs-lookup"><span data-stu-id="e7280-199">This can be optimized to only project the columns that can later be used.</span></span>  
  
### <a name="join-flattening"></a><span data-ttu-id="e7280-200">Dołącz spłaszczania</span><span class="sxs-lookup"><span data-stu-id="e7280-200">Join Flattening</span></span>  
 <span data-ttu-id="e7280-201">Właściwość IsParentAJoin pomaga ustalić, czy można spłaszczenia danego sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="e7280-201">The IsParentAJoin property helps determine whether a given join can be flattened.</span></span> <span data-ttu-id="e7280-202">W szczególności zwraca IsParentAJoin `true` tylko dla lewy element podrzędny sprzężenia i dla każdej DbScanExpression, który jest natychmiastowe wejście do sprzężenia, w którym to przypadku tego węzła podrzędnego ponownie używa tego samego SqlSelectStatement, który później użyty element nadrzędny.</span><span class="sxs-lookup"><span data-stu-id="e7280-202">In particular, IsParentAJoin returns `true` only for the left child of a join and for each DbScanExpression that is an immediate input to a join, in which case that child node reuses the same SqlSelectStatement that the parent would later use.</span></span> <span data-ttu-id="e7280-203">Aby uzyskać więcej informacji zobacz "Dołącz do wyrażenia".</span><span class="sxs-lookup"><span data-stu-id="e7280-203">For more information, see "Join Expressions".</span></span>  
  
### <a name="input-alias-redirecting"></a><span data-ttu-id="e7280-204">Wprowadź Alias przekierowania folderu</span><span class="sxs-lookup"><span data-stu-id="e7280-204">Input Alias Redirecting</span></span>  
 <span data-ttu-id="e7280-205">Alias wejściowy przekierowywanie odbywa się z tabelą symboli.</span><span class="sxs-lookup"><span data-stu-id="e7280-205">Input alias redirecting is accomplished with the symbol table.</span></span>  
  
 <span data-ttu-id="e7280-206">Aby wyjaśnić, przekierowywanie alias wejściowy, należy zapoznać się z pierwszym przykładzie w [generowania SQL z drzew poleceń — najlepsze praktyki](../../../../../docs/framework/data/adonet/ef/generating-sql-from-command-trees-best-practices.md).</span><span class="sxs-lookup"><span data-stu-id="e7280-206">To explain input alias redirecting, refer to the first example in [Generating SQL from Command Trees - Best Practices](../../../../../docs/framework/data/adonet/ef/generating-sql-from-command-trees-best-practices.md).</span></span>  <span data-ttu-id="e7280-207">Brak "" musiał zostać przekierowane na "b" w projekcji.</span><span class="sxs-lookup"><span data-stu-id="e7280-207">There "a" needed to be redirected to "b" in the projection.</span></span>  
  
 <span data-ttu-id="e7280-208">Gdy tworzony jest obiekt SqlSelectStatement, jakim jest danych wejściowych do węzła jest umieszczany we właściwości From SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="e7280-208">When a SqlSelectStatement object is created, the extent that is the input to the node is put in the From property of the SqlSelectStatement.</span></span> <span data-ttu-id="e7280-209">Symbol (< symbol_b >) jest tworzony na podstawie powiązania wejściowego name ("b") do reprezentowania w tym zakresie i "AS" + < symbol_b > jest dołączany do klauzuli From.</span><span class="sxs-lookup"><span data-stu-id="e7280-209">A Symbol (<symbol_b>) is created based on the input binding name ("b") to represent that extent and "AS  " +  <symbol_b> is appended to the From Clause.</span></span>  <span data-ttu-id="e7280-210">Symbol jest także dodawane do właściwości FromExtents.</span><span class="sxs-lookup"><span data-stu-id="e7280-210">The symbol is also added to the FromExtents property.</span></span>  
  
 <span data-ttu-id="e7280-211">Symbol jest także dodawane do tabeli symboli do połączenia nazwa powiązania wejściowego ("b", < symbol_b >).</span><span class="sxs-lookup"><span data-stu-id="e7280-211">The symbol is also added to the symbol table to link the input binding name to it ("b", <symbol_b>).</span></span>  
  
 <span data-ttu-id="e7280-212">Jeśli kolejne węzeł ponownie używa tego SqlSelectStatement, dodaje wpis do tabeli symboli do jego nazwę powiązania wejściowego łącza do tego symbolu.</span><span class="sxs-lookup"><span data-stu-id="e7280-212">If a subsequent node reuses that SqlSelectStatement, it adds an entry to the symbol table to link its input binding name to that symbol.</span></span> <span data-ttu-id="e7280-213">W naszym przykładzie spowoduje ponowne użycie SqlSelectStatement i Dodaj DbProjectExpression o nazwie powiązania wejściowego "a" ("," \< symbol_b >) do tabeli.</span><span class="sxs-lookup"><span data-stu-id="e7280-213">In our example, the DbProjectExpression with the input binding name of "a" would reuse the SqlSelectStatement and add ("a", \< symbol_b>) to the table.</span></span>  
  
 <span data-ttu-id="e7280-214">Jeśli wyrażenia odwoływać się do nazwy powiązania wejściowego węzła, który jest ponowne SqlSelectStatement, odwołanie zostanie rozwiązany, za pomocą tabeli symboli poprawne symbol przekierowane.</span><span class="sxs-lookup"><span data-stu-id="e7280-214">When expressions reference the input binding name of the node that is reusing the SqlSelectStatement, that reference is resolved using the symbol table to the correct redirected symbol.</span></span> <span data-ttu-id="e7280-215">Gdy "" z "a.x""" nie zostanie rozwiązany podczas odwiedzania reprezentujący DbVariableReferenceExpression "" it rozwiąże symbol < symbol_b >.</span><span class="sxs-lookup"><span data-stu-id="e7280-215">When "a" from "a.x" is resolved while visiting the DbVariableReferenceExpression representing "a" it will resolve to the Symbol <symbol_b>.</span></span>  
  
### <a name="join-alias-flattening"></a><span data-ttu-id="e7280-216">Dołącz spłaszczanie aliasu</span><span class="sxs-lookup"><span data-stu-id="e7280-216">Join Alias Flattening</span></span>  
 <span data-ttu-id="e7280-217">Spłaszczanie alias sprzężenia jest osiągana, gdy odwiedzający DbPropertyExpression zgodnie z opisem w sekcji zatytułowany DbPropertyExpression.</span><span class="sxs-lookup"><span data-stu-id="e7280-217">Join alias flattening is achieved when visiting a DbPropertyExpression as described in the section titled DbPropertyExpression.</span></span>  
  
### <a name="column-name-and-extent-alias-renaming"></a><span data-ttu-id="e7280-218">Nazwa kolumny i zakres Alias zmiana nazwy</span><span class="sxs-lookup"><span data-stu-id="e7280-218">Column Name and Extent Alias Renaming</span></span>  
 <span data-ttu-id="e7280-219">Wydanie nazwy kolumny oraz zmiana nazwy aliasu w zakresie zostanie rozwiązana przy użyciu symboli, które tylko pobrać zastępowane z aliasami w drugim etapie generowania opisane w sekcji drugiej fazy generowanie kodu SQL: generowanie polecenie String.</span><span class="sxs-lookup"><span data-stu-id="e7280-219">The issue of column name and extent alias renaming is addressed by using symbols that only get substituted with aliases in the second phase of the generation described in the section titled Second Phase of SQL Generation: Generating the String Command.</span></span>  
  
## <a name="first-phase-of-the-sql-generation-visiting-the-expression-tree"></a><span data-ttu-id="e7280-220">Pierwszą fazę generowanie kodu SQL: odwiedzający wyrażenie drzewa</span><span class="sxs-lookup"><span data-stu-id="e7280-220">First Phase of the SQL Generation: Visiting the Expression Tree</span></span>  
 <span data-ttu-id="e7280-221">W tej sekcji opisano pierwszą fazę generowanie kodu SQL, gdy jest tworzony reprezentujący wyrażenie, które odwiedzenia zapytania i pośredniego struktury, albo SqlSelectStatement lub SqlBuilder.</span><span class="sxs-lookup"><span data-stu-id="e7280-221">This section describes the first phase of SQL generation, when the expression representing the query is visited and an intermediate structure is produced, either a SqlSelectStatement or a SqlBuilder.</span></span>  
  
 <span data-ttu-id="e7280-222">W tej sekcji opisano zasady zaproszonych wyrażenie inny węzeł kategorii i szczegóły odwiedzający typy określonego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="e7280-222">This section describes the principles of visiting different expression node categories, and details of visiting specific expression types.</span></span>  
  
### <a name="relational-non-join-nodes"></a><span data-ttu-id="e7280-223">Relacyjne węzłów (bez sprzężeń)</span><span class="sxs-lookup"><span data-stu-id="e7280-223">Relational (Non-Join) Nodes</span></span>  
 <span data-ttu-id="e7280-224">Następujące typy wyrażeń obsługują węzłów z systemem innym niż sprzężenia:</span><span class="sxs-lookup"><span data-stu-id="e7280-224">The following expression types support non-join nodes:</span></span>  
  
-   <span data-ttu-id="e7280-225">DbDistinctExpression</span><span class="sxs-lookup"><span data-stu-id="e7280-225">DbDistinctExpression</span></span>  
  
-   <span data-ttu-id="e7280-226">DbFilterExpression</span><span class="sxs-lookup"><span data-stu-id="e7280-226">DbFilterExpression</span></span>  
  
-   <span data-ttu-id="e7280-227">DbGroupByExpression</span><span class="sxs-lookup"><span data-stu-id="e7280-227">DbGroupByExpression</span></span>  
  
-   <span data-ttu-id="e7280-228">DbLimitExpession</span><span class="sxs-lookup"><span data-stu-id="e7280-228">DbLimitExpession</span></span>  
  
-   <span data-ttu-id="e7280-229">DbProjectExpression</span><span class="sxs-lookup"><span data-stu-id="e7280-229">DbProjectExpression</span></span>  
  
-   <span data-ttu-id="e7280-230">DbSkipExpression</span><span class="sxs-lookup"><span data-stu-id="e7280-230">DbSkipExpression</span></span>  
  
-   <span data-ttu-id="e7280-231">DbSortExpression</span><span class="sxs-lookup"><span data-stu-id="e7280-231">DbSortExpression</span></span>  
  
 <span data-ttu-id="e7280-232">Te węzły odwiedzający jest zgodny ze wzorcem następujące:</span><span class="sxs-lookup"><span data-stu-id="e7280-232">Visiting these nodes follows the following pattern:</span></span>  
  
1.  <span data-ttu-id="e7280-233">Odwiedź relacyjne dane wejściowe i uzyskać SqlSelectStatement wynikowy.</span><span class="sxs-lookup"><span data-stu-id="e7280-233">Visit the relational input and get the resulting SqlSelectStatement.</span></span> <span data-ttu-id="e7280-234">Dane wejściowe relacyjne węzeł może być jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="e7280-234">The input to a relational node could be one of the following:</span></span>  
  
    -   <span data-ttu-id="e7280-235">Relacyjne węzła, w tym zakresie (DbScanExpression, na przykład).</span><span class="sxs-lookup"><span data-stu-id="e7280-235">A relational node, including an extent (a DbScanExpression, for example).</span></span> <span data-ttu-id="e7280-236">Węzeł takich odwiedzania zwraca SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="e7280-236">Visiting such a node returns a SqlSelectStatement.</span></span>  
  
    -   <span data-ttu-id="e7280-237">Operacja wyrażenie (UNION ALL, na przykład).</span><span class="sxs-lookup"><span data-stu-id="e7280-237">A set operation expression (UNION ALL, for example).</span></span> <span data-ttu-id="e7280-238">Wynik musi być ujęte w nawiasy i umieścić w klauzuli FROM SqlSelectStatement nowe.</span><span class="sxs-lookup"><span data-stu-id="e7280-238">The result has to be wrapped in brackets and put in the FROM clause of a new SqlSelectStatement.</span></span>  
  
2.  <span data-ttu-id="e7280-239">Sprawdź, czy bieżący węzeł może być dodany do SqlSelectStatement produkowane przez danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="e7280-239">Check whether the current node can be added to the SqlSelectStatement produced by the input.</span></span> <span data-ttu-id="e7280-240">Treścią wyrażenia grupowania w instrukcji SQL sekcji opisano to.</span><span class="sxs-lookup"><span data-stu-id="e7280-240">The section titled Grouping Expressions into SQL Statements describes this.</span></span> <span data-ttu-id="e7280-241">Jeśli nie,</span><span class="sxs-lookup"><span data-stu-id="e7280-241">If not,</span></span>  
  
    -   <span data-ttu-id="e7280-242">POP bieżącego obiektu SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="e7280-242">Pop the current SqlSelectStatement object.</span></span>  
  
    -   <span data-ttu-id="e7280-243">Utwórz nowy obiekt SqlSelectStatement i Dodaj popped SqlSelectStatement jako od nowego obiektu SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="e7280-243">Create a new SqlSelectStatement object and add the popped SqlSelectStatement as the FROM of the new SqlSelectStatement object.</span></span>  
  
    -   <span data-ttu-id="e7280-244">Umieść nowy obiekt na szczycie stosu.</span><span class="sxs-lookup"><span data-stu-id="e7280-244">Put the new object on top of the stack.</span></span>  
  
3.  <span data-ttu-id="e7280-245">Przekierowanie powiązania wyrażenie wejściowe poprawne symbol z danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="e7280-245">Redirect the input expression binding to the correct symbol from the input.</span></span> <span data-ttu-id="e7280-246">Te informacje są przechowywane w obiekcie SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="e7280-246">This information is maintained in the SqlSelectStatement object.</span></span>  
  
4.  <span data-ttu-id="e7280-247">Dodaj nowy zakres SymbolTable.</span><span class="sxs-lookup"><span data-stu-id="e7280-247">Add a new SymbolTable scope.</span></span>  
  
5.  <span data-ttu-id="e7280-248">Odwiedź stronę z systemem innym niż dane wejściowe część wyrażenia (na przykład projekcji i predykatu).</span><span class="sxs-lookup"><span data-stu-id="e7280-248">Visit the non-input part of the expression (for example, Projection and Predicate).</span></span>  
  
6.  <span data-ttu-id="e7280-249">Wyświetl wszystkie obiekty dodane do stosów globalnego.</span><span class="sxs-lookup"><span data-stu-id="e7280-249">Pop all the objects added to the global stacks.</span></span>  
  
 <span data-ttu-id="e7280-250">DbSkipExpression nie ma bezpośredniego odpowiednika w języku SQL.</span><span class="sxs-lookup"><span data-stu-id="e7280-250">DbSkipExpression not have a direct equivalent in SQL.</span></span> <span data-ttu-id="e7280-251">Logicznie jest przekształcana na:</span><span class="sxs-lookup"><span data-stu-id="e7280-251">Logically, it is translated into:</span></span>  
  
```  
SELECT Y.x1, Y.x2, ..., Y.xn  
FROM (  
   SELECT X.x1, X.x2, ..., X.xn, row_number() OVER (ORDER BY sk1, sk2, ...) AS [row_number]   
   FROM input as X   
   ) as Y  
WHERE Y.[row_number] > count   
ORDER BY sk1, sk2, ...  
```  
  
### <a name="join-expressions"></a><span data-ttu-id="e7280-252">Dołącz do wyrażeń</span><span class="sxs-lookup"><span data-stu-id="e7280-252">Join Expressions</span></span>  
 <span data-ttu-id="e7280-253">Poniżej są uznawane za wyrażeniach sprzężenia i są przetwarzane w typowy sposób, przy użyciu metody VisitJoinExpression:</span><span class="sxs-lookup"><span data-stu-id="e7280-253">The following are considered join expressions and they are processed in a common way, by the VisitJoinExpression method:</span></span>  
  
-   <span data-ttu-id="e7280-254">Metody DbApplyExpression</span><span class="sxs-lookup"><span data-stu-id="e7280-254">DbApplyExpression</span></span>  
  
-   <span data-ttu-id="e7280-255">DbJoinExpression</span><span class="sxs-lookup"><span data-stu-id="e7280-255">DbJoinExpression</span></span>  
  
-   <span data-ttu-id="e7280-256">Obiekt DbCrossJoinExpression</span><span class="sxs-lookup"><span data-stu-id="e7280-256">DbCrossJoinExpression</span></span>  
  
 <span data-ttu-id="e7280-257">Poniżej przedstawiono kroki, odwiedź stronę:</span><span class="sxs-lookup"><span data-stu-id="e7280-257">The following are the visit steps:</span></span>  
  
 <span data-ttu-id="e7280-258">Najpierw przed odwiedzenie elementów podrzędnych, IsParentAJoin jest wywoływana, aby sprawdzić, czy węzeł sprzężenia jest elementem podrzędnym sprzężenia wzdłuż lewej kręgosłupa.</span><span class="sxs-lookup"><span data-stu-id="e7280-258">First, before visiting the children, IsParentAJoin is invoked to check whether the join node is a child of a join along a left spine.</span></span> <span data-ttu-id="e7280-259">Jeśli zwraca wartość false, nowe SqlSelectStatement jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="e7280-259">If it returns false, a new SqlSelectStatement is started.</span></span> <span data-ttu-id="e7280-260">W tym sensie sprzężeń są odwiedzane inaczej z pozostałych węzłów, ponieważ element nadrzędny (węzeł sprzężenia) tworzy SqlSelectStatement dla dzieci, być może używać.</span><span class="sxs-lookup"><span data-stu-id="e7280-260">In that sense, joins are visited differently from the rest of the nodes, as the parent (the join node) creates the SqlSelectStatement for the children to possibly use.</span></span>  
  
 <span data-ttu-id="e7280-261">Po drugie przetworzyć wejść jeden naraz.</span><span class="sxs-lookup"><span data-stu-id="e7280-261">Second, process the inputs one at a time.</span></span> <span data-ttu-id="e7280-262">Dla każdego danych wejściowych:</span><span class="sxs-lookup"><span data-stu-id="e7280-262">For each input:</span></span>  
  
1.  <span data-ttu-id="e7280-263">Można znaleźć w danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="e7280-263">Visit the input.</span></span>  
  
2.  <span data-ttu-id="e7280-264">Proces POST wynik odwiedzający danych wejściowych, wywołując ProcessJoinInputResult, który jest odpowiedzialny za konserwację tabeli symboli po odwiedzając podrzędnych wyrażenia sprzężenia i prawdopodobnie Kończenie SqlSelectStatement utworzonego przez obiekt podrzędny.</span><span class="sxs-lookup"><span data-stu-id="e7280-264">Post process the result of visiting the input by invoking ProcessJoinInputResult, which is responsible for maintaining the symbol table after visiting a child of a join expression and possibly finishing the SqlSelectStatement produced by the child.</span></span> <span data-ttu-id="e7280-265">Wynik dziecka może być jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="e7280-265">The child's result could be one of the following:</span></span>  
  
    -   <span data-ttu-id="e7280-266">SqlSelectStatement niż ten, który zostanie dodany element nadrzędny.</span><span class="sxs-lookup"><span data-stu-id="e7280-266">A SqlSelectStatement different from the one to which the parent will be added.</span></span> <span data-ttu-id="e7280-267">W takim przypadku mogą musi zostać wykonane przez dodawanie kolumn.</span><span class="sxs-lookup"><span data-stu-id="e7280-267">In such case, it may need to be completed by adding default columns.</span></span> <span data-ttu-id="e7280-268">Jeśli wprowadzono sprzężenia, musisz utworzyć nowy symbol sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="e7280-268">If the input was a Join, you need to create a new join symbol.</span></span> <span data-ttu-id="e7280-269">W przeciwnym razie utwórz normalne symbolu.</span><span class="sxs-lookup"><span data-stu-id="e7280-269">Otherwise, create a normal symbol.</span></span>  
  
    -   <span data-ttu-id="e7280-270">Zakres (DbScanExpression, na przykład), w których przypadku wystarczy dodać go do listy składników elementu nadrzędnego obiektu SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="e7280-270">An extent (a DbScanExpression, for example), in which case it is simply added to the list of inputs of the parent’s SqlSelectStatement.</span></span>  
  
    -   <span data-ttu-id="e7280-271">Nie SqlSelectStatement, w którym przypadku, gdy jest on ujęte w nawiasy.</span><span class="sxs-lookup"><span data-stu-id="e7280-271">Not a SqlSelectStatement, in which case it is wrapped with brackets.</span></span>  
  
    -   <span data-ttu-id="e7280-272">Tym samym SqlSelectStatement, do którego jest dodawany element nadrzędny.</span><span class="sxs-lookup"><span data-stu-id="e7280-272">The same SqlSelectStatement to which the parent is added.</span></span> <span data-ttu-id="e7280-273">W takim przypadku symbole na liście FromExtents konieczne zastąpione pojedynczego JoinSymbol nowe reprezentujący je wszystkie.</span><span class="sxs-lookup"><span data-stu-id="e7280-273">In such case, the symbols in the FromExtents list need to be replaced with a single new JoinSymbol representing them all.</span></span>  
  
    -   <span data-ttu-id="e7280-274">W pierwszych trzech przypadkach AddFromSymbol nazywa się dodać klauzulę AS i zaktualizować tabeli symboli.</span><span class="sxs-lookup"><span data-stu-id="e7280-274">For the first three cases, AddFromSymbol is called to add the AS clause, and update the symbol table.</span></span>  
  
 <span data-ttu-id="e7280-275">Trzecie odwiedzenia warunek sprzężenia (jeśli istnieje).</span><span class="sxs-lookup"><span data-stu-id="e7280-275">Third, the join condition (if any) is visited.</span></span>  
  
### <a name="set-operations"></a><span data-ttu-id="e7280-276">Operacje na zestawie</span><span class="sxs-lookup"><span data-stu-id="e7280-276">Set Operations</span></span>  
 <span data-ttu-id="e7280-277">Operacje na zestawie DbUnionAllExpression wyrażenia DbExceptExpression i DbIntersectExpression są przetwarzane przez metodę VisitSetOpExpression.</span><span class="sxs-lookup"><span data-stu-id="e7280-277">The set operations DbUnionAllExpression, DbExceptExpression, and DbIntersectExpression are processed by the method VisitSetOpExpression.</span></span> <span data-ttu-id="e7280-278">Tworzy SqlBuilder kształtu</span><span class="sxs-lookup"><span data-stu-id="e7280-278">It creates a SqlBuilder of the shape</span></span>  
  
```xml  
<leftSqlSelectStatement> <setOp> <rightSqlSelectStatement>  
```  
  
 <span data-ttu-id="e7280-279">Gdzie \<leftSqlSelectStatement > i \<rightSqlSelectStatement > są SqlSelectStatements uzyskane wszystkich danych wejściowych, odwiedzając i \<setOp > jest odpowiadająca mu operacja (UNION ALL na przykład).</span><span class="sxs-lookup"><span data-stu-id="e7280-279">Where \<leftSqlSelectStatement> and \<rightSqlSelectStatement> are SqlSelectStatements obtained by visiting each of the inputs, and \<setOp> is the corresponding operation (UNION ALL for example).</span></span>  
  
### <a name="dbscanexpression"></a><span data-ttu-id="e7280-280">DbScanExpression</span><span class="sxs-lookup"><span data-stu-id="e7280-280">DbScanExpression</span></span>  
 <span data-ttu-id="e7280-281">Po odwiedzeniu w kontekście sprzężenia (jako dane wejściowe sprzężenia, które jest elementem podrzędnym lewego sprzężenia innego), DbScanExpression zwraca SqlBuilder z elementem docelowym SQL dla odpowiedniego obiektu docelowego, definiującego zapytania, tabeli lub widoku.</span><span class="sxs-lookup"><span data-stu-id="e7280-281">If visited in a join context (as an input to a join that is a left child of another join), DbScanExpression returns a SqlBuilder with the target SQL for the corresponding target, which is either a defining query, table, or a view.</span></span> <span data-ttu-id="e7280-282">W przeciwnym razie nowy SqlSelectStatement jest tworzony z pole od ustawioną odnoszą się do odpowiedniego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="e7280-282">Otherwise, a new SqlSelectStatement is created with the FROM field set to correspond to the corresponding target.</span></span>  
  
### <a name="dbvariablereferenceexpression"></a><span data-ttu-id="e7280-283">DbVariableReferenceExpression</span><span class="sxs-lookup"><span data-stu-id="e7280-283">DbVariableReferenceExpression</span></span>  
 <span data-ttu-id="e7280-284">Odwiedziny DbVariableReferenceExpression zwraca Symbol odpowiadający tego wyrażenia odwołanie do zmiennej, oparte na wyszukiwanie w tabeli symboli.</span><span class="sxs-lookup"><span data-stu-id="e7280-284">The visit of a DbVariableReferenceExpression returns the Symbol corresponding to that variable reference expression based on a look up in the symbol table.</span></span>  
  
### <a name="dbpropertyexpression"></a><span data-ttu-id="e7280-285">DbPropertyExpression</span><span class="sxs-lookup"><span data-stu-id="e7280-285">DbPropertyExpression</span></span>  
 <span data-ttu-id="e7280-286">Spłaszczanie alias sprzężenia jest identyfikowane i przetworzone podczas odwiedzania DbPropertyExpression.</span><span class="sxs-lookup"><span data-stu-id="e7280-286">Join alias flattening is identified and processed when visiting a DbPropertyExpression.</span></span>  
  
 <span data-ttu-id="e7280-287">Właściwości wystąpienia jest najpierw odwiedzi i wynik jest Symbol, JoinSymbol lub SymbolPair.</span><span class="sxs-lookup"><span data-stu-id="e7280-287">The Instance property is first visited and the result is a Symbol, a JoinSymbol, or a SymbolPair.</span></span> <span data-ttu-id="e7280-288">Poniżej przedstawiono sposób obsługi tych trzech przypadkach:</span><span class="sxs-lookup"><span data-stu-id="e7280-288">Here is how these three cases are handled:</span></span>  
  
-   <span data-ttu-id="e7280-289">Jeśli JoinSymbol jest zwracany, właściwość niż jego NameToExtent zawiera symbol wymagane właściwości.</span><span class="sxs-lookup"><span data-stu-id="e7280-289">If a JoinSymbol is returned, than its NameToExtent property contains a symbol for the needed property.</span></span> <span data-ttu-id="e7280-290">Jeśli symbol sprzężenia reprezentuje zagnieżdżonych sprzężenia, nową parę Symbol jest zwracany za symbolu sprzężenia, aby śledzić symbol, który będzie służyć jako alias wystąpienia i symbol reprezentujące właściwość dalszego rozpoznawania.</span><span class="sxs-lookup"><span data-stu-id="e7280-290">If the join symbol represents a nested join, a new Symbol pair is returned with the join symbol to track the symbol that would be used as the instance alias, and the symbol representing the actual property for further resolving.</span></span>  
  
-   <span data-ttu-id="e7280-291">Część kolumny jest symbol sprzężenia SymbolPair jest zwracany, zwracany jest ponownie symbol sprzężenia, ale teraz jako wartość właściwości column jest aktualizowane wskaż właściwości reprezentowanego przez wyrażenie bieżącej właściwości.</span><span class="sxs-lookup"><span data-stu-id="e7280-291">If a SymbolPair is returned and the Column part is a join symbol, a join symbol is again returned, but now the column property is updated to point to the property represented by the current property expression.</span></span> <span data-ttu-id="e7280-292">W przeciwnym razie SqlBuilder jest zwracana ze źródłem SymbolPair jako alias i symbol dla bieżącej właściwości jako kolumnę.</span><span class="sxs-lookup"><span data-stu-id="e7280-292">Otherwise a SqlBuilder is returned with the SymbolPair source as the alias, and the symbol for the current property as the column.</span></span>  
  
-   <span data-ttu-id="e7280-293">Jeśli Symbol jest zwracany, metoda odwiedziny zwraca SqlBuilder metodę z tego wystąpienia jako alias i nazwę właściwości jako nazwa kolumny.</span><span class="sxs-lookup"><span data-stu-id="e7280-293">If a Symbol is returned, the Visit method returns a SqlBuilder method with that instance as the alias, and the property name as column name.</span></span>  
  
### <a name="dbnewinstanceexpression"></a><span data-ttu-id="e7280-294">Obiekt DbNewInstanceExpression</span><span class="sxs-lookup"><span data-stu-id="e7280-294">DbNewInstanceExpression</span></span>  
 <span data-ttu-id="e7280-295">Gdy jest używany jako właściwość projekcji DbProjectExpression, DbNewInstanceExpression tworzy rozdzielana przecinkami lista argumentów do reprezentowania planowanego kolumn.</span><span class="sxs-lookup"><span data-stu-id="e7280-295">When used as the Projection property of DbProjectExpression, DbNewInstanceExpression produces a comma-separated list of the arguments to represent the projected columns.</span></span>  
  
 <span data-ttu-id="e7280-296">Gdy obiekt DbNewInstanceExpression ma typ zwracany kolekcji i definiuje nową kolekcję wyrażeń podane jako argumenty, oddzielnie obsługi następujących trzech przypadkach:</span><span class="sxs-lookup"><span data-stu-id="e7280-296">When DbNewInstanceExpression has a collection return type, and defines a new collection of the expressions provided as arguments, the following three cases are handled separately:</span></span>  
  
-   <span data-ttu-id="e7280-297">Jeśli DbNewInstanceExpression DbElementExpression jako jedynego argumentu, jest translacja w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e7280-297">If DbNewInstanceExpression has DbElementExpression as the only argument, it is translated as follows:</span></span>  
  
    ```  
    NewInstance(Element(X)) =>  SELECT TOP 1 …FROM X  
    ```  
  
 <span data-ttu-id="e7280-298">Jeśli obiekt DbNewInstanceExpression nie ma argumentów (reprezentuje pusta tabela), DbNewInstanceExpression jest przekształcana na:</span><span class="sxs-lookup"><span data-stu-id="e7280-298">If DbNewInstanceExpression has no arguments (represents an empty table), DbNewInstanceExpression is translated into:</span></span>  
  
```  
SELECT CAST(NULL AS <primitiveType>) as X  
FROM (SELECT 1) AS Y WHERE 1=0  
```  
  
 <span data-ttu-id="e7280-299">W przeciwnym razie DbNewInstanceExpression kompilacje drabinę union all, argumentów:</span><span class="sxs-lookup"><span data-stu-id="e7280-299">Otherwise DbNewInstanceExpression builds a union-all ladder of the arguments:</span></span>  
  
```  
SELECT <visit-result-arg1> as X  
UNION ALL SELECT <visit-result-arg2> as X  
UNION ALL …  
UNION ALL SELECT <visit-result-argN> as X  
```  
  
### <a name="dbfunctionexpression"></a><span data-ttu-id="e7280-300">Obiekcie DbFunctionExpression</span><span class="sxs-lookup"><span data-stu-id="e7280-300">DbFunctionExpression</span></span>  
 <span data-ttu-id="e7280-301">Canonical i wbudowane funkcje są przetwarzane tak samo: Jeśli potrzebna jest obsługa specjalnej (TRIM(string) do LTRIM(RTRIM(string), na przykład), odpowiedni program obsługi jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="e7280-301">Canonical and built-in functions are processed the same way: if they need special handling (TRIM(string) to  LTRIM(RTRIM(string), for example), the appropriate handler is invoked.</span></span> <span data-ttu-id="e7280-302">W przeciwnym razie są tłumaczone na FunctionName (arg1, arg2,... argn).</span><span class="sxs-lookup"><span data-stu-id="e7280-302">Otherwise they are translated to FunctionName(arg1, arg2, ..., argn).</span></span>  
  
 <span data-ttu-id="e7280-303">Słowniki są używane do śledzenia funkcje, które wymagają specjalnej obsługi i ich odpowiednie programy obsługi.</span><span class="sxs-lookup"><span data-stu-id="e7280-303">Dictionaries are used to keep track of which functions need special handling and their appropriate handlers.</span></span>  
  
 <span data-ttu-id="e7280-304">Funkcje zdefiniowane przez użytkownika są tanslated do NamespaceName.FunctionName (arg1, arg2,... argn).</span><span class="sxs-lookup"><span data-stu-id="e7280-304">User-defined functions are tanslated to NamespaceName.FunctionName(arg1, arg2, ..., argn).</span></span>  
  
### <a name="dbelementexpression"></a><span data-ttu-id="e7280-305">DbElementExpression</span><span class="sxs-lookup"><span data-stu-id="e7280-305">DbElementExpression</span></span>  
 <span data-ttu-id="e7280-306">Tylko metody, które odwiedza DbElementExpression jest wywołane odwiedzający DbElementExpression, gdy jest używany do reprezentowania skalarne podzapytania.</span><span class="sxs-lookup"><span data-stu-id="e7280-306">The method that visits DbElementExpression is only invoked for visiting a DbElementExpression when used to represent a scalar subquery.</span></span> <span data-ttu-id="e7280-307">W związku z tym DbElementExpression przekłada się na pełną SqlSelectStatement i dodaje je w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="e7280-307">Therefore, DbElementExpression translates into a complete SqlSelectStatement and adds brackets around it.</span></span>  
  
### <a name="dbquantifierexpression"></a><span data-ttu-id="e7280-308">DbQuantifierExpression</span><span class="sxs-lookup"><span data-stu-id="e7280-308">DbQuantifierExpression</span></span>  
 <span data-ttu-id="e7280-309">W zależności od typu wyrażenia (dowolne), jest translacja DbQuantifierExpression go jako:</span><span class="sxs-lookup"><span data-stu-id="e7280-309">Depending on the expression type (Any or All), DbQuantifierExpression is translated it as:</span></span>  
  
```  
Any(input, x) => Exists(Filter(input,x))  
All(input, x) => Not Exists(Filter(input, not(x))  
```  
  
### <a name="dbnotexpression"></a><span data-ttu-id="e7280-310">Obiekt DbNotExpression</span><span class="sxs-lookup"><span data-stu-id="e7280-310">DbNotExpression</span></span>  
 <span data-ttu-id="e7280-311">W niektórych przypadkach prawdopodobnie Zwiń tłumaczenia obiekt DbNotExpression z jego wyrażenie wejściowe.</span><span class="sxs-lookup"><span data-stu-id="e7280-311">In some cases it is possible to collapse the translation of DbNotExpression with its input expression.</span></span> <span data-ttu-id="e7280-312">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="e7280-312">For example:</span></span>  
  
```  
Not(IsNull(a)) =>  "a IS NOT NULL"  
Not(All(input, x) => Not (Not Exists(Filter(input, not(x))) => Exists(Filter(input, not(x))  
```  
  
 <span data-ttu-id="e7280-313">Zwiń drugi jest wykonywane przyczyną jest to ponieważ wydajność zostały wprowadzone przez dostawcę podczas tłumaczenia DbQuantifierExpression z type All.</span><span class="sxs-lookup"><span data-stu-id="e7280-313">The reason the second collapse is performed is because inefficiencies were introduced by the provider when translating DbQuantifierExpression of type All.</span></span> <span data-ttu-id="e7280-314">W związku z tym Entity Framework nie może być wykonana uproszczenia.</span><span class="sxs-lookup"><span data-stu-id="e7280-314">Thus the Entity Framework could not have done the simplification.</span></span>  
  
### <a name="dbisemptyexpression"></a><span data-ttu-id="e7280-315">DbIsEmptyExpression</span><span class="sxs-lookup"><span data-stu-id="e7280-315">DbIsEmptyExpression</span></span>  
 <span data-ttu-id="e7280-316">DbIsEmptyExpression jest translacja jako:</span><span class="sxs-lookup"><span data-stu-id="e7280-316">DbIsEmptyExpression is translated as:</span></span>  
  
```  
IsEmpty(inut) = Not Exists(input)  
```  
  
## <a name="second-phase-of-sql-generation-generating-the-string-command"></a><span data-ttu-id="e7280-317">Drugi etap generowanie kodu SQL: generowanie polecenie String</span><span class="sxs-lookup"><span data-stu-id="e7280-317">Second Phase of SQL Generation: Generating the String Command</span></span>  
 <span data-ttu-id="e7280-318">Podczas generowania ciąg polecenia SQL, SqlSelectStatement tworzy rzeczywiste aliasów dla symboli, którego dotyczy nazwy kolumny oraz zmiana nazwy aliasu w zakresie.</span><span class="sxs-lookup"><span data-stu-id="e7280-318">When generating a string SQL command, the SqlSelectStatement produces actual aliases for the symbols, which addresses the issue of column name and extent alias renaming.</span></span>  
  
 <span data-ttu-id="e7280-319">Zmiana nazwy aliasu zakres występuje podczas zapisu obiektu SqlSelectStatement na ciąg.</span><span class="sxs-lookup"><span data-stu-id="e7280-319">Extent alias renaming occurs while writing the SqlSelectStatement object into a string.</span></span> <span data-ttu-id="e7280-320">Najpierw utwórz listę zawierającą wszystkie aliasy, które są używane przez zewnętrzne zakresów.</span><span class="sxs-lookup"><span data-stu-id="e7280-320">First create a list of all the aliases used by the outer extents.</span></span> <span data-ttu-id="e7280-321">Każdy symbol w FromExtents (lub AllJoinExtents, jeśli jest inne niż null), pobiera zmieniono jego nazwę, jeśli powoduje ona konflikt z jednym z zakresów zewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="e7280-321">Each symbol in the FromExtents (or AllJoinExtents if it is non-null), gets renamed if it collides with any of the outer extents.</span></span> <span data-ttu-id="e7280-322">Jeśli zmiana nazwy jest potrzebny, nie spowoduje ona konflikt z jednym z zakresów zebrane w AllExtentNames.</span><span class="sxs-lookup"><span data-stu-id="e7280-322">If renaming is needed, it will not conflict with any of the extents collected in AllExtentNames.</span></span>  
  
 <span data-ttu-id="e7280-323">Zmiana nazwy kolumny występuje podczas zapisywania obiektu Symbol na ciąg.</span><span class="sxs-lookup"><span data-stu-id="e7280-323">Column renaming occurs while writing a Symbol object to a string.</span></span> <span data-ttu-id="e7280-324">AddDefaultColumns w pierwszej fazie określi, czy można zmienić nazwy symbolu kolumny.</span><span class="sxs-lookup"><span data-stu-id="e7280-324">AddDefaultColumns in the first phase has determined if a certain column symbol has to be renamed.</span></span> <span data-ttu-id="e7280-325">W drugim etapie występuje tylko zmiany nazwy, upewniając się, że nazwa wyprodukowanych nie powoduje konfliktu z dowolną nazwę używaną w AllColumnNames</span><span class="sxs-lookup"><span data-stu-id="e7280-325">In the second phase only the rename occurs making sure that the name produced does not conflict with any name used in AllColumnNames</span></span>  
  
 <span data-ttu-id="e7280-326">Do tworzenia unikatowych nazw zarówno dla zakresu aliasy i dla kolumn, należy użyć _n < existing_name >, gdzie n to najmniejsza alias, który nie został jeszcze użyty.</span><span class="sxs-lookup"><span data-stu-id="e7280-326">To produce unique names both for extent aliases and for columns, use <existing_name>_n where n is the smallest alias that has not been used yet.</span></span> <span data-ttu-id="e7280-327">Globalna lista wszystkie aliasy podkreśla konieczność zmiany nazw w kaskadowego.</span><span class="sxs-lookup"><span data-stu-id="e7280-327">The global list of all aliases increases the need for cascading renames.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7280-328">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e7280-328">See Also</span></span>  
 [<span data-ttu-id="e7280-329">Generowanie kodu SQL w dostawcy próbki</span><span class="sxs-lookup"><span data-stu-id="e7280-329">SQL Generation in the Sample Provider</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation-in-the-sample-provider.md)
