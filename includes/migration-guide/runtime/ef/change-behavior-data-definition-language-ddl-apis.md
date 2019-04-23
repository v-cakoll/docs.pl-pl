---
ms.openlocfilehash: 1f06a185939c40274adad1ceac6990719069167a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804714"
---
### <a name="change-in-behavior-in-data-definition-language-ddl-apis"></a>Zmiana zachowania w definicji języka DDL (Data) interfejsów API

|   |   |
|---|---|
|Szczegóły|Zachowanie API DDL, gdy określona jest AttachDBFilename zmienił się w następujący sposób:<ul><li>Parametry połączeń nie muszą określać wartość katalog początkowy. Wcześniej zarówno AttachDBFilename, jak i Initial Catalog były wymagane.</li><li>Jeśli określono zarówno AttachDBFilename, jak i Initial Catalog i istnieje dany plik MDF, <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A> metoda zwraca <code>true</code>. Uprzednio była zwracana <code>false</code>.</li><li>Jeśli określono zarówno AttachDBFilename, jak i Initial Catalog i istnieje dany plik MDF, wywołanie <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> metoda usuwa pliki.</li><li>Jeśli <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> jest wywoływana, gdy parametry połączenia określają wartość AttachDBFilename z plikiem MDF, który nie istnieje i Initial Catalog, który nie istnieje, metoda zgłasza <xref:System.InvalidOperationException> wyjątku. Poprzednio, wyrzucany <xref:System.Data.SqlClient.SqlException> wyjątku.</li></ul>|
|Sugestia|Te zmiany ułatwiają tworzenie narzędzi i aplikacji używających interfejsów API języka DDL. Te zmiany mogą wpływać na zgodność aplikacji w następujących scenariuszach:<ul><li>Użytkownik pisze kod wykonujący <code>DROP DATABASE</code> polecenia bezpośrednio bez wywoływania <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> Jeśli <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A> zwraca <code>true</code>. Przerywa to działanie istniejącego kodu, jeśli baza danych nie jest dołączona, ale plik MDF istnieje.</li><li>Użytkownik pisze kod, który oczekuje, że <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> metodę, aby zgłosić <xref:System.Data.SqlClient.SqlException> zamiast <xref:System.InvalidOperationException> gdy plik wykazu początkowego i MDF nie istnieją.</li></ul>|
|Zakres|Mały|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
