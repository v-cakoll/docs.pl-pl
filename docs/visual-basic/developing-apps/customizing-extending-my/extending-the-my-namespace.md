---
title: Rozszerzanie przestrzeni nazw My w Visual Basic
ms.date: 07/20/2015
f1_keywords:
- vb.AddingMyExtensions
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: 808e8617-b01c-4135-8b21-babe87389e8e
ms.openlocfilehash: 6da0914c9d2d4dc1220ede5d6fa9f1aa6b43426a
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775298"
---
# <a name="extending-the-my-namespace-in-visual-basic"></a>Rozszerzanie przestrzeni nazw `My` w Visual Basic

Przestrzeń nazw `My` w Visual Basic udostępnia właściwości i metody, które pozwalają łatwo wykorzystać możliwości .NET Framework. Przestrzeń nazw `My` upraszcza typowe problemy z programowaniem, często skracając trudnym zadaniem do jednego wiersza kodu. Ponadto przestrzeń nazw `My` jest w pełni rozszerzalna, aby można było dostosować zachowanie `My` i dodać nowe usługi do swojej hierarchii, aby dostosować je do konkretnych potrzeb aplikacji. W tym temacie omówiono sposób dostosowywania istniejących członków przestrzeni nazw `My` i sposobu dodawania własnych klas niestandardowych do przestrzeni nazw `My`.

## <a name="customizing-existing-my-namespace-members"></a>Dostosowywanie istniejących członków przestrzeni nazw `My`

Przestrzeń nazw `My` w Visual Basic uwidacznia często używane informacje o aplikacji, komputerze i innych. Aby zapoznać się z pełną listą obiektów w przestrzeni nazw `My`, zobacz [Moje odwołanie](../../language-reference/keywords/my-reference.md). Może być konieczne dostosowanie istniejących członków przestrzeni nazw `My`, aby lepiej odpowiadały potrzebom aplikacji. Każda właściwość obiektu w przestrzeni nazw `My`, która nie jest tylko do odczytu, może być ustawiona na wartość niestandardową.

Załóżmy na przykład, że często używasz obiektu `My.User`, aby uzyskać dostęp do bieżącego kontekstu zabezpieczeń dla użytkownika, na którym uruchomiono aplikację. Jednak firma używa niestandardowego obiektu użytkownika w celu udostępnienia dodatkowych informacji i możliwości dla użytkowników w firmie. W tym scenariuszu można zastąpić wartość domyślną właściwości `My.User.CurrentPrincipal` przy użyciu wystąpienia własnego niestandardowego obiektu podmiotu zabezpieczeń, jak pokazano w następującym przykładzie:

