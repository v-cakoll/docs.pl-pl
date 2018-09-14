---
title: Modyfikowanie generowania kodu SQL
ms.date: 03/30/2017
ms.assetid: 2188a39d-46ed-4a8b-906a-c9f15e6fefd1
ms.openlocfilehash: 8e0568e32094b6cc27137409f3d908928d82cebb
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45518181"
---
# <a name="modification-sql-generation"></a><span data-ttu-id="764eb-102">Modyfikowanie generowania kodu SQL</span><span class="sxs-lookup"><span data-stu-id="764eb-102">Modification SQL Generation</span></span>
<span data-ttu-id="764eb-103">W tej sekcji opisano kroki umożliwiające tworzenie modyfikacji modułu generowania SQL dla usługi (SQL:1999-danych zgodnej ze standardem) dostawcy.</span><span class="sxs-lookup"><span data-stu-id="764eb-103">This section discusses how to develop a modification SQL generation module for your (SQL:1999-compliant database) provider.</span></span> <span data-ttu-id="764eb-104">Ten moduł jest odpowiedzialny za tłumaczenie drzewo poleceń modyfikacji w odpowiedniej instrukcji SQL INSERT, UPDATE lub DELETE.</span><span class="sxs-lookup"><span data-stu-id="764eb-104">This module is responsible for translating a modification command tree into the appropriate SQL INSERT, UPDATE or DELETE statements.</span></span>  
  
 <span data-ttu-id="764eb-105">Aby dowiedzieć się, generowanie kodu SQL do instrukcji "select", zobacz [generowanie kodu SQL](../../../../../docs/framework/data/adonet/ef/sql-generation.md).</span><span class="sxs-lookup"><span data-stu-id="764eb-105">For information about SQL generation for select statements, see [SQL Generation](../../../../../docs/framework/data/adonet/ef/sql-generation.md).</span></span>  
  
## <a name="overview-of-modification-command-trees"></a><span data-ttu-id="764eb-106">Omówienie modyfikowanie drzew poleceń</span><span class="sxs-lookup"><span data-stu-id="764eb-106">Overview of Modification Command Trees</span></span>  
 <span data-ttu-id="764eb-107">Moduł generowania SQL modyfikacji generuje instrukcje SQL modyfikacji określonej bazy danych oparte na danym DbModificationCommandTree danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="764eb-107">The modification SQL generation module generates database-specific modification SQL statements based on a given input DbModificationCommandTree.</span></span>  
  
 <span data-ttu-id="764eb-108">DbModificationCommandTree jest reprezentacja modelu obiektu modyfikacji operacji DML (wstawiania, aktualizacji lub operacja usuwania), dziedziczenie z DbCommandTree.</span><span class="sxs-lookup"><span data-stu-id="764eb-108">A DbModificationCommandTree is an object model representation of a modification DML operation (an insert, an update, or a delete operation), inheriting from DbCommandTree.</span></span> <span data-ttu-id="764eb-109">Istnieją trzy implementacje DbModificationCommandTree:</span><span class="sxs-lookup"><span data-stu-id="764eb-109">There are three implementations of DbModificationCommandTree:</span></span>  
  
-   <span data-ttu-id="764eb-110">DbInsertCommandTree</span><span class="sxs-lookup"><span data-stu-id="764eb-110">DbInsertCommandTree</span></span>  
  
-   <span data-ttu-id="764eb-111">DbUpdateCommandTree</span><span class="sxs-lookup"><span data-stu-id="764eb-111">DbUpdateCommandTree</span></span>  
  
