---
title: Generowanie kodu SQL modyfikacji
ms.date: 03/30/2017
ms.assetid: 2188a39d-46ed-4a8b-906a-c9f15e6fefd1
ms.openlocfilehash: b7bb390fd4e221c70d5ed8da5873c557fcde3c98
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32766663"
---
# <a name="modification-sql-generation"></a>Generowanie kodu SQL modyfikacji
W tej sekcji omówiono sposób rozwijać modyfikacji modułu generowania SQL dla użytkownika (SQL:1999-danych zgodnej ze standardem) dostawcy. Ten moduł jest odpowiedzialny za tłumaczenia poziomu drzewa poleceń modyfikacji w odpowiedniej instrukcji SQL INSERT, UPDATE lub DELETE.  
  
 Informacje o generowanie kodu SQL dla instrukcji "select", zobacz [generowanie kodu SQL](../../../../../docs/framework/data/adonet/ef/sql-generation.md).  
  
## <a name="overview-of-modification-command-trees"></a>Przegląd drzewa polecenia modyfikacji  
 Moduł generowania SQL modyfikacji generuje oparte na danym DbModificationCommandTree wejściowych instrukcji SQL modyfikacji specyficzny dla bazy danych.  
  
 DbModificationCommandTree jest reprezentacji modelu obiektu modyfikacji operacji DML (insert, update lub operację usuwania), dziedziczenie z DbCommandTree. Istnieją trzy implementacje DbModificationCommandTree:  
  
-   DbInsertCommandTree  
  
-   DbUpdateCommandTree  
  
-   DbDeleteCommandTree  
  
 DbModificationCommandTree i ich implementacji, które są tworzone przez [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] zawsze reprezentują operacji pojedynczy wiersz. W tej sekcji opisano typy z ich ograniczenia w programie .NET Framework w wersji 3.5.  
  
 ![Diagram](../../../../../docs/framework/data/adonet/ef/media/558ba7b3-dd19-48d0-b91e-30a76415bf5f.gif "558ba7b3-dd19-48d0-b91e-30a76415bf5f")  
  
 DbModificationCommandTree ma właściwość Target, który reprezentuje element docelowy dla operacji modyfikacji. Element docelowy wyrażenie właściwość, która definiuje zestaw wejściowy jest zawsze DbScanExpression.  DbScanExpression może reprezentować tabelę lub widok lub zestaw danych zdefiniowane za pomocą kwerendy właściwości metadanych "Definiowanie zapytania" z elementem docelowym jest inne niż null.  
  
 DbScanExpression, który reprezentuje zapytanie tylko mogą osiągnąć dostawcę jako miejsce docelowe modyfikacji, jeśli zestaw został zdefiniowany przy użyciu definiującego zapytania w modelu, lecz żadna funkcja nie został podany dla odpowiednich operacji modyfikacji. Dostawcy nie może mieć możliwość obsługuje scenariusza (SqlClient, na przykład nie).  
  
 DbInsertCommandTree reprezentuje pojedynczy wiersz operacji wstawiania, wyrażony jako drzewo poleceń.  
  
```  
public sealed class DbInsertCommandTree : DbModificationCommandTree {  
   public IList<DbModificationClause> SetClauses { get }  
   public DbExpression Returning { get }  
}  
```  
  
 DbUpdateCommandTree reprezentuje operację aktualizacji pojedynczy wiersz wyrażonej w postaci drzewa poleceń.  
  
 DbDeleteCommandTree reprezentuje operację usuwania pojedynczy wiersz wyrażonej w postaci drzewa poleceń.  
  
### <a name="restrictions-on-modification-command-tree-properties"></a>Ograniczenia dotyczące właściwości drzewa polecenia modyfikacji  
 Następujące informacje i ograniczenia mają zastosowanie do modyfikacji właściwości drzewa poleceń.  
  
#### <a name="returning-in-dbinsertcommandtree-and-dbupdatecommandtree"></a>Zwracanie DbInsertCommandTree i DbUpdateCommandTree  
 Gdy inną niż null, zwrócenie wskazuje, że polecenie zwraca czytnika. W przeciwnym razie polecenie powinien zwrócić wartość skalarną wskazującą liczbę uwzględnionych wierszy (wstawiane lub aktualizowane).  
  
 Zwrócenie wartości określa projekcji wyników do zwrócenia na podstawie wstawionych lub zaktualizowanych wiersza. Można tylko DbNewInstanceExpression wiersz dla każdego z jego argumentów przekraczającego DbPropertyExpression DbVariableReferenceExpression, reprezentujący odwołanie do obiektu docelowego DbModificationCommandTree odpowiedniego typu. Właściwości reprezentowanej przez DbPropertyExpressions używane we właściwości zwrócenie są zawsze magazynu wygenerowany lub obliczanej wartości. W DbInsertCommandTree zwrócenie nie jest zerowa, gdy co najmniej jedną właściwość tabeli, w której umieszczony jest wiersz jest określony jako magazynu wygenerowany lub obliczonych (oznaczone jako StoreGeneratedPattern.Identity lub StoreGeneratedPattern.Computed w pliku ssdl). W DbUpdateCommandTrees, zwrócenie nie ma wartości null podczas co najmniej jedną właściwość tabeli, w którym jest aktualizowana wiersz jest określony jako magazynu obliczana (oznaczone jako StoreGeneratedPattern.Computed w pliku ssdl).  
  
