---
title: Typowe kroki dotyczące korzystania z LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 9a88bd51-bd74-48f7-a9b1-f650e8d55a3e
ms.openlocfilehash: c7964c821a838e027302cddce704d86cc6a34f66
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792341"
---
# <a name="typical-steps-for-using-linq-to-sql"></a>Typowe kroki dotyczące korzystania z LINQ to SQL
Aby zaimplementować [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikację, wykonaj kroki opisane w dalszej części tego tematu. Należy zauważyć, że wiele kroków jest opcjonalnych. Jest to bardzo możliwe, że można użyć modelu obiektów w stanie domyślnym.  
  
 Aby szybko rozpocząć pracę, użyj Object Relational Designer, aby utworzyć model obiektów i rozpocząć kodowanie zapytań.  
  
## <a name="creating-the-object-model"></a>Tworzenie modelu obiektu  
 Pierwszym krokiem jest utworzenie modelu obiektu na podstawie metadanych istniejącej relacyjnej bazy danych. Model obiektów reprezentuje bazę danych zgodnie z językiem programowania dewelopera. Aby uzyskać więcej informacji, zobacz [model obiektów LINQ to SQL](the-linq-to-sql-object-model.md).  
  
### <a name="1-select-a-tool-to-create-the-model"></a>1. Wybierz narzędzie, aby utworzyć model.  
 Do utworzenia modelu dostępne są trzy narzędzia.  
  
- Object Relational Designer  
  
     Ten Projektant udostępnia rozbudowany interfejs użytkownika służący do tworzenia modelu obiektów z istniejącej bazy danych. To narzędzie jest częścią środowiska IDE programu Visual Studio i najlepiej jest dostosowane do małych i średnich baz danych.  
  
- Narzędzie do generowania kodu SQLMetal  
  
     To narzędzie wiersza polecenia zapewnia nieco inny zestaw opcji z projektanta O/R. Modelowanie dużych baz danych jest najlepszym rozwiązaniem przy użyciu tego narzędzia. Aby uzyskać więcej informacji, zobacz [SQLMetal. exe (Narzędzie generowania kodu)](../../../../tools/sqlmetal-exe-code-generation-tool.md).  
  
- Edytor kodu  
  
     Swój własny kod można napisać przy użyciu edytora kodu programu Visual Studio lub innego edytora. Firma Microsoft nie zaleca tego podejścia, które może być podatne na błędy, gdy istnieje istniejąca baza danych i może korzystać z projektanta O/R lub narzędzia SQLMetal. Jednak Edytor kodu może być cenny dla rafinacji lub modyfikacji kodu, który został już wygenerowany przy użyciu innych narzędzi. Aby uzyskać więcej informacji, zobacz [jak: Dostosuj klasy jednostki za pomocą edytora](how-to-customize-entity-classes-by-using-the-code-editor.md)kodu.  
  
### <a name="2-select-the-kind-of-code-you-want-to-generate"></a>2. Wybierz rodzaj kodu, który chcesz wygenerować.  
  
- C# Lub Visual Basic plik kodu źródłowego dla mapowania opartego na atrybutach.  
  
     Następnie można dołączyć ten plik kodu do projektu programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Mapowanie oparte na atrybutach](attribute-based-mapping.md).  
  
- Plik XML dla mapowania zewnętrznego.  
  
     Korzystając z tej metody, można zachować metadane mapowania z kodu aplikacji. Aby uzyskać więcej informacji, zobacz [Mapowanie zewnętrzne](external-mapping.md).  
  
    > [!NOTE]
    > Projektant O/R nie obsługuje generowania plików mapowania zewnętrznego. Aby zaimplementować tę funkcję, należy użyć narzędzia SQLMetal.  
  
- Plik DBML, który można modyfikować przed wygenerowaniem końcowego pliku kodu.  
  
     Jest to funkcja zaawansowana.  
  
### <a name="3-refine-the-code-file-to-reflect-the-needs-of-your-application"></a>3. Uściślij plik kodu w celu odzwierciedlenia potrzeb aplikacji.  
 W tym celu można użyć projektanta O/R lub edytora kodu.  
  
## <a name="using-the-object-model"></a>Korzystanie z modelu obiektów  
 Na poniższej ilustracji przedstawiono relacje między deweloperem a danymi w scenariuszu dwuwarstwowym. W przypadku innych scenariuszy zobacz [aplikacje N-warstwowe i zdalne za pomocą LINQ to SQL](n-tier-and-remote-applications-with-linq-to-sql.md).  
  
 ![Zrzut ekranu pokazujący model obiektów LINQ.](./media/the-linq-to-sql-object-model/linq-object-model-two-tier.png)  
  
 Teraz, gdy masz już model obiektów, opiszemy żądania informacji i manipulowanie danymi w tym modelu. Myślisz o obiektach i właściwościach w modelu obiektów, a nie w odniesieniu do wierszy i kolumn bazy danych. Nie można bezpośrednio obsłużyć bazy danych.  
  
 Gdy użytkownik instruuje [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] wykonać zapytanie, które zostało opisane lub wywołało `SubmitChanges()` dane, które były manipulowane, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] komunikuje się z bazą danych w języku bazy danych.  
  
 Poniżej przedstawiono typowe kroki dotyczące użycia modelu obiektów, który został utworzony.  
  
### <a name="1-create-queries-to-retrieve-information-from-the-database"></a>1. Utwórz zapytania, aby pobrać informacje z bazy danych.  
 Aby uzyskać więcej informacji, zobacz [pojęcia dotyczące zapytań](query-concepts.md) i [przykłady zapytań](query-examples.md).  
  
### <a name="2-override-default-behaviors-for-insert-update-and-delete"></a>2. Zastąp domyślne zachowania dla operacji INSERT, Update i DELETE.  
 Ten krok jest opcjonalny. Aby uzyskać więcej informacji, zobacz [Dostosowywanie operacji wstawiania, aktualizowania i usuwania](customizing-insert-update-and-delete-operations.md).  
  
### <a name="3-set-appropriate-options-to-detect-and-report-concurrency-conflicts"></a>3. Ustaw odpowiednie opcje wykrywania i zgłaszania konfliktów współbieżności.  
 Możesz pozostawić model z wartościami domyślnymi do obsługi konfliktów współbieżności lub można go zmienić zgodnie z własnymi potrzebami. Aby uzyskać więcej informacji, zobacz [jak: Określ, które elementy członkowskie są testowane pod](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md) kątem [konfliktów współbieżności i jak: Określ, kiedy są zgłaszane](how-to-specify-when-concurrency-exceptions-are-thrown.md)wyjątki współbieżności.  
  
### <a name="4-establish-an-inheritance-hierarchy"></a>4. Ustanów hierarchię dziedziczenia.  
 Ten krok jest opcjonalny. Aby uzyskać więcej informacji, zobacz [Obsługa dziedziczenia](inheritance-support.md).  
  
### <a name="5-provide-an-appropriate-user-interface"></a>5. Podaj odpowiedni interfejs użytkownika.  
 Ten krok jest opcjonalny i zależy od tego, w jaki sposób aplikacja zostanie użyta.  
  
### <a name="6-debug-and-test-your-application"></a>6. Debuguj i Testuj aplikację.  
 Aby uzyskać więcej informacji, zobacz [obsługa debugowania](debugging-support.md).  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie](getting-started.md)
- [Tworzenie modelu obiektu](creating-the-object-model.md)
- [Procedury składowane](stored-procedures.md)
