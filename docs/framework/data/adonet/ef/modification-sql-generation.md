---
title: Modyfikowanie generowania kodu SQL
ms.date: 03/30/2017
ms.assetid: 2188a39d-46ed-4a8b-906a-c9f15e6fefd1
ms.openlocfilehash: b6c1b71effba17d33c035d0f1df386bf56d405b5
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039897"
---
# <a name="modification-sql-generation"></a>Modyfikowanie generowania kodu SQL

W tej sekcji omówiono sposób tworzenia modyfikacji modułu generacji SQL dla dostawcy bazy danych zgodnej z programem (SQL: 1999). Ten moduł jest odpowiedzialny za tłumaczenie drzewa poleceń modyfikacji na odpowiednie instrukcje INSERT, UPDATE lub DELETE języka SQL.

Aby uzyskać informacje na temat generowania kodu SQL dla instrukcji SELECT, zobacz temat [Generowanie bazy danych SQL](sql-generation.md).

## <a name="overview-of-modification-command-trees"></a>Przegląd drzew poleceń modyfikacji

Moduł generowania kodu SQL generuje instrukcje SQL dotyczące modyfikacji specyficzne dla bazy danych w oparciu o dane wejściowe DbModificationCommandTree.

DbModificationCommandTree to reprezentacja modelu obiektów przez operację modyfikacji DML (INSERT, Update lub Delete), która dziedziczy z DbCommandTree. Istnieją trzy implementacje DbModificationCommandTree:

- DbInsertCommandTree

- DbUpdateCommandTree

- DbDeleteCommandTree

DbModificationCommandTree i jego implementacje, które są tworzone przez Entity Framework zawsze reprezentują pojedynczy wiersz operacji. W tej sekcji opisano te typy z ograniczeniami w .NET Framework w wersji 3,5.

![4b](./media/558ba7b3-dd19-48d0-b91e-30a76415bf5f.gif "558ba7b3-dd19-48d0-b91e-30a76415bf5f")

DbModificationCommandTree ma właściwość docelową, która reprezentuje zestaw docelowy dla operacji modyfikacji. Właściwość wyrażenia elementu docelowego, która definiuje zestaw danych wejściowych, jest zawsze DbScanExpression.  DbScanExpression może reprezentować tabelę lub widok lub zestaw danych zdefiniowany za pomocą zapytania, jeśli właściwość metadanych "definiujące zapytanie" jego obiektu docelowego jest inna niż null.

DbScanExpression reprezentujący zapytanie może dotrzeć do dostawcy tylko jako element docelowy modyfikacji, jeśli zestaw został zdefiniowany przy użyciu zapytania definiującego w modelu, ale nie podano żadnej funkcji dla odpowiedniej operacji modyfikacji. Dostawcy mogą nie być w stanie obsłużyć takiego scenariusza (na przykład nie są).

DbInsertCommandTree reprezentuje pojedynczy wiersz operacji wstawiania wyrażony jako drzewo poleceń.

```csharp
public sealed class DbInsertCommandTree : DbModificationCommandTree {
   public IList<DbModificationClause> SetClauses { get }
   public DbExpression Returning { get }
}
```

DbUpdateCommandTree reprezentuje jednowierszową operację aktualizacji wyrażoną jako drzewo poleceń.

DbDeleteCommandTree reprezentuje operację usuwania pojedynczego wiersza wyrażoną jako drzewo poleceń.

### <a name="restrictions-on-modification-command-tree-properties"></a>Ograniczenia dotyczące właściwości drzewa poleceń modyfikacji

Poniższe informacje i ograniczenia dotyczą właściwości drzewa poleceń modyfikacji.

#### <a name="returning-in-dbinsertcommandtree-and-dbupdatecommandtree"></a>Zwracanie w DbInsertCommandTree i DbUpdateCommandTree

Gdy zwracana jest wartość inna niż null, funkcja Return wskazuje, że polecenie zwraca czytnik. W przeciwnym razie polecenie powinno zwrócić wartość skalarną wskazującą liczbę wierszy, których dotyczy (wstawiona lub zaktualizowana).

Wartość zwracana określa rzutowanie wyników do zwrócenia na podstawie wstawionego lub zaktualizowanego wiersza. Może być tylko typu obiekt DbNewInstanceExpression reprezentujący wiersz, a każdy z jego argumentów jest DbPropertyExpressionem nad DbVariableReferenceExpression reprezentującą odwołanie do obiektu docelowego odpowiedniego DbModificationCommandTree. Właściwości reprezentowane przez DbPropertyExpressions używane w zwracanej właściwości są zawsze przechowywane lub obliczane wartości. W DbInsertCommandTree zwraca nie ma wartości null, jeśli co najmniej jedna właściwość tabeli, w której wstawiany jest wiersz, jest określona jako magazyn wygenerowany lub obliczony (oznaczony jako StoreGeneratedPattern. Identity lub StoreGeneratedPattern. COMPUTE in SSDL). W DbUpdateCommandTrees zwraca nie ma wartości null, jeśli co najmniej jedna właściwość tabeli, w której wiersz jest aktualizowany jest określony jako obliczony przez magazyn (oznaczony jako StoreGeneratedPattern. COMPUTE in SSDL).

