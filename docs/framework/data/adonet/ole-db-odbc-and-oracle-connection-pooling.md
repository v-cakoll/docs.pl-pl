---
title: Buforowanie połączenia Oracle, OLE DB i ODBC
ms.date: 03/30/2017
ms.assetid: 2bd83b1e-3ea9-43c4-bade-d9cdb9bbbb04
ms.openlocfilehash: 7552f4a95af51774071f0a4017637570d648dd86
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929256"
---
# <a name="ole-db-odbc-and-oracle-connection-pooling"></a>Buforowanie połączenia Oracle, OLE DB i ODBC
Połączenia w puli mogą znacząco zwiększyć wydajność i skalowalność aplikacji. W tej sekcji omówiono pule połączeń .NET Framework dostawców danych dla OLE DB, ODBC i Oracle.  
  
## <a name="connection-pooling-for-oledb"></a>Buforowanie połączeń dla OleDb  
 Dostawca danych .NET Framework dla OLE DB automatycznie pule połączeń przy użyciu puli sesji OLE DB. Argumenty parametrów połączenia mogą służyć do włączania lub wyłączania usług OLE DB, takich jak pule. Na przykład następujące parametry połączenia uniemożliwiają OLE DB pule sesji i automatyczne rejestracje transakcji.  
  
