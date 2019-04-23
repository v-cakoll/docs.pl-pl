---
title: Narzędzie edytora konfiguracji (SvcConfigEditor.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- configuration files, creating
- configuration files
- Configuration file
- configuration file schema
ms.assetid: 2db21a57-5f64-426f-89df-fb0dc2d2def5
ms.openlocfilehash: e4b54026c71e18e4011661c5cad2ca95dfcb733e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59979943"
---
# <a name="configuration-editor-tool-svcconfigeditorexe"></a>Narzędzie edytora konfiguracji (SvcConfigEditor.exe)
Edytor konfiguracji usługi Windows Communication Foundation (WCF) (SvcConfigEditor.exe) umożliwia administratorów i deweloperów, tworzenie i modyfikowanie ustawień konfiguracji dla usług WCF za pomocą graficznego interfejsu użytkownika. Za pomocą tego narzędzia można zarządzać ustawieniami dla wiązania WCF, zachowań, usług i diagnostyki, bez konieczności bezpośredniego edytowania pliki konfiguracji XML.  
  
 Edytor konfiguracji usługi znajdują się w folderze C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin.  
  
## <a name="the-wcf-configuration-editor"></a>Edytor konfiguracji usługi WCF  
 Edytor konfiguracji usługi jest dostarczany za pomocą kreatora, który przeprowadzi Cię przez wszystkie etapy konfiguracji usługi WCF lub klienta. Zdecydowanie zaleca się bezpośrednio za pomocą Kreatora zamiast edytora.  
  
 Jeśli masz już pewne pliki konfiguracji, które są zgodne ze schematem System.Configuration standardowy, można zarządzać konkretne ustawienia dla powiązania, zachowanie, usług i diagnostyki za pomocą interfejsu użytkownika. Edytor konfiguracji usługi umożliwia zarządzanie ustawieniami dla istniejących plików konfiguracyjnych WCF, a także pliki wykonywalne, usług COM + i usług hostowanych w sieci Web. Podczas otwierania hostowanych w sieci Web usługi za pomocą Edytor konfiguracji usługi, obie usługi firmy własnej konfiguracji i sekcje dziedziczone konfiguracje węzłów górnego poziomu są wyświetlane.  
  
 Ponieważ ustawienia konfiguracji usługi WCF znajdują się w `<system.serviceModel>` sekcję pliku konfiguracji, Edytor działa wyłącznie w przypadku zawartości tego elementu, a nie inne elementy w tym samym pliku. Możesz bezpośrednio przejść do istniejących plików konfiguracji lub możesz wybrać zestaw, który zawiera usługi, katalog wirtualny lub usług COM +. Edytor ładuje plik konfiguracji dla określonej usługi i zezwala użytkownikowi na dodawanie nowych elementów lub Edytuj istniejące elementy zagnieżdżone w `<system.serviceModel>` sekcję pliku konfiguracji.  
  
 Edytor obsługuje funkcję IntelliSense i wymusza zgodność schematu. Dane wyjściowe jest gwarantowane do wykonania schemat pliku konfiguracji i mogą mieć wartości składniowo poprawne dane. Jednak Edytor nie gwarantuje, że plik konfiguracyjny jest semantycznie prawidłowy. Innymi słowy edytora nie gwarantuje, że plik konfiguracyjny może pracować z usługą, który konfiguruje.  
  
> [!CAUTION]
>  Nie można przeczyścić element konfiguracji z pliku konfiguracji w edytorze, po zmodyfikowaniu elementu. Na przykład jeśli używasz edytora ustawiona nazwa punktu końcowego na ciąg pusty, a następnie zapisać go plik konfiguracyjny ma następującą zawartością, jak pokazano w poniższym przykładzie.  
>   
>  `<endpoint binding="basicHttpBinding" name="somename" />`  
>   
>  Jeśli spróbujesz usunąć nazwę przez ustawienie jej pusty ciąg, a następnie zapisz plik nadal plik konfiguracyjny zawiera `name` atrybutu, jak pokazano w poniższym przykładzie.  
>   
>  `<endpoint binding="basicHttpBinding" name="" />`  
>   
>  Aby wyczyścić ten atrybut, należy ręcznie zmodyfikować element przy użyciu innego edytora tekstu.  
>   
>  Należy szczególnie uważać, aby ten problem, korzystając z `issueToken` elementu `clientCredential` zachowanie punktu końcowego. W szczególności `address` atrybutu jego `localIssuer` element podrzędny nie może być ciągiem pustym. Jeśli zmodyfikowano `address` atrybutu za pomocą edytora konfiguracji i chcesz całkowicie usunąć, należy to zrobić przy użyciu narzędzia innego niż edytora. W przeciwnym razie ten atrybut zawiera pusty ciąg, i zgłasza wyjątek, aplikacji.  
  
## <a name="using-the-configuration-editor"></a>Za pomocą edytora konfiguracji  
 Edytor konfiguracji usługi można znaleźć w następującej lokalizacji instalacji zestawu Windows SDK:  
  
 C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin\SvcConfigEditor.exe  
  
 Po uruchomieniu Edytor konfiguracji usługi, możesz użyć **plik i Otwórz** menu, aby przejść do usługi lub zestawu, w którym chcesz zarządzać. Możesz otworzyć pliki bezpośrednio, Przeglądaj w poszukiwaniu usług WCF /COM+ i Otwórz pliki konfiguracji usługi hostowane w sieci Web.  
  
 Interfejs użytkownika edytora konfiguracji usługi jest podzielona na następujące obszary:  
  
-   Okienka widoku drzewa, który zawiera elementy konfiguracji w strukturze drzewa po lewej stronie. Aby wykonywać operacje w drzewie, kliknij prawym przyciskiem myszy węzły.  
  
-   Okienka zadań, która wyświetla typowe zadania związane z bieżącym elementów w lewym dolnym rogu okna  
  
-   Okienko Szczegóły są wyświetlane szczegółowe ustawienia konfiguracji węzła wybranego w widoku drzewa po prawej stronie.  
  
### <a name="opening-a-configuration-file"></a>Otwieranie pliku konfiguracji  
  
1. Uruchom Edytor konfiguracji usługi za pomocą okno polecenia przejdź do lokalizacji instalacji usługi WCF, a następnie wpisz `SvcConfigEditor.exe`.  
  
2. Z **pliku** menu, wybierz opcję **Otwórz** i kliknij typ pliku, w którym chcesz zarządzać.  
  
3. W **Otwórz** okno dialogowe, przejdź do określonego pliku, o których chcesz zarządzać, a następnie kliknij go dwukrotnie.  
  
 Podgląd postępuje zgodnie ze ścieżką konfiguracji scalania i automatycznie tworzy widok scalony konfiguracji. Na przykład rzeczywistą konfigurację-hostowanej usługi jest kombinacją Machine.config i pliku App.config. Wszelkie zmiany są stosowane do aktywnego pliku w pomocą narzędzia SvcConfigEditor. Jeśli chcesz edytować określonego pliku w ścieżce scalania konfiguracji, należy go otworzyć bezpośrednio.  
  
> [!NOTE]
>  Edytor konfiguracji ponownie ładuje plik konfiguracyjny aktualnie otwarte po jego został zmodyfikowany poza edytorem. W takim przypadku wszystkie zmiany, które nie są trwale zapisane w edytorze zostaną utracone. Jeśli ponowne załadowanie stale występuje, najbardziej prawdopodobną przyczyną jest to usługa, która stale uzyskuje dostęp do pliku konfiguracji, na przykład w tle jest uruchomione oprogramowanie antywirusowe. Aby rozwiązać ten problem, upewnij się, że edytor konfiguracji tylko proces, który można uzyskać dostępu do pliku, gdy zostanie otwarta.  
  
### <a name="services"></a>Usługi  
 **Usług** węzeł zawiera wszystkie aktualnie przypisane w pliku konfiguracji usługi. Każdy węzeł podrzędny w drzewie odnosi się do podrzędnego elementu <`services`> element pliku konfiguracji.  
  
 Po kliknięciu **usług** węzeł, aby wyświetlić lub wykonać zadania w usłudze strony Podsumowanie **szczegółów** okienka.  
  
#### <a name="creating-a-new-service-configuration"></a>Tworząc nową konfigurację usługi  
 Można utworzyć nową konfigurację usługi w następujący sposób:  
  
-   Przy użyciu kreatora: Kliknij łącze **Utwórz nową usługę...** Okienko zadań lub strony Podsumowanie, które można uruchomić kreatora. Można również wykonać dlatego w **pliku** menu -> **Dodaj nowy element**.  
  
-   Ręczne tworzenie: Możesz kliknąć prawym przyciskiem myszy **usług** węzeł i wybierz polecenie **nową usługę**.  
  
#### <a name="creating-a-new-service-endpoint-configuration"></a>Tworzenie nowej konfiguracji punktu końcowego usługi  
 Można utworzyć nową konfigurację punktu końcowego usługi, w następujący sposób:  
  
-   Tworzenie przy użyciu kreatora: kliknij link **utworzyć nowy punkt końcowy usługi...** Okienko zadań lub strony Podsumowanie, które można uruchomić kreatora. Można również wykonać dlatego w **pliku** menu -> **Dodaj nowy element**.  
  
-   Ręczne tworzenie: Po utworzeniu usługi, możesz kliknąć prawym przyciskiem myszy **punktów końcowych** węzeł i wybierz polecenie "**nowy punkt końcowy usługi**".  
  
#### <a name="editing-a-service-configuration"></a>Edytowanie konfiguracji usługi  
  
1. Kliknij przycisk **usługi** węzła.  
  
2. Edytuj ustawienia siatki właściwości.  
  
#### <a name="editing-a-service-endpoint-configuration"></a>Edytowanie konfiguracji punktu końcowego usługi  
  
1. Kliknij przycisk **punktu końcowego usługi** węzła.  
  
2. Edytuj ustawienia siatki właściwości.  
  
#### <a name="adding-a-base-address"></a>Dodawanie adres podstawowy  
  
1. Kliknij przycisk **hosta** węzła.  
  
2. Kliknij przycisk **nowy...** znajdujący się w **adresy podstawowy** sekcji.  
  
3. Wpisz adres podstawowy identyfikator URI w oknie dialogowym.  
  
4. Kliknij przycisk **OK**.  
  
> [!NOTE]
>  Nie można edytować wartość [ \<baseAddressPrefixFilters >](../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md) wewnątrz tego narzędzia. Aby dodać lub zmodyfikować ten element, należy użyć edytora tekstu lub programu Visual Studio.  
  
### <a name="client"></a>Klient  
 **Klienta** węzła wyświetla wszystkie punkty końcowe klienta w pliku konfiguracji. Każdy węzeł podrzędny w drzewie odnosi się do podrzędnego elementu <`client`> element pliku konfiguracji.  
  
 Po kliknięciu **klienta** węzła, można wyświetlać lub wykonywania zadań na komputerze klienckim **strony Podsumowanie** w **okienka szczegółów**.  
  
#### <a name="creating-a-new-client-endpoint-configuration"></a>Tworzenie nowej konfiguracji punktu końcowego klienta  
 Można utworzyć nowej konfiguracji punktu końcowego klienta, w następujący sposób:  
  
-   Tworzenie za pomocą kreatora: Kliknij łącze **tworzenia nowego klienta...** na **okienka zadań** w lewym dolnym rogu okna, lub **strony Podsumowanie** Aby uruchomić kreatora. Można również wykonać dlatego w **pliku** menu -> **Dodaj nowy element**. Kreator monituje wskaż lokalizację konfiguracji usługi, z którego jest generowany konfiguracji klienta. Następnie można połączyć się z punktem końcowym usługi.  
  
-   Ręczne tworzenie: Kliknij prawym przyciskiem myszy **punktów końcowych** węźle **klienta**i wybierz polecenie **nowy punkt końcowy klienta**.  
  
#### <a name="editing-a-client-endpoint-configuration"></a>Edytowanie konfiguracji punktu końcowego klienta  
  
1. Kliknij przycisk **punkt końcowy klienta** węzła.  
  
2. Edytuj ustawienia siatki właściwości.  
  
### <a name="standard-endpoint"></a>Standardowy punkt końcowy  
 Standardowe punkty końcowe są specjalne punktów końcowych, którzy mają jeden lub inne aspekty adresu, kontrakt i powiązania ustawione wartości domyślne.  
  
 Takie ustawienia konfiguracji są przechowywane w **standardowy punkt końcowy** węzła. **Standardowy punkt końcowy** węzeł zawiera wszystkie ustawienia standardowy punkt końcowy w pliku konfiguracji. Każdy węzeł podrzędny w drzewie odnosi się do elementu podrzędnego w `<standardEndpoints>` elementu w pliku konfiguracji.  
  
 Po kliknięciu **standardowy punkt końcowy** węzła, można wyświetlać lub wykonywania zadań na standardowy punkt końcowy **strony Podsumowanie** w **okienka szczegółów**.  
  
#### <a name="creating-a-new-standard-endpoint-configuration"></a>Tworzenie nowej konfiguracji standardowy punkt końcowy  
 Nowa konfiguracja standardowego punktu końcowego można utworzyć w następujący sposób:  
  
-   Kliknij prawym przyciskiem myszy **standardowy punkt końcowy** a następnie wybierz węzeł **nowe standardowej konfiguracji punktu końcowego...** Wybierz typ powiązania w oknie dialogowym i kliknij **OK**.  
  
-   Wybierz **standardowy punkt końcowy** węzła i kliknij przycisk **nowe standardowej konfiguracji punktu końcowego...** w **okienka zadań** w lewym dolnym rogu okna.  
  
 **Tworzenie Nowy standardowy punkt końcowy** Wyświetla okno dialogowe i wyświetla listę wszystkich zarejestrowanych typów standardowy punkt końcowy.  
  
#### <a name="viewing-and-editing-a-standard-endpoint-configuration"></a>Wyświetlanie i edytowanie konfiguracji standardowy punkt końcowy  
 Można otworzyć konfiguracji standardowy punkt końcowy do wyświetlania i edytowania w następujący sposób:  
  
-   Kliknij, aby rozwinąć **standardowy punkt końcowy** węzła i kliknij węzeł podrzędny odpowiednich punktu końcowego.  
  
-   Kliknij przycisk **standardowy punkt końcowy** węzła i kliknij odpowiedni punkt końcowy, w okienku szczegółów.  
  
 Atrybuty dla punktu końcowego są wyświetlane w okienku po prawej stronie do edycji.  
  
#### <a name="deleting-a-standard-endpoint-configuration"></a>Usuwanie konfiguracji standardowy punkt końcowy  
 Usuń z konfiguracji standardowy punkt końcowy, w następujący sposób:  
  
-   Kliknij, aby rozwinąć **standardowy punkt końcowy** węzła i kliknij prawym przyciskiem myszy węzeł podrzędny odpowiednich punktu końcowego. Użyć polecenia kontekstowego **Usuń standardowej konfiguracji punktu końcowego** można usunąć punktu końcowego.  
  
-   Kliknij przycisk **standardowy punkt końcowy** węzła. W **zadań** okienku kliknij **Usuń standardowej konfiguracji punktu końcowego**.  
  
 Jeżeli standardowy punkt końcowy w zastosowano, podczas próby usunięcia go jest wyświetlany komunikat ostrzegawczy: **Standardowy punkt końcowy jest używany. Jeśli usuniesz je teraz, należy koniecznie Usuń wszystkie odniesienia w innych częściach elementów konfiguracji (na przykład w punkt końcowy usługi lub punkt końcowy klienta). W przeciwnym razie konfiguracja jest nieprawidłowy i nie można otworzyć następnym razem. Czy na pewno chcesz usunąć standardowy punkt końcowy?"**  
  
### <a name="binding"></a>Wiązanie  
 Konfiguracji powiązania są używane do konfigurowania wiązania dla punktów końcowych. Takie ustawienia konfiguracji są przechowywane w **powiązanie** węzła. Punkty końcowe odwoływać konfiguracji powiązania przy użyciu nazwy i wiele punktów końcowych można odwoływać się do konfiguracji pojedynczego powiązania.  
  
 **Powiązania** węzeł zawiera wszystkie ustawienia powiązania w pliku konfiguracji. Każdy węzeł podrzędny w drzewie odnosi się do elementu podrzędnego w <`bindings`> element pliku konfiguracji.  
  
 Po kliknięciu **powiązania** węzła, można wyświetlać lub wykonywania zadań w powiązaniu **strony Podsumowanie** w **okienka szczegółów**.  
  
#### <a name="creating-a-new-binding-configuration"></a>Tworzenie nowej konfiguracji powiązania  
 Można utworzyć nową konfigurację powiązania w następujący sposób.  
  
-   Kliknij prawym przyciskiem myszy **powiązania** a następnie wybierz węzeł **nowej konfiguracji powiązania**... Wybierz typ powiązania w oknie dialogowym i kliknij **OK**.  
  
-   Wybierz **powiązania** węzła i kliknij przycisk **nowej konfiguracji powiązania**... w **okienka zadań** w lewym dolnym rogu okna.  
  
-   Na stronie podsumowania usługi lub klienta kliknij **kliknij, aby tworzenie** w **Konfiguracja powiązania** pola, aby utworzyć konfigurację powiązania dla odpowiedniego punktu końcowego.  
  
#### <a name="adding-binding-element-extensions-to-a-custom-binding"></a>Dodawanie powiązania rozszerzeń elementów do niestandardowego powiązania  
  
1. Wybierz powiązanie ma zostać dodany element rozszerzenia.  
  
2. Kliknij przycisk **Dodaj**.  
  
3. Z listy dostępnych rozszerzeń wybierz rozszerzenie elementu powiązania, które chcesz dodać. Aby wybrać wiele elementów, naciśnij jednocześnie klawisz CTRL.  
  
4. Kliknij przycisk **Dodaj**.  
  
#### <a name="adjusting-the-extension-position-in-a-custom-binding"></a>Dostosowania pozycji rozszerzenia w niestandardowym powiązaniu  
 Powiązanie niestandardowe jest kolekcją elementów, które tworzą stos wiązania. Każdy element powiązania na stosie ma swoje własne ustawienia konfiguracji. Kolejność rozszerzeń elementów powiązania w niestandardowym powiązaniu wskazuje ich pozycji w stosie. Najpierw stosowane są elementy w górnej części stosu. Aby zmienić kolejność:  
  
1. Wybierz węzeł niestandardowego powiązania.  
  
2. Wybierz jeden element rozszerzenia powiązania w **pozycja rozszerzenia elementu powiązania** sekcji.  
  
3. Użyj **się** lub **dół** przycisku po lewej stronie na liście, aby zmienić położenie wybranego elementu.  
  
#### <a name="editing-the-configuration-of-binding-element-extensions-in-a-custom-binding"></a>Edytowanie konfiguracji powiązania rozszerzeń elementów w niestandardowym powiązaniu  
  
1. Wybierz węzeł powiązania w drzewie.  
  
2. Wybierz niestandardowego powiązania, który zawiera element, który chcesz edytować.  
  
3. Wybierz rozszerzenie elementu powiązania, który chcesz edytować. Ustawienia elementu są wyświetlane w okienku po prawej stronie, na którym można edytować.  
  
### <a name="diagnostics"></a>Diagnostyka  
 **Diagnostyki** węźle są wyświetlane wszystkie ustawienia diagnostyczne w pliku konfiguracji. Pozwala ona włączyć liczniki wydajności, lub wyłączyć, włączyć lub wyłączyć Instrumentacji zarządzania Windows (WMI), skonfigurować śledzenie programu WCF i konfigurowanie rejestrowania komunikatów WCF. Ustawienia w **diagnostyki** odpowiadają węzeł <`system.diagnostics`> sekcji, i `<diagnostics>` sekcji `<system.serviceModel>` w pliku konfiguracji.  
  
 Po kliknięciu **diagnostyki** węzła, można wyświetlać lub wykonywania zadań na diagnostyki **strony Podsumowanie** w **okienka szczegółów**.  
  
#### <a name="configuring-performance-counters-and-wmi"></a>Konfigurowanie i liczniki wydajności usługi WMI  
  
1. Kliknij przycisk **diagnostyki** węzła.  
  
2. Kliknij przycisk **Przełącz liczniki wydajności**. Licznik wydajności ma trzy stany: Wyłączone (domyślnie) ServiceOnly, a wszystkie. Kliknięcie łącza Włącza lub wyłącza ustawienie między te trzy stany.  
  
#### <a name="configuring-wmi-provider"></a>Konfigurowanie dostawcy WMI  
  
1. Kliknij przycisk **diagnostyki** węzła.  
  
2. Aby umożliwić dostawcy usługi WMI, kliknij **Włącz dostawcę WMI** łącza.  
  
#### <a name="enabling-wcf-tracing"></a>Włączanie śledzenia WCF  
 Można utworzyć pliku śledzenia WCF za pomocą właściwości standardowe lub skonfigurować niestandardowy plik śledzenia.  
  
1. Kliknij przycisk **diagnostyki** węzła.  
  
2. Kliknij przycisk **włączyć śledzenie**.  
  
3. Kliknij przycisk **poziom śledzenia** link, aby dostosować poziom śledzenia. Istnieje sześć poziomów śledzenia: Wyłączone, krytyczny, błąd, ostrzeżenie, informacje i szczegółowe informacje. **Śledzenie aktywności** i **Propagacja działania** opcji umożliwiają korzystanie z funkcji śledzenia działań usługi WCF.  
  
4. Kliknij nazwę odbiornika śledzenia, aby określić opcje i plik śledzenia.  
  
#### <a name="enabling-wcf-logging"></a>Włączanie rejestrowania programu WCF  
 Można utworzyć pliku śledzenia WCF za pomocą właściwości standardowe lub skonfigurować niestandardowy plik śledzenia.  
  
1. Kliknij przycisk **diagnostyki** węzła.  
  
2. Kliknij przycisk **włączyć rejestrowanie komunikatów**.  
  
3. Kliknij przycisk **poziom dziennika** link, aby dostosować poziom dziennika. Istnieją trzy poziomy dziennika: Źle sformułowane, usług i mechanizm transportu.  
  
4. Kliknij nazwę odbiornika, aby określić opcje i pliku dziennika.  
  
> [!NOTE]
>  Jeśli chcesz, aby dzienniki śledzenia i wiadomości, aby było opróżnić automatycznie po zamknięciu aplikacji, należy włączyć **automatyczne opróżnianie** opcji.  
  
 **Diagnostyki** **strony Podsumowanie** umożliwia wykonywanie typowych zadań w Konfigurowanie diagnostyki. Jednakże, jeśli chcesz ręcznie zmodyfikować ustawienia źródeł i odbiorników, należy rozwinąć **diagnostyki** węzła i Edytuj ustawienia w **rejestrowania komunikatów**, **odbiorników** i **Źródeł** węzła.  
  
#### <a name="enabling-wcf-custom-tracing-or-message-logging"></a>Włączanie śledzenia niestandardowe WCF lub rejestrowanie komunikatów  
  
1. Kliknij przycisk **diagnostyki** węzeł i rozwiń go.  
  
2. Kliknij prawym przyciskiem myszy **odbiorników** a następnie wybierz węzeł **nowy odbiornik**.  
  
3. Wpisz nazwę pliku śledzenia w **InitData** pola. Możesz kliknąć pozycję "..." przycisk, aby przejść do ścieżki.  
  
4. Klikając **TypeName** wiersz wyświetla "..." przycisk. Kliknij ten przycisk, aby otworzyć **przeglądarki typ odbiornik śledzenia**, którym można znaleźć detektorów śledzenia wstępnie skonfigurowane, które są już zainstalowane.  
  
5. Uwaga **źródła** sekcji. Kliknij przycisk **Dodaj** w tej sekcji, aby otworzyć okno dialogowe z menu rozwijanego, który zawiera listę źródeł dostępnych śledzenia. Wybierz źródło śledzenia, a następnie kliknij przycisk **OK**.  
  
6. Aby edytować ustawienia rejestrowania komunikatów, kliknij przycisk **rejestrowania komunikatów** węzła. Można edytować ustawienia w siatce właściwości.  
  
### <a name="advanced"></a>Zaawansowane  
  
#### <a name="behaviors"></a>Zachowania  
 **Zachowania** węzeł zawiera zachowania, które są obecnie zdefiniowane w pliku konfiguracji.  
  
 Zachowanie konfiguracji są używane do konfigurowania zachowania punktów końcowych i usług. Takie ustawienia konfiguracji są przechowywane w **zaawansowane** węźle **zachowania usług** i **zachowań punktu końcowego**. Zachowania usług są używane przez usługi; natomiast zachowań punktu końcowego przez punkty końcowe.  
  
 Zachowania to zbiór elementów rozszerzeń dla stosu. Najpierw stosowany jest element w górę stosu. Każdy element rozszerzenia może mieć własną konfigurację.  
  
##### <a name="creating-a-new-behavior-configuration"></a>Tworzenie nowej konfiguracji zachowanie  
 Można utworzyć nową konfigurację zachowania na dwa sposoby.  
  
-   Kliknij prawym przyciskiem myszy jeden z węzłów zachowania, a następnie wybierz pozycję "**nowej konfiguracji zachowanie...**  
  
-   Wybierz jeden z węzłów zachowania, a następnie kliknij przycisk **nowej konfiguracji zachowanie**... w **okienka zadań** w lewym dolnym rogu okna.  
  
##### <a name="adding-behavior-element-extensions-to-a-behavior"></a>Dodawanie zachowania rozszerzeń elementów do zachowania  
  
1. Wybierz jeden z węzłów zachowania.  
  
2. Wybierz żądane zachowanie edycji.  
  
3. Kliknij przycisk **Dodaj**.  
  
4. Z listy dostępnych rozszerzeń wybierz element rozszerzenia zachowania, które chcesz dodać.  
  
5. Kliknij przycisk **Dodaj**.  
  
##### <a name="adjusting-the-extension-position-in-a-behavior"></a>Dostosowania pozycji rozszerzenia w działaniu  
 Zachowania są kolekcjami elementów, które tworzą stos. Każdy element na stosie ma własną konfigurację. Kolejność rozszerzeń elementów zachowanie w zachowaniu wskazuje ich pozycji w stosie. Najpierw stosowane są elementy w górnej części stosu. Aby zmienić kolejność:  
  
1. Wybierz jeden z węzłów zachowania.  
  
2. Wybierz żądane zachowanie edycji.  
  
3. Wybierz zachowanie elementu rozszerzenia w **pozycja rozszerzenia elementu zachowanie** sekcji.  
  
4. Użyj **się** lub **dół** przycisku po lewej stronie na liście, aby zmienić położenie wybranego elementu.  
  
##### <a name="editing-the-configuration-of-behavior-element-extensions"></a>Edytowanie konfiguracji zachowanie elementu rozszerzeń  
  
1. Wybierz jeden z węzłów zachowania w drzewie.  
  
2. Wybierz zachowanie, który zawiera element, który chcesz edytować.  
  
3. Wybierz rozszerzenie elementu zachowanie, które chcesz edytować. Ustawienia elementu są wyświetlane w okienku po prawej stronie, na którym można edytować.  
  
#### <a name="protocolmapping"></a>protocolMapping  
 Ta sekcja umożliwia ustawiania domyślnych typów powiązań dla różnych protokołów, takich jak http, tcp, usługi MSMQ lub net.pipe za pośrednictwem zdefiniowanych mapowanie między Schematy adresów protokołu i możliwości wiązania. Można również dodać nowe mapowania do innych protokołów.  
  
#### <a name="extensions"></a>Rozszerzenia  
 Nowe rozszerzenia powiązania, rozszerzeń element powiązania, rozszerzenia standardowy punkt końcowy i rozszerzenia zachowania można zarejestrować do użytku w konfiguracji usługi WCF. Rozszerzenia są pary nazwa/typu. Nazwa definiuje nazwę rozszerzenia w konfiguracji, natomiast typ implementuje rozszerzenie. Istnieją cztery typy rozszerzeń:  
  
-   Rozszerzeń powiązania zdefiniować typ całej powiązania. Przykład: `basicHttpBinding`.  
  
-   Rozszerzenia elementu powiązania zdefiniować element powiązania. Przykład: `textMessageEncoding`.  
  
-   Standardowy punkt końcowy rozszerzenia definiować całej standardowy punkt końcowy. Przykład: `discoveryEndpoint`.  
  
-   Zachowanie elementu rozszerzenia zdefiniować element zachowanie. Przykład: `clientVia`.  
  
 Rozszerzenia, które zostały zarejestrowane w konfiguracji mogą być używane jak jakikolwiek inny składnik WCF tego samego typu.  
  
##### <a name="adding-a-new-extension"></a>Dodawanie nowego rozszerzenia  
 Wybierz jeden z węzłów rozszerzenia w węzłach zaawansowane:  
  
1. Kliknij przycisk **Nowy**.  
  
2. Wprowadź nazwę i typ.  
  
3. Kliknij przycisk **OK**.  
  
4. Rozszerzenie jest teraz wyświetlany w odpowiednim miejscu w edytorze. Na przykład jeśli dodasz rozszerzenia elementu zachowania, wydaje się na liście dostępnych rozszerzeń.  
  
#### <a name="hosting-environment"></a>Środowisko hostingu  
 W tej sekcji pozwala zdefiniować ustawienia podczas tworzenia wystąpienia usługi Środowisko hostingu.  
  
### <a name="creating-a-configuration-file-using-the-wizard"></a>Tworzenie pliku konfiguracji, za pomocą Kreatora  
 Jednym ze sposobów tworzenia nowego pliku konfiguracji jest za pomocą Kreatora nowej Element usługi. Kreator znajduje typy zainstalowanych usług i innych elementów zgodnych z programem WCF na komputerze, łącznie z modelu COM + i -internetowej katalogów wirtualnych i ładuje je w celu tworzenia konfiguracji znacznie bardziej bezproblemowe.  
  
#### <a name="creating-a-configuration-file"></a>Tworzenie pliku konfiguracji  
  
1. Uruchom Edytor konfiguracji usługi za pomocą okno polecenia przejdź do lokalizacji instalacji usługi WCF, a następnie wpisz `SvcConfigEditor.exe`.  
  
2. Z **pliku** menu, wybierz opcję **Otwórz** i kliknij przycisk **plik wykonywalny**, **usług COM +**, lub **usługi WebHosted**, w zależności od typu pliku konfiguracji, którą chcesz utworzyć.  
  
3. W **Otwórz** okno dialogowe, przejdź do określonego pliku, aby utworzyć plik konfiguracji, a następnie kliknij go dwukrotnie.  
  
4. W **pliku** menu wskaż **Dodaj nowy element** i kliknij przycisk **usługi**. Zostanie otwarty Kreator nowego elementu usługi.  
  
5. Postępuj zgodnie z instrukcjami w kreatorze, aby utworzyć nową usługę.  
  
> [!NOTE]
>  Jeśli chcesz użyć NetPeerTcpBinding z pliku konfiguracji, generowane przez kreatora, musisz ręcznie dodać element konfiguracji powiązanie i modyfikowanie `mode` atrybutu jego `security` elementu "None".  
  
## <a name="configuring-com"></a>Konfigurowanie modelu COM +  
 Edytor konfiguracji usługi umożliwia utworzenie nowego pliku konfiguracji dla istniejącej aplikacji modelu COM + lub edytowanie istniejącej konfiguracji modelu COM +. **Kontraktu COM** węzeł jest widoczny tylko wtedy gdy <`comContract`> sekcja istnieje w pliku konfiguracji.  
  
### <a name="creating-a-new-com-configuration"></a>Tworzenie nowej konfiguracji modelu COM +  
 Przed utworzeniem nowej konfiguracji modelu COM +, upewnij się, że jest zainstalowany w usługi składowe aplikacji COM +, a zarejestrowany w globalnej pamięci podręcznej zestawów (GAC).  
  
1. Wybierz **pliku** menu -> **integracja** -> **aplikacji COM +.** Ta operacja powoduje zamknięcie bieżącego otwartego pliku. Jeśli jest to niezapisanych danych w bieżącym pliku, pojawi się okno dialogowe Zapisz. **Kreatora integracji modelu COM +** jest następnie uruchamiany.  
  
2. Na pierwszej stronie należy wybrać aplikacji COM + z drzewa. Jeśli nie możesz znaleźć aplikacji COM + w drzewie, sprawdź, czy jest zainstalowany w usługach składowych i zarejestrowane w globalnej pamięci podręcznej zestawów (GAC).  
  
3. Na następnej stronie Wybierz metody, która ma zostać uwidoczniona jako usługi WCF. Obsługiwane metody w aplikacji COM + są wyświetlane i zaznaczone domyślnie.  
  
4. Wybierz metodę hostingu.  
  
5. Skonfiguruj inne ustawienia zgodnie z przewodników w kreatorze.  
  
6. Edytor konfiguracji usługi wykorzystuje ComSvcConfig.exe w tle, aby wygenerować plik konfiguracji. Po zakończeniu tego procesu możesz wyświetlić podsumowanie i Zakończ pracę kreatora. Plik wygenerowaną konfigurację jest otwarty, tak aby można go edytować bezpośrednio.  
  
### <a name="editing-an-existing-com-configuration"></a>Edytowanie istniejącej konfiguracji modelu COM +  
  
1. Wybierz **pliku** menu -> **Otwórz** -> **usług COM +**...  
  
2. Wybierz usługę modelu COM + do edycji z listy.  
  
3. Edytuj ustawienia konfiguracji w **kontrakty COM** węzła.  
  
    > [!NOTE]
    >  Możesz także bezpośrednio otwierać i edytować plik konfiguracji, który zawiera kontrakty COM.  
  
## <a name="security"></a>Zabezpieczenia  
 Plik konfiguracji usługi generowane przez Edytor konfiguracji nie gwarantuje bezpieczeństwa. Zapoznaj się [zabezpieczeń](../../../docs/framework/wcf/feature-details/security.md) dokumentację, aby dowiedzieć się, jak zabezpieczyć usług WCF.  
  
 Ponadto Edytor konfiguracji tylko może służyć do odczytu i zapisu prawidłowe elementy konfiguracji programu WCF. Narzędzie ignoruje elementy zgodny ze schematem, zdefiniowane przez użytkownika. Ponadto nie będzie podejmował Usuń te elementy z konfiguracji pliku lub określić ich wpływu na znane elementów usług WCF. Odpowiada użytkownika do określenia, czy te elementy stanowią zagrożenie dla aplikacji lub systemu.
