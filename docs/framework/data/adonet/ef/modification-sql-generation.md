---
title: Modyfikowanie generowania kodu SQL
ms.date: 03/30/2017
ms.assetid: 2188a39d-46ed-4a8b-906a-c9f15e6fefd1
ms.openlocfilehash: 94b6c3c97e8255db2dc4d72bae6c6c12905d9710
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854289"
---
# <a name="modification-sql-generation"></a><span data-ttu-id="45651-102">Modyfikowanie generowania kodu SQL</span><span class="sxs-lookup"><span data-stu-id="45651-102">Modification SQL Generation</span></span>

<span data-ttu-id="45651-103">W tej sekcji omówiono sposób tworzenia modyfikacji modułu generacji SQL dla dostawcy bazy danych zgodnej z programem (SQL: 1999).</span><span class="sxs-lookup"><span data-stu-id="45651-103">This section discusses how to develop a modification SQL generation module for your (SQL:1999-compliant database) provider.</span></span> <span data-ttu-id="45651-104">Ten moduł jest odpowiedzialny za tłumaczenie drzewa poleceń modyfikacji na odpowiednie instrukcje INSERT, UPDATE lub DELETE języka SQL.</span><span class="sxs-lookup"><span data-stu-id="45651-104">This module is responsible for translating a modification command tree into the appropriate SQL INSERT, UPDATE or DELETE statements.</span></span>

<span data-ttu-id="45651-105">Aby uzyskać informacje na temat generowania kodu SQL dla instrukcji SELECT, zobacz temat [Generowanie bazy danych SQL](sql-generation.md).</span><span class="sxs-lookup"><span data-stu-id="45651-105">For information about SQL generation for select statements, see [SQL Generation](sql-generation.md).</span></span>

## <a name="overview-of-modification-command-trees"></a><span data-ttu-id="45651-106">Przegląd drzew poleceń modyfikacji</span><span class="sxs-lookup"><span data-stu-id="45651-106">Overview of Modification Command Trees</span></span>

<span data-ttu-id="45651-107">Moduł generowania kodu SQL generuje instrukcje SQL dotyczące modyfikacji specyficzne dla bazy danych w oparciu o dane wejściowe DbModificationCommandTree.</span><span class="sxs-lookup"><span data-stu-id="45651-107">The modification SQL generation module generates database-specific modification SQL statements based on a given input DbModificationCommandTree.</span></span>

<span data-ttu-id="45651-108">DbModificationCommandTree to reprezentacja modelu obiektów przez operację modyfikacji DML (INSERT, Update lub Delete), która dziedziczy z DbCommandTree.</span><span class="sxs-lookup"><span data-stu-id="45651-108">A DbModificationCommandTree is an object model representation of a modification DML operation (an insert, an update, or a delete operation), inheriting from DbCommandTree.</span></span> <span data-ttu-id="45651-109">Istnieją trzy implementacje DbModificationCommandTree:</span><span class="sxs-lookup"><span data-stu-id="45651-109">There are three implementations of DbModificationCommandTree:</span></span>

- <span data-ttu-id="45651-110">DbInsertCommandTree</span><span class="sxs-lookup"><span data-stu-id="45651-110">DbInsertCommandTree</span></span>

- <span data-ttu-id="45651-111">DbUpdateCommandTree</span><span class="sxs-lookup"><span data-stu-id="45651-111">DbUpdateCommandTree</span></span>

- <span data-ttu-id="45651-112">DbDeleteCommandTree</span><span class="sxs-lookup"><span data-stu-id="45651-112">DbDeleteCommandTree</span></span>

<span data-ttu-id="45651-113">DbModificationCommandTree i jego implementacje, które są tworzone przez Entity Framework zawsze reprezentują pojedynczy wiersz operacji.</span><span class="sxs-lookup"><span data-stu-id="45651-113">DbModificationCommandTree and its implementations that are produced by the Entity Framework always represent a single row operation.</span></span> <span data-ttu-id="45651-114">W tej sekcji opisano te typy z ograniczeniami w .NET Framework w wersji 3,5.</span><span class="sxs-lookup"><span data-stu-id="45651-114">This section describes these types with their constraints in the .NET Framework version 3.5.</span></span>

