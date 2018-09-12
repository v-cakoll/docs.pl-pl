---
title: Modyfikowanie generowania kodu SQL
ms.date: 03/30/2017
ms.assetid: 2188a39d-46ed-4a8b-906a-c9f15e6fefd1
ms.openlocfilehash: 8e0568e32094b6cc27137409f3d908928d82cebb
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44494287"
---
# <a name="modification-sql-generation"></a>Modyfikowanie generowania kodu SQL
W tej sekcji opisano kroki umożliwiające tworzenie modyfikacji modułu generowania SQL dla usługi (SQL:1999-danych zgodnej ze standardem) dostawcy. Ten moduł jest odpowiedzialny za tłumaczenie drzewo poleceń modyfikacji w odpowiedniej instrukcji SQL INSERT, UPDATE lub DELETE.  
  
 Aby dowiedzieć się, generowanie kodu SQL do instrukcji "select", zobacz [generowanie kodu SQL](../../../../../docs/framework/data/adonet/ef/sql-generation.md).  
  
## <a name="overview-of-modification-command-trees"></a>Omówienie modyfikowanie drzew poleceń  
 Moduł generowania SQL modyfikacji generuje instrukcje SQL modyfikacji określonej bazy danych oparte na danym DbModificationCommandTree danych wejściowych.  
  
 DbModificationCommandTree jest reprezentacja modelu obiektu modyfikacji operacji DML (wstawiania, aktualizacji lub operacja usuwania), dziedziczenie z DbCommandTree. Istnieją trzy implementacje DbModificationCommandTree:  
  
-   DbInsertCommandTree  
  
-   DbUpdateCommandTree  
  
-   DbDeleteCommandTree  
  
 DbModificationCommandTree i ich implementacji, które są produkowane przez [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] zawsze reprezentują operację pojedynczy wiersz. W tej sekcji opisano te typy z ich ograniczenia w .NET Framework w wersji 3.5.  
  
 ![Diagram](../../../../../docs/framework/data/adonet/ef/media/558ba7b3-dd19-48d0-b91e-30a76415bf5f.gif "558ba7b3-dd19-48d0-b91e-30a76415bf5f")  
  
 DbModificationCommandTree ma właściwość docelowa, która reprezentuje element docelowy dla operacja modyfikacji. Właściwości wyrażenia obiektu docelowego, który definiuje zestaw danych wejściowych jest zawsze DbScanExpression.  DbScanExpression może reprezentować tabelę lub widok lub zestaw danych zdefiniowanych za pomocą zapytania, jeśli właściwość metadanych "Definiowanie zapytania" jego element docelowy jest inna niż null.  
  
 DbScanExpression, który reprezentuje zapytanie, tylko mogą osiągnąć dostawcę jako obiekt docelowy modyfikacji, jeśli zestaw został zdefiniowany przy użyciu Definiowanie zapytania w modelu, ale żadna funkcja nie podano odpowiednia operacja modyfikacji. Dostawców może nie móc obsługuje scenariusza (Klient SQL, na przykład, nie ma).  
  
 DbInsertCommandTree reprezentuje pojedynczy wiersz operacji wstawiania, wyrażone jako drzewo poleceń.  
  
```  
public sealed class DbInsertCommandTree : DbModificationCommandTree {  
   public IList<DbModificationClause> SetClauses { get }  
   public DbExpression Returning { get }  
}  
```  
  
 DbUpdateCommandTree reprezentuje operację aktualizacji pojedynczy wiersz tabeli przedstawiony jako drzewie poleceń.  
  
 DbDeleteCommandTree reprezentuje operację usuwania pojedynczy wiersz przedstawiony jako drzewie poleceń.  
  
### <a name="restrictions-on-modification-command-tree-properties"></a>Ograniczenia dotyczące właściwości drzewa poleceń modyfikacji  
 Poniższe informacje, a ograniczenia dotyczą właściwości drzewa poleceń modyfikacji.  
  