#### <a name="setclauses-in-dbinsertcommandtree-and-dbupdatecommandtree"></a>SetClauses DbInsertCommandTree i DbUpdateCommandTree  
 SetClauses Określa listę insert lub update Ustaw klauzule, które definiują operacji insert lub update.  
  
```  
The elements of the list are specified as type DbModificationClause, which specifies a single clause in an insert or update modification operation. DbSetClause inherits from DbModificationClause and specifies the clause in a modification operation that sets the value of a property. Beginning in version 3.5 of the .NET Framework, all elements in SetClauses are of type SetClause.   
```  
  
 Właściwość określa właściwości, które powinny być zaktualizowane. Jest zawsze DbPropertyExpression nad DbVariableReferenceExpression, co stanowi odwołanie do obiektu docelowego odpowiedniego DbModificationCommandTree.  
  
 Określa nową wartość, z którym można zaktualizować właściwości. Jest ona typu DbConstantExpression lub DbNullExpression.  
  
#### <a name="predicate-in-dbupdatecommandtree-and-dbdeletecommandtree"></a>Predykatu w DbUpdateCommandTree i DbDeleteCommandTree  
 Predykat określa predykatu używane do określenia, które elementy członkowskie kolekcji docelowej powinien można zaktualizować lub usunąć. Drzewo wyrażenia zbudowany z następujących podzbiór DbExpressions jest:  
  
-   Obiekt DbComparisonExpression rodzaju równa prawy element podrzędny jest DbPropertyExression jako ograniczeniami poniżej i lewy element podrzędny obiektu DbConstantExpression.  
  
-   DbConstantExpression  
  
-   Obiektu DbIsNullExpression za pośrednictwem, czy DbPropertyExpresison jako ograniczeniami poniżej  
  
-   DbPropertyExpression za pośrednictwem DbVariableReferenceExpression, reprezentujący odwołanie do obiektu docelowego odpowiedniego DbModificationCommandTree.  
  
-   DbAndExpression  
  
-   Obiekt DbNotExpression  
  
-   Obiekt DbOrExpression  
  
## <a name="modification-sql-generation-in-the-sample-provider"></a>Generowanie kodu SQL modyfikacji w dostawcy próbki  
 [Entity Framework próbki dostawcy](http://go.microsoft.com/fwlink/?LinkId=180616) przedstawiono składniki dostawcy danych ADO.NET, która obsługuje [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Bazę danych programu SQL Server 2005, a jest zaimplementowany jako otoka u góry System.Data.SqlClient dostawca danych programu ADO.NET 2.0.  
  
 Moduł generowania SQL modyfikacji dostawcy próbki (znajdujący się w pliku SQL Generation\DmlSqlGenerator.cs) ma wejściowych DbModificationCommandTree i tworzy jednej modyfikacji instrukcji SQL, prawdopodobnie zostały wykonane przez instrukcję select do zwrócenia Czytnik, jeśli określony przez DbModificationCommandTree. Należy pamiętać, kształt polecenia wygenerowany dotyczy docelowej bazy danych programu SQL Server.  
  
### <a name="helper-classes-expressiontranslator"></a>Klasy pomocy: ExpressionTranslator  
 ExpressionTranslator służy jako translatora lekkie wspólne dla wszystkich właściwości drzewa polecenia modyfikacji typu DbExpression. Obsługuje tłumaczenia tylko typy wyrażenie, do których są ograniczone właściwości modyfikacji drzewa poleceń, a wbudowana w określonym ograniczenia pamiętać.  
  
 Następujące informacje w tym artykule omówiono odwiedzający typy określonego wyrażenia (pominięto węzłów o prostej tłumaczenia).  
  
### <a name="dbcomparisonexpression"></a>Obiekt DbComparisonExpression  
 Gdy ExpressionTranslator jest tworzony z preserveMemberValues = true, i po stała po prawej stronie jest obiektem DbConstantExpression (zamiast DbNullExpression), z którego kojarzy lewy operand (DbPropertyExpressions) DbConstantExpression. Która jest używana, gdy zwracany instrukcji Select ma zostać wygenerowany do identyfikowania wierszu.  
  
### <a name="dbconstantexpression"></a>DbConstantExpression  
 Dla każdej odwiedzony stałej tworzony jest parametrem.  
  
### <a name="dbpropertyexpression"></a>DbPropertyExpression  
 Biorąc pod uwagę, że wystąpienie DbPropertyExpression zawsze reprezentuje tabeli wejściowej, chyba że Generowanie utworzył alias (którą wykonujemy w scenariuszach aktualizacji, gdy jest używana zmienna tabeli), Brak aliasu nie trzeba określać dla danych wejściowych; Tłumaczenie domyślnie nazwę właściwości.  
  
## <a name="generating-an-insert-sql-command"></a>Generowanie polecenia SQL Insert  
 Dla danego DbInsertCommandTree w dostawcy próbki polecenia insert wygenerowanego następuje jeden z poniższych szablonów Wstaw dwa.  
  
 Pierwszy szablon ma polecenia można wykonać polecenia wstawienia podane wartości na liście SetClauses i instrukcję SELECT do zwrócenia właściwości określony we właściwości zwrócenie wstawionego wiersza, jeśli właściwość zwrócenie nie był zerowy. Element predykatu "@@ROWCOUNT > 0" ma wartość true, jeśli został wstawiony wiersz. Element predykatu "keyMemberI = keyValueI &#124; scope_identity()" przyjmuje kształtu "keyMemberI = scope_identity()" tylko wtedy, gdy keyMemeberI jest kluczem generowanych przez Magazyn, ponieważ scope_identity() Zwraca ostatnią wartość tożsamości wstawione do (tożsamości) Kolumna wygenerowana przez Magazyn).  
  
