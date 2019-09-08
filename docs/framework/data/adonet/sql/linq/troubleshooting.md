---
title: Rozwiązywanie problemów
ms.date: 03/30/2017
ms.assetid: 8cd4401c-b12c-4116-a421-f3dcffa65670
ms.openlocfilehash: 0eede70b67cbaef4805fc7fc5f07fc51e342ea3f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780979"
---
# <a name="troubleshooting"></a>Rozwiązywanie problemów
Poniższe informacje ujawniają problemy, które mogą wystąpić w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacjach, i zawierają sugestie dotyczące unikania lub zmniejszania skutków tych problemów.  
  
 Dodatkowe problemy są rozwiązywane w [często zadawanych pytaniach](frequently-asked-questions.md).  
  
## <a name="unsupported-standard-query-operators"></a>Nieobsługiwane standardowe operatory zapytań  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Program nie obsługuje wszystkich standardowych metod operatora zapytań (na przykład <xref:System.Linq.Enumerable.ElementAt%2A>). W efekcie projekty, które kompilują, mogą nadal generować błędy w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [standardowe tłumaczenia operatorów zapytań](standard-query-operator-translation.md).  
  
## <a name="memory-issues"></a>Problemy z pamięcią  
 Jeśli zapytanie obejmuje kolekcję w pamięci i [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601>, zapytanie może być wykonywane w pamięci, w zależności od kolejności, w której określono dwie kolekcje. Jeśli zapytanie musi zostać wykonane w pamięci, należy pobrać dane z tabeli bazy danych.  
  
 Takie podejście jest niewydajne i może spowodować znaczne użycie pamięci i procesora. Spróbuj uniknąć takich zapytań wielodomenowych.  
  
## <a name="file-names-and-sqlmetal"></a>Nazwy plików i SQLMetal  
 Aby określić nazwę pliku wejściowego, należy dodać ją do wiersza polecenia jako plik wejściowy. Dołączenie nazwy pliku w parametrach połączenia (przy użyciu opcji **/Conn** ) nie jest obsługiwane. Aby uzyskać więcej informacji, zobacz [SQLMetal. exe (Narzędzie generowania kodu)](../../../../tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="class-library-projects"></a>Projekty biblioteki klas  
 Object Relational Designer tworzy parametry połączenia w `app.config` pliku projektu. W projektach `app.config` biblioteki klas plik nie jest używany. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]używa parametrów połączenia dostarczonych w plikach czasu projektowania. Zmiana wartości w programie `app.config` nie powoduje zmiany bazy danych, z którą aplikacja nawiązuje połączenie.  
  
## <a name="cascade-delete"></a>Usuwanie kaskadowe  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nie obsługuje ani nie rozpoznaje operacji kaskadowego usuwania. Jeśli chcesz usunąć wiersz w tabeli zawierającej ograniczenia, wykonaj jedną z następujących czynności:  
  
- `ON DELETE CASCADE` Ustaw regułę w ograniczeniu klucza obcego w bazie danych.  
  
- Aby najpierw usunąć obiekty podrzędne, które uniemożliwiają usunięcie obiektu nadrzędnego, użyj własnego kodu.  
  
 W przeciwnym razie jest zgłaszany wyjątek.<xref:System.Data.SqlClient.SqlException>  
  
 Aby uzyskać więcej informacji, zobacz [jak: Usuń wiersze z bazy danych](how-to-delete-rows-from-the-database.md).  
  
## <a name="expression-not-queryable"></a>Wyrażenie nie jest Queryable  
 W przypadku uzyskania wyrażenia "wyrażenie [wyrażenie] nie jest Queryable; Czy brakuje odwołania do zestawu? " błąd, upewnij się, że:  
  
- Twoja aplikacja jest ukierunkowana na .NET Compact Framework 3,5.  
  
- Istnieje odwołanie do `System.Core.dll` i `System.Data.Linq.dll`.  
  
- C# <xref:System.Linq> `using` Masz dyrektywę <xref:System.Data.Linq>(Visual Basic) lub () dla i. `Imports`  
  
## <a name="duplicatekeyexception"></a>DuplicateKeyException  
 W trakcie debugowania [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu można przechodzenie między relacjami jednostek. Dzięki temu te elementy są umieszczane w pamięci podręcznej i [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] będą miały świadomość ich obecności. Jeśli następnie spróbujesz wykonać <xref:System.Data.Linq.Table%601.Attach%2A> lub <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> lub podobną metodę, która produkuje wiele wierszy, które mają ten sam klucz, <xref:System.Data.Linq.DuplicateKeyException> zostanie zgłoszony.  
  
## <a name="string-concatenation-exceptions"></a>Wyjątki łączenia ciągów  
 Łączenie z operandami zamapowanymi `[n]text` na i `[n][var]char` inne nie jest obsługiwane. Wyjątek jest zgłaszany w przypadku łączenia ciągów mapowanych na dwa różne zestawy typów. Aby uzyskać więcej informacji, zobacz [metody System. String](system-string-methods.md).  
  
## <a name="skip-and-take-exceptions-in-sql-server-2000"></a>Pomiń i podejmij wyjątki w SQL Server 2000  
 Należy używać członków tożsamości (<xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>) w przypadku korzystania z bazy danych SQL Server 2000 lub <xref:System.Linq.Queryable.Skip%2A> jej używania <xref:System.Linq.Queryable.Take%2A> . Zapytanie musi znajdować się w odniesieniu do pojedynczej tabeli (to nie sprzężenia) lub <xref:System.Linq.Queryable.Distinct%2A>być <xref:System.Linq.Queryable.Except%2A>operacją, <xref:System.Linq.Queryable.Union%2A> , <xref:System.Linq.Queryable.Intersect%2A>, <xref:System.Linq.Queryable.Concat%2A> lub i nie może zawierać operacji. Aby uzyskać więcej informacji, zobacz sekcję "Pomoc techniczna w SQL Server 2000" w [standardowym tłumaczeniu operatora zapytań](standard-query-operator-translation.md).  
  
 To wymaganie nie ma zastosowania do SQL Server 2005.  
  
## <a name="groupby-invalidoperationexception"></a>InvalidOperationException GroupBy  
 Ten wyjątek jest zgłaszany, gdy wartość kolumny jest równa <xref:System.Linq.Enumerable.GroupBy%2A> null w zapytaniu, `boolean` które grupuje wyrażenie `group x by (Phone==@phone)`, takie jak. Ponieważ wyrażenie ma `boolean`wartość, klucz jest wywnioskowany `boolean`jako, nie `nullable` `boolean`. Gdy przetłumaczone porównanie daje wartość null, podejmowana jest próba przypisania `nullable` `boolean` `boolean`do i, a wyjątek jest zgłaszany.  
  
 Aby uniknąć tej sytuacji (przy założeniu, że chcesz traktować wartości null jako FAŁSZ), użyj podejścia, takiego jak:  
  
 `GroupBy="(Phone != null) && (Phone=@Phone)"`  
  
## <a name="oncreated-partial-method"></a>OnCreated () — Metoda częściowa  
 Wygenerowana Metoda `OnCreated()` jest wywoływana za każdym razem, gdy Konstruktor obiektów jest wywoływany, łącznie z [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenariuszem, w którym Konstruktor tworzy kopię dla oryginalnych wartości. To zachowanie należy wziąć pod uwagę w przypadku zaimplementowania `OnCreated()` metody we własnej klasie częściowej.  
  
## <a name="see-also"></a>Zobacz także

- [Obsługa debugowania](debugging-support.md)
- [Często zadawane pytania](frequently-asked-questions.md)
