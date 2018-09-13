---
title: Nauka przez przewodniki
ms.date: 03/30/2017
ms.assetid: a8ae2965-6a49-4155-89b0-7fab2c488ab1
ms.openlocfilehash: 1386d0e8fadddab5cd15818cb616bf331262e654
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44707740"
---
# <a name="learning-by-walkthroughs"></a>Nauka przez przewodniki
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Dokumentacja zawiera wskazówki dotyczące kilku. W tym temacie rozwiązuje problemy ogólne wskazówki (w tym Rozwiązywanie problemów) i zawiera łącza do kilku klasy podstawowej wskazówki umożliwiające uzyskiwanie informacji o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
> [!NOTE]
>  Przewodniki w tej sekcji wprowadzenie do udostępnienia do kodu podstawowego, który obsługuje [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technologii. W praktyce rzeczywiste zazwyczaj używasz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] i projektami Windows Forms swoje [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacji. [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] Dokumentacji zawiera przykłady i wskazówki, w tym celu.  
  
## <a name="getting-started-walkthroughs"></a>Wprowadzenie — wskazówki  
 Kilka wskazówki są dostępne w tej sekcji. Te przewodniki są oparte na przykładowej bazy danych Northwind i przedstawić [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] funkcji tempie delikatnie minimalnej złożoności.  
  
 Typowy postęp do wykonania będzie następujący:  
  
|Cel|Visual Basic|C#|  
|---------------|------------------|---------|  
|Utwórz klasę jednostki i wykonania prostego zapytania.|[Przewodnik: Prosty model obiektu i zapytanie (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-visual-basic.md)|[Przewodnik: Prosty model obiektu i zapytanie (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-csharp.md)|  
|Dodaj klasę sekundy, a następnie wykonaj bardziej złożonego zapytania.<br /><br /> (Wymaga zakończenia poprzednim przewodniku).|[Przewodnik: Wykonywanie zapytań w relacjach (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-visual-basic.md)|[Przewodnik: Wykonywanie zapytań w relacjach (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-csharp.md)|  
|Dodawanie, zmienianie i usuwać elementy w bazie danych.|[Przewodnik: Manipulowanie danymi (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-visual-basic.md)|[Przewodnik: Manipulowanie danymi (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-csharp.md)|  
|Używanie procedur składowanych.|[Przewodnik: Tylko przy użyciu procedur składowanych (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-using-only-stored-procedures-visual-basic.md)|[Przewodnik: Tylko przy użyciu procedur składowanych (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-using-only-stored-procedures-csharp.md)|  
  
## <a name="general"></a>Ogólne  
 Poniższe informacje ogólnie rzecz biorąc odnoszą się do tych przewodników:  
  
-   Środowisko: Każda [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Instruktaż korzysta z programu Visual Studio jako jego zintegrowanego środowiska programistycznego (IDE).  
  
-   Aparaty SQL: te przewodniki są zapisywane do zaimplementowania za pomocą programu SQL Server Express. Jeśli nie masz programu SQL Server Express, można pobrać bezpłatnie. Aby uzyskać więcej informacji, zobacz [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
    > [!NOTE]
    >  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] wskazówki dotyczące Użyj nazwy pliku jako parametry połączenia. Po prostu określenie nazwy pliku jest wygodne, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapewnia użytkownikom programu SQL Server Express. Zawsze należy zwrócić uwagę na problemy z zabezpieczeniami. Aby uzyskać więcej informacji, zobacz [zabezpieczeń w składniku LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md).  
  
-   [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] wskazówki dotyczące zwykle wymagają przykładowej bazy danych Northwind. Aby uzyskać więcej informacji, zobacz [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
-   Polecenia menu, widocznych na wskazówki i okien dialogowych mogą różnić się od tych opisanych w pomocy, w zależności od ustawień aktywnych lub wersji programu Visual Studio. Aby zmienić swoje ustawienia, kliknij przycisk **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
-   Aby uzyskać wskazówki dotyczące scenariuszy wielowarstwowych serwer musi znajdować się na komputerze, który różni się od komputerze deweloperskim, a musi mieć odpowiednie uprawnienia dostępu do serwera.  
  
-   Nazwa klasy, która zazwyczaj reprezentuje tabeli zamówienia w bazie danych Northwind jest `[Order]`. Anulowanie jest wymagane, ponieważ `Order` jest słowem kluczowym w języku Visual Basic.  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 Mogą wystąpić błędy czasu wykonywania, ponieważ nie masz wystarczających uprawnień dostępu do baz danych używanych w tych przewodników. Zobacz poniższe kroki, aby pomóc w rozwiązaniu typowych problemów.  
  
### <a name="log-on-issues"></a>Problemy dotyczące logowania  
 Aplikację może podjąć próbę dostępu do bazy danych za pomocą logowania bazy danych, które nie są akceptowane.  
  
##### <a name="to-verify-or-change-the-database-log-on"></a>Aby sprawdzić lub zmienić bazy danych logowania  
  
1.  Na Windows **Start** menu wskaż **wszystkie programy**, **Microsoft SQL Server 2005**, wskaż polecenie **narzędzia konfiguracji**, a następnie kliknij przycisk **Menedżera konfiguracji SQL Server**.  
  
2.  W okienku po lewej stronie **Menedżera konfiguracji SQL Server**, kliknij przycisk **usług SQL Server 2005**.  
  
3.  W okienku po prawej stronie kliknij prawym przyciskiem myszy **programu SQL Server (SQLEXPRESS)**, a następnie kliknij przycisk **właściwości**.  
  
4.  Kliknij przycisk **logowanie** kartę i sprawdź, jak chcesz zalogować się do serwera.  
  
     W większości przypadków **systemu lokalnego** działa.  
  
     Jeśli wprowadzisz zmiany, kliknij przycisk **ponowne uruchomienie** ponownie uruchomić usługę.  
  
### <a name="protocols"></a>Protokoły  
 Czasami protokołów wybrano prawidłowo aplikacji dostęp do bazy danych. Na przykład **potoków nazwanych** protokołu, który jest wymagany do instrukcji [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], nie jest domyślnie włączona.  
  
##### <a name="to-enable-the-named-pipes-protocol"></a>Aby włączyć protokół nazwanych potoków  
  
1.  W okienku po lewej stronie **Menedżera konfiguracji SQL Server**, rozwiń węzeł **konfiguracja sieci programu SQL Server 2005**, a następnie kliknij przycisk **protokoły dla SQLEXPRESS**.  
  
2.  Upewnij się, że w okienku po prawej stronie **potoków nazwanych** jest włączony protokół. Jeśli nie, kliknij prawym przyciskiem myszy **nazwane potoki** a następnie kliknij przycisk **Włącz**.  
  
     Trzeba będzie zatrzymać i ponownie uruchomić usługę. Wykonaj kroki opisane w następnym bloku.  
  
### <a name="stopping-and-restarting-the-service"></a>Zatrzymywanie i ponowne uruchomienie usługi  
 Należy zatrzymać i ponownie uruchomić usługi, zanim zmiany zostały wprowadzone.  
  
##### <a name="to-stop-and-restart-the-service"></a>Aby zatrzymać i ponownie uruchom usługę  
  
1.  W okienku po lewej stronie **Menedżera konfiguracji SQL Server**, kliknij przycisk **usług SQL Server 2005**.  
  
2.  W okienku po prawej stronie kliknij prawym przyciskiem myszy **programu SQL Server (SQLEXPRESS)**, a następnie kliknij przycisk **zatrzymać**.  
  
3.  Kliknij prawym przyciskiem myszy **programu SQL Server (SQLEXPRESS)**, a następnie kliknij przycisk **ponowne uruchomienie**.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
