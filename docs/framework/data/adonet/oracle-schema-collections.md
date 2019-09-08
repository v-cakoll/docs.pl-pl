---
title: Kolekcje schematów Oracle
ms.date: 03/30/2017
ms.assetid: 89a75de8-dee8-45e2-a97f-254d7e62e7e1
ms.openlocfilehash: cb91a90ae7323283556954caa401646a2063a37e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783295"
---
# <a name="oracle-schema-collections"></a>Kolekcje schematów Oracle

Program Microsoft .NET Framework Dostawca danych for Oracle obsługuje następujące kolekcje schematów oprócz wspólnych kolekcji schematów:

- Kolumny

- Zwiększa

- IndexColumns

- Procedury

- Sekwencje

- Synonimy

- Tabelę

- Użytkownicy

- Widoki

- Funkcje

- Pakiety

- PackageBodies

- Argumenty

- UniqueKeys

- PrimaryKey

- ForeignKeys

- ForeignKeyColumns

- ProcedureParameters

## <a name="columns"></a>Kolumny

|ColumnName|DataType|Opis|
|----------------|--------------|-----------------|
|WŁAOCICIELA|String|Właściciel tabeli, widoku lub klastra.|
|TABLE_NAME|String|Nazwa tabeli, widoku lub klastra.|
|COLUMN_NAME|String|Nazwa kolumny.|
|id|Wartość dziesiętna|Numer sekwencyjny kolumny jako utworzony.|
|TYPU|String|Typ danych kolumny.|
|DŁUGOŚĆ|Wartość dziesiętna|Długość kolumny w bajtach.|
|DOKŁADNE|Wartość dziesiętna|Precyzja dziesiętna dla typu danych NUMBER; precyzja binarna dla typu ZMIENNOPRZECINKOWego, null dla wszystkich innych typów danych.|
|ZASIĘGU|Wartość dziesiętna|Cyfry z prawej strony punktu dziesiętnego w liczbie.|
|WYMAGA|String|Określa, czy kolumna dopuszcza wartości NULL. Wartość to N, jeśli w kolumnie istnieje ograniczenie NOT NULL lub jeśli kolumna jest częścią klucza podstawowego.|

## <a name="indexes"></a>Zwiększa