#### <a name="setclauses-in-dbinsertcommandtree-and-dbupdatecommandtree"></a>Setklauzuls in DbInsertCommandTree i DbUpdateCommandTree

Setklauzule określa listę klauzul INSERT lub Update Set definiujących operację INSERT lub Update.

Elementy listy są określone jako typ DbModificationClause, który określa pojedynczą klauzulę w operacji INSERT lub modyfikacji Update. DbSetClause dziedziczy z DbModificationClause i określa klauzulę w operacji modyfikacji, która ustawia wartość właściwości. Począwszy od wersji 3,5 .NET Framework, wszystkie elementy w klauzulach setklauzule są typu setklauzuli.

Właściwość określa właściwość, która ma zostać zaktualizowana. Zawsze jest to DbPropertyExpression w DbVariableReferenceExpression, który reprezentuje odwołanie do elementu docelowego odpowiedniego DbModificationCommandTree.

Wartość określa nową wartość, za pomocą której należy zaktualizować właściwość. Jest to typ DbConstantExpression lub DbNullExpression.

#### <a name="predicate-in-dbupdatecommandtree-and-dbdeletecommandtree"></a>Predykat w DbUpdateCommandTree i DbDeleteCommandTree

Predykat określa predykat używany do określenia, które elementy członkowskie kolekcji docelowej należy zaktualizować lub usunąć. Jest to drzewo wyrażenia skompilowane z następującego podzestawu DbExpressions:

- Obiekt DbComparisonExpression rodzaju równa się, z prawym elementem podrzędnym jest DbPropertyExpression, zgodnie z ograniczeniami poniżej, i z lewej strony podrzędnej DbConstantExpression.

- DbConstantExpression

- DbIsNullExpression na DbPropertyExpressionach zgodnie z ograniczeniami poniżej

- DbPropertyExpression nad DbVariableReferenceExpression reprezentującą odwołanie do elementu docelowego odpowiedniego DbModificationCommandTree.

- Metoda DbAndExpression

- Obiekt DbNotExpression

- Obiekt DbOrExpression

## <a name="modification-sql-generation-in-the-sample-provider"></a>Modyfikowanie generowania kodu SQL w przykładowym dostawcy

[Przykładowy dostawca Entity Framework](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) ilustruje składniki dostawców danych ADO.NET, które obsługują Entity Framework. Jest ona przeznaczona dla bazy danych SQL Server 2005 i jest zaimplementowana jako otoka na początku Dostawca danych System. Data. SqlClient ADO.NET 2,0.

W przypadku zmodyfikowania modułu generowania bazy danych SQL dostawcy przykładowego (znajdującego się w pliku SQL Generation\DmlSqlGenerator.cs) tworzony jest DbModificationCommandTree wejściowy i tworzona jest pojedyncza instrukcja SQL, po której występuje instrukcja SELECT zwracająca czytnik, jeśli został określony przez DbModificationCommandTree. Należy zauważyć, że docelowa baza danych SQL Server ma wpływ na kształt generowanych poleceń.

### <a name="helper-classes-expressiontranslator"></a>Klasy pomocnika: ExpressionTranslator

ExpressionTranslator służy jako wspólny lekki Translator dla wszystkich właściwości drzewa poleceń modyfikacji typu DbExpression. Obsługuje translację tylko typów wyrażeń, do których właściwości drzewa poleceń modyfikacji są ograniczone i zostały skompilowane z uwzględnieniem określonych ograniczeń.

Poniższe informacje omawiają odwiedzanie określonych typów wyrażeń (węzły z prostymi tłumaczeniami są pomijane).

### <a name="dbcomparisonexpression"></a>Obiekt DbComparisonExpression

Gdy ExpressionTranslator jest konstruowany przy użyciu preserveMemberValues = true, a gdy stała z prawej strony jest DbConstantExpression (zamiast DbNullExpression), kojarzy z lewym operandem (DbPropertyExpressions) DbConstantExpression. Jest używany, jeśli instrukcja return SELECT musi zostać wygenerowana, aby zidentyfikować odnośny wiersz.

### <a name="dbconstantexpression"></a>DbConstantExpression

Dla każdej odwiedzonej stałej jest tworzony parametr.

### <a name="dbpropertyexpression"></a>DbPropertyExpression

Ponieważ wystąpienie elementu DbPropertyExpression zawsze reprezentuje tabelę wejściową, chyba że generacja utworzyła alias (który występuje tylko w scenariuszach aktualizacji, gdy jest używana zmienna tabeli), nie trzeba określać aliasu dla danych wejściowych; wartość domyślna tłumaczenia na nazwę właściwości.

## <a name="generating-an-insert-sql-command"></a>Generowanie polecenia INSERT SQL

W przypadku danego DbInsertCommandTree w dostawcy przykładowym wygenerowanym poleceniem INSERT następuje jeden z dwóch szablonów wstawiania poniżej.

