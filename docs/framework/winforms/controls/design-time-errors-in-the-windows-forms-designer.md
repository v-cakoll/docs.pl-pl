---
title: Błędy czasu projektowania w Projektant formularzy systemu Windows
ms.date: 09/09/2019
f1_keywords:
- DTELErrorList
- WhyDTELPage
helpviewer_keywords:
- errors [Windows Forms Designer]
- design-time errors [Windows Forms Designer]
ms.assetid: ad408380-825a-46d8-9a4a-531b130b88ce
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3e2366513183337c3c5dd05ff45f8a6f724deaae
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988443"
---
# <a name="windows-forms-designer-error-page"></a>Strona błędu Projektant formularzy systemu Windows

Jeśli nie można załadować Projektant formularzy systemu Windows ze względu na błąd w kodzie, w składniku innej firmy lub w innym miejscu zobaczysz stronę błędu zamiast projektanta. Ta strona błędu niekoniecznie oznacza usterkę w projektancie. Usterka może znajdować się gdzieś na stronie powiązanej z kodem, \<która nazywa się nazwą użytkownika >. Designer.cs. Błędy pojawiają się w zwijanych, żółtych słupkach z linkiem umożliwiającym przechodzenie do lokalizacji błędu na stronie kodowej.

![Strona błędu Projektant formularzy systemu Windows](media/windows-forms-designer-error-page-collapsed.png)

Można wybrać ignorowanie błędów i kontynuowanie ładowania projektanta, klikając przycisk **Ignoruj i Kontynuuj**. Ta akcja może spowodować nieoczekiwane zachowanie, na przykład kontrolki mogą nie być wyświetlane na powierzchni projektowej.

## <a name="instances-of-this-error"></a>Wystąpienia tego błędu

Gdy żółty pasek błędów jest rozwinięty, zostanie wyświetlone każde wystąpienie błędu. Wiele typów błędów zawiera dokładną lokalizację w następującym formacie: *[nazwa projektu]* *[nazwa formularza]* wiersz: *[numer wiersza]* kolumna: *[numer kolumny]* . Jeśli stos wywołań jest skojarzony z błędem, można kliknąć link **Pokaż stos wywołań** , aby go zobaczyć. Badanie stosu wywołań może pomóc w poprawieniu błędu.

![Projektant formularzy systemu Windows rozszerzony błąd](media/windows-forms-designer-error-page-expanded.png)

> [!NOTE]
>
> - W przypadku aplikacji Visual Basic strona błędu czasu projektowania nie wyświetla więcej niż jednego błędu, ale może wyświetlić wiele wystąpień tego samego błędu.
> - W C++ przypadku aplikacji błędy nie mają linków do lokalizacji kodu.

## <a name="help-with-this-error"></a>Pomoc dotycząca tego błędu

Jeśli jest dostępny temat pomocy dotyczący błędu, kliknij link **Pomoc MSDN** , aby przejść bezpośrednio do strony pomocy w witrynie docs.Microsoft.com.

## <a name="forum-posts-about-this-error"></a>Wpisy na forum dotyczące tego błędu