#### <a name="returning-in-dbinsertcommandtree-and-dbupdatecommandtree"></a>Zwracanie DbInsertCommandTree i DbUpdateCommandTree  
 W przypadku innych niż null, zwrócenie oznacza, że polecenie jest zwracane czytnika. W przeciwnym razie polecenie powinna zwrócić wartość skalarną, wskazującą liczbę uwzględnionych wierszy (wstawionych lub zaktualizowanych).  
  
 Wartość zwrócenie określa projekcji wyników do zwrócenia na podstawie wstawiono lub zaktualizowano wierszy. Można tylko obiekt DbNewInstanceExpression wiersz, z każdą z jej argumentów przekraczającego DbPropertyExpression DbVariableReferenceExpression, reprezentująca odwołanie do lokalizacji docelowej DbModificationCommandTree odpowiedniego typu. Właściwości reprezentowanej przez DbPropertyExpressions użyta we właściwości zwrócenie są zawsze magazynu wygenerowany lub obliczonych wartości. W DbInsertCommandTree zwrócenie nie ma wartość null, jeśli nie określono co najmniej jedną właściwość tabeli, w której jest umieszczony wiersza jako magazyn wygenerowanych lub obliczona (oznaczone jako StoreGeneratedPattern.Identity lub StoreGeneratedPattern.Computed w ssdl). W DbUpdateCommandTrees, zwrócenie nie ma wartości null podczas co najmniej jedną właściwość tabeli, w którym wiersz jest aktualizowany jest określony jako magazyn obliczane (oznaczone jako StoreGeneratedPattern.Computed w ssdl).  
  
#### <a name="setclauses-in-dbinsertcommandtree-and-dbupdatecommandtree"></a>SetClauses DbInsertCommandTree i DbUpdateCommandTree  
 SetClauses Określa listę Wstaw lub aktualizacja zestawu klauzul, które definiują operacji wstawiania lub aktualizacji.  
  
```  
The elements of the list are specified as type DbModificationClause, which specifies a single clause in an insert or update modification operation. DbSetClause inherits from DbModificationClause and specifies the clause in a modification operation that sets the value of a property. Beginning in version 3.5 of the .NET Framework, all elements in SetClauses are of type SetClause.   
```  
  
 Właściwość określa właściwość, do której powinien zostać zaktualizowany. Zawsze jest DbPropertyExpression za pośrednictwem DbVariableReferenceExpression, który reprezentuje odwołanie do lokalizacji docelowej odpowiednie DbModificationCommandTree.  
  
 Określa nową wartość za pomocą którego można zaktualizować właściwości. Jest ona typu DbConstantExpression lub DbNullExpression.  
  
#### <a name="predicate-in-dbupdatecommandtree-and-dbdeletecommandtree"></a>Predykatu w DbUpdateCommandTree i DbDeleteCommandTree  
 Predykat określa predykat, używany do określenia, które elementy członkowskie kolekcji docelowej, należy można zaktualizować lub usunąć. Drzewo wyrażenia utworzone następujące podzbioru DbExpressions konieczne jest:  
  
-   Jest równe DbComparisonExpression rodzaju z prawo elementu podrzędnego jest DbPropertyExression jako ograniczeniami poniżej, a po lewej stronie podrzędnych obiektem DbConstantExpression.  
  
-   DbConstantExpression  
  
-   DbIsNullExpression za pośrednictwem, czy DbPropertyExpresison jako ograniczeniami poniżej  
  
-   DbPropertyExpression za pośrednictwem DbVariableReferenceExpression, reprezentująca odwołanie do lokalizacji docelowej odpowiednie DbModificationCommandTree.  
  
-   DbAndExpression  
  
-   Obiekt DbNotExpression  
  
-   DbOrExpression  
  