Pierwszy szablon zawiera polecenie do wykonania Wstaw dane wartości z listy setklauzuls i instrukcji SELECT do zwracania właściwości określonych we właściwości return dla wstawionego wiersza, jeśli właściwość zwracająca wartość nie jest równa null. Element predykatu "\@@ROWCOUNT > 0" ma wartość true, jeśli wiersz został wstawiony. Element predykatu "keyMemberI = keyValueI &#124; SCOPE_IDENTITY ()" przyjmuje kształt "keyMemberI = SCOPE_IDENTITY ()" tylko wtedy, gdy keyMemberI jest kluczem wygenerowanym przez magazyn, ponieważ SCOPE_IDENTITY () zwraca ostatnią wartość tożsamości wstawioną do tożsamości ( kolumna wygenerowana przez magazyn).

```sql
-- first insert Template
INSERT <target>   [ (setClauseProperty0, .. setClausePropertyN)]
VALUES (setClauseValue0, .. setClauseValueN) |  DEFAULT VALUES

[SELECT <returning>
 FROM <target>
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]
```

Drugi szablon jest wymagany, jeśli INSERT określa Wstawianie wiersza, gdzie klucz podstawowy jest generowany przez magazyn, ale nie jest typem całkowitym i dlatego nie można go używać z SCOPE_IDENTITY (). Jest również używany, jeśli istnieje klucz wygenerowany przez magazyn złożony.

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

Poniżej znajduje się przykład wykorzystujący model, który jest dołączony do przykładowego dostawcy. Generuje polecenie INSERT z DbInsertCommandTree.

Poniższy kod wstawia kategorię:

```csharp
using (NorthwindEntities northwindContext = new NorthwindEntities()) {
   Category c = new Category();
   c.CategoryName = "Test Category";
   c.Description = "A new category for testing";
   northwindContext.AddObject("Categories", c);
   northwindContext.SaveChanges();
}
```

Ten kod tworzy następujące drzewo poleceń, które jest przesyłane do dostawcy:

```output
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

Poleceniem Store tworzonym przez przykładowego dostawcę jest następująca instrukcja SQL:

```sql
insert [dbo].[Categories]([CategoryName], [Description], [Picture])
values (@p0, @p1, null)
select [CategoryID]
from [dbo].[Categories]
where @@ROWCOUNT > 0 and [CategoryID] = scope_identity()
```

## <a name="generating-an-update-sql-command"></a>Generowanie polecenia Update SQL

Dla danego DbUpdateCommandTree generowane polecenie Update jest oparte na następującym szablonie:

```sql
-- UPDATE Template
UPDATE <target>
SET setClauseProperty0 = setClauseValue0, .. setClausePropertyN = setClauseValueN  | @i = 0
WHERE <predicate>

[SELECT <returning>
 FROM <target>
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]
```

Klauzula SET ma zainstalowaną klauzulę "@i = 0") tylko wtedy, gdy nie określono żadnych klauzul Set. Ma to na celu upewnienie się, że wszystkie kolumny obliczane przez magazyn są ponownie obliczane.

Tylko wtedy, gdy właściwość zwracająca nie ma wartości null, generowana jest instrukcja SELECT zwracająca właściwości określone we właściwości zwracanej.

W poniższym przykładzie zastosowano model, który jest dołączony do przykładowego dostawcy w celu wygenerowania polecenia Update.

Następujący kod użytkownika aktualizuje kategorię:

```csharp
using (NorthwindEntities northwindContext = new NorthwindEntities()) {
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "Test Category").First();
   c.CategoryName = "New test name";
   northwindContext.SaveChanges();
}
```

Ten kod użytkownika generuje następujące drzewo poleceń, które jest przesyłane do dostawcy:

```output
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

Przykładowy dostawca generuje następujące polecenie magazynu:

```sql
update [dbo].[Categories]
set [CategoryName] = @p0
where ([CategoryID] = @p1)
```

### <a name="generating-a-delete-sql-command"></a>Generowanie polecenia Delete SQL

Dla danego DbDeleteCommandTree wygenerowanego polecenia DELETE bazuje na następującym szablonie:

```sql
-- DELETE Template
DELETE <target>
WHERE <predicate>
```

W poniższym przykładzie zastosowano model, który jest dołączony do przykładowego dostawcy w celu wygenerowania polecenia Delete.

Następujący kod użytkownika usuwa kategorię:

```csharp
using (NorthwindEntities northwindContext = new NorthwindEntities()) {
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "New test name").First();
   northwindContext.DeleteObject(c);
   northwindContext.SaveChanges();
}
```

Ten kod użytkownika generuje następujące drzewo poleceń, które jest przesyłane do dostawcy.

```output
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

Następujące polecenie magazynu jest tworzone przez przykładowego dostawcę:

```sql
delete [dbo].[Categories]
where ([CategoryID] = @p0)
```

## <a name="see-also"></a>Zobacz także

- [Pisanie dostawcy danych programu Entity Framework](writing-an-ef-data-provider.md)
