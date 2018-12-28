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
ms.openlocfilehash: 07c33aa49e6fc8f78acd86a92cf555ae389e200c
ms.sourcegitcommit: 49af435bfdd41faf26d38c20c5b0cc07e87bea60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53397036"
---
# <a name="wpf-add-ins-overview"></a>Przegląd Dodatki WPF
<a name="Introduction"></a> Program .NET Framework zawiera dodatek modelu, który deweloperzy mogą używać do tworzenia aplikacji, które obsługuje rozszerzalność w dodatku. Ten dodatek model umożliwia tworzenie dodatków, które integrują się z oraz rozszerzanie funkcjonalności aplikacji. W niektórych przypadkach aplikacje wymagają także do wyświetlania interfejsu użytkownika, które są dostarczane przez dodatki. W tym temacie pokazano, jak WPF, rozszerzają model dodatku .NET Framework umożliwiają tych scenariuszy, architektura za go, jego zalety i jego pewne ograniczenia.  
  

  
<a name="Requirements"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 Wymagana jest znajomość model dodatku .NET Framework. Aby uzyskać więcej informacji, zobacz [dodatki i rozszerzalność](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).  
  
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
  
-   **Odnajdywanie**: Znajdowanie dodatków zgodne z kontraktów obsługiwane przez hosta aplikacji.  
  
-   **Aktywacja**: Podczas ładowania, uruchamiania i nawiązywania połączenia z dodatków.  
  
-   **Izolacja**: Ustanowienie granic izolacji, które chronić aplikacje przed potencjalne i wykonywania problemy z dodatków przy użyciu domeny aplikacji lub procesów.  
  
-   **Komunikacja**: Pozwalając dodatków i hostowanie aplikacji do komunikowania się ze sobą w granicach izolacji, wywoływanie metod i przekazując dane.  
  
-   **Zarządzanie okresem istnienia**: Ładowanie i zwalnianie domeny aplikacji i procesów w sposób zawsze przejrzyste i przewidywalne (zobacz [domen aplikacji](../../../../docs/framework/app-domains/application-domains.md)).  
  
-   **Przechowywanie wersji**: Zapewnienie, że dodatków i hostowania aplikacji może nadal komunikować się podczas tworzenia nowych wersji jednej.  
  
 Ostatecznie tworzenia niezawodnych model dodatku jest trywialny przedsiębiorstwa. Z tego powodu programu .NET Framework zapewnia infrastrukturę do tworzenia modeli w dodatku.  
  
> [!NOTE]
>  Aby uzyskać bardziej szczegółowe informacje dotyczące dodatków, zobacz [dodatki i rozszerzalność](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).  
  
<a name="NETFrameworkAddInModelOverview"></a>   
## <a name="net-framework-add-in-model-overview"></a>Przegląd Model dodatku .NET framework  
 .NET Framework — w modelu znaleziono w <xref:System.AddIn> przestrzeni nazw, zawiera zestaw typów, które są zaprojektowane w celu uproszczenia opracowywania rozszerzeń w dodatku. Jest podstawową jednostką model dodatku .NET Framework *kontraktu*, która definiuje, jak aplikacji hosta i dodatek komunikują się ze sobą. Kontrakt jest widoczna dla aplikacji hosta, za pomocą hosta aplikacji specyficzne *widoku* kontraktu. Podobnie, add logującego się *widoku* Umowy ma połączenie dodatku. *Karty* służy do umożliwiania hosta aplikacji i Dodaj w komunikacji między swoimi opiniami odpowiedniej umowy. Kontrakty, widoki i adaptery są określane jako segmenty i stanowi zbiór powiązanych segmentów *potoku*. Potoki są podstawę, na którym model dodatku .NET Framework obsługuje odnajdywania, aktywacji, izolacji zabezpieczeń, izolacji wykonywania (przy użyciu domeny aplikacji i procesów), komunikacji, zarządzanie okresem istnienia i przechowywania wersji.  
  
 Suma ta obsługa umożliwia deweloperom tworzenie dodatków, które integrują się z funkcjami aplikacji hosta. Jednak niektóre scenariusze wymagają obsługi aplikacji, aby wyświetlać interfejsy użytkownika dostępne dodatki. Ponieważ poszczególnych technologii prezentacji w programie .NET Framework ma swój własny model dotyczące implementowania interfejsów użytkownika, model dodatku .NET Framework nie obsługuje innych technologii prezentacji. Zamiast tego WPF rozszerza model dodatku .NET Framework z obsługą interfejsu użytkownika dla dodatków.  
  
