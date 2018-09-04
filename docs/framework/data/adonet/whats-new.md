---
title: Co&#39;s Nowość w ADO.NET
ms.date: 03/30/2017
ms.assetid: 3bb65d38-cce2-46f5-b979-e5c505e95e10
ms.openlocfilehash: a94833a513fa6ceef02b5ec64f0a7995779d323a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43511806"
---
# <a name="what39s-new-in-adonet"></a>Co&#39;s Nowość w ADO.NET
Następujące funkcje są nowością w programie [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] w [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].  
  
## <a name="sqlclient-data-provider"></a>Dostawca danych SqlClient  
 Następujące funkcje są nowością w programie [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dostawcy danych programu SQL Server na [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]:  
  
-   ConnectRetryCount i ConnectRetryInterval połączenia ciąg słów kluczowych (<xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>) pozwalają na kontrolowanie funkcji odporności bezczynnego połączenia.  
  
-   Przesyłanie strumieniowe pomocy technicznej z programu SQL Server do aplikacji obsługuje scenariusze, w którym dane na serwerze jest bez struktury.  Zobacz [obsługa przesyłania strumieniowego SqlClient](../../../../docs/framework/data/adonet/sqlclient-streaming-support.md) Aby uzyskać więcej informacji.  
  
-   Dodano obsługę dla programowania asynchronicznego.  Zobacz [Asynchronous Programming](../../../../docs/framework/data/adonet/asynchronous-programming.md) Aby uzyskać więcej informacji.  
  
-   Błędy połączenia będą teraz rejestrowane w dzienniku zdarzeń rozszerzonych. Aby uzyskać więcej informacji, zobacz [danych śledzenia w ADO.NET](../../../../docs/framework/data/adonet/data-tracing.md).  
  
-   Klient SQL ma teraz obsługę programu SQL Server wysoką dostępność, funkcji odzyskiwania po awarii, zawsze włączone. Aby uzyskać więcej informacji, zobacz [Obsługa SqlClient dla wysokiej dostępności, odzyskiwania po awarii](../../../../docs/framework/data/adonet/sql/sqlclient-support-for-high-availability-disaster-recovery.md).  
  
-   Hasła mogą być przekazywane jako <xref:System.Security.SecureString> podczas korzystania z uwierzytelniania programu SQL Server. Aby uzyskać więcej informacji, zobacz <xref:System.Data.SqlClient.SqlCredential>.  
  
-   Gdy `TrustServerCertificate` ma wartość FAŁSZ i `Encrypt` ma wartość true, nazwę serwera (lub adres IP) w certyfikacie SSL serwera SQL musi dokładnie odpowiadać serwera nazwę (lub adres IP) określone w parametrach połączenia. W przeciwnym razie próba połączenia zakończy się niepowodzeniem. Aby uzyskać więcej informacji, zobacz opis `Encrypt` opcja połączenia w <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
     Jeśli ta zmiana powoduje, że już połączyć istniejącą aplikację, można naprawić aplikacji przy użyciu jednej z następujących czynności:  
  
    -   Wystawić certyfikat, który określa krótką nazwę w polu Nazwa pospolita (CN) lub alternatywnej nazwy podmiotu (SAN). To rozwiązanie będzie działać w przypadku dublowania bazy danych.  
  
    -   Dodaj alias, który mapuje krótką nazwę do w pełni kwalifikowaną nazwę domeny.  
  
    -   Użyj w pełni kwalifikowaną nazwę domeny w parametrach połączenia.  
  
-   Klient SQL obsługuje ochrony rozszerzonej. Aby uzyskać więcej informacji na temat ochrony rozszerzonej zobacz [nawiązywania połączenia z bazy danych aparatu przy użyciu ochrony rozszerzonej](https://go.microsoft.com/fwlink/?LinkId=219978).  
  
-   Klient SQL obsługuje połączenia do bazy danych LocalDB. Aby uzyskać więcej informacji, zobacz [Obsługa SqlClient dla LocalDB](../../../../docs/framework/data/adonet/sql/sqlclient-support-for-localdb.md).  
  
-   `Type System Version=SQL Server 2012;` jest nową wartość do przekazania do `Type System Version` właściwości połączenia. `Type System Version=Latest;` Wartości jest już przestarzały i dokonano odpowiednikiem `Type System Version=SQL Server 2008;`. Aby uzyskać więcej informacji, zobacz <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
-   Klient SQL zapewnia dodatkową obsługę kolumn rozrzedzonych, funkcji, który został dodany do programu SQL Server 2008. Jeśli aplikacja już uzyskuje dostęp do danych w tabeli, która używa kolumn rozrzedzonych, powinien zostać wyświetlony wzrost wydajności. Kolumna IsColumnSet <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> wskazuje, czy kolumna jest kolumną rozrzedzoną, który jest członkiem zestawu kolumn. <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> Wskazuje, czy kolumna jest kolumną rozrzedzoną (zobacz [kolekcje schematów programu SQL Server](../../../../docs/framework/data/adonet/sql-server-schema-collections.md) Aby uzyskać więcej informacji). Aby uzyskać więcej informacji na temat kolumn rozrzedzonych, zobacz [przy użyciu kolumn rozrzedzonych](https://go.microsoft.com/fwlink/?LinkId=224244).  
  
-   Zestaw Microsoft.SqlServer.Types.dll, który zawiera typy danych przestrzennych, został uaktualniony z wersji 10.0 do wersji 11.0. Aplikacje odwołujące się do tego zestawu może zakończyć się niepowodzeniem. Aby uzyskać więcej informacji, zobacz [zmiany powodujące funkcje aparatu bazy danych](https://go.microsoft.com/fwlink/?LinkId=224367).  
  
## <a name="adonet-entity-framework"></a>Program Entity Framework na platformie ADO.NET  
 [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] Dodaje interfejsów API, które umożliwiają obsługę nowych scenariuszy podczas pracy z programu Entity Framework 5.0. Aby uzyskać więcej informacji na temat usprawnień i nowych funkcji, które zostały dodane do programu Entity Framework 5.0, zobacz następujące tematy: [What's New](https://go.microsoft.com/fwlink/?LinkID=251106) i [Entity Framework w wersji oraz zarządzanie ich wersjami](https://go.microsoft.com/fwlink/?LinkId=234899).  
  
## <a name="see-also"></a>Zobacz też  
 [ADO.NET](../../../../docs/framework/data/adonet/index.md)  
 [Omówienie ADO.NET](../../../../docs/framework/data/adonet/ado-net-overview.md)  
 [SQL Server i ADO.NET](../../../../docs/framework/data/adonet/sql/index.md)  
 [What's New in usług danych WCF](https://msdn.microsoft.com/library/cf22cad5-b8d9-472b-8d7c-b863b64eaae8)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
