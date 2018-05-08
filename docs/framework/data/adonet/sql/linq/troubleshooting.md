---
title: Rozwiązywanie problemów
ms.date: 03/30/2017
ms.assetid: 8cd4401c-b12c-4116-a421-f3dcffa65670
ms.openlocfilehash: 24c7ddd42a4e66785921d9c63a6a757d9806503d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="troubleshooting"></a>Rozwiązywanie problemów
Poniższe informacje ujawnia niektóre problemy, które mogą wystąpić w Twojej [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacji i zawiera propozycje, aby uniknąć lub w przeciwnym razie ograniczenia wpływu tych problemów.  
  
 Dodatkowe problemy zostały rozwiązane w [— często zadawane pytania](../../../../../../docs/framework/data/adonet/sql/linq/frequently-asked-questions.md).  
  
## <a name="unsupported-standard-query-operators"></a>Nieobsługiwany standardowych operatorów zapytań  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie obsługuje wszystkich metod operator standardowego zapytania (na przykład <xref:System.Linq.Enumerable.ElementAt%2A>). W związku z tym projekty kompilowane nadal może spowodować błędy środowiska wykonawczego. Aby uzyskać więcej informacji, zobacz [standardowe Translacja Operator zapytania](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md).  
  
## <a name="memory-issues"></a>Problemy z pamięcią  
 Jeśli zapytanie obejmuje kolekcji w pamięci i [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601>, może być można wykonać zapytania w pamięci, w zależności od kolejności, w którym określono dwie kolekcje. Jeśli zapytanie musi zostać wykonana w pamięci, następnie danych z tabeli bazy danych należy do pobrania.  
  
 Takie podejście jest nieefektywne i mogą spowodować znaczne użycie pamięci i procesora. Należy unikać takich kwerend wielu domen.  
  
## <a name="file-names-and-sqlmetal"></a>Nazwy plików i SQLMetal  
 Aby określić nazwę pliku wejściowego, należy dodać ją do wiersza polecenia jako plik wejściowy. Łącznie z nazwą pliku w ciągu połączenia (przy użyciu **/conn** opcji) nie jest obsługiwana. Aby uzyskać więcej informacji, zobacz [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="class-library-projects"></a>Projektów biblioteki klas  
 [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] Tworzy ciąg połączenia w `app.config` pliku projektu. W projektach biblioteki klas `app.config` plik nie jest używany. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] używany w plikach czasu projektowania w podanym ciągu połączenia. Zmiana wartości w `app.config` nie powoduje zmiany bazy danych, do której aplikacja nawiązuje połączenie.  
  
## <a name="cascade-delete"></a>Usuwanie kaskadowe  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie obsługuje ani nie rozpoznaje operacjami usuwania kaskadowego. Jeśli chcesz usunąć wiersza w tabeli, która ma ograniczenia na nim, należy wykonać jedną z następujących czynności:  
  
-   Ustaw `ON DELETE CASCADE` reguły w ograniczenie klucza obcego w bazie danych.  
  
-   Najpierw usuń obiekty podrzędne, które zapobiec usunięciu obiektu nadrzędnego przy użyciu własnego kodu.  
  
 W przeciwnym razie <xref:System.Data.SqlClient.SqlException> wyjątku.  
  
 Aby uzyskać więcej informacji, zobacz [porady: usuwanie wierszy z bazy danych](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).  
  
## <a name="expression-not-queryable"></a>Wyrażenie nie zapytań  
 Jeśli otrzymasz "wyrażenie [wyrażenie] nie jest kolejność; czy nie brakuje odwołania do zestawu?" błąd, upewnij się, że z następujących czynności:  
  
-   Aplikacja jest docelowo [!INCLUDE[compact_v35_short](../../../../../../includes/compact-v35-short-md.md)].  
  
-   Zawierają odwołanie do `System.Core.dll` i `System.Data.Linq.dll`.  
  
-   Masz `Imports` (Visual Basic) lub `using` — dyrektywa (C#) dla <xref:System.Linq> i <xref:System.Data.Linq>.  
  
## <a name="duplicatekeyexception"></a>DuplicateKeyException  
 W trakcie debugowania [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu, może przejść przez relacjami jednostek. To powoduje przeniesienie tych elementów do pamięci podręcznej, i [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uzyska informacje o ich obecności. Jeśli użytkownik spróbuje wykonać <xref:System.Data.Linq.Table%601.Attach%2A> lub <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> lub podobnej metody tworzącego wiele wierszy, które mają ten sam klucz <xref:System.Data.Linq.DuplicateKeyException> jest generowany.  
  
## <a name="string-concatenation-exceptions"></a>Wyjątki łączenie ciągów  
 Łączenie w wypadku argumentów operacji mapowane na `[n]text` i innych `[n][var]char` nie jest obsługiwane. Do łączenia ciągów zamapowane na dwie różne zestawy typów jest zgłaszany wyjątek. Aby uzyskać więcej informacji, zobacz [metod typu System.String](../../../../../../docs/framework/data/adonet/sql/linq/system-string-methods.md).  
  
## <a name="skip-and-take-exceptions-in-sql-server-2000"></a>SKIP i Take wyjątków w programie SQL Server 2000  
 Należy użyć członków tożsamości (<xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>) korzystając <xref:System.Linq.Queryable.Take%2A> lub <xref:System.Linq.Queryable.Skip%2A> w bazie danych programu SQL Server 2000. Zapytanie musi być na jednej tabeli (czyli nie sprzężenia) lub <xref:System.Linq.Queryable.Distinct%2A>, <xref:System.Linq.Queryable.Except%2A>, <xref:System.Linq.Queryable.Intersect%2A>, lub <xref:System.Linq.Queryable.Union%2A> operację i nie może zawierać <xref:System.Linq.Queryable.Concat%2A> operacji. Aby uzyskać więcej informacji, zobacz sekcję "Obsługa programu SQL Server 2000" w [standardowe Translacja Operator zapytania](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md).  
  
 Ten wymóg nie ma zastosowania do [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)].  
  
## <a name="groupby-invalidoperationexception"></a>GroupBy InvalidOperationException  
 Zgłoszenia tego wyjątku, gdy wartość kolumny jest równa null w <xref:System.Linq.Enumerable.GroupBy%2A> zapytania, który grupuje przez `boolean` wyrażenia, takich jak `group x by (Phone==@phone)`. Ponieważ wyrażenie jest `boolean`, klucz jest wywnioskowany jako `boolean`, a nie `nullable``boolean`. Gdy przetłumaczonego porównanie daje wartość null, aby przypisać podejmowana jest próba `nullable``boolean` do `boolean`, i jest wyjątek.  
  
 Aby uniknąć tej sytuacji (przy założeniu, że mają być traktowane jako FAŁSZ wartości null), należy użyć podejście podobne do poniższych:  
  
 `GroupBy="(Phone != null) && (Phone=@Phone)"`  
  
## <a name="oncreated-partial-method"></a>Metoda częściowa OnCreated()  
 Metoda wygenerowanego `OnCreated()` jest wywoływana za każdym razem, wywołania konstruktora obiektu, w którym w tym scenariuszu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] wywołuje konstruktor do skopiowania do oryginalnych wartości. Uwzględniać to zachowanie w przypadku zastosowania `OnCreated()` metody w klasie częściowej.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa debugowania](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)  
 [Często zadawane pytania](../../../../../../docs/framework/data/adonet/sql/linq/frequently-asked-questions.md)
