---
title: Generowanie kodu SQL modyfikacji
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2188a39d-46ed-4a8b-906a-c9f15e6fefd1
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6696d80246d61cc2eac47266837d79661141b9b0
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="modification-sql-generation"></a><span data-ttu-id="5a58f-102">Generowanie kodu SQL modyfikacji</span><span class="sxs-lookup"><span data-stu-id="5a58f-102">Modification SQL Generation</span></span>
<span data-ttu-id="5a58f-103">W tej sekcji omówiono sposób rozwijać modyfikacji modułu generowania SQL dla użytkownika (SQL:1999-danych zgodnej ze standardem) dostawcy.</span><span class="sxs-lookup"><span data-stu-id="5a58f-103">This section discusses how to develop a modification SQL generation module for your (SQL:1999-compliant database) provider.</span></span> <span data-ttu-id="5a58f-104">Ten moduł jest odpowiedzialny za tłumaczenia poziomu drzewa poleceń modyfikacji w odpowiedniej instrukcji SQL INSERT, UPDATE lub DELETE.</span><span class="sxs-lookup"><span data-stu-id="5a58f-104">This module is responsible for translating a modification command tree into the appropriate SQL INSERT, UPDATE or DELETE statements.</span></span>  
  
 <span data-ttu-id="5a58f-105">Informacje o generowanie kodu SQL dla instrukcji "select", zobacz [generowanie kodu SQL](../../../../../docs/framework/data/adonet/ef/sql-generation.md).</span><span class="sxs-lookup"><span data-stu-id="5a58f-105">For information about SQL generation for select statements, see [SQL Generation](../../../../../docs/framework/data/adonet/ef/sql-generation.md).</span></span>  
  
## <a name="overview-of-modification-command-trees"></a><span data-ttu-id="5a58f-106">Przegląd drzewa polecenia modyfikacji</span><span class="sxs-lookup"><span data-stu-id="5a58f-106">Overview of Modification Command Trees</span></span>  
 <span data-ttu-id="5a58f-107">Moduł generowania SQL modyfikacji generuje oparte na danym DbModificationCommandTree wejściowych instrukcji SQL modyfikacji specyficzny dla bazy danych.</span><span class="sxs-lookup"><span data-stu-id="5a58f-107">The modification SQL generation module generates database-specific modification SQL statements based on a given input DbModificationCommandTree.</span></span>  
  
 <span data-ttu-id="5a58f-108">DbModificationCommandTree jest reprezentacji modelu obiektu modyfikacji operacji DML (insert, update lub operację usuwania), dziedziczenie z DbCommandTree.</span><span class="sxs-lookup"><span data-stu-id="5a58f-108">A DbModificationCommandTree is an object model representation of a modification DML operation (an insert, an update, or a delete operation), inheriting from DbCommandTree.</span></span> <span data-ttu-id="5a58f-109">Istnieją trzy implementacje DbModificationCommandTree:</span><span class="sxs-lookup"><span data-stu-id="5a58f-109">There are three implementations of DbModificationCommandTree:</span></span>  
  
-   <span data-ttu-id="5a58f-110">DbInsertCommandTree</span><span class="sxs-lookup"><span data-stu-id="5a58f-110">DbInsertCommandTree</span></span>  
  
-   <span data-ttu-id="5a58f-111">DbUpdateCommandTree</span><span class="sxs-lookup"><span data-stu-id="5a58f-111">DbUpdateCommandTree</span></span>  
  
