---
ms.openlocfilehash: 4396ff43a48a23df29c5938b6bd2137d527b4ef5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620298"
---
### <a name="change-in-behavior-in-data-definition-language-ddl-apis"></a>Zmiana zachowania w interfejsie API języka definicji danych (DDL)

#### <a name="details"></a>Szczegóły

Zachowanie interfejsów API DDL po określeniu AttachDBFilename zmieniło się w następujący sposób:<ul><li>Parametry połączenia nie muszą określać początkowej wartości katalogu. Wcześniej są wymagane zarówno AttachDBFilename, jak i katalog początkowy.</li><li>Jeśli określono zarówno AttachDBFilename, jak i katalog początkowy, a dany plik MDF istnieje, <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A> Metoda zwraca <code>true</code> . Wcześniej zwrócone <code>false</code> .</li><li>Jeśli określono zarówno AttachDBFilename, jak i katalog początkowy, a dany plik MDF istnieje, wywołanie <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> metody spowoduje usunięcie plików.</li><li>Jeśli <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> jest wywoływana, gdy parametry połączenia określają wartość AttachDBFileName z MDF, która nie istnieje i początkowy wykaz, który nie istnieje, metoda zgłasza <xref:System.InvalidOperationException> wyjątek. Wcześniej wywołał <xref:System.Data.SqlClient.SqlException> wyjątek.</li></ul>

#### <a name="suggestion"></a>Sugestia

Te zmiany ułatwiają tworzenie narzędzi i aplikacji używających interfejsów API języka DDL. Te zmiany mogą wpływać na zgodność aplikacji w następujących scenariuszach:<ul><li>Użytkownik zapisuje kod, który wykonuje <code>DROP DATABASE</code> polecenie bezpośrednio, zamiast wywołania <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> if <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A> Returns <code>true</code> . Przerywa to działanie istniejącego kodu, jeśli baza danych nie jest dołączona, ale plik MDF istnieje.</li><li>Użytkownik zapisuje kod, który oczekuje <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> metody do wygenerowania a, a nie do <xref:System.Data.SqlClient.SqlException> <xref:System.InvalidOperationException> momentu, gdy katalog początkowy i plik MDF nie istnieją.</li></ul>

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Mały|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