<a name="WPFAddInModel"></a>   
## <a name="wpf-add-ins"></a>Dodatki WPF  
 WPF, w połączeniu z .NET Framework — w modelu pozwala rozwiązać szerokiej gamy scenariuszy, które wymagają obsługi aplikacji, aby wyświetlić interfejs użytkownika z dodatków. W szczególności te scenariusze są rozwiązywane przez WPF za pomocą następujących dwóch modelach programowania:  
  
1.  **Dodatek zwraca interfejs użytkownika**. Dodatek zwraca interfejs użytkownika do aplikacji hosta za pośrednictwem wywołania metody, zgodnie z definicją w umowie. W tym scenariuszu jest używany w następujących przypadkach:  
  
    -   Wygląd interfejsu użytkownika, który jest zwracany przez dodatek jest zależny od danych albo lub warunków, które istnieją tylko w czasie wykonywania, takie jak dynamicznie wygenerowanych raportów.  
  
    -   W interfejsie użytkownika dla usług udostępnianych przez dodatek różni się od interfejsu użytkownika aplikacji hosta, które można używać dodatku.  
  
    -   Dodatek przede wszystkim wykonuje usługi dla aplikacji hosta i raportuje stan aplikacji hosta, za pomocą interfejsu użytkownika.  
  
2.  **Dodatek jest interfejsem użytkownika**. Dodatek jest interfejsem użytkownika, zgodnie z definicją w umowie. W tym scenariuszu jest używany w następujących przypadkach:  
  
    -   Dodatek nie zapewnia usługami innymi niż są wyświetlane, takich jak reklamy.  
  
    -   W interfejsie użytkownika dla usług udostępnianych przez dodatek jest wspólne dla wszystkich aplikacji hosta, które można użyć tego dodatku, takich jak kalkulatora lub próbnika kolorów.  
  
 Scenariusze te wymagają, że obiekty interfejsu użytkownika mogą być przekazywane między aplikacją hosta i domen aplikacji w dodatku. Od programu .NET Framework, który zależy od usług zdalnych do komunikowania się między domenami aplikacji model dodatku obiekty, które są przekazywane między nimi musi być może być zastosowana zdalnie.  
  
 Obiekt może być zastosowana zdalnie jest wystąpieniem klasy, która wykonuje jedno lub więcej z następujących czynności:  
  
-   Pochodzi od klasy <xref:System.MarshalByRefObject> klasy.  
  
-   Implementuje <xref:System.Runtime.Serialization.ISerializable> interfejsu.  
  