-   <span data-ttu-id="5a58f-112">DbDeleteCommandTree</span><span class="sxs-lookup"><span data-stu-id="5a58f-112">DbDeleteCommandTree</span></span>  
  
 <span data-ttu-id="5a58f-113">DbModificationCommandTree i ich implementacji, które są tworzone przez [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] zawsze reprezentują operacji pojedynczy wiersz.</span><span class="sxs-lookup"><span data-stu-id="5a58f-113">DbModificationCommandTree and its implementations that are produced by the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] always represent a single row operation.</span></span> <span data-ttu-id="5a58f-114">W tej sekcji opisano typy z ich ograniczenia w programie .NET Framework w wersji 3.5.</span><span class="sxs-lookup"><span data-stu-id="5a58f-114">This section describes these types with their constraints in the .NET Framework version 3.5.</span></span>  
  
 <span data-ttu-id="5a58f-115">![Diagram](../../../../../docs/framework/data/adonet/ef/media/558ba7b3-dd19-48d0-b91e-30a76415bf5f.gif "558ba7b3-dd19-48d0-b91e-30a76415bf5f")</span><span class="sxs-lookup"><span data-stu-id="5a58f-115">![Diagram](../../../../../docs/framework/data/adonet/ef/media/558ba7b3-dd19-48d0-b91e-30a76415bf5f.gif "558ba7b3-dd19-48d0-b91e-30a76415bf5f")</span></span>  
  
 <span data-ttu-id="5a58f-116">DbModificationCommandTree ma właściwość Target, który reprezentuje element docelowy dla operacji modyfikacji.</span><span class="sxs-lookup"><span data-stu-id="5a58f-116">DbModificationCommandTree has a Target property that represents the target set for the modification operation.</span></span> <span data-ttu-id="5a58f-117">Element docelowy wyrażenie właściwość, która definiuje zestaw wejściowy jest zawsze DbScanExpression.</span><span class="sxs-lookup"><span data-stu-id="5a58f-117">The Target’s Expression property, which defines the input set is always DbScanExpression.</span></span>  <span data-ttu-id="5a58f-118">DbScanExpression może reprezentować tabelę lub widok lub zestaw danych zdefiniowane za pomocą kwerendy właściwości metadanych "Definiowanie zapytania" z elementem docelowym jest inne niż null.</span><span class="sxs-lookup"><span data-stu-id="5a58f-118">A DbScanExpression can either represent a table or a view, or a set of data defined with a query if the metadata property "Defining Query" of its Target is non-null.</span></span>  
  
 <span data-ttu-id="5a58f-119">DbScanExpression, który reprezentuje zapytanie tylko mogą osiągnąć dostawcę jako miejsce docelowe modyfikacji, jeśli zestaw został zdefiniowany przy użyciu definiującego zapytania w modelu, lecz żadna funkcja nie został podany dla odpowiednich operacji modyfikacji.</span><span class="sxs-lookup"><span data-stu-id="5a58f-119">A DbScanExpression that represents a query could only reach a provider as a target of modification if the set was defined by using a defining query in the model but no function was provided for the corresponding modification operation.</span></span> <span data-ttu-id="5a58f-120">Dostawcy nie może mieć możliwość obsługuje scenariusza (SqlClient, na przykład nie).</span><span class="sxs-lookup"><span data-stu-id="5a58f-120">Providers may not be able to support such a scenario (SqlClient, for example, does not).</span></span>  
  
 <span data-ttu-id="5a58f-121">DbInsertCommandTree reprezentuje pojedynczy wiersz operacji wstawiania, wyrażony jako drzewo poleceń.</span><span class="sxs-lookup"><span data-stu-id="5a58f-121">DbInsertCommandTree represents a single row insert operation expressed as a command tree.</span></span>  
  
```  
public sealed class DbInsertCommandTree : DbModificationCommandTree {  
   public IList<DbModificationClause> SetClauses { get }  
   public DbExpression Returning { get }  
}  
```  
  
 <span data-ttu-id="5a58f-122">DbUpdateCommandTree reprezentuje operację aktualizacji pojedynczy wiersz wyrażonej w postaci drzewa poleceń.</span><span class="sxs-lookup"><span data-stu-id="5a58f-122">DbUpdateCommandTree represents a single-row update operation expressed as a command tree.</span></span>  
  
 <span data-ttu-id="5a58f-123">DbDeleteCommandTree reprezentuje operację usuwania pojedynczy wiersz wyrażonej w postaci drzewa poleceń.</span><span class="sxs-lookup"><span data-stu-id="5a58f-123">DbDeleteCommandTree represents a single row delete operation expressed as a command tree.</span></span>  
  
### <a name="restrictions-on-modification-command-tree-properties"></a><span data-ttu-id="5a58f-124">Ograniczenia dotyczące właściwości drzewa polecenia modyfikacji</span><span class="sxs-lookup"><span data-stu-id="5a58f-124">Restrictions on Modification Command Tree Properties</span></span>  
 <span data-ttu-id="5a58f-125">Następujące informacje i ograniczenia mają zastosowanie do modyfikacji właściwości drzewa poleceń.</span><span class="sxs-lookup"><span data-stu-id="5a58f-125">The following information and restrictions apply to the modification command tree properties.</span></span>  
  