<span data-ttu-id="45651-115">![Diagram](./media/558ba7b3-dd19-48d0-b91e-30a76415bf5f.gif "558ba7b3-dd19-48d0-b91e-30a76415bf5f")</span><span class="sxs-lookup"><span data-stu-id="45651-115">![Diagram](./media/558ba7b3-dd19-48d0-b91e-30a76415bf5f.gif "558ba7b3-dd19-48d0-b91e-30a76415bf5f")</span></span>

<span data-ttu-id="45651-116">DbModificationCommandTree ma właściwość docelową, która reprezentuje zestaw docelowy dla operacji modyfikacji.</span><span class="sxs-lookup"><span data-stu-id="45651-116">DbModificationCommandTree has a Target property that represents the target set for the modification operation.</span></span> <span data-ttu-id="45651-117">Właściwość wyrażenia elementu docelowego, która definiuje zestaw danych wejściowych, jest zawsze DbScanExpression.</span><span class="sxs-lookup"><span data-stu-id="45651-117">The Target’s Expression property, which defines the input set is always DbScanExpression.</span></span>  <span data-ttu-id="45651-118">DbScanExpression może reprezentować tabelę lub widok lub zestaw danych zdefiniowany za pomocą zapytania, jeśli właściwość metadanych "definiujące zapytanie" jego obiektu docelowego jest inna niż null.</span><span class="sxs-lookup"><span data-stu-id="45651-118">A DbScanExpression can either represent a table or a view, or a set of data defined with a query if the metadata property "Defining Query" of its Target is non-null.</span></span>

<span data-ttu-id="45651-119">DbScanExpression reprezentujący zapytanie może dotrzeć do dostawcy tylko jako element docelowy modyfikacji, jeśli zestaw został zdefiniowany przy użyciu zapytania definiującego w modelu, ale nie podano żadnej funkcji dla odpowiedniej operacji modyfikacji.</span><span class="sxs-lookup"><span data-stu-id="45651-119">A DbScanExpression that represents a query could only reach a provider as a target of modification if the set was defined by using a defining query in the model but no function was provided for the corresponding modification operation.</span></span> <span data-ttu-id="45651-120">Dostawcy mogą nie być w stanie obsłużyć takiego scenariusza (na przykład nie są).</span><span class="sxs-lookup"><span data-stu-id="45651-120">Providers may not be able to support such a scenario (SqlClient, for example, does not).</span></span>

<span data-ttu-id="45651-121">DbInsertCommandTree reprezentuje pojedynczy wiersz operacji wstawiania wyrażony jako drzewo poleceń.</span><span class="sxs-lookup"><span data-stu-id="45651-121">DbInsertCommandTree represents a single row insert operation expressed as a command tree.</span></span>

```csharp
public sealed class DbInsertCommandTree : DbModificationCommandTree {
   public IList<DbModificationClause> SetClauses { get }
   public DbExpression Returning { get }
}
```

<span data-ttu-id="45651-122">DbUpdateCommandTree reprezentuje jednowierszową operację aktualizacji wyrażoną jako drzewo poleceń.</span><span class="sxs-lookup"><span data-stu-id="45651-122">DbUpdateCommandTree represents a single-row update operation expressed as a command tree.</span></span>

<span data-ttu-id="45651-123">DbDeleteCommandTree reprezentuje operację usuwania pojedynczego wiersza wyrażoną jako drzewo poleceń.</span><span class="sxs-lookup"><span data-stu-id="45651-123">DbDeleteCommandTree represents a single row delete operation expressed as a command tree.</span></span>

### <a name="restrictions-on-modification-command-tree-properties"></a><span data-ttu-id="45651-124">Ograniczenia dotyczące właściwości drzewa poleceń modyfikacji</span><span class="sxs-lookup"><span data-stu-id="45651-124">Restrictions on Modification Command Tree Properties</span></span>

<span data-ttu-id="45651-125">Poniższe informacje i ograniczenia dotyczą właściwości drzewa poleceń modyfikacji.</span><span class="sxs-lookup"><span data-stu-id="45651-125">The following information and restrictions apply to the modification command tree properties.</span></span>

#### <a name="returning-in-dbinsertcommandtree-and-dbupdatecommandtree"></a><span data-ttu-id="45651-126">Zwracanie w DbInsertCommandTree i DbUpdateCommandTree</span><span class="sxs-lookup"><span data-stu-id="45651-126">Returning in DbInsertCommandTree and DbUpdateCommandTree</span></span>

