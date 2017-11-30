---
title: "Kolekcje schematów Oracle"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 89a75de8-dee8-45e2-a97f-254d7e62e7e1
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 828e5ae0a9db2542debf8e09e5d8875fcea0ba23
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="oracle-schema-collections"></a>Kolekcje schematów Oracle
Dostawcy danych programu Microsoft .NET Framework dla programu Oracle obsługuje następujące kolekcje określonego schematu, oprócz typowych kolekcje schematów:  
  
-   Kolumny  
  
-   Indeksy  
  
-   IndexColumns  
  
-   Procedury  
  
-   Sekwencje  
  
-   Synonimy  
  
-   Tabele  
  
-   Użytkownicy  
  
-   Widoki  
  
-   Funkcje  
  
-   Pakiety  
  
-   PackageBodies  
  
-   Argumenty  
  
-   UniqueKeys  
  
-   PrimaryKeys  
  
-   ForeignKeys  
  
-   Zawierającej kolumny kluczy obcych  
  
-   ProcedureParameters  
  
## <a name="columns"></a>Kolumny  
  
|Element columnName|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|WŁAŚCICIEL|String|Właściciel tabeli, widoku lub klastra.|  
|TABLE_NAME|String|Tabela, widok lub nazwy klastra.|  
|COLUMN_NAME|String|Nazwa kolumny.|  
|ID|Wartość dziesiętna|Numer kolumny sekwencji, jak utworzyć.|  
|TYP DANYCH|String|Typ danych kolumny.|  
|DŁUGOŚĆ|Wartość dziesiętna|Długość kolumny w bajtach.|  
|DOKŁADNOŚĆ|Wartość dziesiętna|Dokładność dla typu danych Liczba; binarny precyzja dla typu danych typu FLOAT, wartość null dla wszystkich innych typów danych.|  
|SKALI|Wartość dziesiętna|Cyfr z prawej strony punktu dziesiętnego w kilku.|  
|DOPUSZCZAJĄCE WARTOŚCI ZEROWE|String|Określa, czy kolumna zezwala na wartości null. Wartość jest N Jeśli istnieje ograniczenie NOT NULL w kolumnie lub kolumna jest częścią klucza podstawowego.|  
  
## <a name="indexes"></a>Indeksy  
  