#### <a name="returning-in-dbinsertcommandtree-and-dbupdatecommandtree"></a><span data-ttu-id="5a58f-126">Zwracanie DbInsertCommandTree i DbUpdateCommandTree</span><span class="sxs-lookup"><span data-stu-id="5a58f-126">Returning in DbInsertCommandTree and DbUpdateCommandTree</span></span>  
 <span data-ttu-id="5a58f-127">Gdy inną niż null, zwrócenie wskazuje, że polecenie zwraca czytnika.</span><span class="sxs-lookup"><span data-stu-id="5a58f-127">When non-null, Returning indicates that the command returns a reader.</span></span> <span data-ttu-id="5a58f-128">W przeciwnym razie polecenie powinien zwrócić wartość skalarną wskazującą liczbę uwzględnionych wierszy (wstawiane lub aktualizowane).</span><span class="sxs-lookup"><span data-stu-id="5a58f-128">Otherwise, the command should return a scalar value indicating the number of rows affected (inserted or updated).</span></span>  
  
 <span data-ttu-id="5a58f-129">Zwrócenie wartości określa projekcji wyników do zwrócenia na podstawie wstawionych lub zaktualizowanych wiersza.</span><span class="sxs-lookup"><span data-stu-id="5a58f-129">The Returning value specifies a projection of results to be returned based on the inserted or the updated row.</span></span> <span data-ttu-id="5a58f-130">Można tylko DbNewInstanceExpression wiersz dla każdego z jego argumentów przekraczającego DbPropertyExpression DbVariableReferenceExpression, reprezentujący odwołanie do obiektu docelowego DbModificationCommandTree odpowiedniego typu.</span><span class="sxs-lookup"><span data-stu-id="5a58f-130">It can only be of type DbNewInstanceExpression representing a row, with each of its arguments being a DbPropertyExpression over a DbVariableReferenceExpression representing a reference to the Target of the corresponding DbModificationCommandTree.</span></span> <span data-ttu-id="5a58f-131">Właściwości reprezentowanej przez DbPropertyExpressions używane we właściwości zwrócenie są zawsze magazynu wygenerowany lub obliczanej wartości.</span><span class="sxs-lookup"><span data-stu-id="5a58f-131">The properties represented by the DbPropertyExpressions used in the property Returning are always store generated or computed values.</span></span> <span data-ttu-id="5a58f-132">W DbInsertCommandTree zwrócenie nie jest zerowa, gdy co najmniej jedną właściwość tabeli, w której umieszczony jest wiersz jest określony jako magazynu wygenerowany lub obliczonych (oznaczone jako StoreGeneratedPattern.Identity lub StoreGeneratedPattern.Computed w pliku ssdl).</span><span class="sxs-lookup"><span data-stu-id="5a58f-132">In DbInsertCommandTree, Returning is not null when at least one property of the table in which the row is being inserted is specified as store generated or computed (marked as StoreGeneratedPattern.Identity or StoreGeneratedPattern.Computed in the ssdl).</span></span> <span data-ttu-id="5a58f-133">W DbUpdateCommandTrees, zwrócenie nie ma wartości null podczas co najmniej jedną właściwość tabeli, w którym jest aktualizowana wiersz jest określony jako magazynu obliczana (oznaczone jako StoreGeneratedPattern.Computed w pliku ssdl).</span><span class="sxs-lookup"><span data-stu-id="5a58f-133">In DbUpdateCommandTrees, Returning is not null when at least one property of the table in which the row is being updated is specified as store computed (marked as StoreGeneratedPattern.Computed in the ssdl).</span></span>  
  
#### <a name="setclauses-in-dbinsertcommandtree-and-dbupdatecommandtree"></a><span data-ttu-id="5a58f-134">SetClauses DbInsertCommandTree i DbUpdateCommandTree</span><span class="sxs-lookup"><span data-stu-id="5a58f-134">SetClauses in DbInsertCommandTree and DbUpdateCommandTree</span></span>  
 <span data-ttu-id="5a58f-135">SetClauses Określa listę insert lub update Ustaw klauzule, które definiują operacji insert lub update.</span><span class="sxs-lookup"><span data-stu-id="5a58f-135">SetClauses specifies the list of insert or update set clauses that define the insert or update operation.</span></span>  
  