-   <span data-ttu-id="764eb-112">DbDeleteCommandTree</span><span class="sxs-lookup"><span data-stu-id="764eb-112">DbDeleteCommandTree</span></span>  
  
 <span data-ttu-id="764eb-113">DbModificationCommandTree i ich implementacji, które są produkowane przez [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] zawsze reprezentują operację pojedynczy wiersz.</span><span class="sxs-lookup"><span data-stu-id="764eb-113">DbModificationCommandTree and its implementations that are produced by the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] always represent a single row operation.</span></span> <span data-ttu-id="764eb-114">W tej sekcji opisano te typy z ich ograniczenia w .NET Framework w wersji 3.5.</span><span class="sxs-lookup"><span data-stu-id="764eb-114">This section describes these types with their constraints in the .NET Framework version 3.5.</span></span>  
  
 <span data-ttu-id="764eb-115">![Diagram](../../../../../docs/framework/data/adonet/ef/media/558ba7b3-dd19-48d0-b91e-30a76415bf5f.gif "558ba7b3-dd19-48d0-b91e-30a76415bf5f")</span><span class="sxs-lookup"><span data-stu-id="764eb-115">![Diagram](../../../../../docs/framework/data/adonet/ef/media/558ba7b3-dd19-48d0-b91e-30a76415bf5f.gif "558ba7b3-dd19-48d0-b91e-30a76415bf5f")</span></span>  
  
 <span data-ttu-id="764eb-116">DbModificationCommandTree ma właściwość docelowa, która reprezentuje element docelowy dla operacja modyfikacji.</span><span class="sxs-lookup"><span data-stu-id="764eb-116">DbModificationCommandTree has a Target property that represents the target set for the modification operation.</span></span> <span data-ttu-id="764eb-117">Właściwości wyrażenia obiektu docelowego, który definiuje zestaw danych wejściowych jest zawsze DbScanExpression.</span><span class="sxs-lookup"><span data-stu-id="764eb-117">The Target’s Expression property, which defines the input set is always DbScanExpression.</span></span>  <span data-ttu-id="764eb-118">DbScanExpression może reprezentować tabelę lub widok lub zestaw danych zdefiniowanych za pomocą zapytania, jeśli właściwość metadanych "Definiowanie zapytania" jego element docelowy jest inna niż null.</span><span class="sxs-lookup"><span data-stu-id="764eb-118">A DbScanExpression can either represent a table or a view, or a set of data defined with a query if the metadata property "Defining Query" of its Target is non-null.</span></span>  
  
 <span data-ttu-id="764eb-119">DbScanExpression, który reprezentuje zapytanie, tylko mogą osiągnąć dostawcę jako obiekt docelowy modyfikacji, jeśli zestaw został zdefiniowany przy użyciu Definiowanie zapytania w modelu, ale żadna funkcja nie podano odpowiednia operacja modyfikacji.</span><span class="sxs-lookup"><span data-stu-id="764eb-119">A DbScanExpression that represents a query could only reach a provider as a target of modification if the set was defined by using a defining query in the model but no function was provided for the corresponding modification operation.</span></span> <span data-ttu-id="764eb-120">Dostawców może nie móc obsługuje scenariusza (Klient SQL, na przykład, nie ma).</span><span class="sxs-lookup"><span data-stu-id="764eb-120">Providers may not be able to support such a scenario (SqlClient, for example, does not).</span></span>  
  
 <span data-ttu-id="764eb-121">DbInsertCommandTree reprezentuje pojedynczy wiersz operacji wstawiania, wyrażone jako drzewo poleceń.</span><span class="sxs-lookup"><span data-stu-id="764eb-121">DbInsertCommandTree represents a single row insert operation expressed as a command tree.</span></span>  
  
```  
public sealed class DbInsertCommandTree : DbModificationCommandTree {  
   public IList<DbModificationClause> SetClauses { get }  
   public DbExpression Returning { get }  
}  
```  
  
 <span data-ttu-id="764eb-122">DbUpdateCommandTree reprezentuje operację aktualizacji pojedynczy wiersz tabeli przedstawiony jako drzewie poleceń.</span><span class="sxs-lookup"><span data-stu-id="764eb-122">DbUpdateCommandTree represents a single-row update operation expressed as a command tree.</span></span>  
  
 <span data-ttu-id="764eb-123">DbDeleteCommandTree reprezentuje operację usuwania pojedynczy wiersz przedstawiony jako drzewie poleceń.</span><span class="sxs-lookup"><span data-stu-id="764eb-123">DbDeleteCommandTree represents a single row delete operation expressed as a command tree.</span></span>  
  
