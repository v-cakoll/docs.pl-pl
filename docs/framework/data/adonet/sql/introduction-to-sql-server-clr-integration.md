---
title: Wprowadzenie do integracji środowiska CLR programu SQL Server
ms.date: 03/30/2017
ms.assetid: 551d2290-ed80-49be-b377-44b32444da1c
ms.openlocfilehash: dc7d19bf361ed5fcda1fd5edf64eeb5e4ce15a71
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59336814"
---
# <a name="introduction-to-sql-server-clr-integration"></a>Wprowadzenie do integracji środowiska CLR programu SQL Server
Środowisko uruchomieniowe języka wspólnego (CLR) to serce platformy Microsoft .NET Framework i oferuje środowisko wykonywania dla całego kodu .NET Framework. Kod, który jest uruchamiany w ramach środowiska CLR jest określany jako kod zarządzany. Środowisko CLR oferuje różnych funkcji i usług wymaganych do wykonania programu, w tym just-in-time (JIT) kompilacja, przydzielanie i zarządzanie pamięcią, wymuszanie bezpieczeństwo typów, obsługa wyjątków, zarządzanie wątkami i zabezpieczeń.  
  
 Za pomocą środowiska CLR hostowanych w programie Microsoft SQL Server (nazywane integrację środowiska CLR) można tworzyć procedury składowane, wyzwalacze, funkcje zdefiniowane przez użytkownika, typy zdefiniowane przez użytkownika i agregacje zdefiniowane przez użytkownika w kodzie zarządzanym. Ponieważ kompiluje kodu zarządzanego do kodu macierzystego przed wykonywania, można osiągnąć zwiększa istotnie poprawiającą wydajność w niektórych scenariuszach.  
  
 Zarządzany kod używa zabezpieczeń dostępu kodu (CAS), linków do kodu i domen aplikacji, aby zapobiec zestawów z wykonywania pewnych operacji. Program SQL Server używa urzędów certyfikacji, aby ułatwić zabezpieczenie kodu zarządzanego i zapobiec naruszeniu zabezpieczeń systemu operacyjnego lub serwera bazy danych.  
  
 Ta sekcja ma zapewnić tylko wystarczających informacji, aby rozpocząć programowanie z użyciem integracji środowiska CLR programu SQL Server i nie jest przeznaczona do wyczerpująca. Aby uzyskać szczegółowe informacje Zobacz wersję programu SQL Server — książki Online dla wersji programu SQL Server, którego używasz.  
  
 **SQL Server Books Online**  
  
-   [Omówienie integracji środowiska uruchomieniowego (języka wspólnego CLR) w usłudze wspólnego języka](https://go.microsoft.com/fwlink/?LinkId=115242)  
  
## <a name="enabling-clr-integration"></a>Włączanie integracji środowiska CLR  
 Typowych funkcji integracji środowiska uruchomieniowego (języka wspólnego CLR) języka jest wyłączona, domyślnie w programie Microsoft SQL Server, a musi być włączona, aby można było używać obiektów, które są implementowane przy użyciu integrację środowiska CLR. Aby włączyć integrację środowiska CLR przy użyciu języka Transact-SQL, użyj `clr enabled` opcji `sp_configure` procedurę składowaną, jak pokazano:  
  
```  
sp_configure 'clr enabled', 1  
GO  
RECONFIGURE  
GO  
```  
  
 Wyłącz integrację środowiska CLR, ustawiając `clr enabled` opcję na wartość 0. Po wyłączeniu integrację środowiska CLR programu SQL Server zatrzymuje wykonywanie wszystkich procedur CLR i zwalnia wszystkie domeny aplikacji.  
  
 Aby uzyskać szczegółowe informacje Zobacz wersję programu SQL Server — książki Online dla wersji programu SQL Server, którego używasz.  
  
 **SQL Server Books Online**  
  
-   [Włączanie integracji środowiska CLR](https://go.microsoft.com/fwlink/?LinkId=115230)  
  
## <a name="deploying-a-clr-assembly"></a>Wdrażanie zestawu CLR  
 Po metodach CLR zostały przetestowane i zweryfikowane na serwerze testowym, mogą być rozproszone na serwerach produkcyjnych przy użyciu skryptu wdrażania. Ręcznie lub za pomocą programu SQL Server Management Studio można wygenerować skryptu wdrażania. Aby uzyskać szczegółowe informacje Zobacz wersję programu SQL Server — książki Online dla wersji programu SQL Server, którego używasz.  
  
 **SQL Server Books Online**  
  
1. [Wdrażanie obiekty bazy danych środowiska CLR](https://go.microsoft.com/fwlink/?LinkId=115232)  
  
## <a name="clr-integration-security"></a>Zabezpieczenia integracji CLR  
 Model zabezpieczeń integracji programu Microsoft SQL Server za pomocą programu Microsoft .NET Framework środowisko uruchomieniowe języka wspólnego (CLR) zarządza i zabezpiecza dostęp między różnymi typami obiektów CLR i / CLR, które są uruchomione w programie SQL Server. Te obiekty może zostać wywołana przez instrukcję Transact-SQL lub innego obiektu CLR uruchomiona na serwerze.  
  
 Aby uzyskać szczegółowe informacje Zobacz wersję programu SQL Server — książki Online dla wersji programu SQL Server, którego używasz.  
  
 **SQL Server Books Online**  
  
-   [Zabezpieczenia integracji CLR](https://go.microsoft.com/fwlink/?LinkId=115234)  
  
## <a name="debugging-a-clr-assembly"></a>Debugowanie zestawu CLR  
 Microsoft SQL Server zapewnia obsługę debugowania języka Transact-SQL i obiekty wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) w bazie danych. Debugowanie działa w wielu językach: użytkownicy mogą Wkrocz bezproblemowo obiektów CLR z instrukcji Transact-SQL i na odwrót.  
  
 Aby uzyskać szczegółowe informacje Zobacz wersję programu SQL Server — książki Online dla wersji programu SQL Server, którego używasz.  
  
 **SQL Server Books Online**  
  
-   [Debugowanie obiektów bazy danych środowiska CLR](https://go.microsoft.com/fwlink/?LinkId=115236)  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczenia dostępu kodu i ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