|ColumnName|DataType|Opis|
|----------------|--------------|-----------------|
|WŁAOCICIELA|String|Właściciel indeksu|
|INDEX_NAME|String|Nazwa indeksu.|
|INDEX_TYPE|String|Typ indeksu (NORMALNa, mapa bitowa, oparta na FUNKCJAch zwykła, oparta na FUNKCJAch Mapa bitowa lub domena).|
|TABLE_OWNER|String|Właściciel indeksowanego obiektu.|
|TABLE_NAME|String|Nazwa indeksowanego obiektu.|
|TABLE_TYPE|String|Typ indeksowanego obiektu (na przykład tabela, klaster).|
|UNIKATOWOŚĆ|String|Czy indeks jest unikatowy, czy nieunikatowy.|
|SKOMPRESOWANE|String|Określa, czy indeks jest włączony, czy wyłączony.|
|PREFIX_LENGTH|Wartość dziesiętna|Liczba kolumn w prefiksie klucza kompresji.|
|TABLESPACE_NAME|String|Nazwa obszaru tabel zawierającego indeks.|
|INI_TRANS|Wartość dziesiętna|Początkowa liczba transakcji.|
|MAX_TRANS|Wartość dziesiętna|Maksymalna liczba transakcji.|
|INITIAL_EXTENT|Wartość dziesiętna|Rozmiar początkowego zakresu.|
|NEXT_EXTENT|Wartość dziesiętna|Rozmiar pomocniczych zakresów.|
|MIN_EXTENTS|Wartość dziesiętna|Minimalna liczba zakresów dozwolona w segmencie.|
|MAX_EXTENTS|Wartość dziesiętna|Maksymalna dozwolona liczba zakresów w segmencie.|
|PCT_INCREASE|Wartość dziesiętna|Procent wzrostu rozmiaru w zakresie.|
|PCT_THRESHOLD|Wartość dziesiętna|Procentowy próg dozwolonego miejsca blokowego na wpis indeksu.|
|INCLUDE_COLUMN|Wartość dziesiętna|Identyfikator kolumny ostatniej kolumny, która ma zostać uwzględniona w indeksie klucza podstawowego tabeli (nie przepełnienia). Ta kolumna jest mapowana do kolumny COLUMN_ID w widokach słownika danych _TAB_COLUMNS.|
|FREELISTS|Wartość dziesiętna|Liczba freelists procesu przydzielono do tego segmentu.|
|FREELIST_GROUPS|Wartość dziesiętna|Liczba grup freelist przypisywanych do tego segmentu.|
|PCT_FREE|Wartość dziesiętna|Minimalny procent wolnego miejsca w bloku.|
|REJESTROWAĆ|String|Rejestrowanie informacji.|
|BLEVEL|Wartość dziesiętna|B *-poziomy drzewa: głębokość indeksu z jego bloku głównego do jego bloków liścia. Głębokość 0 wskazuje, że główny blok i blok liścia są takie same.|
|LEAF_BLOCKS|Wartość dziesiętna|Liczba bloków liścia w indeksie|
|DISTINCT_KEYS|Wartość dziesiętna|Liczba unikatowych indeksowanych wartości. W przypadku indeksów, które wymuszają ograniczenia UNIQUE i PRIMARY KEY, ta wartość jest taka sama jak liczba wierszy w tabeli (USER_TABLES. NUM_ROWS).|
|AVG_LEAF_BLOCKS_PER_KEY|Wartość dziesiętna|Średnia liczba bloków liścia, w których każda unikatowa wartość w indeksie jest zaokrąglana do najbliższej liczby całkowitej. W przypadku indeksów, które wymuszają ograniczenia UNIQUE i PRIMARY KEY, ta wartość jest zawsze równa 1.|
|AVG_DATA_BLOCKS_PER_KEY|Wartość dziesiętna|Średnia liczba bloków danych w tabeli, które są wskazywane przez unikatową wartość w indeksie zaokrągloną do najbliższej liczby całkowitej. Ta statystyka to średnia liczba bloków danych, które zawierają wiersze zawierające daną wartość dla indeksowanych kolumn.|
|CLUSTERING_FACTOR|Wartość dziesiętna|Wskazuje ilość zamówienia wierszy w tabeli na podstawie wartości indeksu.|
|STANY|String|Czy indeks niepartycjonowany jest prawidłowy, czy nie można go użyć.|
|NUM_ROWS|Wartość dziesiętna|Liczba wierszy w indeksie.|
|SAMPLE_SIZE|Wartość dziesiętna|Rozmiar próbki używany do analizowania indeksu.|
|LAST_ANALYZED|DataGodzina|Data ostatniego przeanalizowania tego indeksu.|
|STOPIEŃ|String|Liczba wątków na wystąpienie na potrzeby skanowania indeksu.|
|LICZBA|String|Liczba wystąpień, w których indeksy mają być skanowane.|
|PARTYCJONOWANE|String|Określa, czy ten indeks jest podzielony na &#124; partycje (tak nie).|
|PRAWA|String|Czy indeks znajduje się w tabeli tymczasowej.|
|WYTWARZA|String|Określa, czy nazwa indeksu jest generowana przez system (&#124;t N).|
|DODATKOWYCH|String|Czy indeks jest obiektem pomocniczym utworzonym przez metodę ODCIIndexCreate kasety danych Oracle9i (Y&#124;N).|
|BUFFER_POOL|String|Nazwa domyślnej puli buforów, która ma być używana dla bloków indeksu.|
|USER_STATS|String|Czy statystyki zostały wprowadzone bezpośrednio przez użytkownika.|
|TRWANIA|String|Wskazuje czas trwania tabeli tymczasowej: 1) SYS $ SESSION: wiersze są zachowywane na czas trwania sesji, 2) SYS $ TRANSACTION: wiersze są usuwane po ZATWIERDZENIu, 3) wartości null dla trwałej tabeli.|
|PCT_DIRECT_ACCESS|Wartość dziesiętna|W przypadku indeksu pomocniczego tabeli zorganizowanej w indeksie procent wierszy z PRAWIDŁOWYm zgadywaniem|
|ITYP_OWNER|String|Dla indeksu domeny, właściciel obiektu IndexType.|
|ITYP_NAME|String|Nazwa typu IndexType dla indeksu domeny.|
|WEJŚCIOWE|String|W przypadku indeksu domeny ciąg parametru.|
|GLOBAL_STATS|String|W przypadku indeksów partycjonowanych wskazuje, czy statystyki zostały zebrane przez analizowanie indeksu jako całości (tak), czy szacowane na podstawie statystyk dotyczących partycji indeksu bazowego i podpartycji (nie).|
|DOMIDX_STATUS|String|Odzwierciedla stan indeksu domeny. Wartość zerowa: określony indeks nie jest indeksem domeny. PRAWIDŁOWY: indeks jest prawidłowym indeksem domeny. IDXTYP_INVLD: Typ indeksu tego indeksu domeny jest nieprawidłowy.|
|DOMIDX_OPSTATUS|String|Odzwierciedla stan operacji wykonanej na indeksie domeny: Wartość zerowa: określony indeks nie jest indeksem domeny. PRAWIDŁOWE: operacja została wykonana bez błędów. Niepowodzenie: operacja nie powiodła się z powodu błędu.|
|FUNCIDX_STATUS|String|Wskazuje stan indeksu opartego na funkcji: NULL: to nie jest indeks oparty na funkcji, włączony: indeks oparty na funkcji jest włączony, wyłączony: indeks oparty na funkcjach jest wyłączony.|
|JOIN_INDEX|String|Wskazuje, czy jest to indeks sprzężenia, czy nie.|