### <a name="restrictions-on-modification-command-tree-properties"></a><span data-ttu-id="764eb-124">Ograniczenia dotyczące właściwości drzewa poleceń modyfikacji</span><span class="sxs-lookup"><span data-stu-id="764eb-124">Restrictions on Modification Command Tree Properties</span></span>  
 <span data-ttu-id="764eb-125">Poniższe informacje, a ograniczenia dotyczą właściwości drzewa poleceń modyfikacji.</span><span class="sxs-lookup"><span data-stu-id="764eb-125">The following information and restrictions apply to the modification command tree properties.</span></span>  
  
#### <a name="returning-in-dbinsertcommandtree-and-dbupdatecommandtree"></a><span data-ttu-id="764eb-126">Zwracanie DbInsertCommandTree i DbUpdateCommandTree</span><span class="sxs-lookup"><span data-stu-id="764eb-126">Returning in DbInsertCommandTree and DbUpdateCommandTree</span></span>  
 <span data-ttu-id="764eb-127">W przypadku innych niż null, zwrócenie oznacza, że polecenie jest zwracane czytnika.</span><span class="sxs-lookup"><span data-stu-id="764eb-127">When non-null, Returning indicates that the command returns a reader.</span></span> <span data-ttu-id="764eb-128">W przeciwnym razie polecenie powinna zwrócić wartość skalarną, wskazującą liczbę uwzględnionych wierszy (wstawionych lub zaktualizowanych).</span><span class="sxs-lookup"><span data-stu-id="764eb-128">Otherwise, the command should return a scalar value indicating the number of rows affected (inserted or updated).</span></span>  
  
 <span data-ttu-id="764eb-129">Wartość zwrócenie określa projekcji wyników do zwrócenia na podstawie wstawiono lub zaktualizowano wierszy.</span><span class="sxs-lookup"><span data-stu-id="764eb-129">The Returning value specifies a projection of results to be returned based on the inserted or the updated row.</span></span> <span data-ttu-id="764eb-130">Można tylko obiekt DbNewInstanceExpression wiersz, z każdą z jej argumentów przekraczającego DbPropertyExpression DbVariableReferenceExpression, reprezentująca odwołanie do lokalizacji docelowej DbModificationCommandTree odpowiedniego typu.</span><span class="sxs-lookup"><span data-stu-id="764eb-130">It can only be of type DbNewInstanceExpression representing a row, with each of its arguments being a DbPropertyExpression over a DbVariableReferenceExpression representing a reference to the Target of the corresponding DbModificationCommandTree.</span></span> <span data-ttu-id="764eb-131">Właściwości reprezentowanej przez DbPropertyExpressions użyta we właściwości zwrócenie są zawsze magazynu wygenerowany lub obliczonych wartości.</span><span class="sxs-lookup"><span data-stu-id="764eb-131">The properties represented by the DbPropertyExpressions used in the property Returning are always store generated or computed values.</span></span> <span data-ttu-id="764eb-132">W DbInsertCommandTree zwrócenie nie ma wartość null, jeśli nie określono co najmniej jedną właściwość tabeli, w której jest umieszczony wiersza jako magazyn wygenerowanych lub obliczona (oznaczone jako StoreGeneratedPattern.Identity lub StoreGeneratedPattern.Computed w ssdl).</span><span class="sxs-lookup"><span data-stu-id="764eb-132">In DbInsertCommandTree, Returning is not null when at least one property of the table in which the row is being inserted is specified as store generated or computed (marked as StoreGeneratedPattern.Identity or StoreGeneratedPattern.Computed in the ssdl).</span></span> <span data-ttu-id="764eb-133">W DbUpdateCommandTrees, zwrócenie nie ma wartości null podczas co najmniej jedną właściwość tabeli, w którym wiersz jest aktualizowany jest określony jako magazyn obliczane (oznaczone jako StoreGeneratedPattern.Computed w ssdl).</span><span class="sxs-lookup"><span data-stu-id="764eb-133">In DbUpdateCommandTrees, Returning is not null when at least one property of the table in which the row is being updated is specified as store computed (marked as StoreGeneratedPattern.Computed in the ssdl).</span></span>  
  
#### <a name="setclauses-in-dbinsertcommandtree-and-dbupdatecommandtree"></a><span data-ttu-id="764eb-134">SetClauses DbInsertCommandTree i DbUpdateCommandTree</span><span class="sxs-lookup"><span data-stu-id="764eb-134">SetClauses in DbInsertCommandTree and DbUpdateCommandTree</span></span>  
 <span data-ttu-id="764eb-135">SetClauses Określa listę Wstaw lub aktualizacja zestawu klauzul, które definiują operacji wstawiania lub aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="764eb-135">SetClauses specifies the list of insert or update set clauses that define the insert or update operation.</span></span>  
  
