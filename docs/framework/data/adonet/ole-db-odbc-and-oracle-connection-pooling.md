---
title: Połączenia Oracle, OLE DB i ODBC buforowanie
ms.date: 03/30/2017
ms.assetid: 2bd83b1e-3ea9-43c4-bade-d9cdb9bbbb04
ms.openlocfilehash: 3ce65036605b7693955c3a6064fca80263d3538f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43527379"
---
# <a name="ole-db-odbc-and-oracle-connection-pooling"></a>Połączenia Oracle, OLE DB i ODBC buforowanie
Tworzenie puli połączeń mogą znacznie poprawić wydajność i skalowalność aplikacji. W tej sekcji omówiono tworzenie puli połączeń dla dostawcy danych .NET Framework dla OLE DB, ODBC i Oracle.  
  
## <a name="connection-pooling-for-oledb"></a>Tworzenie puli połączeń dla OLE DB  
 .NET Framework Data Provider for OLE DB automatycznie pul połączeń przy użyciu puli sesji OLE DB. Argumenty ciągu połączenia może służyć do Włączanie lub wyłączanie usług OLE DB, łącznie z puli. Na przykład następujący ciąg połączenia wyłącza buforowanie sesji OLE DB i rejestracji automatycznej transakcji.  
  
```  
Provider=SQLOLEDB;OLE DB Services=-4;Data Source=localhost;Integrated Security=SSPI;  
```  
  
 Firma Microsoft zaleca, zawsze możesz zamknąć lub usunąć połączenie po zakończeniu korzystania z niego w celu Zwróć połączenia do puli. Połączenia, które nie zostały jawnie zamknięte nie może być zwrócona do puli. Na przykład połączenia, który przeszedł poza zakresem, ale które nie zostało jawnie zamknięte tylko powróci do puli połączeń, jeśli osiągnięto maksymalny rozmiar puli, a połączenie jest nadal ważny.  
  
 Aby uzyskać więcej informacji na temat sesji OLE DB lub pule zasobów, a także jak wyłączyć buforowanie przez zastąpienie ustawień domyślnych usługi dostawcy OLE DB, zobacz [OLE DB przewodnik](https://go.microsoft.com/fwlink/?linkid=45232).  
  
## <a name="connection-pooling-for-odbc"></a>Tworzenie puli połączeń dla Odbc  
 Tworzenie puli połączeń dla .NET Framework Data Provider for ODBC jest zarządzany przez Menedżera sterowników ODBC jest używany dla połączenia, która nie występuje w .NET Framework Data Provider for ODBC.  
  
 Aby włączyć lub wyłączyć buforowanie połączeń, należy otworzyć **Administrator źródła danych ODBC** w folderze Narzędzia administracyjne w Panelu sterowania. **Buforowanie połączeń** karcie można określić parametrów dla każdego sterownika ODBC zainstalowane buforowania połączeń. Należy pamiętać, że połączenie zmiany buforowania dla określonego sterownika ODBC mieć wpływ na wszystkie aplikacje, które używają tego sterownika ODBC.  
  
## <a name="connection-pooling-for-oracleclient"></a>Tworzenie puli połączeń dla programu OracleClient  
 .NET Framework Data Provider for Oracle zapewnia buforowanie połączeń, automatycznie dla aplikacji klienckiej ADO.NET. Można też podać kilka modyfikatorów parametrów połączenia do kontrolowania zachowania buforowania połączeń (zobacz "Kontrolowanie połączenia puli za pomocą połączenia ciąg słów kluczowych," w dalszej części tego tematu).  
  
### <a name="pool-creation-and-assignment"></a>Tworzenie puli i przypisanie  
 Po otwarciu połączenia puli połączeń jest oparta na dokładne algorytm dopasowania, które kojarzy puli przy użyciu parametrów połączenia w połączeniu. Każdej puli połączeń jest skojarzony z parametrami połączenia distinct. Po otwarciu nowego połączenia, jeśli parametry połączenia nie jest dokładnie dopasowany do istniejącej puli, tworzona jest nowa pula.  
  
 Po utworzeniu pul połączeń nie są niszczone, do czasu zakończenia aktywnego procesu. Obsługa pul nieaktywne lub jest pusty używa bardzo mało zasobów systemowych.  
  
### <a name="connection-addition"></a>Dodawanie połączenia  
 Puli połączeń jest tworzony dla każdego ciągu unikatowego połączenia. Po utworzeniu puli wielu obiektów połączeń są tworzone i dodawane do puli, dzięki czemu puli minimalny wymagany rozmiar jest spełniony. Połączenia są dodawane do puli, zgodnie z potrzebami, maksymalnie maksymalny rozmiar puli.  
  
 Gdy <xref:System.Data.OracleClient.OracleConnection> Zażądano obiektu, jest uzyskiwana z puli, jeśli można używać połączenia jest dostępny. Może być używany, połączenie musi aktualnie używana, mają pasujących kontekstu transakcji lub nie być skojarzone z jakimkolwiek kontekście transakcji i mają prawidłowe łącze do serwera.  
  
 Jeśli osiągnięty maksymalny rozmiar puli, a nie można używać połączenia jest dostępna, żądanie znajduje się w kolejce. Pulę połączeń spełnia te żądania przez ponowne przydzielanie połączenia po ich wydaniu do puli. Połączenia są wydawane do puli, gdy są one zamknięte lub usunięty.  
  
### <a name="connection-removal"></a>Usuwanie połączeń  
 Pulę połączeń usuwa połączenie z puli, po była bezczynna przez dłuższy czas lub pulę wykryje, że zostały oddzielone połączenia z serwerem. Należy zwrócić uwagę na to, czy to można wykryć tylko po próby komunikacji z serwerem. Jeśli połączenie zostanie znaleziony, który nie jest już połączony z serwerem, jest oznaczona jako niepoprawna. Pulę połączeń okresowo skanuje pul połączeń wyszukiwanie obiektów, które zostały zwolnione z pulą i są oznaczone jako nieprawidłowe. Połączenia te są następnie trwale usunięte.  
  
 Jeśli połączenie istnieje na serwerze, na którym nie zniknie, to połączenie może być pobierana z puli, jeśli nie wykryto połączenia ODCIĘTA i ona oznaczona jako niepoprawna pulę połączeń. W takim wypadku, generowany jest wyjątek. Jednak nadal należy zamknąć połączenie w celu zwolnij go z powrotem do puli.  
  
 Nie wywołuj `Close` lub `Dispose` na `Connection`, `DataReader`, lub inne obiekt zarządzany w `Finalize` metody klasy. W finalizatora zwolnić tylko niezarządzane zasoby, które należą bezpośrednio do swojej klasy. Jeśli klasa nie ma żadnych niezarządzanych zasobów, nie dołączaj `Finalize` metody w swojej definicji klasy. Aby uzyskać więcej informacji, zobacz [wyrzucania elementów bezużytecznych](../../../../docs/standard/garbage-collection/index.md).  
  
### <a name="transaction-support"></a>Obsługa transakcji  
 Połączenia są pobierane z puli i przypisane transakcji na podstawie kontekstu. Kontekst żądania wątku i przypisane połączenia muszą być zgodne. W związku z tym, każdej puli połączeń jest faktycznie podzielone na połączenia z kontekstem transakcji, nie skojarzonych z nimi oraz do *N* segmentami, że każdy zawiera połączenia z kontekstem określonej transakcji.  
  
 Gdy połączenie jest zamknięte, jest on zwalniany powrót do puli i odpowiednie części pola na podstawie jego kontekstu transakcji. W związku z tym, można zamknąć połączenia nie generuje błąd, mimo że transakcja rozproszona jest nadal oczekujące. Dzięki temu można zatwierdzić lub przerwać transakcję rozproszoną w późniejszym czasie.  
  
### <a name="controlling-connection-pooling-with-connection-string-keywords"></a>Kontrolowanie buforowania połączeń ze słowami kluczowymi ciąg połączenia  
 <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> Właściwość <xref:System.Data.OracleClient.OracleConnection> obiekt obsługuje pary klucz/wartość ciągu połączenia, których można użyć, aby dostosować zachowanie buforowania logiki połączeń.  
  
 W poniższej tabeli opisano <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> wartości można użyć, aby dostosować zachowanie buforowania połączeń.  
  
|Nazwa|Domyślny|Opis|  
|----------|-------------|-----------------|  
|`Connection Lifetime`|0|Połączenia są zwracane do puli, jej godzina utworzenia jest porównywany z bieżącym czasem, gdy połączenie jest niszczony, jeśli ten przedział czasu (w sekundach) przekracza wartość określoną przez `Connection Lifetime`. Jest to przydatne w konfiguracji klastra, aby wymusić Równoważenie obciążenia między używania serwera i serwera, po prostu przełączyć do trybu online.<br /><br /> Wartość zero (0) spowoduje, że mieć maksymalny limit czasu puli połączeń.|  
|`Enlist`|'true'|Gdy `true`, pulę automatycznie powoduje zarejestrowanie połączenia w bieżącym kontekście transakcji tworzenia wątku, jeśli istnieje kontekst transakcji.|  
|`Max Pool Size`|100|Maksymalna liczba dozwolonych w puli połączeń.|  
|`Min Pool Size`|0|Minimalna liczba połączeń w puli.|  
|`Pooling`|'true'|Gdy `true`, połączenie jest rysowana od odpowiedniej puli, lub jeśli to konieczne, utworzony i dodany do odpowiedniej puli.|  
  
## <a name="see-also"></a>Zobacz też  
 [Pula połączeń](../../../../docs/framework/data/adonet/connection-pooling.md)  
 [Liczniki wydajności](../../../../docs/framework/data/adonet/performance-counters.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