<span data-ttu-id="45651-127">Gdy zwracana jest wartość inna niż null, funkcja Return wskazuje, że polecenie zwraca czytnik.</span><span class="sxs-lookup"><span data-stu-id="45651-127">When non-null, Returning indicates that the command returns a reader.</span></span> <span data-ttu-id="45651-128">W przeciwnym razie polecenie powinno zwrócić wartość skalarną wskazującą liczbę wierszy, których dotyczy (wstawiona lub zaktualizowana).</span><span class="sxs-lookup"><span data-stu-id="45651-128">Otherwise, the command should return a scalar value indicating the number of rows affected (inserted or updated).</span></span>

<span data-ttu-id="45651-129">Wartość zwracana określa rzutowanie wyników do zwrócenia na podstawie wstawionego lub zaktualizowanego wiersza.</span><span class="sxs-lookup"><span data-stu-id="45651-129">The Returning value specifies a projection of results to be returned based on the inserted or the updated row.</span></span> <span data-ttu-id="45651-130">Może być tylko typu obiekt DbNewInstanceExpression reprezentujący wiersz, a każdy z jego argumentów jest DbPropertyExpressionem nad DbVariableReferenceExpression reprezentującą odwołanie do obiektu docelowego odpowiedniego DbModificationCommandTree.</span><span class="sxs-lookup"><span data-stu-id="45651-130">It can only be of type DbNewInstanceExpression representing a row, with each of its arguments being a DbPropertyExpression over a DbVariableReferenceExpression representing a reference to the Target of the corresponding DbModificationCommandTree.</span></span> <span data-ttu-id="45651-131">Właściwości reprezentowane przez DbPropertyExpressions używane w zwracanej właściwości są zawsze przechowywane lub obliczane wartości.</span><span class="sxs-lookup"><span data-stu-id="45651-131">The properties represented by the DbPropertyExpressions used in the property Returning are always store generated or computed values.</span></span> <span data-ttu-id="45651-132">W DbInsertCommandTree zwraca nie ma wartości null, jeśli co najmniej jedna właściwość tabeli, w której wstawiany jest wiersz, jest określona jako magazyn wygenerowany lub obliczony (oznaczony jako StoreGeneratedPattern. Identity lub StoreGeneratedPattern. COMPUTE in SSDL).</span><span class="sxs-lookup"><span data-stu-id="45651-132">In DbInsertCommandTree, Returning is not null when at least one property of the table in which the row is being inserted is specified as store generated or computed (marked as StoreGeneratedPattern.Identity or StoreGeneratedPattern.Computed in the ssdl).</span></span> <span data-ttu-id="45651-133">W DbUpdateCommandTrees zwraca nie ma wartości null, jeśli co najmniej jedna właściwość tabeli, w której wiersz jest aktualizowany jest określony jako obliczony przez magazyn (oznaczony jako StoreGeneratedPattern. COMPUTE in SSDL).</span><span class="sxs-lookup"><span data-stu-id="45651-133">In DbUpdateCommandTrees, Returning is not null when at least one property of the table in which the row is being updated is specified as store computed (marked as StoreGeneratedPattern.Computed in the ssdl).</span></span>

#### <a name="setclauses-in-dbinsertcommandtree-and-dbupdatecommandtree"></a><span data-ttu-id="45651-134">Setklauzuls in DbInsertCommandTree i DbUpdateCommandTree</span><span class="sxs-lookup"><span data-stu-id="45651-134">SetClauses in DbInsertCommandTree and DbUpdateCommandTree</span></span>

<span data-ttu-id="45651-135">Setklauzule określa listę klauzul INSERT lub Update Set definiujących operację INSERT lub Update.</span><span class="sxs-lookup"><span data-stu-id="45651-135">SetClauses specifies the list of insert or update set clauses that define the insert or update operation.</span></span>

```
The elements of the list are specified as type DbModificationClause, which specifies a single clause in an insert or update modification operation. DbSetClause inherits from DbModificationClause and specifies the clause in a modification operation that sets the value of a property. Beginning in version 3.5 of the .NET Framework, all elements in SetClauses are of type SetClause.
```