```  
The elements of the list are specified as type DbModificationClause, which specifies a single clause in an insert or update modification operation. DbSetClause inherits from DbModificationClause and specifies the clause in a modification operation that sets the value of a property. Beginning in version 3.5 of the .NET Framework, all elements in SetClauses are of type SetClause.   
```  
  
 <span data-ttu-id="764eb-136">Właściwość określa właściwość, do której powinien zostać zaktualizowany.</span><span class="sxs-lookup"><span data-stu-id="764eb-136">Property specifies the property that should be updated.</span></span> <span data-ttu-id="764eb-137">Zawsze jest DbPropertyExpression za pośrednictwem DbVariableReferenceExpression, który reprezentuje odwołanie do lokalizacji docelowej odpowiednie DbModificationCommandTree.</span><span class="sxs-lookup"><span data-stu-id="764eb-137">It is always a DbPropertyExpression over a DbVariableReferenceExpression, which represents a reference to the Target of the corresponding DbModificationCommandTree.</span></span>  
  
 <span data-ttu-id="764eb-138">Określa nową wartość za pomocą którego można zaktualizować właściwości.</span><span class="sxs-lookup"><span data-stu-id="764eb-138">Value specifies the new value with which to update the property.</span></span> <span data-ttu-id="764eb-139">Jest ona typu DbConstantExpression lub DbNullExpression.</span><span class="sxs-lookup"><span data-stu-id="764eb-139">It is either of type DbConstantExpression or DbNullExpression.</span></span>  
  
#### <a name="predicate-in-dbupdatecommandtree-and-dbdeletecommandtree"></a><span data-ttu-id="764eb-140">Predykatu w DbUpdateCommandTree i DbDeleteCommandTree</span><span class="sxs-lookup"><span data-stu-id="764eb-140">Predicate in DbUpdateCommandTree and DbDeleteCommandTree</span></span>  
 <span data-ttu-id="764eb-141">Predykat określa predykat, używany do określenia, które elementy członkowskie kolekcji docelowej, należy można zaktualizować lub usunąć.</span><span class="sxs-lookup"><span data-stu-id="764eb-141">Predicate specifies the predicate used to determine which members of the target collection should be updated or deleted.</span></span> <span data-ttu-id="764eb-142">Drzewo wyrażenia utworzone następujące podzbioru DbExpressions konieczne jest:</span><span class="sxs-lookup"><span data-stu-id="764eb-142">It is an expression tree built of the following subset of DbExpressions:</span></span>  
  
-   <span data-ttu-id="764eb-143">Jest równe DbComparisonExpression rodzaju z prawo elementu podrzędnego jest DbPropertyExression jako ograniczeniami poniżej, a po lewej stronie podrzędnych obiektem DbConstantExpression.</span><span class="sxs-lookup"><span data-stu-id="764eb-143">DbComparisonExpression of kind Equals, with the right child being a DbPropertyExression as restricted below and the left child a DbConstantExpression.</span></span>  
  
-   <span data-ttu-id="764eb-144">DbConstantExpression</span><span class="sxs-lookup"><span data-stu-id="764eb-144">DbConstantExpression</span></span>  
  
-   <span data-ttu-id="764eb-145">DbIsNullExpression za pośrednictwem, czy DbPropertyExpresison jako ograniczeniami poniżej</span><span class="sxs-lookup"><span data-stu-id="764eb-145">DbIsNullExpression over a DbPropertyExpresison as restricted below</span></span>  
  
-   <span data-ttu-id="764eb-146">DbPropertyExpression za pośrednictwem DbVariableReferenceExpression, reprezentująca odwołanie do lokalizacji docelowej odpowiednie DbModificationCommandTree.</span><span class="sxs-lookup"><span data-stu-id="764eb-146">DbPropertyExpression over a DbVariableReferenceExpression representing a reference to the Target of the corresponding DbModificationCommandTree.</span></span>  
  
