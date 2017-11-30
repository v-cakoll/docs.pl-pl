---
title: Rozszerzanie przestrzeni nazw My w Visual Studio
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.AddingMyExtensions
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: 808e8617-b01c-4135-8b21-babe87389e8e
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 25fff04b19cce299a2d437e662fb7481153d29da
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="extending-the-my-namespace-in-visual-basic"></a>Rozszerzanie przestrzeni nazw My w Visual Studio
`My` Przestrzeni nazw w Visual Basic udostępnia właściwości i metody, które pozwalają łatwo korzystać z możliwości programu .NET Framework. `My` Przestrzeni nazw upraszcza typowych problemów programowania, często zmniejszanie trudne do pojedynczy wiersz kodu. Ponadto `My` przestrzeń nazw jest całkowicie rozszerzalny, dzięki czemu można dostosować zachowanie `My` i dodać nowe usługi do swojej hierarchii w celu dostosowania do potrzeb określonej aplikacji. W tym temacie omówiono zarówno dostosowywanie istniejących członków `My` przestrzeni nazw oraz sposobie dodania niestandardowych klas do `My` przestrzeni nazw.  
  
 **Zawartość tematu**  
  
-   [Dostosowywanie istniejących członków mojego Namespace](#customizing)  
  
-   [Dodawanie członków do obiekty](#addingtoobjects)  
  
-   [Dodawanie niestandardowych obiektów do mojego Namespace](#addingcustom)  
  
-   [Dodawanie członków do mojego Namespace](#addingtonamespace)  
  
-   [Dodawanie zdarzeń do niestandardowe obiekty](#addingevents)  
  
-   [Wytyczne dotyczące projektowania](#design)  
  
-   [Projektowanie biblioteki klas dla moich](#designing)  
  
-   [Opakowanie i wdrażanie rozszerzeń](#packaging)  
  
##  <a name="customizing"></a>Dostosowywanie istniejących członków mojego Namespace  
 `My` Przestrzeni nazw w Visual Basic ujawnia często używane informacje o aplikacji i komputera. Aby uzyskać pełną listę obiektów w `My` przestrzeni nazw, zobacz [Moje odwołanie](../../../visual-basic/language-reference/keywords/my-reference.md). Może być konieczne dostosowanie istniejących członków `My` przestrzeni nazw, aby ich lepsze dostosowany do potrzeb aplikacji. Wszystkie właściwości obiektu w `My` przestrzeni nazw, który nie jest tylko do odczytu można ustawić wartości niestandardowych.  
  
 Na przykład, załóżmy, że często `My.User` obiekt, aby uzyskać dostępu do bieżącego kontekstu zabezpieczeń dla użytkownika, uruchomienie aplikacji. Jednak firma korzysta z obiektu użytkownika niestandardowego do udostępnienia dodatkowych informacji i funkcji dla użytkowników w firmie. W tym scenariuszu można zastąpić wartość domyślną `My.User.CurrentPrincipal` właściwości z wystąpieniem własny niestandardowy obiekt główny, jak pokazano w poniższym przykładzie.  
  
 [!code-vb[VbVbcnExtendingMy#1](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_1.vb)]  
  
 Ustawienie `CurrentPrincipal` właściwość `My.User` zmianach tożsamość, pod którą jest uruchomiona aplikacja. `My.User` Obiektu, z kolei zwraca informacje o nowo określonego użytkownika.  
  
##  <a name="addingtoobjects"></a>Dodawanie członków do obiekty  
 Typy zwracane z `My.Application` i `My.Computer` są zdefiniowane jako `Partial` klasy. W związku z tym można rozszerzyć `My.Application` i `My.Computer` obiektów, tworząc `Partial` klasy o nazwie `MyApplication` lub `MyComputer`. Klasa nie może być `Private` klasy. W przypadku określenia klasy jako część `My` przestrzeni nazw, można dodać właściwości i metody, które zostaną dołączone `My.Application` lub `My.Computer` obiektów.  
  
 Na przykład w poniższym przykładzie dodano właściwość o nazwie `DnsServerIPAddresses` do `My.Computer` obiektu.  
  
 [!code-vb[VbVbcnExtendingMy#2](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_2.vb)]  
  
##  <a name="addingcustom"></a>Dodawanie niestandardowych obiektów do mojego Namespace  
 Mimo że `My` przestrzeń nazw zawiera rozwiązania typowych zadań programistycznych, mogą wystąpić zadania który `My` przestrzeni nazw nie dotyczy. Na przykład aplikacji mogą uzyskiwać dostęp do usługi katalogowe niestandardowego dla danych użytkownika lub aplikacja może używać zestawów, które nie są instalowane domyślnie w języku Visual Basic. Można rozszerzyć `My` przestrzeni nazw w celu uwzględnienia niestandardowych rozwiązań do typowych zadań, które są specyficzne dla danego środowiska. `My` Przestrzeni nazw można łatwo rozszerzyć, aby dodać nowe elementy członkowskie do rosnących potrzeb aplikacji. Ponadto można wdrożyć z `My` przestrzeń nazw rozszerzeń inni deweloperzy jako szablon programu Visual Basic.  
  
###  <a name="addingtonamespace"></a>Dodawanie członków do mojego Namespace  
 Ponieważ `My` jest przestrzenią nazw podobnie jak inne przestrzeni nazw, można dodać właściwości najwyższego poziomu do niego tylko dodanie modułu i określając `Namespace` z `My`. Dodawanie adnotacji moduł `HideModuleName` atrybutu, jak pokazano w poniższym przykładzie. `HideModuleName` Atrybutu gwarantuje, że funkcja IntelliSense nie będą wyświetlane nazwy modułu wyświetlanych elementów członkowskich `My` przestrzeni nazw.  
  
 [!code-vb[VbVbcnExtendingMy#3](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_3.vb)]  
  
 Aby dodać członków do `My` przestrzeni nazw, Dodaj właściwości, w razie potrzeby do modułu. Dla każdej właściwości dodane do `My` przestrzeni nazw, Dodaj pole prywatne typu `ThreadSafeObjectProvider(Of T)`, których typem jest typ zwracany przez właściwości niestandardowej. To pole służy do tworzenia wystąpienia obiektu obsługującej wielowątkowość zwracanej przez właściwość przez wywołanie metody `GetInstance` metody. W związku z tym każdy wątek, który uzyskuje dostęp do właściwości rozszerzonej odbiera własne wystąpienie typu zwracanych. Poniższy przykład umożliwia dodanie właściwości o nazwie `SampleExtension` jest typu `SampleExtension` do `My` przestrzeni nazw:  
  
 [!code-vb[VbVbcnExtendingMy#4](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_4.vb)]  
  
##  <a name="addingevents"></a>Dodawanie zdarzeń do niestandardowe obiekty  
 Można użyć `My.Application` obiektu do udostępnienia zdarzenia dla niestandardowych `My` obiektów rozszerzając `MyApplication` częściowej klasy w `My` przestrzeni nazw. Dla projektów opartych na systemie Windows, możesz kliknąć dwukrotnie **mój projekt** w węźle dla projektu w **Eksploratora rozwiązań**. W języku Visual Basic **projektanta projektu**, kliknij przycisk `Application` a następnie kliknij pozycję `View Application Events` przycisku. Nowy plik o nazwie ApplicationEvents.vb zostanie utworzona. Zawiera on następujący kod do rozszerzania `MyApplication` klasy.  
  
 [!code-vb[VbVbcnExtendingMy#5](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_5.vb)]  
  
 Można dodać obsługi zdarzeń dla niestandardowych `My` obiektów przez dodanie obsługi zdarzeń niestandardowych do `MyApplication` klasy. Zdarzenia niestandardowe umożliwiają Dodaj kod, który zostanie wykonany, gdy program obsługi zdarzeń jest dodawać, usuwać, lub zdarzenie jest wywoływane. Należy pamiętać, że `AddHandler` kodu dla niestandardowych zdarzeń działa tylko wtedy, gdy kod jest dodawany przez użytkownika do obsługi zdarzenia. Rozważmy na przykład, że `SampleExtension` obiekt z poprzedniej sekcji ma `Load` zdarzenie, które chcesz dodać obsługi zdarzenia niestandardowe. Poniższy przykład kodu pokazuje niestandardowy program obsługi zdarzeń o nazwie `SampleExtensionLoad` które będą wywoływane, gdy `My.SampleExtension.Load` zdarzenie. Po dodaniu kod do obsługi nowej `My.SampleExtensionLoad` zdarzenia `AddHandler` część tego zdarzenia niestandardowego kodu jest wykonywana. `MyApplication_SampleExtensionLoad` Metody znajduje się w przykładzie kodu, aby wyświetlić przykład program obsługi zdarzeń, która obsługuje `My.SampleExtensionLoad` zdarzeń. Należy pamiętać, że `SampleExtensionLoad` zdarzenia będą dostępne po wybraniu **Moje zdarzenia aplikacji** opcji na liście rozwijanej po lewej stronie powyżej edytora kodu podczas edytowania pliku ApplicationEvents.vb.  
  
 [!code-vb[VbVbcnExtendingMy#6](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_6.vb)]  
  
##  <a name="design"></a>Wytyczne dotyczące projektowania  
 Podczas opracowywania rozszerzeń `My` przestrzeni nazw, skorzystaj z poniższych wskazówek, aby zminimalizować koszty obsługi składników rozszerzenia.  
  
-   **Dołącz tylko logikę rozszerzenia.** Logika zawarte w `My` rozszerzenia nazw powinna zawierać tylko kod, który jest potrzebne do udostępnienia funkcji wymagany w `My` przestrzeni nazw. Ponieważ rozszerzenia będą znajdować się w projektach użytkownika jako kodu źródłowego, aktualizacja składnika rozszerzenia generuje koszt obsługi wysokiej i należy unikać, jeśli to możliwe.  
  
-   **Minimalizowanie założenia projektu.** Po utworzeniu rozszerzeń z `My` przestrzeni nazw, zakłada się zestaw odwołania, importy poziom projektu lub Ustawienia kompilatora określonych (na przykład `Option Strict` off). Zamiast tego należy zminimalizować zależności i pełnej kwalifikacji wszystkie odwołania do typu przy użyciu `Global` — słowo kluczowe. Upewnij się również, że rozszerzenie kompiluje z `Option Strict` w celu zminimalizowania błędy w rozszerzeniu.  
  
-   **Izolowanie kod rozszerzenia.** Wprowadzenie do kodu w jednym pliku sprawia, że rozszerzenie łatwo można wdrożyć jako szablon elementu programu Visual Studio. Aby uzyskać więcej informacji zobacz "Pakowania i wdrażania rozszerzeń" w dalszej części tego tematu. Wprowadzenie do wszystkich `My` kod rozszerzenie przestrzeni nazw w jednym pliku lub oddzielnego folderu w projekcie również ułatwić użytkownikom znajdowanie `My` rozszerzenie przestrzeni nazw.  
  
##  <a name="designing"></a>Projektowanie biblioteki klas dla moich  
 Jest dostępna w przypadku większości modeli obiektów, niektóre wzorce projektowe działają poprawnie w `My` przestrzeni nazw i innych nie. Podczas projektowania rozszerzenie `My` przestrzeni nazw, należy wziąć pod uwagę następujące zasady:  
  
-   **Metody bezstanowe.** Metody w `My` przestrzeni nazw powinien zawierać kompletne rozwiązanie do określonego zadania. Upewnij się, że wartości parametrów, które są przekazywane do metody Podaj wszystkie dane wejściowe wymagane do wykonania określonego zadania. Unikaj tworzenia metod, które opierają się na poprzedni stan, takie jak otwieranie połączenia z zasobami.  
  
-   **Globalnego wystąpienia.** Tylko stanu, która jest przechowywana w `My` przestrzeni nazw jest globalna do projektu. Na przykład `My.Application.Info` hermetyzuje stan, który jest udostępniony w całej aplikacji.  
  
-   **Typy parametrów proste.** Zachowaj elementy proste dzięki unikaniu typów złożonych parametrów. Zamiast tego utwórz metody, które albo przyjmować nie parametrów wejściowych lub, które wymagają proste typów wejściowych, takich jak ciągów, typy pierwotne i tak dalej.  
  
-   **Metody fabryki.** Niektóre typy są zawsze trudne do utworzenia wystąpienia. Udostępnia metody fabryki jako rozszerzenia `My` przestrzeni nazw umożliwia łatwiejsze odkrycie i używanie typów, które należą do tej kategorii. Na przykład metoda fabryki, które działa dobrze `My.Computer.FileSystem.OpenTextFileReader`. Istnieją różne typy strumienia dostępnych w programie .NET Framework. W szczególności, określając pliki tekstowe `OpenTextFileReader` ułatwia użytkownikom zrozumienie strumień do użycia.  
  
 Niniejsze wytyczne nie wykluczają zasady ogólne projektu biblioteki klas. Zamiast znajdują się zalecenia, które są zoptymalizowane pod kątem deweloperów, którzy korzystają z języka Visual Basic i `My` przestrzeni nazw. Dla zasady ogólne projekt do tworzenia biblioteki klas, zobacz [zaleceń dotyczących projektowania Framework](../../../standard/design-guidelines/index.md).  
  
##  <a name="packaging"></a>Opakowanie i wdrażanie rozszerzeń  
 Można uwzględnić `My` rozszerzeń nazw w szablon projektu Visual Studio, lub można pakiet rozszerzeń i wdrożyć je jako szablon elementu programu Visual Studio. Gdy pakiet z `My` rozszerzenia przestrzeń nazw jako szablon elementu programu Visual Studio, możesz korzystać z dodatkowych możliwości oferowane przez wersję programu Visual Basic. Te funkcje umożliwiają rozszerzenie, gdy projekt odwołuje się do określonego zestawu lub umożliwiają użytkownikom jawnie dodać Twojego `My` rozszerzenie przestrzeni nazw przy użyciu **Moje rozszerzenia** strony Visual Basic Projektant projektu.  
  
 Aby uzyskać więcej informacji o sposobie wdrażania `My` rozszerzenia przestrzeni nazw, zobacz [opakowanie i wdrażanie niestandardowych rozszerzeń Moje](../../../visual-basic/developing-apps/customizing-extending-my/packaging-and-deploying-custom-my-extensions.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Pakowanie i wdrażanie niestandardowych rozszerzeń My](../../../visual-basic/developing-apps/customizing-extending-my/packaging-and-deploying-custom-my-extensions.md)  
 [Rozszerzanie modelu aplikacji Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)  
 [Dostosowywanie, które obiekty są dostępne w mojej](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)  
 [Strona Moje rozszerzenia, Projektant projektu](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)  
 [Strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)  
 [Częściowe](../../../visual-basic/language-reference/modifiers/partial.md)
