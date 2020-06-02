---
title: Nowości
description: Dowiedz się więcej o nowych funkcjach programu ADO.NET w .NET Framework 4,5, w tym o nowych funkcjach dostawcy danych SqlClient i ADO.NET Entity Framework.
ms.date: 03/30/2017
ms.assetid: 3bb65d38-cce2-46f5-b979-e5c505e95e10
ms.openlocfilehash: 536b9314dd83366202f7fd9b489759681021fd9e
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286174"
---
# <a name="whats-new-in-adonet"></a>Nowości w programie ADO.NET

Następujące funkcje są nowością w programie ADO.NET w .NET Framework 4,5.

## <a name="sqlclient-data-provider"></a>Dostawca danych SqlClient

Następujące funkcje są nowe w .NET Framework Dostawca danych SQL Server w .NET Framework 4,5:

- Słowa kluczowe parametrów połączenia ConnectRetryCount i ConnectRetryInterval ( <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> ) pozwalają kontrolować funkcję odporności bezczynnego połączenia.

- Obsługa przesyłania strumieniowego z SQL Server do aplikacji obsługuje scenariusze, w których dane na serwerze mają nieprawidłową strukturę.  Aby uzyskać więcej informacji, zobacz [obsługa przesyłania strumieniowego SqlClient](sqlclient-streaming-support.md) .

- Dodano obsługę w programowaniu asynchronicznym.  Aby uzyskać więcej informacji, zobacz [programowanie asynchroniczne](asynchronous-programming.md) .

- Błędy połączeń będą teraz rejestrowane w dzienniku zdarzeń rozszerzonych. Aby uzyskać więcej informacji, zobacz [śledzenie danych w ADO.NET](data-tracing.md).

- Klient SqlClient ma teraz obsługę wysokiej dostępności SQL Server, funkcji odzyskiwania po awarii, AlwaysOn. Aby uzyskać więcej informacji, zobacz temat [Obsługa klienta w przypadku wysokiej dostępności i odzyskiwania po awarii](./sql/sqlclient-support-for-high-availability-disaster-recovery.md).

- Hasło można przesłać jako <xref:System.Security.SecureString> przy użyciu uwierzytelniania SQL Server. Aby uzyskać więcej informacji, zobacz <xref:System.Data.SqlClient.SqlCredential>.

- Gdy `TrustServerCertificate` ma wartość false i `Encrypt` ma wartość true, nazwa serwera (lub adres IP) w SQL Server certyfikat SSL musi być dokładnie zgodna z nazwą serwera (lub adresem IP) określoną w parametrach połączenia. W przeciwnym razie próba połączenia nie powiedzie się. Aby uzyskać więcej informacji, zobacz Opis `Encrypt` opcji połączenia w temacie <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> .

  Jeśli ta zmiana spowoduje, że istniejąca aplikacja nie będzie mogła nawiązywać połączenia, możesz naprawić aplikację, korzystając z jednego z następujących elementów:

  - Wystawianie certyfikatu określającego krótką nazwę w polu Nazwa pospolita (CN) lub alternatywna nazwa podmiotu (SAN). To rozwiązanie będzie działało na potrzeby dublowania baz danych.

  - Dodaj alias, który mapuje krótką nazwę na w pełni kwalifikowaną nazwę domeny.

  - Użyj w pełni kwalifikowanej nazwy domeny w parametrach połączenia.

- Klient SqlClient obsługuje rozszerzoną ochronę. Aby uzyskać więcej informacji na temat ochrony rozszerzonej, zobacz [nawiązywanie połączenia z aparatem bazy danych przy użyciu ochrony rozszerzonej](/sql/database-engine/configure-windows/connect-to-the-database-engine-using-extended-protection).

- Klient SqlClient obsługuje połączenia z bazami danych LocalDB. Aby uzyskać więcej informacji, zobacz temat [Obsługa SqlClient dla LocalDB](./sql/sqlclient-support-for-localdb.md).

- `Type System Version=SQL Server 2012;`jest nową wartością do przekazania do `Type System Version` właściwości Connection. `Type System Version=Latest;`Wartość jest obecnie przestarzała i została przeprowadzona jako odpowiednik `Type System Version=SQL Server 2008;` . Aby uzyskać więcej informacji, zobacz <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.

- Klient SqlClient oferuje dodatkową obsługę kolumn rozrzedzonych, funkcję dodaną w SQL Server 2008. Jeśli aplikacja już uzyskuje dostęp do danych w tabeli używającej kolumn rozrzedzonych, powinien zostać wyświetlony wzrost wydajności. Kolumna IsColumnSet wskazuje, <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> czy kolumna jest kolumną rozrzedzoną, która jest elementem członkowskim zestawu kolumn. <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>wskazuje, czy kolumna jest kolumną rozrzedzoną (zobacz [SQL Server kolekcje schematów](sql-server-schema-collections.md) , aby uzyskać więcej informacji). Aby uzyskać więcej informacji na temat kolumn rozrzedzonych, zobacz [Korzystanie z kolumn rozrzedzonych](/sql/relational-databases/tables/use-sparse-columns).

- Zestaw Microsoft. SqlServer. Types. dll, który zawiera typy danych przestrzennych, został uaktualniony z wersji 10,0 do wersji 11,0. Aplikacje odwołujące się do tego zestawu mogą zakończyć się niepowodzeniem. Aby uzyskać więcej informacji, zobacz istotne [zmiany w funkcjach aparatu bazy danych](https://docs.microsoft.com/previous-versions/sql/sql-server-2012/ms143179(v=sql.110)).

## <a name="adonet-entity-framework"></a>Program Entity Framework na platformie ADO.NET

.NET Framework 4,5 dodaje interfejsy API, które umożliwiają nowe scenariusze podczas pracy z Entity Framework 5,0. Aby uzyskać więcej informacji na temat ulepszeń i funkcji, które zostały dodane do Entity Framework 5,0, zobacz następujące tematy: [co nowego](https://docs.microsoft.com/previous-versions/gg696190(v=vs.103)) i [Entity Framework wersje i przechowywanie wersji](/ef/ef6/what-is-new/past-releases).

## <a name="see-also"></a>Zobacz także

- [ADO.NET](index.md)
- [Omówienie ADO.NET](ado-net-overview.md)
- [SQL Server i ADO.NET](./sql/index.md)
- [Co nowego w Usługi danych programu WCF 5,0](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))