-   <span data-ttu-id="764eb-147">DbAndExpression</span><span class="sxs-lookup"><span data-stu-id="764eb-147">DbAndExpression</span></span>  
  
-   <span data-ttu-id="764eb-148">Obiekt DbNotExpression</span><span class="sxs-lookup"><span data-stu-id="764eb-148">DbNotExpression</span></span>  
  
-   <span data-ttu-id="764eb-149">DbOrExpression</span><span class="sxs-lookup"><span data-stu-id="764eb-149">DbOrExpression</span></span>  
  
## <a name="modification-sql-generation-in-the-sample-provider"></a><span data-ttu-id="764eb-150">Modyfikowanie generowania kodu SQL w dostawcy próbki</span><span class="sxs-lookup"><span data-stu-id="764eb-150">Modification SQL Generation in the Sample Provider</span></span>  
 <span data-ttu-id="764eb-151">[Dostawcy programu Entity Framework przykładowe](https://go.microsoft.com/fwlink/?LinkId=180616) przedstawiono składniki dostawcy danych ADO.NET, który obsługuje [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="764eb-151">The [Entity Framework Sample Provider](https://go.microsoft.com/fwlink/?LinkId=180616) demonstrates the components of ADO.NET Data Providers that support the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="764eb-152">Jest przeznaczony dla bazy danych programu SQL Server 2005, a jest implementowany jako otoki na podstawie System.Data.SqlClient dostawca danych programu ADO.NET w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="764eb-152">It targets a SQL Server 2005 database and is implemented as a wrapper on top of System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>  
  
 <span data-ttu-id="764eb-153">Moduł generowania SQL modyfikacji dostawcy próbki (znajdujący się w pliku SQL Generation\DmlSqlGenerator.cs) przyjmuje DbModificationCommandTree danych wejściowych i generuje pojedynczy modyfikacji instrukcji SQL, prawdopodobnie następuje instrukcję select do zwrócenia Czytnik, jeśli określony przez DbModificationCommandTree.</span><span class="sxs-lookup"><span data-stu-id="764eb-153">The modification SQL generation module of the sample provider (located in the file SQL Generation\DmlSqlGenerator.cs) takes an input DbModificationCommandTree and produces a single modification SQL statement possibly followed by a select statement to return a reader if specified by the DbModificationCommandTree.</span></span> <span data-ttu-id="764eb-154">Należy pamiętać, że kształt polecenia wygenerowany ma wpływ docelowej bazy danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="764eb-154">Note that the shape of the commands generated is affected by the target SQL Server database.</span></span>  
  
### <a name="helper-classes-expressiontranslator"></a><span data-ttu-id="764eb-155">Klasy pomocnika: ExpressionTranslator</span><span class="sxs-lookup"><span data-stu-id="764eb-155">Helper Classes: ExpressionTranslator</span></span>  
 <span data-ttu-id="764eb-156">ExpressionTranslator służy jako translator uproszczone wspólne dla wszystkich właściwości drzewa polecenia modyfikacji typu DbExpression.</span><span class="sxs-lookup"><span data-stu-id="764eb-156">ExpressionTranslator serves as a common lightweight translator for all modification command tree properties of type DbExpression.</span></span> <span data-ttu-id="764eb-157">Go obsługuje translację tylko typy wyrażenia, do których są one ograniczone właściwości drzewo poleceń modyfikacji i został utworzony za pomocą określonego ograniczenia należy pamiętać.</span><span class="sxs-lookup"><span data-stu-id="764eb-157">It supports translation of only the expression types to which the properties of the modification command tree are constrained and is built with the particular constraints in mind.</span></span>  
  
 <span data-ttu-id="764eb-158">Poniższe informacje omawiają, odwiedzając typy określonego wyrażenia (pominięto węzłów za pomocą uproszczonych tłumaczenia).</span><span class="sxs-lookup"><span data-stu-id="764eb-158">The following information discusses visiting specific expression types (nodes with trivial translations are omitted).</span></span>  
  
### <a name="dbcomparisonexpression"></a><span data-ttu-id="764eb-159">DbComparisonExpression</span><span class="sxs-lookup"><span data-stu-id="764eb-159">DbComparisonExpression</span></span>  
 <span data-ttu-id="764eb-160">Gdy jest konstruowany ExpressionTranslator preserveMemberValues = true, i gdy stała się po prawej stronie jest obiektem DbConstantExpression (zamiast DbNullExpression), korzystając z niego kojarzy lewy operand (DbPropertyExpressions) DbConstantExpression.</span><span class="sxs-lookup"><span data-stu-id="764eb-160">When the ExpressionTranslator is constructed with preserveMemberValues = true, and when the constant to the right is a DbConstantExpression (instead of DbNullExpression), it associates the left operand (a DbPropertyExpressions) with that DbConstantExpression.</span></span> <span data-ttu-id="764eb-161">Który jest używany, jeśli return instrukcji Select musi zostać wygenerowane do identyfikowania odpowiednim wierszu.</span><span class="sxs-lookup"><span data-stu-id="764eb-161">That is used if a return Select statement needs to be generated to identify the affected row.</span></span>  
  
### <a name="dbconstantexpression"></a><span data-ttu-id="764eb-162">DbConstantExpression</span><span class="sxs-lookup"><span data-stu-id="764eb-162">DbConstantExpression</span></span>  
 <span data-ttu-id="764eb-163">Dla każdej odwiedzane stałej parametr zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="764eb-163">For each visited constant a parameter is created.</span></span>  
  
### <a name="dbpropertyexpression"></a><span data-ttu-id="764eb-164">DbPropertyExpression</span><span class="sxs-lookup"><span data-stu-id="764eb-164">DbPropertyExpression</span></span>  
 <span data-ttu-id="764eb-165">Biorąc pod uwagę, że wystąpienie DbPropertyExpression zawsze reprezentuje tabeli wejściowej, chyba że Generowanie utworzył alias (tylko wykonywane w scenariuszach aktualizacji, gdy jest używana zmienna tabeli), Brak aliasu musi być określona dla danych wejściowych; tłumaczenie jest wartością domyślną nazwę właściwości.</span><span class="sxs-lookup"><span data-stu-id="764eb-165">Given that the Instance of the DbPropertyExpression always represents the input table, unless the generation has created an alias (which only happens in update scenarios when a table variable is used), no alias needs to be specified for the input; the translation defaults to the property name.</span></span>  
  
## <a name="generating-an-insert-sql-command"></a><span data-ttu-id="764eb-166">Generowanie polecenia SQL Insert</span><span class="sxs-lookup"><span data-stu-id="764eb-166">Generating an Insert SQL Command</span></span>  
 <span data-ttu-id="764eb-167">Dla danego DbInsertCommandTree w dostawcy próbki polecenia insert wygenerowanego następuje jeden z szablonów Wstaw dwa poniższe.</span><span class="sxs-lookup"><span data-stu-id="764eb-167">For a given DbInsertCommandTree in the sample provider, the generated insert command follows one of the two insert templates below.</span></span>  
  
 <span data-ttu-id="764eb-168">Pierwszego szablonu zawiera polecenie, aby wykonać polecenia wstawienia, biorąc pod uwagę wartości na liście SetClauses i instrukcji SELECT w celu wróć do właściwości określony we właściwości zwrócenie wstawionego wiersza, jeśli właściwość zwrócenie nie miał wartość null.</span><span class="sxs-lookup"><span data-stu-id="764eb-168">The first template has a command to perform the insert given the values in the list of SetClauses, and a SELECT statement to return the properties specified in the Returning property for the inserted row if the Returning property was not null.</span></span> <span data-ttu-id="764eb-169">Element predykatu "\@ @ROWCOUNT > 0" ma wartość true, jeśli został wstawiony wiersz.</span><span class="sxs-lookup"><span data-stu-id="764eb-169">The predicate element "\@@ROWCOUNT > 0" is true if a row was inserted.</span></span> <span data-ttu-id="764eb-170">Element predykatu "keyMemberI = keyValueI &#124; scope_identity()" przyjmie kształt "keyMemberI = scope_identity()" tylko wtedy, gdy keyMemeberI jest kluczem generowane przez Magazyn, ponieważ scope_identity() Zwraca ostatnią wartość tożsamości wstawiony (tożsamości) Kolumna, generowane przez Magazyn).</span><span class="sxs-lookup"><span data-stu-id="764eb-170">The predicate element "keyMemberI =  keyValueI &#124; scope_identity()" takes the shape  "keyMemberI =  scope_identity()" only if keyMemeberI is a store-generated key, because scope_identity() returns the last identity value inserted into an identity (store-generated) column.</span></span>  
  
