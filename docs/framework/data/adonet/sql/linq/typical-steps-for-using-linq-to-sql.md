---
title: Typowe kroki dotyczące korzystania z LINQ do SQL
ms.date: 03/30/2017
ms.assetid: 9a88bd51-bd74-48f7-a9b1-f650e8d55a3e
ms.openlocfilehash: e45f53b8fdea877bb3921b77d485abcab4393df7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="typical-steps-for-using-linq-to-sql"></a>Typowe kroki dotyczące korzystania z LINQ do SQL
Aby zaimplementować [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacji, wykonaj kroki opisane w dalszej części tego tematu. Należy pamiętać, że wiele czynności są opcjonalne. Jest bardzo możliwe, że można użyć modelu obiektów w stanie domyślnym.  
  
 Naprawdę szybki start, można użyć [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] do tworzenia modelu obiektu i rozpoczęcie kodowania zapytań.  
  
## <a name="creating-the-object-model"></a>Tworzenie modelu obiektów  
 Pierwszym krokiem jest utworzenie modelu obiektu z metadanych istniejących relacyjnej bazy danych. Model obiektów reprezentuje bazy danych zgodnie z językiem programowania dewelopera. Aby uzyskać więcej informacji, zobacz [LINQ w modelu obiektu SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).  
  
### <a name="1-select-a-tool-to-create-the-model"></a>1. Wybierz narzędzia do tworzenia modelu.  
 Trzy narzędzia są dostępne do tworzenia modelu.  
  
-   programu [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]  
  
     Ten Projektant udostępnia interfejs użytkownika sformatowanego do tworzenia modelu obiektów z istniejącej bazy danych. To narzędzie jest częścią środowiska IDE programu Visual Studio i najlepiej nadaje się do małych i średnich baz danych.  
  
-   Narzędzie generowania kodu SQLMetal  
  
     To narzędzie wiersza polecenia zapewnia nieco inny zestaw opcji z [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)]. Modelowanie dużych baz danych najlepiej odbywa się za pomocą tego narzędzia. Aby uzyskać więcej informacji, zobacz [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
-   Edytor kodu  
  
     Można napisać własny kod za pomocą edytora kodu programu Visual Studio lub innego edytora. Nie zaleca się takie podejście, które mogą być podatne na błędy, po istniejącej bazy danych i można użyć dowolnego [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] lub narzędzie SQLMetal. Jednak edytora kodu może być przydatny do aktualizowania lub modyfikowania kodu, które zostały już wygenerowane za pomocą innych narzędzi. Aby uzyskać więcej informacji, zobacz [porady: dostosowywanie klas jednostek za pomocą edytora kodu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md).  
  
### <a name="2-select-the-kind-of-code-you-want-to-generate"></a>2. Wybierz typ kodu, który ma zostać wygenerowany.  
  
-   C# lub Visual Basic pliku kodu źródłowego dla opartych na atrybutach mapowania.  
  
     Następnie ten plik kodu są uwzględnione w projekcie programu Visual Studio. Aby uzyskać więcej informacji, zobacz [mapowania na podstawie atrybutów](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
-   Plik XML dla zewnętrznych mapowania.  
  
     Przy użyciu tej metody, można zachować metadanych mapowania poza kod aplikacji. Aby uzyskać więcej informacji, zobacz [zewnętrznych mapowania](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
    > [!NOTE]
    >  [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] Nie obsługuje generowania plików zewnętrznych mapowania. Aby wdrożyć tę funkcję, należy użyć narzędzia SQLMetal.  
  
-   Za pomocą pliku DBML, którą można zmienić przed wygenerowaniem pliku kodu końcowego.  
  
     Jest to zaawansowana funkcja.  
  
### <a name="3-refine-the-code-file-to-reflect-the-needs-of-your-application"></a>3. Dostosuj pliku kodu, aby uwzględnić wymagania aplikacji.  
 W tym celu możesz użyć dowolnej [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] lub edytora kodu.  
  
## <a name="using-the-object-model"></a>Za pomocą modelu obiektów  
 Na poniższej ilustracji przedstawiono relację między projektanta i dane w scenariuszu dwuwarstwowa. W innych sytuacjach, zobacz [N-warstwowa oraz zdalnych aplikacji za pomocą LINQ do SQL](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md).  
  
 ![DLinqObjectModel](../../../../../../docs/framework/data/adonet/sql/linq/media/dlinqobjectmodel.png "DLinqObjectModel")  
  
 Teraz, gdy masz model obiektów opisano informacje żądania i manipulować danymi w ramach tego modelu. Uważasz, że pod względem obiektów i właściwości w modelu obiektu, a nie w postaci liczby wierszy i kolumn bazy danych. Dotyczy bezpośrednio z bazą danych.  
  
 Gdy poinstruować [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] jednej wykonać zapytanie, które zostały opisane lub wywołanie `SubmitChanges()` danych, które można było manipulować [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] komunikuje się z bazą danych w języku bazy danych.  
  
 Następujące reprezentuje typowe etapy za pomocą modelu obiektów, które zostały utworzone.  
  
### <a name="1-create-queries-to-retrieve-information-from-the-database"></a>1. Tworzenie zapytań, aby pobrać informacje z bazy danych.  
 Aby uzyskać więcej informacji, zobacz [pojęcia zapytania](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md) i [przykłady zapytania](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md).  
  
### <a name="2-override-default-behaviors-for-insert-update-and-delete"></a>2. Zastąpić domyślne działania w operacjach wstawiania, aktualizacji i usuwania.  
 Ten krok jest opcjonalny. Aby uzyskać więcej informacji, zobacz [Dostosowywanie Insert, Update i operacji usunięcia](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
  
### <a name="3-set-appropriate-options-to-detect-and-report-concurrency-conflicts"></a>3. Ustaw odpowiednie opcje wykrywać i zgłaszać konfliktom współbieżności.  
 Model może narazić wartościami domyślnymi konfliktów współbieżności lub zmień, aby dostosować do własnych celów. Aby uzyskać więcej informacji, zobacz [porady: Określ, które elementy członkowskie są sprawdzane pod kątem konfliktom współbieżności](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md) i [porady: Określ podczas współbieżności wyjątki są zgłaszane](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-when-concurrency-exceptions-are-thrown.md).  
  
### <a name="4-establish-an-inheritance-hierarchy"></a>4. Ustanów hierarchii dziedziczenia.  
 Ten krok jest opcjonalny. Aby uzyskać więcej informacji, zobacz [Obsługa dziedziczenia](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md).  
  
### <a name="5-provide-an-appropriate-user-interface"></a>5. Podaj odpowiedni interfejs.  
 Ten krok jest opcjonalny i zależy od sposobu użycia aplikacji.  
  
### <a name="6-debug-and-test-your-application"></a>6. Debugowania i testowania aplikacji.  
 Aby uzyskać więcej informacji, zobacz [obsługi debugowania](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)  
 [Tworzenie modelu obiektu](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)  
 [Procedury składowane](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