|Element columnName|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|WŁAŚCICIEL|String|Właściciel indeksu|  
|INDEX_NAME|String|Nazwa indeksu.|  
|INDEX_TYPE|String|Typ indeksu (normalny, mapy BITOWEJ, oparte na funkcji normalny, oparte na funkcji mapy BITOWEJ lub domeny).|  
|TABLE_OWNER|String|Właściciel obiektu indeksowanego.|  
|TABLE_NAME|String|Nazwa obiektu indeksowanego.|  
|TABLE_TYPE|String|Typ obiektu indeksowanego (na przykład tabeli, KLASTRA).|  
|UNIKATOWOŚĆ|String|Określa, czy indeks jest unikatowy lub NONUNIQUE.|  
|KOMPRESJA|String|Określa, czy indeks jest włączone lub wyłączone.|  
|PREFIX_LENGTH|Wartość dziesiętna|Liczba kolumn w prefiks klucza kompresji.|  
|TABLESPACE_NAME|String|Nazwa obszaru tabel zawierających indeks.|  
|INI_TRANS|Wartość dziesiętna|Początkowa liczba transakcji.|  
|MAX_TRANS|Wartość dziesiętna|Maksymalna liczba transakcji.|  
|INITIAL_EXTENT|Wartość dziesiętna|Rozmiar początkowy zakresu.|  
|NEXT_EXTENT|Wartość dziesiętna|Rozmiar dodatkowej zakresów.|  
|MIN_EXTENTS|Wartość dziesiętna|Minimalna liczba zakresów dozwolone w segmencie.|  
|MAX_EXTENTS|Wartość dziesiętna|Maksymalna liczba zakresów dozwolone w segmencie.|  
|PCT_INCREASE|Wartość dziesiętna|Procentowy wzrost rozmiar zakresu.|  
|PCT_THRESHOLD|Wartość dziesiętna|Procentowy próg bloku miejsca na wpis indeksu.|  
|INCLUDE_COLUMN|Wartość dziesiętna|Identyfikator kolumny ostatniej kolumny mają zostać uwzględnione w indeksowanej tabeli indeksu klucza podstawowego (z systemem innym niż przepełnienie). W tej kolumnie jest mapowany na kolumnie COLUMN_ID * _TAB_COLUMNS danych słownika widoków.|  
|LIST ZWOLNIEŃ|Wartość dziesiętna|Liczba bloków procesu przydzielone do tego segmentu.|  
|FREELIST_GROUPS|Wartość dziesiętna|Liczba grup elementu freelist przydzielone do tego segmentu.|  
|PCT_FREE|Wartość dziesiętna|Minimalny procent wolnego miejsca w bloku.|  
|REJESTROWANIE|String|Informacje o rejestrowaniu.|  
|BLEVEL|Wartość dziesiętna|B *-drzewa poziom: głębokość indeksu z bloku jej głównego jego bloków typu liść. Głębokość 0 wskazuje, że głównego bloku oraz blok liścia są takie same.|  
|LEAF_BLOCKS|Wartość dziesiętna|Liczba bloków liścia w indeksie|  
|DISTINCT_KEYS|Wartość dziesiętna|Liczba unikatowych wartości indeksowanego. Dla indeksów, które wymuszają ograniczenia UNIQUE i PRIMARY KEY ta wartość jest taka sama jak liczba wierszy w tabeli (USER_TABLES. NUM_ROWS).|  
|AVG_LEAF_BLOCKS_PER_KEY|Wartość dziesiętna|Średnia liczba bloków typu liść, w których występuje każdy różne wartości w indeksie jest zaokrąglana do najbliższej liczby całkowitej. Indeksy, które wymuszają ograniczenia UNIQUE i PRIMARY KEY ta wartość jest zawsze 1.|  
|AVG_DATA_BLOCKS_PER_KEY|Wartość dziesiętna|Średnia liczba danych blokuje w tabeli, która jest wskazywana przez różne wartości w indeksie zaokrąglona do najbliższej liczby całkowitej. Ta statystyka jest to średnia liczba bloków danych, zawierające wiersze zawierające podanej wartości dla indeksowanego kolumn.|  
|CLUSTERING_FACTOR|Wartość dziesiętna|Wskazuje wielkość kolejność wierszy w tabeli na podstawie wartości indeksu.|  
|STAN|String|Określa, czy niepartycjonowany indeks jest PRAWIDŁOWY lub UNUSABLE.|  
|NUM_ROWS|Wartość dziesiętna|Liczba wierszy w indeksie.|  
|WARTOŚĆ PARAMETRU SAMPLE_SIZE|Wartość dziesiętna|Rozmiar próbki używane do analizowania indeksu.|  
|LAST_ANALYZED|DataGodzina|Data ostatniego przeanalizowane tego indeksu.|  
|STOPNIA|String|Liczba wątków dla każdego wystąpienia skanowania indeksu.|  
|WYSTĄPIENIA|String|Liczba wystąpień, w którym indeksów do przeskanowania.|  
|PODZIELONE NA PARTYCJE|String|Określa, czy ten indeks jest podzielona na partycje (tak &#124; NIE).|  
|TYMCZASOWE|String|Określa, czy indeks znajduje się w tabeli tymczasowej.|  
|WYGENEROWANY|String|Czy nazwę indeksu systemu wygenerowaniu (T &#124; N).|  
|POMOCNICZY|String|Określa, czy indeks jest obiektem dodatkowej tworzone przez metodę ODCIIndexCreate Oracle9i kasety danych (T &#124; N).|  
|BUFFER_POOL|String|Nazwa domyślnej puli bufora używanego do bloków indeksu.|  
|USER_STATS|String|Określa, czy wprowadzono statystyki bezpośrednio przez użytkownika.|  
|CZAS TRWANIA|String|Wskazuje czas trwania tabeli tymczasowej: 1) SYS$ sesji: wiersze zostaną zachowane w czasie trwania sesji, 2) SYS$ transakcji: wiersze zostaną usunięte po zatwierdzenie, Null 3) dla tabeli trwałych.|  
|PCT_DIRECT_ACCESS|Wartość dziesiętna|Na pomocniczy indeks w indeksowanej tabeli, wartość procentowa wiersze z nieprawidłowy wynik|  
|ITYP_OWNER|String|Dla indeksu domeny właściciela indextype.|  
|ITYP_NAME|String|Dla indeksu domeny, nazwę indextype.|  
|PARAMETRY|String|Dla indeksu domeny ciąg parametru.|  
|GLOBAL_STATS|String|Dla podzielonej na partycje indeksów wskazuje, czy statystyki zebrano analizując indeksu (tak) jako jedną całość, czy oszacowano z statystyk na partycje indeksu źródłowej i subpartitions (nie).|  
|DOMIDX_STATUS|String|Odzwierciedla stan indeksu domeny. Wartość NULL: określony indeks nie jest indeksem domeny. : Indeks jest PRAWIDŁOWY indeks prawidłową domenę. IDXTYP_INVLD: typ indeksu tego indeksu domeny jest nieprawidłowa.|  
|DOMIDX_OPSTATUS|String|Odzwierciedla stan operacji, która została wykonana w indeksie domeny: NULL: określony indeks nie jest indeksem domeny. NIEPRAWIDŁOWA: wykonanie tej operacji bez błędów. Nie powiodło się: operacja nie powiodła się z powodu błędu.|  
|FUNCIDX_STATUS|String|Wskazuje stan indeksu na podstawie funkcji: NULL: nie jest to funkcja oparta indeksu włączone: indeksu na podstawie funkcja jest włączona, wyłączona: indeksu na podstawie funkcja jest wyłączona.|  
|JOIN_INDEX|String|Wskazuje, czy to jest indeks sprzężenia.|  
  
