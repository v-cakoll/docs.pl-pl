---
title: Nauka przez przewodniki
ms.date: 03/30/2017
ms.assetid: a8ae2965-6a49-4155-89b0-7fab2c488ab1
ms.openlocfilehash: 4beb9944a13fd2f76d7305b4d84230fcc33483be
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781316"
---
# <a name="learning-by-walkthroughs"></a>Nauka przez przewodniki
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Dokumentacja zawiera kilka przewodników. Ten temat dotyczy niektórych ogólnych problemów z instruktażem (w tym rozwiązywania problemów) i zawiera linki do kilku przewodników dotyczących [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]poziomu wejścia do uczenia się.  
  
> [!NOTE]
> Instruktaże w tej sekcji wprowadzenie uwidaczniają kod podstawowy, który obsługuje [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technologię. W rzeczywistej obsłużeniu zwykle projekty Object Relational Designer i Windows Forms do implementowania [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacji. Dokumentacja projektanta O/R zawiera przykłady i instruktaże do tego celu.  
  
## <a name="getting-started-walkthroughs"></a>Instruktaże Wprowadzenie  
 W tej sekcji są dostępne kilka instruktaży. Te przewodniki są oparte na przykładowej bazie danych Northwind i stanowią [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] łagodne tempo z minimalnymi złożonością.  
  
 Typowy postęp powinien być następujący:  
  
|Jakim|Visual Basic|C#|  
|---------------|------------------|---------|  
|Utwórz klasę jednostki i wykonaj proste zapytanie.|[Przewodnik: Prosty model obiektu i zapytanie (Visual Basic)](walkthrough-simple-object-model-and-query-visual-basic.md)|[Przewodnik: Prosty model obiektu i zapytanie (C#)](walkthrough-simple-object-model-and-query-csharp.md)|  
|Dodaj drugą klasę i wykonaj bardziej skomplikowaną kwerendę.<br /><br /> (Wymaga zakończenia poprzedniego przewodnika).|[Przewodnik: Wykonywanie zapytań w relacjach (Visual Basic)](walkthrough-querying-across-relationships-visual-basic.md)|[Przewodnik: Wykonywanie zapytań w relacjachC#()](walkthrough-querying-across-relationships-csharp.md)|  
|Dodawanie, zmienianie i usuwanie elementów w bazie danych.|[Przewodnik: Manipulowanie danymi (Visual Basic)](walkthrough-manipulating-data-visual-basic.md)|[Przewodnik: Manipulowanie danymi (C#)](walkthrough-manipulating-data-csharp.md)|  
|Użyj procedur składowanych.|[Przewodnik: Używanie tylko procedur składowanych (Visual Basic)](walkthrough-using-only-stored-procedures-visual-basic.md)|[Przewodnik: Używanie tylko procedur składowanychC#()](walkthrough-using-only-stored-procedures-csharp.md)|  
  
## <a name="general"></a>Ogólne  
 Poniższe informacje dotyczą następujących przewodników:  
  
- Naturalne Każdy [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Przewodnik używa programu Visual Studio jako zintegrowanego środowiska programistycznego (IDE).  
  
- Aparaty SQL: Te instruktaże są zapisywane do wdrożenia przy użyciu SQL Server Express. Jeśli nie masz SQL Server Express, możesz pobrać bezpłatnie. Aby uzyskać więcej informacji, zobacz [Pobieranie przykładowych baz danych](downloading-sample-databases.md).  
  
    > [!NOTE]
    > [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Instruktaże używają nazwy pliku jako parametrów połączenia. Po prostu określenie nazwy pliku jest wygodą, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] która zapewnia użytkownikom SQL Server Express. Zawsze należy zwrócić uwagę na problemy z zabezpieczeniami. Aby uzyskać więcej informacji, zobacz [zabezpieczenia w LINQ to SQL](security-in-linq-to-sql.md).  
  
- [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Instruktaże wymagają zwykle przykładowej bazy danych Northwind. Aby uzyskać więcej informacji, zobacz [Pobieranie przykładowych baz danych](downloading-sample-databases.md).  
  
- Okna dialogowe i polecenia menu wyświetlane w przewodnikach mogą różnić się od tych opisanych w pomocy, w zależności od ustawień aktywnych lub wersji programu Visual Studio. Aby zmienić ustawienia, kliknij przycisk **Importuj i Eksportuj ustawienia** w menu **Narzędzia** . Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
- W przypadku przewodników związanych z wielowarstwowymi scenariuszami serwer musi znajdować się na komputerze, który jest odrębny od komputera deweloperskiego, a użytkownik musi mieć odpowiednie uprawnienia dostępu do serwera.  
  
- Nazwa klasy, która zwykle reprezentuje tabelę Orders w przykładowej bazie danych Northwind, to `[Order]`. Ucieczki jest wymagane, ponieważ `Order` jest słowem kluczowym w Visual Basic.  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 Błędy w czasie wykonywania mogą wystąpić, ponieważ nie masz wystarczających uprawnień, aby uzyskać dostęp do baz danych używanych w tych przewodnikach. Zapoznaj się z poniższymi krokami, aby pomóc w rozwiązaniu najbardziej typowych problemów.  
  
### <a name="log-on-issues"></a>Problemy z logowaniem  
 Aplikacja może próbować uzyskać dostęp do bazy danych za pomocą logowania do bazy danych, której nie akceptuje.  
  
##### <a name="to-verify-or-change-the-database-log-on"></a>Aby sprawdzić lub zmienić logowanie do bazy danych  
  
1. W menu **Start** systemu Windows wskaż **wszystkie programy**, **Microsoft SQL Server 2005**, wskaż **Narzędzia konfiguracji**, a następnie kliknij **SQL Server Configuration Manager**.  
  
2. W lewym okienku **Configuration Manager SQL Server**kliknij pozycję **SQL Server 2005 Services**.  
  
3. W prawym okienku kliknij prawym przyciskiem myszy pozycję **SQL Server (SQLExpress)** , a następnie kliknij pozycję **Właściwości**.  
  
4. Kliknij kartę **Logowanie** i sprawdź, jak próbujesz się zalogować na serwerze.  
  
     W większości przypadków działa **System lokalny** .  
  
     Jeśli wprowadzisz zmiany, kliknij przycisk **Uruchom ponownie** , aby ponownie uruchomić usługę.  
  
### <a name="protocols"></a>Protokołów  
 Czasami protokoły mogą nie być poprawnie ustawione dla aplikacji w celu uzyskania dostępu do bazy danych. Na przykład protokół **nazwanych potoków** , który jest wymagany dla przewodników w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], nie jest domyślnie włączony.  
  
##### <a name="to-enable-the-named-pipes-protocol"></a>Aby włączyć protokół nazwanych potoków  
  
1. W lewym okienku **Configuration Manager SQL Server**rozwiń węzeł **konfiguracja sieci w SQL Server 2005**, a następnie kliknij pozycję **Protokoły dla programu SQLExpress**.  
  
2. Upewnij się, że w okienku po prawej stronie jest włączony protokół **nazwanych potoków** . Jeśli tak nie jest, kliknij prawym przyciskiem myszy pozycję **nazwy potoki** , a następnie kliknij pozycję **Włącz**.  
  
     Trzeba będzie zatrzymać i ponownie uruchomić usługę. Postępuj zgodnie z instrukcjami w następnym bloku.  
  
### <a name="stopping-and-restarting-the-service"></a>Zatrzymywanie i ponowne uruchamianie usługi  
 Aby zmiany zaczęły obowiązywać, należy zatrzymać i ponownie uruchomić usługi.  
  
##### <a name="to-stop-and-restart-the-service"></a>Aby zatrzymać i ponownie uruchomić usługę  
  
1. W lewym okienku **Configuration Manager SQL Server**kliknij pozycję **SQL Server 2005 Services**.  
  
2. W prawym okienku kliknij prawym przyciskiem myszy pozycję **SQL Server (SQLExpress)** , a następnie kliknij przycisk **Zatrzymaj**.  
  
3. Kliknij prawym przyciskiem myszy pozycję **SQL Server (SQLExpress)** , a następnie kliknij pozycję **Uruchom ponownie**.  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie](getting-started.md)