-   Ma <xref:System.SerializableAttribute> zastosowany.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat tworzenia obiektów .NET Framework może być zastosowana zdalnie, zobacz [może być zastosowana zdalnie obiektów wprowadzania](https://msdn.microsoft.com/library/01197253-3f13-43b7-894d-9683e431192a).  
  
 Typy WPF UI nie są wykonywane zdalnie. Aby rozwiązać ten problem, WPF rozszerza model dodatku .NET Framework umożliwia WPF UI utworzone przez dodatki mają być wyświetlane z hosta aplikacji. Ta pomoc techniczna jest świadczona przez WPF przez dwa typy: <xref:System.AddIn.Contract.INativeHandleContract> interfejsu i dwa statycznych metod zaimplementowanych przez <xref:System.AddIn.Pipeline.FrameworkElementAdapters> klasy: <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> i <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>. Na wysokim poziomie te typy i metody są używane w następujący sposób:  
  
1.  WPF wymaga, że interfejsy użytkownika, dostarczone przez dodatki są klas, które pochodzą bezpośrednio lub pośrednio z <xref:System.Windows.FrameworkElement>, takich jak kształtów, formantów, kontrolki użytkownika, panele układu i strony.  
  
2.  Wszędzie tam, gdzie kontrakt deklaruje, że interfejs użytkownika będą przekazywane między dodatkiem a aplikacją hosta, musi być zadeklarowany jako <xref:System.AddIn.Contract.INativeHandleContract> (nie <xref:System.Windows.FrameworkElement>); <xref:System.AddIn.Contract.INativeHandleContract> jest reprezentacją może być zastosowana zdalnie dodatku interfejs użytkownika, który może być przekazywany w granicach izolacji.  
  
3.  Przed przesłaniem z dodatku w domenie aplikacji <xref:System.Windows.FrameworkElement> jest spakowany jako <xref:System.AddIn.Contract.INativeHandleContract> przez wywołanie metody <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>.  
  
4.  Po były przekazywane do aplikacji hosta domeny aplikacji, <xref:System.AddIn.Contract.INativeHandleContract> muszą być udostępniane jako <xref:System.Windows.FrameworkElement> przez wywołanie metody <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>.  
  
 Jak <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, i <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> służą zależy od konkretnego scenariusza. Poniższe sekcje zawierają szczegółowe informacje dla każdego modelu programowania.  
  
<a name="ReturnUIFromAddInContract"></a>   
## <a name="add-in-returns-a-user-interface"></a>Dodatek zwraca interfejs użytkownika  
 Dla dodatku do zwrócenia interfejsu użytkownika dla aplikacji hosta wymagane jest spełnienie następujących:  
  
1.  Aplikacja hosta i potoku należy utworzyć, zgodnie z opisem w programie .NET Framework [dodatki i rozszerzalność](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)) dokumentacji.  
  
2.  Kontrakt musi implementować <xref:System.AddIn.Contract.IContract> i zwracać interfejsu użytkownika, kontrakt musi deklarować metody o wartości zwracanego typu <xref:System.AddIn.Contract.INativeHandleContract>.  
  
3.  Interfejs użytkownika, który jest przekazywany między dodatkiem a aplikacją hosta należy bezpośrednio ani pośrednio dziedziczyć <xref:System.Windows.FrameworkElement>.  
  
4.  Interfejs użytkownika, który jest zwracany przez dodatek muszą zostać skonwertowane z <xref:System.Windows.FrameworkElement> do <xref:System.AddIn.Contract.INativeHandleContract> przed przekroczeniem granic izolacji.  
  
5.  Interfejs użytkownika, który jest zwracany, muszą zostać skonwertowane z <xref:System.AddIn.Contract.INativeHandleContract> do <xref:System.Windows.FrameworkElement> po przekroczeniu granic izolacji.  
  
6.  Aplikacja hosta Wyświetla zwracanego <xref:System.Windows.FrameworkElement>.  
  
 Na przykład, który demonstruje sposób implementacji dodatku, który zwraca interfejs użytkownika, zobacz [utworzyć dodatek zwracającego interfejs użytkownika](../../../../docs/framework/wpf/app-development/how-to-create-an-add-in-that-returns-a-ui.md).  
  
<a name="AddInIsAUI"></a>   
## <a name="add-in-is-a-user-interface"></a>Dodatek jest interfejsem użytkownika  
 Gdy dodatek jest interfejsem użytkownika, wymagane są następujące:  
  
1.  Aplikacja hosta i potoku należy utworzyć, zgodnie z opisem w programie .NET Framework [dodatki i rozszerzalność](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)) dokumentacji.  
  
2.  Musi implementować interfejs kontraktu dla dodatku <xref:System.AddIn.Contract.INativeHandleContract>.  
  
3.  Dodatek, który jest przekazywany do aplikacji hosta należy bezpośrednio ani pośrednio dziedziczyć <xref:System.Windows.FrameworkElement>.  
  
