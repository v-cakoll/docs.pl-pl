---
title: Kolekcje schematów Oracle
ms.date: 03/30/2017
ms.assetid: 89a75de8-dee8-45e2-a97f-254d7e62e7e1
ms.openlocfilehash: 342c4cbe994eb983713be0f258e3a029df6739f8
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43886087"
---
# <a name="oracle-schema-collections"></a>Kolekcje schematów Oracle
Microsoft .NET Framework Data Provider na oprogramowanie Oracle, obsługuje następujące kolekcje z określonego schematu, oprócz Typowe kolekcje schematów:  
  
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
  
-   ForeignKeyColumns  
  
-   ProcedureParameters  
  
## <a name="columns"></a>Kolumny  
  
|NazwaKolumny|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|WŁAŚCICIEL|String|Właściciel tabeli, widoku lub klastra.|  
|TABLE_NAME|String|Tabela, widok lub nazwy klastra.|  
|COLUMN_NAME|String|Nazwa kolumny.|  
|ID|Wartość dziesiętna|Przeprowadzaj sekwencjonowanie numer kolumny, podczas tworzenia.|  
|TYP DANYCH|String|Typ danych kolumny.|  
|DŁUGOŚĆ|Wartość dziesiętna|Długość kolumny w bajtach.|  
|PRECYZJA|Wartość dziesiętna|Precyzja dziesiętna dla liczb typu danych; binarny dokładność dla typu danych ZMIENNOPRZECINKOWYCH, wartość null w przypadku innych typów danych.|  
|SKALA|Wartość dziesiętna|Cyfr z prawej strony punktu dziesiętnego w kilku.|  
|DOPUSZCZA WARTOŚCI NULL|String|Określa, czy w kolumnie dozwolone wartości null. Wartość N czy istnieje ograniczenie NOT NULL w kolumnie czy kolumna jest częścią klucza podstawowego.|  
  
## <a name="indexes"></a>Indeksy  
  