```  
The elements of the list are specified as type DbModificationClause, which specifies a single clause in an insert or update modification operation. DbSetClause inherits from DbModificationClause and specifies the clause in a modification operation that sets the value of a property. Beginning in version 3.5 of the .NET Framework, all elements in SetClauses are of type SetClause.   
```  
  
 <span data-ttu-id="5a58f-136">Właściwość określa właściwości, które powinny być zaktualizowane.</span><span class="sxs-lookup"><span data-stu-id="5a58f-136">Property specifies the property that should be updated.</span></span> <span data-ttu-id="5a58f-137">Jest zawsze DbPropertyExpression nad DbVariableReferenceExpression, co stanowi odwołanie do obiektu docelowego odpowiedniego DbModificationCommandTree.</span><span class="sxs-lookup"><span data-stu-id="5a58f-137">It is always a DbPropertyExpression over a DbVariableReferenceExpression, which represents a reference to the Target of the corresponding DbModificationCommandTree.</span></span>  
  
 <span data-ttu-id="5a58f-138">Określa nową wartość, z którym można zaktualizować właściwości.</span><span class="sxs-lookup"><span data-stu-id="5a58f-138">Value specifies the new value with which to update the property.</span></span> <span data-ttu-id="5a58f-139">Jest ona typu DbConstantExpression lub DbNullExpression.</span><span class="sxs-lookup"><span data-stu-id="5a58f-139">It is either of type DbConstantExpression or DbNullExpression.</span></span>  
  
#### <a name="predicate-in-dbupdatecommandtree-and-dbdeletecommandtree"></a><span data-ttu-id="5a58f-140">Predykatu w DbUpdateCommandTree i DbDeleteCommandTree</span><span class="sxs-lookup"><span data-stu-id="5a58f-140">Predicate in DbUpdateCommandTree and DbDeleteCommandTree</span></span>  
 <span data-ttu-id="5a58f-141">Predykat określa predykatu używane do określenia, które elementy członkowskie kolekcji docelowej powinien można zaktualizować lub usunąć.</span><span class="sxs-lookup"><span data-stu-id="5a58f-141">Predicate specifies the predicate used to determine which members of the target collection should be updated or deleted.</span></span> <span data-ttu-id="5a58f-142">Drzewo wyrażenia zbudowany z następujących podzbiór DbExpressions jest:</span><span class="sxs-lookup"><span data-stu-id="5a58f-142">It is an expression tree built of the following subset of DbExpressions:</span></span>  
  
-   <span data-ttu-id="5a58f-143">Obiekt DbComparisonExpression rodzaju równa prawy element podrzędny jest DbPropertyExression jako ograniczeniami poniżej i lewy element podrzędny obiektu DbConstantExpression.</span><span class="sxs-lookup"><span data-stu-id="5a58f-143">DbComparisonExpression of kind Equals, with the right child being a DbPropertyExression as restricted below and the left child a DbConstantExpression.</span></span>  
  
-   <span data-ttu-id="5a58f-144">DbConstantExpression</span><span class="sxs-lookup"><span data-stu-id="5a58f-144">DbConstantExpression</span></span>  
  
-   <span data-ttu-id="5a58f-145">Obiektu DbIsNullExpression za pośrednictwem, czy DbPropertyExpresison jako ograniczeniami poniżej</span><span class="sxs-lookup"><span data-stu-id="5a58f-145">DbIsNullExpression over a DbPropertyExpresison as restricted below</span></span>  
  
-   <span data-ttu-id="5a58f-146">DbPropertyExpression za pośrednictwem DbVariableReferenceExpression, reprezentujący odwołanie do obiektu docelowego odpowiedniego DbModificationCommandTree.</span><span class="sxs-lookup"><span data-stu-id="5a58f-146">DbPropertyExpression over a DbVariableReferenceExpression representing a reference to the Target of the corresponding DbModificationCommandTree.</span></span>  
  
-   <span data-ttu-id="5a58f-147">DbAndExpression</span><span class="sxs-lookup"><span data-stu-id="5a58f-147">DbAndExpression</span></span>  
  