<span data-ttu-id="45651-136">Właściwość określa właściwość, która ma zostać zaktualizowana.</span><span class="sxs-lookup"><span data-stu-id="45651-136">Property specifies the property that should be updated.</span></span> <span data-ttu-id="45651-137">Zawsze jest to DbPropertyExpression w DbVariableReferenceExpression, który reprezentuje odwołanie do elementu docelowego odpowiedniego DbModificationCommandTree.</span><span class="sxs-lookup"><span data-stu-id="45651-137">It is always a DbPropertyExpression over a DbVariableReferenceExpression, which represents a reference to the Target of the corresponding DbModificationCommandTree.</span></span>

<span data-ttu-id="45651-138">Wartość określa nową wartość, za pomocą której należy zaktualizować właściwość.</span><span class="sxs-lookup"><span data-stu-id="45651-138">Value specifies the new value with which to update the property.</span></span> <span data-ttu-id="45651-139">Jest to typ DbConstantExpression lub DbNullExpression.</span><span class="sxs-lookup"><span data-stu-id="45651-139">It is either of type DbConstantExpression or DbNullExpression.</span></span>

#### <a name="predicate-in-dbupdatecommandtree-and-dbdeletecommandtree"></a><span data-ttu-id="45651-140">Predykat w DbUpdateCommandTree i DbDeleteCommandTree</span><span class="sxs-lookup"><span data-stu-id="45651-140">Predicate in DbUpdateCommandTree and DbDeleteCommandTree</span></span>

<span data-ttu-id="45651-141">Predykat określa predykat używany do określenia, które elementy członkowskie kolekcji docelowej należy zaktualizować lub usunąć.</span><span class="sxs-lookup"><span data-stu-id="45651-141">Predicate specifies the predicate used to determine which members of the target collection should be updated or deleted.</span></span> <span data-ttu-id="45651-142">Jest to drzewo wyrażenia skompilowane z następującego podzestawu DbExpressions:</span><span class="sxs-lookup"><span data-stu-id="45651-142">It is an expression tree built of the following subset of DbExpressions:</span></span>

- <span data-ttu-id="45651-143">Obiekt DbComparisonExpression rodzaju równa się, z prawym elementem podrzędnym jest DbPropertyExpression, zgodnie z ograniczeniami poniżej, i z lewej strony podrzędnej DbConstantExpression.</span><span class="sxs-lookup"><span data-stu-id="45651-143">DbComparisonExpression of kind Equals, with the right child being a DbPropertyExpression as restricted below and the left child a DbConstantExpression.</span></span>

- <span data-ttu-id="45651-144">DbConstantExpression</span><span class="sxs-lookup"><span data-stu-id="45651-144">DbConstantExpression</span></span>

- <span data-ttu-id="45651-145">DbIsNullExpression na DbPropertyExpressionach zgodnie z ograniczeniami poniżej</span><span class="sxs-lookup"><span data-stu-id="45651-145">DbIsNullExpression over a DbPropertyExpression as restricted below</span></span>

- <span data-ttu-id="45651-146">DbPropertyExpression nad DbVariableReferenceExpression reprezentującą odwołanie do elementu docelowego odpowiedniego DbModificationCommandTree.</span><span class="sxs-lookup"><span data-stu-id="45651-146">DbPropertyExpression over a DbVariableReferenceExpression representing a reference to the Target of the corresponding DbModificationCommandTree.</span></span>

- <span data-ttu-id="45651-147">DbAndExpression</span><span class="sxs-lookup"><span data-stu-id="45651-147">DbAndExpression</span></span>

- <span data-ttu-id="45651-148">DbNotExpression</span><span class="sxs-lookup"><span data-stu-id="45651-148">DbNotExpression</span></span>

- <span data-ttu-id="45651-149">DbOrExpression</span><span class="sxs-lookup"><span data-stu-id="45651-149">DbOrExpression</span></span>

## <a name="modification-sql-generation-in-the-sample-provider"></a><span data-ttu-id="45651-150">Modyfikowanie generowania kodu SQL w przykładowym dostawcy</span><span class="sxs-lookup"><span data-stu-id="45651-150">Modification SQL Generation in the Sample Provider</span></span>

<span data-ttu-id="45651-151">[Przykładowy dostawca Entity Framework](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) ilustruje składniki dostawców danych ADO.NET, które obsługują Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="45651-151">The [Entity Framework Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) demonstrates the components of ADO.NET Data Providers that support the Entity Framework.</span></span> <span data-ttu-id="45651-152">Jest ona przeznaczona dla bazy danych SQL Server 2005 i jest zaimplementowana jako otoka na początku Dostawca danych System. Data. SqlClient ADO.NET 2,0.</span><span class="sxs-lookup"><span data-stu-id="45651-152">It targets a SQL Server 2005 database and is implemented as a wrapper on top of System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>

