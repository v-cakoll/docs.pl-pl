---
title: Wymagania systemowe programu .NET Framework Data Provider for Oracle
ms.date: 03/30/2017
ms.assetid: 054f76b9-1737-43f0-8160-84a00a387217
ms.openlocfilehash: a5ce0e831af40cbe86e6ac901d6e92d5a60f8774
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="system-requirements-for-the-net-framework-data-provider-for-oracle"></a>Wymagania systemowe programu .NET Framework Data Provider for Oracle
.NET Framework Data Provider for Oracle wymaga programu Microsoft Data Access Components (MDAC) w wersji version 2.6 lub nowszej. Zaleca się MDAC 2.8 z dodatkiem SP1.  
  
 Musi mieć również klienta programu Oracle 8i (8.1.7) w wersji 3 lub nowszej.  
  
 Oprogramowania klienta Oracle poprzedzające wersję Oracle 9i nie może uzyskać dostępu UTF16 baz danych, ponieważ UTF16 jest nową funkcją w Oracle 9i. Aby użyć tej funkcji, należy uaktualnić oprogramowanie klienta Oracle 9i lub nowszej.  
  
## <a name="working-with-the-data-provider-for-oracle-and-unicode-data"></a>Praca z dostawcy danych programu Oracle i danych Unicode  
 Poniżej znajduje się lista problemów związanych z Unicode, które należy rozważyć podczas pracy z dostawcy danych programu .NET Framework dla programu Oracle i Oracle bibliotek klienckich. Aby uzyskać więcej informacji zobacz dokumentacji programu Oracle.  
  
### <a name="setting-the-unicode-value-in-a-connection-string-attribute"></a>Ustawianie wartości Unicode w atrybut parametrów połączenia  
 Podczas pracy z programem Oracle, można użyć atrybut parametrów połączenia  
  
```  
Unicode=True   
```  
  
 Aby zainicjować bibliotek klienta Oracle w trybie UTF-16. Powoduje to klienta Oracle biblioteki, aby zaakceptować UTF-16 (który jest bardzo podobny do UCS 2) zamiast wielobajtowego ciągów. Dzięki temu dostawca danych dla Oracle zawsze pracować z dowolnej strony kodowej Oracle bez konieczności dodatkowej translacji działań. Ta konfiguracja działa tylko, jeśli używasz Oracle 9i klientów do komunikacji z bazą danych programu Oracle 9i z zestawem znaków alternatywnych AL16UTF16. Gdy klienta Oracle 9i komunikuje się z serwerem Oracle 9i, można przekonwertować Unicode są wymagane dodatkowe zasoby **CommandText** wartości na odpowiedni znak wielobajtowego zestawu Oracle9i korzysta z serwera. Można tego uniknąć, gdy wiesz, że masz bezpiecznej konfiguracji przez dodanie `Unicode=True` do parametrów połączenia.  
  
### <a name="mixing-versions-of-oracle-client-and-oracle-server"></a>Mieszanie wersji klienta Oracle i serwera Oracle  
 Oracle 8i klienci nie mają dostępu **NCHAR**, **NVARCHAR2**, lub **NCLOB** danych w bazach danych 9i Oracle gdy zestaw znaków national serwera jest określony jako AL16UTF16 ( domyślne ustawienie dla Oracle 9i). Ponieważ obsługa zestawu znaków UTF-16 nie zostało wprowadzone do czasu Oracle 9i, Oracle 8i klientów nie można go odczytać.  
  
### <a name="working-with-utf-8-data"></a>Praca z danymi UTF-8  
 Zestaw znaków alternatywnych, ustawia HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\HOMEID\NLS_LANG klucz rejestru do UTF8. W danej platformy, aby uzyskać więcej informacji, zobacz uwagi instalacji programu Oracle. Ustawienie domyślne to zestaw znaków podstawowego języka, z którego instalowania oprogramowania klienta Oracle. To ustawienie nie zostanie języka aby dopasować zestaw znaków języków narodowych bazy danych, z którym chcesz się połączyć spowoduje powiązania parametru i kolumny do wysyłania i odbierania danych w podstawowej bazie danych zestawu znaków, nie zestaw znaków national.  
  
### <a name="oraclelob-can-only-update-full-characters"></a>OracleLob może aktualizować tylko pełna znaków.  
 Ze względu na użyteczność <xref:System.Data.OracleClient.OracleLob> obiekt dziedziczy z klasy strumieniu .NET Framework i oferuje **ReadByte** i **Element WriteByte** metody. On również implementuje metody, takie jak **CopyTo** i **wymazać**, że pracować nad sekcje Oracle **LOB** obiektów. Z kolei klienta Oracle udostępnia kilka interfejsów API do pracy z znak **LOB**s (**CLOB** i **NCLOB**). Jednak te interfejsy API działać tylko pełna znaków. Z powodu tej różnicy dostawcy danych dla programu Oracle zapewnia obsługę **odczytu** i **ReadByte** do pracy z danymi UTF-16, w sposób byte-wise. Jednak inne metody **OracleLob** obiektu Zezwalaj tylko na operacje pełnej znak.  
  
## <a name="see-also"></a>Zobacz też  
 [Oracle i ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