-   <span data-ttu-id="5a58f-148">DbNotExpression</span><span class="sxs-lookup"><span data-stu-id="5a58f-148">DbNotExpression</span></span>  
  
-   <span data-ttu-id="5a58f-149">Obiekt DbOrExpression</span><span class="sxs-lookup"><span data-stu-id="5a58f-149">DbOrExpression</span></span>  
  
## <a name="modification-sql-generation-in-the-sample-provider"></a><span data-ttu-id="5a58f-150">Generowanie kodu SQL modyfikacji w dostawcy próbki</span><span class="sxs-lookup"><span data-stu-id="5a58f-150">Modification SQL Generation in the Sample Provider</span></span>  
 <span data-ttu-id="5a58f-151">[Entity Framework próbki dostawcy](http://go.microsoft.com/fwlink/?LinkId=180616) przedstawiono składniki dostawcy danych ADO.NET, która obsługuje [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5a58f-151">The [Entity Framework Sample Provider](http://go.microsoft.com/fwlink/?LinkId=180616) demonstrates the components of ADO.NET Data Providers that support the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="5a58f-152">Bazę danych programu SQL Server 2005, a jest zaimplementowany jako otoka u góry System.Data.SqlClient dostawca danych programu ADO.NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="5a58f-152">It targets a SQL Server 2005 database and is implemented as a wrapper on top of System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>  
  
 <span data-ttu-id="5a58f-153">Moduł generowania SQL modyfikacji dostawcy próbki (znajdujący się w pliku SQL Generation\DmlSqlGenerator.cs) ma wejściowych DbModificationCommandTree i tworzy jednej modyfikacji instrukcji SQL, prawdopodobnie zostały wykonane przez instrukcję select do zwrócenia Czytnik, jeśli określony przez DbModificationCommandTree.</span><span class="sxs-lookup"><span data-stu-id="5a58f-153">The modification SQL generation module of the sample provider (located in the file SQL Generation\DmlSqlGenerator.cs) takes an input DbModificationCommandTree and produces a single modification SQL statement possibly followed by a select statement to return a reader if specified by the DbModificationCommandTree.</span></span> <span data-ttu-id="5a58f-154">Należy pamiętać, kształt polecenia wygenerowany dotyczy docelowej bazy danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5a58f-154">Note that the shape of the commands generated is affected by the target SQL Server database.</span></span>  
  
### <a name="helper-classes-expressiontranslator"></a><span data-ttu-id="5a58f-155">Klasy pomocy: ExpressionTranslator</span><span class="sxs-lookup"><span data-stu-id="5a58f-155">Helper Classes: ExpressionTranslator</span></span>  
 <span data-ttu-id="5a58f-156">ExpressionTranslator służy jako translatora lekkie wspólne dla wszystkich właściwości drzewa polecenia modyfikacji typu DbExpression.</span><span class="sxs-lookup"><span data-stu-id="5a58f-156">ExpressionTranslator serves as a common lightweight translator for all modification command tree properties of type DbExpression.</span></span> <span data-ttu-id="5a58f-157">Obsługuje tłumaczenia tylko typy wyrażenie, do których są ograniczone właściwości modyfikacji drzewa poleceń, a wbudowana w określonym ograniczenia pamiętać.</span><span class="sxs-lookup"><span data-stu-id="5a58f-157">It supports translation of only the expression types to which the properties of the modification command tree are constrained and is built with the particular constraints in mind.</span></span>  
  
 <span data-ttu-id="5a58f-158">Następujące informacje w tym artykule omówiono odwiedzający typy określonego wyrażenia (pominięto węzłów o prostej tłumaczenia).</span><span class="sxs-lookup"><span data-stu-id="5a58f-158">The following information discusses visiting specific expression types (nodes with trivial translations are omitted).</span></span>  
  
### <a name="dbcomparisonexpression"></a><span data-ttu-id="5a58f-159">Obiekt DbComparisonExpression</span><span class="sxs-lookup"><span data-stu-id="5a58f-159">DbComparisonExpression</span></span>  
 <span data-ttu-id="5a58f-160">Gdy ExpressionTranslator jest tworzony z preserveMemberValues = true, i po stała po prawej stronie jest obiektem DbConstantExpression (zamiast DbNullExpression), z którego kojarzy lewy operand (DbPropertyExpressions) DbConstantExpression.</span><span class="sxs-lookup"><span data-stu-id="5a58f-160">When the ExpressionTranslator is constructed with preserveMemberValues = true, and when the constant to the right is a DbConstantExpression (instead of DbNullExpression), it associates the left operand (a DbPropertyExpressions) with that DbConstantExpression.</span></span> <span data-ttu-id="5a58f-161">Która jest używana, gdy zwracany instrukcji Select ma zostać wygenerowany do identyfikowania wierszu.</span><span class="sxs-lookup"><span data-stu-id="5a58f-161">That is used if a return Select statement needs to be generated to identify the affected row.</span></span>  
  
### <a name="dbconstantexpression"></a><span data-ttu-id="5a58f-162">DbConstantExpression</span><span class="sxs-lookup"><span data-stu-id="5a58f-162">DbConstantExpression</span></span>  
 <span data-ttu-id="5a58f-163">Dla każdej odwiedzony stałej tworzony jest parametrem.</span><span class="sxs-lookup"><span data-stu-id="5a58f-163">For each visited constant a parameter is created.</span></span>  
  
### <a name="dbpropertyexpression"></a><span data-ttu-id="5a58f-164">DbPropertyExpression</span><span class="sxs-lookup"><span data-stu-id="5a58f-164">DbPropertyExpression</span></span>  
 <span data-ttu-id="5a58f-165">Biorąc pod uwagę, że wystąpienie DbPropertyExpression zawsze reprezentuje tabeli wejściowej, chyba że Generowanie utworzył alias (którą wykonujemy w scenariuszach aktualizacji, gdy jest używana zmienna tabeli), Brak aliasu nie trzeba określać dla danych wejściowych; Tłumaczenie domyślnie nazwę właściwości.</span><span class="sxs-lookup"><span data-stu-id="5a58f-165">Given that the Instance of the DbPropertyExpression always represents the input table, unless the generation has created an alias (which only happens in update scenarios when a table variable is used), no alias needs to be specified for the input; the translation defaults to the property name.</span></span>  
  
## <a name="generating-an-insert-sql-command"></a><span data-ttu-id="5a58f-166">Generowanie polecenia SQL Insert</span><span class="sxs-lookup"><span data-stu-id="5a58f-166">Generating an Insert SQL Command</span></span>  
 <span data-ttu-id="5a58f-167">Dla danego DbInsertCommandTree w dostawcy próbki polecenia insert wygenerowanego następuje jeden z poniższych szablonów Wstaw dwa.</span><span class="sxs-lookup"><span data-stu-id="5a58f-167">For a given DbInsertCommandTree in the sample provider, the generated insert command follows one of the two insert templates below.</span></span>  
  
 <span data-ttu-id="5a58f-168">Pierwszy szablon ma polecenia można wykonać polecenia wstawienia podane wartości na liście SetClauses i instrukcję SELECT do zwrócenia właściwości określony we właściwości zwrócenie wstawionego wiersza, jeśli właściwość zwrócenie nie był zerowy.</span><span class="sxs-lookup"><span data-stu-id="5a58f-168">The first template has a command to perform the insert given the values in the list of SetClauses, and a SELECT statement to return the properties specified in the Returning property for the inserted row if the Returning property was not null.</span></span> <span data-ttu-id="5a58f-169">Element predykatu "@@ROWCOUNT > 0" ma wartość true, jeśli został wstawiony wiersz.</span><span class="sxs-lookup"><span data-stu-id="5a58f-169">The predicate element "@@ROWCOUNT > 0" is true if a row was inserted.</span></span> <span data-ttu-id="5a58f-170">Element predykatu "keyMemberI = keyValueI &#124; scope_identity() "przyjmuje kształtu" keyMemberI = scope_identity() "tylko wtedy, gdy keyMemeberI jest kluczem generowanych przez Magazyn, ponieważ scope_identity() Zwraca ostatnią wartość tożsamości wstawione do kolumny tożsamości (generowanych przez Magazyn).</span><span class="sxs-lookup"><span data-stu-id="5a58f-170">The predicate element "keyMemberI =  keyValueI &#124; scope_identity()" takes the shape  "keyMemberI =  scope_identity()" only if keyMemeberI is a store-generated key, because scope_identity() returns the last identity value inserted into an identity (store-generated) column.</span></span>  
  
```  
-- first insert Template  
INSERT <target>   [ (setClauseProperty0, .. setClausePropertyN)]    
VALUES (setClauseValue0, .. setClauseValueN) |  DEFAULT VALUES   
  
[SELECT <returning>   
 FROM <target>  
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]  
```  
  
 <span data-ttu-id="5a58f-171">Drugi szablon jest niezbędny w przypadku insert określa wstawiania wiersza, w którym klucz podstawowy jest generowanych przez Magazyn, ale nie jest typu integer i w związku z tym nie można używać z scope_identity()).</span><span class="sxs-lookup"><span data-stu-id="5a58f-171">The second template is needed if the insert specifies inserting a row where the primary key is store-generated but is not an integer type and therefore can't be used with scope_identity()).</span></span> <span data-ttu-id="5a58f-172">Również służy, jeśli jest generowanych przez Magazyn klucza złożonego.</span><span class="sxs-lookup"><span data-stu-id="5a58f-172">It is also used if there is a compound store-generated key.</span></span>  
  
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
  
 <span data-ttu-id="5a58f-173">Oto przykład, w którym korzysta z modelu, który jest dołączony do dostawcy próbki.</span><span class="sxs-lookup"><span data-stu-id="5a58f-173">The following is an example that uses the model that is included with the sample provider.</span></span> <span data-ttu-id="5a58f-174">Generuje on polecenia insert z DbInsertCommandTree.</span><span class="sxs-lookup"><span data-stu-id="5a58f-174">It generates an insert command from a DbInsertCommandTree.</span></span>  
  
 <span data-ttu-id="5a58f-175">Poniższy kod wstawia kategorii:</span><span class="sxs-lookup"><span data-stu-id="5a58f-175">The following code inserts a Category:</span></span>  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = new Category();  
   c.CategoryName = "Test Category";  
   c.Description = "A new category for testing";  
   northwindContext.AddObject("Categories", c);  
   northwindContext.SaveChanges();  
}  
```  
  
 <span data-ttu-id="5a58f-176">Ten kod tworzy następujące drzewo poleceń jest przekazywane do dostawcy:</span><span class="sxs-lookup"><span data-stu-id="5a58f-176">This code produces the following command tree, which is passed to the provider:</span></span>  
  
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
  
 <span data-ttu-id="5a58f-177">Polecenie magazynu tworzącego dostawcy próbki jest następującą instrukcję SQL:</span><span class="sxs-lookup"><span data-stu-id="5a58f-177">The store command that the sample provider produces is the following SQL statement:</span></span>  
  
```  
insert [dbo].[Categories]([CategoryName], [Description], [Picture])  
values (@p0, @p1, null)  
select [CategoryID]  
from [dbo].[Categories]  
where @@ROWCOUNT > 0 and [CategoryID] = scope_identity()  
```  
  
## <a name="generating-an-update-sql-command"></a><span data-ttu-id="5a58f-178">Generowanie polecenia SQL Update</span><span class="sxs-lookup"><span data-stu-id="5a58f-178">Generating an Update SQL Command</span></span>  
 <span data-ttu-id="5a58f-179">Dla danego DbUpdateCommandTree polecenia update wygenerowanego opiera się na następującego szablonu:</span><span class="sxs-lookup"><span data-stu-id="5a58f-179">For a given DbUpdateCommandTree, the generated update command is based on the following template:</span></span>  
  
```  
-- UPDATE Template   
UPDATE <target>   
SET setClauseProprerty0 = setClauseValue0,  .. setClauseProprertyN = setClauseValueN  | @i = 0  
WHERE <predicate>  
  
