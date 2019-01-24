---
title: Typowe kroki dotyczące korzystania z LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 9a88bd51-bd74-48f7-a9b1-f650e8d55a3e
ms.openlocfilehash: 32e81d08010f67b8eac19777a40826b18c440f83
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54548014"
---
# <a name="typical-steps-for-using-linq-to-sql"></a>Typowe kroki dotyczące korzystania z LINQ to SQL
Aby zaimplementować [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacji, wykonaj czynności opisane w dalszej części tego tematu. Należy pamiętać, że wiele kroki są opcjonalne. Jest bardzo prawdopodobne, że można użyć modelu obiektów w stanie domyślnym.  
  
 W przypadku bardzo szybko rozpoczniesz pracę, użyj [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] do tworzenia modelu obiektu i Rozpocznij kodowanie zapytań.  
  
## <a name="creating-the-object-model"></a>Tworzenie modelu obiektu  
 Pierwszym krokiem jest utworzenie modelu obiektu z metadanych istniejących relacyjnej bazy danych. Model obiektów reprezentuje bazę danych, zgodnie z językiem programowania dewelopera. Aby uzyskać więcej informacji, zobacz [LINQ to SQL Model obiektów](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).  
  
### <a name="1-select-a-tool-to-create-the-model"></a>1. Wybierz narzędzia do tworzenia modelu.  
 Trzy narzędzia są dostępne do tworzenia modelu.  
  
-   W [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]  
  
     Projektant zawiera zaawansowanego interfejsu użytkownika do tworzenia modeli obiektów z istniejącej bazy danych. To narzędzie jest częścią środowiska IDE programu Visual Studio i najlepiej nadaje się dla małych i średnich baz danych.  
  
-   Narzędzia do generowania kodu SQLMetal  
  
     To narzędzie wiersza polecenia oferuje nieco inny zestaw opcji dostępnych w [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)]. Modelowanie dużych baz danych najlepiej odbywa się za pomocą tego narzędzia. Aby uzyskać więcej informacji, zobacz [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
-   Edytor kodu  
  
     Za pomocą edytora kodu Visual Studio lub innego edytora, można napisać własny kod. Nie zaleca tego podejścia może być podatne na błędy, gdy masz istniejącą bazę danych i można użyć dowolnego [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] lub narzędzia SQLMetal. Jednak Edytor kodu może być przydatny w przypadku aktualizowania lub modyfikowania kodu, który został już wygenerowany przy użyciu innych narzędzi. Aby uzyskać więcej informacji, zobacz [jak: Dostosowywanie klas jednostek za pomocą edytora kodu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md).  
  
### <a name="2-select-the-kind-of-code-you-want-to-generate"></a>2. Wybierz typ kodu, które mają zostać wygenerowane.  
  
-   A C# lub plik kodu źródłowego języka Visual Basic dla opartych na atrybutach mapowania.  
  
     Następnie dodasz tego pliku kodu w projekcie programu Visual Studio. Aby uzyskać więcej informacji, zobacz [mapowanie oparte na atrybutach](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
-   Plik XML do mapowania zewnętrznych.  
  
     Za pomocą tej metody, można zachować metadanych mapowania poza swój kod aplikacji. Aby uzyskać więcej informacji, zobacz [mapowanie zewnętrzne](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
    > [!NOTE]
    >  [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] Nie obsługuje generowania zewnętrznych plików mapowania. Aby wdrożyć tę funkcję, należy użyć narzędzia SQLMetal.  
  
-   Za pomocą pliku DBML, którą można modyfikować, przed wygenerowaniem plik kodu końcowego.  
  
     Jest to zaawansowana funkcja.  
  
### <a name="3-refine-the-code-file-to-reflect-the-needs-of-your-application"></a>3. Dostosuj plik kodu w celu uwzględnienia wymagań aplikacji.  
 W tym celu można użyć dowolnego [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] lub edytora kodu.  
  
## <a name="using-the-object-model"></a>Za pomocą modelu obiektów  
 Poniższa ilustracja przedstawia relację między warstwą Deweloper a danych w scenariuszu dwuwarstwowej. W innych sytuacjach, zobacz [N-warstwowe i zdalne aplikacje za pomocą LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md).  
  
 ![DLinqObjectModel](../../../../../../docs/framework/data/adonet/sql/linq/media/dlinqobjectmodel.png "DLinqObjectModel")  
  
 Teraz, gdy model obiektów, opisz żądań informacji i manipulowanie danymi w ramach tego modelu. Należy traktować jako liczba obiektów i właściwości w modelu obiektu, a nie w wiersze i kolumny bazy danych. Dotyczy bezpośrednio z bazą danych.  
  
 Gdy poinstruować [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] do każdego wykonania zapytania, które zostały opisane lub wywołanie `SubmitChanges()` danych, które można było manipulować [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] komunikuje się z bazą danych w języku bazy danych.  
  
 Następujące reprezentuje typowe etapy za pomocą modelu obiektów, które zostały utworzone.  
  
### <a name="1-create-queries-to-retrieve-information-from-the-database"></a>1. Utwórz zapytania, aby pobrać informacje z bazy danych.  
 Aby uzyskać więcej informacji, zobacz [kwestie dotyczące zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md) i [przykłady zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md).  
  
### <a name="2-override-default-behaviors-for-insert-update-and-delete"></a>2. Zastąpienie zachowania domyślnego dla Insert, Update, a następnie usuń.  
 Ten krok jest opcjonalny. Aby uzyskać więcej informacji, zobacz [Dostosowywanie Insert, Update i operacje usuwania](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
  
### <a name="3-set-appropriate-options-to-detect-and-report-concurrency-conflicts"></a>3. Ustaw odpowiednie opcje, aby wykrywać i zgłaszać konfliktów współbieżności.  
 Model można pozostawić wartościami domyślnymi dla Obsługa konfliktów współbieżności lub można zmienić go do własnych własnych celów. Aby uzyskać więcej informacji, zobacz [jak: Określ, które elementy członkowskie są sprawdzane pod kątem konfliktów współbieżności](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md) i [jak: Określ są zgłaszane wyjątki współbieżności podczas](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-when-concurrency-exceptions-are-thrown.md).  
  
### <a name="4-establish-an-inheritance-hierarchy"></a>4. Ustanów hierarchii dziedziczenia.  
 Ten krok jest opcjonalny. Aby uzyskać więcej informacji, zobacz [Obsługa dziedziczenia](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md).  
  
### <a name="5-provide-an-appropriate-user-interface"></a>5. Zapewniają interfejs odpowiedniego użytkownika.  
 Ten krok jest opcjonalny i zależy od użycia aplikacji.  
  
### <a name="6-debug-and-test-your-application"></a>6. Debugowanie i testowanie aplikacji.  
 Aby uzyskać więcej informacji, zobacz [obsługę debugowania](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md).  
  
## <a name="see-also"></a>Zobacz także
- [Wprowadzenie](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
- [Tworzenie modelu obiektu](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
- [Procedury składowane](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