[!code-vb[VbVbcnExtendingMy#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#1)]

Ustawienie właściwości `CurrentPrincipal` obiektu `My.User` zmienia tożsamość, w której działa aplikacja. Obiekt `My.User`, z kolei zwraca informacje o nowo określonym użytkowniku.
  
## <a name="adding-members-to-my-objects"></a>Dodawanie elementów członkowskich do `My` obiektów

Typy zwracane z `My.Application` i `My.Computer` są zdefiniowane jako klasy `Partial`. W związku z tym można rozciągnąć `My.Application` i `My.Computer` obiekty przez utworzenie klasy `Partial` o nazwie `MyApplication` lub `MyComputer`. Klasa nie może być klasą `Private`. W przypadku określenia klasy jako części przestrzeni nazw `My` można dodać właściwości i metody, które zostaną dołączone do obiektów `My.Application` lub `My.Computer`.

Poniższy przykład dodaje właściwość o nazwie `DnsServerIPAddresses` do obiektu `My.Computer`:

[!code-vb[VbVbcnExtendingMy#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class2.vb#2)]

## <a name="adding-custom-objects-to-the-my-namespace"></a>Dodawanie niestandardowych obiektów do przestrzeni nazw `My`

Chociaż przestrzeń nazw `My` zawiera rozwiązania dla wielu typowych zadań programistycznych, mogą wystąpić zadania, które nie są adresami `My` przestrzeni nazw. Na przykład aplikacja może uzyskiwać dostęp do niestandardowych usług katalogowych dla danych użytkownika lub aplikacja może korzystać z zestawów, które nie są instalowane domyślnie z Visual Basic. Można zwiększyć przestrzeń nazw `My`, aby uwzględnić niestandardowe rozwiązania typowych zadań, które są specyficzne dla danego środowiska. Przestrzeń nazw `My` można łatwo rozszerzyć, aby dodać nowych członków w celu spełnienia rosnących potrzeb aplikacji. Ponadto można wdrożyć rozszerzenia przestrzeni nazw `My` dla innych deweloperów jako szablon Visual Basic.
  
### <a name="adding-members-to-the-my-namespace"></a>Dodawanie członków do przestrzeni nazw `My`

Ponieważ `My` jest przestrzenią nazw, taką jak jakakolwiek inna przestrzeń nazw, można dodać do niej właściwości najwyższego poziomu, dodając moduł i określając `Namespace` `My`. Dodaj adnotację do modułu z atrybutem `HideModuleName`, jak pokazano w poniższym przykładzie. Atrybut `HideModuleName` zapewnia, że funkcja IntelliSense nie będzie wyświetlała nazwy modułu podczas wyświetlania elementów członkowskich `My` przestrzeni nazw.

[!code-vb[VbVbcnExtendingMy#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#3)]

Aby dodać elementy członkowskie do przestrzeni nazw `My`, Dodaj do modułu odpowiednie właściwości. Dla każdej właściwości dodanej do przestrzeni nazw `My` Dodaj pole private typu `ThreadSafeObjectProvider(Of T)`, gdzie typ jest typem zwracanym przez właściwość niestandardową. To pole służy do tworzenia wystąpień obiektów bezpiecznych dla wątków, które mają być zwracane przez właściwość przez wywołanie metody `GetInstance`. W związku z tym każdy wątek, który uzyskuje dostęp do właściwości rozszerzonej, odbiera własne wystąpienie zwróconego typu. Poniższy przykład dodaje właściwość o nazwie `SampleExtension`, która jest typu `SampleExtension` do przestrzeni nazw `My`:

[!code-vb[VbVbcnExtendingMy#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#4)]

## <a name="adding-events-to-custom-my-objects"></a>Dodawanie zdarzeń do niestandardowych obiektów `My`

Można użyć obiektu `My.Application`, aby uwidocznić zdarzenia dla niestandardowych obiektów `My`, rozszerzając klasę `MyApplication` częściową w przestrzeni nazw `My`. W przypadku projektów opartych na systemie Windows można kliknąć dwukrotnie węzeł **mój projekt** w programie dla projektu w **Eksplorator rozwiązań**. W **projektancie projektu**Visual Basic kliknij kartę **aplikacja** , a następnie kliknij przycisk **Wyświetl zdarzenia aplikacji** . Zostanie utworzony nowy plik o nazwie *ApplicationEvents. vb* . Zawiera poniższy kod rozszerzający klasę `MyApplication`:

[!code-vb[VbVbcnExtendingMy#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#5)]

Obsługę zdarzeń można dodać do niestandardowych obiektów `My`, dodając niestandardowe programy obsługi zdarzeń do klasy `MyApplication`. Zdarzenia niestandardowe umożliwiają dodanie kodu, który będzie wykonywany po dodaniu lub usunięciu procedury obsługi zdarzeń. Należy zauważyć, że kod `AddHandler` dla zdarzenia niestandardowego jest uruchamiany tylko wtedy, gdy użytkownik dodaliśmy kod, aby obsłużyć zdarzenie. Rozważmy na przykład, że obiekt `SampleExtension` z poprzedniej sekcji ma zdarzenie `Load`, dla którego chcesz dodać obsługę zdarzeń niestandardowych. Poniższy przykład kodu pokazuje niestandardowy program obsługi zdarzeń o nazwie `SampleExtensionLoad`, który zostanie wywołany, gdy wystąpi zdarzenie `My.SampleExtension.Load`. Po dodaniu kodu do obsługi nowego zdarzenia `My.SampleExtensionLoad` jest wykonywany `AddHandler` część tego niestandardowego kodu zdarzenia. Metoda `MyApplication_SampleExtensionLoad` jest dołączona do przykładu kodu, aby pokazać przykład programu obsługi zdarzeń, który obsługuje zdarzenie `My.SampleExtensionLoad`. Należy pamiętać, że zdarzenie `SampleExtensionLoad` będzie dostępne po wybraniu opcji **Moje zdarzenia aplikacji** z lewej listy rozwijanej powyżej edytora kodu podczas edytowania pliku *ApplicationEvents. vb* .

[!code-vb[VbVbcnExtendingMy#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#6)]

## <a name="design-guidelines"></a>Wytyczne dotyczące projektowania

Podczas tworzenia rozszerzeń do przestrzeni nazw `My` należy skorzystać z poniższych wskazówek, aby zminimalizować koszty konserwacji składników rozszerzeń:

- **Uwzględnij tylko logikę rozszerzenia.** Logika uwzględniona w rozszerzeniu przestrzeni nazw `My` powinna zawierać tylko kod, który jest potrzebny do udostępnienia wymaganych funkcji w przestrzeni nazw `My`. Ponieważ Twoje rozszerzenie będzie znajdować się w projektach użytkownika jako kod źródłowy, aktualizowanie składnika rozszerzenia wiąże się z wysokim kosztem konserwacji i należy je unikać, jeśli jest to możliwe.
- **Minimalizuj założenia projektu.** Podczas tworzenia rozszerzeń przestrzeni nazw `My` nie należy przyjmować zestawu odwołań, importów na poziomie projektu ani ustawień określonego kompilatora (na przykład `Option Strict` wyłączone). Zamiast tego należy zminimalizować zależności i w pełni kwalifikować wszystkie odwołania do typu za pomocą słowa kluczowego `Global`. Ponadto upewnij się, że rozszerzenie kompiluje się z `Option Strict` on, aby zminimalizować błędy w rozszerzeniu.
- **Izoluj kod rozszerzenia.** Umieszczenie kodu w pojedynczym pliku sprawia, że rozszerzenie jest łatwo wdrożone jako szablon elementu programu Visual Studio. Aby uzyskać więcej informacji, zobacz sekcję "Pakowanie i wdrażanie rozszerzeń" w dalszej części tego tematu. Umieszczenie całego kodu rozszerzenia przestrzeni nazw `My` w jednym pliku lub oddzielnym folderze w projekcie ułatwi użytkownikom znalezienie rozszerzenia `My` przestrzeni nazw.

## <a name="designing-class-libraries-for-my"></a>Projektowanie bibliotek klas dla `My`

Podobnie jak w przypadku większości modeli obiektów, niektóre wzorce projektowania działają prawidłowo w przestrzeni nazw `My` i inne nie. Podczas projektowania rozszerzenia do przestrzeni nazw `My` należy wziąć pod uwagę następujące zasady:

- **Metody bezstanowe.** Metody w przestrzeni nazw `My` powinny dostarczyć kompletne rozwiązanie do określonego zadania. Upewnij się, że wartości parametrów, które są przesyłane do metody, zapewniają wszystkie dane wejściowe wymagane do ukończenia określonego zadania. Należy unikać tworzenia metod, które są zależne od wcześniejszego stanu, na przykład otwartych połączeń z zasobami.
- **Wystąpienia globalne.** Jedynym stanem obsługiwanym w przestrzeni nazw `My` jest globalny dla projektu. Na przykład `My.Application.Info` hermetyzuje stan współużytkowany przez aplikację.
- **Proste typy parametrów.** Zachowaj prostotę, unikając złożonych typów parametrów. Zamiast tego należy utworzyć metody, które nie przyjmują danych wejściowych parametrów ani mają proste typy wejściowe, takie jak ciągi, typy pierwotne i tak dalej.
- **Metody fabryki.** Niektóre typy muszą być trudne do wystąpienia. Dostarczanie metod fabrycznych jako rozszerzeń przestrzeni nazw `My` umożliwia łatwiejsze odnajdywanie i używanie typów, które należą do tej kategorii. Przykładem metody fabryki, która działa prawidłowo, jest `My.Computer.FileSystem.OpenTextFileReader`. Istnieje kilka typów strumieni dostępnych w .NET Framework. Dzięki określeniu plików tekstowych `OpenTextFileReader` pomaga użytkownikowi zrozumieć, którego strumienia użyć.

Te wytyczne nie uniemożliwiają ogólnych zasad projektowania bibliotek klas. Nie są to zalecenia zoptymalizowane pod kątem deweloperów korzystających z Visual Basic i przestrzeni nazw `My`. Ogólne zasady projektowania dotyczące tworzenia bibliotek klas można znaleźć w temacie [wskazówki dotyczące projektowania struktury](../../../standard/design-guidelines/index.md).

## <a name="packaging-and-deploying-extensions"></a>Pakowanie i wdrażanie rozszerzeń

Można uwzględnić rozszerzenia przestrzeni nazw `My` w szablonie projektu programu Visual Studio lub można spakować rozszerzenia i wdrożyć je jako szablon elementu programu Visual Studio. W przypadku pakowania rozszerzeń przestrzeni nazw `My` jako szablonu elementu programu Visual Studio możesz skorzystać z dodatkowych możliwości zapewnianych przez Visual Basic. Te możliwości umożliwiają dołączenie rozszerzenia, gdy projekt odwołuje się do określonego zestawu, lub umożliwia użytkownikom jawne dodanie rozszerzenia przestrzeni nazw `My` przy użyciu strony **Moje rozszerzenia** w projektancie projektu Visual Basic.

Aby uzyskać szczegółowe informacje na temat wdrażania rozszerzeń przestrzeni nazw `My`, zobacz [pakowanie i wdrażanie niestandardowych rozszerzeń](packaging-and-deploying-custom-my-extensions.md).

## <a name="see-also"></a>Zobacz także

- [Pakowanie i wdrażanie niestandardowych rozszerzeń My](packaging-and-deploying-custom-my-extensions.md)
- [Rozszerzanie modelu aplikacji Visual Basic](extending-the-visual-basic-application-model.md)
- [Dostosowywanie, które obiekty są dostępne w My](customizing-which-objects-are-available-in-my.md)
- [Strona Moje rozszerzenia, Projektant projektu](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
- [Strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [Partial](../../language-reference/modifiers/partial.md)
