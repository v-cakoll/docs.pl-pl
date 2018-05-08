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
ms.openlocfilehash: 942f5706a83a9f9e9cd969701ed5625c57b76f83
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="wpf-add-ins-overview"></a>Przegląd Dodatki WPF
<a name="Introduction"></a> [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zawiera dodatek modelu, który deweloperzy mogą używać do tworzenia aplikacji, które obsługują rozszerzalności w dodatku. Ten model dodatku umożliwia tworzenie dodatków, które integrują się z i rozszerzanie funkcjonalności aplikacji. W niektórych scenariuszach aplikacji również należy wyświetlić [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] są dostarczane przez dodatki. W tym temacie przedstawiono sposób [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] wspomaga [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] modelu dodatku, aby włączyć te scenariusze, architektura za nią korzyści i jego ograniczenia.  
  

  
<a name="Requirements"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 Znajomość [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dodatku model jest wymagany. Aby uzyskać więcej informacji, zobacz [dodatki i rozszerzalność](../../../../docs/framework/add-ins/index.md).  
  
<a name="AddInsOverview"></a>   
## <a name="add-ins-overview"></a>Omówienie dodatki  
 Aby uniknąć złożoności kompilację aplikacji i ponowne wdrożenie w celu uwzględnienia nowych funkcji, aplikacje implementować rozszerzalności mechanizmy, które umożliwiają deweloperom (firmy i innych firm), aby utworzyć inne aplikacje, które Integracja z nich. Typowym sposobem obsługi tego typu rozszerzeń jest przy użyciu dodatków (znanej także jako "dodatki" i "dodatków plug-in"). Przykłady praktyczne aplikacje, które ujawnia rozszerzalności z dodatków:  
  
-   Dodatki programu Internet Explorer.  
  
-   Program Windows Media Player dodatków plug-in.  
  
-   Visual Studio dodatków.  
  
 Na przykład modelu dodatku Windows Media Player umożliwia deweloperom innych firm implementować "dodatków plug-in" rozszerzających Windows Media Player na różne sposoby, m.in. Tworzenie dekoderów i kodery formatów multimediów, które nie są obsługiwane natywnie przez system Windows Media Player (na przykład dysku DVD, MP3), efekty audio i karnacji. Każdy model dodatku korzysta z wbudowanej udostępniają funkcje, który jest unikatowy dla aplikacji, mimo że dostępne są różne jednostki zachowania, które są wspólne dla wszystkich modeli dodatku.  
  
 Są trzy główne jednostki rozwiązań typowych rozszerzalności dodatku *kontrakty*, *dodatków*, i *hostowania aplikacji*. Kontrakty określają, jak zintegrować dodatków z aplikacji hosta na dwa sposoby:  
  
-   Dodatki zintegrować z funkcji, które jest implementowany przez hosta aplikacji.  
  
-   Obsługę aplikacji ujawniać funkcjonalność dodatki do integracji z.  
  
 Aby dodatki do użycia obsługę aplikacji należy je odnaleźć i załadować je w czasie wykonywania. W związku z tym aplikacje, które obsługują dodatki mają następujące obowiązki dodatkowe:  
  
-   **Odnajdywanie**: znajdowanie dodatki zgodnymi ze kontrakty obsługiwane przez aplikacje hosta.  
  
-   **Aktywacja**: ładowanie, uruchamiania i nawiązywania połączenia z dodatków.  
  
-   **Izolacja**: przy użyciu domeny aplikacji lub procesów ustanowienie granice obszarów izolowanych, które chronić aplikacje z potencjalne problemy zabezpieczeń i wykonywania z dodatków.  
  
-   **Komunikacja**: stosowanie dodatków i hostowanie aplikacji komunikują się ze sobą za pośrednictwem granice obszarów izolowanych przez wywołanie metody i przekazywanie danych.  
  
-   **Zarządzanie okresem istnienia**: ładowanie i zwalnianie domen aplikacji i procesów w sposób czystą, przewidywalnych (zobacz [domen aplikacji](../../../../docs/framework/app-domains/application-domains.md)).  
  
-   **Przechowywanie wersji**: zapewnienie, że host aplikacji i dodatki może nadal komunikować się podczas tworzenia nowych wersji albo.  
  
 Ostatecznie tworzenie niezawodnych modelu dodatku jest nieuproszczony przedsiębiorstwa. Z tego powodu [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] oferuje infrastrukturę do tworzenia modeli w dodatku.  
  
> [!NOTE]
>  Aby uzyskać bardziej szczegółowe informacje dotyczące dodatków, zobacz [dodatki i rozszerzalność](../../../../docs/framework/add-ins/index.md).  
  
<a name="NETFrameworkAddInModelOverview"></a>   
## <a name="net-framework-add-in-model-overview"></a>Omówienie programu .NET framework modelu dodatku  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Modelu dodatku, znalezione w <xref:System.AddIn> przestrzeni nazw, zawiera zestaw typów, które pozwalają uprościć tworzenie rozszerzeń dodatku. Podstawową jednostkę [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] modelu dodatku jest *kontraktu*, która określa, w jaki sposób aplikacja hosta i dodatek komunikują się ze sobą. Kontrakt jest uwidaczniany w aplikacji hosta, za pomocą hosta specyficzne dla aplikacji *widoku* kontraktu. Podobnie, Dodaj w specyficzne dla *widoku* kontraktu jest uwidaczniany w dodatku. *Karty* jest stosowane do umożliwienia hosta aplikacji i Dodaj w, do komunikacji między ich odpowiednich widoków kontraktu. Kontrakty, widoków i kart są określane jako segmentów i stanowi zbiór powiązanych segmentów *potoku*. Foundation, na którym są potoki [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dodatku modelu obsługuje odnajdywania, aktywacja izolacji zabezpieczeń, izolacji wykonywania (przy użyciu procesów i domen aplikacji), komunikacji, zarządzanie okresem istnienia i przechowywanie wersji.  
  
 Suma ta obsługa umożliwia deweloperom tworzenie dodatków, które integrację z funkcjami aplikacji hosta. Jednak w niektórych scenariuszach wymagane obsługę aplikacji do wyświetlenia [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] dostarczonych przez dodatki. Ponieważ poszczególnych technologii prezentacji w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ma własny model wdrażania [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)], [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dodatku modelu nie obsługuje innych technologii prezentacji. Zamiast tego [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] rozszerza [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] modelu dodatku z [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] obsługę dodatków.  
  
<a name="WPFAddInModel"></a>   
## <a name="wpf-add-ins"></a>Dodatki WPF  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], w połączeniu z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dodatku modelu pozwala na adres szerokiej gamy scenariuszy, które wymagają obsługi aplikacji do wyświetlenia [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] z dodatków. W szczególności dotyczy tych scenariuszy [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] z następujących dwóch programowania modeli:  
  
1.  **Dodatek zwraca interfejs użytkownika**. Dodatek zwraca [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] do aplikacji hosta za pośrednictwem wywołania metody, zgodnie z umową. W tym scenariuszu jest używana w następujących przypadkach:  
  
    -   Wygląd [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] zwróconego przez dodatek jest zależna od dane lub warunków, które istnieją tylko w czasie wykonywania, takie jak dynamicznie wygenerowanych raportów.  
  
    -   [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Usługi świadczone przez dodatek różni się od [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aplikacji hosta, które można użyć dodatku.  
  
    -   Dodatek głównie wykonuje usługa dla aplikacji hosta, a następnie raportuje stan do aplikacji hosta z [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
2.  **Dodatek jest interfejs użytkownika**. Dodatek jest [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], zgodnie z umową. W tym scenariuszu jest używana w następujących przypadkach:  
  
    -   Dodatek nie zapewnia usług innych niż wyświetlanej takie jak anonsu.  
  
    -   [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Usługi świadczone przez dodatek jest wspólny dla wszystkich aplikacji hosta, które można użyć tego dodatku, takich jak Kalkulator lub próbnika kolorów.  
  
 Te scenariusze wymagają, aby [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] obiekty mogą być przekazywane między hosta aplikacji i domen aplikacji dodatku. Ponieważ [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dodatku modelu zależy od usług zdalnych do komunikowania się między domenami aplikacji obiektów, które są przekazywane między nimi musi być może być zastosowana zdalnie.  
  
 Obiekt może być zastosowana zdalnie jest wystąpieniem klasy, która wykonuje jedno lub więcej z następujących czynności:  
  
-   Pochodną <xref:System.MarshalByRefObject> klasy.  
  
-   Implementuje <xref:System.Runtime.Serialization.ISerializable> interfejsu.  
  
-   Ma <xref:System.SerializableAttribute> atrybut zastosowany.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji dotyczących tworzenia może być zastosowana zdalnie [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] obiekty, zobacz [wprowadzania zdalnych obiektów](http://msdn.microsoft.com/library/01197253-3f13-43b7-894d-9683e431192a).  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Typy nie są wykonywane zdalnie. Aby rozwiązać ten problem, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] rozszerza [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] modelu dodatku, aby włączyć [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] utworzone przez dodatki mają być wyświetlane w aplikacji hosta. Te są obsługiwane przez [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] przez dwa typy: <xref:System.AddIn.Contract.INativeHandleContract> interfejsu i dwie metody statyczne implementowane przez <xref:System.AddIn.Pipeline.FrameworkElementAdapters> klasy: <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> i <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>. Na wysokim poziomie te typy i metody są używane w następujący sposób:  
  
1.  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] wymaga, aby [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] dostarczonych przez dodatki są klas pochodzących od bezpośrednio lub pośrednio <xref:System.Windows.FrameworkElement>, na przykład kształtów, kontrolek, kontrolek użytkownika, panele układu i strony.  
  
2.  Wszędzie tam, gdzie kontrakt deklaruje, że interfejs użytkownika będą przekazywane między dodatek a host, musi być zadeklarowany jako <xref:System.AddIn.Contract.INativeHandleContract> (nie <xref:System.Windows.FrameworkElement>); <xref:System.AddIn.Contract.INativeHandleContract> odzwierciedla może być zastosowana zdalnie dodatek [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] mogą być przekazywane przez granice obszarów izolowanych.  
  
3.  Przed przesłaniem z dodatku domeny aplikacji <xref:System.Windows.FrameworkElement> jest dostarczana jako <xref:System.AddIn.Contract.INativeHandleContract> przez wywołanie metody <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>.  
  
4.  Po przekazywany do domeny aplikacji w aplikacji hosta, <xref:System.AddIn.Contract.INativeHandleContract> musi być udostępniane jako <xref:System.Windows.FrameworkElement> przez wywołanie metody <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>.  
  
 Jak <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, i <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> są używane zależy od konkretnego scenariusza. Poniższe sekcje zawierają szczegółowe informacje dla każdego modelu programowania.  
  
<a name="ReturnUIFromAddInContract"></a>   
## <a name="add-in-returns-a-user-interface"></a>Dodatek zwraca interfejsu użytkownika  
 Dodatku do zwrócenia [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] do aplikacji hosta, wymagane są następujące:  
  
1.  Aplikacja hosta i potoku musi być tworzone, zgodnie z opisem w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] [dodatki i rozszerzalność](../../../../docs/framework/add-ins/index.md) dokumentacji.  
  
2.  Kontrakt musi implementować <xref:System.AddIn.Contract.IContract> i do zwrócenia [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], kontrakt musi zadeklarować metodę z wartością zwracaną typu <xref:System.AddIn.Contract.INativeHandleContract>.  
  
3.  [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Jest ono przekazywane między dodatek i hostem aplikacji muszą bezpośrednio lub pośrednio pochodzi od <xref:System.Windows.FrameworkElement>.  
  
4.  [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Zwróconego przez dodatek musi zostać przekonwertowany z <xref:System.Windows.FrameworkElement> do <xref:System.AddIn.Contract.INativeHandleContract> przed przekroczeniem granic izolacji.  
  
5.  [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Który jest zwracany musi zostać przekonwertowany z <xref:System.AddIn.Contract.INativeHandleContract> do <xref:System.Windows.FrameworkElement> po przekroczeniu granic izolacji.  
  
6.  Aplikacja hosta Wyświetla zwróconego <xref:System.Windows.FrameworkElement>.  
  
 Na przykład, który demonstruje sposób wdrożenia dodatku, który zwraca [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], zobacz [tworzenia dodatku zwracającą interfejsu użytkownika](../../../../docs/framework/wpf/app-development/how-to-create-an-add-in-that-returns-a-ui.md).  
  
<a name="AddInIsAUI"></a>   
## <a name="add-in-is-a-user-interface"></a>Dodatek jest interfejs użytkownika  
 Gdy dodatek jest [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], wymagane są następujące:  
  
1.  Aplikacja hosta i potoku musi być tworzone, zgodnie z opisem w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] [dodatki i rozszerzalność](../../../../docs/framework/add-ins/index.md) dokumentacji.  
  
2.  Musi implementować interfejs kontraktu dla dodatku <xref:System.AddIn.Contract.INativeHandleContract>.  
  
3.  Dodatek, który jest przekazywany do aplikacji hosta należy bezpośrednio ani pośrednio dziedziczyć <xref:System.Windows.FrameworkElement>.  
  
4.  Dodatek musi zostać przekonwertowany z <xref:System.Windows.FrameworkElement> do <xref:System.AddIn.Contract.INativeHandleContract> przed przekroczeniem granic izolacji.  
  
5.  Dodatek musi zostać przekonwertowany z <xref:System.AddIn.Contract.INativeHandleContract> do <xref:System.Windows.FrameworkElement> po przekroczeniu granic izolacji.  
  
6.  Aplikacja hosta Wyświetla zwróconego <xref:System.Windows.FrameworkElement>.  
  
 Na przykład, który demonstruje sposób wdrożenia dodatku, który jest [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], zobacz [dodatku jest tworzenie interfejsu użytkownika](../../../../docs/framework/wpf/app-development/how-to-create-an-add-in-that-is-a-ui.md).  
  
<a name="ReturningMultipleUIsFromAnAddIn"></a>   
## <a name="returning-multiple-uis-from-an-add-in"></a>Zwracanie wielu UI z dodatku  
 Dodatki często udostępniają wiele [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] dla hosta aplikacji do wyświetlenia. Rozważmy na przykład dodatku, który jest [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] również udostępniająca informacje o stanie do aplikacji hosta również jako [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Dodaj w następujący sposób można zaimplementować przy użyciu kombinacji metod z obu [interfejsu użytkownika dodatku zwraca](#ReturnUIFromAddInContract) i [dodatek jest to interfejs użytkownika](#AddInIsAUI) modeli.  
  
<a name="AddInsAndXBAPs"></a>   
## <a name="add-ins-and-xaml-browser-applications"></a>Dodatki i aplikacje przeglądarki XAML  
 W przykładach do tej pory aplikacji hosta została autonomiczny zainstalowanych aplikacji. Ale [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] może również obsługiwać dodatków, choć z następujące dodatkowe wymagania kompilacji i wdrażania:  
  
-   [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Manifest aplikacji musi być skonfigurowany specjalnie w celu pobrania potoku (foldery i zestawy) i zestaw dodatku do [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] pamięci podręcznej aplikacji na komputerze klienckim, w tym samym folderze co [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)].  
  
-   [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Kod, aby odnaleźć i załadować dodatków, należy użyć [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] pamięci podręcznej aplikacji dla [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] jako lokalizacji potoku i dodatek.  
  
-   [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Musi załadować dodatku w kontekście zabezpieczeń specjalnych, jeśli dodatek odwołuje się utracić pliki, które znajdują się w witrynie pochodzenia; obsługiwany przez [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], dodatki może odwoływać się tylko utracić pliki, które znajdują się w aplikacji hosta lokacji pochodzenia.  
  
 Te zadania opisano szczegółowo w poniższych podsekcjach.  
  
### <a name="configuring-the-pipeline-and-add-in-for-clickonce-deployment"></a>Konfigurowanie potoku i Add-In for wdrażania ClickOnce  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] pobrana i uruchom z folderu bezpieczne w [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] wdrożenia w pamięci podręcznej. Aby [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] do hostowania dodatku, potoku i Dodaj w zestawie musi zostać pobrana do folderu bezpieczne. Aby to osiągnąć, należy skonfigurować manifestu aplikacji obejmują potoku i zestawu dodatku do pobrania. Jest to łatwo zrobić [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], mimo że zestawu potoku i dodatek musi być na hoście [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] katalogu głównym projektu, aby [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] do wykrywania zestawy potoku.  
  
 W związku z tym, pierwszym krokiem jest utworzenie potoku i zestawu dodatku do [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] głównego projektu przez ustawienie każdego potoku dane wyjściowe kompilacji zestawu i dodatek zestaw projektów. W poniższej tabeli przedstawiono kompilacji dane wyjściowe ścieżki potoku zestaw projektów i projekt zestawu dodatku znajdujących się w tym samym folderze rozwiązania i głównego jako host [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] projektu.  
  
 Tabela 1: Tworzenie ścieżek danych wyjściowych dla zestawów potoku, które są obsługiwane przez XBAP  
  
|Projekt zestawu potoku|Ścieżka danych wyjściowych kompilacji|  
|-------------------------------|-----------------------|  
|Kontrakt|`..\HostXBAP\Contracts\`|  
|Dodaj w widoku|`..\HostXBAP\AddInViews\`|  
|Dodawanie strony karty|`..\HostXBAP\AddInSideAdapters\`|  
|Adaptery po stronie hosta|`..\HostXBAP\HostSideAdapters\`|  
|Dodatek|`..\HostXBAP\AddIns\WPFAddIn1`|  
  
 Następnym krokiem jest określenie zestawu dodatku jako i zestawy potoku [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] zawartość plików w [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] przez wykonanie następujących czynności:  
  
1.  W tym potoku i dodatek zestawu w projekcie prawym przyciskiem myszy każdy potoku folder w Eksploratorze rozwiązań i wybierając pozycję **załącz do projektu**.  
  
2.  Ustawienie **Akcja kompilacji** każdego zestawu potoku i zestawu dodatku do **zawartości** z **właściwości** okna.  
  
 Ostatnim krokiem jest skonfigurowanie manifest aplikacji, aby uwzględnić pliki zestawu potoku i pliku zestawu w dodatku do pobrania. Pliki powinny się znajdować w folderach w katalogu głównym folderu w [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] pamięci podręcznej, który [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] zajmuje aplikacji. Konfiguracja można osiągnąć [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] przez wykonanie następujących czynności:  
  
1.  Kliknij prawym przyciskiem myszy [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] projektu, kliknij przycisk **właściwości**, kliknij przycisk **publikowania**, a następnie kliknij przycisk **pliki aplikacji** przycisku.  
  
2.  W **pliki aplikacji** okno dialogowe, zestaw **stan publikowania** każdego potoku i biblioteki DLL dodatku **Include (automatycznie)** i ustaw **grupy pobierania** dla każdego potoku i DLL dodatku do **(wymagane)**.  
  
### <a name="using-the-pipeline-and-add-in-from-the-application-base"></a>Za pomocą potoku i dodać od podstawy aplikacji  
 Jeśli skonfigurowana potoku i Dodaj do [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] wdrożenia, są one pobierane do tej samej [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] folder pamięci podręcznej jako [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]. Aby użyć potoku i dodatek z [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] kod należy pobrać je z aplikacji podstawowej. Różne typy i elementy członkowskie [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dodatku modelu przy użyciu potoków i dodatki zapewniają obsługę specjalne dla tego scenariusza. Po pierwsze, ścieżka jest określana przez <xref:System.AddIn.Hosting.PipelineStoreLocation.ApplicationBase> wartości wyliczenia. Możesz Użyj tej wartości z przeciążeń odpowiednich członków dodatku przy użyciu potoki, które obejmują następujące czynności:  
  
-   <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>  
  
-   <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%2CSystem.String%5B%5D%29?displayProperty=nameWithType>  
  
-   <xref:System.AddIn.Hosting.AddInStore.Rebuild%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>  
  
-   <xref:System.AddIn.Hosting.AddInStore.Update%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>  
  
### <a name="accessing-the-hosts-site-of-origin"></a>Uzyskiwanie dostępu do hosta witryny pochodzenia  
 Aby upewnić się, że dodatek może odwoływać się plików z witryny pochodzenia, dodatek muszą być ładowane przy użyciu izolacji zabezpieczeń, który jest odpowiednikiem aplikacji hosta. Ten poziom zabezpieczeń jest identyfikowany przez <xref:System.AddIn.Hosting.AddInSecurityLevel.Host?displayProperty=nameWithType> wartość wyliczenia i przekazywane do <xref:System.AddIn.Hosting.AddInToken.Activate%2A> metody, gdy dodatek jest aktywny.  
  
<a name="WPFAddInModelArchitecture"></a>   
## <a name="wpf-add-in-architecture"></a>Architektura dodatków WPF  
 Na najwyższym poziomie jak firma Microsoft w tym samouczku, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] umożliwia [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dodatki do zaimplementowania [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] (który pochodzi bezpośrednio lub pośrednio od <xref:System.Windows.FrameworkElement>) przy użyciu <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> i <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>. Wynik jest zwracany jest aplikacja hosta <xref:System.Windows.FrameworkElement> która jest wyświetlana z [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] w aplikacji hosta.  
  
 Dla prostej [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scenariusze dodatku jest tyle szczegółów deweloper musi. Dla bardziej złożonymi scenariuszami, zwłaszcza tych, które spróbuj mogą korzystać z dodatkowych [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] usług, takie jak układ, zasobów i powiązanie, danych bardziej szczegółowych informacji dotyczących jak [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] rozszerza [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] modelu dodatku z [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Obsługa jest wymagana do zrozumieć jego korzyści i ograniczeń.  
  
 Zasadniczo [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] nie przeszło [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] z dodatku do aplikacji hosta; zamiast tego [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] przekazuje Win32 uchwytu okna [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] przy użyciu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] współdziałania. Tak, gdy [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] z dodatku jest przekazywany do aplikacji hosta, wystąpią następujące zdarzenia:  
  
-   Na stronie dodatku [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uzyskuje uchwytu okna dla [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] który będzie wyświetlany w aplikacji hosta. Uchwyt okna jest hermetyzowany przez wewnętrznego [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] klasą pochodzącą z <xref:System.Windows.Interop.HwndSource> i implementuje <xref:System.AddIn.Contract.INativeHandleContract>. Wystąpienie tej klasy jest zwracany przez <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> i jest przekazywane z dodatku domeny aplikacji do aplikacji hosta domeny aplikacji.  
  
-   Na stronie aplikacji hosta [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] przepakowuje <xref:System.Windows.Interop.HwndSource> jako wewnętrznego [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] klasą pochodzącą z <xref:System.Windows.Interop.HwndHost> i wykorzystuje <xref:System.AddIn.Contract.INativeHandleContract>. Wystąpienie tej klasy jest zwracany przez <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> do aplikacji hosta.  
  
 <xref:System.Windows.Interop.HwndHost> istnieje, aby wyświetlić [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)], identyfikowane przez uchwytów okien z [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]. Aby uzyskać więcej informacji, zobacz [WPF i współdziałanie Win32](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md).  
  
 Podsumowując <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, i <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> umożliwiających uchwytu okna dla [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] przekazany z dodatku do aplikacji hosta, w której jest hermetyzowany przez <xref:System.Windows.Interop.HwndHost> i wyświetlane hosta aplikacji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
> [!NOTE]
>  Ponieważ aplikacja hosta pobiera <xref:System.Windows.Interop.HwndHost>, aplikacji hosta nie można przekonwertować obiektu, który jest zwracany przez <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> do typu zaimplementowano według dodatku (na przykład <xref:System.Windows.Controls.UserControl>).  
  
 Z natury <xref:System.Windows.Interop.HwndHost> ma pewne ograniczenia, które mają wpływ na sposób obsługi aplikacji można użyć ich. Jednak [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] rozszerza <xref:System.Windows.Interop.HwndHost> z kilka możliwości dla scenariuszy dodatku. Poniżej opisano te korzyści i ograniczeń.  
  
<a name="WPFAddInModelBenefits"></a>   
## <a name="wpf-add-in-benefits"></a>WPF dodatku korzyści  
 Ponieważ [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dodatku [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] są wyświetlane z hosta aplikacji przy użyciu klasą wewnętrzną, która jest pochodną <xref:System.Windows.Interop.HwndHost>, w których [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] są ograniczone przez możliwości <xref:System.Windows.Interop.HwndHost> w odniesieniu do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] usług, takich jak układ, renderowanie wiązania z danymi, style, szablonów i zasobów. Jednak [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] wspomaga wewnętrznymi <xref:System.Windows.Interop.HwndHost> podklasy dodatkowe funkcje, które są następujące:  
  
-   Przełączania między aplikacją hosta [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] i dodatku [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Należy pamiętać, że "dodatku jest [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]" model programowania wymaga karty serwerowe w dodatku do przesłonięcia <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> do Włączanie przełączania, czy dodatek jest zaufane w pełni lub częściowo zaufany.  
  
-   Wymagania dotyczące ułatwień dostępu dla — w ramach [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] które są wyświetlane w aplikacji hosta [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)].  
  
-   Włączanie [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] na uruchamianie aplikacji bezpiecznie w wielu scenariuszach domeny aplikacji.  
  
-   Zapobieganie nielegalnemu dostępowi do dodatku [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] okna obsługi dodatków uruchamianych przy użyciu izolacji zabezpieczeń (to znaczy piaskownicy częściowego zaufania zabezpieczeń). Wywołanie <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> zapewnia zabezpieczeń:  
  
    -   Dla "dodatku zwraca [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]" model programowania, jedynym sposobem, aby przekazać uchwytu okna dla dodatku [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] między izolację granic jest wywołanie <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>.  
  
    -   Dla "dodatku jest [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]" programowania modelu, zastępowanie <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> na Dodaj w stronie karty i wywoływania <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> (jak pokazano w powyższych przykładach) jest wymagane, ponieważ wywołuje karty Dodaj w po stronie `QueryContract` implementacji z karty po stronie hosta.  
  
-   Podanie wielu ochrony wykonywania domeny aplikacji. Ze względu na ograniczenia z domenami aplikacji nieobsłużonych wyjątków, które są generowane w domenach aplikacji dodatku spowodować całej aplikacji do awarii, nawet jeśli granica izolacji istnieje. Jednak [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] i [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] modelu dodatku zapewniają prosty sposób do obejścia tego problemu i zwiększenia stabilności aplikacji. A [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dodatku wyświetlający [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] tworzy <xref:System.Windows.Threading.Dispatcher> dla wątku, który domeny aplikacji jest uruchamiany, gdy aplikacja hosta [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji. Wykrywa wszystkie nieobsługiwanych wyjątków, które występują w domenie aplikacji obsługa <xref:System.Windows.Threading.Dispatcher.UnhandledException> zdarzenie [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dodatku <xref:System.Windows.Threading.Dispatcher>. Możesz uzyskać <xref:System.Windows.Threading.Dispatcher> z <xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A> właściwości.  
  
<a name="WPFAddInModelLimitations"></a>   
## <a name="wpf-add-in-limitations"></a>Ograniczenia dotyczące dodawania WPF  
 Poza korzyści który [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dodaje do zachowania domyślne, dostarczone przez <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost>i uchwytów okien, obowiązują również ograniczenia dodatku [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] które są wyświetlane w aplikacji hosta:  
  
-   Dodatek [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] wyświetlany z hosta aplikacji nie przestrzega zachowanie wycinka aplikacji hosta.  
  
-   Pojęcie *powietrznej* w współdziałanie scenariusze dotyczą również dodatków (zobacz [omówienie technologii regionów](../../../../docs/framework/wpf/advanced/technology-regions-overview.md)).  
  
-   Aplikację hosta [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] usług, takich jak dziedziczenie zasobów, powiązania danych i są droższe, nie są automatycznie dostępne dla dodatku [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]. Zapewnienie tych usług do dodatku, musisz zaktualizować potoku.  
  
-   Dodatek [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] nie można obracać, skalowania, niesymetryczna lub w przeciwnym razie wpływ transformację (zobacz [przekształca omówienie](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)).  
  
-   Zawartości wewnątrz dodatku [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] który jest renderowany za pomocą operacji rysowania <xref:System.Drawing> przestrzeni nazw może obejmować przenikanie alfa. Jednak zarówno dodatek [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] a host [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] która zawiera 100% musi być nieprzezroczyste; innymi słowy, `Opacity` właściwość zarówno musi być ustawiona na 1.  
  
-   Jeśli <xref:System.Windows.Window.AllowsTransparency%2A> właściwość okna w aplikacji hosta, który zawiera dodatek [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ma ustawioną wartość `true`, dodatek jest niewidoczny. Dotyczy to nawet wtedy, gdy dodatek [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] jest nieprzezroczysta 100% (to znaczy `Opacity` właściwość ma wartość 1).  
  
-   Dodatek [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] musi znajdować się na drugim [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] elementów w tym samym oknie najwyższego poziomu.  
  
-   Nie części dodatku [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] może być renderowany przy użyciu <xref:System.Windows.Media.VisualBrush>. Zamiast tego dodatku mogą utworzyć migawkę wygenerowany [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] można utworzyć mapy bitowej, które mogą zostać przekazane do aplikacji hosta przy użyciu metody zdefiniowane przez umowy.  
  
-   Nie można odtworzyć pliki multimedialne z <xref:System.Windows.Controls.MediaElement> w dodatku [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
-   Mysz zdarzenia generowane dla dodatku [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] są Odebrano ani zgłoszone przez aplikację hosta i `IsMouseOver` właściwości dla aplikacji hosta [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ma wartość `false`.  
  
-   Gdy fokus zostanie przeniesiony między formantami w dodatku [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], `GotFocus` i `LostFocus` zdarzenia nie są odebrane ani zgłoszone przez aplikację hosta.  
  
-   Część aplikacji hosta, który zawiera dodatek [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pojawi się białym znakiem, po wydrukowaniu.  
  
-   Wszystkie dyspozytorów (zobacz <xref:System.Windows.Threading.Dispatcher>) utworzone przez dodatek [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] muszą zostać wyłączone ręcznie przed dodatku właściciela zostanie zwolniona, jeśli aplikacja hosta kontynuuje wykonywanie. Kontrakt można zaimplementować metody, które pozwalają na sygnał dodatek przed dodatek jest załadowany, umożliwiając dodatek aplikacji hosta [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] zamknie jego dyspozytorów.  
  
-   Jeśli dodatek [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] jest <xref:System.Windows.Controls.InkCanvas> lub zawiera <xref:System.Windows.Controls.InkCanvas>, nie można zwolnić dodatku.  
  
<a name="PerformanceOptimization"></a>   
## <a name="performance-optimization"></a>Optymalizacja wydajności  
 Domyślnie w przypadku używania wielu domen aplikacji różnych [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zestawy wymagane przez poszczególne aplikacje są wszystkie załadowane do domeny tej aplikacji. W związku z tym czas wymagany do tworzenia nowych domen aplikacji i uruchamianie aplikacji w nich mogą mieć wpływ na wydajność. Jednak [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pozwala zmniejszyć godziny rozpoczęcia przez poinstruowanie aplikacji do udostępniania zestawów między domenami aplikacji, jeśli zostały już załadowane. Można to zrobić przy użyciu <xref:System.LoaderOptimizationAttribute> atrybut, który należy zastosować do metody punktu wejścia (`Main`). W takim przypadku należy użyć tylko kodu do zaimplementowania definicji aplikacji (zobacz [omówienie zarządzania aplikacji](../../../../docs/framework/wpf/app-development/application-management-overview.md)).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.LoaderOptimizationAttribute>  
 [Dodatki i rozszerzalność](../../../../docs/framework/add-ins/index.md)  
 [Domeny aplikacji](../../../../docs/framework/app-domains/application-domains.md)  
 [.NET framework zdalnych — omówienie](http://msdn.microsoft.com/library/eccb1d31-0a22-417a-97fd-f4f1f3aa4462)  
 [Tworzenie obiektów może być zastosowana zdalnie](http://msdn.microsoft.com/library/01197253-3f13-43b7-894d-9683e431192a)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/app-development/how-to-topics.md)
