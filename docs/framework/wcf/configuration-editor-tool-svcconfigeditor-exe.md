---
title: Narzędzie edytora konfiguracji (SvcConfigEditor.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- configuration files, creating
- configuration files
- Configuration file
- configuration file schema
ms.assetid: 2db21a57-5f64-426f-89df-fb0dc2d2def5
ms.openlocfilehash: 3d482e2b03346c9443066c480575a1394324b9bf
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320702"
---
# <a name="configuration-editor-tool-svcconfigeditorexe"></a>Narzędzie edytora konfiguracji (SvcConfigEditor.exe)

Edytor konfiguracji usługi Windows Communication Foundation (WCF) (SvcConfigEditor. exe) umożliwia administratorom i deweloperom tworzenie i modyfikowanie ustawień konfiguracji usług WCF przy użyciu graficznego interfejsu użytkownika. Za pomocą tego narzędzia można zarządzać ustawieniami powiązań programu WCF, zachowań, usług i diagnostyki bez konieczności bezpośredniego edytowania plików konfiguracji XML.

Edytor konfiguracji usługi można znaleźć w folderze C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin.

## <a name="the-wcf-configuration-editor"></a>Edytor konfiguracji WCF

Edytor konfiguracji usługi zawiera kreatora, który przeprowadzi Cię przez wszystkie kroki opisane w temacie Konfigurowanie usługi lub klienta WCF. Zdecydowanie zaleca się użycie Kreatora zamiast edytora bezpośrednio.

Jeśli masz już pewne pliki konfiguracji zgodne ze standardowym schematem system. Configuration, możesz zarządzać określonymi ustawieniami powiązań, zachowań, usług i diagnostyki przy użyciu interfejsu użytkownika. Edytor konfiguracji usługi umożliwia zarządzanie ustawieniami istniejących plików konfiguracji WCF oraz plikami wykonywalnymi, usługami COM+ i usługami hostowanymi w sieci Web. Podczas otwierania usługi hostowanej w sieci Web za pomocą edytora konfiguracji usługi, są wyświetlane sekcje konfiguracja i dziedziczone konfiguracje usługi.

Ponieważ ustawienia konfiguracji programu WCF znajdują się w sekcji `<system.serviceModel>` pliku konfiguracyjnego, Edytor działa wyłącznie na zawartości tego elementu i nie uzyskuje dostępu do innych elementów w tym samym pliku. Możesz przejść do istniejących plików konfiguracji bezpośrednio lub wybrać zestaw, który zawiera usługę, katalog wirtualny lub usługę COM+. Edytor ładuje plik konfiguracyjny dla danej usługi i zezwala użytkownikowi na dodawanie nowych elementów lub edytowanie istniejących elementów zagnieżdżonych w sekcji `<system.serviceModel>` pliku konfiguracyjnego.

Edytor obsługuje funkcję IntelliSense i wymusza zgodność schematu. Wynikowe dane wyjściowe są gwarantowane w celu zachowania zgodności ze schematem pliku konfiguracji i zawierają składniowo prawidłowe wartości danych. Jednak Edytor nie gwarantuje, że plik konfiguracji jest semantycznie prawidłowy. Innymi słowy, Edytor nie gwarantuje, że plik konfiguracji może współdziałać z usługą, którą konfiguruje.

> [!CAUTION]
> Edytor nie może przeczyścić elementu konfiguracji z pliku konfiguracji po zmodyfikowaniu elementu. Na przykład, jeśli używasz edytora, aby ustawić nazwę punktu końcowego jako niepusty ciąg i zapisać go, plik konfiguracyjny ma następującą zawartość, jak pokazano w poniższym przykładzie.
>
> `<endpoint binding="basicHttpBinding" name="somename" />`
>
> Jeśli podjęto próbę usunięcia nazwy przez ustawienie jej jako pustego ciągu i zapisania pliku, plik konfiguracji nadal zawiera atrybut `name`, jak pokazano w poniższym przykładzie.
>
> `<endpoint binding="basicHttpBinding" name="" />`
>
> Aby przeczyścić atrybut, należy ręcznie edytować element przy użyciu innego edytora tekstu.
>
> Należy zachować szczególną ostrożność przy tym problemie, jeśli używasz elementu `issueToken` zachowania punktu końcowego `clientCredential`. W przeciwnym razie atrybut `address` elementu podrzędnego `localIssuer` nie może być pustym ciągiem. Jeśli atrybut `address` został zmodyfikowany przy użyciu edytora konfiguracji i chcesz go całkowicie usunąć, należy to zrobić przy użyciu narzędzia innego niż Edytor. W przeciwnym razie atrybut zawiera pusty ciąg, a aplikacja zgłasza wyjątek.

## <a name="using-the-configuration-editor"></a>Korzystanie z edytora konfiguracji

Edytor konfiguracji usługi można znaleźć w następującej Windows SDK lokalizacji instalacji:

C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin\SvcConfigEditor.exe

Po uruchomieniu edytora konfiguracji usługi możesz użyć menu **plik/Otwórz** , aby przeglądać w poszukiwaniu usługi lub zestawu, którym chcesz zarządzać. Pliki konfiguracji można otwierać bezpośrednio, przeglądać w poszukiwaniu usług WCF/COM + usługi i otwierać pliki konfiguracji dla usług hostowanych w sieci Web.

Interfejs użytkownika edytora konfiguracji usługi jest podzielony na następujące obszary:

- Okienko widoku drzewa, które wyświetla elementy konfiguracji w strukturze drzewa po lewej stronie. Aby wykonać operacje w drzewie, kliknij prawym przyciskiem myszy węzły.

- Okienko zadań, które wyświetla typowe zadania dla bieżących elementów w lewym dolnym rogu okna

- Okienko szczegółów, w którym są wyświetlane szczegółowe ustawienia węzła konfiguracji wybranego w widoku drzewa po prawej stronie.

### <a name="opening-a-configuration-file"></a>Otwieranie pliku konfiguracji

1. Uruchom Edytor konfiguracji usługi przy użyciu okna wiersza polecenia, aby przejść do lokalizacji instalacji programu WCF, a następnie wpisz `SvcConfigEditor.exe`.

2. Z menu **plik** wybierz polecenie **Otwórz** , a następnie kliknij typ pliku, którym chcesz zarządzać.

3. W oknie dialogowym **otwieranie** przejdź do określonego pliku, który chcesz zarządzać, a następnie kliknij go dwukrotnie.

Przeglądarka automatycznie postępuje zgodnie ze ścieżką scalania konfiguracji i tworzy widok Scalonej konfiguracji. Na przykład rzeczywista konfiguracja usługi niehostowanej jest kombinacją Machine. config i App. config. Wszystkie zmiany są stosowane do aktywnego pliku w SvcConfigEditor. Jeśli chcesz edytować konkretny plik w ścieżce scalania konfiguracji, należy otworzyć go bezpośrednio.

> [!NOTE]
> Edytor konfiguracji ponownie ładuje aktualnie otwarty plik konfiguracji, gdy ten ostatni został zmodyfikowany poza edytorem. W takim przypadku wszystkie zmiany, które nie zostały trwale zapisane w edytorze, zostaną utracone. Jeśli ponowne ładowanie odbywa się konsekwentnie, najbardziej prawdopodobną przyczyną jest usługa, która stale uzyskuje dostęp do pliku konfiguracji, na przykład oprogramowania antywirusowego działającego w tle. Aby rozwiązać ten problem, upewnij się, że Edytor konfiguracji jest jedynym procesem, który ma dostęp do pliku po jego otwarciu.

### <a name="services"></a>Usługi

W węźle **usługi** są wyświetlane wszystkie usługi aktualnie przypisane w pliku konfiguracji. Każdy podwęzeł w drzewie odnosi się do elementu podrzędnego < `services` > elementu w pliku konfiguracji.

Po kliknięciu węzła **usługi** można wyświetlić lub wykonać zadania na stronie Podsumowanie usługi w okienku **szczegółów** .

#### <a name="creating-a-new-service-configuration"></a>Tworzenie nowej konfiguracji usługi

Nową konfigurację usługi można utworzyć w następujący sposób:

- Korzystanie z kreatora: kliknij link **Utwórz nową usługę...** Aby uruchomić kreatora, w okienku zadań lub stronie podsumowania. Można to również zrobić w menu **plik** — > **dodać nowy element**.

- Utwórz ręcznie: możesz kliknąć prawym przyciskiem myszy węzeł **usługi** i wybrać polecenie **Nowa usługa**.

#### <a name="creating-a-new-service-endpoint-configuration"></a>Tworzenie nowej konfiguracji punktu końcowego usługi

Nową konfigurację punktu końcowego usługi można utworzyć w następujący sposób:

- Utwórz za pomocą kreatora: kliknij link **Utwórz nowy punkt końcowy usługi...** Aby uruchomić kreatora, w okienku zadań lub stronie podsumowania. Można to również zrobić w menu **plik** — > **dodać nowy element**.

- Utwórz ręcznie: po utworzeniu usługi można kliknąć prawym przyciskiem myszy węzeł **punkty końcowe** i wybrać pozycję "**nowy punkt końcowy usługi**".

#### <a name="editing-a-service-configuration"></a>Edytowanie konfiguracji usługi

1. Kliknij węzeł **usługi** .

2. Edytuj ustawienia w siatce właściwości.

#### <a name="editing-a-service-endpoint-configuration"></a>Edytowanie konfiguracji punktu końcowego usługi

1. Kliknij węzeł **punktu końcowego usługi** .

2. Edytuj ustawienia w siatce właściwości.

#### <a name="adding-a-base-address"></a>Dodawanie adresu podstawowego

1. Kliknij węzeł **hosta** .

2. Kliknij **Nowy...** w sekcji **adresy podstawowe** .

3. W oknie dialogowym wpisz adres URI adresu podstawowego.

4. Kliknij przycisk **OK**.

> [!NOTE]
> Nie można edytować wartości [\<baseAddressPrefixFilters >](../configure-apps/file-schema/wcf/baseaddressprefixfilters.md) wewnątrz tego narzędzia. Aby dodać lub zmodyfikować ten element, należy użyć edytora tekstu lub programu Visual Studio.

### <a name="client"></a>Klient

W węźle **klienta** są wyświetlane wszystkie punkty końcowe klienta w pliku konfiguracji. Każdy podwęzeł w drzewie odnosi się do elementu podrzędnego < `client` > elementu w pliku konfiguracji.

Po kliknięciu węzła **klienta** można wyświetlić lub wykonać zadania na **stronie Podsumowanie** klienta w **okienku szczegółów**.

#### <a name="creating-a-new-client-endpoint-configuration"></a>Tworzenie nowej konfiguracji punktu końcowego klienta

Nową konfigurację punktu końcowego klienta można utworzyć w następujący sposób:

- Utwórz przez kreatora: kliknij link **Utwórz nowego klienta...** w **okienku zadań** w dolnej części okna lub **stronie podsumowania** , aby uruchomić kreatora. Można to również zrobić w menu **plik** — > **dodać nowy element**. Kreator poprosi o wskazanie lokalizacji konfiguracji usługi, z której jest generowana konfiguracja klienta. Następnie można wybrać punkt końcowy usługi, z którym ma zostać nawiązane połączenie.

- Utwórz ręcznie: kliknij prawym przyciskiem myszy węzeł **punkty końcowe** w obszarze **Klient**, a następnie wybierz polecenie **nowy punkt końcowy klienta**.

#### <a name="editing-a-client-endpoint-configuration"></a>Edytowanie konfiguracji punktu końcowego klienta

1. Kliknij węzeł **punktu końcowego klienta** .

2. Edytuj ustawienia w siatce właściwości.

### <a name="standard-endpoint"></a>Standardowy punkt końcowy

Standardowe punkty końcowe to wyspecjalizowane punkty końcowe, które mają co najmniej jeden aspekt adresu, kontraktu i powiązania ustawione na wartości domyślne.

Takie ustawienia konfiguracji są przechowywane w **standardowym węźle punktu końcowego** . **Standardowy węzeł punktu końcowego** wyświetla wszystkie standardowe ustawienia punktu końcowego w pliku konfiguracji. Każdy podwęzeł w drzewie odpowiada elementowi podrzędnemu w elemencie `<standardEndpoints>` w pliku konfiguracji.

Po kliknięciu węzła **standardowego punktu końcowego** można wyświetlić lub wykonać zadania na **stronie Podsumowanie** standardowego punktu końcowego w **okienku szczegółów**.

#### <a name="creating-a-new-standard-endpoint-configuration"></a>Tworzenie nowej konfiguracji standardowego punktu końcowego

Nową konfigurację standardowego punktu końcowego można utworzyć w następujący sposób:

- Kliknij prawym przyciskiem myszy **Standardowy węzeł punktu końcowego** i wybierz pozycję **Nowa Standardowa konfiguracja punktu końcowego...** W oknie dialogowym Wybierz typ powiązania i kliknij przycisk **OK**.

- Wybierz węzeł **standardowego punktu końcowego** , a następnie kliknij pozycję **Nowa Standardowa konfiguracja punktu końcowego...** w **okienku zadań** w lewym dolnym rogu okna.

W oknie dialogowym **Tworzenie nowego standardowego punktu końcowego** zostaną wyświetlone wszystkie zarejestrowane standardowe typy punktów końcowych.

#### <a name="viewing-and-editing-a-standard-endpoint-configuration"></a>Wyświetlanie i edytowanie standardowej konfiguracji punktu końcowego

Konfigurację standardowego punktu końcowego można otworzyć do wyświetlania i edytowania w następujący sposób:

- Kliknij, aby rozwinąć węzeł **standardowego punktu końcowego** , a następnie kliknij odpowiedni podwęzeł punktu końcowego.

- Kliknij węzeł **standardowego punktu końcowego** , a następnie kliknij odpowiedni punkt końcowy w okienku szczegółów.

Atrybuty punktu końcowego są wyświetlane w okienku po prawej stronie do edycji.

#### <a name="deleting-a-standard-endpoint-configuration"></a>Usuwanie standardowej konfiguracji punktu końcowego

Konfigurację standardowego punktu końcowego można usunąć w następujący sposób:

- Kliknij, aby rozwinąć węzeł **standardowego punktu końcowego** , a następnie kliknij prawym przyciskiem myszy odpowiedni podwęzeł punktu końcowego. Użyj polecenia kontekstowego **Usuń konfigurację standardowego punktu końcowego** , aby usunąć punkt końcowy.

- Kliknij węzeł **standardowego punktu końcowego** . W okienku **zadań** kliknij pozycję **Usuń konfigurację standardowego punktu końcowego**.

Jeśli standardowy punkt końcowy jest używany, podczas próby usunięcia zostanie wyświetlony komunikat ostrzegawczy: **Standardowy punkt końcowy jest w użyciu. Jeśli usuniesz ją teraz, pamiętaj, aby usunąć wszystkie odwołania do innych części konfiguracji (na przykład w punkcie końcowym usługi lub w punkcie końcowym klienta). W przeciwnym razie konfiguracja będzie nieprawidłowa i nie będzie można jej otworzyć następnym razem. Czy na pewno chcesz usunąć standardowy punkt końcowy? "**

### <a name="binding"></a>Wiązanie

Konfiguracje powiązań są używane do konfigurowania powiązań dla punktów końcowych. Takie ustawienia konfiguracji są przechowywane w węźle **powiązania** . Odniesienia do konfiguracji powiązań odwołań według nazwy i wielu punktów końcowych mogą odwoływać się do konfiguracji pojedynczego powiązania.

W węźle **powiązania** są wyświetlane wszystkie ustawienia powiązań w pliku konfiguracji. Każdy podwęzeł w drzewie odpowiada elementowi podrzędnemu w < `bindings` > w pliku konfiguracyjnym.

Po kliknięciu węzła **powiązania** można wyświetlić lub wykonać zadania na **stronie Podsumowanie** powiązań w **okienku szczegółów**.

#### <a name="creating-a-new-binding-configuration"></a>Tworzenie nowej konfiguracji powiązania

Nową konfigurację powiązania można utworzyć w następujący sposób.

- Kliknij prawym przyciskiem myszy węzeł **powiązania** i wybierz pozycję **Nowa konfiguracja powiązania**... W oknie dialogowym Wybierz typ powiązania i kliknij przycisk **OK**.

- Wybierz węzeł **powiązania** , a następnie kliknij pozycję **Nowa konfiguracja powiązania**... w **okienku zadań** w lewym dolnym rogu okna.

- Na stronie Podsumowanie usługi lub klienta kliknij przycisk **kliknij, aby utworzyć** w polu **Konfiguracja powiązania** , aby utworzyć konfigurację powiązania dla odpowiedniego punktu końcowego.

#### <a name="adding-binding-element-extensions-to-a-custom-binding"></a>Dodawanie rozszerzeń elementu wiązania do niestandardowego powiązania

1. Wybierz powiązanie, do którego chcesz dodać element rozszerzenia.

2. Kliknij przycisk **Dodaj**.

3. Z listy dostępnych rozszerzeń wybierz rozszerzenie elementu powiązania, które chcesz dodać. Aby zaznaczyć wiele elementów, naciśnij jednocześnie klawisz CTRL.

4. Kliknij przycisk **Dodaj**.

#### <a name="adjusting-the-extension-position-in-a-custom-binding"></a>Dopasowanie położenia rozszerzenia w niestandardowym powiązaniu

Niestandardowe powiązanie to kolekcja elementów powiązania, które tworzą stos. Każdy element powiązania na stosie ma własne ustawienia konfiguracji. Kolejność rozszerzeń elementu powiązania w niestandardowym powiązaniu wskazuje ich położenie w stosie. Elementy w górnej części stosu są stosowane najpierw. Aby zmienić kolejność:

1. Wybierz węzeł niestandardowego powiązania.

2. Wybierz jeden element rozszerzenia powiązania w sekcji **pozycja rozszerzenia elementu powiązania** .

3. Użyj przycisku w **górę** lub w **dół** z lewej strony listy, aby zmienić pozycję wybranego elementu.

#### <a name="editing-the-configuration-of-binding-element-extensions-in-a-custom-binding"></a>Edytowanie konfiguracji rozszerzeń elementu powiązania w niestandardowym powiązaniu

1. Wybierz węzeł powiązanie w drzewie.

2. Wybierz niestandardowe powiązanie, które zawiera element, który chcesz edytować.

3. Wybierz rozszerzenie elementu powiązania, które chcesz edytować. Ustawienia elementu są wyświetlane w okienku po prawej stronie, gdzie mogą być edytowane.

### <a name="diagnostics"></a>Diagnostyka

W węźle **Diagnostyka** są wyświetlane wszystkie ustawienia diagnostyczne w pliku konfiguracji. Umożliwia włączenie lub wyłączenie liczników wydajności, włączenie lub wyłączenie Instrumentacja zarządzania Windows (WMI), skonfigurowanie śledzenia WCF i skonfigurowanie rejestrowania komunikatów WCF. Ustawienia w węźle **Diagnostyka** odpowiadają sekcji < `system.diagnostics` > i `<diagnostics>` w `<system.serviceModel>` w pliku konfiguracyjnym.

Po kliknięciu węzła **Diagnostyka** można wyświetlić lub wykonać zadania na **stronie podsumowania** diagnostyki w **okienku szczegółów**.

#### <a name="configuring-performance-counters-and-wmi"></a>Konfigurowanie liczników wydajności i usługi WMI

1. Kliknij węzeł **Diagnostyka** .

2. Kliknij pozycję **Przełącz liczniki wydajności**. Licznik wydajności ma trzy stany: wyłączone (wartość domyślna), tylko serviceI ALL. Kliknięcie linku powoduje przełączenie tego ustawienia między tymi trzema stanami.

#### <a name="configuring-wmi-provider"></a>Konfigurowanie dostawcy WMI

1. Kliknij węzeł **Diagnostyka** .

2. Aby włączyć dostawcę usługi WMI, kliknij link **Włącz dostawcę WMI** .

#### <a name="enabling-wcf-tracing"></a>Włączanie śledzenia WCF

Można utworzyć plik śledzenia WCF ze standardowymi właściwościami lub skonfigurować niestandardowy plik śledzenia.

1. Kliknij węzeł **Diagnostyka** .

2. Kliknij pozycję **Włącz śledzenie**.

3. Kliknij link **poziom śledzenia** , aby dostosować poziom śledzenia. Istnieje sześć poziomów śledzenia: wyłączone, krytyczne, błąd, ostrzeżenie, informacje i pełne. Opcja **śledzenie działań** i **propagowanie** działań umożliwia korzystanie z funkcji śledzenia działań programu WCF.

4. Kliknij nazwę odbiornika śledzenia, aby określić plik śledzenia i opcje.

#### <a name="enabling-wcf-logging"></a>Włączanie rejestrowania WCF

Można utworzyć plik śledzenia WCF ze standardowymi właściwościami lub skonfigurować niestandardowy plik śledzenia.

1. Kliknij węzeł **Diagnostyka** .

2. Kliknij pozycję **Włącz rejestrowanie komunikatów**.

3. Kliknij link **poziom rejestrowania** , aby dostosować poziom rejestrowania. Istnieją trzy poziomy dziennika: źle sformułowane, usługa i transport.

4. Kliknij nazwę odbiornika, aby określić plik dziennika i opcje.

> [!NOTE]
> Jeśli chcesz, aby dzienniki śledzenia i komunikatów były opróżniane automatycznie po zamknięciu aplikacji, Włącz opcję **automatycznego opróżniania** .

**Strona podsumowania** **diagnostyki** umożliwia wykonywanie najbardziej typowych zadań związanych z konfigurowaniem diagnostyki. Jeśli jednak chcesz ręcznie edytować ustawienia odbiorników i źródeł, należy rozwinąć węzeł **Diagnostyka** i edytować ustawienia w węźle **Rejestrowanie komunikatów**, **odbiorniki** i **źródła** .

#### <a name="enabling-wcf-custom-tracing-or-message-logging"></a>Włączanie śledzenia niestandardowego programu WCF lub rejestrowanie komunikatów

1. Kliknij węzeł **Diagnostyka** i rozwiń go.

2. Kliknij prawym przyciskiem myszy węzeł **detektory** i wybierz pozycję **Nowy odbiornik**.

3. Wpisz nazwę pliku śledzenia w polu **InitData** . Możesz kliknąć przycisk "..." przycisk, aby przejść do ścieżki.

4. Kliknięcie wiersza **TypeName** powoduje wyświetlenie "..." przycisk. Kliknij ten przycisk, aby otworzyć **przeglądarkę śledzenia typów odbiorników**, której można użyć do znajdowania wstępnie skonfigurowanych detektorów śledzenia, które są już zainstalowane.

5. Zwróć uwagę na sekcję **źródłową** . Kliknij przycisk **Dodaj** w tej sekcji, aby otworzyć okno dialogowe z menu rozwijanym zawierającym listę dostępnych źródeł śledzenia. Wybierz źródło śledzenia i kliknij przycisk **OK**.

6. Aby edytować ustawienia rejestrowania komunikatów, kliknij węzeł **Rejestrowanie komunikatów** . Ustawienia można edytować w siatce właściwości.

### <a name="advanced"></a>Zaawansowane

#### <a name="behaviors"></a>Zachowania

W węźle **zachowań** są wyświetlane zachowania, które są obecnie zdefiniowane w pliku konfiguracji.

Konfiguracje zachowań są używane do konfigurowania zachowań punktów końcowych i usług. Takie ustawienia konfiguracji są przechowywane w węźle **Zaawansowane** w obszarze **zachowania usługi** i **zachowania punktów końcowych**. Zachowania usługi są używane przez usługi; zachowania punktu końcowego dla punktów końcowych.

Zachowania są kolekcją elementów rozszerzenia, które stosują stos. Element w górnej części stosu jest stosowany najpierw. Każdy element rozszerzenia może mieć własną konfigurację.

##### <a name="creating-a-new-behavior-configuration"></a>Tworzenie nowej konfiguracji zachowania

Nową konfigurację zachowania można utworzyć na dwa sposoby.

- Kliknij prawym przyciskiem myszy jeden z węzłów zachowań i wybierz polecenie "**Nowa konfiguracja zachowań...**

- Wybierz jeden z węzłów zachowań i kliknij **nową konfigurację zachowań**... w **okienku zadań** w lewym dolnym rogu okna.

##### <a name="adding-behavior-element-extensions-to-a-behavior"></a>Dodawanie rozszerzeń elementu zachowania do zachowania

1. Wybierz jeden z węzłów zachowań.

2. Wybierz zachowanie, które chcesz edytować.

3. Kliknij przycisk **Dodaj**.

4. Z listy dostępnych rozszerzeń wybierz rozszerzenie elementu zachowania, które chcesz dodać.

5. Kliknij przycisk **Dodaj**.

##### <a name="adjusting-the-extension-position-in-a-behavior"></a>Dopasowanie położenia rozszerzenia w ramach zachowania

Zachowania są kolekcjami elementów tworzących stos. Każdy element na stosie ma własną konfigurację. Kolejność rozszerzeń elementów zachowań w zachowaniu wskazuje ich położenie w stosie. Elementy w górnej części stosu są stosowane najpierw. Aby zmienić kolejność:

1. Wybierz jeden z węzłów zachowań.

2. Wybierz zachowanie, które chcesz edytować.

3. Zaznacz element rozszerzenia zachowań w sekcji **pozycja rozszerzenia elementu zachowania** .

4. Użyj przycisku w **górę** lub w **dół** z lewej strony listy, aby zmienić pozycję wybranego elementu.

##### <a name="editing-the-configuration-of-behavior-element-extensions"></a>Edytowanie konfiguracji rozszerzeń elementów zachowań

1. Wybierz jeden z węzłów zachowań w drzewie.

2. Wybierz zachowanie, które zawiera element, który chcesz edytować.

3. Wybierz rozszerzenie elementu zachowania, które chcesz edytować. Ustawienia elementu są wyświetlane w okienku po prawej stronie, w którym można je edytować.

#### <a name="protocolmapping"></a>ProtocolMapping

Ta sekcja umożliwia ustawienie domyślnych typów powiązań dla różnych protokołów, takich jak http, TCP, MSMQ lub net. pipe przez zdefiniowane mapowanie między schematami adresów protokołu a możliwymi powiązaniami. Możesz również dodać nowe mapowania do innych protokołów.

#### <a name="extensions"></a>rozszerzenia

Nowe rozszerzenia powiązań, rozszerzenia elementów powiązania, standardowe rozszerzenia punktów końcowych i rozszerzenia zachowań mogą być zarejestrowane do użycia w konfiguracji WCF. Rozszerzeniami są pary nazwa/typ. Nazwa definiuje nazwę rozszerzenia w konfiguracji, podczas gdy typ implementuje rozszerzenie. Istnieją cztery typy rozszerzeń:

- Rozszerzenia powiązań definiują cały typ powiązania. Przykład: `basicHttpBinding`.

- Rozszerzenia elementów powiązania definiują element powiązania. Przykład: `textMessageEncoding`.

- Standardowe rozszerzenia punktów końcowych definiują cały standardowy punkt końcowy. Przykład: `discoveryEndpoint`.

- Rozszerzenia elementów zachowań definiują element zachowania. Przykład: `clientVia`.

 Rozszerzenia, które zostały zarejestrowane w konfiguracji, mogą być używane jak każdy inny składnik WCF tego samego typu.

##### <a name="adding-a-new-extension"></a>Dodawanie nowego rozszerzenia

Wybierz jeden z węzłów rozszerzeń w węzłach zaawansowanych:

1. Kliknij pozycję **Nowy**.

2. Wprowadź nazwę i typ.

3. Kliknij przycisk **OK**.

4. Rozszerzenie jest teraz widoczne w odpowiednim miejscu w edytorze. Na przykład, jeśli dodasz rozszerzenie elementu zachowania, pojawia się ono na liście dostępnych rozszerzeń.

#### <a name="hosting-environment"></a>Środowisko hostingu

Ta sekcja umożliwia zdefiniowanie ustawień tworzenia wystąpienia dla środowiska hostingu usługi.

### <a name="creating-a-configuration-file-using-the-wizard"></a>Tworzenie pliku konfiguracji przy użyciu kreatora

Jednym ze sposobów tworzenia nowego pliku konfiguracji jest użycie Kreatora nowego elementu usługi. Kreator odnajduje zainstalowane typy usług i inne elementy zgodne z programem WCF na komputerze, w tym katalogi wirtualne COM+ i hostowane w sieci Web, i ładuje je w celu znacznie usprawnienia tworzenia konfiguracji.

#### <a name="creating-a-configuration-file"></a>Tworzenie pliku konfiguracji

1. Uruchom Edytor konfiguracji usługi przy użyciu okna wiersza polecenia, aby przejść do lokalizacji instalacji programu WCF, a następnie wpisz `SvcConfigEditor.exe`.

2. W menu **plik** wybierz pozycję **Otwórz** , a następnie kliknij pozycję plik **wykonywalny**, **Usługa com+** lub **Usługa webhosted**, w zależności od typu pliku konfiguracji, który chcesz utworzyć.

3. W oknie dialogowym **Otwórz** przejdź do określonego pliku, dla którego chcesz utworzyć plik konfiguracji, a następnie kliknij go dwukrotnie.

4. W menu **plik** wskaż polecenie **Dodaj nowy element** , a następnie kliknij pozycję **Usługa**. Zostanie otwarty Kreator nowego elementu usługi.

5. Postępuj zgodnie z instrukcjami w kreatorze, aby utworzyć nową usługę.

> [!NOTE]
> Jeśli chcesz użyć NetPeerTcpBinding z pliku konfiguracyjnego wygenerowanego przez kreatora, musisz ręcznie dodać element konfiguracji powiązania i zmodyfikować atrybut `mode` elementu `security` na wartość "none" (brak).

## <a name="configuring-com"></a>Konfigurowanie modelu COM+

Edytor konfiguracji usługi umożliwia utworzenie nowego pliku konfiguracji dla istniejącej aplikacji modelu COM+ lub edytowanie istniejącej konfiguracji modelu COM+. Węzeł **kontraktu com** jest widoczny tylko wtedy, gdy sekcja < `comContract` > istnieje w pliku konfiguracji.

### <a name="creating-a-new-com-configuration"></a>Tworzenie nowej konfiguracji modelu COM+

Przed utworzeniem nowej konfiguracji modelu COM+ upewnij się, że aplikacja modelu COM+ jest zainstalowana w usługach składników i zarejestrowana w globalnej pamięci podręcznej zestawów (GAC).

1. Wybierz menu **plik** > **zintegruj** **aplikację com+**  -> . Ta operacja zamyka bieżący otwarty plik. Jeśli w bieżącym pliku znajdują się niezapisane dane, zostanie wyświetlone okno dialogowe Zapisz. Następnie zostanie uruchomiony **Kreator integracji modelu COM+** .

2. Na pierwszej stronie wybierz aplikację COM+ z drzewa. Jeśli nie możesz znaleźć aplikacji modelu COM+ w drzewie, sprawdź, czy jest ona zainstalowana w usługach składników i zarejestrowana w globalnej pamięci podręcznej zestawów (GAC).

3. Na następnej stronie Wybierz metody, które chcesz uwidocznić jako usługi WCF. Wszystkie obsługiwane metody w aplikacji COM+ są domyślnie wyświetlane i wybierane.

4. Wybierz metodę hostingu.

5. Skonfiguruj inne ustawienia zgodnie z przewodnikami w kreatorze.

6. Edytor konfiguracji usługi używa programu ComSvcConfig. exe w tle do generowania pliku konfiguracji. Po zakończeniu tej operacji można wyświetlić podsumowanie i zakończyć pracę kreatora. Wygenerowany plik konfiguracji zostanie otwarty, aby można go było edytować bezpośrednio.

### <a name="editing-an-existing-com-configuration"></a>Edytowanie istniejącej konfiguracji modelu COM+

1. Wybierz menu **plik** > **Otwórz** -> **usługi com+** ...

2. Wybierz z listy usługę COM+, którą chcesz edytować.

3. Edytuj ustawienia konfiguracji w węźle **kontrakty com** .

    > [!NOTE]
    > Można również bezpośrednio otworzyć i edytować plik konfiguracji, który zawiera kontrakty COM.

## <a name="security"></a>Zabezpieczenia

Nie ma gwarancji, że plik konfiguracji usługi wygenerowany przez Edytor konfiguracji jest bezpieczny. Zapoznaj się z dokumentacją [zabezpieczeń](./feature-details/security.md) , aby dowiedzieć się, jak zabezpieczyć usługi WCF.

Ponadto edytor konfiguracji może być używany tylko do odczytu i zapisu prawidłowych elementów konfiguracji WCF. Narzędzie ignoruje elementy zdefiniowane przez użytkownika, które są zgodne ze schematem. Nie powoduje to również usunięcia tych elementów z pliku konfiguracyjnego ani określania ich wpływu na znane elementy programu WCF. Użytkownik jest odpowiedzialny za określenie, czy te elementy stanowią zagrożenie dla aplikacji lub systemu.
