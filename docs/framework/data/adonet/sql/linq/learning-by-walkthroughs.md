---
title: "Learning przez — wskazówki"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8ae2965-6a49-4155-89b0-7fab2c488ab1
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 53ddead8bd03fd9ce5e1adf8fe41a6f4c8b06154
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="learning-by-walkthroughs"></a>Learning przez — wskazówki
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Dokumentacja zawiera wskazówki dotyczące kilku. W tym temacie rozwiązuje problemy ogólne wskazówki (w tym Rozwiązywanie problemów) oraz linki do kilku klasy podstawowej wskazówki szkoleniowe dotyczące [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
> [!NOTE]
>  Wskazówki w tej sekcji wprowadzenie ujawnia podstawowe kod obsługujący [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technologii. W praktyce rzeczywiste zwykle użyjesz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] i projektami formularzy systemu Windows z [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacji. [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] Dokumentacji udostępniono wskazówki i przykłady w tym celu.  
  
## <a name="getting-started-walkthroughs"></a>Wprowadzenie — wskazówki  
 Wskazówki dotyczące kilku dostępnych w tej sekcji. Wskazówki te są oparte na przykładowej bazy danych Northwind i prezentowanie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] funkcje w tempie łagodne z minimalnym złożoności.  
  
 Typowy postępu do wykonania, należy w następujący sposób:  
  
|Cel|Visual Basic|C#|  
|---------------|------------------|---------|  
|Utwórz klasę jednostki i wykonywanie prostych zapytań.|[Przewodnik: Prosty model obiektu i zapytanie (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-visual-basic.md)|[Przewodnik: Prosty model obiektu i zapytanie (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-csharp.md)|  
|Dodaj klasę sekundy i wykonaj bardziej złożonego zapytania.<br /><br /> (Wymaga zakończenia w poprzednim przewodniku).|[Przewodnik: Wykonywanie zapytań w relacjach (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-visual-basic.md)|[Przewodnik: Wykonywanie zapytań w relacjach (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-csharp.md)|  
|Dodawanie, zmienianie i usuwanie elementów w bazie danych.|[Przewodnik: Manipulowanie danymi (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-visual-basic.md)|[Przewodnik: Manipulowanie danymi (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-csharp.md)|  
|Użyj procedur składowanych.|[Przewodnik: Tylko przy użyciu procedur składowanych (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-using-only-stored-procedures-visual-basic.md)|[Przewodnik: Tylko przy użyciu procedur składowanych (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-using-only-stored-procedures-csharp.md)|  
  
## <a name="general"></a>Ogólne  
 Poniższe informacje dotyczą te wskazówki ogólnie:  
  
-   Środowisko: Każdego [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] używa wskazówki [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] jako jego zintegrowane środowisko programistyczne (IDE).  
  
-   Aparaty SQL: wskazówki te są zapisywane w można implementować przy użyciu programu SQL Server Express. Jeśli nie masz programu SQL Server Express, można pobrać bezpłatnie. Aby uzyskać więcej informacji, zobacz [pobieranie przykładowe bazy danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
    > [!NOTE]
    >  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]wskazówki dotyczące Użyj nazwy pliku jako ciąg połączenia. Po prostu określenie nazwy pliku jest udogodnienie który [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapewnia użytkownikom programu SQL Server Express. Zawsze należy zwrócić uwagę na problemy z zabezpieczeniami. Aby uzyskać więcej informacji, zobacz [zabezpieczeń w składniku LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md).  
  
-   [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]wskazówki dotyczące zwykle wymagają przykładowej bazy danych Northwind. Aby uzyskać więcej informacji, zobacz [pobieranie przykładowe bazy danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
-   Okna dialogowe i poleceń menu zostanie wyświetlony w wskazówki mogą różnić się od opisanych w pomocy, w zależności od ustawienia active lub [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] edition. Aby zmienić ustawienia, kliknij przycisk **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
-   Aby uzyskać wskazówki dotyczące adresów wielowarstwowych scenariuszy serwer musi znajdować się na komputerze, który różni się od na komputerze deweloperskim, a musi mieć odpowiednie uprawnienia dostępu do serwera.  
  
-   Nazwa klasy, która zazwyczaj reprezentuje tabeli zamówienia w bazie danych Northwind jest `[Order]`. Anulowanie jest wymagana, ponieważ `Order` jest słowo kluczowe w [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)].  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 Mogą wystąpić błędy czasu wykonywania, ponieważ nie masz wystarczających uprawnień dostępu do baz danych, używany w te wskazówki. Zobacz poniższe kroki, aby rozwiązać najbardziej typowe tych problemów.  
  
### <a name="log-on-issues"></a>Problemy dotyczące logowania  
 Aplikacja może podjąć próbę dostępu do bazy danych i logowania bazy danych, które nie są akceptowane.  
  
##### <a name="to-verify-or-change-the-database-log-on"></a>Aby sprawdzić lub zmienić bazy danych logowania  
  
1.  W systemie Windows **Start** menu wskaż **wszystkie programy**, **Microsoft SQL Server 2005**, wskaż polecenie **narzędzia do konfiguracji**, a następnie kliknij przycisk **Programu SQL Server Configuration Manager**.  
  
2.  W lewym okienku **SQL Server Configuration Manager**, kliknij przycisk **usług SQL Server 2005**.  
  
3.  W prawym okienku kliknij prawym przyciskiem myszy **programu SQL Server (SQLEXPRESS)**, a następnie kliknij przycisk **właściwości**.  
  
4.  Kliknij przycisk **logowanie** kartę i sprawdź, jak chcesz zalogować się do serwera.  
  
     W większości przypadków **systemu lokalnego** działa.  
  
     Jeśli wprowadzisz zmiany, kliknij przycisk **ponowne uruchomienie** ponownie uruchomić usługę.  
  
### <a name="protocols"></a>protokoły  
 W czasie protokoły może nie można prawidłowo aplikacji dostęp do bazy danych. Na przykład **potoków nazwanych** protokołu, który jest wymagany dla wskazówki w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], nie jest domyślnie włączona.  
  
##### <a name="to-enable-the-named-pipes-protocol"></a>Aby włączyć protokół nazwanych potoków  
  
1.  W lewym okienku **SQL Server Configuration Manager**, rozwiń węzeł **konfigurację sieci programu SQL Server 2005**, a następnie kliknij przycisk **protokoły dla programu SQLEXPRESS**.  
  
2.  W okienku po prawej stronie, upewnij się, że **potoków nazwanych** jest włączony protokół. Jeśli nie, kliknij prawym przyciskiem myszy **potoków nazwa** , a następnie kliknij przycisk **włączyć**.  
  
     Należy zatrzymać i uruchomić ponownie usługę. Postępuj zgodnie z instrukcjami kolejnego bloku.  
  
### <a name="stopping-and-restarting-the-service"></a>Zatrzymywanie i ponowne uruchomienie usługi  
 Należy zatrzymać i ponownie uruchomić usługi, aby zmiany zostały wprowadzone.  
  
##### <a name="to-stop-and-restart-the-service"></a>Aby zatrzymać i ponownie uruchom usługę  
  
1.  W lewym okienku **SQL Server Configuration Manager**, kliknij przycisk **usług SQL Server 2005**.  
  
2.  W prawym okienku kliknij prawym przyciskiem myszy **programu SQL Server (SQLEXPRESS)**, a następnie kliknij przycisk **zatrzymać**.  
  
3.  Kliknij prawym przyciskiem myszy **programu SQL Server (SQLEXPRESS)**, a następnie kliknij przycisk **ponownego uruchomienia**.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