```  
-- first insert Template  
INSERT <target>   [ (setClauseProperty0, .. setClausePropertyN)]    
VALUES (setClauseValue0, .. setClauseValueN) |  DEFAULT VALUES   
  
[SELECT <returning>   
 FROM <target>  
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]  
```  
  
 <span data-ttu-id="764eb-171">Drugi szablon jest potrzebny, jeśli insert określa wstawienie wiersza, w którym klucz podstawowy jest generowane przez Magazyn, ale nie jest typu całkowitego i w związku z tym nie można używać z scope_identity()).</span><span class="sxs-lookup"><span data-stu-id="764eb-171">The second template is needed if the insert specifies inserting a row where the primary key is store-generated but is not an integer type and therefore can't be used with scope_identity()).</span></span> <span data-ttu-id="764eb-172">Służy również w przypadku klucza złożonego generowane przez Magazyn.</span><span class="sxs-lookup"><span data-stu-id="764eb-172">It is also used if there is a compound store-generated key.</span></span>  
  
```  
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
  
 <span data-ttu-id="764eb-173">Oto przykład, który korzysta z modelu, który jest dołączony do dostawcy próbki.</span><span class="sxs-lookup"><span data-stu-id="764eb-173">The following is an example that uses the model that is included with the sample provider.</span></span> <span data-ttu-id="764eb-174">Generuje on polecenia insert z DbInsertCommandTree.</span><span class="sxs-lookup"><span data-stu-id="764eb-174">It generates an insert command from a DbInsertCommandTree.</span></span>  
  
 <span data-ttu-id="764eb-175">Poniższy kod wstawia kategorii:</span><span class="sxs-lookup"><span data-stu-id="764eb-175">The following code inserts a Category:</span></span>  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = new Category();  
   c.CategoryName = "Test Category";  
   c.Description = "A new category for testing";  
   northwindContext.AddObject("Categories", c);  
   northwindContext.SaveChanges();  
}  
```  
  
 <span data-ttu-id="764eb-176">Ten kod tworzy następujące drzewo poleceń jest przekazywane do dostawcy:</span><span class="sxs-lookup"><span data-stu-id="764eb-176">This code produces the following command tree, which is passed to the provider:</span></span>  
  
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
  
 <span data-ttu-id="764eb-177">Polecenie magazynu, który produkuje dostawcy próbki jest następującą instrukcję SQL:</span><span class="sxs-lookup"><span data-stu-id="764eb-177">The store command that the sample provider produces is the following SQL statement:</span></span>  
  