## <a name="indexcolumns"></a>IndexColumns  
  
|Element columnName|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|INDEX_OWNER|String|Właściciel indeksu.|  
|INDEX_NAME|String|Nazwa indeksu.|  
|TABLE_OWNER|String|Właściciel tabeli lub klastra.|  
|TABLE_NAME|String|Nazwa tabeli lub klastra.|  
|COLUMN_NAME|String|Nazwa kolumny lub atrybut kolumny typu obiektu.|  
|COLUMN_POSITION|Wartość dziesiętna|Pozycja kolumny lub atrybutu w indeksie.|  
|COLUMN_LENGTH|Wartość dziesiętna|Indeksowane długość kolumny.|  
|CHAR_LENGTH|Wartość dziesiętna|Długość maksymalna punktów kodowych znaków dwuskładnikowych kolumny.|  
|ELEMENTEM PODRZĘDNYM ELEMENTU|String|Określa, czy kolumna jest posortowane w kolejności malejącej.|  
  
## <a name="procedures"></a>Procedury  
  
|Element columnName|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|WŁAŚCICIEL|String|Właściciel obiektu.|  
|OBJECT_NAME|String|Nazwa obiektu.|  
|SUBOBJECT_NAME|String|Nazwa podobiektów (na przykład partycji).|  
|IDENTYFIKATOR OBIEKTU|Wartość dziesiętna|Liczba obiekt słownika obiektu.|  
|DATA_OBJECT_ID|Wartość dziesiętna|Numer obiekt segmentu, która zawiera obiekt słownika.|  
|LAST_DDL_TIME|DataGodzina|Sygnatura czasowa ostatniej modyfikacji obiektu wynikające z polecenia języka DDL, (w tym przyznaje i wycofanie).|  
|ZNACZNIK CZASU|String|Sygnatura czasowa specyfikacji obiektu (dane znaków).|  
|STAN|String|Stan obiektu (prawidłowe, nieprawidłowe lub brak).|  
|TYMCZASOWE|String|Określa, czy obiekt jest tymczasowe (bieżącej sesji można znaleźć tylko te dane, które go umieścić w ten sam obiekt).|  
|WYGENEROWANY|String|Znajdował się wygenerowany przez system tego obiektu? (T &#124; N).|  
|POMOCNICZY|String|Czy to jest obiekt dodatkowej tworzone przez metodę ODCIIndexCreate Oracle9i filtra danych (T &#124; N).|  
|UTWORZONE|DataGodzina|Data utworzenia obiektu.|  
  
## <a name="sequences"></a>Sekwencje  
  
|Element columnName|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|SEQUENCE_OWNER|String|Nazwa właściciela sekwencji.|  
|SEQUENCE_NAME|String|Nazwa sekwencji.|  
|MIN_VALUE|Wartość dziesiętna|Minimalna wartość sekwencji.|  
|MAX_VALUE|Wartość dziesiętna|Maksymalna wartość sekwencji.|  
|INCREMENT_BY|Wartość dziesiętna|Wartość, według której jest zwiększany sekwencji.|  
|CYCLE_FLAG|String|Sekwencja Zawijaj po osiągnięciu limitu.|  
|ORDER_FLAG|String|Numery sekwencji są generowane w kolejności.|  
|CACHE_SIZE|Wartość dziesiętna|Liczba numerów sekwencji. do pamięci podręcznej.|  
|LAST_NUMBER|Wartość dziesiętna|Numer porządkowy ostatni zapisany na dysku. Jeśli sekwencję używa buforowania, numer zapisywane na dysku to numer ostatnio umieszczane w pamięci podręcznej sekwencji. Ta liczba jest może być większa niż ostatni numer sekwencji, który został użyty.|  
  
## <a name="synonyms"></a>Synonimy  
  
|Element columnName|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|WŁAŚCICIEL|String|Właściciel synonim.|  
|SYNONYM_NAME|String|Nazwa synonim.|  
|TABLE_OWNER|String|Właściciel obiektu odwołuje się synonim.|  
|TABLE_NAME|String|Nazwa obiektu odwołuje się synonim.|  
|DB_LINK|String|Nazwa odwołania, jeśli istnieje łącze bazy danych.|  
  
## <a name="tables"></a>Tabele  
  
|Element columnName|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|WŁAŚCICIEL|String|Właściciel tabeli.|  
|TABLE_NAME|String|Nazwa tabeli.|  
|TYP|String|Typ tabeli.|  
  
## <a name="users"></a>Użytkownicy  
  
|Element columnName|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|NAZWA|String|Nazwa użytkownika.|  
|ID|Wartość dziesiętna|Identyfikator użytkownika.|  
|CREATEDATE|DataGodzina|Data utworzenia użytkownika.|  
  
## <a name="views"></a>Widoki  
  
|Element columnName|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|WŁAŚCICIEL|String|Właściciel widoku.|  
|VIEW_NAME|String|Nazwa widoku.|  
|TEXT_LENGTH|Wartość dziesiętna|Długość tekstu widoku.|  
|TEKST|String|Wyświetlanie tekstu.|  
|TYPE_TEXT_LENGTH|Wartość dziesiętna|Długość klauzuli typu typizowanego widoku.|  
|TYP_TEKST|String|Klauzula typu typizowanego widoku.|  
|OID_TEXT_LENGTH|Wartość dziesiętna|Długość identyfikatora OID z klauzuli typu widoku.|  
|OID_TEXT|String|Z klauzulą OID typizowanego widoku.|  
|VIEW_TYPE_OWNER|String|Właściciel typu widoku, jeśli widok jest typizowanego widoku.|  
|VIEW_TYPE|String|Typ widoku, jeśli widok jest typizowanego widoku.|  
|SUPERVIEW_NAME|String|Nazwa superview.|  
  
## <a name="functions"></a>Funkcje  
  
|Element columnName|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|WŁAŚCICIEL|String|Właściciel obiektu.|  
|OBJECT_NAME|String|Nazwa obiektu.|  
|SUBOBJECT_NAME|String|Nazwa podobiektów (na przykład partycji).|  
|IDENTYFIKATOR OBIEKTU|Wartość dziesiętna|Liczba obiekt słownika obiektu.|  
|DATA_OBJECT_ID|Wartość dziesiętna|Numer obiekt segmentu, która zawiera obiekt słownika.|  
|OBJECT_TYPE|String|Typ obiektu.|  
|UTWORZONE|DataGodzina|Data utworzenia obiektu.|  
|LAST_DDL_TIME|DataGodzina|Sygnatura czasowa ostatniej modyfikacji obiektu wynikające z polecenia języka DDL, (w tym przyznaje i wycofanie).|  
|ZNACZNIK CZASU|String|Sygnatura czasowa specyfikacji obiektu (dane znakowe)|  
|STAN|String|Stan obiektu (prawidłowe, nieprawidłowe lub brak).|  
|TYMCZASOWE|String|Określa, czy obiekt jest tymczasowe (bieżącej sesji można znaleźć tylko te dane, które go umieścić w ten sam obiekt).|  
|WYGENEROWANY|String|Znajdował się wygenerowany przez system tego obiektu? (T &#124; N).|  
|POMOCNICZY|String|Czy to jest obiekt dodatkowej tworzone przez metodę ODCIIndexCreate Oracle9i filtra danych (T &#124; N).|  
  
## <a name="packages"></a>Pakiety  
  
|Element columnName|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|WŁAŚCICIEL|String|Właściciel obiektu.|  
|OBJECT_NAME|String|Nazwa obiektu.|  
|SUBOBJECT_NAME|String|Nazwa podobiektów (na przykład partycji).|  
|IDENTYFIKATOR OBIEKTU|Wartość dziesiętna|Liczba obiekt słownika obiektu.|  
|DATA_OBJECT_ID|Wartość dziesiętna|Numer obiekt segmentu, która zawiera obiekt słownika.|  
|LAST_DDL_TIME|DataGodzina|Sygnatura czasowa ostatniej modyfikacji obiektu wynikające z polecenia języka DDL, (w tym przyznaje i wycofanie).|  
|ZNACZNIK CZASU|String|Sygnatura czasowa specyfikacji obiektu (dane znaków).|  
|STAN|String|Stan obiektu (prawidłowe, nieprawidłowe lub brak).|  
|TYMCZASOWE|String|Określa, czy obiekt jest tymczasowe (bieżącej sesji można znaleźć tylko te dane, które go umieścić w ten sam obiekt).|  
|WYGENEROWANY|String|Znajdował się wygenerowany przez system tego obiektu? (T &#124; N).|  
|POMOCNICZY|String|Czy to jest obiekt dodatkowej tworzone przez metodę ODCIIndexCreate Oracle9i filtra danych (T &#124; N).|  
|UTWORZONE|DataGodzina|Data utworzenia obiektu.|  
  
## <a name="packagebodies"></a>PackageBodies  
  
|Element columnName|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|WŁAŚCICIEL|String|Właściciel obiektu.|  
|OBJECT_NAME|String|Nazwa obiektu.|  
|SUBOBJECT_NAME|String|Nazwa podobiektów (na przykład partycji).|  
|IDENTYFIKATOR OBIEKTU|Wartość dziesiętna|Liczba obiekt słownika obiektu.|  
|DATA_OBJECT_ID|Wartość dziesiętna|Numer obiekt segmentu, która zawiera obiekt słownika.|  
|LAST_DDL_TIME|DataGodzina|Sygnatura czasowa ostatniej modyfikacji obiektu wynikające z polecenia języka DDL, (w tym przyznaje i wycofanie).|  
|ZNACZNIK CZASU|String|Sygnatura czasowa specyfikacji obiektu (dane znaków).|  
|STAN|String|Stan obiektu (prawidłowe, nieprawidłowe lub brak).|  
|TYMCZASOWE|String|Określa, czy obiekt jest tymczasowe (bieżącej sesji można znaleźć tylko te dane, które go umieścić w ten sam obiekt).|  
|WYGENEROWANY|String|Znajdował się wygenerowany przez system tego obiektu? (T &#124; N).|  
|POMOCNICZY|String|Czy to jest obiekt dodatkowej tworzone przez metodę ODCIIndexCreate Oracle9i filtra danych (T &#124; N).|  
|UTWORZONE|DataGodzina|Data utworzenia obiektu.|  
  
## <a name="arguments"></a>Argumenty  
  
|Element columnName|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|WŁAŚCICIEL|String|Nazwa właściciela obiektu.|  
|NAZWA_PAKIETU|String|Nazwa pakietu.|  
|OBJECT_NAME|String|Nazwa procedury lub funkcji.|  
|ARGUMENT_NAME|String|Nazwa argumentu.|  
|STANOWISKO|Wartość dziesiętna|Pozycja listy argumentów lub wartość NULL dla wartości zwracanej funkcji.|  
|SEKWENCJA|Wartość dziesiętna|Argument sekwencji, w tym wszystkich poziomów zagnieżdżenia.|  
|DEFAULT_VALUE|String|Wartość domyślna argumentu.|  
|DEFAULT_LENGTH|Wartość dziesiętna|Długość wartości domyślnej dla argumentu.|  
|IN_OUT|String|Kierunek argumentu (IN, OUT lub we/wy).|  
|DATA_LENGTH|Wartość dziesiętna|Długość kolumny w bajtach.|  
|DATA_PRECISION|Wartość dziesiętna|Długość w cyfr dziesiętnych (NUMBER) i cyfr (FLOAT).|  
|DATA_SCALE|Wartość dziesiętna|Cyfr z prawej strony punktu dziesiętnego w kilku.|  
|DATA_TYPE|String|Typ danych argumentu.|  
  
## <a name="uniquekeys"></a>UniqueKeys  
  
|Element columnName|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|WŁAŚCICIEL|String|Właściciel definicji ograniczenia.|  
|CONSTRAINT_NAME|String|Nazwa definicji ograniczenia.|  
|TABLE_NAME|String|Nazwa skojarzona z tabeli (lub Widok) z definicji ograniczenia.|  
|SEARCH_CONDITION JEST|String|Tekst warunku wyszukiwania dla ograniczenia sprawdzania.|  
|R_OWNER|String|Właściciel tabeli określonej w ograniczeniu referencyjnym.|  
|R_CONSTRAINT_NAME|String|Nazwa definicji unikatowego ograniczenia dla tabeli.|  
|DELETE_RULE|String|Usuń regułę dla ograniczenia referencyjnego (CASCADE lub NO ACTION).|  
|STAN|String|Stan wymuszenia ograniczenia (włączone lub wyłączone).|  
|DEFERRABLE|String|Określa, czy ograniczenie jest deferrable.|  
|SPRAWDZANIA POPRAWNOŚCI|String|Określa, czy wszystkie dane przestrzega ograniczenia (WERYFIKOWANE lub NIEZWERYFIKOWANY).|  
|WYGENEROWANY|String|Określa, czy nazwy ograniczenia użytkownika lub jest wygenerowany przez system.|  
|ZŁY|String|Wartość Tak oznacza, że to ograniczenie określa wieku w sposób niejednoznaczny. Aby uniknąć błędów wynikających z tę niejednoznaczność, należy zmodyfikować ograniczenie funkcja TO_DATE z rokiem czterocyfrowym.|  
|POLEGAĆ|String|Określa, czy włączone jest wymuszane lub niewymuszone.|  
|LAST_CHANGE|DataGodzina|Po ograniczenie ostatniego włączone lub wyłączone|  
|INDEX_OWNER|String|Nazwa użytkownika, którego indeks|  
|INDEX_NAME|String|Nazwa indeksu|  
  
## <a name="primarykeys"></a>PrimaryKeys  
  
|Element columnName|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|WŁAŚCICIEL|String|Właściciel definicji ograniczenia.|  
|CONSTRAINT_NAME|String|Nazwa definicji ograniczenia.|  
|TABLE_NAME|String|Nazwa skojarzona z tabeli (lub Widok) z definicji ograniczenia.|  
|SEARCH_CONDITION JEST|String|Tekst warunku wyszukiwania dla ograniczenia sprawdzania.|  
|R_OWNER|String|Właściciel tabeli określonej w ograniczeniu referencyjnym.|  
|R_CONSTRAINT_NAME|String|Nazwa definicji unikatowego ograniczenia dla tabeli.|  
|DELETE_RULE|String|Usuń regułę dla ograniczenia referencyjnego (CASCADE lub NO ACTION).|  
|STAN|String|Stan wymuszenia ograniczenia (włączone lub wyłączone).|  
|DEFERRABLE|String|Określa, czy ograniczenie jest deferrable.|  
|SPRAWDZANIA POPRAWNOŚCI|String|Określa, czy wszystkie dane przestrzega ograniczenia (WERYFIKOWANE lub NIEZWERYFIKOWANY).|  
|WYGENEROWANY|String|Określa, czy nazwy ograniczenia użytkownika lub jest wygenerowany przez system.|  
|ZŁY|String|Wartość Tak oznacza, że to ograniczenie określa wieku w sposób niejednoznaczny. Aby uniknąć błędów wynikających z tę niejednoznaczność, należy zmodyfikować ograniczenie funkcja TO_DATE z rokiem czterocyfrowym.|  
|POLEGAĆ|String|Określa, czy włączone jest wymuszane lub niewymuszone.|  
|LAST_CHANGE|DataGodzina|Podczas ostatniego ograniczenie włączone lub wyłączone.|  
|INDEX_OWNER|String|Nazwa użytkownika, którego indeks.|  
|INDEX_NAME|String|Nazwa indeksu.|  
  
## <a name="foreignkeys"></a>ForeignKeys  
  
|Element columnName|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|PRIMARY_KEY_CONSTRAINT_NAME|String|Nazwa definicji ograniczenia.|  
|PRIMARY_KEY_OWNER|String|Właściciel definicji ograniczenia.|  
|PRIMARY_KEY_TABLE_NAME|String|Nazwa skojarzona z tabeli (lub Widok) z definicji ograniczenia|  
|FOREIGN_KEY_OWNER|String|Właściciel definicji ograniczenia.|  
|FOREIGN_KEY_CONSTRIANT_NAME|String|Nazwa definicji ograniczenia.|  
|FOREIGN_KEY_TABLE_NAME|String|Nazwa skojarzona z tabeli (lub Widok) z definicji ograniczenia.|  
|SEARCH_CONDITION JEST|String|Tekst warunku wyszukiwania dla ograniczenia check|  
|R_OWNER|String|Właściciel tabeli określonej w ograniczeniu referencyjnym.|  
|R_CONSTRAINT_NAME|String|Nazwa definicji unikatowego ograniczenia dla tabeli.|  
|DELETE_RULE|String|Usuń regułę dla ograniczenia referencyjnego (CASCADE lub NO ACTION).|  
|STAN|String|Stan wymuszenia ograniczenia (włączone lub wyłączone).|  
|SPRAWDZANIA POPRAWNOŚCI|String|Określa, czy wszystkie dane przestrzega ograniczenia (WERYFIKOWANE lub NIEZWERYFIKOWANY).|  
|WYGENEROWANY|String|Określa, czy nazwy ograniczenia użytkownika lub jest wygenerowany przez system.|  
|POLEGAĆ|String|Określa, czy włączone jest wymuszane lub niewymuszone.|  
|LAST_CHANGE|DataGodzina|Podczas ostatniego ograniczenie włączone lub wyłączone.|  
|INDEX_OWNER|String|Nazwa użytkownika, którego indeks.|  
|INDEX_NAME|String|Nazwa indeksu.|  
  
## <a name="foreignkeycolumns"></a>Zawierającej kolumny kluczy obcych  
  
|Element columnName|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|WŁAŚCICIEL|String|Właściciel definicji ograniczenia.|  
|CONSTRAINT_NAME|String|Nazwa definicji ograniczenia.|  
|TABLE_NAME|String|Nazwa tabeli z definicji ograniczenia.|  
|COLUMN_NAME|String|Nazwa kolumny lub atrybut kolumny typu obiektu określonego w definicji ograniczenia.|  
|STANOWISKO|Wartość dziesiętna|Początkowe położenie atrybut lub kolumny w definicji obiektu.|  
  
## <a name="procedureparameters"></a>ProcedureParameters  
  
|Element columnName|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|WŁAŚCICIEL|String|Właściciel obiektu.|  
|OBJECT_NAME|String|Nazwa procedury lub funkcji.|  
|NAZWA_PAKIETU|String|Nazwa procedury lub funkcji.|  
|IDENTYFIKATOR OBIEKTU|Wartość dziesiętna|Liczba obiektów obiektu.|  
|PRZECIĄŻENIA|String|Przeciążenia Unikatowy identyfikator.|  
|ARGUMENT_NAME|String|Nazwa argumentu.|  
|STANOWISKO|Wartość dziesiętna|Pozycja na liście argument lub wartość null dla wartości zwracanej funkcji.|  
|SEKWENCJA|Wartość dziesiętna|Argument sekwencji, w tym wszystkich poziomów zagnieżdżenia.|  
|DATA_LEVEL|Wartość dziesiętna|Zagnieżdżania głębokość argumentu dla typów złożonych.|  
|DATA_TYPE|String|Typ danych argumentu.|  
|DEFAULT_VALUE|String|Wartość domyślna argumentu.|  
|DEFAULT_LENGTH|Wartość dziesiętna|Długość wartości domyślne dla argumentu.|  
|IN_OUT|String|Kierunek argumentu (IN, OUT lub we/wy).|  
|DATA_LENGTH|Wartość dziesiętna|Długość kolumny (w bajtach).|  
|DATA_PRECISION|Wartość dziesiętna|Długość w cyfr dziesiętnych (NUMBER) i cyfr (FLOAT).|  
|DATA_SCALE|Wartość dziesiętna|Cyfr z prawej strony punktu dziesiętnego w kilku.|  
|PODSTAWA|Wartość dziesiętna|Argument podstawa dla numeru.|  
|CHARACTER_SET_NAME|String|Nazwa argumentu zestaw znaków.|  
|TYPE_OWNER|String|Właściciel typu argumentu.|  
|TYPE_NAME|String|Nazwa typu argumentu. Jeśli typ jest typem lokalnego pakietu (to znaczy jest zadeklarowany jako w specyfikacji pakietu), a następnie w tej kolumnie jest wyświetlana nazwa pakietu.|  
|TYPE_SUBNAME|String|Zastosowanie tylko w przypadku lokalnego typów pakietów. Wyświetla nazwę typu zadeklarowany w pakiecie, który został zidentyfikowany w kolumnie TYPE_NAME.|  
|TYPE_LINK|String|Zastosowanie tylko w przypadku typów pakietów lokalnego po pakietu oznaczone w kolumnie TYPE_NAME zdalnych pakietów. W tej kolumnie Wyświetla użyta w odwołaniu do pakietów zdalnego link bazy danych.|  
|PLS_TYPE|String|Dla argumentów, nazwa typu PL/SQL argumentu. W przeciwnym razie wartość null.|  
|CHAR_LENGTH|Wartość dziesiętna|Limit znaków dla danych typu ciąg.|  
|CHAR_USED|String|Wskazuje, czy limit bajtów (B) lub limitu char (C) jest oficjalnego ciągu.|  
  
## <a name="see-also"></a>Zobacz też  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