<span data-ttu-id="45651-153">W przypadku zmodyfikowania modułu generowania bazy danych SQL dostawcy przykładowego (znajdującego się w pliku SQL Generation\DmlSqlGenerator.cs) tworzony jest DbModificationCommandTree wejściowy i tworzona jest pojedyncza instrukcja SQL, po której występuje instrukcja SELECT zwracająca czytnik, jeśli został określony przez DbModificationCommandTree.</span><span class="sxs-lookup"><span data-stu-id="45651-153">The modification SQL generation module of the sample provider (located in the file SQL Generation\DmlSqlGenerator.cs) takes an input DbModificationCommandTree and produces a single modification SQL statement possibly followed by a select statement to return a reader if specified by the DbModificationCommandTree.</span></span> <span data-ttu-id="45651-154">Należy zauważyć, że docelowa baza danych SQL Server ma wpływ na kształt generowanych poleceń.</span><span class="sxs-lookup"><span data-stu-id="45651-154">Note that the shape of the commands generated is affected by the target SQL Server database.</span></span>

### <a name="helper-classes-expressiontranslator"></a><span data-ttu-id="45651-155">Klasy pomocnika: ExpressionTranslator</span><span class="sxs-lookup"><span data-stu-id="45651-155">Helper Classes: ExpressionTranslator</span></span>

<span data-ttu-id="45651-156">ExpressionTranslator służy jako wspólny lekki Translator dla wszystkich właściwości drzewa poleceń modyfikacji typu DbExpression.</span><span class="sxs-lookup"><span data-stu-id="45651-156">ExpressionTranslator serves as a common lightweight translator for all modification command tree properties of type DbExpression.</span></span> <span data-ttu-id="45651-157">Obsługuje translację tylko typów wyrażeń, do których właściwości drzewa poleceń modyfikacji są ograniczone i zostały skompilowane z uwzględnieniem określonych ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="45651-157">It supports translation of only the expression types to which the properties of the modification command tree are constrained and is built with the particular constraints in mind.</span></span>

<span data-ttu-id="45651-158">Poniższe informacje omawiają odwiedzanie określonych typów wyrażeń (węzły z prostymi tłumaczeniami są pomijane).</span><span class="sxs-lookup"><span data-stu-id="45651-158">The following information discusses visiting specific expression types (nodes with trivial translations are omitted).</span></span>

### <a name="dbcomparisonexpression"></a><span data-ttu-id="45651-159">DbComparisonExpression</span><span class="sxs-lookup"><span data-stu-id="45651-159">DbComparisonExpression</span></span>

<span data-ttu-id="45651-160">Gdy ExpressionTranslator jest konstruowany przy użyciu preserveMemberValues = true, a gdy stała z prawej strony jest DbConstantExpression (zamiast DbNullExpression), kojarzy z lewym operandem (DbPropertyExpressions) DbConstantExpression.</span><span class="sxs-lookup"><span data-stu-id="45651-160">When the ExpressionTranslator is constructed with preserveMemberValues = true, and when the constant to the right is a DbConstantExpression (instead of DbNullExpression), it associates the left operand (a DbPropertyExpressions) with that DbConstantExpression.</span></span> <span data-ttu-id="45651-161">Jest używany, jeśli instrukcja return SELECT musi zostać wygenerowana, aby zidentyfikować odnośny wiersz.</span><span class="sxs-lookup"><span data-stu-id="45651-161">That is used if a return Select statement needs to be generated to identify the affected row.</span></span>

### <a name="dbconstantexpression"></a><span data-ttu-id="45651-162">DbConstantExpression</span><span class="sxs-lookup"><span data-stu-id="45651-162">DbConstantExpression</span></span>

<span data-ttu-id="45651-163">Dla każdej odwiedzonej stałej jest tworzony parametr.</span><span class="sxs-lookup"><span data-stu-id="45651-163">For each visited constant a parameter is created.</span></span>

### <a name="dbpropertyexpression"></a><span data-ttu-id="45651-164">DbPropertyExpression</span><span class="sxs-lookup"><span data-stu-id="45651-164">DbPropertyExpression</span></span>