Kliknij link **Przeszukaj fora MSDN pod kątem wpisów związanych z tym** łączem błędu, aby przejść do forów Microsoft Developer Network. Możesz chcieć przeszukać [Projektant formularzy systemu Windows](https://social.msdn.microsoft.com/Forums/windows/home?forum=winformsdesigner) lub [Windows Forms](https://social.msdn.microsoft.com/Forums/windows/home?category=windowsforms) forów.

## <a name="design-time-errors"></a>Błędy czasu projektowania

W tej sekcji wymieniono niektóre z błędów, które mogą wystąpić.

### <a name="identifier-name-is-not-a-valid-identifier"></a>"\<nazwa identyfikatora >" nie jest prawidłowym identyfikatorem

Ten błąd wskazuje, że pole, metoda, zdarzenie lub obiekt jest nieprawidłowo nazwane.

### <a name="name-already-exists-in-project-name"></a>"\<nazwa >" istnieje już w nazwie\<"projektu >"

Komunikat o błędzie: "\<nazwa >" już istnieje w "\<nazwie projektu >". Wprowadź unikatową nazwę ".

Określono nazwę dla dziedziczonego formularza, który już istnieje w projekcie. Aby naprawić ten błąd, nadaj dziedziczonemu formularzowi unikatową nazwę.

### <a name="toolbox-tab-name-is-not-a-toolbox-category"></a>"\<Nazwa karty przybornika >" nie jest kategorią przybornika

Projektant innych firm próbował uzyskać dostęp do karty w przyborniku, który nie istnieje. Skontaktuj się z dostawcą składnika.

### <a name="a-requested-language-parser-is-not-installed"></a>Żądany parser języka nie jest zainstalowany

Komunikat o błędzie: "Żądany parser języka nie jest zainstalowany. Nazwa analizatora języka to "{0}".

Program Visual Studio podjął próbę załadowania projektanta, który został zarejestrowany dla typu pliku, ale nie może. Jest to najprawdopodobniej spowodowane błędem, który wystąpił podczas instalacji. Skontaktuj się z dostawcą języka, którego używasz, aby naprawić.

### <a name="a-service-required-for-generating-and-parsing-source-code-is-missing"></a>Brak usługi wymaganej do generowania i analizowania kodu źródłowego

Jest to problem związany ze składnikiem innej firmy. Skontaktuj się z dostawcą składnika.

### <a name="an-exception-occurred-while-trying-to-create-an-instance-of-object-name"></a>Wystąpił wyjątek podczas próby utworzenia wystąpienia "\<Object Name >"

Komunikat o błędzie: "Wystąpił wyjątek podczas próby utworzenia wystąpienia"\<Object Name > ". Wyjątek: "\<String\>Exception".

Projektant innej firmy zażądał utworzenia obiektu przez program Visual Studio, ale obiekt zgłosił błąd. Skontaktuj się z dostawcą składnika.

### <a name="another-editor-has-document-name-open-in-an-incompatible-mode"></a>Inny edytor ma otwartą nazwę dokumentu "\<>" w niezgodnym trybie

Komunikat o błędzie: "Inny edytor ma\<otwartą nazwę dokumentu" > "w niezgodnym trybie. Zamknij Edytor i spróbuj wykonać tę operację ponownie. "

Ten błąd występuje, jeśli próbujesz otworzyć plik, który jest już otwarty w innym edytorze. Wyświetlany jest Edytor, który ma już otwarty plik. Aby naprawić ten błąd, Zamknij Edytor, który otworzył plik, i spróbuj ponownie.

### <a name="another-editor-has-made-changes-to-document-name"></a>Inny edytor wprowadził zmiany w nazwie dokumentu\<">"

Zamknij i ponownie otwórz projektanta, aby zmiany zaczęły obowiązywać. Zwykle program Visual Studio automatycznie ponownie ładuje projektanta po wprowadzeniu zmian. Jednak inne projektanci, takie jak projektanci składników innych firm, mogą nie obsługiwać zachowania ponownego ładowania. W takim przypadku program Visual Studio poprosi o zamknięcie i ponowne otwarcie projektanta ręcznie.

### <a name="another-editor-has-the-file-open-in-an-incompatible-mode"></a>Plik jest otwarty w innym edytorze w niezgodnym trybie

Komunikat o błędzie: "Inny edytor ma otwarty plik w niezgodnym trybie. Zamknij Edytor i spróbuj wykonać tę operację ponownie. "

Ten komunikat jest podobny do "inny edytor ma\<otwartą nazwę dokumentu" > "w niezgodnym trybie", ale program Visual Studio nie może określić nazwy pliku. Aby naprawić ten błąd, Zamknij Edytor, który otworzył plik, i spróbuj ponownie.

### <a name="array-rank-rank-in-array-is-too-high"></a>Zbyt wysoka ranga tablicy "\<ranga w tablicy >"

Program Visual Studio obsługuje tylko tablice o pojedynczym wymiarze w bloku kodu, który jest analizowany przez projektanta. Tablice wielowymiarowe są prawidłowe poza tym obszarem.

### <a name="assembly-assembly-name-could-not-be-opened"></a>Nie można\<otworzyć zestawu "Nazwa zestawu >"

Komunikat o błędzie: Nie można otworzyć\<zestawu "Assembly" > ". Sprawdź, czy plik nadal istnieje. "

Ten komunikat o błędzie występuje podczas próby otwarcia pliku, którego nie można otworzyć. Sprawdź, czy plik istnieje i czy jest prawidłowym zestawem.

### <a name="bad-element-type-this-serializer-expects-an-element-of-type-type-name"></a>Zły typ elementu. Ten serializator oczekuje elementu typu "\<nazwa typu >"

Jest to problem związany ze składnikiem innej firmy. Skontaktuj się z dostawcą składnika.

### <a name="cannot-access-the-visual-studio-toolbox-at-this-time"></a>Nie można uzyskać dostępu do Przybornika Visual Studio

Program Visual Studio wykonał wywołanie przybornika, który nie jest dostępny. Jeśli ten błąd jest wyświetlany, w przypadku wystąpienia tego błędu należy zgłosić problem, korzystając z [raportu](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).

### <a name="cannot-bind-an-event-handler-to-the-event-name-event-because-it-is-read-only"></a>Nie można powiązać procedury obsługi zdarzeń z zdarzeniem "\<Nazwa zdarzenia >", ponieważ jest tylko do odczytu

Ten błąd występuje najczęściej, gdy podjęto próbę połączenia zdarzenia z kontrolką dziedziczoną z klasy bazowej. Jeśli zmienna członkowska kontrolki jest prywatna, program Visual Studio nie może połączyć zdarzenia z metodą. Formanty dziedziczone prywatnie nie mogą mieć żadnych dodatkowych zdarzeń.

### <a name="cannot-create-a-method-name-for-the-requested-component-because-it-is-not-a-member-of-the-design-container"></a>Nie można utworzyć nazwy metody dla żądanego elementu, ponieważ nie jest on elementem członkowskim kontenera projektu

Program Visual Studio próbował dodać procedurę obsługi zdarzeń do składnika, który nie ma zmiennej składowej w projektancie. Skontaktuj się z dostawcą składnika.

### <a name="cannot-name-the-object-name-because-it-is-already-named-name"></a>Nie można nazwać obiektu\<"name >", ponieważ ma już nazwę\<"name >"

Jest to błąd wewnętrzny w serializatorze programu Visual Studio. Wskazuje, że serializator próbował nazwać obiekt dwa razy, co nie jest obsługiwane. Jeśli widzisz ten błąd, zarejestruj problem, korzystając z [raportu o problemie](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).

### <a name="cannot-remove-or-destroy-inherited-component-component-name"></a>Nie można usunąć ani zniszczyć składnika dziedziczonego "Nazwa składnika"\<> "

Dziedziczone kontrolki znajdują się poniżej własności dziedziczonej klasy. Zmiany dziedziczonej kontrolki muszą zostać wprowadzone w klasie, z której pochodzi formant. W rezultacie nie można zmienić nazwy ani zniszczyć.

### <a name="category-toolbox-tab-name-does-not-have-a-tool-for-class-class-name"></a>Nazwa karty\<przybornika kategorii ">" nie ma narzędzia klasy "class name >"\<

Projektant próbował odwołać się do klasy na określonej karcie przybornika, ale Klasa nie istnieje. Skontaktuj się z dostawcą składnika.

### <a name="class-class-name-has-no-matching-constructor"></a>Klasa "\<class name >" nie ma pasującego konstruktora

Projektant innej firmy poprosił program Visual Studio o utworzenie obiektu z określonymi parametrami w konstruktorze, który nie istnieje. Skontaktuj się z dostawcą składnika.

### <a name="code-generation-for-property-property-name-failed"></a>Generowanie kodu dla właściwości "\<Property Name >" nie powiodło się

Jest to ogólna otoka dla błędu. Ciąg błędu, który towarzyszy tej wiadomości, zawiera więcej szczegółowych informacji o komunikacie o błędzie i link do bardziej szczegółowego tematu pomocy. Aby naprawić ten błąd, należy rozwiązać błąd określony w komunikacie o błędzie dołączonym do tego błędu.

### <a name="component-component-name-did-not-call-containeradd-in-its-constructor"></a>Składnik "\<nazwa składnika >" nie wywołał kontenera. Add () w jego konstruktorze

Jest to błąd w składniku, który właśnie został załadowany lub umieszczony w formularzu. Wskazuje, że składnik nie dodał siebie do kontrolki kontenera (czy jest to inna kontrolka czy formularz). Projektant będzie kontynuował pracę, ale mogą wystąpić problemy ze składnikiem w czasie wykonywania.

Aby naprawić ten błąd, skontaktuj się z dostawcą składnika. Lub, jeśli jest to składnik, który został utworzony, wywołaj `IContainer.Add` metodę w konstruktorze składnika.

### <a name="component-name-cannot-be-empty"></a>Nazwa składnika nie może być pusta

Ten błąd występuje podczas próby zmiany nazwy składnika na wartość pustą.

### <a name="could-not-access-the-variable-variable-name-because-it-has-not-been-initialized-yet"></a>Nie można uzyskać dostępu do zmiennej\<"nazwa zmiennej >", ponieważ nie została jeszcze zainicjowana

Ten błąd może wystąpić z powodu dwóch scenariuszy. Dostawca składnika innej firmy ma problem z kontrolką lub składnikiem, które zostały rozdystrybuowane lub czy zapisany kod ma zależności cykliczne między składnikami.

Aby naprawić ten błąd, upewnij się, że Twój kod nie ma zależności cyklicznej. Jeśli te problemy są bezpłatne, należy zwrócić uwagę na dokładny tekst komunikatu o błędzie i skontaktować się z dostawcą składnika.

### <a name="could-not-find-type-type-name"></a>Nie można odnaleźć typu "\<type name >".

Komunikat o błędzie: "Nie można znaleźć nazwy typu\<" > ". Upewnij się, że zestaw zawierający ten typ jest przywoływany. Jeśli ten typ jest częścią projektu deweloperskiego, upewnij się, że projekt został pomyślnie skompilowany.

Wystąpił błąd, ponieważ nie znaleziono odwołania. Upewnij się, że typ wskazany w komunikacie o błędzie jest przywoływany i że wszystkie zestawy, których wymaga typ, są również wywoływane. Często problem polega na tym, że formant w rozwiązaniu nie został skompilowany. Aby skompilować, wybierz opcję **Kompiluj rozwiązanie** z menu **kompilacja** . W przeciwnym razie, Jeśli kontrolka została już skompilowana, Dodaj odwołanie ręcznie z menu rozwijanego prawym przyciskiem myszy folderu **References** lub **zależności** w Eksplorator rozwiązań.

### <a name="could-not-load-type-type-name"></a>Nie można załadować typu "\<type name >".

Komunikat o błędzie: "Nie można załadować nazwy typu\<" > ". Upewnij się, że zestaw zawierający ten typ jest dodawany do odwołań projektu.

Program Visual Studio podjął próbę przeprowadzenia metody obsługi zdarzeń i nie może odnaleźć jednego lub większej liczby typów parametrów dla metody. Jest to zazwyczaj spowodowane brakującym odwołaniem. Aby naprawić ten błąd, Dodaj odwołanie zawierające typ do projektu i spróbuj ponownie.

### <a name="could-not-locate-the-project-item-templates-for-inherited-components"></a>Zlokalizowanie szablonów elementu projektu dla elementów dziedziczonych nie powiodło się

Szablony formularzy dziedziczonych w programie Visual Studio są niedostępne. Jeśli widzisz ten błąd, zarejestruj problem, korzystając z [raportu o problemie](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).

### <a name="delegate-class-class-name-has-no-invoke-method-is-this-class-a-delegate"></a>Klasa delegata\<"class name >" nie ma metody Invoke. Czy ta klasa jest delegatem?

Program Visual Studio próbował utworzyć procedurę obsługi zdarzeń, ale wystąpił problem z typem zdarzenia. Taka sytuacja może wystąpić, jeśli zdarzenie zostało utworzone przez język niezgodny ze specyfikacją CLS. Skontaktuj się z dostawcą składnika.

### <a name="duplicate-declaration-of-member-member-name"></a>Zduplikowana deklaracja składowej\<"> nazwy składowej"

Ten błąd występuje, ponieważ zmienna członkowska została zadeklarowana dwukrotnie (na przykład dwa kontrolki o `Button1` nazwie są zadeklarowane w kodzie). Nazwy muszą być unikatowe w różnych formularzach dziedziczonych. Ponadto nazwy nie mogą się różnić tylko wielkością liter.

### <a name="error-reading-resources-from-the-resource-file-for-the-culture-culture-name"></a>Błąd podczas odczytu zasobów z pliku zasobów dla kultury "nazwa\<kultury" > "

Ten błąd może wystąpić, jeśli w projekcie znajduje się nieodpowiedni plik resx.

Aby poprawić ten błąd:

1. Kliknij przycisk **Pokaż wszystkie pliki** w Eksplorator rozwiązań, aby wyświetlić pliki RESX skojarzone z rozwiązaniem.
2. Załaduj plik resx w edytorze XML, klikając prawym przyciskiem myszy plik resx i wybierając polecenie **Otwórz**.
3. Edytuj ręcznie plik resx, aby rozwiązać błędy.

### <a name="error-reading-resources-from-the-resource-file-for-the-default-culture-culture-name"></a>Błąd podczas odczytu zasobów z pliku zasobów dla kultury domyślnej "\<nazwa kultury >"

Ten błąd może wystąpić, jeśli w projekcie istnieje nieodpowiedni plik resx dla kultury domyślnej.

Aby poprawić ten błąd:

1. Kliknij przycisk **Pokaż wszystkie pliki** w Eksplorator rozwiązań, aby wyświetlić pliki RESX skojarzone z rozwiązaniem.
2. Załaduj plik resx w edytorze XML, klikając prawym przyciskiem myszy plik resx i wybierając polecenie **Otwórz**.
3. Edytuj ręcznie plik resx, aby rozwiązać błędy.

### <a name="failed-to-parse-method-method-name"></a>Nie można przeanalizować\<metody "> nazwy metody"

Komunikat o błędzie: "Nie można przeanalizować\<nazwy metody" > ". Analizator składni zgłosił następujący błąd: "\<ciąg błędu >". Zapoznaj się z Lista zadań, aby uzyskać potencjalne błędy ".

Jest to ogólny komunikat o błędzie dotyczący problemów, które pojawiają się podczas analizowania. Te błędy są często spowodowane błędami składni. Zapoznaj się Lista zadań określonymi komunikatami dotyczącymi błędu.

### <a name="invalid-component-name-component-name"></a>Nieprawidłowa nazwa składnika: "\<nazwa składnika >"

Podjęto próbę zmiany nazwy składnika na nieprawidłową wartość dla tego języka. Aby naprawić ten błąd, nadaj nazwę składnikowi, który jest zgodny z regułami nazewnictwa dla tego języka.

### <a name="the-type-class-name-is-made-of-several-partial-classes-in-the-same-file"></a>Typ "\<class name >" składa się z kilku klas częściowych w tym samym pliku

Podczas definiowania klasy w wielu plikach za pomocą słowa kluczowego [częściowe](/dotnet/csharp/language-reference/keywords/partial-type) można mieć tylko jedną definicję częściową w każdym pliku.

Aby naprawić ten błąd, Usuń wszystkie oprócz jednej części definicji klasy z pliku.

### <a name="the-assembly-assembly-name-could-not-be-found"></a>Nie można odnaleźć\<zestawu "Nazwa zestawu >"

Komunikat o błędzie: Nie można znaleźć nazwy\<zestawu "Assembly" > ". Upewnij się, że zestaw jest przywoływany. Jeśli zestaw jest częścią bieżącego projektu programistycznego, upewnij się, że projekt został skompilowany.

Ten błąd jest podobny do "typu\<" nazwa typu ">" nie może zostać znaleziona, ale ten błąd zwykle występuje z powodu atrybutu metadanych. Aby naprawić ten błąd, sprawdź, czy istnieją odwołania do wszystkich zestawów używanych przez atrybuty.

### <a name="the-assembly-name-assembly-name-is-invalid"></a>Nazwa zestawu "\<nazwa zestawu >" jest nieprawidłowa

Składnik zażądał określonego zestawu, ale nazwa podana przez składnik nie jest prawidłową nazwą zestawu. Skontaktuj się z dostawcą składnika.

### <a name="the-base-class-class-name-cannot-be-designed"></a>Nie można zaprojektować klasy podstawowej "\<class name >"

Program Visual Studio załadował klasę, ale nie można zaprojektować klasy, ponieważ Implementująca klasa nie dostarczyła projektanta. Jeśli klasa obsługuje projektanta, upewnij się, że nie występują żadne problemy, które mogłyby powodować problemy z wyświetlaniem go w projektancie, na przykład błędy kompilatora. Upewnij się również, że wszystkie odwołania do klasy są poprawne i wszystkie nazwy klas są poprawnie wpisane. W przeciwnym razie, jeśli nie można zaprojektować klasy, Edytuj ją w widoku kodu.

### <a name="the-base-class-class-name-could-not-be-loaded"></a>Nie można załadować klasy\<podstawowej "class name >"

Klasa nie jest przywoływana w projekcie, dlatego program Visual Studio nie może go załadować. Aby naprawić ten błąd, Dodaj odwołanie do klasy w projekcie, a następnie zamknij i ponownie otwórz okno Projektant formularzy systemu Windows.

### <a name="the-class-class-name-cannot-be-designed-in-this-version-of-visual-studio"></a>Nie można zaprojektować klasy "\<class name >" w tej wersji programu Visual Studio

Projektant dla tego formantu lub składnika nie obsługuje tych samych typów, które są używane w programie Visual Studio. Skontaktuj się z dostawcą składnika.

### <a name="the-class-name-is-not-a-valid-identifier-for-this-language"></a>Nazwa klasy nie jest prawidłowym identyfikatorem dla tego języka

Kod źródłowy tworzony przez użytkownika ma nazwę klasy, która jest nieprawidłowa dla używanego języka. Aby naprawić ten błąd, nadaj klasie nazwę, która jest zgodna z wymaganiami dotyczącymi języka.

### <a name="the-component-cannot-be-added-because-it-contains-a-circular-reference-to-reference-name"></a>Nie można dodać składnika, ponieważ zawiera odwołanie cykliczne do nazwy referencyjnej "\<>"

Nie można dodać kontrolki lub składnika do samego siebie. Inną sytuacją, w której taka sytuacja może wystąpić, jest to, że w metodzie wywoływać InitializeComponent formularza (na przykład Form1) tworzony jest inny kod Form1.

### <a name="the-designer-cannot-be-modified-at-this-time"></a>Projektant nie może być w tej chwili modyfikowany

Ten błąd występuje, gdy plik w edytorze jest oznaczony jako tylko do odczytu. Upewnij się, że plik nie jest oznaczony jako tylko do odczytu, a aplikacja nie jest uruchomiona.

### <a name="the-designer-could-not-be-shown-for-this-file-because-none-of-the-classes-within-it-can-be-designed"></a>Nie można wyświetlić projektanta dla tego pliku, ponieważ żadna z klas w tym pliku nie może być zaprojektowana

Ten błąd występuje, gdy program Visual Studio nie może znaleźć klasy bazowej, która spełnia wymagania projektanta. Formularze i kontrolki muszą pochodzić od klasy bazowej, która obsługuje projektantów. W przypadku wyprowadzania z dziedziczonego formularza lub kontrolki upewnij się, że projekt został skompilowany.

### <a name="the-designer-for-base-class-class-name-is-not-installed"></a>Nie zainstalowano projektanta dla\<klasy podstawowej "class name >"

Program Visual Studio nie może załadować projektanta dla klasy. Jeśli widzisz ten błąd, zarejestruj problem, korzystając z [raportu o problemie](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).

### <a name="the-designer-must-create-an-instance-of-type-type-name-but-it-cant-because-the-type-is-declared-as-abstract"></a>Projektant musi utworzyć wystąpienie typu "\<type name >", ale nie jest to możliwe, ponieważ typ został zadeklarowany jako abstrakcyjny

Wystąpił błąd, ponieważ klasa bazowa obiektu, który jest przesyłany do projektanta, jest [abstrakcyjna](/dotnet/csharp/language-reference/keywords/abstract), co jest niedozwolone.

### <a name="the-file-could-not-be-loaded-in-the-designer"></a>Nie można załadować pliku projektu do projektanta

Klasa bazowa tego pliku nie obsługuje żadnych projektantów. Aby obejść ten sposób, użyj widoku kodu do pracy z plikiem. Kliknij prawym przyciskiem myszy plik w Eksplorator rozwiązań i wybierz polecenie **Wyświetl kod**.

### <a name="the-language-for-this-file-does-not-support-the-necessary-code-parsing-and-generation-services"></a>Język tego pliku nie obsługuje niezbędnego parsowania kodu i usług generowania

Komunikat o błędzie: "Język tego pliku nie obsługuje niezbędnych usług analizy i generowania kodu. Upewnij się, że otwierany plik jest członkiem projektu, a następnie spróbuj ponownie otworzyć plik ".

Przyczyną tego błędu jest prawdopodobnie otwarcie pliku, który znajduje się w projekcie, który nie obsługuje projektantów.

### <a name="the-language-parser-class-class-name-is-not-implemented-properly"></a>Nazwa\<klasy analizatora składni > ' nie została zaimplementowana prawidłowo

Komunikat o błędzie: "Nazwa klasy" parsera\<języka ">" nie została zaimplementowana prawidłowo. Skontaktuj się z dostawcą, aby uzyskać zaktualizowany moduł parsera ".

Używany język zarejestrował klasę projektanta, która nie pochodzi od poprawnej klasy bazowej. Skontaktuj się z dostawcą używanego języka.

### <a name="the-name-name-is-already-used-by-another-object"></a>Nazwa "\<Name >" jest już używana przez inny obiekt

Jest to błąd wewnętrzny w serializatorze programu Visual Studio. Jeśli widzisz ten błąd, zarejestruj problem, korzystając z [raportu o problemie](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).

### <a name="the-object-object-name-does-not-implement-the-icomponent-interface"></a>Obiekt "\<Object Name >" nie implementuje interfejsu IComponent

Program Visual Studio próbował utworzyć składnik, ale utworzony obiekt nie implementuje <xref:System.ComponentModel.IComponent> interfejsu. Aby rozwiązać problem, skontaktuj się z dostawcą składnika.

### <a name="the-object-object-name-returned-null-for-the-property-property-name-but-this-is-not-allowed"></a>Obiekt "\<Object Name >" zwrócił wartość null dla właściwości "\<Property Name >", ale nie jest to dozwolone

Istnieją pewne właściwości platformy .NET, które powinny zawsze zwracać obiekt. Na przykład kolekcja **Controls** formularza powinna zawsze zwracać obiekt, nawet jeśli nie ma żadnych kontrolek.

Aby naprawić ten błąd, upewnij się, że właściwość określona w błędzie nie ma wartości null.

### <a name="the-serialization-data-object-is-not-of-the-proper-type"></a>Obiekt danych serializacji nie jest obiektem właściwego typu

Obiekt danych oferowany przez serializator nie jest wystąpieniem typu, który jest zgodny z aktualnie używanym serializatorem. Skontaktuj się z dostawcą składnika.

### <a name="the-service-service-name-is-required-but-could-not-be-located"></a>Nazwa usługi "\<>" jest wymagana, ale nie można jej zlokalizować

Komunikat o błędzie: Nazwa usługi "Service\<" > "jest wymagana, ale nie można jej zlokalizować. Może wystąpić problem z instalacją programu Visual Studio ".

Usługa wymagana przez program Visual Studio jest niedostępna. Jeśli próbujesz załadować projekt, który nie obsługuje tego projektanta, użyj edytora kodu, aby wprowadzić wymagane zmiany. W przeciwnym razie, jeśli ten błąd wystąpi, należy zgłosić problem przy użyciu polecenia [Zgłoś problem](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).

### <a name="the-service-instance-must-derive-from-or-implement-interface-name"></a>Wystąpienie usługi musi być pochodną lub zaimplementować "\<nazwa interfejsu >".

Ten błąd wskazuje, że składnik lub Projektant składników nazywa metodę **AddService** , która wymaga interfejsu i obiektu, ale określony obiekt nie implementuje określonego interfejsu. Skontaktuj się z dostawcą składnika.

### <a name="the-text-in-the-code-window-could-not-be-modified"></a>Tekst w oknie kodu nie może zostać zmodyfikowany

Komunikat o błędzie: "Tekst w oknie kodu nie mógł zostać zmodyfikowany. Sprawdź, czy plik nie jest tylko do odczytu i czy jest wystarczająca ilość miejsca na dysku ".

Ten błąd występuje, gdy program Visual Studio nie może edytować pliku z powodu problemów z ilością miejsca na dysku lub pamięci albo plik jest oznaczony jako tylko do odczytu.

### <a name="the-toolbox-enumerator-object-only-supports-retrieving-one-item-at-a-time"></a>Obiekt modułu wyliczającego przybornika obsługuje jedynie pobieranie pojedynczego elementu

Jeśli ten błąd jest wyświetlany, w przypadku wystąpienia tego błędu należy zgłosić problem, korzystając z [raportu](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).

### <a name="the-toolbox-item-for-component-name-could-not-be-retrieved-from-the-toolbox"></a>Nie można pobrać elementu przybornika dla "\<nazwa składnika >" z przybornika

Komunikat o błędzie: "Elementu przybornika dla nazwy\<składnika" > "nie można pobrać z przybornika. Upewnij się, że zestaw zawierający element przybornika jest prawidłowo zainstalowany. Element przybornika zgłosił następujący błąd: \<ciąg błędu > ".

Przedmiotowy składnik zgłosił wyjątek, gdy program Visual Studio uzyskał do niego dostęp. Skontaktuj się z dostawcą składnika.

### <a name="the-toolbox-item-for-toolbox-item-name-could-not-be-retrieved-from-the-toolbox"></a>Nie można pobrać elementu przybornika dla "\<nazwa elementu przybornika >" z przybornika

Komunikat o błędzie: "Nie można pobrać elementu przybornika dla\<nazwy elementu przybornika >" z przybornika. Spróbuj usunąć element z przybornika i dodać go ponownie. "

Ten błąd występuje, gdy dane w obrębie elementu przybornika przestaną być uszkodzone lub wersja składnika uległa zmianie. Spróbuj usunąć element z przybornika i dodać go ponownie.

### <a name="the-type-type-name-could-not-be-found"></a>Nie można znaleźć\<typu "nazwa typu >"

Komunikat o błędzie: Nie można znaleźć nazwy\<typu "Type" > ". Upewnij się, że zestaw zawierający typ jest przywoływany. Jeśli zestaw jest częścią bieżącego projektu programistycznego, upewnij się, że projekt został skompilowany.

Podczas ładowania projektanta program Visual Studio nie może odnaleźć typu. Upewnij się, że zestaw zawierający typ jest przywoływany. Jeśli zestaw jest częścią bieżącego projektu programistycznego, upewnij się, że projekt został skompilowany.

### <a name="the-type-resolution-service-may-only-be-called-from-the-main-application-thread"></a>Usługa rozpoznawania typów może być wywołana tylko z głównego wątku aplikacji

Program Visual Studio próbował uzyskać dostęp do wymaganych zasobów z niewłaściwego wątku. Ten błąd jest wyświetlany, gdy kod używany do tworzenia projektanta nosi nazwę usługi rozpoznawania typów z wątku innego niż główny wątek aplikacji. Aby naprawić ten błąd, Wywołaj usługę z właściwego wątku lub skontaktuj się z dostawcą składnika.

### <a name="the-variable-variable-name-is-either-undeclared-or-was-never-assigned"></a>Zmienna "\<nazwa zmiennej >" jest niezadeklarowana lub nigdy nie została przypisana

Kod źródłowy zawiera odwołanie do zmiennej, takiej jak **Button1**, która nie została zadeklarowana ani przypisana. Jeśli zmienna nie została przypisana, ten komunikat pojawia się jako ostrzeżenie, a nie błąd.

### <a name="there-is-already-a-command-handler-for-the-menu-command-menu-command-name"></a>Istnieje już procedura obsługi poleceń dla polecenia menu "\<nazwa polecenia menu >"

Ten błąd występuje, gdy projektant innych firm dodaje polecenie, które ma już procedurę obsługi do tabeli poleceń. Skontaktuj się z dostawcą składnika.

### <a name="there-is-already-a-component-named-component-name"></a>Istnieje już składnik o nazwie "\<nazwa składnika >"

Komunikat o błędzie: "Istnieje już składnik o nazwie" nazwa\<składnika ">". Składniki muszą mieć unikatowe nazwy, a nazwy nie mogą być rozróżniane wielkości liter. Nazwa nie może również powodować konfliktu z nazwą żadnego składnika w dziedziczonej klasie. "

Ten komunikat o błędzie występuje w przypadku zmiany nazwy składnika w okno Właściwości. Aby naprawić ten błąd, upewnij się, że wszystkie nazwy składników są unikatowe, nie są rozróżniane wielkości liter i nie powodują konfliktów z nazwami składników w klasach dziedziczonych.

### <a name="there-is-already-a-toolbox-item-creator-registered-for-the-format-format-name"></a>Istnieje już twórca elementu przybornika zarejestrowano dla formatu "\<format nazwy >"

Składnik innej firmy wykonał wywołanie zwrotne do elementu na karcie przybornika, ale element już zawierał wywołanie zwrotne. Skontaktuj się z dostawcą składnika.

### <a name="this-language-engine-does-not-support-a-codemodel-with-which-to-load-a-designer"></a>Ten silnik języka nie obsługuje „CodeModel", który ma służyć do załadowania projektanta

Ten komunikat jest podobny do "język tego pliku nie obsługuje niezbędnych usług analizy i generowania kodu", ale ten komunikat obejmuje problem z rejestracją wewnętrzną. Jeśli ten błąd jest wyświetlany, w przypadku wystąpienia tego błędu należy zgłosić problem, korzystając z [raportu](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).

### <a name="type-type-name-does-not-have-a-constructor-with-parameters-of-types-parameter-type-names"></a>Typ "\<type name\>" nie ma konstruktora z parametrami typów "\<>"

Program Visual Studio nie może znaleźć [konstruktora](/dotnet/csharp/programming-guide/classes-and-structs/constructors) , który miał zgodne parametry. Może to być wynikiem dostarczenia konstruktora z typami innymi niż te, które są wymagane. Na przykład Konstruktor **punktów** może przyjmować dwie liczby całkowite. Jeśli podano wartości zmiennoprzecinkowe, ten błąd jest wywoływany.

Aby naprawić ten błąd, użyj innego konstruktora lub jawnie rzutowanie typów parametrów, tak aby były one zgodne z wartościami dostarczonymi przez konstruktora.

### <a name="unable-to-add-reference-reference-name-to-the-current-application"></a>Nie można dodać odwołania "\<Nazwa referencyjna >" do bieżącej aplikacji

Komunikat o błędzie: "Nie można dodać nazwy odwołania\<" > "do bieżącej aplikacji. Sprawdź, czy nie ma już odwołania\<do innej wersji "Nazwa referencyjna >".

Program Visual Studio nie może dodać odwołania. Aby naprawić ten błąd, sprawdź, czy nie ma już odwołania do innej wersji odwołania.

### <a name="unable-to-check-out-the-current-file"></a>Nie można wyewidencjonować bieżącego pliku

Komunikat o błędzie: "Nie można wyewidencjonować bieżącego pliku. Plik może być zablokowany lub może być konieczne ręczne Wyewidencjonuj plik ".

Ten błąd występuje, gdy zmieniasz plik, który jest aktualnie zaewidencjonowany w kontroli kodu źródłowego. Zwykle program Visual Studio Wyświetla okno dialogowe wyewidencjonowywanie plików, dzięki czemu użytkownik może wyewidencjonować plik. Tym razem plik nie został wyewidencjonowany, prawdopodobnie z powodu konfliktu scalania podczas wyewidencjonowania. Aby naprawić ten błąd, upewnij się, że plik nie jest zablokowany, a następnie spróbuj ręcznie wyewidencjonować plik.

### <a name="unable-to-find-page-named-options-dialog-box-tab-name"></a>Nie można odnaleźć nazwy karty okna\<dialogowego opcji o nazwie ">"

Ten błąd występuje, gdy Projektant składników żąda dostępu do strony z okna dialogowego Opcje przy użyciu nazwy, która nie istnieje. Skontaktuj się z dostawcą składnika.

### <a name="unable-to-find-property-property-name-on-page-options-dialog-box-tab-name"></a>Nie można znaleźć właściwości "\<nazwa właściwości >" w nazwie karty\<okna dialogowego opcji strony > "

Ten błąd występuje, gdy Projektant składników żąda dostępu do określonej wartości na stronie z okna dialogowego Opcje, ale ta wartość nie istnieje. Skontaktuj się z dostawcą składnika.

### <a name="visual-studio-cannot-open-a-designer-for-the-file-because-the-class-within-it-does-not-inherit-from-a-class-that-can-be-visually-designed"></a>Visual Studio nie może otworzyć projektanta dla pliku, ponieważ klasa w tym projektancie nie dziedziczy z klasy, którą można zaprojektować wizualnie

Program Visual Studio załadował klasę, ale nie można załadować projektanta dla tej klasy. Program Visual Studio wymaga, aby projektanci używali pierwszej klasy w pliku. Aby naprawić ten błąd, Przenieś kod klasy tak, aby był to pierwsza klasa w pliku, a następnie ponownie załaduj projektanta.

### <a name="visual-studio-cannot-save-or-load-instances-of-the-type-type-name"></a>Program Visual Studio nie może zapisać ani załadować wystąpień typu "\<nazwa typu >".

Jest to problem związany ze składnikiem innej firmy. Skontaktuj się z dostawcą składnika.

### <a name="visual-studio-is-unable-to-open-document-name-in-design-view"></a>Program Visual Studio nie może otworzyć "\<> nazwy dokumentu" w widok Projekt

Komunikat o błędzie: "Program Visual Studio nie może otworzyć"\<> nazwy dokumentu "w widok Projekt. Nie zainstalowano parsera dla typu pliku ".

Ten błąd wskazuje, że język projektu nie obsługuje projektanta i występuje podczas próby otwarcia pliku w oknie dialogowym Otwórz plik lub z Eksplorator rozwiązań. Zamiast tego Edytuj plik w widoku kodu.

### <a name="visual-studio-was-unable-to-find-a-designer-for-classes-of-type-type-name"></a>Program Visual Studio nie może odnaleźć projektanta dla klas typu "\<type name >"

Program Visual Studio załadował klasę, ale nie można zaprojektować klasy. Zamiast tego Edytuj klasę w widoku kodu, klikając ją prawym przyciskiem myszy i wybierając polecenie **Wyświetl kod**.

## <a name="see-also"></a>Zobacz także

- [Opracowywanie formantów Windows Forms przy użyciu narzędzia Projektant](developing-windows-forms-controls-at-design-time.md)
- [Forum Projektant formularzy systemu Windows](https://social.msdn.microsoft.com/Forums/windows/home?forum=winformsdesigner)
