---
title: Wymagania systemowe dla dostawcy danych .NET Framework dla oracle
ms.date: 03/30/2017
ms.assetid: 054f76b9-1737-43f0-8160-84a00a387217
ms.openlocfilehash: dab3378d3022c01c674640201a67f3bdbb4f571f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174254"
---
# <a name="system-requirements-for-the-net-framework-data-provider-for-oracle"></a>Wymagania systemowe dla dostawcy danych .NET Framework dla oracle

Dostawca danych programu .NET Framework dla programu Oracle wymaga wersji 2.6 (MDAC) w wersji 2.6 lub nowszej. Zaleca się stosowanie mdac 2.8 SP1.  
  
 Musisz również mieć zainstalowanego klienta Oracle 8i Release 3 (8.1.7) lub nowszego.  
  
 Oprogramowanie Oracle Client przed wersją Oracle 9i nie może uzyskać dostępu do baz danych UTF16, ponieważ UTF16 jest nową funkcją w Oracle 9i. Aby korzystać z tej funkcji, należy uaktualnić oprogramowanie klienckie do oracle 9i lub nowszego.  
  
## <a name="working-with-the-data-provider-for-oracle-and-unicode-data"></a>Współpraca z dostawcą danych oracle i unicode data  

Poniżej znajduje się lista problemów związanych z Unicode, które należy wziąć pod uwagę podczas pracy z dostawcą danych .NET Framework dla bibliotek klientów Oracle i Oracle. Aby uzyskać więcej informacji, zapoznaj się z dokumentacją Oracle.  
  
### <a name="setting-the-unicode-value-in-a-connection-string-attribute"></a>Ustawianie wartości Unicode w atrybucie ciągu połączenia  

Podczas pracy z Oracle można użyć atrybutu parametry połączenia  
  
`Unicode=True`
  
, aby zainicjować biblioteki klientów Oracle w trybie UTF-16. Powoduje to, że biblioteki klientów Oracle do akceptowania UTF-16 (który jest bardzo podobny do LUW-2) zamiast ciągów wielo bajtowych. Dzięki temu dostawca danych oracle zawsze może pracować z dowolną stroną kodową Oracle bez dodatkowej pracy tłumaczeniowej. Ta konfiguracja działa tylko wtedy, gdy używasz klientów Oracle 9i do komunikowania się z bazą danych Oracle 9i z alternatywnym zestawem znaków AL16UTF16. Gdy klient Oracle 9i komunikuje się z serwerem Oracle 9i, wymagane są dodatkowe zasoby do konwersji wartości **Unicode CommandText** na odpowiedni wielo bajtowy zestaw znaków używany przez serwer Oracle9i. Można tego uniknąć, gdy wiesz, że masz `Unicode=True` bezpieczną konfigurację, dodając do ciągu połączenia.  
  
### <a name="mixing-versions-of-oracle-client-and-oracle-server"></a>Mieszanie wersji oracle client i oracle server  

Klienci Oracle 8i nie mogą uzyskać dostępu do danych **NCHAR,** **NVARCHAR2**lub **NCLOB** w bazach danych Oracle 9i, gdy krajowy zestaw znaków serwera jest określony jako AL16UTF16 (domyślne ustawienie dla Oracle 9i). Ponieważ obsługa zestawu znaków UTF-16 została wprowadzona dopiero w oracle 9i, klienci Oracle 8i nie mogą go odczytać.  
  
### <a name="working-with-utf-8-data"></a>Praca z danymi UTF-8  

Aby ustawić alternatywny zestaw znaków, ustaw HKEY_LOCAL_MACHINE klucz rejestru\SOFTWARE\ORACLE\HOMEID\NLS_LANG na UTF8. Więcej informacji można znaleźć w uwagach dotyczących instalacji Oracle na swojej platformie. Ustawieniem domyślnym jest podstawowy zestaw znaków języka, z którego instalujesz oprogramowanie Klienta Oracle. Nie ustawienie języka zgodnego z zestawem znaków języka narodowego bazy danych, z którą się łączysz, spowoduje, że powiązania parametrów i kolumn będą wysyłać lub odbierać dane w podstawowym zestawie znaków bazy danych, a nie w krajowym zestawie znaków.  
  
### <a name="oraclelob-can-only-update-full-characters"></a>OracleLob może aktualizować tylko pełne znaki.  

Ze względu na <xref:System.Data.OracleClient.OracleLob> użyteczność obiekt dziedziczy z klasy .NET Framework Stream i udostępnia metody **ReadByte** i **WriteByte.** Implementuje również metody, takie jak **CopyTo** i **Erase**, które działają na sekcje oracle **lob** obiektów. Natomiast oprogramowanie klienckie Oracle udostępnia szereg interfejsów API do pracy z **lobami**znaków **(CLOB** i **NCLOB).** Jednak te interfejsy API działają tylko na pełnych znakach. Z powodu tej różnicy dostawca danych dla oracle implementuje obsługę **odczytu** i **odczytu** do pracy z danymi UTF-16 w sposób bajtowy. Jednak inne metody **OracleLob** obiektu zezwalają tylko na operacje pełnoznakowe.  
  
## <a name="see-also"></a>Zobacz też

- [Oracle i ADO.NET](oracle-and-adonet.md)
- [Omówienie ADO.NET](ado-net-overview.md)
