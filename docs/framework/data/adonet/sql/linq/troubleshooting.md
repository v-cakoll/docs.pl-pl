---
title: Rozwiązywanie problemów
ms.date: 03/30/2017
ms.assetid: 8cd4401c-b12c-4116-a421-f3dcffa65670
ms.openlocfilehash: ebcfec475d20492f5ce1f971163544d9faa52223
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64613765"
---
# <a name="troubleshooting"></a>Rozwiązywanie problemów
Poniższe informacje przedstawia niektóre problemy, które mogą wystąpić w swojej [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacji i oferuje sugestie, aby uniknąć lub w przeciwnym razie ograniczenia wpływu tych problemów.  
  
 Dodatkowe problemy zostały rozwiązane w [— często zadawane pytania](../../../../../../docs/framework/data/adonet/sql/linq/frequently-asked-questions.md).  
  
## <a name="unsupported-standard-query-operators"></a>Nieobsługiwana standardowych operatorów zapytań  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie obsługuje wszystkie metody standardowego operatora zapytań (na przykład <xref:System.Linq.Enumerable.ElementAt%2A>). W rezultacie projekty kompilowane nadal może spowodować błędy czasu wykonywania. Aby uzyskać więcej informacji, zobacz [standardowa translacji operatora zapytania](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md).  
  
## <a name="memory-issues"></a>Problemy z pamięcią  
 Jeśli zapytanie obejmuje kolekcji w pamięci i [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601>, być może można wykonać zapytania w pamięci, w zależności od kolejności, w której określane są dwie kolekcje. Jeśli zapytanie musi zostać wykonana w pamięci, następnie dane z tabeli bazy danych należy do pobrania.  
  
 To podejście jest nieefektywne i może spowodować znaczne obciążenie pamięci i procesora. Należy unikać takich zapytania obejmujące wiele domen.  
  
## <a name="file-names-and-sqlmetal"></a>Nazwy plików i SQLMetal  
 Aby określić nazwę pliku wejściowego, należy dodać ją do wiersza polecenia jako plik wejściowy. Łącznie z nazwą pliku w parametrach połączenia (przy użyciu **/conn** opcja) nie jest obsługiwane. Aby uzyskać więcej informacji, zobacz [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="class-library-projects"></a>Projekty bibliotek klas  
 [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] Tworzy ciąg połączenia w `app.config` pliku projektu. W projektach biblioteki klas `app.config` plik nie jest używany. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] korzysta z plików czasu projektowania w podanym ciągu połączenia. Zmiana wartości w `app.config` nie zmienia się z bazą danych, z którym łączy się aplikacja.  
  
## <a name="cascade-delete"></a>Usuwanie kaskadowe  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie obsługuje ani nie rozpoznają operations usuwanie kaskadowe. Aby usunąć wiersz w tabeli, która ma ograniczenia względem go, należy wykonać jedną z następujących czynności:  
  
- Ustaw `ON DELETE CASCADE` reguły w ograniczenie klucza obcego w bazie danych.  
  
- Użyj własnego kodu, aby najpierw usunąć obiekty podrzędne, które uniemożliwiają usunięcie obiektu nadrzędnego.  
  
 W przeciwnym razie <xref:System.Data.SqlClient.SqlException> jest zgłaszany wyjątek.  
  
 Aby uzyskać więcej informacji, zobacz [jak: Usuwanie wierszy z bazy danych](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).  
  
## <a name="expression-not-queryable"></a>Wyrażenie nie umożliwia zadawania zapytań  
 Jeśli zostanie wyświetlony, "wyrażenie [wyrażenie] jest nie umożliwia zadawania zapytań; czy nie brakuje odwołania do zestawu?" błąd, upewnij się, z następujących czynności:  
  
- Aplikacja jest przeznaczony dla [!INCLUDE[compact_v35_short](../../../../../../includes/compact-v35-short-md.md)].  
  
- Odwołania do `System.Core.dll` i `System.Data.Linq.dll`.  
  
- Masz `Imports` (Visual Basic) lub `using` — dyrektywa (C#) dla <xref:System.Linq> i <xref:System.Data.Linq>.  
  
## <a name="duplicatekeyexception"></a>DuplicateKeyException  
 W trakcie debugowania [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu, może przechodzić przez relacji jednostek. Ten sposób zapewniają te elementy w pamięci podręcznej i [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uzyska informacje o ich obecności. Jeśli zostanie podjęta próba wykonania <xref:System.Data.Linq.Table%601.Attach%2A> lub <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> lub podobnej metody, która tworzy wiele wierszy, które mają ten sam klucz <xref:System.Data.Linq.DuplicateKeyException> zgłaszany.  
  
## <a name="string-concatenation-exceptions"></a>Wyjątki konkatenacji ciągów  
 Łączenie w przypadku argumentów operacji mapowane na `[n]text` i innych `[n][var]char` nie jest obsługiwane. Wyjątek jest generowany dla łączenia ciągów mapowany na dwa różne zestawy typów. Aby uzyskać więcej informacji, zobacz [metody System.String](../../../../../../docs/framework/data/adonet/sql/linq/system-string-methods.md).  
  
## <a name="skip-and-take-exceptions-in-sql-server-2000"></a>Pomiń i Pobierz wyjątki w programie SQL Server 2000  
 Należy użyć składowych tożsamości (<xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>) zastosowania <xref:System.Linq.Queryable.Take%2A> lub <xref:System.Linq.Queryable.Skip%2A> względem bazy danych programu SQL Server 2000. Zapytanie musi być względem pojedynczej tabeli (czyli nie sprzężenia) lub <xref:System.Linq.Queryable.Distinct%2A>, <xref:System.Linq.Queryable.Except%2A>, <xref:System.Linq.Queryable.Intersect%2A>, lub <xref:System.Linq.Queryable.Union%2A> operacji i nie może zawierać <xref:System.Linq.Queryable.Concat%2A> operacji. Aby uzyskać więcej informacji, zobacz sekcję "Obsługa programu SQL Server 2000" w [standardowa translacji operatora zapytania](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md).  
  
 Ten wymóg nie ma zastosowania do [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)].  
  
## <a name="groupby-invalidoperationexception"></a>GroupBy InvalidOperationException  
 Ten wyjątek jest zgłaszany, gdy wartość kolumny ma wartość null w <xref:System.Linq.Enumerable.GroupBy%2A> kwerendę, która grupuje według `boolean` wyrażenie, takie jak `group x by (Phone==@phone)`. Ponieważ wyrażenie jest `boolean`, klucz wywnioskowana jest `boolean`, a nie `nullable` `boolean`. Gdy przetłumaczone porównania tworzy wartość null, aby przypisać zostanie podjęta próba `nullable` `boolean` do `boolean`, i jest wyjątek.  
  
 Aby uniknąć tej sytuacji (przy założeniu, że ma traktować wartości null jako FAŁSZ), należy użyć podejścia, takie jak następujące:  
  
 `GroupBy="(Phone != null) && (Phone=@Phone)"`  
  
## <a name="oncreated-partial-method"></a>OnCreated() Partial Method  
 Wygenerowana metoda `OnCreated()` jest wywoływana za każdym razem, wywoływany jest konstruktor obiektu, w którym w tym scenariuszu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] wywołuje konstruktor kopiowania do oryginalnych wartości. Uwzględnia to zachowanie w przypadku zaimplementowania `OnCreated()` metody w klasie częściowej.  
  
## <a name="see-also"></a>Zobacz także

- [Obsługa debugowania](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)
- [Często zadawane pytania](../../../../../../docs/framework/data/adonet/sql/linq/frequently-asked-questions.md)
