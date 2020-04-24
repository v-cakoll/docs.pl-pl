---
title: Rozszerzanie przestrzeni nazw My
ms.date: 07/20/2015
f1_keywords:
- vb.AddingMyExtensions
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: 808e8617-b01c-4135-8b21-babe87389e8e
ms.openlocfilehash: 2a7b0b84061fccd9a333a68e4a19477bd19ca4ff
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330321"
---
# <a name="extending-the-my-namespace-in-visual-basic"></a>Rozszerzanie `My` przestrzeni nazw w Visual Basic

`My` Przestrzeń nazw w Visual Basic udostępnia właściwości i metody, które pozwalają łatwo wykorzystać możliwości .NET Framework. `My` Przestrzeń nazw upraszcza typowe problemy z programowaniem, często skracając trudnym zadaniem do jednego wiersza kodu. Ponadto przestrzeń nazw `My` jest w pełni rozszerzalna, aby można było dostosować zachowanie `My` i dodać nowe usługi do swojej hierarchii w celu dostosowania do określonych wymagań aplikacji. W tym temacie omówiono sposób dostosowywania istniejących członków `My` przestrzeni nazw oraz dodawania własnych klas niestandardowych do `My` przestrzeni nazw.

## <a name="customizing-existing-my-namespace-members"></a>Dostosowywanie istniejących `My` członków przestrzeni nazw

`My` Przestrzeń nazw w Visual Basic uwidacznia często używane informacje o aplikacji, komputerze i innych. Aby uzyskać pełną listę obiektów w `My` przestrzeni nazw, zobacz [Moje odwołanie](../../language-reference/keywords/my-reference.md). Może być konieczne dostosowanie istniejących członków `My` przestrzeni nazw, aby lepiej odpowiadały potrzebom aplikacji. Właściwość obiektu w `My` przestrzeni nazw, który nie jest tylko do odczytu, można ustawić na wartość niestandardową.

Załóżmy na przykład, że często używasz `My.User` obiektu do uzyskiwania dostępu do bieżącego kontekstu zabezpieczeń dla użytkownika, na którym uruchomiono aplikację. Jednak firma używa niestandardowego obiektu użytkownika w celu udostępnienia dodatkowych informacji i możliwości dla użytkowników w firmie. W tym scenariuszu można zastąpić wartość domyślną `My.User.CurrentPrincipal` właściwości wystąpieniem niestandardowego obiektu podmiotu zabezpieczeń, jak pokazano w następującym przykładzie:

[!code-vb[VbVbcnExtendingMy#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#1)]

Ustawienie `CurrentPrincipal` właściwości `My.User` obiektu zmienia tożsamość, pod którą jest uruchomiona aplikacja. `My.User` Obiekt z kolei zwraca informacje o nowo określonym użytkowniku.
  
## <a name="adding-members-to-my-objects"></a>Dodawanie elementów członkowskich `My` do obiektów

Typy zwracane z `My.Application` i `My.Computer` są zdefiniowane jako `Partial` klasy. W związku z `My.Application` tym, można rozciągnąć obiekty i `My.Computer` utworzyć `Partial` klasę o `MyApplication` nazwie `MyComputer`lub. Klasa nie może być `Private` klasą. Jeśli określisz klasę jako część `My` przestrzeni nazw, możesz dodać właściwości i metody, które zostaną dołączone do `My.Application` obiektów lub. `My.Computer`

Poniższy przykład dodaje właściwość o nazwie `DnsServerIPAddresses` do `My.Computer` obiektu:

[!code-vb[VbVbcnExtendingMy#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class2.vb#2)]

## <a name="adding-custom-objects-to-the-my-namespace"></a>Dodawanie niestandardowych obiektów do `My` przestrzeni nazw

Mimo że `My` przestrzeń nazw zawiera rozwiązania dla wielu typowych zadań programistycznych, mogą wystąpić zadania, `My` które nie są adresami przestrzeni nazw. Na przykład aplikacja może uzyskiwać dostęp do niestandardowych usług katalogowych dla danych użytkownika lub aplikacja może korzystać z zestawów, które nie są instalowane domyślnie z Visual Basic. Można zwiększyć `My` przestrzeń nazw, aby uwzględnić niestandardowe rozwiązania typowych zadań, które są specyficzne dla danego środowiska. Przestrzeń `My` nazw można łatwo rozszerzyć, aby dodać nowych członków w celu spełnienia rosnących potrzeb aplikacji. Ponadto rozszerzenia `My` przestrzeni nazw można wdrożyć innym deweloperom jako szablon Visual Basic.
  
### <a name="adding-members-to-the-my-namespace"></a>Dodawanie członków do `My` przestrzeni nazw

Ponieważ `My` jest przestrzenią nazw, taką jak jakakolwiek inna przestrzeń nazw, można dodać do niej właściwości najwyższego poziomu, dodając moduł `Namespace` i `My`podając wartość. Dodaj adnotację do modułu z `HideModuleName` atrybutem, jak pokazano w poniższym przykładzie. Ten `HideModuleName` atrybut gwarantuje, że funkcja IntelliSense nie będzie wyświetlać nazwy modułu, gdy wyświetla elementy członkowskie `My` przestrzeni nazw.

[!code-vb[VbVbcnExtendingMy#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#3)]

Aby dodać elementy członkowskie do `My` przestrzeni nazw, Dodaj do modułu właściwości zgodnie z wymaganiami. Dla każdej właściwości dodanej `My` do przestrzeni nazw Dodaj pole prywatne typu `ThreadSafeObjectProvider(Of T)`, gdzie typ jest typem zwracanym przez właściwość niestandardową. To pole służy do tworzenia wystąpień obiektów bezpiecznych dla wątków, które mają być zwracane przez właściwość przez wywołanie `GetInstance` metody. W związku z tym każdy wątek, który uzyskuje dostęp do właściwości rozszerzonej, odbiera własne wystąpienie zwróconego typu. Poniższy przykład dodaje właściwość o nazwie `SampleExtension` , która jest typu `SampleExtension` do `My` przestrzeni nazw:

[!code-vb[VbVbcnExtendingMy#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#4)]

## <a name="adding-events-to-custom-my-objects"></a>Dodawanie zdarzeń do obiektów `My` niestandardowych

Można użyć obiektu, `My.Application` Aby uwidocznić zdarzenia dla obiektów niestandardowych `My` przez rozszerzenie klasy `MyApplication` częściowej w `My` przestrzeni nazw. W przypadku projektów opartych na systemie Windows można kliknąć dwukrotnie węzeł **mój projekt** w programie dla projektu w **Eksplorator rozwiązań**. W **projektancie projektu**Visual Basic kliknij kartę **aplikacja** , a następnie kliknij przycisk **Wyświetl zdarzenia aplikacji** . Zostanie utworzony nowy plik o nazwie *ApplicationEvents. vb* . Zawiera następujący kod służący do rozszerzania `MyApplication` klasy:

[!code-vb[VbVbcnExtendingMy#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#5)]

Obsługę zdarzeń dla obiektów niestandardowych `My` można dodać, dodając niestandardowe programy obsługi zdarzeń do `MyApplication` klasy. Zdarzenia niestandardowe umożliwiają dodanie kodu, który będzie wykonywany po dodaniu lub usunięciu procedury obsługi zdarzeń. Należy zauważyć, `AddHandler` że kod dla zdarzenia niestandardowego jest uruchamiany tylko wtedy, gdy użytkownik dodaje kod do obsługi zdarzenia. Rozważmy na przykład, że `SampleExtension` obiekt z poprzedniej sekcji ma `Load` zdarzenie, dla którego chcesz dodać program obsługi zdarzeń niestandardowych. Poniższy przykład kodu pokazuje niestandardowy program obsługi zdarzeń o nazwie `SampleExtensionLoad` , który zostanie wywołany po `My.SampleExtension.Load` wystąpieniu zdarzenia. Po dodaniu kodu do obsługi nowego `My.SampleExtensionLoad` zdarzenia jest wykonywane `AddHandler` część tego niestandardowego kodu zdarzenia. `MyApplication_SampleExtensionLoad` Metoda jest dołączona do przykładu kodu, aby pokazać przykład programu obsługi zdarzeń, który obsługuje `My.SampleExtensionLoad` zdarzenie. Należy zauważyć, `SampleExtensionLoad` że zdarzenie będzie dostępne po wybraniu opcji **Moje zdarzenia aplikacji** z lewej listy rozwijanej powyżej edytora kodu podczas edytowania pliku *ApplicationEvents. vb* .

[!code-vb[VbVbcnExtendingMy#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#6)]

## <a name="design-guidelines"></a>Wytyczne dotyczące projektowania

Podczas tworzenia rozszerzeń do `My` przestrzeni nazw należy skorzystać z poniższych wskazówek, aby zminimalizować koszty konserwacji składników rozszerzeń:

- **Uwzględnij tylko logikę rozszerzenia.** Logika uwzględniona w `My` rozszerzeniu przestrzeni nazw powinna zawierać tylko kod, który jest potrzebny do udostępnienia wymaganych funkcji `My` w przestrzeni nazw. Ponieważ Twoje rozszerzenie będzie znajdować się w projektach użytkownika jako kod źródłowy, aktualizowanie składnika rozszerzenia wiąże się z wysokim kosztem konserwacji i należy je unikać, jeśli jest to możliwe.
- **Minimalizuj założenia projektu.** Podczas tworzenia rozszerzeń `My` przestrzeni nazw nie należy zakładać zestawu odwołań, importów na poziomie projektu ani ustawień określonego kompilatora (na przykład `Option Strict` wyłączonych). Zamiast tego należy zminimalizować zależności i w pełni kwalifikować wszystkie odwołania do typu `Global` za pomocą słowa kluczowego. Upewnij się również, że rozszerzenie kompiluje się `Option Strict` z on, aby zminimalizować błędy w rozszerzeniu.
- **Izoluj kod rozszerzenia.** Umieszczenie kodu w pojedynczym pliku sprawia, że rozszerzenie jest łatwo wdrożone jako szablon elementu programu Visual Studio. Aby uzyskać więcej informacji, zobacz sekcję "Pakowanie i wdrażanie rozszerzeń" w dalszej części tego tematu. Umieszczenie całego kodu `My` rozszerzenia przestrzeni nazw w jednym pliku lub osobnym folderze w projekcie ułatwi użytkownikom lokalizowanie rozszerzenia `My` przestrzeni nazw.

## <a name="designing-class-libraries-for-my"></a>Projektowanie bibliotek klas dla`My`

Podobnie jak w przypadku większości modeli obiektów, niektóre wzorce projektowania działają dobrze w `My` przestrzeni nazw, a inne nie. Podczas projektowania rozszerzenia do `My` przestrzeni nazw należy wziąć pod uwagę następujące zasady:

- **Metody bezstanowe.** Metody w `My` przestrzeni nazw powinny dostarczyć kompletne rozwiązanie do określonego zadania. Upewnij się, że wartości parametrów, które są przesyłane do metody, zapewniają wszystkie dane wejściowe wymagane do ukończenia określonego zadania. Należy unikać tworzenia metod, które są zależne od wcześniejszego stanu, na przykład otwartych połączeń z zasobami.
- **Wystąpienia globalne.** Jedynym stanem obsługiwanym w `My` przestrzeni nazw jest globalny dla projektu. Na przykład `My.Application.Info` hermetyzuje stan współużytkowany przez aplikację.
- **Proste typy parametrów.** Zachowaj prostotę, unikając złożonych typów parametrów. Zamiast tego należy utworzyć metody, które nie przyjmują danych wejściowych parametrów ani mają proste typy wejściowe, takie jak ciągi, typy pierwotne i tak dalej.
- **Metody fabryki.** Niektóre typy muszą być trudne do wystąpienia. Dostarczanie metod fabrycznych jako rozszerzeń do `My` przestrzeni nazw pozwala łatwiej odnajdywać i korzystać z typów, które należą do tej kategorii. Przykładem metody fabryki, która dobrze się `My.Computer.FileSystem.OpenTextFileReader`sprawdza. Istnieje kilka typów strumieni dostępnych w .NET Framework. Określenie plików tekstowych w `OpenTextFileReader` specjalny sposób pomaga użytkownikowi zrozumieć, którego strumienia użyć.

Te wytyczne nie uniemożliwiają ogólnych zasad projektowania bibliotek klas. Są to zalecenia, które są zoptymalizowane dla deweloperów, którzy używają Visual Basic i `My` przestrzeni nazw. Ogólne zasady projektowania dotyczące tworzenia bibliotek klas można znaleźć w temacie [wskazówki dotyczące projektowania struktury](../../../standard/design-guidelines/index.md).

## <a name="packaging-and-deploying-extensions"></a>Pakowanie i wdrażanie rozszerzeń

Można uwzględnić `My` rozszerzenia przestrzeni nazw w szablonie projektu programu Visual Studio lub spakować rozszerzenia i wdrożyć je jako szablon elementu programu Visual Studio. W przypadku pakowania rozszerzeń `My` przestrzeni nazw jako szablonu elementu programu Visual Studio możesz skorzystać z dodatkowych możliwości zapewnianych przez Visual Basic. Te możliwości umożliwiają dołączenie rozszerzenia, gdy projekt odwołuje się do określonego zestawu, lub umożliwia użytkownikom jawne dodanie rozszerzenia `My` przestrzeni nazw za pomocą strony **Moje rozszerzenia** w projektancie projektu Visual Basic.

Aby uzyskać szczegółowe informacje o sposobie `My` wdrażania rozszerzeń przestrzeni nazw, zobacz [pakowanie i wdrażanie niestandardowych rozszerzeń my](packaging-and-deploying-custom-my-extensions.md).

## <a name="see-also"></a>Zobacz też

- [Pakowanie i wdrażanie niestandardowych rozszerzeń My](packaging-and-deploying-custom-my-extensions.md)
- [Rozszerzanie modelu aplikacji Visual Basic](extending-the-visual-basic-application-model.md)
- [Dostosowywanie, które obiekty są dostępne w My](customizing-which-objects-are-available-in-my.md)
- [Strona Moje rozszerzenia, Projektant projektu](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
- [Strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [Częściowe](../../language-reference/modifiers/partial.md)
