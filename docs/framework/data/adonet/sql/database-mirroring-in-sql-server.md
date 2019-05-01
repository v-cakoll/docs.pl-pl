---
title: Dublowanie bazy danych w programie SQL Server
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 89befaff-bb46-4290-8382-e67cdb0e3de9
ms.openlocfilehash: 1445a95fc6360a7956048d2bae2d840f9c3f7a99
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61877815"
---
# <a name="database-mirroring-in-sql-server"></a>Dublowanie bazy danych w programie SQL Server
Funkcja dublowania baz danych w programie SQL Server pozwala na zachowanie kopiowania lub dublowania bazy danych programu SQL Server na serwerze wstrzymania. Dublowanie gwarantuje, że dwie oddzielne kopie danych istnieją przez cały czas, zapewniając wysoką dostępność i ukończyć nadmiarowości danych. .NET Data Provider for SQL Server obsługuje niejawne dublowania bazy danych, tak aby deweloper nie trzeba podejmować żadnych działań lub pisania kodu, gdy został skonfigurowany dla bazy danych programu SQL Server. Ponadto <xref:System.Data.SqlClient.SqlConnection> obiekt obsługuje tryb jawne połączenie, który umożliwia podanie nazwy serwera partnerskiego trybu failover, w <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
 Poniższy uproszczony sekwencja zdarzeń dla <xref:System.Data.SqlClient.SqlConnection> obiektu, który jest przeznaczony dla skonfigurowano obsługę dublowania bazy danych:  
  
1. Aplikacja kliencka połączy się z główną bazą danych, a serwer odsyła nazwę serwera partnera, który następnie jest buforowana na kliencie.  
  
2. Jeśli serwer zawierający dublowanej bazy danych ulegnie awarii lub połączenie zostało przerwane, stan połączenia i transakcji zostaną utracone. Aplikacja kliencka próbuje ponownie ustanowić połączenia z główną bazą danych i kończy się niepowodzeniem.  
  
3. Następnie aplikacja kliencka przezroczyste próbuje nawiązać połączenie z duplikatu bazy danych na serwerze partnerskim. Jeśli się powiedzie, połączenie jest przekierowywane do duplikatu bazy danych, które następnie staje się nowej nazwy głównej bazy danych.  
  
## <a name="specifying-the-failover-partner-in-the-connection-string"></a>Określanie serwera partnerskiego trybu Failover w parametrach połączenia  
 Jeśli podasz nazwę serwera partnerskiego trybu failover w parametrach połączenia klienta przezroczyste prób połączenia z serwera partnerskiego trybu failover, jeśli główna baza danych jest niedostępny przy pierwszym połączeniu z aplikacji klienckiej.  
  
```  
";Failover Partner=PartnerServerName"  
```  
  
 Jeśli pominięto nazwę serwera partnerskiego trybu failover i główna baza danych jest niedostępna podczas aplikacja kliencka najpierw łączy się następnie <xref:System.Data.SqlClient.SqlException> jest wywoływane.  
  
 Gdy <xref:System.Data.SqlClient.SqlConnection> został pomyślnie otwarty, Nazwa partnera pracy awaryjnej jest zwracany przez serwer i zastępuje wszystkie wartości podane w parametrach połączenia.  
  
> [!NOTE]
>  Początkowa nazwa katalogu lub bazy danych musi być jawnie określone w ciąg połączenia dla scenariuszy dublowania bazy danych. Jeśli klient otrzymuje informacje trybu failover dla połączenia, który nie ma jawnie określonego katalogu początkowego lub bazy danych, informacje o pracy awaryjnej nie jest buforowana i aplikacja nie jest podejmowana próba pracy awaryjnej w przypadku awarii serwera podmiotu zabezpieczeń. Jeśli ciąg połączenia ma wartość dla serwera partnerskiego trybu failover, ale brak wartości dla katalogu początkowego lub bazy danych, `InvalidArgumentException` jest wywoływane.  
  
## <a name="retrieving-the-current-server-name"></a>Pobieranie bieżącej nazwy serwera  
 Zdarzenia na pracę awaryjną, możesz pobrać nazwę serwera, do którego bieżące połączenie jest rzeczywiście połączone za pomocą <xref:System.Data.SqlClient.SqlConnection.DataSource%2A> właściwość <xref:System.Data.SqlClient.SqlConnection> obiektu. Poniższy fragment kodu pobiera nazwę ASP, zakładając, że zmienna połączenia odwołuje się otwartą <xref:System.Data.SqlClient.SqlConnection>.  
  
 Po wystąpieniu zdarzenia pracy awaryjnej i połączenie zostanie przełączone na serwer duplikatu **DataSource** właściwość zostanie zaktualizowany w celu odzwierciedlenia nazwy dublowania.  
  
```vb  
Dim activeServer As String = connection.DataSource  
```  
  
```csharp  
string activeServer = connection.DataSource;  
```  
  
## <a name="sqlclient-mirroring-behavior"></a>Zachowanie funkcji dublowania SqlClient  
 Klient zawsze próbuje połączyć się z bieżącym serwerze dublowanym. Jeśli nie powiedzie się, próbuje serwera partnerskiego trybu failover. Jeśli główna rola na serwerze partnerskim już został przełączony duplikatu bazy danych, połączenie powiedzie się, a nowe mapowanie dublowane jednostki jest wysyłane do klienta w pamięci podręcznej i okresem istnienia wywołania <xref:System.AppDomain>. Nie są przechowywane w magazynie trwałym i nie jest dostępna dla kolejnych połączeń w innej **AppDomain** lub procesu. Jednak jest dostępna tylko dla kolejnych połączeń, w tym samym **AppDomain**. Uwaga oznacza innego **AppDomain** lub proces uruchomiony na tym samym lub innym komputerze zawsze ma puli połączeń i te połączenia nie są resetowane. W takim przypadku podstawowej bazy danych ulegnie awarii, każdy proces lub **AppDomain** kończy się niepowodzeniem, jeden raz i puli są automatycznie usuwane.  
  
> [!NOTE]
>  Funkcja dublowania obsługi na serwerze jest skonfigurowana na podstawie poszczególnych baz danych. Jeśli operacji na strumieniach danych są wykonywane w odniesieniu do innych baz danych, które nie są uwzględniane w zestawie jednostki/woluminu dublowanego, przy użyciu nazwy wieloczęściowej lub zmieniając bieżącej bazy danych zmian do tych baz danych nie propagować awarii. Nie zostanie wygenerowany błąd modyfikacji danych w bazie danych, która nie jest dublowana. Deweloper musi zwrócić możliwy wpływ takich operacji.  
  
## <a name="database-mirroring-resources"></a>Zasoby dublowania bazy danych  
 Dokumentacja koncepcyjna i informacji na temat konfigurowania wdrażania i administrowania dublowania, zobacz następujące zasoby w dokumentacji SQL Server.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Funkcja dublowania baz danych](/sql/database-engine/database-mirroring/database-mirroring-sql-server)|Opisuje sposób instalowania i konfigurowania dublowania w programie SQL Server.|  
  
## <a name="see-also"></a>Zobacz także

- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
