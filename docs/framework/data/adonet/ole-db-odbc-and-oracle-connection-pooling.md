---
title: Połączenia Oracle, OLE DB i ODBC buforowanie
ms.date: 03/30/2017
ms.assetid: 2bd83b1e-3ea9-43c4-bade-d9cdb9bbbb04
ms.openlocfilehash: 2e42b52bb75008fd34f3e4bef1788626d96368bc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ole-db-odbc-and-oracle-connection-pooling"></a>Połączenia Oracle, OLE DB i ODBC buforowanie
Tworzenie puli połączeń może znacznie zwiększyć wydajność i skalowalność aplikacji. W tej sekcji omówiono tworzenie puli połączeń dla dostawcy danych .NET Framework dla OLE DB i ODBC programu Oracle.  
  
## <a name="connection-pooling-for-oledb"></a>Tworzenie puli połączeń dla OleDb  
 .NET Framework Data Provider for OLE DB automatycznie puli połączeń przy użyciu puli sesji OLE DB. Argumenty ciągu połączenia można włączyć lub wyłączyć buforowanie w tym usługi OLE DB. Na przykład następujący ciąg połączenia wyłącza buforowanie sesji OLE DB i transakcji automatycznej rejestracji.  
  
```  
Provider=SQLOLEDB;OLE DB Services=-4;Data Source=localhost;Integrated Security=SSPI;  
```  
  
 Firma Microsoft zaleca, zawsze możesz zamknąć lub usunięcia połączenia po zakończeniu zastosowanie go, aby zwrócić połączenia do puli. Połączenia, które nie są jawnie zamknięty nie może pobrać zwrócony do puli. Na przykład, która wykroczyła poza zakres, ale które nie zostały jawnie zamknął połączenie tylko powróci do puli połączeń Osiągnięto maksymalny rozmiar puli, jeśli połączenie jest nadal ważny.  
  
 Aby uzyskać więcej informacji o sesji OLE DB lub pule zasobów, a także jak wyłączyć buforowanie przez zastąpienie ustawień domyślnych usługi dostawcy OLE DB, zobacz [OLE DB przewodnik](http://go.microsoft.com/fwlink/?linkid=45232).  
  
## <a name="connection-pooling-for-odbc"></a>Tworzenie puli połączeń dla Odbc  
 Tworzenie puli połączeń dla dostawcy danych programu .NET Framework dla ODBC jest zarządzana przez menedżera sterownika ODBC, który jest używany dla połączenia, nie ma wpływu na .NET Framework Data Provider for ODBC.  
  
 Aby włączyć lub wyłączyć buforowanie połączeń, otwórz **Administrator źródła danych ODBC** w folderze Narzędzia administracyjne w Panelu sterowania. **Puli połączeń** karta umożliwia określenie parametrów dla każdego sterownika ODBC zainstalowany buforowania połączeń. Należy pamiętać, że zmiany korzystanie z puli połączeń dla określonego sterownika ODBC wpływają na wszystkie aplikacje, które używają tego sterownika ODBC.  
  
 Aby uzyskać więcej informacji na puli połączeń ODBC, zobacz [informacji: często zadawane pytania dotyczące ODBC puli połączeń](http://support.microsoft.com/kb/169470).  
  
## <a name="connection-pooling-for-oracleclient"></a>Tworzenie puli połączeń dla OracleClient  
 .NET Framework Data Provider for Oracle zapewnia ADO.NET aplikacji klienta automatycznie puli połączeń. Może też podawać wiele modyfikatorów ciągu połączenia można kontrolować zachowanie buforowania połączeń (zobacz "Kontrolowanie połączenia buforowanie ze słowami kluczowymi parametrów połączenia," w dalszej części tego tematu).  
  
### <a name="pool-creation-and-assignment"></a>Tworzenie puli i przypisania  
 Po otwarciu połączenia puli połączeń jest utworzony oparte na dokładne algorytm dopasowania, które kojarzy puli przy użyciu parametrów połączenia dla połączenia. Każdej puli połączeń jest skojarzony z ciągu połączenia distinct. Po otwarciu nowego połączenia, jeśli ciąg połączenia nie jest dokładnego dopasowania do istniejącej puli, jest tworzona nowa pula.  
  
 Po utworzeniu pul połączeń nie zostaną zniszczone do czasu zakończenia aktywnego procesu. Obsługa pule nieaktywne lub pusty używa bardzo mało zasobów systemowych.  
  
### <a name="connection-addition"></a>Dodawanie połączenia  
 Puli połączeń jest tworzona dla każdej parametry połączenia unikatowy. Po utworzeniu puli wielu obiektów połączenia są tworzone i dodawane do puli, dzięki czemu puli minimalny wymagany rozmiar jest spełniony. Połączenia są dodawane do puli, w razie potrzeby do maksymalny rozmiar puli.  
  
 Gdy <xref:System.Data.OracleClient.OracleConnection> wymagany jest obiekt, są uzyskiwane z puli, jeśli jest dostępne połączenie można używać. Może być używany, połączenie musi aktualnie używana, mają pasujących kontekst transakcji lub nie jest skojarzony z żadnym kontekstem transakcji i mają prawidłowe łącze do serwera.  
  
 Jeśli został osiągnięty maksymalny rozmiar puli i nie można używać połączenie nie jest dostępne, żądanie jest przechowywane w kolejce. Pulę połączeń spełnia te żądania przez ponowne przydzielanie połączeń po ich wydaniu do puli. Połączenia są wydawane do puli, gdy są one zamknięty lub usunięty.  
  
### <a name="connection-removal"></a>Usuwanie połączenia  
 Pulę połączeń usuwa połączenie z puli, po bezczynności przez dłuższy czas lub jeśli pulę wykryje, że zostały Przerwano połączenie z serwerem. Należy pamiętać, że to można wykryć tylko po próbie do komunikowania się z serwerem. Jeśli połączenie zostanie znaleziony, który nie jest już połączony z serwerem, jest oznaczony jako nieprawidłowy. Pulę połączeń okresowo skanuje pul połączeń wyszukiwania dla obiektów, które zostały wydane do puli i są oznaczone jako nieprawidłowe. Połączenia te są następnie trwale usunięte.  
  
 Jeśli istnieje połączenie z serwerem nie zniknie, to połączenie można nakreślić z puli, jeśli pulę połączeń ma nie wykryto ODCIĘTA połączenia i nie jest ona oznaczona jako niepoprawna. W takim przypadku jest generowane wyjątek. Jednak nadal musisz zamknąć połączenie w celu zwolnij go z powrotem do puli.  
  
 Nie wywołuj `Close` lub `Dispose` na `Connection`, `DataReader`, lub innego obiektu zarządzanego w `Finalize` metody klasy. W finalizator zwolnić tylko niezarządzane zasoby, które bezpośrednio należą do klasy. Jeśli klasa nie ma żadnych niezarządzanych zasobów, nie dołączaj `Finalize` metody w definicji klasy. Aby uzyskać więcej informacji, zobacz [wyrzucanie elementów bezużytecznych](../../../../docs/standard/garbage-collection/index.md).  
  
### <a name="transaction-support"></a>Obsługa transakcji  
 Połączenia są pobierane z puli i przypisane transakcji na podstawie kontekstu. Kontekst wątku żądania i przypisane połączenia muszą być zgodne. W związku z tym każdej puli połączeń jest rzeczywiście podzielone na połączenia z Brak kontekstu transakcji skojarzonych z nimi, a także do *N* podziałów podrzędnych, że każdy zawierać połączenia z kontekstem transakcji.  
  
 Gdy połączenie jest zamknięte, zwolnieniu do puli, jak i w odpowiednich części, na podstawie jego kontekstu transakcji. W związku z tym można zamknąć połączenia bez wygenerowaniem błędu, nawet jeśli transakcja rozproszona jest nadal oczekujące. Dzięki temu można zatwierdzić lub przerwać transakcji rozproszonych w późniejszym czasie.  
  
### <a name="controlling-connection-pooling-with-connection-string-keywords"></a>Kontrolowanie użycia puli połączeń ze słowami kluczowymi parametrów połączenia  
 <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> Właściwość <xref:System.Data.OracleClient.OracleConnection> obiekt obsługuje pary klucz wartość ciągu połączenia, które pozwalają dostosować zachowanie logiki buforowania połączeń.  
  
 W poniższej tabeli opisano <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> wartości można użyć, aby dostosować zachowanie buforowania połączeń.  
  
|Nazwa|Domyślny|Opis|  
|----------|-------------|-----------------|  
|`Connection Lifetime`|0|Gdy połączenie jest zwracana do puli, jej godzina utworzenia jest porównywany z bieżącym czasem i połączenie zostanie zniszczony, jeśli ten przedział czasu (w sekundach) przekracza wartość określoną przez `Connection Lifetime`. Jest to przydatne w konfiguracji klastra, aby wymusić zrównoważenia obciążenia między programem server i serwer, który właśnie został przełączony do trybu online.<br /><br /> Wartość zero (0) spowoduje mieć maksymalny limit czasu puli połączeń.|  
|`Enlist`|'true'|Gdy `true`, jeśli istnieje w kontekście transakcji pulę automatycznie rejestruje połączenia w bieżącym kontekście transakcji wątku tworzenia.|  
|`Max Pool Size`|100|Maksymalna liczba dozwolonych w puli połączeń.|  
|`Min Pool Size`|0|Minimalna liczba połączeń utrzymywane w puli.|  
|`Pooling`|'true'|Gdy `true`, połączenie jest pobierana z odpowiedniej puli lub w razie potrzeby tworzony i dodawany do odpowiedniej puli.|  
  
## <a name="see-also"></a>Zobacz też  
 [Pula połączeń](../../../../docs/framework/data/adonet/connection-pooling.md)  
 [Liczniki wydajności](../../../../docs/framework/data/adonet/performance-counters.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