```  
Provider=SQLOLEDB;OLE DB Services=-4;Data Source=localhost;Integrated Security=SSPI;  
```  
  
 Zaleca się, aby zawsze zamykać lub zbyć połączenie po zakończeniu korzystania z niego w celu zwrócenia połączenia z pulą. Połączenia, które nie są jawnie zamknięte, mogą nie zostać zwrócone do puli. Na przykład połączenie, które zostało utracone poza zakresem, ale nie zostało jawnie zamknięte, zostanie zwrócone do puli połączeń tylko wtedy, gdy Osiągnięto maksymalny rozmiar puli, a połączenie jest nadal ważne.  
  
 Aby uzyskać więcej informacji na temat OLE DB sesji lub puli zasobów, a także sposobu wyłączania puli przez zastępowanie ustawień domyślnych usługi dostawcy OLE DB, zobacz [Podręcznik programisty programu OLE DB](https://go.microsoft.com/fwlink/?linkid=45232).  
  
## <a name="connection-pooling-for-odbc"></a>Buforowanie połączeń dla ODBC  
 Pule połączeń dla Dostawca danych .NET Framework dla ODBC są zarządzane przez Menedżera sterowników ODBC, który jest używany do połączenia, i nie ma wpływ na .NET Framework Dostawca danych dla ODBC.  
  
 Aby włączyć lub wyłączyć buforowanie połączeń, Otwórz pozycję **Administrator źródła danych ODBC** w folderze Narzędzia administracyjne w panelu sterowania. Karta **pula połączeń** umożliwia określenie parametrów puli połączeń dla każdego zainstalowanego sterownika ODBC. Należy pamiętać, że zmiany puli połączeń dla określonego sterownika ODBC mają wpływ na wszystkie aplikacje używające tego sterownika ODBC.  
  
## <a name="connection-pooling-for-oracleclient"></a>Buforowanie połączeń dla OracleClient  
 .NET Framework Dostawca danych dla programu Oracle zapewnia automatyczne buforowanie połączeń dla aplikacji klienckiej ADO.NET. Możesz również podać kilka modyfikatorów parametrów połączenia, aby kontrolować zachowanie puli połączeń (zobacz "kontrolowanie puli połączeń ze słowami kluczowymi parametrów połączenia" w dalszej części tego tematu).  
  
### <a name="pool-creation-and-assignment"></a>Tworzenie i przypisywanie puli  
 Po otwarciu połączenia tworzona jest pula połączeń oparta na dokładnie zgodnym algorytmie, który kojarzy pulę z parametrami połączenia w połączeniu. Każda pula połączeń jest skojarzona z unikatowymi parametrami połączenia. W przypadku otwarcia nowego połączenia, jeśli parametry połączenia nie są dokładnie zgodne z istniejącą pulą, tworzona jest nowa pula.  
  
 Po utworzeniu pule połączeń nie są niszczone do momentu zakończenia aktywnego procesu. Obsługa nieaktywnych lub pustych pul używa bardzo mało zasobów systemowych.  
  
### <a name="connection-addition"></a>Dodawanie połączenia  
 Pula połączeń jest tworzona dla każdego unikatowego ciągu połączenia. Po utworzeniu puli do puli są tworzone i dodawane wiele obiektów połączeń, aby zapewnić spełnienie minimalnych wymagań dotyczących rozmiaru puli. Połączenia są dodawane do puli w razie potrzeby do maksymalnego rozmiaru puli.  
  
 Po zażądaniu <xref:System.Data.OracleClient.OracleConnection> obiektu jest on uzyskiwany z puli, jeśli dostępne jest połączenie użyteczne. Aby można było korzystać z tego połączenia, połączenie musi być obecnie nieużywane, mieć pasujący kontekst transakcji lub nie być skojarzone z żadnym kontekstem transakcji i mieć prawidłowe połączenie z serwerem.  
  
 Jeśli maksymalny rozmiar puli został osiągnięty i nie jest dostępne żadne możliwe połączenie, żądanie jest umieszczane w kolejce. Pulę połączenia spełnia te żądania, ponownie przydzielając połączenia po ich wydaniu z powrotem do puli. Połączenia są zwalniane z powrotem do puli, gdy są zamknięte lub usuwane.  
  
### <a name="connection-removal"></a>Usuwanie połączenia  
 Połączenie pulę usuwa połączenie z puli, gdy było ono bezczynne przez dłuższy czas lub jeśli pulę wykryje, że połączenie z serwerem zostało odłączone. Należy zauważyć, że można to wykryć tylko po próbie komunikacji z serwerem. Jeśli zostanie znalezione połączenie, które nie jest już połączone z serwerem, jest oznaczone jako nieprawidłowe. Pulę połączenia okresowo skanuje pule połączeń, szukając obiektów, które zostały wydane do puli i są oznaczone jako nieprawidłowe. Zostaną one trwale usunięte.  
  
 Jeśli połączenie istnieje na serwerze, który został wyświetlony, to połączenie może być narysowane z puli, jeśli połączenie pulę nie wykryło poprawnego połączenia i zostało oznaczone jako nieprawidłowe. W takim przypadku zostanie wygenerowany wyjątek. Jednak nadal należy zamknąć połączenie w celu zwolnienia go z powrotem do puli.  
  
 `Close` Nie wywołuj `Finalize` ani `Dispose` w`Connection`, a`DataReader`, ani żadnego innego obiektu zarządzanego w metodzie klasy. W finalizatorze zwalniane są tylko niezarządzane zasoby, które są własnością klasy bezpośrednio. Jeśli Klasa nie jest własnością żadnych niezarządzanych zasobów, nie Uwzględniaj `Finalize` metody w definicji klasy. Aby uzyskać więcej informacji, zobacz [odzyskiwanie pamięci](../../../standard/garbage-collection/index.md).  
  
### <a name="transaction-support"></a>Obsługa transakcji  
 Połączenia są rysowane z puli i przypisywane na podstawie kontekstu transakcji. Kontekst wątku żądającego i przypisanego połączenia musi być zgodny. W związku z tym każda pula połączeń jest w rzeczywistości podzielona na połączenia bez kontekstu transakcji skojarzonych z nimi oraz do *N* podpodziałów, które każdy z nich zawiera połączenia z określonym kontekstem transakcji.  
  
 Gdy połączenie jest zamknięte, zostaje wydane z powrotem do puli i do odpowiedniej części pola na podstawie kontekstu transakcji. W związku z tym możesz zamknąć połączenie bez generowania błędu, mimo że transakcja rozproszona nadal oczekuje. Dzięki temu możesz zatwierdzić lub przerwać transakcję rozproszoną w późniejszym czasie.  
  
### <a name="controlling-connection-pooling-with-connection-string-keywords"></a>Kontrolowanie puli połączeń przy użyciu słów kluczowych parametrów połączenia  
 <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> Właściwość<xref:System.Data.OracleClient.OracleConnection> obiektu obsługuje pary klucz/wartość parametrów połączenia, których można użyć do dostosowania zachowania logiki puli połączeń.  
  
 W poniższej tabeli opisano <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> wartości, których można użyć do dostosowania zachowania puli połączeń.  
  
|Nazwa|Domyślny|Opis|  
|----------|-------------|-----------------|  
|`Connection Lifetime`|0|Gdy połączenie zostanie zwrócone do puli, jego czas utworzenia jest porównywany z bieżącą godziną i połączenie jest niszczone, jeśli ten przedział czasu (w sekundach) przekroczy wartość określoną `Connection Lifetime`przez. Jest to przydatne w konfiguracjach klastrowanych w celu wymuszenia równoważenia obciążenia między uruchomionym serwerem a serwerem, który został przełączony w tryb online.<br /><br /> Wartość zero (0) powoduje, że połączenia w puli mają maksymalny limit czasu.|  
|`Enlist`|'true'|Kiedy `true`program pulę automatycznie zarejestrowana w bieżącym kontekście transakcji wątku tworzenia, jeśli istnieje kontekst transakcji.|  
|`Max Pool Size`|100|Maksymalna liczba połączeń dozwolonych w puli.|  
|`Min Pool Size`|0|Minimalna liczba połączeń przechowywanych w puli.|  
|`Pooling`|'true'|Gdy `true`połączenie jest narysowane z odpowiedniej puli lub w razie potrzeby utworzone i dodane do odpowiedniej puli.|  
  
## <a name="see-also"></a>Zobacz także

- [Pula połączeń](../../../../docs/framework/data/adonet/connection-pooling.md)
- [Liczniki wydajności](../../../../docs/framework/data/adonet/performance-counters.md)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