4.  Dodatek muszą zostać skonwertowane z <xref:System.Windows.FrameworkElement> do <xref:System.AddIn.Contract.INativeHandleContract> przed przekroczeniem granic izolacji.  
  
5.  Dodatek muszą zostać skonwertowane z <xref:System.AddIn.Contract.INativeHandleContract> do <xref:System.Windows.FrameworkElement> po przekroczeniu granic izolacji.  
  
6.  Aplikacja hosta Wyświetla zwracanego <xref:System.Windows.FrameworkElement>.  
  
 Na przykład, który demonstruje sposób implementacji dodatku, który jest interfejsem użytkownika, zobacz [dodatku oznacza to tworzenie interfejsu użytkownika](../../../../docs/framework/wpf/app-development/how-to-create-an-add-in-that-is-a-ui.md).  
  
<a name="ReturningMultipleUIsFromAnAddIn"></a>   
## <a name="returning-multiple-uis-from-an-add-in"></a>Zwracanie wielu interfejsów użytkownika z dodatku  
 Dodatki często udostępniają wiele interfejsów użytkownika dla aplikacji hosta do wyświetlenia. Na przykład należy wziąć pod uwagę dodatku, który jest interfejsem użytkownika, które również jako interfejs użytkownika umożliwia także informacje o stanie aplikacji hosta. Dodatek w następujący sposób można zaimplementować przy użyciu kombinacji metod z obu [interfejsu użytkownika dodatku zwraca](#ReturnUIFromAddInContract) i [dodatek jest to interfejs użytkownika](#AddInIsAUI) modeli.  
  
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
 Jeśli skonfigurowana potoku i dodać do [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] wdrożenie, są one pobierane do tej samej [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] folder pamięci podręcznej jako [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]. Korzystanie z potoku i dodatek z [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] kodu należy pobrać je z aplikacji podstawowej. Różne typy i członkowie model dodatku .NET Framework dla przy użyciu potoków i dodatki obsługi specjalnych dla tego scenariusza. Po pierwsze, ścieżka jest identyfikowane za pomocą <xref:System.AddIn.Hosting.PipelineStoreLocation.ApplicationBase> wartości wyliczenia. Będzie ona używana z przeciążeń odpowiednich członków dodatku dotyczące korzystania z potokiem, które są następujące:  
  
-   <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>  
  
-   <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%2CSystem.String%5B%5D%29?displayProperty=nameWithType>  
  
-   <xref:System.AddIn.Hosting.AddInStore.Rebuild%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>  
  
-   <xref:System.AddIn.Hosting.AddInStore.Update%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>  
  
### <a name="accessing-the-hosts-site-of-origin"></a>Uzyskiwanie dostępu do witryny pochodzenia hosta  
 Aby upewnić się, dodatek odwołać się do plików z witryny pochodzenia, dodatek muszą być ładowane izolacji zabezpieczeń, który jest odpowiednikiem aplikacji hosta. Ten poziom zabezpieczeń jest identyfikowany przez <xref:System.AddIn.Hosting.AddInSecurityLevel.Host?displayProperty=nameWithType> wartość wyliczenia i przekazywane do <xref:System.AddIn.Hosting.AddInToken.Activate%2A> metody, gdy dodatek jest aktywny.  
  
<a name="WPFAddInModelArchitecture"></a>   
## <a name="wpf-add-in-architecture"></a>Architektura dodatków WPF  
 Na najwyższym poziomie, jak w związku z czym dostrzegliśmy, WPF umożliwia dodatków .NET Framework do implementacji interfejsów użytkownika (który pochodzi bezpośrednio lub pośrednio od <xref:System.Windows.FrameworkElement>) przy użyciu <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> i <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>. Wynik jest zwracany jest aplikacja hosta <xref:System.Windows.FrameworkElement> która jest wyświetlana w interfejsie użytkownika w aplikacji hosta.  
  
 W przypadku prostego interfejsu użytkownika dodatku scenariuszy jest możliwie szczegółowo potrzebuje Deweloper. Dla bardziej złożonych scenariuszy, szczególnie te, w których podejmowana jest próba korzystanie z dodatkowych usług WPF, takie jak układ, zasobów i powiązania danych bardziej szczegółowych informacji dotyczących sposobu WPF rozszerza model dodatku .NET Framework z obsługą interfejsu użytkownika jest wymagane, aby zrozumieć korzyści i ograniczenia.  
  
 Zasadniczo WPF nie przeszło interfejsu użytkownika z dodatku dla aplikacji hosta; Zamiast tego WPF przechodzi uchwyt okna Win32 dla interfejsu użytkownika przy użyciu współdziałanie WPF. Jako takie gdy interfejs użytkownika z dodatku jest przekazywany do aplikacji hosta, są następujące operacje:  
  
-   Po stronie dodatku WPF uzyskuje uchwyt okna interfejsu użytkownika, który będzie wyświetlany przez aplikację hosta. Uchwyt okna jest hermetyzowany przez Wewnętrzna klasa WPF, która pochodzi od klasy <xref:System.Windows.Interop.HwndSource> i implementuje <xref:System.AddIn.Contract.INativeHandleContract>. Wystąpienie tej klasy jest zwracany przez <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> i jest przekazywane z dodatku w domenie aplikacji do aplikacji hosta domeny aplikacji.  
  
-   Po stronie aplikacja hosta WPF przepakowuje <xref:System.Windows.Interop.HwndSource> jako Wewnętrzna klasa WPF, która pochodzi od klasy <xref:System.Windows.Interop.HwndHost> i wykorzystuje <xref:System.AddIn.Contract.INativeHandleContract>. Wystąpienie tej klasy jest zwracany przez <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> aplikacji hosta.  
  
 <xref:System.Windows.Interop.HwndHost> istnieje, aby wyświetlać interfejsy użytkownika, identyfikowane za pomocą uchwytów okien, od interfejsów użytkownika WPF. Aby uzyskać więcej informacji, zobacz [WPF i Win32 — współdziałanie](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md).  
  
 Podsumowując <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, i <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> pozwalających uchwytu okna WPF UI przekazany z dodatku dla aplikacji hosta, gdzie jest hermetyzowany przez <xref:System.Windows.Interop.HwndHost> i wyświetlane w interfejsie użytkownika aplikacji hosta.  
  
> [!NOTE]
>  Ponieważ aplikacja hosta pobiera <xref:System.Windows.Interop.HwndHost>, aplikacji hosta nie można przekonwertować na obiekt, który jest zwracany przez <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> do typu jest implementowana za dodatek (na przykład <xref:System.Windows.Controls.UserControl>).  
  
 Z natury <xref:System.Windows.Interop.HwndHost> ma pewne ograniczenia, które wpływają na jak aplikacji hosta można z nich korzystać. Jednak rozszerza WPF <xref:System.Windows.Interop.HwndHost> możliwości kilku scenariuszach dodatku. Te korzyści i ograniczenia są opisane poniżej.  
  
<a name="WPFAddInModelBenefits"></a>   
## <a name="wpf-add-in-benefits"></a>Korzyści z dodatku programu WPF  
 Ponieważ interfejsy użytkownika w dodatku WPF zostaną wyświetlone z aplikacji hosta, za pomocą klasą wewnętrzną, która pochodzi od klasy <xref:System.Windows.Interop.HwndHost>, te interfejsy użytkownika są ograniczone przez możliwości <xref:System.Windows.Interop.HwndHost> względem usługi WPF UI, takie jak układ Renderowanie, powiązań danych, style, szablony i zasoby. Jednak WPF rozszerzają jego wewnętrznych <xref:System.Windows.Interop.HwndHost> podklasy o dodatkowe funkcje, które obejmują następujące elementy:  
  
-   Przełączania między interfejsu użytkownika dla aplikacji hosta i interfejsu użytkownika dodatku. Pamiętaj, że model programowania "dodatek jest interfejsem użytkownika" wymaga karty add w side zastąpić <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> włączyć klawiszem TAB, czy dodatek jest w pełni zaufana, czy częściowo zaufany.  
  
-   Zapewniane wymagania dotyczące ułatwień dostępu dla interfejsów użytkownika w dodatku, które są wyświetlane od interfejsów użytkownika aplikacji hosta.  
  
-   Włączanie aplikacji WPF, bezpieczne uruchamianie w wielu scenariuszach domeny aplikacji.  
  
-   Zapobieganie niedozwolony dostęp do interfejsu użytkownika dodatku okna obsługuje uruchamiania dodatków przy użyciu zabezpieczeń, izolacji (to znaczy piaskownicy częściowego zaufania zabezpieczeń). Wywoływanie <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> zapewnia to bezpieczeństwo:  
  
    -   "Add-in zwraca interfejs użytkownika" modelu programowania, jedynym sposobem, aby przekazać uchwyt okna dla dodatków interfejsu użytkownika przez granicę izolacji jest wywołać <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>.  
  
    -   "Dodatek jest interfejsem użytkownika" modelu programowania zastępowanie <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> na karcie add w side i wywoływania <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> (jak pokazano w poprzednich przykładach) jest wymagana, ponieważ wywoływany kartę add w side `QueryContract` implementację z Adaptery po stronie hosta.  
  
-   Zapewnienie ochrony wykonywania domeny w usłudze wielu aplikacji. Ze względu na ograniczenia z domenami aplikacji nieobsłużonych wyjątków, które są zgłaszane w domenach aplikacji dodatku spowodować całej aplikacji ulega awarii, nawet jeśli istnieje granic izolacji. Jednakże WPF i model dodatku .NET Framework zapewnia prostą metodę obejścia tego problemu i zwiększenia stabilności aplikacji. Dodatek programu WPF, który wyświetla interfejs użytkownika tworzy <xref:System.Windows.Threading.Dispatcher> dla wątku, który domeny aplikacji działa, jeśli aplikacja hosta aplikacji WPF. Można wykryć wszystkie nieobsługiwane wyjątki, występujących w domenie aplikacji, obsługując <xref:System.Windows.Threading.Dispatcher.UnhandledException> zdarzenia WPF dodatku <xref:System.Windows.Threading.Dispatcher>. Możesz uzyskać <xref:System.Windows.Threading.Dispatcher> z <xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A> właściwości.  
  
<a name="WPFAddInModelLimitations"></a>   
## <a name="wpf-add-in-limitations"></a>Ograniczenia dotyczące dodawania WPF  
 Poza korzyści, które WPF dodaje się do zachowania domyślne, dostarczone przez <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost>i uchwytów okien są również ograniczenia dla interfejsów użytkownika w dodatku, które są wyświetlane z hosta aplikacji:  
  
-   Interfejsy użytkownika dodatku wyświetlane z aplikacją hosta nie respektują zachowanie wycinka aplikacji hosta.  
  
-   Pojęcie *powietrznej* w współdziałanie scenariuszy ma również zastosowanie do dodatków (zobacz [regiony technologiczne — Przegląd](../../../../docs/framework/wpf/advanced/technology-regions-overview.md)).  
  
-   Interfejs użytkownika dla aplikacji hosta usług, takich jak dziedziczenie zasobów, powiązań danych i polecenia, nie są automatycznie dostępne dla dodatku interfejsów użytkownika. Aby zapewnić tych usług do dodatku, należy zaktualizować potoku.  
  
-   Dodatków interfejsu użytkownika nie można obracać, skalować, nierówne lub w przeciwnym razie wpływ transformacji (zobacz [przekształca Przegląd](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)).  
  
-   Zawartość wewnątrz interfejsy użytkownika dodatku renderowania za pomocą rysowania operacje z <xref:System.Drawing> przestrzeni nazw może obejmować przenikaniem alfa. Jednak zarówno dodatków interfejsu użytkownika, jak i hosta aplikacji interfejsu użytkownika, który go zawiera musi wskazywać 100% nieprzezroczyste; innymi słowy `Opacity` zarówno właściwość musi być równa 1.  
  
-   Jeśli <xref:System.Windows.Window.AllowsTransparency%2A> właściwości okna aplikacji hosta, który zawiera dodatków interfejsu użytkownika ustawiono `true`, dodatek jest niewidoczna. Ta zasada obowiązuje nawet w przypadku interfejsu użytkownika dodatku w 100% nieprzezroczyste (czyli `Opacity` właściwość ma wartość 1).  
  
-   Dodatek interfejsu użytkownika musi znajdować się na inne elementy WPF, w tym samym oknie najwyższego poziomu.  
  
-   Nie części interfejsu użytkownika dodatku może być renderowany przy użyciu <xref:System.Windows.Media.VisualBrush>. Zamiast tego dodatku mogą utworzyć migawkę wygenerowany interfejs użytkownika, aby utworzyć mapę bitową, który może być przekazywany do aplikacji hosta, za pomocą metod zdefiniowanych przez umowy.  
  
-   Pliki multimedialne, nie można odtworzyć z <xref:System.Windows.Controls.MediaElement> w dodatku w interfejsie użytkownika.  
  
-   Zdarzenia myszy generowane dla interfejsu użytkownika dodatku nie są odbierane ani zgłoszone przez aplikację hosta i `IsMouseOver` właściwości dla hosta aplikacji interfejsu użytkownika ma wartość `false`.  
  
-   Gdy fokus jest przenoszony między kontrolkami w dodatku w interfejsie użytkownika, `GotFocus` i `LostFocus` zdarzenia nie są odbierane ani zgłoszone przez aplikację hosta.  
  
-   Część aplikacji hosta, który zawiera dodatków interfejsu użytkownika pojawi się białe po wydrukowaniu.  
  
-   Wszystkie dyspozytorów (zobacz <xref:System.Windows.Threading.Dispatcher>) utworzone przez dodatek interfejsu użytkownika musi być zamknięty ręcznie przed dodatku właściciel jest zwalniana, gdy aplikacja hosta kontynuuje wykonywanie. Kontrakt może implementować metody, które umożliwiają aplikacji hosta w celu sygnalizowania, że dodatek przed dodatek jest załadowany, umożliwiając w ten sposób dodatków interfejsu użytkownika do zamykania jego dyspozytorów.  
  
-   Jeśli dodatek interfejs użytkownika jest <xref:System.Windows.Controls.InkCanvas> lub zawiera <xref:System.Windows.Controls.InkCanvas>, nie można zwolnić dodatku.  
  
<a name="PerformanceOptimization"></a>   
## <a name="performance-optimization"></a>Optymalizacja wydajności  
 Domyślnie jeśli używanych jest wiele domen aplikacji, różnych zestawów .NET Framework, wymagane przez poszczególne aplikacje są wszystkie ładowane do domeny w tej aplikacji. W rezultacie czas wymagany do tworzenia nowych domen aplikacji i uruchamiania aplikacji w nich może wpłynąć na wydajność. Jednak .NET Framework umożliwia zmniejszenie czasu uruchomienia przez poinstruowanie aplikacjom udostępnianie zestawów w domenach aplikacji, jeśli są już załadowane. Możesz to zrobić przy użyciu <xref:System.LoaderOptimizationAttribute> atrybut, który należy zastosować do metody punktu wejścia (`Main`). W takim przypadku musisz podać tylko kod do implementacji definicji aplikacji (zobacz [Zarządzanie aplikacjami — omówienie](../../../../docs/framework/wpf/app-development/application-management-overview.md)).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.LoaderOptimizationAttribute>  
 [Dodatki i rozszerzalność](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))  
 [Domeny aplikacji](../../../../docs/framework/app-domains/application-domains.md)  
 [Przegląd komunikacji zdalnej programu .NET framework](https://msdn.microsoft.com/library/eccb1d31-0a22-417a-97fd-f4f1f3aa4462)  
 [Tworzenie obiektów może być zastosowana zdalnie](https://msdn.microsoft.com/library/01197253-3f13-43b7-894d-9683e431192a)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/app-development/how-to-topics.md)