## <a name="modification-sql-generation-in-the-sample-provider"></a>Modyfikowanie generowania kodu SQL w dostawcy próbki  
 [Dostawcy programu Entity Framework przykładowe](https://go.microsoft.com/fwlink/?LinkId=180616) przedstawiono składniki dostawcy danych ADO.NET, który obsługuje [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Jest przeznaczony dla bazy danych programu SQL Server 2005, a jest implementowany jako otoki na podstawie System.Data.SqlClient dostawca danych programu ADO.NET w wersji 2.0.  
  
 Moduł generowania SQL modyfikacji dostawcy próbki (znajdujący się w pliku SQL Generation\DmlSqlGenerator.cs) przyjmuje DbModificationCommandTree danych wejściowych i generuje pojedynczy modyfikacji instrukcji SQL, prawdopodobnie następuje instrukcję select do zwrócenia Czytnik, jeśli określony przez DbModificationCommandTree. Należy pamiętać, że kształt polecenia wygenerowany ma wpływ docelowej bazy danych programu SQL Server.  
  
### <a name="helper-classes-expressiontranslator"></a>Klasy pomocnika: ExpressionTranslator  
 ExpressionTranslator służy jako translator uproszczone wspólne dla wszystkich właściwości drzewa polecenia modyfikacji typu DbExpression. Go obsługuje translację tylko typy wyrażenia, do których są one ograniczone właściwości drzewo poleceń modyfikacji i został utworzony za pomocą określonego ograniczenia należy pamiętać.  
  
 Poniższe informacje omawiają, odwiedzając typy określonego wyrażenia (pominięto węzłów za pomocą uproszczonych tłumaczenia).  
  
### <a name="dbcomparisonexpression"></a>DbComparisonExpression  
 Gdy jest konstruowany ExpressionTranslator preserveMemberValues = true, i gdy stała się po prawej stronie jest obiektem DbConstantExpression (zamiast DbNullExpression), korzystając z niego kojarzy lewy operand (DbPropertyExpressions) DbConstantExpression. Który jest używany, jeśli return instrukcji Select musi zostać wygenerowane do identyfikowania odpowiednim wierszu.  
  
### <a name="dbconstantexpression"></a>DbConstantExpression  
 Dla każdej odwiedzane stałej parametr zostanie utworzony.  
  
### <a name="dbpropertyexpression"></a>DbPropertyExpression  
 Biorąc pod uwagę, że wystąpienie DbPropertyExpression zawsze reprezentuje tabeli wejściowej, chyba że Generowanie utworzył alias (tylko wykonywane w scenariuszach aktualizacji, gdy jest używana zmienna tabeli), Brak aliasu musi być określona dla danych wejściowych; tłumaczenie jest wartością domyślną nazwę właściwości.  
  
## <a name="generating-an-insert-sql-command"></a>Generowanie polecenia SQL Insert  
 Dla danego DbInsertCommandTree w dostawcy próbki polecenia insert wygenerowanego następuje jeden z szablonów Wstaw dwa poniższe.  
  
 Pierwszego szablonu zawiera polecenie, aby wykonać polecenia wstawienia, biorąc pod uwagę wartości na liście SetClauses i instrukcji SELECT w celu wróć do właściwości określony we właściwości zwrócenie wstawionego wiersza, jeśli właściwość zwrócenie nie miał wartość null. Element predykatu "\@ @ROWCOUNT > 0" ma wartość true, jeśli został wstawiony wiersz. Element predykatu "keyMemberI = keyValueI &#124; scope_identity()" przyjmie kształt "keyMemberI = scope_identity()" tylko wtedy, gdy keyMemeberI jest kluczem generowane przez Magazyn, ponieważ scope_identity() Zwraca ostatnią wartość tożsamości wstawiony (tożsamości) Kolumna, generowane przez Magazyn).  
  
