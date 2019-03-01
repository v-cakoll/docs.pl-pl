---
title: Rozszerzanie przestrzeni nazw My w Visual Studio
ms.date: 07/20/2015
f1_keywords:
- vb.AddingMyExtensions
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: 808e8617-b01c-4135-8b21-babe87389e8e
ms.openlocfilehash: de3403be4a23283d27887c149ed62df37e13c334
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975384"
---
# <a name="extending-the-my-namespace-in-visual-basic"></a>Rozszerzanie przestrzeni nazw My w Visual Studio
`My` Przestrzeni nazw w języku Visual Basic udostępnia właściwości i metod, które umożliwiają użytkownikowi łatwo korzystać z możliwości programu .NET Framework. `My` Przestrzeni nazw upraszcza typowe problemy programowania, często zmniejszanie trudne do jednego wiersza kodu. Ponadto `My` przestrzeń nazw jest całkowicie rozszerzalny, dzięki czemu możesz dostosować zachowanie `My` i dodawanie nowych usług do swojej hierarchii w celu dostosowania do potrzeb konkretnej aplikacji. W tym temacie omówiono zarówno jak dostosować istniejący członkowie `My` przestrzeni nazw oraz sposób dodawania niestandardowych klas do `My` przestrzeni nazw.  
  
 **Zawartość tematów**  
  
