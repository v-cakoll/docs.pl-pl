---
title: Wprowadzenie do integracji środowiska CLR programu SQL Server
ms.date: 03/30/2017
ms.assetid: 551d2290-ed80-49be-b377-44b32444da1c
ms.openlocfilehash: dd0ef041db13aa842554c70533770bf99c369941
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365582"
---
# <a name="introduction-to-sql-server-clr-integration"></a>Wprowadzenie do integracji środowiska CLR programu SQL Server
Środowisko uruchomieniowe języka wspólnego (CLR) jest bardzo ważne dla programu Microsoft .NET Framework i zapewnia środowiska wykonawczego dla całego kodu .NET Framework. Kod uruchamiany w ramach środowiska CLR jest określana jako kod zarządzany. Środowisko CLR zapewnia różnych funkcji i usług wymaganych do wykonania programu, w tym just in time (JIT) kompilację, przydzielanie i zarządzanie pamięcią, wymuszanie zabezpieczeń, obsługa wyjątków wątku zarządzania i zabezpieczeń.  
  
 Z CLR hostowanej w programie Microsoft SQL Server (nazywane integrację środowiska CLR) można tworzyć procedury składowane, wyzwalacze, funkcje zdefiniowane przez użytkownika, typy danych zdefiniowane przez użytkownika i agregacje zdefiniowane przez użytkownika, w kodzie zarządzanym. Ponieważ kompiluje kodu zarządzanego do kodu natywnego przed wykonaniem, można osiągnąć wzrośnie znaczne wydajności w niektórych scenariuszach.  
  
 Zarządzany kod używa zabezpieczeń dostępu kodu (CAS), linków do kodu i domen aplikacji, aby zapobiec zestawy z wykonywania pewnych operacji. SQL Server używa urzędów certyfikacji, aby ułatwić Zabezpieczanie kodu zarządzanego i zapobiec naruszeniu zabezpieczeń systemu operacyjnego lub serwer bazy danych.  
  
 Ta sekcja ma zapewnić tylko za mało informacji, aby rozpocząć programowanie z integrację środowiska CLR programu SQL Server i nie jest przeznaczona pełne. Aby uzyskać szczegółowe informacje Zobacz wersji programu SQL Server — książki Online dla wersji programu SQL Server są przy użyciu.  
  
 **SQL Server — książki Online**  
  
-   [Omówienie integracji środowiska uruchomieniowego (języka wspólnego CLR) w usłudze wspólnego języka](http://go.microsoft.com/fwlink/?LinkId=115242)  
  
## <a name="enabling-clr-integration"></a>Włączanie integracji środowiska CLR  
 Z typowych funkcji Integracja z języka wspólnego (CLR) jest wyłączona, domyślnie w programie Microsoft SQL Server, a musi być włączona, aby można było używać obiektów, które są implementowane za pomocą integracji środowiska CLR. Aby włączyć integrację środowiska CLR przy użyciu języka Transact-SQL, należy użyć `clr enabled` opcji `sp_configure` procedury składowanej, jak pokazano:  
  
```  
sp_configure 'clr enabled', 1  
GO  
RECONFIGURE  
GO  
```  
  
 Integrację środowiska CLR można wyłączyć, ustawiając `clr enabled` opcję na wartość 0. Po wyłączeniu integrację środowiska CLR programu SQL Server zatrzymuje wykonywanie wszystkich procedur CLR i zwalnia wszystkie domeny aplikacji.  
  
 Aby uzyskać szczegółowe informacje Zobacz wersji programu SQL Server — książki Online dla wersji programu SQL Server są przy użyciu.  
  
 **SQL Server — książki Online**  
  
-   [Włączanie integracji środowiska CLR](http://go.microsoft.com/fwlink/?LinkId=115230)  
  
## <a name="deploying-a-clr-assembly"></a>Wdrażanie Zestaw CLR  
 Po metodach CLR zostały przetestowane i zweryfikowane na serwerze testowym, mogą być dystrybuowane do produkcyjnego serwerami przy użyciu skryptu wdrażania. Skrypt wdrożenia można wygenerować ręcznie lub za pomocą programu SQL Server Management Studio. Aby uzyskać szczegółowe informacje Zobacz wersji programu SQL Server — książki Online dla wersji programu SQL Server są przy użyciu.  
  
 **SQL Server — książki Online**  
  
1.  [Wdrażanie obiektów bazy danych CLR](http://go.microsoft.com/fwlink/?LinkId=115232)  
  
## <a name="clr-integration-security"></a>Zabezpieczenia integracji środowiska CLR  
 Model zabezpieczeń integracji programu Microsoft SQL Server z systemu Microsoft .NET Framework środowisko uruchomieniowe języka wspólnego (CLR) zarządza i zabezpiecza dostęp między różnymi typami obiektów CLR i -CLR uruchomiony w programie SQL Server. Te obiekty może zostać wywołana przez instrukcję Transact-SQL lub innego obiektu CLR uruchomionej na serwerze.  
  
 Aby uzyskać szczegółowe informacje Zobacz wersji programu SQL Server — książki Online dla wersji programu SQL Server są przy użyciu.  
  
 **SQL Server — książki Online**  
  
-   [Zabezpieczenia integracji środowiska CLR](http://go.microsoft.com/fwlink/?LinkId=115234)  
  
## <a name="debugging-a-clr-assembly"></a>Debugowanie zestawu CLR  
 Microsoft SQL Server zapewnia obsługę debugowania Transact-SQL i wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) obiektów w bazie danych. Debugowanie działa w językach: użytkownicy mogą Wkrocz bezproblemowo obiektów CLR z Transact-SQL i na odwrót.  
  
 Aby uzyskać szczegółowe informacje Zobacz wersji programu SQL Server — książki Online dla wersji programu SQL Server są przy użyciu.  
  
 **SQL Server — książki Online**  
  
-   [Debugowanie CLR obiektów bazy danych](http://go.microsoft.com/fwlink/?LinkId=115236)  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie obiekty programu SQL Server 2005 w kodzie zarządzanym](http://msdn.microsoft.com/library/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [Zabezpieczenia dostępu kodu i ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