```  
-- first insert Template  
INSERT <target>   [ (setClauseProperty0, .. setClausePropertyN)]    
VALUES (setClauseValue0, .. setClauseValueN) |  DEFAULT VALUES   
  
[SELECT <returning>   
 FROM <target>  
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]  
```  
  
 Drugi szablon jest potrzebny, jeśli insert określa wstawienie wiersza, w którym klucz podstawowy jest generowane przez Magazyn, ale nie jest typu całkowitego i w związku z tym nie można używać z scope_identity()). Służy również w przypadku klucza złożonego generowane przez Magazyn.  
  
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
  
 Oto przykład, który korzysta z modelu, który jest dołączony do dostawcy próbki. Generuje on polecenia insert z DbInsertCommandTree.  
  
 Poniższy kod wstawia kategorii:  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = new Category();  
   c.CategoryName = "Test Category";  
   c.Description = "A new category for testing";  
   northwindContext.AddObject("Categories", c);  
   northwindContext.SaveChanges();  
}  
```  
  
 Ten kod tworzy następujące drzewo poleceń jest przekazywane do dostawcy:  
  
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
  
 Polecenie magazynu, który produkuje dostawcy próbki jest następującą instrukcję SQL:  
  
```  
insert [dbo].[Categories]([CategoryName], [Description], [Picture])  
values (@p0, @p1, null)  
select [CategoryID]  
from [dbo].[Categories]  
where @@ROWCOUNT > 0 and [CategoryID] = scope_identity()  
```  
  
## <a name="generating-an-update-sql-command"></a>Generowanie polecenia SQL Update  
 Dla danego DbUpdateCommandTree polecenia update wygenerowanego opiera się na następujący szablon:  
  
```  
-- UPDATE Template   
UPDATE <target>   
SET setClauseProprerty0 = setClauseValue0,  .. setClauseProprertyN = setClauseValueN  | @i = 0  
WHERE <predicate>  
  
[SELECT <returning>   
 FROM <target>  
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]  
```  
  
 Klauzula set ma klauzula set sztuczne ("@i = 0") tylko, jeśli nie określono żadnych klauzul zestawu. To, aby upewnić się, że dowolny magazyn obliczanej kolumny są obliczane ponownie.  
  
 Tylko wtedy, gdy właściwość zwrócenie nie ma wartość null, instrukcji select jest generowany w celu wróć do właściwości określony we właściwości zwrócenie.  
  
 W poniższym przykładzie użyto modelu, który jest uwzględniona w dostawcy próbki, można wygenerować polecenia update.  
  
 Poniższy kod użytkownika aktualizacje kategorii:  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "Test Category").First();  
   c.CategoryName = "New test name";  
   northwindContext.SaveChanges();  
}  
```  
  
 Ten kod użytkownika generuje następujące drzewo poleceń jest przekazywane do dostawcy:  
  
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
  
 Dostawcy próbki generuje następujące polecenie magazynu:  
  
```  
update [dbo].[Categories]  
set [CategoryName] = @p0  
where ([CategoryID] = @p1)   
```  
  
### <a name="generating-a-delete-sql-command"></a>Generowanie za pomocą polecenia SQL Delete  
 Dla danego DbDeleteCommandTree wygenerowany polecenie Usuń opiera się na następujący szablon:  
  
```  
-- DELETE Template   
DELETE <target>   
WHERE <predicate>  
```  
  
 W poniższym przykładzie użyto modelu, który jest uwzględniona w dostawcy próbki, można wygenerować polecenia delete.  
  
 Poniższy kod użytkownika usuwa kategorii:  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "New test name").First();  
   northwindContext.DeleteObject(c);  
   northwindContext.SaveChanges();  
}  
```  
  
 Ten kod użytkownika tworzy następujące drzewo poleceń jest przekazywane do dostawcy.  
  
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
  
 Następujące polecenie magazynu jest generowany przez dostawcę próbki:  
  
```  
delete [dbo].[Categories]  
where ([CategoryID] = @p0)  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Pisanie dostawcy danych programu Entity Framework](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)