-   [Dostosowywanie istniejących członków mojego Namespace](#customizing)  
  
-   [Dodawanie członków do mojego obiektów](#addingtoobjects)  
  
-   [Dodawanie niestandardowych obiektów do mojego Namespace](#addingcustom)  
  
-   [Dodawanie członków do mojego Namespace](#addingtonamespace)  
  
-   [Dodawanie zdarzeń do niestandardowego Moje obiekty](#addingevents)  
  
-   [Wytyczne dotyczące projektowania](#design)  
  
-   [Projektowanie bibliotek klas dla mojego](#designing)  
  
-   [Pakowanie i wdrażanie rozszerzeń](#packaging)  
  
##  <a name="customizing"></a> Dostosowywanie istniejących członków mojego Namespace  
 `My` Przestrzeni nazw w Visual Basic ujawnia często używane informacje o aplikacji i komputera. Aby uzyskać pełną listę obiektów w `My` przestrzeni nazw, zobacz [Moje odwołanie](../../../visual-basic/language-reference/keywords/my-reference.md). Być może trzeba dostosować istniejący członkowie `My` przestrzeni nazw, dzięki czemu mogą lepiej odpowiadały potrzebom aplikacji. Wszystkie właściwości obiektu w `My` przestrzeni nazw, który nie jest tylko do odczytu można ustawić na wartość niestandardową.  
  
 Na przykład, załóżmy, że często `My.User` obiektu do uzyskania dostępu bieżącego kontekstu zabezpieczeń dla użytkownika uruchamiającego aplikację. Jednak firma korzysta z obiektem użytkownika niestandardowego do udostępnienia dodatkowych informacji i możliwości dla użytkowników w firmie. W tym scenariuszu możesz zastąpić wartość domyślną `My.User.CurrentPrincipal` właściwości z wystąpieniem własny niestandardowy obiekt podmiotu zabezpieczeń, jak pokazano w poniższym przykładzie.  
  
 [!code-vb[VbVbcnExtendingMy#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#1)]  
  
 Ustawienie `CurrentPrincipal` właściwość `My.User` zmianach obiektu tożsamości, w ramach której działa aplikacja. `My.User` Obiektu, z kolei zwraca informacje o nowo określonego użytkownika.  
  
##  <a name="addingtoobjects"></a> Dodawanie członków do mojego obiektów  
 Typy zwracane z `My.Application` i `My.Computer` są definiowane jako `Partial` klasy. W związku z tym, można rozszerzyć `My.Application` i `My.Computer` obiektów, tworząc `Partial` klasę o nazwie `MyApplication` lub `MyComputer`. Klasa nie może być `Private` klasy. W przypadku określenia klasy jako część `My` przestrzeni nazw, można dodać właściwości i metod, które będą dołączone `My.Application` lub `My.Computer` obiektów.  
  
 Na przykład, poniższy przykład dodaje właściwość o nazwie `DnsServerIPAddresses` do `My.Computer` obiektu.  
  
 [!code-vb[VbVbcnExtendingMy#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class2.vb#2)]  
  
##  <a name="addingcustom"></a> Dodawanie niestandardowych obiektów do mojego Namespace  
 Mimo że `My` przestrzeń nazw zapewnia rozwiązania typowych zadań programistycznych, możesz napotkać zadania, `My` nie rozwiążą przestrzeni nazw. Na przykład aplikacja może uzyskać dostęp do usług katalogu niestandardowego dla danych użytkownika lub aplikacja może używać zestawów, które nie są instalowane domyślnie w języku Visual Basic. Możesz rozszerzyć `My` namespace, aby uwzględnić niestandardowe rozwiązania do typowych zadań, które są specyficzne dla danego środowiska. `My` Przestrzeni nazw można łatwo rozszerzyć, aby dodawać nowych członków do rosnących potrzeb aplikacji. Ponadto, możesz wdrażać swoje `My` rozszerzenia nazw, aby inni deweloperzy jako szablon, Visual Basic.  
  
###  <a name="addingtonamespace"></a> Dodawanie członków do mojego Namespace  
 Ponieważ `My` jest przestrzenią nazw, takich jak inne przestrzeni nazw, można dodać właściwości najwyższego poziomu do niego tylko dodanie modułu i określając `Namespace` z `My`. Dodawanie adnotacji do modułu za pomocą `HideModuleName` atrybutu, jak pokazano w poniższym przykładzie. `HideModuleName` Atrybutu gwarantuje, że IntelliSense nie będą wyświetlane Nazwa modułu, gdy Wyświetla elementy członkowskie `My` przestrzeni nazw.  
  
 [!code-vb[VbVbcnExtendingMy#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#3)]  
  
 Aby dodać członków do `My` przestrzeni nazw, Dodaj właściwości, zgodnie z potrzebami w module. Dla każdej właściwości dodawane do `My` przestrzeni nazw, Dodaj pole private typu `ThreadSafeObjectProvider(Of T)`, których typem jest typ zwracany przez właściwości niestandardowej. To pole służy do tworzenia wystąpienia obiektu wątkowo ma zostać zwrócona przez właściwość przez wywołanie metody `GetInstance` metody. W rezultacie każdego wątku, który uzyskuje dostęp do właściwości rozszerzonej odbiera własne wystąpienie typu zwracanego. Poniższy przykład dodaje właściwość o nazwie `SampleExtension` jest typu `SampleExtension` do `My` przestrzeni nazw:  
  
 [!code-vb[VbVbcnExtendingMy#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#4)]  
  
##  <a name="addingevents"></a> Dodawanie zdarzeń do niestandardowego Moje obiekty  
 Możesz użyć `My.Application` obiektu do udostępnienia zdarzenia dla niestandardowych `My` obiektów, rozszerzając `MyApplication` klasy częściowej w `My` przestrzeni nazw. Dla projektów z systemem Windows, możesz kliknąć dwukrotnie **mój projekt** węzeł w projekcie w **Eksploratora rozwiązań**. W języku Visual Basic **projektanta projektu**, kliknij przycisk `Application` kartę, a następnie kliknij przycisk `View Application Events` przycisku. Zostanie utworzony nowy plik o nazwie ApplicationEvents.vb. Zawiera on następujący kod do rozszerzania `MyApplication` klasy.  
  
 [!code-vb[VbVbcnExtendingMy#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#5)]  
  
 Można dodać procedury obsługi zdarzeń dla niestandardowych `My` obiektów przez dodanie programów obsługi zdarzeń niestandardowych do `MyApplication` klasy. Zdarzenia niestandardowe umożliwiają Dodaj kod, który będzie wykonywać, gdy program obsługi zdarzeń jest dodane, usunięte, lub zdarzenie jest wywoływane. Należy pamiętać, że `AddHandler` kod zdarzenia niestandardowego jest uruchamiane tylko wtedy, gdy kod jest dodawany przez użytkownika, aby obsłużyć zdarzenie. Rozważmy na przykład, który `SampleExtension` obiekt z poprzedniej sekcji, ma `Load` zdarzenia, które chcesz dodać niestandardowy program obsługi zdarzeń dla. Poniższy przykład kodu pokazuje niestandardowy program obsługi zdarzeń o nazwie `SampleExtensionLoad` który będzie wywoływany, gdy `My.SampleExtension.Load` wystąpi zdarzenie. Gdy kod jest dodawany do obsługi nowej `My.SampleExtensionLoad` zdarzenia `AddHandler` części niniejszego Kodeksu zdarzenia niestandardowego jest wykonywany. `MyApplication_SampleExtensionLoad` Metoda znajduje się w przykładzie kodu, aby wyświetlić przykład program obsługi zdarzeń, który obsługuje `My.SampleExtensionLoad` zdarzeń. Należy pamiętać, że `SampleExtensionLoad` zdarzenia będą dostępne po wybraniu **Moje zdarzenia aplikacji** opcji na liście po lewej stronie listy rozwijanej powyżej edytora kodu podczas edycji pliku ApplicationEvents.vb.  
  
 [!code-vb[VbVbcnExtendingMy#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#6)]  
  
##  <a name="design"></a> Wytyczne dotyczące projektowania  
 Podczas opracowywania rozszerzeń `My` przestrzeni nazw, skorzystaj z poniższych wskazówek w celu ułatwienia zminimalizowania kosztów konserwacji składniki rozszerzenia.  
  
-   **Zawiera tylko logiki rozszerzenia.** Logika objęte `My` rozszerzenie przestrzeni nazw powinien zawierać tylko kod, który jest potrzebny do udostępnienia wymaganej funkcjonalności w `My` przestrzeni nazw. Ponieważ rozszerzenia będą znajdować się w projektach użytkownika jako kod źródłowy, aktualizowanie składnika rozszerzenia ponosi kosztów utrzymania wysokiej i jeśli to możliwe należy unikać.  
  
-   **Minimalizuj założeń projektowych.** Podczas tworzenia usługi rozszerzeń `My` przestrzeni nazw, nie należy zakładać, zestaw odwołania, instrukcji imports na poziomie projektu lub Ustawienia kompilatora określonych (na przykład `Option Strict` wyłączone). Zamiast tego należy zminimalizować zależności i pełnej kwalifikacji wszystkich odwołań do typu przy użyciu `Global` — słowo kluczowe. Upewnij się również, że rozszerzenie kompiluje się przy użyciu `Option Strict` włączone, aby zminimalizować błędy w rozszerzeniu.  
  
-   **Izolowanie kod rozszerzenia.** Wprowadzenie do kodu w jednym pliku sprawia, że rozszerzenie łatwo można wdrożyć jako szablon elementu programu Visual Studio. Aby uzyskać więcej informacji zobacz "Pakowanie i wdrażanie rozszerzenia" w dalszej części tego tematu. Wprowadzenie do wszystkich `My` kod rozszerzenia przestrzeni nazw w jednym pliku lub oddzielnego folderu w projekcie pomoże użytkownikom znajdowanie `My` rozszerzenie przestrzeni nazw.  
  
##  <a name="designing"></a> Projektowanie bibliotek klas dla mojego  
 Podobnie jak w przypadku większości modeli obiektów, niektóre wzorce projektowe działają poprawnie w `My` przestrzeni nazw, a inne nie. Podczas projektowania rozszerzenie `My` przestrzeni nazw, należy wziąć pod uwagę następujące zasady:  
  
-   **Metody bezstanowe.** Metody `My` przestrzeni nazw powinien zapewnić kompletne rozwiązanie do konkretnego zadania. Upewnij się, że wartości parametrów, które są przekazywane do metody zawierają wszystkie dane wejściowe wymagane do ukończenia danego zadania. Unikaj tworzenia metody, które zależą od poprzedniego stanu, takich jak otwieranie połączenia z zasobami.  
  
-   **Globalnego wystąpienia.** Tylko stan, który jest zachowywany w `My` przestrzeni nazw jest globalna do projektu. Na przykład `My.Application.Info` hermetyzuje stan, który jest udostępniany w całej aplikacji.  
  
-   **Typy proste parametrów.** Zachować ich prostotę, unikając typy złożone parametrów. Zamiast tego utworzyć metod, dla których albo braku parametrów wejściowych lub które wymagają prostych typów wejściowych, takich jak ciągi, typy pierwotne i tak dalej.  
  
-   **Metody fabryki.** Niektóre typy są zawsze trudne do utworzenia wystąpienia. Zapewnianie metodami factory jako rozszerzenia `My` przestrzeń nazw umożliwia łatwiejsze odkrycie i używanie typów, które należą do tej kategorii. Na przykład metoda fabryki, które działa dobrze `My.Computer.FileSystem.OpenTextFileReader`. Istnieje kilka typów usługi stream, dostępne w programie .NET Framework. Określając pliki tekstowe, w szczególności `OpenTextFileReader` pomaga użytkownikom zrozumieć, które strumienia do wykorzystania.  
  
 Te wytyczne nie wyklucza ogólnego projektowania dla bibliotek klas. Przeciwnie są one zaleceń, które są zoptymalizowane dla deweloperów, którzy są w języku Visual Basic i `My` przestrzeni nazw. Aby zasady ogólne projektowania do tworzenia biblioteki klas, zobacz [wytyczne dotyczące projektowania Framework](../../../standard/design-guidelines/index.md).  
  
##  <a name="packaging"></a> Pakowanie i wdrażanie rozszerzeń  
 Możesz uwzględnić `My` rozszerzenia nazw szablon projektu Visual Studio lub można pakietu rozszerzeń i wdrażanie ich jako szablon elementu programu Visual Studio. Gdy pakiet usługi `My` rozszerzenia nazw jako szablon elementu programu Visual Studio, możesz korzystać z zalet dodatkowe funkcje udostępniane przez program Visual Basic. Te funkcje umożliwiają objęcie rozszerzenia, gdy projekt odwołuje się do określonego zestawu lub umożliwić użytkownikom jawnie dodać swoje `My` rozszerzenie przestrzeni nazw za pomocą **Moje rozszerzenia** strony języka Visual Basic Projektant projektu.  
  
 Aby uzyskać szczegółowe informacje o sposobie wdrażania `My` rozszerzenia przestrzeni nazw, zobacz [pakowanie i wdrażanie niestandardowych rozszerzeń Moje](../../../visual-basic/developing-apps/customizing-extending-my/packaging-and-deploying-custom-my-extensions.md).  
  
## <a name="see-also"></a>Zobacz także
- [Pakowanie i wdrażanie niestandardowych rozszerzeń My](../../../visual-basic/developing-apps/customizing-extending-my/packaging-and-deploying-custom-my-extensions.md)
- [Rozszerzanie modelu aplikacji Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)
- [Dostosowywanie, które obiekty są dostępne w My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
- [Strona Moje rozszerzenia, Projektant projektu](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
- [Strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [Partial](../../../visual-basic/language-reference/modifiers/partial.md)