## <a name="indexcolumns"></a>IndexColumns

|ColumnName|DataType|Opis|
|----------------|--------------|-----------------|
|INDEX_OWNER|String|Właściciel indeksu.|
|INDEX_NAME|String|Nazwa indeksu.|
|TABLE_OWNER|String|Właściciel tabeli lub klastra.|
|TABLE_NAME|String|Nazwa tabeli lub klastra.|
|COLUMN_NAME|String|Nazwa kolumny lub atrybut kolumny typu Object.|
|COLUMN_POSITION|Wartość dziesiętna|Pozycja kolumny lub atrybutu w indeksie.|
|COLUMN_LENGTH|Wartość dziesiętna|Indeksowana długość kolumny.|
|CHAR_LENGTH|Wartość dziesiętna|Maksymalna kodu długość kolumny.|
|ELEMENTY|String|Określa, czy kolumna jest sortowana w kolejności malejącej.|

## <a name="procedures"></a>Procedury

|ColumnName|DataType|Opis|
|----------------|--------------|-----------------|
|WŁAOCICIELA|String|Właściciel obiektu.|
|OBJECT_NAME|String|Nazwa obiektu.|
|SUBOBJECT_NAME|String|Nazwa podobiektu (na przykład Partition).|
|OBJECT_ID|Wartość dziesiętna|Numer obiektu słownika.|
|DATA_OBJECT_ID|Wartość dziesiętna|Numer obiektu słownika z segmentem zawierającym obiekt.|
|LAST_DDL_TIME|DataGodzina|Sygnatura czasowa ostatniej modyfikacji obiektu wynikający z polecenia DDL (w tym Grants and revokes).|
|TIMESTAMP|String|Sygnatura czasowa dla specyfikacji obiektu (dane znakowe).|
|STANY|String|Stan obiektu (prawidłowy, nieprawidłowy lub N/A).|
|PRAWA|String|Określa, czy obiekt jest tymczasowy (bieżąca sesja może zobaczyć tylko te dane, które zostały umieszczone w tym obiekcie).|
|WYTWARZA|String|Czy nazwa tego systemu obiektów została wygenerowana? (T &#124; N).|
|DODATKOWYCH|String|Określa, czy jest to obiekt pomocniczy utworzony przez metodę ODCIIndexCreate kasety danych Oracle9i (Y &#124; N).|
|UTWORZONY|DataGodzina|Data utworzenia obiektu.|

## <a name="sequences"></a>Sekwencje

|ColumnName|DataType|Opis|
|----------------|--------------|-----------------|
|SEQUENCE_OWNER|String|Nazwa właściciela sekwencji.|
|SEQUENCE_NAME|String|Nazwa sekwencji.|
|MIN_VALUE|Wartość dziesiętna|Minimalna wartość sekwencji.|
|MAX_VALUE|Wartość dziesiętna|Maksymalna wartość sekwencji.|
|INCREMENT_BY|Wartość dziesiętna|Wartość, według której sekwencja jest zwiększana.|
|CYCLE_FLAG|String|Powoduje Zawijanie sekwencji wokół osiągnięcia limitu.|
|ORDER_FLAG|String|Numery sekwencji są generowane w kolejności.|
|CACHE_SIZE|Wartość dziesiętna|Liczba numerów sekwencji do buforowania.|
|LAST_NUMBER|Wartość dziesiętna|Ostatni numer sekwencyjny zapisany na dysku. Jeśli sekwencja używa buforowania, liczba zapisywana na dysku jest ostatnim numerem umieszczonym w pamięci podręcznej sekwencji. Ta liczba może być większa niż ostatni użyty numer sekwencyjny.|

## <a name="synonyms"></a>Synonimy

|ColumnName|DataType|Opis|
|----------------|--------------|-----------------|
|WŁAOCICIELA|String|Właściciel synonimu.|
|SYNONYM_NAME|String|Nazwa synonimu.|
|TABLE_OWNER|String|Właściciel obiektu, do którego odwołuje się synonim.|
|TABLE_NAME|String|Nazwa obiektu, do którego odwołuje się synonim.|
|DB_LINK|String|Nazwa łącza do bazy danych, do którego istnieje odwołanie (jeśli istnieje).|

## <a name="tables"></a>Tabelę

|ColumnName|DataType|Opis|
|----------------|--------------|-----------------|
|WŁAOCICIELA|String|Właściciel tabeli.|
|TABLE_NAME|String|Nazwa tabeli.|
|WPROWADŹ|String|Typ tabeli.|

## <a name="users"></a>Użytkownicy

|ColumnName|DataType|Opis|
|----------------|--------------|-----------------|
|NAZWA|String|Nazwa użytkownika.|
|id|Wartość dziesiętna|Numer IDENTYFIKACYJNy użytkownika.|
|DATA I GODZINA|DataGodzina|Data utworzenia użytkownika.|

## <a name="views"></a>Widoki

|ColumnName|DataType|Opis|
|----------------|--------------|-----------------|
|WŁAOCICIELA|String|Właściciel widoku.|
|VIEW_NAME|String|Nazwa widoku.|
|TEXT_LENGTH|Wartość dziesiętna|Długość tekstu widoku.|
|TEXT|String|Wyświetl tekst.|
|TYPE_TEXT_LENGTH|Wartość dziesiętna|Długość klauzuli Type w widoku z określonym typem.|
|TYPE_TEXT|String|Klauzula typu widoku z określonym typem.|
|OID_TEXT_LENGTH|Wartość dziesiętna|Długość klauzuli WITH OID w widoku o określonym typie.|
|OID_TEXT|String|Z klauzulą OID widoku z określonym typem.|
|VIEW_TYPE_OWNER|String|Właściciel typu widoku, jeśli widok jest widokiem określonym przez.|
|VIEW_TYPE|String|Typ widoku, jeśli widok jest widokiem określonym przez.|
|SUPERVIEW_NAME|String|Nazwa widoku.|

## <a name="functions"></a>Funkcje

|ColumnName|DataType|Opis|
|----------------|--------------|-----------------|
|WŁAOCICIELA|String|Właściciel obiektu.|
|OBJECT_NAME|String|Nazwa obiektu.|
|SUBOBJECT_NAME|String|Nazwa podobiektu (na przykład Partition).|
|OBJECT_ID|Wartość dziesiętna|Numer obiektu słownika.|
|DATA_OBJECT_ID|Wartość dziesiętna|Numer obiektu słownika z segmentem zawierającym obiekt.|
|OBJECT_TYPE|String|Typ obiektu.|
|UTWORZONY|DataGodzina|Data utworzenia obiektu.|
|LAST_DDL_TIME|DataGodzina|Sygnatura czasowa ostatniej modyfikacji obiektu wynikający z polecenia DDL (w tym Grants and revokes).|
|TIMESTAMP|String|Sygnatura czasowa dla specyfikacji obiektu (dane znakowe)|
|STANY|String|Stan obiektu (prawidłowy, nieprawidłowy lub N/A).|
|PRAWA|String|Określa, czy obiekt jest tymczasowy (bieżąca sesja może zobaczyć tylko te dane, które zostały umieszczone w tym obiekcie).|
|WYTWARZA|String|Czy nazwa tego systemu obiektów została wygenerowana? (T &#124; N).|
|DODATKOWYCH|String|Określa, czy jest to obiekt pomocniczy utworzony przez metodę ODCIIndexCreate kasety danych Oracle9i (Y &#124; N).|

## <a name="packages"></a>Pakiety

|ColumnName|DataType|Opis|
|----------------|--------------|-----------------|
|WŁAOCICIELA|String|Właściciel obiektu.|
|OBJECT_NAME|String|Nazwa obiektu.|
|SUBOBJECT_NAME|String|Nazwa podobiektu (na przykład Partition).|
|OBJECT_ID|Wartość dziesiętna|Numer obiektu słownika.|
|DATA_OBJECT_ID|Wartość dziesiętna|Numer obiektu słownika z segmentem zawierającym obiekt.|
|LAST_DDL_TIME|DataGodzina|Sygnatura czasowa ostatniej modyfikacji obiektu wynikający z polecenia DDL (w tym Grants and revokes).|
|TIMESTAMP|String|Sygnatura czasowa dla specyfikacji obiektu (dane znakowe).|
|STANY|String|Stan obiektu (prawidłowy, nieprawidłowy lub N/A).|
|PRAWA|String|Określa, czy obiekt jest tymczasowy (bieżąca sesja może zobaczyć tylko te dane, które zostały umieszczone w tym obiekcie).|
|WYTWARZA|String|Czy nazwa tego systemu obiektów została wygenerowana? (T &#124; N).|
|DODATKOWYCH|String|Określa, czy jest to obiekt pomocniczy utworzony przez metodę ODCIIndexCreate kasety danych Oracle9i (Y &#124; N).|
|UTWORZONY|DataGodzina|Data utworzenia obiektu.|

## <a name="packagebodies"></a>PackageBodies

|ColumnName|DataType|Opis|
|----------------|--------------|-----------------|
|WŁAOCICIELA|String|Właściciel obiektu.|
|OBJECT_NAME|String|Nazwa obiektu.|
|SUBOBJECT_NAME|String|Nazwa podobiektu (na przykład Partition).|
|OBJECT_ID|Wartość dziesiętna|Numer obiektu słownika.|
|DATA_OBJECT_ID|Wartość dziesiętna|Numer obiektu słownika z segmentem zawierającym obiekt.|
|LAST_DDL_TIME|DataGodzina|Sygnatura czasowa ostatniej modyfikacji obiektu wynikający z polecenia DDL (w tym Grants and revokes).|
|TIMESTAMP|String|Sygnatura czasowa dla specyfikacji obiektu (dane znakowe).|
|STANY|String|Stan obiektu (prawidłowy, nieprawidłowy lub N/A).|
|PRAWA|String|Określa, czy obiekt jest tymczasowy (bieżąca sesja może zobaczyć tylko te dane, które zostały umieszczone w tym obiekcie).|
|WYTWARZA|String|Czy nazwa tego systemu obiektów została wygenerowana? (T &#124; N).|
|DODATKOWYCH|String|Określa, czy jest to obiekt pomocniczy utworzony przez metodę ODCIIndexCreate kasety danych Oracle9i (Y &#124; N).|
|UTWORZONY|DataGodzina|Data utworzenia obiektu.|

## <a name="arguments"></a>Argumenty

|ColumnName|DataType|Opis|
|----------------|--------------|-----------------|
|WŁAOCICIELA|String|Nazwa właściciela obiektu.|
|PACKAGE_NAME|String|Nazwa pakietu.|
|OBJECT_NAME|String|Nazwa procedury lub funkcji.|
|ARGUMENT_NAME|String|Nazwa argumentu.|
|UMIEŚCIĆ|Wartość dziesiętna|Pozycja na liście argumentów lub wartość zerowa dla wartości zwracanej funkcji.|
|NAZWISK|Wartość dziesiętna|Sekwencja argumentów, z uwzględnieniem wszystkich poziomów zagnieżdżenia.|
|DEFAULT_VALUE|String|Wartość domyślna dla argumentu.|
|DEFAULT_LENGTH|Wartość dziesiętna|Długość wartości domyślnej argumentu.|
|IN_OUT|String|Kierunek argumentu (w, OUT lub we/OUT).|
|DATA_LENGTH|Wartość dziesiętna|Długość kolumny w bajtach.|
|DATA_PRECISION|Wartość dziesiętna|Długość w cyfrach dziesiętnych (liczba) lub cyfry binarne (ZMIENNOPRZECINKOWe).|
|DATA_SCALE|Wartość dziesiętna|Cyfry z prawej strony punktu dziesiętnego w liczbie.|
|DATA_TYPE|String|Typ danych argumentu.|

## <a name="uniquekeys"></a>UniqueKeys

|ColumnName|DataType|Opis|
|----------------|--------------|-----------------|
|WŁAOCICIELA|String|Właściciel definicji ograniczenia.|
|CONSTRAINT_NAME|String|Nazwa definicji ograniczenia.|
|TABLE_NAME|String|Nazwa skojarzona z tabelą (lub widokiem) z definicją ograniczenia.|
|SEARCH_CONDITION|String|Tekst warunku wyszukiwania dla ograniczenia check.|
|R_OWNER|String|Właściciel tabeli, do której odwołuje się ograniczenie referencyjne.|
|R_CONSTRAINT_NAME|String|Nazwa unikatowej definicji ograniczenia dla tabeli, do której istnieje odwołanie.|
|DELETE_RULE|String|Usuń regułę ograniczenia referencyjnego (KASKADowo lub bez akcji).|
|STANY|String|Stan wymuszania ograniczenia (włączone lub wyłączone).|
|ODROCZENIE|String|Określa, czy ograniczenie jest opóźnione.|
|ZWERYFIKOWANE|String|Określa, czy wszystkie dane przestrzegają ograniczenia (ZWERYFIKOWANe lub nie ZWERYFIKOWANe).|
|WYTWARZA|String|Określa, czy nazwa ograniczenia jest generowana przez użytkownika, czy system.|
|BAD|String|Wartość YES wskazuje, że to ograniczenie określa Century w sposób niejednoznaczny. Aby uniknąć błędów wynikających z tej niejednoznaczności, należy ponownie napisać ograniczenie przy użyciu funkcji TO_DATE z rokiem czterocyfrowym.|
|POLEGAĆ|String|Czy włączone ograniczenie jest wymuszane lub niewymuszane.|
|LAST_CHANGE|DataGodzina|Kiedy ograniczenie zostało ostatnio włączone lub wyłączone|
|INDEX_OWNER|String|Nazwa użytkownika będącego właścicielem indeksu|
|INDEX_NAME|String|Nazwa indeksu|

## <a name="primarykeys"></a>PrimaryKey

|ColumnName|DataType|Opis|
|----------------|--------------|-----------------|
|WŁAOCICIELA|String|Właściciel definicji ograniczenia.|
|CONSTRAINT_NAME|String|Nazwa definicji ograniczenia.|
|TABLE_NAME|String|Nazwa skojarzona z tabelą (lub widokiem) z definicją ograniczenia.|
|SEARCH_CONDITION|String|Tekst warunku wyszukiwania dla ograniczenia check.|
|R_OWNER|String|Właściciel tabeli, do której odwołuje się ograniczenie referencyjne.|
|R_CONSTRAINT_NAME|String|Nazwa unikatowej definicji ograniczenia dla tabeli, do której istnieje odwołanie.|
|DELETE_RULE|String|Usuń regułę ograniczenia referencyjnego (KASKADowo lub bez akcji).|
|STANY|String|Stan wymuszania ograniczenia (włączone lub wyłączone).|
|ODROCZENIE|String|Określa, czy ograniczenie jest opóźnione.|
|ZWERYFIKOWANE|String|Określa, czy wszystkie dane przestrzegają ograniczenia (ZWERYFIKOWANe lub nie ZWERYFIKOWANe).|
|WYTWARZA|String|Określa, czy nazwa ograniczenia jest generowana przez użytkownika, czy system.|
|BAD|String|Wartość YES wskazuje, że to ograniczenie określa Century w sposób niejednoznaczny. Aby uniknąć błędów wynikających z tej niejednoznaczności, należy ponownie napisać ograniczenie przy użyciu funkcji TO_DATE z rokiem czterocyfrowym.|
|POLEGAĆ|String|Czy włączone ograniczenie jest wymuszane lub niewymuszane.|
|LAST_CHANGE|DataGodzina|Kiedy ograniczenie zostało ostatnio włączone lub wyłączone.|
|INDEX_OWNER|String|Nazwa użytkownika będącego właścicielem indeksu.|
|INDEX_NAME|String|Nazwa indeksu.|

## <a name="foreignkeys"></a>ForeignKeys

|ColumnName|DataType|Opis|
|----------------|--------------|-----------------|
|PRIMARY_KEY_CONSTRAINT_NAME|String|Nazwa definicji ograniczenia.|
|PRIMARY_KEY_OWNER|String|Właściciel definicji ograniczenia.|
|PRIMARY_KEY_TABLE_NAME|String|Nazwa skojarzona z tabelą (lub widokiem) z definicją ograniczenia|
|FOREIGN_KEY_OWNER|String|Właściciel definicji ograniczenia.|
|FOREIGN_KEY_CONSTRAINT_NAME|String|Nazwa definicji ograniczenia.|
|FOREIGN_KEY_TABLE_NAME|String|Nazwa skojarzona z tabelą (lub widokiem) z definicją ograniczenia.|
|SEARCH_CONDITION|String|Tekst warunku wyszukiwania dla ograniczenia check|
|R_OWNER|String|Właściciel tabeli, do której odwołuje się ograniczenie referencyjne.|
|R_CONSTRAINT_NAME|String|Nazwa unikatowej definicji ograniczenia dla tabeli, do której istnieje odwołanie.|
|DELETE_RULE|String|Usuń regułę ograniczenia referencyjnego (KASKADowo lub bez akcji).|
|STANY|String|Stan wymuszania ograniczenia (włączone lub wyłączone).|
|ZWERYFIKOWANE|String|Określa, czy wszystkie dane przestrzegają ograniczenia (ZWERYFIKOWANe lub nie ZWERYFIKOWANe).|
|WYTWARZA|String|Określa, czy nazwa ograniczenia jest generowana przez użytkownika, czy system.|
|POLEGAĆ|String|Czy włączone ograniczenie jest wymuszane lub niewymuszane.|
|LAST_CHANGE|DataGodzina|Kiedy ograniczenie zostało ostatnio włączone lub wyłączone.|
|INDEX_OWNER|String|Nazwa użytkownika będącego właścicielem indeksu.|
|INDEX_NAME|String|Nazwa indeksu.|

## <a name="foreignkeycolumns"></a>ForeignKeyColumns

|ColumnName|DataType|Opis|
|----------------|--------------|-----------------|
|WŁAOCICIELA|String|Właściciel definicji ograniczenia.|
|CONSTRAINT_NAME|String|Nazwa definicji ograniczenia.|
|TABLE_NAME|String|Nazwa tabeli z definicją ograniczenia.|
|COLUMN_NAME|String|Nazwa kolumny lub atrybutu kolumny typu obiektu określonego w definicji ograniczenia.|
|UMIEŚCIĆ|Wartość dziesiętna|Oryginalna pozycja kolumny lub atrybutu w definicji obiektu.|

## <a name="procedureparameters"></a>ProcedureParameters

|ColumnName|DataType|Opis|
|----------------|--------------|-----------------|
|WŁAOCICIELA|String|Właściciel obiektu.|
|OBJECT_NAME|String|Nazwa procedury lub funkcji.|
|PACKAGE_NAME|String|Nazwa procedury lub funkcji.|
|OBJECT_ID|Wartość dziesiętna|Numer obiektu obiektu.|
|WYSTĘPUJĄ|String|Unikatowy identyfikator przeciążenia.|
|ARGUMENT_NAME|String|Nazwa argumentu.|
|UMIEŚCIĆ|Wartość dziesiętna|Pozycja na liście argumentów lub wartość zerowa dla zwracanej wartości funkcji.|
|NAZWISK|Wartość dziesiętna|Sekwencja argumentów, z uwzględnieniem wszystkich poziomów zagnieżdżenia.|
|DATA_LEVEL|Wartość dziesiętna|Zagnieżdżanie głębokości argumentu dla typów złożonych.|
|DATA_TYPE|String|Typ danych argumentu.|
|DEFAULT_VALUE|String|Wartość domyślna dla argumentu.|
|DEFAULT_LENGTH|Wartość dziesiętna|Długość wartości domyślnej argumentu.|
|IN_OUT|String|Kierunek argumentu (w, OUT lub we/OUT).|
|DATA_LENGTH|Wartość dziesiętna|Długość kolumny (w bajtach).|
|DATA_PRECISION|Wartość dziesiętna|Długość w cyfrach dziesiętnych (liczba) lub cyfry binarne (ZMIENNOPRZECINKOWe).|
|DATA_SCALE|Wartość dziesiętna|Cyfry z prawej strony punktu dziesiętnego w liczbie.|
|RADIX|Wartość dziesiętna|Argument podstawy dla liczby.|
|CHARACTER_SET_NAME|String|Nazwa zestawu znaków dla argumentu.|
|TYPE_OWNER|String|Właściciel typu argumentu.|
|TYPE_NAME|String|Nazwa typu argumentu. Jeśli typ jest typem lokalnym pakietu (oznacza to, że jest zadeklarowany w specyfikacji pakietu), w tej kolumnie jest wyświetlana nazwa pakietu.|
|TYPE_SUBNAME|String|Dotyczy tylko typów lokalnych pakietu. Wyświetla nazwę typu zadeklarowanego w pakiecie identyfikowanego w kolumnie TYPE_NAME.|
|TYPE_LINK|String|Dotyczy tylko typów lokalnych pakietu, gdy pakiet zidentyfikowany w kolumnie TYPE_NAME jest pakietem zdalnym. W tej kolumnie jest wyświetlane łącze bazy danych używane do odwoływania się do pakietu zdalnego.|
|PLS_TYPE|String|Dla argumentów liczbowych, nazwa typu PL/SQL argumentu. W przeciwnym razie wartość null.|
|CHAR_LENGTH|Wartość dziesiętna|Limit znaków dla typów danych ciągu.|
|CHAR_USED|String|Wskazuje, czy limit bajtów (B) lub limit znaków (C) jest oficjalny dla ciągu.|

## <a name="see-also"></a>Zobacz także

- [Omówienie ADO.NET](ado-net-overview.md)