<span data-ttu-id="45651-165">Ponieważ wystąpienie elementu DbPropertyExpression zawsze reprezentuje tabelę wejściową, chyba że generacja utworzyła alias (który występuje tylko w scenariuszach aktualizacji, gdy jest używana zmienna tabeli), nie trzeba określać aliasu dla danych wejściowych; wartość domyślna tłumaczenia na nazwę właściwości.</span><span class="sxs-lookup"><span data-stu-id="45651-165">Given that the Instance of the DbPropertyExpression always represents the input table, unless the generation has created an alias (which only happens in update scenarios when a table variable is used), no alias needs to be specified for the input; the translation defaults to the property name.</span></span>

## <a name="generating-an-insert-sql-command"></a><span data-ttu-id="45651-166">Generowanie polecenia INSERT SQL</span><span class="sxs-lookup"><span data-stu-id="45651-166">Generating an Insert SQL Command</span></span>

<span data-ttu-id="45651-167">W przypadku danego DbInsertCommandTree w dostawcy przykładowym wygenerowanym poleceniem INSERT następuje jeden z dwóch szablonów wstawiania poniżej.</span><span class="sxs-lookup"><span data-stu-id="45651-167">For a given DbInsertCommandTree in the sample provider, the generated insert command follows one of the two insert templates below.</span></span>

<span data-ttu-id="45651-168">Pierwszy szablon zawiera polecenie do wykonania Wstaw dane wartości z listy setklauzuls i instrukcji SELECT do zwracania właściwości określonych we właściwości return dla wstawionego wiersza, jeśli właściwość zwracająca wartość nie jest równa null.</span><span class="sxs-lookup"><span data-stu-id="45651-168">The first template has a command to perform the insert given the values in the list of SetClauses, and a SELECT statement to return the properties specified in the Returning property for the inserted row if the Returning property was not null.</span></span> <span data-ttu-id="45651-169">Element predykatu "\@ @ROWCOUNT > 0" ma wartość true, jeśli wiersz został wstawiony.</span><span class="sxs-lookup"><span data-stu-id="45651-169">The predicate element "\@@ROWCOUNT > 0" is true if a row was inserted.</span></span> <span data-ttu-id="45651-170">Element predykatu "keyMemberI = keyValueI &#124; SCOPE_IDENTITY ()" przyjmuje kształt "keyMemberI = SCOPE_IDENTITY ()" tylko wtedy, gdy keyMemberI jest kluczem wygenerowanym przez magazyn, ponieważ SCOPE_IDENTITY () zwraca ostatnią wartość tożsamości wstawioną do tożsamości ( kolumna wygenerowana przez magazyn).</span><span class="sxs-lookup"><span data-stu-id="45651-170">The predicate element "keyMemberI =  keyValueI &#124; scope_identity()" takes the shape  "keyMemberI =  scope_identity()" only if keyMemberI is a store-generated key, because scope_identity() returns the last identity value inserted into an identity (store-generated) column.</span></span>

```sql
-- first insert Template
INSERT <target>   [ (setClauseProperty0, .. setClausePropertyN)]
VALUES (setClauseValue0, .. setClauseValueN) |  DEFAULT VALUES

[SELECT <returning>
 FROM <target>
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]
```

<span data-ttu-id="45651-171">Drugi szablon jest wymagany, jeśli INSERT określa Wstawianie wiersza, gdzie klucz podstawowy jest generowany przez magazyn, ale nie jest typem całkowitym i dlatego nie można go używać z SCOPE_IDENTITY ().</span><span class="sxs-lookup"><span data-stu-id="45651-171">The second template is needed if the insert specifies inserting a row where the primary key is store-generated but is not an integer type and therefore can't be used with scope_identity()).</span></span> <span data-ttu-id="45651-172">Jest również używany, jeśli istnieje klucz wygenerowany przez magazyn złożony.</span><span class="sxs-lookup"><span data-stu-id="45651-172">It is also used if there is a compound store-generated key.</span></span>

