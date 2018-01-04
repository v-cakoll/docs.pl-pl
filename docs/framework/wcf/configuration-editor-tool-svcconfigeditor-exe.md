---
title: "Narzędzie edytora konfiguracji (SvcConfigEditor.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuration files, creating
- configuration files
- Configuration file
- configuration file schema
ms.assetid: 2db21a57-5f64-426f-89df-fb0dc2d2def5
caps.latest.revision: "45"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e21dacd5f01ba956ba78456b8e325d0b7e767df7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="configuration-editor-tool-svcconfigeditorexe"></a>Narzędzie edytora konfiguracji (SvcConfigEditor.exe)
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] Usługi edytora konfiguracji (SvcConfigEditor.exe) umożliwia administratorów i deweloperów, tworzenie i modyfikowanie ustawień konfiguracji [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usług przy użyciu graficznego interfejsu użytkownika. Z tego narzędzia można zarządzać ustawieniami dla [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] powiązania zachowania, usług i diagnostyki bez konieczności bezpośredniego edytowania plików XML konfiguracji.  
  
 Edytor konfiguracji usługi znajdują się w folderze C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin.  
  
## <a name="the-wcf-configuration-editor"></a>Edytor konfiguracji usługi WCF  
 Edytor konfiguracji usługi jest dostarczany za pomocą kreatora, który przeprowadzi Cię przez kroki konfigurowania [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi lub klienta. Zdecydowanie zaleca się bezpośrednio za pomocą Kreatora zamiast edytora.  
  
 Jeśli masz już pewne pliki konfiguracyjne, które są zgodne ze schematem System.Configuration standardowe, można zarządzać ustawienia specyficzne dla powiązania, zachowanie, usług i diagnostyki przy użyciu interfejsu użytkownika. Edytor konfiguracji usługi umożliwia zarządzanie ustawieniami dla istniejących [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] plików konfiguracji oraz pliki wykonywalne, usług COM + i usług hostowanych w sieci Web. Podczas otwierania hostowanych w sieci Web usługi z usługi konfiguracji edytora, zarówno usługę własnych konfiguracji i sekcje dziedziczone konfiguracje węzłów górnego poziomu są wyświetlane.  
  
 Ponieważ [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] ustawienia konfiguracyjne znajdują się w `<system.serviceModel>` sekcji pliku konfiguracji, Edytor działa wyłącznie na zawartość tego elementu i nie dostępu do innych elementów w tym samym pliku. Można przejść do istniejących plików konfiguracyjnych bezpośrednio lub możesz wybrać zestaw, który zawiera usługę, katalog wirtualny lub usług COM +. Edytor ładuje plik konfiguracji dla określonej usługi i zezwala użytkownikowi na dodawanie nowych elementów albo edytowania istniejących elementów zagnieżdżonych w `<system.serviceModel>` sekcji pliku konfiguracji.  
  
 Edytor obsługuje funkcję IntelliSense i wymusza zgodność schematu. Dane wyjściowe jest gwarantowana zgodne ze schematem pliku konfiguracji i poprawna składniowo danych wartości. Jednak Edytor nie gwarantuje, że plik konfiguracji jest semantycznie nieprawidłowy. Innymi słowy edytor nie gwarantuje, że plik konfiguracji można pracować z usługą, który konfiguruje.  
  
> [!CAUTION]
>  Edytor nie może przeczyścić element konfiguracji z pliku konfiguracji po zmodyfikowaniu elementu. Na przykład jeśli używasz edytora Ustaw nazwę punktu końcowego niepustym ciągiem i zapisać ją plik konfiguracji ma następującą zawartość, jak pokazano w poniższym przykładzie.  
>   
>  `<endpoint binding="basicHttpBinding" name="somename" />`  
>   
>  Próba usunięcia nazwy przez ustawienie jej na ciąg pusty, a następnie zapisz plik nadal plik konfiguracji zawiera `name` atrybutu, jak pokazano w poniższym przykładzie.  
>   
>  `<endpoint binding="basicHttpBinding" name="" />`  
>   
>  Aby przeczyścić atrybutu, należy ręcznie zmienić element przy użyciu innego edytora tekstu.  
>   
>  Należy zachować ostrożność szczególnie ten problem, korzystając z `issueToken` elementu `clientCredential` zachowania punktu końcowego. W szczególności `address` atrybutu jego `localIssuer` podelementu, nie może być pustym ciągiem. Jeśli zmodyfikowano `address` atrybutu za pomocą edytora konfiguracji i chcesz całkowicie usunąć, należy zrobić przy użyciu narzędzia innego niż edytora. W przeciwnym razie wartość atrybutu zawiera pusty ciąg, a aplikacja zgłasza wyjątek.  
  
## <a name="using-the-configuration-editor"></a>Za pomocą edytora konfiguracji  
 Edytor konfiguracji usługi można znaleźć w następującej lokalizacji instalacji zestawu Windows SDK:  
  
 C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin\SvcConfigEditor.exe  
  
 Po uruchomieniu edytora konfiguracji usługi można użyć **plik i Otwórz** menu do przeglądania dla usługi lub zestawu, którymi chcesz zarządzać. Można otworzyć plików konfiguracyjnych bezpośrednio, wyszukaj [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] /COM+ usługi i pliki konfiguracyjne otwarty dla usług hostowanych w sieci Web.  
  
 Interfejs użytkownika edytora konfiguracji usługi jest podzielona na następujące obszary:  
  
-   Okienka widoku drzewa, który zawiera elementy konfiguracji w strukturze drzewa po lewej stronie. W drzewie mogą wykonywać operacje, klikając prawym przyciskiem myszy węzły.  
  
-   Okienka zadań, który zawiera typowe zadania związane z bieżącym elementów na dolnym rogu okna  
  
-   Okienko Szczegóły są wyświetlane szczegółowe ustawienia konfiguracji węzła wybranego w widoku drzewa po prawej stronie.  
  
### <a name="opening-a-configuration-file"></a>Otwieranie pliku konfiguracji  
  
1.  Uruchom Edytor konfiguracji usługi przy użyciu okna polecenia, aby przejść do Twojej [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] lokalizacja instalacji, a następnie wpisz `SvcConfigEditor.exe`.  
  
2.  Z **pliku** menu, wybierz opcję **Otwórz** i wybierz typ pliku, w którym chcesz zarządzać.  
  
3.  W **Otwórz** okno dialogowe, przejdź do określonego pliku chcesz zarządzać i kliknij ją dwukrotnie.  
  
 Podgląd komunikatów o następuje ścieżki scalania konfiguracji i automatycznie tworzy widok scalony konfiguracji. Na przykład rzeczywista konfiguracja-hostowanej usługi jest kombinacją Machine.config i App.config. Wszelkie zmiany są stosowane do aktywnego pliku w SvcConfigEditor. Jeśli chcesz edytować określonego pliku w ścieżce scalania konfiguracji, należy otworzyć go bezpośrednio.  
  
> [!NOTE]
>  Edytor konfiguracji ponowne załadowanie pliku konfiguracji aktualnie otwarty podczas jego został zmodyfikowany poza edytorem. W takim przypadku wszystkie zmiany, które nie są zapisywane trwale wewnątrz edytora zostaną utracone. Ponowne ładowanie sytuacji spójnie najbardziej prawdopodobną przyczyną jest to usługa, która stale uzyskuje dostęp do pliku konfiguracji, na przykład oprogramowanie antywirusowe uruchomione w tle. Aby rozwiązać ten problem, upewnij się, że edytor konfiguracji jest tylko proces, który można uzyskać dostępu do pliku, gdy jest otwarty.  
  
### <a name="services"></a>Usługi  
 **Usług** węzeł zawiera wszystkie aktualnie przypisane w pliku konfiguracji usługi. Każdy węzeł podrzędny w drzewie odnosi się do elementu podrzędnego elementu <`services`> w pliku konfiguracji.  
  
 Po kliknięciu **usług** węzeł, aby wyświetlić lub wykonać zadania w usłudze w obszarze Podsumowanie **szczegółów** okienka.  
  
#### <a name="creating-a-new-service-configuration"></a>Tworzenie nowej konfiguracji usługi  
 Nową konfigurację usługi można utworzyć w następujący sposób:  
  
-   Przy użyciu kreatora: kliknij łącze **Utwórz nową usługę...** w okienku zadań lub na stronie Podsumowanie, które można uruchomić kreatora. Można również wykonać dlatego w **pliku** -> menu **Dodaj nowy element**.  
  
-   Utwórz ręcznie: kliknąć prawym przyciskiem myszy **usług** węzeł i wybierz polecenie **nową usługę**.  
  
#### <a name="creating-a-new-service-endpoint-configuration"></a>Tworzenie nowej konfiguracji punktu końcowego usługi  
 Można utworzyć nową konfigurację punktu końcowego usługi, w następujący sposób:  
  
-   Tworzenie przy użyciu kreatora: kliknij łącze **utworzyć nowy punkt końcowy usługi...** w okienku zadań lub na stronie Podsumowanie, które można uruchomić kreatora. Można również wykonać dlatego w **pliku** -> menu **Dodaj nowy element**.  
  
-   Utwórz ręcznie: po utworzeniu usługi, należy kliknąć prawym przyciskiem myszy **punkty końcowe** węzeł i wybierz polecenie "**nowy punkt końcowy usługi**".  
  
#### <a name="editing-a-service-configuration"></a>Edytowanie konfiguracji usługi  
  
1.  Kliknij przycisk **usługi** węzła.  
  
2.  Edytuj ustawienia siatki właściwości.  
  
#### <a name="editing-a-service-endpoint-configuration"></a>Edytowanie konfiguracji punktu końcowego usługi  
  
1.  Kliknij przycisk **punktu końcowego usługi** węzła.  
  
2.  Edytuj ustawienia siatki właściwości.  
  
#### <a name="adding-a-base-address"></a>Dodawanie adres podstawowy  
  
1.  Kliknij przycisk **hosta** węzła.  
  
2.  Kliknij przycisk **nowych...** przycisk **adresy Base** sekcji.  
  
3.  Wpisz adres podstawowy identyfikator URI w oknie dialogowym.  
  
4.  Kliknij przycisk **OK**.  
  
> [!NOTE]
>  Nie można edytować wartość [ \<baseAddressPrefixFilters >](../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md) wewnątrz tego narzędzia. Aby dodać lub zmodyfikować ten element, należy użyć edytora tekstu lub [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
### <a name="client"></a>Klient  
 **Klienta** węzeł Wyświetla wszystkie punkty końcowe klienta w pliku konfiguracji. Każdy węzeł podrzędny w drzewie odnosi się do elementu podrzędnego elementu <`client`> w pliku konfiguracji.  
  
 Po kliknięciu **klienta** węzła, można wyświetlić lub wykonać zadania na kliencie **na stronie Podsumowanie** w **okienka szczegółów**.  
  
#### <a name="creating-a-new-client-endpoint-configuration"></a>Tworzenie nowej konfiguracji punktu końcowego klienta  
 Można utworzyć nowej konfiguracji punktu końcowego klienta w następujący sposób:  
  
-   Tworzenie za pomocą kreatora: kliknij łącze **tworzenia nowego klienta...** na **okienka zadań** na dolnym rogu okna, lub **na stronie Podsumowanie** Aby uruchomić kreatora. Można również wykonać dlatego w **pliku** -> menu **Dodaj nowy element**. Kreator wyświetli monit wskaż lokalizację konfiguracji usługi, z którego konfiguracja klienta jest generowany. Następnie możesz punktu końcowego usługi, aby nawiązać połączenie.  
  
-   Utwórz ręcznie: kliknij prawym przyciskiem myszy **punkty końcowe** węźle **klienta**i wybierz polecenie **nowego klienta punktu końcowego**.  
  
#### <a name="editing-a-client-endpoint-configuration"></a>Edytowanie konfiguracji punktu końcowego klienta  
  
1.  Kliknij przycisk **punktu końcowego klienta** węzła.  
  
2.  Edytuj ustawienia siatki właściwości.  
  
### <a name="standard-endpoint"></a>Standardowy punkt końcowy  
 Standardowych punktów końcowych są specjalne punkty końcowe, które mają jeden lub więcej aspektów adres, kontrakt i powiązanie ustawić wartości domyślne.  
  
 Takie ustawienia konfiguracji są przechowywane w **standardowy punkt końcowy** węzła. **Standardowy punkt końcowy** węzeł zawiera wszystkie ustawienia standardowy punkt końcowy w pliku konfiguracji. Każdy węzeł podrzędny w drzewie odnosi się do elementu podrzędnego w `<standardEndpoints>` w pliku konfiguracji.  
  
 Po kliknięciu **standardowy punkt końcowy** węzła, można wyświetlić lub wykonać zadania na standardowy punkt końcowy **na stronie Podsumowanie** w **okienka szczegółów**.  
  
#### <a name="creating-a-new-standard-endpoint-configuration"></a>Tworzenie nowej konfiguracji standardowego punktu końcowego  
 Nowa konfiguracja standardowego punktu końcowego można utworzyć w następujący sposób:  
  
-   Kliknij prawym przyciskiem myszy **standardowy punkt końcowy** a następnie wybierz węzeł **nowe standardowej konfiguracji punktu końcowego...** Wybierz typ powiązania w oknie dialogowym i kliknij przycisk **OK**.  
  
-   Wybierz **standardowy punkt końcowy** węzeł i kliknij przycisk **nowe standardowej konfiguracji punktu końcowego...** w **okienka zadań** na dolnym rogu okna.  
  
 **Tworzenie Nowy standardowy punkt końcowy** okno dialogowe wyświetla i wyświetla listę wszystkich zarejestrowanych typów standardowego punktu końcowego.  
  
#### <a name="viewing-and-editing-a-standard-endpoint-configuration"></a>Wyświetlanie i edytowanie Konfiguracja standardowego punktu końcowego  
 Można otworzyć konfiguracji standardowy punkt końcowy do wyświetlania i edytowania w następujący sposób:  
  
-   Kliknij, aby rozwinąć **standardowy punkt końcowy** węzeł i kliknij węzeł podrzędny odpowiednich punktu końcowego.  
  
-   Kliknij przycisk **standardowy punkt końcowy** węzeł i kliknij odpowiedni punkt końcowy w okienku szczegółów.  
  
 Atrybuty dla punktu końcowego są wyświetlane w okienku po prawej stronie do edycji.  
  
#### <a name="deleting-a-standard-endpoint-configuration"></a>Usuwanie konfiguracji standardowego punktu końcowego  
 Konfiguracja standardowego punktu końcowego można usunąć w następujący sposób:  
  
-   Kliknij, aby rozwinąć **standardowy punkt końcowy** węzeł i kliknij prawym przyciskiem myszy węzeł podrzędny odpowiednich punktu końcowego. Użyj polecenia kontekstu **usunąć standardowej konfiguracji punktu końcowego** można usunąć punktu końcowego.  
  
-   Kliknij przycisk **standardowy punkt końcowy** węzła. W **zadań** okienku, kliknij przycisk **usunąć standardowej konfiguracji punktu końcowego**.  
  
 Jeśli standardowy punkt końcowy w służy, wyświetlany jest komunikat ostrzegawczy, gdy próba usunięcia: **standardowy punkt końcowy jest używany. Jeśli usuniesz teraz, koniecznie Usuń wszystkie odniesienia w innych częściach konfiguracji (na przykład w punkt końcowy usługi lub klienta punktu końcowego). W przeciwnym razie wartość konfiguracji jest nieprawidłowy i nie można otworzyć następnym razem. Czy na pewno chcesz usunąć standardowy punkt końcowy?"**  
  
### <a name="binding"></a>Powiązanie  
 Powiązanie konfiguracje są używane do konfigurowania wiązania dla punktów końcowych. Takie ustawienia konfiguracji są przechowywane w **powiązanie** węzła. Punkty końcowe odwoływania konfiguracjami powiązań według nazwy i konfiguracji jednego powiązania może odwoływać się wiele punktów końcowych.  
  
 **Powiązania** węzeł zawiera wszystkie ustawienia powiązania w pliku konfiguracji. Każdy węzeł podrzędny w drzewie odnosi się do elementu podrzędnego w <`bindings`> w pliku konfiguracji.  
  
 Po kliknięciu **powiązania** węzła, można wyświetlić lub wykonać zadania w powiązaniu **na stronie Podsumowanie** w **okienka szczegółów**.  
  
#### <a name="creating-a-new-binding-configuration"></a>Tworzenie nowej konfiguracji powiązania  
 Można utworzyć nową konfigurację powiązania w następujący sposób.  
  
-   Kliknij prawym przyciskiem myszy **powiązania** a następnie wybierz węzeł **nowej konfiguracji powiązania**... Wybierz typ powiązania w oknie dialogowym i kliknij przycisk **OK**.  
  
-   Wybierz **powiązania** węzeł i kliknij przycisk **nowej konfiguracji powiązania**... w **okienka zadań** na dolnym rogu okna.  
  
-   Na stronie Podsumowanie usługi lub klienta, kliknij przycisk **umożliwia tworzenie** w **Konfiguracja powiązania** pola, aby utworzyć konfigurację powiązania dla odpowiedniego punktu końcowego.  
  
#### <a name="adding-binding-element-extensions-to-a-custom-binding"></a>Dodawanie powiązanie rozszerzenia elementu powiązania niestandardowego  
  
1.  Wybierz chcesz dodać element rozszerzenia powiązania.  
  
2.  Kliknij przycisk **Dodaj**.  
  
3.  Z listy dostępnych rozszerzeń wybierz element rozszerzenia powiązania, które chcesz dodać. Aby wybrać wiele elementów, naciśnij jednocześnie klawisz CTRL.  
  
4.  Kliknij przycisk **Dodaj**.  
  
#### <a name="adjusting-the-extension-position-in-a-custom-binding"></a>Dostosowania pozycji rozszerzenia powiązania niestandardowego  
 Niestandardowego powiązania jest kolekcją elementów, które tworzą stosu wiązania. Każdy element powiązania na stosie ma swoje własne ustawienia konfiguracji. Kolejność rozszerzeń element powiązania w niestandardowym powiązaniu wskazuje ich położenia na stosie. Najpierw stosowane są elementy w górę stosu. Aby zmienić kolejność:  
  
1.  Wybierz węzeł niestandardowego powiązania.  
  
2.  Wybierz jeden element rozszerzenia powiązania w **pozycja rozszerzenia elementu powiązania** sekcji.  
  
3.  Użyj **się** lub **dół** przycisku po lewej stronie na liście, aby zmienić jego położenie wybranego elementu.  
  
#### <a name="editing-the-configuration-of-binding-element-extensions-in-a-custom-binding"></a>Edytowanie konfiguracji powiązania rozszerzenia elementu powiązania niestandardowego  
  
1.  Wybierz węzeł powiązania w drzewie.  
  
2.  Wybierz niestandardowego powiązania, który zawiera element, który chcesz edytować.  
  
3.  Wybierz element rozszerzenia powiązania, który chcesz edytować. Ustawienia elementu są wyświetlane w okienku po prawej stronie, na którym można edytować.  
  
### <a name="diagnostics"></a>Diagnostyka  
 **Diagnostyki** węzeł zawiera wszystkie ustawienia diagnostyki w pliku konfiguracji. Umożliwia ona włączyć liczniki wydajności lub wyłączyć, włączyć lub wyłączyć Instrumentacji zarządzania Windows (WMI), skonfigurować [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] śledzenie i skonfigurować [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] rejestrowanie komunikatów. Ustawienia w **diagnostyki** odpowiadają węzeł <`system.diagnostics`> sekcji, i `<diagnostics>` sekcji `<system.serviceModel>` w pliku konfiguracji.  
  
 Po kliknięciu **diagnostyki** węzła, można wyświetlić lub wykonać zadania na diagnostyki **na stronie Podsumowanie** w **okienka szczegółów**.  
  
#### <a name="configuring-performance-counters-and-wmi"></a>Konfigurowanie liczników wydajności i WMI  
  
1.  Kliknij przycisk **diagnostyki** węzła.  
  
2.  Kliknij przycisk **Przełącz liczniki wydajności**. Licznik wydajności ma trzy stany: wyłączone (ustawienie domyślne), ServiceOnly, a wszystkie. Kliknięcie łącza Włącza lub wyłącza ustawienie między te trzy stany.  
  
#### <a name="configuring-wmi-provider"></a>Konfigurowanie dostawcy usługi WMI  
  
1.  Kliknij przycisk **diagnostyki** węzła.  
  
2.  Aby włączyć dostawcy usługi WMI, kliknij **włączyć dostawcy WMI** łącza.  
  
#### <a name="enabling-wcf-tracing"></a>Włączanie śledzenia WCF  
 Można utworzyć [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] śledzenia plików z właściwościami standardowe lub skonfigurować niestandardowy plik śledzenia.  
  
1.  Kliknij przycisk **diagnostyki** węzła.  
  
2.  Kliknij przycisk **włączyć śledzenie**.  
  
3.  Kliknij przycisk **poziom śledzenia** łącze, aby dostosować poziom śledzenia. Istnieją sześciu poziomy śledzenia: Wyłącz krytyczny, błąd, ostrzeżenie, informacje i pełne. **Śledzenie działania** i **propagację działania** opcji umożliwiają korzystanie [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] działania funkcji śledzenia.  
  
4.  Kliknij nazwę odbiornika śledzenia, aby określić plik śledzenia i opcje.  
  
#### <a name="enabling-wcf-logging"></a>Włączanie rejestrowania programu WCF  
 Można utworzyć [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] śledzenia plików z właściwościami standardowe lub skonfigurować niestandardowy plik śledzenia.  
  
1.  Kliknij przycisk **diagnostyki** węzła.  
  
2.  Kliknij przycisk **włączyć rejestrowanie komunikatów**.  
  
3.  Kliknij przycisk **poziom dziennika** łącze, aby dostosować poziom dziennika. Istnieją trzy dziennika poziomów: źle sformułowany, usług i mechanizm transportu.  
  
4.  Kliknij nazwę odbiornika, aby określić plik dziennika i opcje.  
  
> [!NOTE]
>  Jeśli chcesz, aby w dziennikach śledzenia i komunikat opróżniany automatycznie po zamknięciu aplikacji, Włącz **automatycznie opróżnić** opcji.  
  
 **Diagnostyki** **na stronie Podsumowanie** pozwala wykonywać typowe zadania w konfigurowaniu diagnostyki. Jednak jeśli chcesz ręcznie zmodyfikować ustawienia odbiorników i źródła, należy rozwinąć **diagnostyki** węzła i Edytuj ustawienia w **rejestrowania komunikatów**, **odbiorników** i **Źródeł** węzła.  
  
#### <a name="enabling-wcf-custom-tracing-or-message-logging"></a>Włączanie śledzenia niestandardowych WCF lub rejestrowania komunikatów  
  
1.  Kliknij przycisk **diagnostyki** węzeł i rozwiń go.  
  
2.  Kliknij prawym przyciskiem myszy **odbiorników** a następnie wybierz węzeł **nowy**.  
  
3.  Wpisz nazwę pliku śledzenia w **InitData** pola. Kliknięcie przycisku "...", aby przejść do ścieżki.  
  
4.  Kliknięcie przycisku **TypeName** wiersz zawiera przycisk "...". Kliknij ten przycisk, aby otworzyć **przeglądarki typu odbiornika śledzenia**, którym można znaleźć wstępnie skonfigurowanych obiektów nasłuchujących śledzenia są już zainstalowane.  
  
5.  Uwaga **źródła** sekcji. Kliknij przycisk **Dodaj** w tej sekcji, aby otworzyć okno dialogowe z listy rozwijanej, która zawiera źródła śledzenia dostępne. Wybierz źródło śledzenia, a następnie kliknij przycisk **OK**.  
  
6.  Aby edytować ustawienia rejestrowania komunikatów, kliknij przycisk **rejestrowania komunikatów** węzła. Można edytować ustawienia w siatce właściwości.  
  
### <a name="advanced"></a>Zaawansowane  
  
#### <a name="behaviors"></a>Zachowania  
 **Zachowania** węzeł Wyświetla zachowania, które są obecnie zdefiniowane w pliku konfiguracji.  
  
 Konfiguracje zachowanie służą do konfigurowania zachowań punktów końcowych i usług. Takie ustawienia konfiguracji są przechowywane w **zaawansowane** węźle **zachowania usługi** i **zachowania punktu końcowego**. Zachowania usług są używane przez usługi; natomiast zachowania punktu końcowego przez punkty końcowe.  
  
 Zachowania to zbiór elementów rozszerzeń dla stosu. Element w górę stosu zostanie zastosowana jako pierwsza. Każdy element rozszerzenia może mieć własną konfigurację.  
  
##### <a name="creating-a-new-behavior-configuration"></a>Tworzenie nowej konfiguracji zachowania  
 Można utworzyć nową konfigurację zachowania na dwa sposoby.  
  
-   Kliknij prawym przyciskiem myszy jeden z węzłów zachowania i wybierz opcję "**nową konfigurację zachowania...**  
  
-   Wybierz jeden z węzłów zachowanie, a następnie kliknij przycisk **nową konfigurację zachowania**... w **okienka zadań** na dolnym rogu okna.  
  
##### <a name="adding-behavior-element-extensions-to-a-behavior"></a>Dodawanie zachowania rozszerzeń elementów do zachowania  
  
1.  Wybierz jeden z węzłów zachowanie.  
  
2.  Wybierz żądane zachowanie edycji.  
  
3.  Kliknij przycisk **Dodaj**.  
  
4.  Z listy dostępnych rozszerzeń wybierz rozszerzenie elementu zachowanie, które chcesz dodać.  
  
5.  Kliknij przycisk **Dodaj**.  
  
##### <a name="adjusting-the-extension-position-in-a-behavior"></a>Dostosowania pozycji rozszerzenia w zachowanie  
 Zachowania są kolekcjami elementów, które tworzą stosu. Każdy element na stosie ma własną konfigurację. Kolejność rozszerzeń element zachowanie w zachowaniu wskazuje ich położenia na stosie. Najpierw stosowane są elementy w górę stosu. Aby zmienić kolejność:  
  
1.  Wybierz jeden z węzłów zachowanie.  
  
2.  Wybierz żądane zachowanie edycji.  
  
3.  Wybierz element rozszerzenia zachowanie w **pozycja rozszerzenia elementu zachowanie** sekcji.  
  
4.  Użyj **się** lub **dół** przycisku po lewej stronie na liście, aby zmienić jego położenie wybranego elementu.  
  
##### <a name="editing-the-configuration-of-behavior-element-extensions"></a>Edytowanie konfiguracji rozszerzenia elementu zachowanie  
  
1.  Wybierz jeden z węzłów zachowanie w drzewie.  
  
2.  Wybierz zachowanie, który zawiera element, który chcesz edytować.  
  
3.  Wybierz zachowanie rozszerzenia elementu, który chcesz edytować. Ustawienia elementu są wyświetlane w okienku po prawej stronie, na którym można edytować.  
  
#### <a name="protocolmapping"></a>ProtocolMapping  
 Ta sekcja umożliwia ustawienie domyślnego typ powiązania dla różnych protokołów, takich jak http, tcp, usługi MSMQ lub net.pipe za pośrednictwem zdefiniowanego mapowania między schematami protokołu adresu i możliwe powiązania. Można również dodać nowe mapowania do innych protokołów.  
  
#### <a name="extensions"></a>Rozszerzenia  
 Nowe powiązanie rozszerzenia, rozszerzenia elementu powiązania, rozszerzenia standardowego punktu końcowego i rozszerzenia zachowanie może być zarejestrowany do użycia w [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] konfiguracji. Rozszerzenia są pary nazwa/typu. Nazwa definiuje nazwę rozszerzenia w konfiguracji, podczas gdy typ implementuje rozszerzenia. Istnieją cztery typy rozszerzeń:  
  
-   Rozszerzenia powiązania Definiowanie typu cały powiązania. Przykład: `basicHttpBinding`.  
  
-   Rozszerzenia elementu powiązania zdefiniować element powiązania. Przykład: `textMessageEncoding`.  
  
-   Standardowy punkt końcowy rozszerzenia Zdefiniuj cały standardowy punkt końcowy. Przykład: `discoveryEndpoint`.  
  
-   Zachowanie elementu rozszerzenia zdefiniować element zachowania. Przykład: `clientVia`.  
  
 Rozszerzenia, które zostały zarejestrowane w konfiguracji można używać jak każdy inny [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] składnika tego samego typu.  
  
##### <a name="adding-a-new-extension"></a>Dodawanie nowych rozszerzeń  
 Wybierz jeden z węzłów rozszerzenia w węzłach zaawansowane:  
  
1.  Kliknij przycisk **nowe**.  
  
2.  Wprowadź nazwę i typ.  
  
3.  Kliknij przycisk **OK**.  
  
4.  Rozszerzenia jest teraz wyświetlany w odpowiednim miejscu w edytorze. Na przykład jeśli dodasz rozszerzenia elementu zachowania wydaje się na liście dostępnych rozszerzeń.  
  
#### <a name="hosting-environment"></a>Środowisko macierzyste  
 W tej sekcji można zdefiniować ustawienia wystąpienia usługi Środowisko hostingu.  
  
### <a name="creating-a-configuration-file-using-the-wizard"></a>Tworzenie pliku konfiguracji za pomocą Kreatora  
 Jednym ze sposobów tworzenia nowego pliku konfiguracji jest za pomocą Kreatora nowej Element usługi. Kreator odnajdzie typy zainstalowanej usługi i inne elementy zgodne z [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] na komputerze, w tym modelu COM + i -internetowej katalogów wirtualnych i ładuje je w celu udostępnienia Tworzenie konfiguracji bardziej uproszczone.  
  
#### <a name="creating-a-configuration-file"></a>Tworzenie pliku konfiguracji  
  
1.  Uruchom Edytor konfiguracji usługi przy użyciu okna polecenia, aby przejść do Twojej [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] lokalizacja instalacji, a następnie wpisz `SvcConfigEditor.exe`.  
  
2.  Z **pliku** menu, wybierz opcję **Otwórz** i kliknij przycisk **plik wykonywalny**, **usług COM +**, lub **usługi WebHosted**w zależności od typu pliku konfiguracji, który chcesz utworzyć.  
  
3.  W **Otwórz** okno dialogowe, przejdź do określonego pliku, który chcesz utworzyć plik konfiguracji i kliknij ją dwukrotnie.  
  
4.  W **pliku** menu wskaż **Dodaj nowy element** i kliknij przycisk **usługi**. Zostanie otwarty Kreator nowego elementu usługi.  
  
5.  Postępuj zgodnie z instrukcjami kreatora, aby utworzyć nową usługę.  
  
> [!NOTE]
>  Jeśli chcesz użyć NetPeerTcpBinding z pliku konfiguracji generowane przez kreatora, musisz ręcznie Dodaj element konfiguracji powiązanie i modyfikowanie `mode` atrybutu jego `security` elementu "None".  
  
## <a name="configuring-com"></a>Konfigurowanie modelu COM +  
 Edytor konfiguracji usługi umożliwia tworzenie nowego pliku konfiguracji dla istniejącej aplikacji COM + lub Edytuj istniejącą konfigurację modelu COM +. **Kontraktu COM** węzeł jest widoczny tylko wtedy gdy <`comContract`> sekcji istnieje w pliku konfiguracji.  
  
### <a name="creating-a-new-com-configuration"></a>Tworzenie nowej konfiguracji modelu COM +  
 Przed utworzeniem nowej konfiguracji modelu COM +, upewnij się, że jest zainstalowany w usługi składowe aplikacji COM +, a zarejestrowane w globalnej pamięci podręcznej zestawów (GAC).  
  
1.  Wybierz **pliku** -> menu **integracji** -> **aplikacji COM +.** Ta operacja powoduje zamknięcie bieżącego otwartego pliku. Jeśli jest niezapisane dane w bieżącym pliku, zostanie wyświetlone okno dialogowe Zapisz. **Kreator integracji COM +** następnie jest uruchamiana.  
  
2.  Na pierwszej stronie wybierz aplikacji COM + z drzewa. Nie można odnaleźć aplikacji COM + w drzewie, sprawdź, czy jest zainstalowany w usługach składowych i zarejestrowane w globalnej pamięci podręcznej zestawów (GAC).  
  
3.  Na następnej stronie Wybierz metody, które chcesz uwidocznić jako [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usług. Obsługiwane metody w aplikacji COM + są wyświetlane i domyślnie zaznaczone.  
  
4.  Wybierz metodę obsługi.  
  
5.  Skonfiguruj inne ustawienia zgodnie z przewodników w kreatorze.  
  
6.  Edytor konfiguracji usługi wykorzystuje ComSvcConfig.exe w tle, aby wygenerować plik konfiguracji. Po zakończeniu tego procesu można wyświetlić podsumowanie i zakończyć pracę kreatora. Wygenerowano plik konfiguracyjny jest otwarty, aby można ją edytować bezpośrednio.  
  
### <a name="editing-an-existing-com-configuration"></a>Edytowanie istniejącej konfiguracji modelu COM +  
  
1.  Wybierz **pliku** -> menu **Otwórz** -> **usług COM +**...  
  
2.  Wybierz usługę modelu COM +, aby edytować na liście.  
  
3.  Edytuj ustawienia konfiguracji w **kontrakty COM** węzła.  
  
    > [!NOTE]
    >  Można również bezpośrednio otworzyć i edytować plik konfiguracji, który zawiera kontrakty COM.  
  
## <a name="security"></a>Zabezpieczenia  
 Plik konfiguracji usługi generowane przez Edytor konfiguracji nie jest gwarantowana do zabezpieczenia. Zapoznaj się z [zabezpieczeń](../../../docs/framework/wcf/feature-details/security.md) dokumentacji, aby dowiedzieć się, jak zabezpieczyć Twoje [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usług.  
  
 Ponadto edytora konfiguracji mogą służyć tylko do odczytu i zapisu prawidłową [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] elementy konfiguracji. Narzędzie ignoruje elementów schematu zgodne, zdefiniowane przez użytkownika. On również nie będzie podejmował Usuń te elementy z konfiguracji plików lub określić ich wpływu na znany [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] elementów. Jest odpowiedzialny za użytkownika do określenia, czy te elementy stanowiących zagrożenie dla aplikacji lub systemu.
