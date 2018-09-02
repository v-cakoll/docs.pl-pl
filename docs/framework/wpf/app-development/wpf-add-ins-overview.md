---
title: Przegląd Dodatki WPF
ms.date: 03/30/2017
helpviewer_keywords:
- add-ins and XAML browser applications [WPF]
- add-ins overview [WPF]
- add-ins [WPF], performance
- add-ins [WPF], benefits
- .NET Framework add-in model [WPF]
- add-ins [WPF], user interface
- add-ins and the user interface [WPF]
- add-ins [WPF], architecture
- add-ins [WPF], limitations
ms.assetid: 00b4c776-29a8-4dba-b603-280a0cdc2ade
ms.openlocfilehash: 2e5d133a4744124723c0373e3d5974b505936190
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43402104"
---
# <a name="wpf-add-ins-overview"></a>Przegląd Dodatki WPF
<a name="Introduction"></a> [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Obejmuje model dodatku, deweloperzy mogą używać do tworzenia aplikacji, które obsługuje rozszerzalność w dodatku. Ten dodatek model umożliwia tworzenie dodatków, które integrują się z oraz rozszerzanie funkcjonalności aplikacji. W niektórych przypadkach aplikacje wymagają także do wyświetlenia [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] są dostarczane przez dodatków. W tym temacie przedstawiono sposób [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] rozszerzają [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] model w dodatku, aby włączyć te scenariusze, architektura związanych z nim, korzyści i jego pewne ograniczenia.  
  

  
<a name="Requirements"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 Znajomość [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dodatku model jest wymagany. Aby uzyskać więcej informacji, zobacz [dodatki i rozszerzalność](../../../../docs/framework/add-ins/index.md).  
  
<a name="AddInsOverview"></a>   
## <a name="add-ins-overview"></a>Omówienie dodatków  
 W celu uniknięcia komplikacje związane z ponowną kompilację aplikacji i ponowne włączenie nowe funkcje, aplikacje zaimplementować rozszerzalności mechanizmów, które umożliwiają deweloperom (firmy Microsoft i innych firm), aby utworzyć inne aplikacje, które Integracja z nich. Jest najczęstszym sposobem obsługi tego rodzaju rozszerzalność przy użyciu dodatków (znany także jako "dodatki" i "dodatki"). Przykłady rzeczywistych aplikacjach, które uwidaczniają rozszerzalność przy użyciu dodatków:  
  
-   Dodatki programu Internet Explorer.  
  
-   Dodatki plug-in Windows Media Player.  
  
-   Visual Studio dodatków.  
  
 Na przykład model dodatku Windows Media Player umożliwia deweloperom innej firmy zaimplementować "dodatki", które rozszerzają Windows Media Player na różne sposoby, m.in. tworzenia dekoderów i koderów dla formatów multimediów, które nie są obsługiwane natywnie przez Windows Usługa Media Player (na przykład DVD, MP3), efekty dźwiękowe i skórki. Każdy model dodatek został opracowany pod kątem udostępniają funkcje, który jest unikatowy dla aplikacji, chociaż istnieje kilka jednostek i zachowania, które są wspólne dla wszystkich modeli dodatku.  
  
 Są trzy główne jednostki rozszerzalności typowy dodatek rozwiązania *umów*, *dodatków*, i *hostowanie aplikacji*. Kontrakty określają, jak dodatki integracji z aplikacjami hosta na dwa sposoby:  
  
-   Dodatki integracji z funkcjonalnością, który jest implementowany przez hosta aplikacji.  
  
-   Hostowanie aplikacji ujawniać funkcjonalność dla dodatków do integracji z.  
  
 Aby dodatków do użycia hostowanie aplikacji trzeba je znaleźć i załadować je w czasie wykonywania. W związku z tym aplikacje, które obsługują dodatki mają następujące dodatkowe obowiązki:  
  
-   **Odnajdywanie**: znajdowanie dodatków zgodne z kontraktów obsługiwane przez hosta aplikacji.  
  
-   **Aktywacja**: podczas ładowania, uruchamiania i nawiązywania połączenia z dodatków.  
  
-   **Izolacja**: za pomocą domen aplikacji lub procesów można ustanowić granic izolacji, które chronić aplikacje przed potencjalne problemy zabezpieczeń i wykonywania za pomocą dodatków.  
  
-   **Komunikacja**: pozwalając dodatków i hostowanie aplikacji do komunikowania się ze sobą w granicach izolacji, wywoływanie metod i przekazując dane.  
  
-   **Zarządzanie okresem istnienia**: ładowanie i zwalnianie domeny aplikacji i procesów w sposób zawsze przejrzyste i przewidywalne (zobacz [domen aplikacji](../../../../docs/framework/app-domains/application-domains.md)).  
  
-   **Przechowywanie wersji**: zapewnienie, że dodatków i hostowania aplikacji może nadal komunikować się podczas tworzenia nowych wersji jednej.  
  
 Ostatecznie tworzenia niezawodnych model dodatku jest trywialny przedsiębiorstwa. Z tego powodu [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zapewnia infrastrukturę do tworzenia modeli w dodatku.  
  
> [!NOTE]
>  Aby uzyskać bardziej szczegółowe informacje dotyczące dodatków, zobacz [dodatki i rozszerzalność](../../../../docs/framework/add-ins/index.md).  
  
<a name="NETFrameworkAddInModelOverview"></a>   
## <a name="net-framework-add-in-model-overview"></a>Przegląd Model dodatku .NET framework  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Model dodatku, znaleziono w <xref:System.AddIn> przestrzeni nazw, zawiera zestaw typów, które są zaprojektowane w celu uproszczenia opracowywania rozszerzeń w dodatku. Podstawową jednostką [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dodatku model jest *kontraktu*, która definiuje, jak aplikacji hosta i dodatek komunikują się ze sobą. Kontrakt jest widoczna dla aplikacji hosta, za pomocą hosta aplikacji specyficzne *widoku* kontraktu. Podobnie, add logującego się *widoku* Umowy ma połączenie dodatku. *Karty* służy do umożliwiania hosta aplikacji i Dodaj w komunikacji między swoimi opiniami odpowiedniej umowy. Kontrakty, widoki i adaptery są określane jako segmenty i stanowi zbiór powiązanych segmentów *potoku*. Potoki są podstawę, na którym [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dodatku model obsługuje odnajdywania, aktywacji, izolacji zabezpieczeń, izolacji wykonywania (przy użyciu domeny aplikacji i procesów), komunikacji, zarządzanie okresem istnienia i przechowywania wersji.  
  
 Suma ta obsługa umożliwia deweloperom tworzenie dodatków, które integrują się z funkcjami aplikacji hosta. Jednak niektóre scenariusze wymagają obsługi aplikacji do wyświetlenia [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] dostarczone przez dodatków. Ponieważ każda technologia prezentacji w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ma swój własny model implementowania [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)], [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dodatku model nie obsługuje innych technologii prezentacji. Zamiast tego [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] rozszerza [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] model dodatku za pomocą [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pomocy technicznej dla dodatku.  
  
<a name="WPFAddInModel"></a>   
## <a name="wpf-add-ins"></a>Dodatki WPF  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], w połączeniu z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dodatek modelu pozwala rozwiązać szerokiej gamy scenariuszy, które wymagają obsługi aplikacji do wyświetlenia [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] z dodatków. W szczególności te scenariusze są rozwiązywane przez [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] za pomocą następujących dwóch modelach programowania:  
  
1.  **Dodatek zwraca interfejs użytkownika**. Dodatek zwraca [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aplikacji hosta, za pomocą wywołania metody, zgodnie z definicją w umowie. W tym scenariuszu jest używany w następujących przypadkach:  
  
    -   Wygląd [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] zwracanym przez dodatek jest zależny od danych albo lub warunków, które istnieją tylko w czasie wykonywania, takie jak dynamicznie wygenerowanych raportów.  
  
    -   [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Usługi świadczone przez dodatek różni się od [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aplikacji hosta, które można używać dodatku.  
  
    -   Dodatek przede wszystkim wykonuje usługi dla aplikacji hosta, a następnie raportuje stan aplikacji hosta, za pomocą [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
2.  **Dodatek jest interfejsem użytkownika**. Dodatek jest [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], zgodnie z definicją w umowie. W tym scenariuszu jest używany w następujących przypadkach:  
  
    -   Dodatek nie zapewnia usługami innymi niż są wyświetlane, takich jak reklamy.  
  
    -   [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Usługi świadczone przez dodatek jest wspólny dla wszystkich aplikacji hosta, które można użyć tego dodatku, takich jak kalkulatora lub próbnika kolorów.  
  
 Scenariusze te wymagają, aby [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] obiekty mogą być przekazywane między aplikacją hosta i domen aplikacji w dodatku. Ponieważ [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dodatku model opiera się na komunikacji zdalnej do komunikowania się między domenami aplikacji, obiekty, które są przekazywane między nimi muszą być może być zastosowana zdalnie.  
  
 Obiekt może być zastosowana zdalnie jest wystąpieniem klasy, która wykonuje jedno lub więcej z następujących czynności:  
  
-   Pochodzi od klasy <xref:System.MarshalByRefObject> klasy.  
  
-   Implementuje <xref:System.Runtime.Serialization.ISerializable> interfejsu.  
  
-   Ma <xref:System.SerializableAttribute> zastosowany.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat tworzenia może być zastosowana zdalnie [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] obiekty, zobacz [może być zastosowana zdalnie obiektów wprowadzania](https://msdn.microsoft.com/library/01197253-3f13-43b7-894d-9683e431192a).  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Typy nie są wykonywane zdalnie. Aby rozwiązać ten problem, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] rozszerza [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] model w dodatku, aby umożliwić [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] utworzone przez dodatki mają być wyświetlane z hosta aplikacji. Ta pomoc techniczna jest świadczona przez [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] przez dwa typy: <xref:System.AddIn.Contract.INativeHandleContract> interfejsu i dwa statycznych metod zaimplementowanych przez <xref:System.AddIn.Pipeline.FrameworkElementAdapters> klasy: <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> i <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>. Na wysokim poziomie te typy i metody są używane w następujący sposób:  
  
1.  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] wymaga, aby [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] dostarczone przez dodatki są klasami, które pochodzą bezpośrednio lub pośrednio z <xref:System.Windows.FrameworkElement>, takich jak kształtów, formantów, kontrolki użytkownika, panele układu i strony.  
  
2.  Wszędzie tam, gdzie kontrakt deklaruje, że interfejs użytkownika będą przekazywane między dodatkiem a aplikacją hosta, musi być zadeklarowany jako <xref:System.AddIn.Contract.INativeHandleContract> (nie <xref:System.Windows.FrameworkElement>); <xref:System.AddIn.Contract.INativeHandleContract> jest reprezentacją może być zastosowana zdalnie dodatek [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] mogą być przekazywane w granicach izolacji.  
  
3.  Przed przesłaniem z dodatku w domenie aplikacji <xref:System.Windows.FrameworkElement> jest spakowany jako <xref:System.AddIn.Contract.INativeHandleContract> przez wywołanie metody <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>.  
  
4.  Po były przekazywane do aplikacji hosta domeny aplikacji, <xref:System.AddIn.Contract.INativeHandleContract> muszą być udostępniane jako <xref:System.Windows.FrameworkElement> przez wywołanie metody <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>.  
  
 Jak <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, i <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> służą zależy od konkretnego scenariusza. Poniższe sekcje zawierają szczegółowe informacje dla każdego modelu programowania.  
  
<a name="ReturnUIFromAddInContract"></a>   
## <a name="add-in-returns-a-user-interface"></a>Dodatek zwraca interfejs użytkownika  
 Dla dodatku do zwrócenia [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dla aplikacji hosta, wymagane są następujące:  
  
1.  Aplikacja hosta i potoku należy utworzyć, zgodnie z opisem w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] [dodatki i rozszerzalność](../../../../docs/framework/add-ins/index.md) dokumentacji.  
  
2.  Kontrakt musi implementować <xref:System.AddIn.Contract.IContract> i zwracać [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], kontrakt musi zadeklarować metody o wartości zwracanego typu <xref:System.AddIn.Contract.INativeHandleContract>.  
  
3.  [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Jest ono przekazywane między dodatkiem a hostem aplikacji należy bezpośrednio ani pośrednio dziedziczyć <xref:System.Windows.FrameworkElement>.  
  
4.  [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Zwracanym przez dodatek muszą zostać skonwertowane z <xref:System.Windows.FrameworkElement> do <xref:System.AddIn.Contract.INativeHandleContract> przed przekroczeniem granic izolacji.  
  
5.  [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Zwracanym muszą zostać skonwertowane z <xref:System.AddIn.Contract.INativeHandleContract> do <xref:System.Windows.FrameworkElement> po przekroczeniu granic izolacji.  
  
6.  Aplikacja hosta Wyświetla zwracanego <xref:System.Windows.FrameworkElement>.  
  
 Aby uzyskać przykład, który demonstruje sposób implementacji dodatku, który zwraca [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], zobacz [utworzyć dodatek zwracającego interfejs użytkownika](../../../../docs/framework/wpf/app-development/how-to-create-an-add-in-that-returns-a-ui.md).  
  
<a name="AddInIsAUI"></a>   
## <a name="add-in-is-a-user-interface"></a>Dodatek jest interfejsem użytkownika  
 Gdy dodatek jest [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], wymagane są następujące:  
  
1.  Aplikacja hosta i potoku należy utworzyć, zgodnie z opisem w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] [dodatki i rozszerzalność](../../../../docs/framework/add-ins/index.md) dokumentacji.  
  
2.  Musi implementować interfejs kontraktu dla dodatku <xref:System.AddIn.Contract.INativeHandleContract>.  
  
3.  Dodatek, który jest przekazywany do aplikacji hosta należy bezpośrednio ani pośrednio dziedziczyć <xref:System.Windows.FrameworkElement>.  
  
4.  Dodatek muszą zostać skonwertowane z <xref:System.Windows.FrameworkElement> do <xref:System.AddIn.Contract.INativeHandleContract> przed przekroczeniem granic izolacji.  
  
5.  Dodatek muszą zostać skonwertowane z <xref:System.AddIn.Contract.INativeHandleContract> do <xref:System.Windows.FrameworkElement> po przekroczeniu granic izolacji.  
  
6.  Aplikacja hosta Wyświetla zwracanego <xref:System.Windows.FrameworkElement>.  
  
 Aby uzyskać przykład, który demonstruje sposób implementacji dodatku, który jest [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], zobacz [dodatku oznacza to tworzenie interfejsu użytkownika](../../../../docs/framework/wpf/app-development/how-to-create-an-add-in-that-is-a-ui.md).  
  
<a name="ReturningMultipleUIsFromAnAddIn"></a>   
## <a name="returning-multiple-uis-from-an-add-in"></a>Zwracanie wielu interfejsów użytkownika z dodatku  
 Dodatki często udostępniają wiele [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] dla aplikacji hosta do wyświetlenia. Rozważmy na przykład dodatku, który jest [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , także zawiera informacje o stanie aplikacji hosta również jako [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Dodatek w następujący sposób można zaimplementować przy użyciu kombinacji metod z obu [interfejsu użytkownika dodatku zwraca](#ReturnUIFromAddInContract) i [dodatek jest to interfejs użytkownika](#AddInIsAUI) modeli.  
  
<a name="AddInsAndXBAPs"></a>   
## <a name="add-ins-and-xaml-browser-applications"></a>Dodatki i aplikacje przeglądarek XAML  
 W przykładach do tej pory aplikacji hosta zostało zainstalowane oddzielną aplikację. Ale [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] może również obsługiwać dodatków, aczkolwiek z następujące dodatkowe wymagania kompilacji i wdrażania:  
  
-   [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Manifest aplikacji musi być skonfigurowany specjalnie do potoku (foldery i zestawy) i zestawu w dodatku, aby pobrać [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] pamięci podręcznej aplikacji na komputerze klienckim, w tym samym folderze co [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)].  
  
-   [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Należy użyć kodu wykrycie i załadowanie dodatków [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] pamięci podręcznej aplikacji [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] jako lokalizację potoku i dodatek.  
  
-   [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Należy załadować dodatek do kontekstu zabezpieczeń specjalne, jeśli dodatek odwołuje się luźne pliki, które znajdują się w miejscu pochodzenia; w przypadku hostowania za [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], dodatki mogą odwoływać się tylko luźne pliki, które znajdują się w witrynie aplikacji hosta pochodzenia.  
  
 Zadania te są opisane szczegółowo w następujących podsekcjach.  
  
### <a name="configuring-the-pipeline-and-add-in-for-clickonce-deployment"></a>Konfigurowanie potoku i dodatek dla wdrażania ClickOnce  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] pobrane i uruchomić z bezpiecznego folderu w [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] wdrożenia w pamięci podręcznej. Aby [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] do hostowania dodatku, potoku i Dodaj w zestawie musi zostać pobrany do bezpiecznego folderu. Aby to osiągnąć, należy skonfigurować manifest aplikacji do uwzględnienia w potoku i zestawów w dodatku do pobrania. Najłatwiej jest to realizowane w [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], mimo że zestawu potoku dodatek i musi być zapisana w hoście [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] folderze głównym projektu, aby [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] wykrywania zestawy potoku.  
  
 W związku z tym, pierwszym krokiem jest utworzenie potoku i zestawów w dodatku do [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] korzeniem projektu, ustawiając dane wyjściowe kompilacji, każdy potoku zestawu i Dodaj w projektach zestawu. W poniższej tabeli przedstawiono kompilacji dane wyjściowe ścieżki projektów zestawu potoku i projekt dodatku zestawu znajdujących się w tym samym folderze rozwiązania i głównego jako host [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] projektu.  
  
 Tabela 1: Tworzenie ścieżki danych wyjściowych dla zestawów potoku, które są hostowane przez XBAP  
  
|Projekt zestawu potoku|Kompiluj ścieżkę wyjściową|  
|-------------------------------|-----------------------|  
|Kontrakt|`..\HostXBAP\Contracts\`|  
|Widok dodatku|`..\HostXBAP\AddInViews\`|  
|Dodawanie strony karty|`..\HostXBAP\AddInSideAdapters\`|  
|Adaptery po stronie hosta|`..\HostXBAP\HostSideAdapters\`|  
|Add-In|`..\HostXBAP\AddIns\WPFAddIn1`|  
  
 Następnym krokiem jest określenie zestawów potoku i zestawów w dodatku, jako [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] zawartości plików w [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] , wykonując następujące czynności:  
  
1.  Łącznie z zestawu potoku i dodatek w projekcie, klikając prawym przyciskiem myszy każdy folder potoku w Eksploratorze rozwiązań i wybierając pozycję **załącz do projektu**.  
  
2.  Ustawienie **Build Action** każdego zestawu potoku i zestawów w dodatku do **zawartości** z **właściwości** okna.  
  
 Ostatnim krokiem jest skonfigurowanie manifest aplikacji do uwzględnienia potoku plików zestawu i pliku zestawu w dodatku do pobrania. Pliki powinny się znajdować w foldery w katalogu głównym folderu w [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] pamięci podręcznej, który [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] zajmuje aplikacji. Konfigurację można osiągnąć w [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] , wykonując następujące czynności:  
  
1.  Kliknij prawym przyciskiem myszy [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] projektu, kliknij przycisk **właściwości**, kliknij przycisk **Publikuj**, a następnie kliknij przycisk **pliki aplikacji** przycisku.  
  
2.  W **pliki aplikacji** okno dialogowe, zestaw **stan publikowania** każdego potoku i biblioteki DLL dodatku **Include (Auto)** i ustaw **grupa pobierania** dla każdego potoku dodatku DLL **(wymagane)**.  
  
### <a name="using-the-pipeline-and-add-in-from-the-application-base"></a>Przy użyciu potoku i dodać od podstawy aplikacji  
 Jeśli skonfigurowana potoku i dodać do [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] wdrożenie, są one pobierane do tej samej [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] folder pamięci podręcznej jako [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]. Korzystanie z potoku i dodatek z [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] kodu należy pobrać je z aplikacji podstawowej. Różne typy i członkowie [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dodatku model przy użyciu potoków i dodatki obsługi specjalnych dla tego scenariusza. Po pierwsze, ścieżka jest identyfikowane za pomocą <xref:System.AddIn.Hosting.PipelineStoreLocation.ApplicationBase> wartości wyliczenia. Będzie ona używana z przeciążeń odpowiednich członków dodatku dotyczące korzystania z potokiem, które są następujące:  
  
-   <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>  
  
-   <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%2CSystem.String%5B%5D%29?displayProperty=nameWithType>  
  
-   <xref:System.AddIn.Hosting.AddInStore.Rebuild%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>  
  
-   <xref:System.AddIn.Hosting.AddInStore.Update%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>  
  
### <a name="accessing-the-hosts-site-of-origin"></a>Uzyskiwanie dostępu do witryny pochodzenia hosta  
 Aby upewnić się, dodatek odwołać się do plików z witryny pochodzenia, dodatek muszą być ładowane izolacji zabezpieczeń, który jest odpowiednikiem aplikacji hosta. Ten poziom zabezpieczeń jest identyfikowany przez <xref:System.AddIn.Hosting.AddInSecurityLevel.Host?displayProperty=nameWithType> wartość wyliczenia i przekazywane do <xref:System.AddIn.Hosting.AddInToken.Activate%2A> metody, gdy dodatek jest aktywny.  
  
<a name="WPFAddInModelArchitecture"></a>   
## <a name="wpf-add-in-architecture"></a>Architektura dodatków WPF  
 Na najwyższym poziomie jak w związku z czym dostrzegliśmy, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] umożliwia [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dodatków do zaimplementowania [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] (który pochodzi bezpośrednio lub pośrednio od <xref:System.Windows.FrameworkElement>) przy użyciu <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> i <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>. Wynik jest zwracany jest aplikacja hosta <xref:System.Windows.FrameworkElement> wyświetlonej z [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] w aplikacji hosta.  
  
 Dla prostej [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scenariuszy dodatek jest możliwie szczegółowo jeden z deweloperów musi. W przypadku bardziej złożonych scenariuszy, szczególnie te, które spróbuj korzystanie z dodatkowych [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] usługi, takie jak układ, zasobów i wiązania danych, szczegółowymi wiedzy na temat [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] rozszerza [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] model dodatku za pomocą [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Obsługa jest wymagana do zrozumieć jego zalety i ograniczenia.  
  
 Zasadniczo [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] nie przeszło [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] z dodatku dla aplikacji hosta; zamiast tego [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] przechodzi uchwyt okna Win32 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] przy użyciu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] współdziałania. Jako takie, gdy [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] z dodatku jest przekazywany do aplikacji hosta, zostaną wykonane następujące zadania:  
  
-   Po stronie dodatku [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uzyskuje uchwytu okna dla [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] który będzie wyświetlany przez aplikację hosta. Uchwyt okna jest hermetyzowany przez wewnętrzną [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] klasę pochodzącą od <xref:System.Windows.Interop.HwndSource> i implementuje <xref:System.AddIn.Contract.INativeHandleContract>. Wystąpienie tej klasy jest zwracany przez <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> i jest przekazywane z dodatku w domenie aplikacji do aplikacji hosta domeny aplikacji.  
  
-   Na stronie aplikacji hosta [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] przepakowuje <xref:System.Windows.Interop.HwndSource> jako wewnętrzne [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] klasę pochodzącą od <xref:System.Windows.Interop.HwndHost> i wykorzystuje <xref:System.AddIn.Contract.INativeHandleContract>. Wystąpienie tej klasy jest zwracany przez <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> aplikacji hosta.  
  
 <xref:System.Windows.Interop.HwndHost> istnieje w celu wyświetlenia [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)], identyfikowane przez uchwytów okien z [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]. Aby uzyskać więcej informacji, zobacz [WPF i Win32 — współdziałanie](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md).  
  
 Podsumowując <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, i <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> pozwalających uchwytu okna dla [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] przekazany z dodatku dla aplikacji hosta, w której jest hermetyzowany przez <xref:System.Windows.Interop.HwndHost> i wyświetlane hosta aplikacji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
> [!NOTE]
>  Ponieważ aplikacja hosta pobiera <xref:System.Windows.Interop.HwndHost>, aplikacji hosta nie można przekonwertować na obiekt, który jest zwracany przez <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> do typu jest implementowana za dodatek (na przykład <xref:System.Windows.Controls.UserControl>).  
  
 Z natury <xref:System.Windows.Interop.HwndHost> ma pewne ograniczenia, które wpływają na jak aplikacji hosta można z nich korzystać. Jednak [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] rozszerza <xref:System.Windows.Interop.HwndHost> możliwości kilku scenariuszach dodatku. Te korzyści i ograniczenia są opisane poniżej.  
  
<a name="WPFAddInModelBenefits"></a>   
## <a name="wpf-add-in-benefits"></a>Korzyści z dodatku programu WPF  
 Ponieważ [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dodatku [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] są wyświetlane w aplikacji hosta, za pomocą klasą wewnętrzną, która pochodzi od klasy <xref:System.Windows.Interop.HwndHost>, w których [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] są ograniczone przez możliwości <xref:System.Windows.Interop.HwndHost> w odniesieniu do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] usługi, takie jak układ, renderowanie, powiązanie danych, style, szablony i zasoby. Jednak [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] rozszerzają jego wewnętrznych <xref:System.Windows.Interop.HwndHost> podklasy o dodatkowe funkcje, które obejmują następujące elementy:  
  
-   Przełączania między aplikacją hosta [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] i dodatku [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Należy pamiętać, że "dodatek jest [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]" modelu programowania wymaga karty Dodaj strony zastąpić <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> włączyć klawiszem TAB, czy dodatek jest w pełni zaufana, czy częściowo zaufany.  
  
-   Wymagania dotyczące ułatwień dostępu dla dodatku zapewniane [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] , zostaną wyświetlone z aplikacją hosta [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)].  
  
-   Włączanie [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] bezpieczne uruchamianie w wielu zastosowaniach domeny aplikacji.  
  
-   Zapobieganie dostępowi niedozwolone dodatku [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] okna obsługi uruchamiania dodatków przy użyciu zabezpieczeń, izolacji (to znaczy piaskownicy częściowego zaufania zabezpieczeń). Wywoływanie <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> zapewnia to bezpieczeństwo:  
  
    -   Dla "dodatek zwraca [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]" model programowania, jedynym sposobem, aby przekazać uchwyt okna dodatku [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] na izolację granic jest wywołanie <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>.  
  
    -   Dla "dodatek jest [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]" programowania modelu, zastępowanie <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> na karcie add w side i wywoływania <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> (jak pokazano w poprzednich przykładach) jest wymagana, ponieważ wywoływany kartę add w side `QueryContract` implementacji z karty po stronie hosta.  
  
-   Zapewnienie ochrony wykonywania domeny w usłudze wielu aplikacji. Ze względu na ograniczenia z domenami aplikacji nieobsłużonych wyjątków, które są zgłaszane w domenach aplikacji dodatku spowodować całej aplikacji ulega awarii, nawet jeśli istnieje granic izolacji. Jednak [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] i [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] model dodatku zapewniają prosty sposób do obejścia tego problemu i zwiększenia stabilności aplikacji. A [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dodatek, który wyświetla [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] tworzy <xref:System.Windows.Threading.Dispatcher> dla wątku, który domeny aplikacji jest wykonywany, gdy aplikacja hosta jest [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji. Można wykryć wszystkie nieobsługiwane wyjątki, występujących w domenie aplikacji, obsługując <xref:System.Windows.Threading.Dispatcher.UnhandledException> zdarzenia [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dodatku <xref:System.Windows.Threading.Dispatcher>. Możesz uzyskać <xref:System.Windows.Threading.Dispatcher> z <xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A> właściwości.  
  
<a name="WPFAddInModelLimitations"></a>   
## <a name="wpf-add-in-limitations"></a>Ograniczenia dotyczące dodawania WPF  
 Poza korzyści, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dodaje do zachowania domyślne, dostarczone przez <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost>i uchwytów okien są również ograniczenia dotyczące dodatku [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] które są wyświetlane z hosta aplikacji:  
  
-   Dodatek [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] wyświetlane z hosta aplikacji nie respektują zachowanie wycinka aplikacji hosta.  
  
-   Pojęcie *powietrznej* w współdziałanie scenariuszy ma również zastosowanie do dodatków (zobacz [regiony technologiczne — Przegląd](../../../../docs/framework/wpf/advanced/technology-regions-overview.md)).  
  
-   Dla aplikacji hosta [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] usług, takich jak dziedziczenie zasobów, powiązań danych i polecenia, nie są automatycznie dostępne dla dodatku [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]. Aby zapewnić tych usług do dodatku, należy zaktualizować potoku.  
  
-   Dodatek [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] nie można obracać, skalować, nierówne lub w przeciwnym razie wpływ transformacji (zobacz [przekształca Przegląd](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)).  
  
-   Zawartość wewnątrz dodatku [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] który jest renderowany za pomocą rysowania operacje z <xref:System.Drawing> przestrzeni nazw może obejmować przenikaniem alfa. Jednak zarówno dodatku [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] a aplikacją hosta [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] zawierający go musi być nieprzezroczyste 100%; innymi słowy, `Opacity` zarówno właściwość musi być równa 1.  
  
-   Jeśli <xref:System.Windows.Window.AllowsTransparency%2A> właściwości okna aplikacji hosta, który zawiera dodatek [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ustawiono `true`, dodatek jest niewidoczna. Ta zasada obowiązuje nawet wtedy, gdy dodatek [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] jest nieprzezroczysta 100% (czyli `Opacity` właściwość ma wartość 1).  
  
-   Dodatek [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] musi znajdować się na drugim [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] elementów w tym samym oknie najwyższego poziomu.  
  
-   Nie części dodatku [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] może być renderowany przy użyciu <xref:System.Windows.Media.VisualBrush>. Zamiast tego dodatku mogą utworzyć migawkę wygenerowany [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] do utworzenia mapy bitowej, który może być przekazywany do aplikacji hosta, za pomocą metod zdefiniowanych przez umowy.  
  
-   Pliki multimedialne, nie można odtworzyć z <xref:System.Windows.Controls.MediaElement> w dodatku [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
-   Wskaźnik myszy generowane dla dodatku [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] nie są odbierane ani zgłoszone przez aplikację hosta i `IsMouseOver` właściwości dla aplikacji hosta [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ma wartość `false`.  
  
-   Gdy fokus jest przenoszony między kontrolkami w dodatku [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], `GotFocus` i `LostFocus` zdarzenia nie są odbierane ani zgłoszone przez aplikację hosta.  
  
-   Część aplikacji hosta, który zawiera dodatek [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pojawia się białe po wydrukowaniu.  
  
-   Wszystkie dyspozytorów (zobacz <xref:System.Windows.Threading.Dispatcher>) utworzone przez dodatek [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] musi być zamknięty ręcznie przed dodatku właściciel jest zwalniana, gdy aplikacja hosta kontynuuje wykonywanie. Kontrakt można implementować metody, które umożliwiają aplikacji hosta w celu sygnalizowania, że dodatek przed dodatek jest zwalniany, umożliwiając dodatek [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] zamknąć jego dystrybucja.  
  
-   Jeśli dodatek [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] jest <xref:System.Windows.Controls.InkCanvas> lub zawiera <xref:System.Windows.Controls.InkCanvas>, nie można zwolnić dodatku.  
  
<a name="PerformanceOptimization"></a>   
## <a name="performance-optimization"></a>Optymalizacja wydajności  
 Domyślnie, jeśli używanych jest wiele domen aplikacji różnych [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zestawów wymaganych przez poszczególne aplikacje są wszystkie załadowane do domeny tej aplikacji. W rezultacie czas wymagany do tworzenia nowych domen aplikacji i uruchamiania aplikacji w nich może wpłynąć na wydajność. Jednak [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] umożliwia zmniejszenie czasu uruchomienia przez poinstruowanie aplikacjom udostępnianie zestawów w domenach aplikacji, jeśli są już załadowane. Możesz to zrobić przy użyciu <xref:System.LoaderOptimizationAttribute> atrybut, który należy zastosować do metody punktu wejścia (`Main`). W takim przypadku musisz podać tylko kod do implementacji definicji aplikacji (zobacz [Zarządzanie aplikacjami — omówienie](../../../../docs/framework/wpf/app-development/application-management-overview.md)).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.LoaderOptimizationAttribute>  
 [Dodatki i rozszerzalność](../../../../docs/framework/add-ins/index.md)  
 [Domeny aplikacji](../../../../docs/framework/app-domains/application-domains.md)  
 [Przegląd komunikacji zdalnej programu .NET framework](https://msdn.microsoft.com/library/eccb1d31-0a22-417a-97fd-f4f1f3aa4462)  
 [Tworzenie obiektów może być zastosowana zdalnie](https://msdn.microsoft.com/library/01197253-3f13-43b7-894d-9683e431192a)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/app-development/how-to-topics.md)