```sql
-- second insert template
DECLARE @generated_keys TABLE [(keyMember0, … keyMemberN)

INSERT <target>   [ (setClauseProperty0, .. setClausePropertyN)]
 OUTPUT inserted.KeyMember0, …, inserted.KeyMemberN INTO @generated_keys
 VALUES (setClauseValue0, .. setClauseValueN) |  DEFAULT VALUES

[SELECT <returning_over_t>
 FROM @generated_keys  AS g
JOIN <target> AS t ON g.KeyMember0 = t.KeyMember0 AND … g.KeyMemberN = t.KeyMemberN
 WHERE @@ROWCOUNT > 0
```

<span data-ttu-id="45651-173">Poniżej znajduje się przykład wykorzystujący model, który jest dołączony do przykładowego dostawcy.</span><span class="sxs-lookup"><span data-stu-id="45651-173">The following is an example that uses the model that is included with the sample provider.</span></span> <span data-ttu-id="45651-174">Generuje polecenie INSERT z DbInsertCommandTree.</span><span class="sxs-lookup"><span data-stu-id="45651-174">It generates an insert command from a DbInsertCommandTree.</span></span>

<span data-ttu-id="45651-175">Poniższy kod wstawia kategorię:</span><span class="sxs-lookup"><span data-stu-id="45651-175">The following code inserts a Category:</span></span>

```csharp
using (NorthwindEntities northwindContext = new NorthwindEntities()) {
   Category c = new Category();
   c.CategoryName = "Test Category";
   c.Description = "A new category for testing";
   northwindContext.AddObject("Categories", c);
   northwindContext.SaveChanges();
}
```

<span data-ttu-id="45651-176">Ten kod tworzy następujące drzewo poleceń, które jest przesyłane do dostawcy:</span><span class="sxs-lookup"><span data-stu-id="45651-176">This code produces the following command tree, which is passed to the provider:</span></span>

```
DbInsertCommandTree
|_Parameters
|_Target : 'target'
| |_Scan : dbo.Categories
|_SetClauses
| |_DbSetClause
| | |_Property
| | | |_Var(target).CategoryName
| | |_Value
| |   |_'Test Category'
| |_DbSetClause
| | |_Property
| | | |_Var(target).Description
| | |_Value
| |   |_'A new category for testing'
| |_DbSetClause
|   |_Property
|   | |_Var(target).Picture
|   |_Value
|     |_null
|_Returning
  |_NewInstance : Record['CategoryID'=Edm.Int32]
    |_Column : 'CategoryID'
      |_Var(target).CategoryID
```

<span data-ttu-id="45651-177">Poleceniem Store tworzonym przez przykładowego dostawcę jest następująca instrukcja SQL:</span><span class="sxs-lookup"><span data-stu-id="45651-177">The store command that the sample provider produces is the following SQL statement:</span></span>

```sql
insert [dbo].[Categories]([CategoryName], [Description], [Picture])
values (@p0, @p1, null)
select [CategoryID]
from [dbo].[Categories]
where @@ROWCOUNT > 0 and [CategoryID] = scope_identity()
```

## <a name="generating-an-update-sql-command"></a><span data-ttu-id="45651-178">Generowanie polecenia Update SQL</span><span class="sxs-lookup"><span data-stu-id="45651-178">Generating an Update SQL Command</span></span>

<span data-ttu-id="45651-179">Dla danego DbUpdateCommandTree generowane polecenie Update jest oparte na następującym szablonie:</span><span class="sxs-lookup"><span data-stu-id="45651-179">For a given DbUpdateCommandTree, the generated update command is based on the following template:</span></span>

```sql
-- UPDATE Template
UPDATE <target>
SET setClauseProperty0 = setClauseValue0, .. setClausePropertyN = setClauseValueN  | @i = 0
WHERE <predicate>

[SELECT <returning>
 FROM <target>
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]
```

<span data-ttu-id="45651-180">Klauzula SET ma fałszywą klauzulę Set ("@i = 0") tylko wtedy, gdy nie określono żadnych klauzul Set.</span><span class="sxs-lookup"><span data-stu-id="45651-180">The set clause has the fake set clause ("@i = 0") only if no set clauses are specified.</span></span> <span data-ttu-id="45651-181">Ma to na celu upewnienie się, że wszystkie kolumny obliczane przez magazyn są ponownie obliczane.</span><span class="sxs-lookup"><span data-stu-id="45651-181">This is to ensure that any store-computed columns are recomputed.</span></span>