[SELECT <returning>   
 FROM <target>  
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]  
```  
  
 <span data-ttu-id="5a58f-180">W klauzuli set ma klauzuli set fałszywych ("@i = 0") tylko, jeśli nie określono żadnych klauzul zestawu.</span><span class="sxs-lookup"><span data-stu-id="5a58f-180">The set clause has the fake set clause ("@i = 0") only if no set clauses are specified.</span></span> <span data-ttu-id="5a58f-181">To, aby upewnić się, że wszelkie magazynu obliczona kolumn są przeliczane.</span><span class="sxs-lookup"><span data-stu-id="5a58f-181">This is to ensure that any store-computed columns are recomputed.</span></span>  
  
 <span data-ttu-id="5a58f-182">Tylko wtedy, gdy właściwość zwrócenie nie jest zerowa, instrukcję select jest generowany do zwrócenia właściwości określony we właściwości zwrócenie.</span><span class="sxs-lookup"><span data-stu-id="5a58f-182">Only if the Returning property is not null, a select statement is generated to return the properties specified in the Returning property.</span></span>  
  
 <span data-ttu-id="5a58f-183">W poniższym przykładzie użyto modelu, który jest dołączony do dostawcy próbki można wygenerować polecenia Aktualizuj.</span><span class="sxs-lookup"><span data-stu-id="5a58f-183">The following example uses the model that is included with the sample provider to generate an update command.</span></span>  
  
 <span data-ttu-id="5a58f-184">Poniższy kod użytkownika aktualizacji kategorii:</span><span class="sxs-lookup"><span data-stu-id="5a58f-184">The following user code updates a Category:</span></span>  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "Test Category").First();  
   c.CategoryName = "New test name";  
   northwindContext.SaveChanges();  
}  
```  
  
 <span data-ttu-id="5a58f-185">Ten kod użytkownika tworzy następujące drzewo poleceń jest przekazywane do dostawcy:</span><span class="sxs-lookup"><span data-stu-id="5a58f-185">This user code produces the following command tree, which is passed to the provider:</span></span>  
  
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
  
 <span data-ttu-id="5a58f-186">Dostawca przykładowe tworzy następujące polecenie magazynu:</span><span class="sxs-lookup"><span data-stu-id="5a58f-186">The sample provider produces the following store command:</span></span>  
  