```  
-- first insert Template  
INSERT <target>   [ (setClauseProperty0, .. setClausePropertyN)]    
VALUES (setClauseValue0, .. setClauseValueN) |  DEFAULT VALUES   
  
[SELECT <returning>   
 FROM <target>  
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]  
```  
  
 Drugi szablon jest niezbędny w przypadku insert określa wstawiania wiersza, w którym klucz podstawowy jest generowanych przez Magazyn, ale nie jest typu integer i w związku z tym nie można używać z scope_identity()). Również służy, jeśli jest generowanych przez Magazyn klucza złożonego.  
  
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
  
 Oto przykład, w którym korzysta z modelu, który jest dołączony do dostawcy próbki. Generuje on polecenia insert z DbInsertCommandTree.  
  
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
  
 Polecenie magazynu tworzącego dostawcy próbki jest następującą instrukcję SQL:  
  
```  
insert [dbo].[Categories]([CategoryName], [Description], [Picture])  
values (@p0, @p1, null)  
select [CategoryID]  
from [dbo].[Categories]  
where @@ROWCOUNT > 0 and [CategoryID] = scope_identity()  
```  
  
## <a name="generating-an-update-sql-command"></a>Generowanie polecenia SQL Update  
 Dla danego DbUpdateCommandTree polecenia update wygenerowanego opiera się na następującego szablonu:  
  
```  
-- UPDATE Template   
UPDATE <target>   
SET setClauseProprerty0 = setClauseValue0,  .. setClauseProprertyN = setClauseValueN  | @i = 0  
WHERE <predicate>  
  
[SELECT <returning>   
 FROM <target>  
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]  
```  
  
 W klauzuli set ma klauzuli set fałszywych ("@i = 0") tylko, jeśli nie określono żadnych klauzul zestawu. To, aby upewnić się, że wszelkie magazynu obliczona kolumn są przeliczane.  
  
 Tylko wtedy, gdy właściwość zwrócenie nie jest zerowa, instrukcję select jest generowany do zwrócenia właściwości określony we właściwości zwrócenie.  
  
 W poniższym przykładzie użyto modelu, który jest dołączony do dostawcy próbki można wygenerować polecenia Aktualizuj.  
  
 Poniższy kod użytkownika aktualizacji kategorii:  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "Test Category").First();  
   c.CategoryName = "New test name";  
   northwindContext.SaveChanges();  
}  
```  
  
 Ten kod użytkownika tworzy następujące drzewo poleceń jest przekazywane do dostawcy:  
  
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
  
 Dostawca przykładowe tworzy następujące polecenie magazynu:  
  
```  
update [dbo].[Categories]  
set [CategoryName] = @p0  
where ([CategoryID] = @p1)   
```  
  
### <a name="generating-a-delete-sql-command"></a>Generowanie polecenia SQL Delete  
 Dla danego DbDeleteCommandTree generowane polecenia DELETE jest oparty na szablonie następujące:  
  
```  
-- DELETE Template   
DELETE <target>   
WHERE <predicate>  
```  
  
 W poniższym przykładzie użyto modelu, który jest dołączony do dostawcy próbki można wygenerować polecenia delete.  
  
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
  
 Polecenie magazynu jest generowany przez dostawcę próbki:  
  
```  
delete [dbo].[Categories]  
where ([CategoryID] = @p0)  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Pisanie dostawcy danych programu Entity Framework](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)