<span data-ttu-id="45651-182">Tylko wtedy, gdy właściwość zwracająca nie ma wartości null, generowana jest instrukcja SELECT zwracająca właściwości określone we właściwości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="45651-182">Only if the Returning property is not null, a select statement is generated to return the properties specified in the Returning property.</span></span>

<span data-ttu-id="45651-183">W poniższym przykładzie zastosowano model, który jest dołączony do przykładowego dostawcy w celu wygenerowania polecenia Update.</span><span class="sxs-lookup"><span data-stu-id="45651-183">The following example uses the model that is included with the sample provider to generate an update command.</span></span>

<span data-ttu-id="45651-184">Następujący kod użytkownika aktualizuje kategorię:</span><span class="sxs-lookup"><span data-stu-id="45651-184">The following user code updates a Category:</span></span>

```csharp
using (NorthwindEntities northwindContext = new NorthwindEntities()) {
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "Test Category").First();
   c.CategoryName = "New test name";
   northwindContext.SaveChanges();
}
```

<span data-ttu-id="45651-185">Ten kod użytkownika generuje następujące drzewo poleceń, które jest przesyłane do dostawcy:</span><span class="sxs-lookup"><span data-stu-id="45651-185">This user code produces the following command tree, which is passed to the provider:</span></span>

```
DbUpdateCommandTree
|_Parameters
|_Target : 'target'
| |_Scan : dbo.Categories
|_SetClauses
| |_DbSetClause
|   |_Property
|   | |_Var(target).CategoryName
|   |_Value
|     |_'New test name'
|_Predicate
| |_
|   |_Var(target).CategoryID
|   |_=
|   |_10
|_Returning
```

<span data-ttu-id="45651-186">Przykładowy dostawca generuje następujące polecenie magazynu:</span><span class="sxs-lookup"><span data-stu-id="45651-186">The sample provider produces the following store command:</span></span>

```sql
update [dbo].[Categories]
set [CategoryName] = @p0
where ([CategoryID] = @p1)
```

### <a name="generating-a-delete-sql-command"></a><span data-ttu-id="45651-187">Generowanie polecenia Delete SQL</span><span class="sxs-lookup"><span data-stu-id="45651-187">Generating a Delete SQL Command</span></span>

<span data-ttu-id="45651-188">Dla danego DbDeleteCommandTree wygenerowanego polecenia DELETE bazuje na następującym szablonie:</span><span class="sxs-lookup"><span data-stu-id="45651-188">For a given DbDeleteCommandTree, the generated DELETE command is based on the following template:</span></span>

```sql
-- DELETE Template
DELETE <target>
WHERE <predicate>
```

<span data-ttu-id="45651-189">W poniższym przykładzie zastosowano model, który jest dołączony do przykładowego dostawcy w celu wygenerowania polecenia Delete.</span><span class="sxs-lookup"><span data-stu-id="45651-189">The following example uses the model that is included with the sample provider to generate a delete command.</span></span>

<span data-ttu-id="45651-190">Następujący kod użytkownika usuwa kategorię:</span><span class="sxs-lookup"><span data-stu-id="45651-190">The following user code deletes a Category:</span></span>

```csharp
using (NorthwindEntities northwindContext = new NorthwindEntities()) {
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "New test name").First();
   northwindContext.DeleteObject(c);
   northwindContext.SaveChanges();
}
```

<span data-ttu-id="45651-191">Ten kod użytkownika generuje następujące drzewo poleceń, które jest przesyłane do dostawcy.</span><span class="sxs-lookup"><span data-stu-id="45651-191">This user code produces the following command tree, which is passed to the provider.</span></span>

```
DbDeleteCommandTree
|_Parameters
|_Target : 'target'
| |_Scan : dbo.Categories
|_Predicate
  |_
    |_Var(target).CategoryID
    |_=
    |_10
```

<span data-ttu-id="45651-192">Następujące polecenie magazynu jest tworzone przez przykładowego dostawcę:</span><span class="sxs-lookup"><span data-stu-id="45651-192">The following store command is produced by the sample provider:</span></span>

```sql
delete [dbo].[Categories]
where ([CategoryID] = @p0)
```

## <a name="see-also"></a><span data-ttu-id="45651-193">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="45651-193">See also</span></span>

- [<span data-ttu-id="45651-194">Pisanie dostawcy danych programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="45651-194">Writing an Entity Framework Data Provider</span></span>](writing-an-ef-data-provider.md)