```  
update [dbo].[Categories]  
set [CategoryName] = @p0  
where ([CategoryID] = @p1)   
```  
  
### <a name="generating-a-delete-sql-command"></a><span data-ttu-id="5a58f-187">Generowanie polecenia SQL Delete</span><span class="sxs-lookup"><span data-stu-id="5a58f-187">Generating a Delete SQL Command</span></span>  
 <span data-ttu-id="5a58f-188">Dla danego DbDeleteCommandTree generowane polecenia DELETE jest oparty na szablonie następujące:</span><span class="sxs-lookup"><span data-stu-id="5a58f-188">For a given DbDeleteCommandTree, the generated DELETE command is based on the following template:</span></span>  
  
```  
-- DELETE Template   
DELETE <target>   
WHERE <predicate>  
```  
  
 <span data-ttu-id="5a58f-189">W poniższym przykładzie użyto modelu, który jest dołączony do dostawcy próbki można wygenerować polecenia delete.</span><span class="sxs-lookup"><span data-stu-id="5a58f-189">The following example uses the model that is included with the sample provider to generate a delete command.</span></span>  
  
 <span data-ttu-id="5a58f-190">Poniższy kod użytkownika usuwa kategorii:</span><span class="sxs-lookup"><span data-stu-id="5a58f-190">The following user code deletes a Category:</span></span>  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "New test name").First();  
   northwindContext.DeleteObject(c);  
   northwindContext.SaveChanges();  
}  
```  
  
 <span data-ttu-id="5a58f-191">Ten kod użytkownika tworzy następujące drzewo poleceń jest przekazywane do dostawcy.</span><span class="sxs-lookup"><span data-stu-id="5a58f-191">This user code produces the following command tree, which is passed to the provider.</span></span>  
  
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
  
 <span data-ttu-id="5a58f-192">Polecenie magazynu jest generowany przez dostawcę próbki:</span><span class="sxs-lookup"><span data-stu-id="5a58f-192">The following store command is produced by the sample provider:</span></span>  
  
```  
delete [dbo].[Categories]  
where ([CategoryID] = @p0)  
```  
  
## <a name="see-also"></a><span data-ttu-id="5a58f-193">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5a58f-193">See Also</span></span>  
 [<span data-ttu-id="5a58f-194">Pisanie dostawcy danych programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="5a58f-194">Writing an Entity Framework Data Provider</span></span>](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)
