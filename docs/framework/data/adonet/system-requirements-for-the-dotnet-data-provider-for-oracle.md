---
title: Wymagania systemowe Dostawca danych .NET Framework dla programu Oracle
ms.date: 03/30/2017
ms.assetid: 054f76b9-1737-43f0-8160-84a00a387217
ms.openlocfilehash: b64a84b8d8246bae9028a6ca710f0a62cc85bf79
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894380"
---
# <a name="system-requirements-for-the-net-framework-data-provider-for-oracle"></a>Wymagania systemowe Dostawca danych .NET Framework dla programu Oracle
.NET Framework Dostawca danych dla programu Oracle wymaga programu Microsoft Data Access Components (MDAC) w wersji 2,6 lub nowszej. Zaleca się używanie programu MDAC 2,8 z dodatkiem SP1.  
  
 Wymagany jest również klient Oracle 8i w wersji 3 (8.1.7) lub nowszy.  
  
 Oprogramowanie klienckie Oracle starsze niż wersja Oracle 9i nie może uzyskać dostępu do baz danych UTF16, ponieważ UTF16 to nowa funkcja w systemie Oracle 9i. Aby użyć tej funkcji, należy uaktualnić oprogramowanie klienckie do wersji Oracle 9i lub nowszej.  
  
## <a name="working-with-the-data-provider-for-oracle-and-unicode-data"></a>Praca z Dostawca danychami dla danych Oracle i Unicode  
 Poniżej znajduje się lista problemów związanych z kodowaniem Unicode, które należy wziąć pod uwagę podczas pracy z Dostawca danych .NET Framework dla bibliotek klienckich Oracle i Oracle. Aby uzyskać więcej informacji, zapoznaj się z dokumentacją firmy Oracle.  
  
### <a name="setting-the-unicode-value-in-a-connection-string-attribute"></a>Ustawianie wartości Unicode w atrybucie parametrów połączenia  
 Podczas pracy z programem Oracle można użyć atrybutu parametrów połączenia  
  
`Unicode=True`
  
 Aby zainicjować biblioteki klienckie Oracle w trybie UTF-16. Powoduje to, że biblioteki klienckie Oracle akceptują UTF-16 (co jest bardzo podobne do UCS-2) zamiast ciągów wielobajtowych. Dzięki temu Dostawca danych dla programu Oracle będzie zawsze współpracować ze stroną kodową Oracle bez dodatkowych zadań związanych z tłumaczeniami. Ta konfiguracja działa tylko w przypadku korzystania z klientów Oracle 9i do komunikowania się z bazą danych Oracle 9i z alternatywnym zestawem znaków AL16UTF16. Gdy klient Oracle 9i komunikuje się z serwerem Oracle 9i, do konwersji wartości **CommandText** Unicode na odpowiedni zestaw znaków wielobajtowych używanych przez serwer Oracle9i są wymagane dodatkowe zasoby. Można to uniknąć, Jeśli wiesz, że masz bezpieczną konfigurację przez dodanie `Unicode=True` do parametrów połączenia.  
  
### <a name="mixing-versions-of-oracle-client-and-oracle-server"></a>Mieszanie wersji klienta Oracle i serwera Oracle  
 Klienci Oracle 8i nie mogą uzyskać dostępu do danych w formacie **nchar**, **NVARCHAR2**lub **NCLOB** w bazach danych Oracle 9i, gdy Narodowy zestaw znaków serwera jest określony jako AL16UTF16 (domyślne ustawienie dla Oracle 9i). Ponieważ obsługa zestawu znaków UTF-16 nie została wprowadzona do momentu Oracle 9i, klienci Oracle 8i nie mogą go odczytać.  
  
### <a name="working-with-utf-8-data"></a>Praca z danymi UTF-8  
 Aby ustawić alternatywny zestaw znaków, Ustaw klucz rejestru HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\HOMEID\NLS_LANG na UTF8. Aby uzyskać więcej informacji, zobacz uwagi dotyczące instalacji oprogramowania Oracle na platformie. Ustawieniem domyślnym jest podstawowy zestaw znaków języka, z którego jest instalowane oprogramowanie klienckie Oracle. Nie ustawienie języka tak, aby był zgodny z zestawem znaków języka narodowego bazy danych, z którą nawiązujesz połączenie, spowoduje, że powiązania parametrów i kolumn będą wysyłać lub odbierać dane w podstawowym zestawie znaków bazy danych, a nie w zestawie znaków narodowych.  
  
### <a name="oraclelob-can-only-update-full-characters"></a>OracleLob może aktualizować tylko pełne znaki.  
 Ze względów <xref:System.Data.OracleClient.OracleLob> użyteczności obiekt dziedziczy z klasy strumienia .NET Framework i udostępnia metody **ReadByte** i **WriteByte** . Implementuje również metody, takie jak **CopyTo** i **Erase**, które pracują z sekcjami obiektów **LOB** Oracle. Z kolei oprogramowanie klienckie Oracle udostępnia wiele interfejsów API do pracy z znakami **LOB**(**obiektów CLOB** i **NCLOB**). Jednak te interfejsy API działają tylko w przypadku pełnych znaków. Ze względu na tę różnicę Dostawca danych w przypadku oprogramowania Oracle implementuje obsługę funkcji **Read** i **ReadByte** , która umożliwia korzystanie z danych UTF-16 w sposób spójny. Jednak inne metody obiektu **OracleLob** umożliwiają tylko wykonywanie operacji pełnych znaków.  
  
## <a name="see-also"></a>Zobacz także

- [Oracle i ADO.NET](oracle-and-adonet.md)
- [Omówienie ADO.NET](ado-net-overview.md)