|NazwaKolumny|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|WŁAŚCICIEL|String|Właściciel indeksu|  
|INDEX_NAME|String|Nazwa indeksu.|  
|INDEX_TYPE|String|Typ indeksu (normalny, mapy BITOWEJ, oparte na funkcji normalny, oparte na funkcji mapy BITOWEJ lub domeny).|  
|TABLE_OWNER|String|Właściciel obiektu indeksowanego.|  
|TABLE_NAME|String|Nazwa obiektu indeksowanego.|  
|TABLE_TYPE|String|Typ obiektu indeksowane (na przykład tabela, KLASTRA).|  
|UNIKATOWOŚĆ|String|Czy indeks jest klucza UNIKATOWEGO lub NONUNIQUE.|  
|KOMPRESJA|String|Czy indeks jest włączone lub wyłączone.|  
|PREFIX_LENGTH|Wartość dziesiętna|Liczba kolumn w prefiksie klucz kompresji.|  
|TABLESPACE_NAME|String|Nazwa obszaru tabel zawierających indeks.|  
|INI_TRANS|Wartość dziesiętna|Początkowa liczba transakcji.|  
|MAX_TRANS|Wartość dziesiętna|Maksymalna liczba transakcji.|  
|INITIAL_EXTENT|Wartość dziesiętna|Rozmiar początkowy zakresu.|  
|NEXT_EXTENT|Wartość dziesiętna|Rozmiar dodatkowej zakresów.|  
|MIN_EXTENTS|Wartość dziesiętna|Minimalna liczba zakresów dozwolone w segmencie.|  
|MAX_EXTENTS|Wartość dziesiętna|Maksymalna liczba zakresów dozwolone w segmencie.|  
|PCT_INCREASE|Wartość dziesiętna|Wzrost procentowy rozmiar zakresu.|  
|PCT_THRESHOLD|Wartość dziesiętna|Procentowy próg przestrzeni blokowych może istnieć wpis indeksu.|  
|INCLUDE_COLUMN|Wartość dziesiętna|Kolumny o identyfikatorze ostatniej kolumny do uwzględnienia w indeksowanej tabeli klucza podstawowego (inne niż przepełnienie) indeksu. W tej kolumnie mapuje do kolumny COLUMN_ID * widoki słownika danych _TAB_COLUMNS.|  
|LIST ZWOLNIEŃ|Wartość dziesiętna|Liczba bloków procesu przydzielony do tego segmentu.|  
|FREELIST_GROUPS|Wartość dziesiętna|Liczba grup FreeList — przydzielony do tego segmentu.|  
|PCT_FREE|Wartość dziesiętna|Minimalny procent wolnego miejsca, w bloku.|  
|REJESTROWANIE|String|Rejestrowanie informacji.|  
|BLEVEL|Wartość dziesiętna|B * — poziom drzewa: głębokość indeksu z jego bloku głównego do jego bloków typu liść. Głębokość 0 oznacza, że głównego bloku oraz blok typu liść są takie same.|  
|LEAF_BLOCKS|Wartość dziesiętna|Liczba bloków liścia w indeksie|  
|DISTINCT_KEYS|Wartość dziesiętna|Liczba unikatowych wartości indeksowanego. Dla indeksów, które wymuszają ograniczenia UNIQUE i PRIMARY KEY ta wartość jest taka sama jak liczba wierszy w tabeli (USER_TABLES. NUM_ROWS).|  
|AVG_LEAF_BLOCKS_PER_KEY|Wartość dziesiętna|Średnia liczba bloków typu liść, w których występuje każdej unikatowej wartości w indeksie jest zaokrąglana do najbliższej liczby całkowitej. Indeksy, które wymuszają ograniczenia UNIQUE i PRIMARY KEY ta wartość ma zawsze numer 1.|  
|AVG_DATA_BLOCKS_PER_KEY|Wartość dziesiętna|Średnia liczba danych bloków w tabeli, który jest wskazywany przez różne wartości w indeks zaokrąglana do najbliższej liczby całkowitej. Ta statystyka jest to średnia liczba bloków danych, zawierające wiersze, które zawierają podanej wartości w przypadku indeksowanych kolumn.|  
|CLUSTERING_FACTOR|Wartość dziesiętna|Wskazuje ilość kolejności wierszy w tabeli na podstawie wartości indeksu.|  
|STAN|String|Czy niepartycjonowany indeks jest PRAWIDŁOWY lub UNUSABLE.|  
|NUM_ROWS|Wartość dziesiętna|Liczba wierszy w indeksie.|  
|SAMPLE_SIZE|Wartość dziesiętna|Rozmiar próbki używane do analizowania indeksu.|  
|LAST_ANALYZED|DataGodzina|Data ostatnio przeanalizowany tego indeksu.|  
|STOPIEŃ|String|Liczba wątków dla każdego wystąpienia skanowania indeksu.|  
|WYSTĄPIENIA|String|Liczba wystąpień, w którym indeksów do przeskanowania.|  
|PODZIELONA NA PARTYCJE|String|Czy ten indeks jest podzielona na partycje (tak &#124; nie).|  
|TYMCZASOWE|String|Czy indeks znajduje się w tabeli tymczasowej.|  
|WYGENEROWANY|String|Czy nazwa indeksu jest generowane przez system (Y&#124;N).|  
|POMOCNICZY|String|Czy indeks jest obiekt pomocniczy tworzone przez metodę ODCIIndexCreate filtra danych Oracle9i (Y&#124;N).|  
|BUFFER_POOL|String|Nazwa puli buforów domyślna ma być używany dla bloków indeksu.|  
|USER_STATS|String|Czy statystyki wprowadzono bezpośrednio przez użytkownika.|  
|CZAS TRWANIA|String|Wskazuje czas trwania tabeli tymczasowej: 1) sesji$ SYS: wiersze są zachowywane w czasie trwania sesji, transakcji$ 2) SYS: wiersze zostaną usunięte po zatwierdzeniu, wartość Null (3) w przypadku trwałej tabeli.|  
|PCT_DIRECT_ACCESS|Wartość dziesiętna|Na pomocniczy indeks w indeksowanej tabeli, wartość procentowa wiersze z PRAWIDŁOWĄ odgadnięcia|  
|ITYP_OWNER|String|Dla indeksu domeny właściciela indextype.|  
|ITYP_NAME|String|Dla indeksu domeny nazwa indextype.|  
|PARAMETRY|String|Dla indeksu domeny ciąg parametru.|  
|GLOBAL_STATS|String|Dla indeksów podzielonym na partycje wskazuje, czy statystyki zostały zebrane, analizując indeksu jako całość (tak), czy zostały szacowane z statystyki dotyczące podstawowych partycji indeksu i subpartitions (nie).|  
|DOMIDX_STATUS|String|Odzwierciedla stan indeksu domeny. Wartość NULL: określony indeks nie jest indeksem domeny. : Indeks jest PRAWIDŁOWY indeks prawidłową domenę. IDXTYP_INVLD: typ indeksu tego indeksu domeny jest nieprawidłowy.|  
|DOMIDX_OPSTATUS|String|Odzwierciedla stan operacji, która została wykonana w indeksie domeny: NULL: określony indeks nie jest indeksem domeny. NIEPRAWIDŁOWA: wykonanie operacji bez błędów. Nie powiodło się: operacja nie powiodła się z powodu błędu.|  
|FUNCIDX_STATUS|String|Wskazuje stan indeksu na podstawie funkcji: NULL: to nie jest to funkcja oparta na indeksowanie włączone: indeksu na podstawie funkcja jest włączona, wyłączona: indeksu na podstawie funkcji jest wyłączone.|  
|JOIN_INDEX|String|Wskazuje, czy to indeks sprzężenia.|  
  
## <a name="indexcolumns"></a>IndexColumns  
  
|NazwaKolumny|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|INDEX_OWNER|String|Właściciel indeksu.|  
|INDEX_NAME|String|Nazwa indeksu.|  
|TABLE_OWNER|String|Właściciel tabeli lub klastra.|  
|TABLE_NAME|String|Nazwa tabeli lub klastra.|  
|COLUMN_NAME|String|Nazwa kolumny lub atrybut kolumna typu obiektu.|  
|COLUMN_POSITION|Wartość dziesiętna|Pozycja kolumny lub atrybut w indeksie.|  
|COLUMN_LENGTH|Wartość dziesiętna|Indeksowane długość kolumny.|  
|CHAR_LENGTH|Wartość dziesiętna|Punktu kodu maksymalną długość kolumny.|  
|JEST ELEMENTEM PODRZĘDNYM ELEMENTU|String|Czy kolumna jest sortowany w kolejności malejącej.|  
  
## <a name="procedures"></a>Procedury  
  
|NazwaKolumny|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|WŁAŚCICIEL|String|Właściciel obiektu.|  
|OBJECT_NAME|String|Nazwa obiektu.|  
|SUBOBJECT_NAME|String|Nazwa obiektu podrzędnego (na przykład partycji).|  
|OBJECT_ID|Wartość dziesiętna|Liczba obiekt słownika obiektu.|  
|DATA_OBJECT_ID|Wartość dziesiętna|Numer obiektu segment, który zawiera obiekt słownika.|  
|LAST_DDL_TIME|DataGodzina|Sygnatura czasowa ostatniej modyfikacji obiektu wynikające z polecenia języka DDL, (w tym przyznaje i wycofanie).|  
|ZNACZNIK CZASU:|String|Sygnatura czasowa specyfikacji obiektu (znak dane).|  
|STAN|String|Stan obiektu (prawidłowe, nieprawidłowe lub n/d).|  
|TYMCZASOWE|String|Czy obiekt jest tymczasowy (bieżącej sesji można wyświetlić tylko te dane, które go umieścić w ten sam obiekt).|  
|WYGENEROWANY|String|Była nazwa wygenerowanej przez system ten obiekt? (Y &AMP;#124; N).|  
|POMOCNICZY|String|Czy jest to obiekt pomocniczy tworzone przez metodę ODCIIndexCreate filtra danych Oracle9i (Y &#124; N).|  
|UTWORZONE|DataGodzina|Data utworzenia obiektu.|  
  
## <a name="sequences"></a>Sekwencje  
  
|NazwaKolumny|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|SEQUENCE_OWNER|String|Nazwa właściciela sekwencji.|  
|SEQUENCE_NAME|String|Nazwa sekwencji.|  
|MIN_VALUE|Wartość dziesiętna|Minimalna wartość w sekwencji.|  
|MAX_VALUE|Wartość dziesiętna|Maksymalna wartość w sekwencji.|  
|INCREMENT_BY|Wartość dziesiętna|Wartość, według której jest zwiększany sekwencji.|  
|CYCLE_FLAG|String|Przeprowadzaj sekwencjonowanie Zawijaj po osiągnięciu limitu.|  
|ORDER_FLAG|String|Czy numerów sekwencji są generowane w kolejności.|  
|CACHE_SIZE|Wartość dziesiętna|Liczba numerów sekwencji do pamięci podręcznej.|  
|LAST_NUMBER|Wartość dziesiętna|Numer ostatniej sekwencyjny zapisane na dysku. Jeśli sekwencja numer jest używany buforowania, zapisywane dysku to numer ostatnio umieszczane w pamięci podręcznej sekwencji. Ta liczba jest może być większa niż ostatni numer sekwencji, który został użyty.|  
  
## <a name="synonyms"></a>Synonimy  
  
|NazwaKolumny|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|WŁAŚCICIEL|String|Właściciel synonim.|  
|SYNONYM_NAME|String|Nazwa synonim.|  
|TABLE_OWNER|String|Właściciel obiektu odwołuje się synonim.|  
|TABLE_NAME|String|Nazwa obiektu odwołuje się synonim.|  
|DB_LINK|String|Nazwa odwołania, jeśli istnieje łącze bazy danych.|  
  
## <a name="tables"></a>Tabele  
  
|NazwaKolumny|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|WŁAŚCICIEL|String|Właściciel tabeli.|  
|TABLE_NAME|String|Nazwa tabeli.|  
|TYP|String|Typ tabeli.|  
  
## <a name="users"></a>Użytkownicy  
  
|NazwaKolumny|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|NAZWA|String|Nazwa użytkownika.|  
|ID|Wartość dziesiętna|Numer identyfikacyjny użytkownika.|  
|CREATEDATE|DataGodzina|Data utworzenia użytkownika.|  
  
## <a name="views"></a>Widoki  
  
|NazwaKolumny|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|WŁAŚCICIEL|String|Właściciel tego widoku.|  
|VIEW_NAME|String|Nazwa widoku.|  
|TEXT_LENGTH|Wartość dziesiętna|Długość tekstu widoku.|  
|TEKST|String|Wyświetl tekst.|  
|TYPE_TEXT_LENGTH|Wartość dziesiętna|Długość klauzuli typu typizowanego widoku.|  
|TYP_TEKST|String|Typ klauzuli typizowanego widoku.|  
|OID_TEXT_LENGTH|Wartość dziesiętna|Długość klauzuli za pomocą identyfikatora OID typizowanego widoku.|  
|OID_TEXT|String|Za pomocą klauzuli identyfikatora OID typizowanego widoku.|  
|VIEW_TYPE_OWNER|String|Właściciel od typu widoku, jeśli widok jest typizowanego widoku.|  
|VIEW_TYPE|String|Typ widoku, jeśli widok jest typizowanego widoku.|  
|SUPERVIEW_NAME|String|Nazwa superview.|  
  
## <a name="functions"></a>Funkcje  
  
|NazwaKolumny|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|WŁAŚCICIEL|String|Właściciel obiektu.|  
|OBJECT_NAME|String|Nazwa obiektu.|  
|SUBOBJECT_NAME|String|Nazwa obiektu podrzędnego (na przykład partycji).|  
|OBJECT_ID|Wartość dziesiętna|Liczba obiekt słownika obiektu.|  
|DATA_OBJECT_ID|Wartość dziesiętna|Numer obiektu segment, który zawiera obiekt słownika.|  
|OBJECT_TYPE|String|Typ obiektu.|  
|UTWORZONE|DataGodzina|Data utworzenia obiektu.|  
|LAST_DDL_TIME|DataGodzina|Sygnatura czasowa ostatniej modyfikacji obiektu wynikające z polecenia języka DDL, (w tym przyznaje i wycofanie).|  
|ZNACZNIK CZASU:|String|Sygnatura czasowa specyfikacji obiektu (znak dane)|  
|STAN|String|Stan obiektu (prawidłowe, nieprawidłowe lub n/d).|  
|TYMCZASOWE|String|Czy obiekt jest tymczasowy (bieżącej sesji można wyświetlić tylko te dane, które go umieścić w ten sam obiekt).|  
|WYGENEROWANY|String|Była nazwa wygenerowanej przez system ten obiekt? (Y &AMP;#124; N).|  
|POMOCNICZY|String|Czy jest to obiekt pomocniczy tworzone przez metodę ODCIIndexCreate filtra danych Oracle9i (Y &#124; N).|  
  
## <a name="packages"></a>Pakiety  
  
|NazwaKolumny|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|WŁAŚCICIEL|String|Właściciel obiektu.|  
|OBJECT_NAME|String|Nazwa obiektu.|  
|SUBOBJECT_NAME|String|Nazwa obiektu podrzędnego (na przykład partycji).|  
|OBJECT_ID|Wartość dziesiętna|Liczba obiekt słownika obiektu.|  
|DATA_OBJECT_ID|Wartość dziesiętna|Numer obiektu segment, który zawiera obiekt słownika.|  
|LAST_DDL_TIME|DataGodzina|Sygnatura czasowa ostatniej modyfikacji obiektu wynikające z polecenia języka DDL, (w tym przyznaje i wycofanie).|  
|ZNACZNIK CZASU:|String|Sygnatura czasowa specyfikacji obiektu (znak dane).|  
|STAN|String|Stan obiektu (prawidłowe, nieprawidłowe lub n/d).|  
|TYMCZASOWE|String|Czy obiekt jest tymczasowy (bieżącej sesji można wyświetlić tylko te dane, które go umieścić w ten sam obiekt).|  
|WYGENEROWANY|String|Była nazwa wygenerowanej przez system ten obiekt? (Y &AMP;#124; N).|  
|POMOCNICZY|String|Czy jest to obiekt pomocniczy tworzone przez metodę ODCIIndexCreate filtra danych Oracle9i (Y &#124; N).|  
|UTWORZONE|DataGodzina|Data utworzenia obiektu.|  
  
## <a name="packagebodies"></a>PackageBodies  
  
|NazwaKolumny|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|WŁAŚCICIEL|String|Właściciel obiektu.|  
|OBJECT_NAME|String|Nazwa obiektu.|  
|SUBOBJECT_NAME|String|Nazwa obiektu podrzędnego (na przykład partycji).|  
|OBJECT_ID|Wartość dziesiętna|Liczba obiekt słownika obiektu.|  
|DATA_OBJECT_ID|Wartość dziesiętna|Numer obiektu segment, który zawiera obiekt słownika.|  
|LAST_DDL_TIME|DataGodzina|Sygnatura czasowa ostatniej modyfikacji obiektu wynikające z polecenia języka DDL, (w tym przyznaje i wycofanie).|  
|ZNACZNIK CZASU:|String|Sygnatura czasowa specyfikacji obiektu (znak dane).|  
|STAN|String|Stan obiektu (prawidłowe, nieprawidłowe lub n/d).|  
|TYMCZASOWE|String|Czy obiekt jest tymczasowy (bieżącej sesji można wyświetlić tylko te dane, które go umieścić w ten sam obiekt).|  
|WYGENEROWANY|String|Była nazwa wygenerowanej przez system ten obiekt? (Y &AMP;#124; N).|  
|POMOCNICZY|String|Czy jest to obiekt pomocniczy tworzone przez metodę ODCIIndexCreate filtra danych Oracle9i (Y &#124; N).|  
|UTWORZONE|DataGodzina|Data utworzenia obiektu.|  
  
## <a name="arguments"></a>Argumenty  
  
|NazwaKolumny|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|WŁAŚCICIEL|String|Nazwa właściciela obiektu.|  
|PACKAGE_NAME|String|Nazwa pakietu.|  
|OBJECT_NAME|String|Nazwa procedury lub funkcji.|  
|ARGUMENT_NAME|String|Nazwa argumentu.|  
|STANOWISKO|Wartość dziesiętna|Pozycja na liście argumentów lub wartość NULL dla wartości zwracanej funkcji.|  
|SEKWENCJA|Wartość dziesiętna|Sekwencja argumentów, włącznie ze wszystkimi poziomami zagnieżdżenia.|  
|DEFAULT_VALUE|String|Wartość domyślna dla argumentu.|  
|DEFAULT_LENGTH|Wartość dziesiętna|Długość domyślnej wartości dla argumentu.|  
|IN_OUT|String|Kierunek argumentu (IN, OUT lub we/wy).|  
|DATA_LENGTH|Wartość dziesiętna|Długość kolumny w bajtach.|  
|DATA_PRECISION|Wartość dziesiętna|Długość w cyfry dziesiętne (liczba) lub cyfr (FLOAT).|  
|DATA_SCALE|Wartość dziesiętna|Cyfr z prawej strony punktu dziesiętnego w kilku.|  
|DATA_TYPE|String|Typ danych argumentu.|  
  
## <a name="uniquekeys"></a>UniqueKeys  
  
|NazwaKolumny|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|WŁAŚCICIEL|String|Właściciel definicji ograniczenia.|  
|CONSTRAINT_NAME|String|Nazwa definicji ograniczenia.|  
|TABLE_NAME|String|Nazwa skojarzona z tabeli (lub Widok) przy użyciu definicji ograniczenia.|  
|SEARCH_CONDITION JEST|String|Tekst warunków wyszukiwania dla ograniczenia check.|  
|R_OWNER|String|Właściciel tabeli określonej w ograniczeniu referencyjnym.|  
|R_CONSTRAINT_NAME|String|Nazwa definicji unikatowego ograniczenia dla tabeli.|  
|DELETE_RULE|String|Usuń regułę dla ograniczenia referencyjnego (CASCADE lub NO ACTION).|  
|STAN|String|Stan wymuszania ograniczenia (włączone lub wyłączone).|  
|DEFERRABLE|String|Czy ograniczenie jest deferrable.|  
|ZWERYFIKOWANE|String|Czy wszystkie dane przestrzegają ograniczenie (WERYFIKOWANE lub NIEZWERYFIKOWANY).|  
|WYGENEROWANY|String|Czy nazwa ograniczenia jest użytkownika lub wygenerowanej przez system.|  
|BAD|String|Wartość Tak oznacza, że to ograniczenie określa wieku w sposób niejednoznaczny. Aby uniknąć błędów wynikających z tę niejednoznaczność, należy zmodyfikować ograniczenia przy użyciu funkcji TO_DATE z rokiem czterocyfrowym.|  
|POLEGAĆ|String|Włączone ograniczenie jest wymuszane czy niewymuszone.|  
|LAST_CHANGE|DataGodzina|Gdy ograniczenia został ostatnio włączone lub wyłączone|  
|INDEX_OWNER|String|Nazwa użytkownika będącego właścicielem indeksu|  
|INDEX_NAME|String|Nazwa indeksu|  
  
## <a name="primarykeys"></a>PrimaryKeys  
  
|NazwaKolumny|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|WŁAŚCICIEL|String|Właściciel definicji ograniczenia.|  
|CONSTRAINT_NAME|String|Nazwa definicji ograniczenia.|  
|TABLE_NAME|String|Nazwa skojarzona z tabeli (lub Widok) przy użyciu definicji ograniczenia.|  
|SEARCH_CONDITION JEST|String|Tekst warunków wyszukiwania dla ograniczenia check.|  
|R_OWNER|String|Właściciel tabeli określonej w ograniczeniu referencyjnym.|  
|R_CONSTRAINT_NAME|String|Nazwa definicji unikatowego ograniczenia dla tabeli.|  
|DELETE_RULE|String|Usuń regułę dla ograniczenia referencyjnego (CASCADE lub NO ACTION).|  
|STAN|String|Stan wymuszania ograniczenia (włączone lub wyłączone).|  
|DEFERRABLE|String|Czy ograniczenie jest deferrable.|  
|ZWERYFIKOWANE|String|Czy wszystkie dane przestrzegają ograniczenie (WERYFIKOWANE lub NIEZWERYFIKOWANY).|  
|WYGENEROWANY|String|Czy nazwa ograniczenia jest użytkownika lub wygenerowanej przez system.|  
|BAD|String|Wartość Tak oznacza, że to ograniczenie określa wieku w sposób niejednoznaczny. Aby uniknąć błędów wynikających z tę niejednoznaczność, należy zmodyfikować ograniczenia przy użyciu funkcji TO_DATE z rokiem czterocyfrowym.|  
|POLEGAĆ|String|Włączone ograniczenie jest wymuszane czy niewymuszone.|  
|LAST_CHANGE|DataGodzina|Gdy ograniczenia ostatnio zostało włączone czy wyłączone.|  
|INDEX_OWNER|String|Nazwa użytkownika będącego właścicielem indeksu.|  
|INDEX_NAME|String|Nazwa indeksu.|  
  
## <a name="foreignkeys"></a>ForeignKeys  
  
|NazwaKolumny|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|PRIMARY_KEY_CONSTRAINT_NAME|String|Nazwa definicji ograniczenia.|  
|PRIMARY_KEY_OWNER|String|Właściciel definicji ograniczenia.|  
|PRIMARY_KEY_TABLE_NAME|String|Nazwa skojarzona z tabeli (lub Widok) przy użyciu definicji ograniczenia|  
|FOREIGN_KEY_OWNER|String|Właściciel definicji ograniczenia.|  
|FOREIGN_KEY_CONSTRIANT_NAME|String|Nazwa definicji ograniczenia.|  
|FOREIGN_KEY_TABLE_NAME|String|Nazwa skojarzona z tabeli (lub Widok) przy użyciu definicji ograniczenia.|  
|SEARCH_CONDITION JEST|String|Tekst warunków wyszukiwania dla ograniczenia check|  
|R_OWNER|String|Właściciel tabeli określonej w ograniczeniu referencyjnym.|  
|R_CONSTRAINT_NAME|String|Nazwa definicji unikatowego ograniczenia dla tabeli.|  
|DELETE_RULE|String|Usuń regułę dla ograniczenia referencyjnego (CASCADE lub NO ACTION).|  
|STAN|String|Stan wymuszania ograniczenia (włączone lub wyłączone).|  
|ZWERYFIKOWANE|String|Czy wszystkie dane przestrzegają ograniczenie (WERYFIKOWANE lub NIEZWERYFIKOWANY).|  
|WYGENEROWANY|String|Czy nazwa ograniczenia jest użytkownika lub wygenerowanej przez system.|  
|POLEGAĆ|String|Włączone ograniczenie jest wymuszane czy niewymuszone.|  
|LAST_CHANGE|DataGodzina|Gdy ograniczenia ostatnio zostało włączone czy wyłączone.|  
|INDEX_OWNER|String|Nazwa użytkownika będącego właścicielem indeksu.|  
|INDEX_NAME|String|Nazwa indeksu.|  
  
## <a name="foreignkeycolumns"></a>ForeignKeyColumns  
  
|NazwaKolumny|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|WŁAŚCICIEL|String|Właściciel definicji ograniczenia.|  
|CONSTRAINT_NAME|String|Nazwa definicji ograniczenia.|  
|TABLE_NAME|String|Nazwa tabeli z definicji ograniczenia.|  
|COLUMN_NAME|String|Nazwa kolumny lub atrybut kolumna typu obiektu, które są określone w definicji ograniczenia.|  
|STANOWISKO|Wartość dziesiętna|Początkowe położenie kolumny lub atrybutu w definicji obiektu.|  
  
## <a name="procedureparameters"></a>ProcedureParameters  
  
|NazwaKolumny|Typ danych|Opis|  
|----------------|--------------|-----------------|  
|WŁAŚCICIEL|String|Właściciel obiektu.|  
|OBJECT_NAME|String|Nazwa procedury lub funkcji.|  
|PACKAGE_NAME|String|Nazwa procedury lub funkcji.|  
|OBJECT_ID|Wartość dziesiętna|Liczba obiektów obiektu.|  
|PRZECIĄŻENIE|String|Przeciążenie Unikatowy identyfikator.|  
|ARGUMENT_NAME|String|Nazwa argumentu.|  
|STANOWISKO|Wartość dziesiętna|Pozycja na liście argumentów lub wartość null dla wartości zwracanej funkcji.|  
|SEKWENCJA|Wartość dziesiętna|Sekwencja argumentów, włącznie ze wszystkimi poziomami zagnieżdżenia.|  
|DATA_LEVEL|Wartość dziesiętna|Zagnieżdżanie głębokość argument dla typów złożonych.|  
|DATA_TYPE|String|Typ danych argumentu.|  
|DEFAULT_VALUE|String|Wartość domyślna dla argumentu.|  
|DEFAULT_LENGTH|Wartość dziesiętna|Długość domyślnej wartości dla argumentu.|  
|IN_OUT|String|Kierunek argumentu (IN, OUT lub we/wy).|  
|DATA_LENGTH|Wartość dziesiętna|Długość kolumny (w bajtach).|  
|DATA_PRECISION|Wartość dziesiętna|Długość w cyfry dziesiętne (liczba) lub cyfr (FLOAT).|  
|DATA_SCALE|Wartość dziesiętna|Cyfr z prawej strony punktu dziesiętnego w kilku.|  
|PODSTAWY|Wartość dziesiętna|Podstawy argument na liczbę.|  
|CHARACTER_SET_NAME|String|Nazwa argumentu zestaw znaków.|  
|TYPE_OWNER|String|Właściciel typ argumentu.|  
|TYPE_NAME|String|Nazwa typu argumentu. Jeśli typ to typ lokalny pakiet (oznacza to, że zostanie ona zadeklarowana w specyfikacji pakietu), a następnie w tej kolumnie jest wyświetlana nazwa pakietu.|  
|TYPE_SUBNAME|String|Zastosowanie tylko w przypadku lokalnego typów pakietów. Wyświetla nazwę typem zadeklarowanym w pakiecie, który został zidentyfikowany w kolumnie TYPE_NAME.|  
|TYPE_LINK|String|Zastosowanie tylko w przypadku lokalnego typów pakietów po pakiet, który został zidentyfikowany w kolumnie TYPE_NAME zdalnych pakietów. Ta kolumna zawiera łącze bazy danych używane do odwoływania się do zdalnego pakietu.|  
|PLS_TYPE|String|Dla argumentów numerycznych, nazwa typu PL/SQL argumentu. W przeciwnym razie wartość null.|  
|CHAR_LENGTH|Wartość dziesiętna|Limit znaków dla typów danych parametrów.|  
|CHAR_USED|String|Wskazuje, czy limicie (B) lub limitu char (C) jest oficjalnym ciągu.|  
  
## <a name="see-also"></a>Zobacz też  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