```  
insert [dbo].[Categories]([CategoryName], [Description], [Picture])  
values (@p0, @p1, null)  
select [CategoryID]  
from [dbo].[Categories]  
where @@ROWCOUNT > 0 and [CategoryID] = scope_identity()  
```  
  
## <a name="generating-an-update-sql-command"></a><span data-ttu-id="764eb-178">Generowanie polecenia SQL Update</span><span class="sxs-lookup"><span data-stu-id="764eb-178">Generating an Update SQL Command</span></span>  
 <span data-ttu-id="764eb-179">Dla danego DbUpdateCommandTree polecenia update wygenerowanego opiera się na następujący szablon:</span><span class="sxs-lookup"><span data-stu-id="764eb-179">For a given DbUpdateCommandTree, the generated update command is based on the following template:</span></span>  
  
```  
-- UPDATE Template   
UPDATE <target>   
SET setClauseProprerty0 = setClauseValue0,  .. setClauseProprertyN = setClauseValueN  | @i = 0  
WHERE <predicate>  
  
[SELECT <returning>   
 FROM <target>  
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]  
```  
  
 <span data-ttu-id="764eb-180">Klauzula set ma klauzula set sztuczne ("@i = 0") tylko, jeśli nie określono żadnych klauzul zestawu.</span><span class="sxs-lookup"><span data-stu-id="764eb-180">The set clause has the fake set clause ("@i = 0") only if no set clauses are specified.</span></span> <span data-ttu-id="764eb-181">To, aby upewnić się, że dowolny magazyn obliczanej kolumny są obliczane ponownie.</span><span class="sxs-lookup"><span data-stu-id="764eb-181">This is to ensure that any store-computed columns are recomputed.</span></span>  
  
 <span data-ttu-id="764eb-182">Tylko wtedy, gdy właściwość zwrócenie nie ma wartość null, instrukcji select jest generowany w celu wróć do właściwości określony we właściwości zwrócenie.</span><span class="sxs-lookup"><span data-stu-id="764eb-182">Only if the Returning property is not null, a select statement is generated to return the properties specified in the Returning property.</span></span>  
  
 <span data-ttu-id="764eb-183">W poniższym przykładzie użyto modelu, który jest uwzględniona w dostawcy próbki, można wygenerować polecenia update.</span><span class="sxs-lookup"><span data-stu-id="764eb-183">The following example uses the model that is included with the sample provider to generate an update command.</span></span>  
  
 <span data-ttu-id="764eb-184">Poniższy kod użytkownika aktualizacje kategorii:</span><span class="sxs-lookup"><span data-stu-id="764eb-184">The following user code updates a Category:</span></span>  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "Test Category").First();  
   c.CategoryName = "New test name";  
   northwindContext.SaveChanges();  
}  
```  
  
 <span data-ttu-id="764eb-185">Ten kod użytkownika generuje następujące drzewo poleceń jest przekazywane do dostawcy:</span><span class="sxs-lookup"><span data-stu-id="764eb-185">This user code produces the following command tree, which is passed to the provider:</span></span>  
  
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
  
 <span data-ttu-id="764eb-186">Dostawcy próbki generuje następujące polecenie magazynu:</span><span class="sxs-lookup"><span data-stu-id="764eb-186">The sample provider produces the following store command:</span></span>  
  
```  
update [dbo].[Categories]  
set [CategoryName] = @p0  
where ([CategoryID] = @p1)   
```  
  
### <a name="generating-a-delete-sql-command"></a><span data-ttu-id="764eb-187">Generowanie za pomocą polecenia SQL Delete</span><span class="sxs-lookup"><span data-stu-id="764eb-187">Generating a Delete SQL Command</span></span>  
 <span data-ttu-id="764eb-188">Dla danego DbDeleteCommandTree wygenerowany polecenie Usuń opiera się na następujący szablon:</span><span class="sxs-lookup"><span data-stu-id="764eb-188">For a given DbDeleteCommandTree, the generated DELETE command is based on the following template:</span></span>  
  
```  
-- DELETE Template   
DELETE <target>   
WHERE <predicate>  
```  
  
 <span data-ttu-id="764eb-189">W poniższym przykładzie użyto modelu, który jest uwzględniona w dostawcy próbki, można wygenerować polecenia delete.</span><span class="sxs-lookup"><span data-stu-id="764eb-189">The following example uses the model that is included with the sample provider to generate a delete command.</span></span>  
  
 <span data-ttu-id="764eb-190">Poniższy kod użytkownika usuwa kategorii:</span><span class="sxs-lookup"><span data-stu-id="764eb-190">The following user code deletes a Category:</span></span>  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "New test name").First();  
   northwindContext.DeleteObject(c);  
   northwindContext.SaveChanges();  
}  
```  
  
 <span data-ttu-id="764eb-191">Ten kod użytkownika tworzy następujące drzewo poleceń jest przekazywane do dostawcy.</span><span class="sxs-lookup"><span data-stu-id="764eb-191">This user code produces the following command tree, which is passed to the provider.</span></span>  
  
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
  
 <span data-ttu-id="764eb-192">Następujące polecenie magazynu jest generowany przez dostawcę próbki:</span><span class="sxs-lookup"><span data-stu-id="764eb-192">The following store command is produced by the sample provider:</span></span>  
  
```  
delete [dbo].[Categories]  
where ([CategoryID] = @p0)  
```  
  
## <a name="see-also"></a><span data-ttu-id="764eb-193">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="764eb-193">See Also</span></span>  
 [<span data-ttu-id="764eb-194">Pisanie dostawcy danych programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="764eb-194">Writing an Entity Framework Data Provider</span></span>](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)
