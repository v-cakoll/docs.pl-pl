---
title: Wymagania systemowe programu .NET Framework Data Provider for Oracle
ms.date: 03/30/2017
ms.assetid: 054f76b9-1737-43f0-8160-84a00a387217
ms.openlocfilehash: 61f8509cce248f6cc0a56900227f9758eb27c4e0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111050"
---
# <a name="system-requirements-for-the-net-framework-data-provider-for-oracle"></a>Wymagania systemowe programu .NET Framework Data Provider for Oracle
.NET Framework Data Provider for Oracle wymaga programu Microsoft Data Access Components (MDAC) w wersji 2.6 lub nowszej. Zaleca się MDAC 2.8 SP1.  
  
 Musisz również posiadać wersję klienta Oracle 8i w wersji 3 (8.1.7) lub nowszy.  
  
 Oprogramowanie klienckie Oracle wcześniejszymi niż wersja programu Oracle 9i nie mają dostępu UTF16 baz danych, ponieważ UTF16 jest nową funkcją w Oracle 9i. Aby użyć tej funkcji, należy uaktualnić oprogramowanie klienta Oracle 9i lub nowszej.  
  
## <a name="working-with-the-data-provider-for-oracle-and-unicode-data"></a>Praca z dostawcy danych do bazy danych Oracle i danych Unicode  
 Poniżej znajduje się lista problemów dotyczących Unicode, które należy wziąć pod uwagę podczas pracy z .NET Framework Data Provider for Oracle i Oracle bibliotek klienckich. Aby uzyskać więcej informacji zajrzyj do dokumentacji programu Oracle.  
  
### <a name="setting-the-unicode-value-in-a-connection-string-attribute"></a>Ustawienie wartości Unicode na atrybut parametrów połączenia  
 Podczas pracy z bazą danych Oracle, można użyć atrybut parametrów połączenia  
  
```  
Unicode=True   
```  
  
 można zainicjować biblioteki klienta Oracle w trybie UTF-16. Powoduje to klienta Oracle biblioteki zaakceptować UTF-16, (która jest bardzo podobne do UCS-2) zamiast ciągów znaków wielobajtowych. Dzięki temu dostawcy danych na oprogramowanie Oracle Praca zawsze przy użyciu dowolnej strony kodu Oracle bez wykonywania pracy dodatkowe tłumaczenia. Ta konfiguracja tylko wtedy, gdy używasz klientów 9i Oracle do komunikowania się z bazą danych Oracle 9i z zestawem znaków alternatywne AL16UTF16. Gdy klienta Oracle 9i komunikuje się z serwerem Oracle 9i, dodatkowe zasoby są wymagane do konwersji z Unicode **CommandText** wartości do odpowiedniego znaku wielobajtowego zestawu Oracle9i korzysta z serwera. To można uniknąć, gdy wiesz, że ma bezpieczne konfiguracji, dodając `Unicode=True` do parametrów połączenia.  
  
### <a name="mixing-versions-of-oracle-client-and-oracle-server"></a>Mieszanie wersji klienta Oracle i serwera Oracle  
 Oracle 8i klienci nie mają dostępu **NCHAR**, **NVARCHAR2**, lub **NCLOB** danych w bazach danych dla bazy danych Oracle 9i gdy zestaw znaków national serwera jest określony jako AL16UTF16 ( domyślne ustawienie dla Oracle 9i). Ponieważ obsługa zestawu znaków UTF-16 nie została wprowadzona do momentu 9i Oracle, Oracle, 8i klientów nie można go odczytać.  
  
### <a name="working-with-utf-8-data"></a>Praca z danymi w formacie UTF-8  
 Zestaw znaków alternatywne, ustawia HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\HOMEID\NLS_LANG klucza rejestru do UTF8. Zobacz uwagi dotyczące instalacji oprogramowania Oracle na platformie w taki sposób, aby uzyskać więcej informacji. Ustawieniem domyślnym jest zestaw znaków podstawowego języka, w którym ją instalujesz oprogramowanie klienckie Oracle. To ustawienie nie zostanie języka zgodna z zestawem znaków języków narodowych bazy danych, do której się łączysz spowoduje, że powiązania parametrów i kolumny do wysyłania lub odbierania danych w podstawowej bazie danych zestawu znaków, nie zestaw znaków krajowych.  
  
### <a name="oraclelob-can-only-update-full-characters"></a>OracleLob może aktualizować jedynie pełny znaków.  
 Ze względu na użyteczność <xref:System.Data.OracleClient.OracleLob> obiekt dziedziczy z klasy .NET Framework Stream i zapewnia **ReadByte** i **Element WriteByte** metody. Implementuje także metod, takich jak **CopyTo** i **wymazać**, które działają na sekcje Oracle **LOB** obiektów. W odróżnieniu od nich oprogramowanie klienckie Oracle oferuje pewną liczbę interfejsów API do pracy ze znakiem **LOB**s (**CLOB** i **NCLOB**). Jednak te interfejsy API pracować na pełnej tylko znaki. Z powodu tej różnicy Data Provider Pro Oracle TFTP implementuje obsługę **odczytu** i **ReadByte** do pracy z danymi UTF-16 w sposób byte-wise. Jednak inne metody **OracleLob** obiektu Zezwalaj tylko na operacje pełnej znaków.  
  
## <a name="see-also"></a>Zobacz także

- [Oracle i ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
