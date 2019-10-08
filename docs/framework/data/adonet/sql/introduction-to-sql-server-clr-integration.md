---
title: Wprowadzenie do integracji środowiska CLR programu SQL Server
ms.date: 03/30/2017
ms.assetid: 551d2290-ed80-49be-b377-44b32444da1c
ms.openlocfilehash: 76c6fb4cb37807f286f1f1f2aeedbdea6c74fe38
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002143"
---
# <a name="introduction-to-sql-server-clr-integration"></a>Wprowadzenie do integracji środowiska CLR programu SQL Server
Środowisko uruchomieniowe języka wspólnego (CLR) jest sercem struktury Microsoft .NET i udostępnia środowisko wykonywania dla całego kodu .NET Framework. Kod, który jest uruchamiany w środowisku CLR, jest nazywany kodem zarządzanym. Środowisko CLR udostępnia różne funkcje i usługi wymagane do wykonania programu, w tym kompilację just-in-Time (JIT), przydzielanie i zarządzanie pamięcią, wymuszanie bezpieczeństwa typów, obsługę wyjątków, zarządzanie wątkami i zabezpieczenia.  
  
 Za pomocą środowiska CLR hostowanego w Microsoft SQL Server (nazywanej integracją środowiska CLR) można tworzyć procedury składowane, wyzwalacze, funkcje zdefiniowane przez użytkownika, typy zdefiniowane przez użytkownika i agregacje zdefiniowane przez użytkownika w kodzie zarządzanym. Ponieważ kod zarządzany kompiluje się do kodu natywnego przed wykonaniem, można osiągnąć znaczący wzrost wydajności w niektórych scenariuszach.  
  
 Kod zarządzany używa zabezpieczeń dostępu kodu (CAS), linków do kodu i domen aplikacji, aby zapobiec wykonywaniu przez nie niektórych operacji. SQL Server używa urzędów certyfikacji do zabezpieczania kodu zarządzanego i zapobiegania naruszeniu systemu operacyjnego lub serwera bazy danych.  
  
 Ta sekcja ma na celu dostarczenie tylko wystarczającej ilości informacji, aby rozpocząć programowanie przy użyciu integracji środowiska CLR SQL Server i nie jest to wszechstronne. Aby uzyskać bardziej szczegółowe informacje, zapoznaj się z wersją usługi SQL Server Books Online dla używanej wersji SQL Server.  
  
 **Książka SQL Server online**  
  
- [Omówienie integracji środowiska uruchomieniowego języka wspólnego (CLR)](https://go.microsoft.com/fwlink/?LinkId=115242)  
  
## <a name="enabling-clr-integration"></a>Włączanie integracji środowiska CLR  
 Funkcja integracji środowiska uruchomieniowego języka wspólnego (CLR) jest domyślnie wyłączona w Microsoft SQL Server i musi być włączona, aby można było używać obiektów wdrożonych przy użyciu integracji środowiska CLR. Aby włączyć integrację środowiska CLR przy użyciu języka Transact-SQL, użyj opcji `clr enabled` procedury składowanej `sp_configure`, jak pokazano poniżej:  
  
```sql  
sp_configure 'clr enabled', 1  
GO  
RECONFIGURE  
GO  
```  
  
 Integrację środowiska CLR można wyłączyć, ustawiając opcję `clr enabled` na 0. Po wyłączeniu integracji środowiska CLR SQL Server przestaje wykonywać wszystkie procedury CLR i zwalnia wszystkie domeny aplikacji.  
  
 Aby uzyskać bardziej szczegółowe informacje, zapoznaj się z wersją usługi SQL Server Books Online dla używanej wersji SQL Server.  
  
 **Książka SQL Server online**  
  
- [Włączanie integracji środowiska CLR](https://go.microsoft.com/fwlink/?LinkId=115230)  
  
## <a name="deploying-a-clr-assembly"></a>Wdrażanie zestawu CLR  
 Po przetestowaniu i zweryfikowaniu metod CLR na serwerze testowym mogą one być dystrybuowane do serwerów produkcyjnych przy użyciu skryptu wdrażania. Skrypt wdrażania można wygenerować ręcznie lub za pomocą SQL Server Management Studio. Aby uzyskać bardziej szczegółowe informacje, zapoznaj się z wersją usługi SQL Server Books Online dla używanej wersji SQL Server.  
  
 **Książka SQL Server online**  
  
1. [Wdrażanie obiektów bazy danych CLR](https://go.microsoft.com/fwlink/?LinkId=115232)  
  
## <a name="clr-integration-security"></a>Zabezpieczenia integracji środowiska CLR  
 Model zabezpieczeń Microsoft SQL Server integracji ze środowiskiem uruchomieniowym języka wspólnego (CLR) w programie Microsoft .NET Framework umożliwia zarządzanie dostępem między różnymi typami obiektów CLR i innych niż środowiska CLR uruchomionych w SQL Server. Te obiekty mogą być wywoływane przez instrukcję języka Transact-SQL lub inny obiekt CLR uruchomiony na serwerze.  
  
 Aby uzyskać bardziej szczegółowe informacje, zapoznaj się z wersją usługi SQL Server Books Online dla używanej wersji SQL Server.  
  
 **Książka SQL Server online**  
  
- [Zabezpieczenia integracji środowiska CLR](https://go.microsoft.com/fwlink/?LinkId=115234)  
  
## <a name="debugging-a-clr-assembly"></a>Debugowanie zestawu CLR  
 Microsoft SQL Server zapewnia obsługę debugowania obiektów Transact-SQL i środowiska uruchomieniowego języka wspólnego (CLR) w bazie danych programu. Debugowanie działa między językami: użytkownicy mogą bezproblemowo przechodzenie do obiektów CLR z języka Transact-SQL i na odwrót.  
  
 Aby uzyskać bardziej szczegółowe informacje, zapoznaj się z wersją usługi SQL Server Books Online dla używanej wersji SQL Server.  
  
 **Książka SQL Server online**  
  
- [Debugowanie obiektów bazy danych CLR](https://go.microsoft.com/fwlink/?LinkId=115236)  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczenia dostępu kodu i ADO.NET](../code-access-security.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
