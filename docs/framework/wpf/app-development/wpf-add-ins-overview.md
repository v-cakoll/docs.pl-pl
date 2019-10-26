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
ms.openlocfilehash: e1daf9efd59b89d5d5be5f51cf9ac5e00750dda3
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2019
ms.locfileid: "72919723"
---
# <a name="wpf-add-ins-overview"></a>Przegląd Dodatki WPF

<a name="Introduction"></a>.NET Framework zawiera model dodatków, za pomocą którego deweloperzy mogą tworzyć aplikacje obsługujące rozszerzalność dodatków. Ten model dodatku umożliwia tworzenie dodatków, które integrują się z funkcjonalnością i rozszerzenia aplikacji. W niektórych scenariuszach aplikacje muszą również wyświetlać interfejsy użytkownika udostępniane przez dodatki. W tym temacie pokazano, w jaki sposób WPF rozszerza model dodatku .NET Framework, aby umożliwić te scenariusze, jego architekturę, korzyści i ograniczenia.

<a name="Requirements"></a>

## <a name="prerequisites"></a>Wymagania wstępne

Wymagana jest znajomość modelu dodatku .NET Framework. Aby uzyskać więcej informacji, zobacz [Dodatki i rozszerzalność](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).

<a name="AddInsOverview"></a>

## <a name="add-ins-overview"></a>Omówienie dodatków

Aby uniknąć złożoności ponownej kompilacji i ponownego wdrożenia aplikacji w celu uwzględnienia nowych funkcji, aplikacje implementują mechanizmy rozszerzalności, które umożliwiają deweloperom (podmiotom pierwszej firmy i innej firmy) Tworzenie innych aplikacji, które Zintegruj z nimi. Najbardziej typowym sposobem obsługi tego typu rozszerzalności jest użycie dodatków (znanych również jako "Dodatki" i "wtyczki"). Przykładowe aplikacje w świecie, które uwidaczniają rozszerzalność z dodatkami, to m.in.:

- Dodatki programu Internet Explorer.

- Dodatki plug-in systemu Windows Media Player.

- Dodatki programu Visual Studio.

Na przykład model dodatku systemu Windows Media Player umożliwia deweloperom innych firm implementowanie dodatków plug-in, które poszerzają Media Player systemu Windows na różne sposoby, w tym tworzenie dekoderów i koderów dla formatów multimedialnych, które nie są obsługiwane natywnie przez system Windows Media Player (na przykład DVD, MP3), efekty audio i karnacje. Każdy model dodatku jest zbudowany w celu udostępnienia funkcji, która jest unikatowa dla aplikacji, chociaż istnieje kilka podmiotów i zachowań, które są wspólne dla wszystkich modeli dodatków.

Trzy główne jednostki typowych rozwiązań rozszerzalności dodatków to *kontrakty*, *Dodatki*i *aplikacje obsługujące hosty*. Kontrakty definiują sposób integracji dodatków z aplikacjami hosta na dwa sposoby:

- Dodatki integrują się z funkcją wdrożoną przez aplikacje hosta.

- Aplikacje hosta udostępniają funkcje dodatków do integracji z programem.

Aby można było używać dodatków, aplikacje hosta muszą je znaleźć i załadować w czasie wykonywania. W związku z tym aplikacje obsługujące dodatki mają następujące dodatkowe obowiązki:

- **Odnajdywanie**: Znajdowanie dodatków, które są zgodne z kontraktami obsługiwanymi przez aplikacje hosta.

- **Aktywacja**: ładowanie, uruchamianie i nawiązywanie komunikacji z dodatkami.

- **Izolacja**: korzystając z domen lub procesów aplikacji, można ustanowić granice izolacji chroniące aplikacje przed potencjalnymi problemami związanymi z zabezpieczeniami i wykonywaniem.

- **Komunikacja**: zezwolenie na dodatki i aplikacje hosta do komunikacji ze sobą w granicach izolacji przez wywoływanie metod i przekazywanie danych.

- **Zarządzanie okresem istnienia**: ładowanie i zwalnianie domen i procesów aplikacji w czysty i przewidywalny sposób (zobacz [domeny aplikacji](../../app-domains/application-domains.md)).

- **Przechowywanie wersji**: zapewnianie, że aplikacje i dodatki hosta mogą nadal komunikować się po utworzeniu nowych wersji programu.

Ostatecznie tworzenie niezawodnego modelu dodatków jest nieuproszczonym przedsiębiorstwem. Z tego powodu .NET Framework zapewnia infrastrukturę do tworzenia modeli dodatków.

> [!NOTE]
> Aby uzyskać bardziej szczegółowe informacje na temat dodatków, zobacz [Dodatki i rozszerzalność](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).

<a name="NETFrameworkAddInModelOverview"></a>

## <a name="net-framework-add-in-model-overview"></a>Omówienie modelu dodatku .NET Framework

.NET Framework model dodatku, który znajduje się w przestrzeni nazw <xref:System.AddIn>, zawiera zestaw typów, które są zaprojektowane w celu uproszczenia opracowywania rozszerzalności dodatków. Podstawową jednostką modelu dodatku .NET Framework jest *kontrakt*, który definiuje sposób, w jaki aplikacja hosta i dodatek komunikują się ze sobą. Kontrakt jest udostępniany aplikacji hosta za pomocą *widoku* określonego dla aplikacji hosta. Podobnie, szczegółowy *Widok* kontraktu jest narażony na dodatek. *Adapter* służy do zezwalania aplikacji hosta i dodatku do komunikacji między odpowiednimi widokami kontraktu. Kontrakty, widoki i karty są określane jako segmenty, a zestaw powiązanych segmentów stanowi *potoku*. Potoki stanowią podstawę, w której model dodatku .NET Framework obsługuje odnajdywanie, aktywację, izolację zabezpieczeń, izolację wykonania (przy użyciu aplikacji i procesów, zarządzania komunikacją, okresem istnienia i przechowywania wersji).

Suma tej obsługi umożliwia deweloperom tworzenie dodatków, które integrują się z funkcjonalnością aplikacji hosta. Jednak niektóre scenariusze wymagają, aby aplikacje hosta wyświetlały interfejsy użytkownika udostępniane przez dodatki. Ponieważ każda Technologia prezentacji w .NET Framework ma własny model do implementowania interfejsów użytkownika, .NET Framework model dodatku nie obsługuje żadnej konkretnej technologii prezentacji. Zamiast tego, WPF rozszerza model dodatku .NET Framework z obsługą interfejsu użytkownika dla dodatków.

<a name="WPFAddInModel"></a>

## <a name="wpf-add-ins"></a>Dodatki WPF

WPF, w połączeniu z modelem dodatku .NET Framework, umożliwia rozwiązywanie różnorodnych scenariuszy, które wymagają, aby aplikacje hosta wyświetlały interfejsy użytkownika z dodatków. W szczególności te scenariusze są rozwiązywane przez WPF z następującymi dwoma modelami programowania:

1. **Dodatek zwraca interfejs użytkownika**. Dodatek zwraca interfejs użytkownika do aplikacji hosta za pośrednictwem wywołania metody, zgodnie z definicją kontraktu. Ten scenariusz jest używany w następujących przypadkach:

    - Wygląd interfejsu użytkownika, który jest zwracany przez dodatek, zależy od danych lub warunków, które istnieją tylko w czasie wykonywania, takich jak raporty generowane dynamicznie.

    - Interfejs użytkownika dla usług udostępnianych przez dodatek różni się od interfejsu użytkownika aplikacji hosta, które mogą korzystać z dodatku.

    - Dodatek wykonuje głównie usługę dla aplikacji hosta i raportuje stan do aplikacji hosta za pomocą interfejsu użytkownika.

2. **Dodatek jest interfejsem użytkownika**. Dodatek jest interfejsem użytkownika, zdefiniowanym przez kontrakt. Ten scenariusz jest używany w następujących przypadkach:

    - Dodatek nie zapewnia usług innych niż wyświetlane, takich jak anonsowanie.

    - Interfejs użytkownika dla usług udostępnianych przez dodatek jest wspólny dla wszystkich aplikacji hosta, które mogą korzystać z tego dodatku, takich jak Kalkulator lub selektor kolorów.

Te scenariusze wymagają, aby obiekty interfejsu użytkownika mogły być przesyłane między aplikacjami hosta i domenami aplikacji dodatkowych. Ponieważ model dodatku .NET Framework polega na komunikacji zdalnej między domenami aplikacji, obiekty, które są przekazywane między nimi, muszą być zdalne.

Obiekt zdalny jest wystąpieniem klasy, która wykonuje co najmniej jedną z następujących czynności:

- Pochodzi z klasy <xref:System.MarshalByRefObject>.

- Implementuje interfejs <xref:System.Runtime.Serialization.ISerializable>.

- Ma zastosowany atrybut <xref:System.SerializableAttribute>.

> [!NOTE]
> Aby uzyskać więcej informacji na temat tworzenia obiektów .NET Framework zdalnych, zobacz [Tworzenie obiektów zdalnie](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/wcf3swha(v=vs.100)).

Typy interfejsu użytkownika WPF nie są zdalne. Aby rozwiązać ten problem, WPF rozszerza model dodatku .NET Framework, aby umożliwić wyświetlanie interfejsu użytkownika WPF utworzonego przez dodatki do wyświetlania z aplikacji hosta. To wsparcie jest obsługiwane przez WPF przez dwa typy: interfejs <xref:System.AddIn.Contract.INativeHandleContract> i dwie metody statyczne zaimplementowane przez klasę <xref:System.AddIn.Pipeline.FrameworkElementAdapters>: <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> i <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>. Na wysokim poziomie te typy i metody są używane w następujący sposób:

1. WPF wymaga, aby interfejsy użytkownika udostępniane przez dodatki to klasy, które są wyprowadzane bezpośrednio lub pośrednio z <xref:System.Windows.FrameworkElement>, takie jak kształty, formanty, formanty użytkownika, panele układu i strony.

2. Wszędzie tam, gdzie umowa deklaruje, że interfejs użytkownika zostanie przekazywać między dodatkiem a aplikacją hosta, musi być zadeklarowany jako <xref:System.AddIn.Contract.INativeHandleContract> (nie <xref:System.Windows.FrameworkElement>); <xref:System.AddIn.Contract.INativeHandleContract> jest reprezentacją zdalną interfejsu użytkownika dodatku, który można przekazywać między granicami izolacji.

3. Przed przekazaniem z domeny aplikacji dodatku <xref:System.Windows.FrameworkElement> jest spakowany jako <xref:System.AddIn.Contract.INativeHandleContract> przez wywołanie <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>.

4. Po przekazaniu do domeny aplikacji hosta <xref:System.AddIn.Contract.INativeHandleContract> należy ponownie spakować jako <xref:System.Windows.FrameworkElement> przez wywołanie <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>.

Sposób użycia <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>i <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> zależy od konkretnego scenariusza. Poniższe sekcje zawierają szczegółowe informacje dotyczące każdego modelu programowania.

<a name="ReturnUIFromAddInContract"></a>

## <a name="add-in-returns-a-user-interface"></a>Dodatek zwraca interfejs użytkownika

Aby dodatek mógł zwrócić interfejs użytkownika do aplikacji hosta, wymagane są następujące elementy:

1. Należy utworzyć aplikację hosta, dodatek i potok, zgodnie z opisem w temacie .NET Framework [Dodatki i dokumentacja rozszerzalności](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)) .

2. Kontrakt musi implementować <xref:System.AddIn.Contract.IContract> i, aby zwrócić interfejs użytkownika, kontrakt musi deklarować metodę z wartością zwracaną typu <xref:System.AddIn.Contract.INativeHandleContract>.

3. Interfejs użytkownika, który jest przesyłany między dodatkiem a aplikacją hosta, musi bezpośrednio lub pośrednio pochodzić od <xref:System.Windows.FrameworkElement>.

4. Interfejs użytkownika, który jest zwracany przez dodatek, musi zostać przekonwertowany z <xref:System.Windows.FrameworkElement> na <xref:System.AddIn.Contract.INativeHandleContract> przed przekroczeniem granicy izolacji.

5. Zwracany interfejs użytkownika musi zostać przekonwertowany z <xref:System.AddIn.Contract.INativeHandleContract> na <xref:System.Windows.FrameworkElement> po przekroczeniu granicy izolacji.

6. Aplikacja hosta wyświetla zwrócone <xref:System.Windows.FrameworkElement>.

Przykład demonstrujący sposób implementacji dodatku, który zwraca interfejs użytkownika, znajduje się w temacie [Tworzenie dodatku, który zwraca interfejs użytkownika](how-to-create-an-add-in-that-returns-a-ui.md).

<a name="AddInIsAUI"></a>

## <a name="add-in-is-a-user-interface"></a>Dodatek jest interfejsem użytkownika

Gdy dodatek jest interfejsem użytkownika, wymagane są następujące elementy:

1. Należy utworzyć aplikację hosta, dodatek i potok, zgodnie z opisem w temacie .NET Framework [Dodatki i dokumentacja rozszerzalności](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)) .

2. Interfejs kontraktu dla dodatku musi implementować <xref:System.AddIn.Contract.INativeHandleContract>.

3. Dodatek, który jest przesyłany do aplikacji hosta, musi bezpośrednio lub pośrednio pochodzić od <xref:System.Windows.FrameworkElement>.

4. Dodatek musi zostać przekonwertowany z <xref:System.Windows.FrameworkElement> na <xref:System.AddIn.Contract.INativeHandleContract> przed przekroczeniem granicy izolacji.

5. Dodatek musi zostać przekonwertowany z <xref:System.AddIn.Contract.INativeHandleContract> na <xref:System.Windows.FrameworkElement> po przekroczeniu granicy izolacji.

6. Aplikacja hosta wyświetla zwrócone <xref:System.Windows.FrameworkElement>.

Aby zapoznać się z przykładem, który ilustruje sposób implementacji dodatku, który jest interfejsem użytkownika, zobacz [Tworzenie dodatku, który jest interfejsem użytkownika](how-to-create-an-add-in-that-is-a-ui.md).

<a name="ReturningMultipleUIsFromAnAddIn"></a>

## <a name="returning-multiple-uis-from-an-add-in"></a>Zwracanie wielu interfejsów użytkownika z dodatku

Dodatki często udostępniają wiele interfejsów użytkownika do wyświetlania aplikacji hosta. Rozważmy na przykład dodatek, który jest interfejsem użytkownika, który udostępnia również informacje o stanie aplikacji hosta, również jako interfejs użytkownika. Dodatek podobny do tego można zaimplementować przy użyciu kombinacji technik z obu [dodatków zwraca interfejs użytkownika](#ReturnUIFromAddInContract) , a [dodatek jest modelami interfejsu użytkownika](#AddInIsAUI) .

<a name="AddInsAndXBAPs"></a>

## <a name="add-ins-and-xaml-browser-applications"></a>Dodatki i aplikacje przeglądarki XAML

W przykładach do tej pory aplikacja hosta była zainstalowaną aplikacją autonomiczną. Ale [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] mogą również hostować dodatki, chociaż z następującymi dodatkowymi wymaganiami dotyczącymi kompilacji i implementacji:

- Manifest aplikacji [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] musi być skonfigurowany specjalnie do pobierania potoku (folderów i zestawów) oraz zestawu dodatków do pamięci podręcznej aplikacji ClickOnce na komputerze klienckim, w tym samym folderze co [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)].

- Kod [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] do odnalezienia i załadowania dodatków musi używać pamięci podręcznej aplikacji ClickOnce dla [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] jako lokalizacji potoków i dodatków.

- [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] musi załadować dodatek do specjalnego kontekstu zabezpieczeń, jeśli dodatek odwołuje się do luźnych plików, które znajdują się w miejscu pochodzenia; w przypadku hostowania przez [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]Dodatki mogą odwoływać się tylko do swobodnych plików, które znajdują się w lokalizacji źródłowej aplikacji hosta.

Te zadania są szczegółowo opisane w poniższych podsekcjach.

### <a name="configuring-the-pipeline-and-add-in-for-clickonce-deployment"></a>Konfigurowanie potoku i dodatku dla wdrożenia ClickOnce

[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] są pobierane do i uruchamiane z bezpiecznego folderu w pamięci podręcznej wdrażania ClickOnce. Aby [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] hostować dodatek, należy również pobrać potok i zestaw dodatków do bezpiecznego folderu. Aby to osiągnąć, należy skonfigurować manifest aplikacji w taki sposób, aby obejmował zarówno potok, jak i zestaw dodatków do pobrania. Jest to najłatwiej wykonywane w programie Visual Studio, chociaż potok i zestaw dodatku muszą znajdować się w folderze głównym hosta [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] projektu, aby program Visual Studio wykrył zestawy potoków.

W związku z tym pierwszym krokiem jest skompilowanie potoku i zestawu dodatków do głównego katalogu [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] projektu przez ustawienie danych wyjściowych kompilacji dla każdego zestawu potoku i projektów zestawu dodatków. W poniższej tabeli przedstawiono ścieżki wyjściowe kompilacji dla projektów zestawu potoku i projektu zestawu dodatków, które znajdują się w tym samym rozwiązaniu i folderze głównym co [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] hosta.

Tabela 1: Tworzenie ścieżek wyjściowych dla zestawów potoku hostowanych przez aplikację XBAP

|Projekt zestawu potoku|Ścieżka wyjściowa kompilacji|
|-------------------------------|-----------------------|
|Kontrakt|`..\HostXBAP\Contracts\`|
|Widok dodatku|`..\HostXBAP\AddInViews\`|
|Adapter dodatku|`..\HostXBAP\AddInSideAdapters\`|
|Adapter po stronie hosta|`..\HostXBAP\HostSideAdapters\`|
|Dodatek|`..\HostXBAP\AddIns\WPFAddIn1`|

Następnym krokiem jest określenie zestawów potoku i zestawu dodatków jako plików zawartości [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] w programie Visual Studio, wykonując następujące czynności:

1. Uwzględniając potok i zestaw dodatków w projekcie, klikając prawym przyciskiem myszy każdy folder potoku w Eksplorator rozwiązań i wybierając opcję **Dołącz do projektu**.

2. Ustawianie **akcji kompilacji** dla każdego zestawu potoku i zestawu dodatków do **zawartości** z okna **Właściwości** .

Ostatnim krokiem jest skonfigurowanie manifestu aplikacji w celu uwzględnienia plików zestawu potoku i pliku zestawu dodatku do pobrania. Pliki powinny znajdować się w folderach w folderze głównym folderu w pamięci podręcznej ClickOnce, w której zajmowana jest aplikacja [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]. Konfigurację można uzyskać w programie Visual Studio, wykonując następujące czynności:

1. Kliknij prawym przyciskiem myszy projekt [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], kliknij pozycję **Właściwości**, kliknij pozycję **Opublikuj**, a następnie kliknij przycisk **pliki aplikacji** .

2. W oknie dialogowym **pliki aplikacji** Ustaw **stan publikacji** każdego potoku i dodatku dll na wartość ( **Auto)** i ustaw **grupę pobierania** dla każdego potoku i dodatku dll na **(wymagane)** .

### <a name="using-the-pipeline-and-add-in-from-the-application-base"></a>Korzystanie z potoku i dodatku z bazy aplikacji

Gdy potok i dodatek są skonfigurowane do wdrażania ClickOnce, są pobierane do tego samego folderu pamięci podręcznej ClickOnce co [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]. Aby użyć potoku i dodatku z [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], kod [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] musi pobrać je z bazy aplikacji. Różne typy i elementy członkowskie modelu dodatku .NET Framework na potrzeby używania potoków i dodatków zapewniają specjalną pomoc techniczną dla tego scenariusza. Po pierwsze ścieżka jest identyfikowana przez <xref:System.AddIn.Hosting.PipelineStoreLocation.ApplicationBase> wartość wyliczenia. Ta wartość jest używana z przeciążeniami odpowiednich członków dodatku, aby używać potoków, które obejmują następujące elementy:

- <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>

- <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%2CSystem.String%5B%5D%29?displayProperty=nameWithType>

- <xref:System.AddIn.Hosting.AddInStore.Rebuild%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>

- <xref:System.AddIn.Hosting.AddInStore.Update%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>

### <a name="accessing-the-hosts-site-of-origin"></a>Uzyskiwanie dostępu do lokacji hosta pochodzenia

Aby zapewnić, że dodatek może odwoływać się do plików z lokacji źródłowej, dodatek musi być załadowany z izolacją zabezpieczeń, która jest równoważna z aplikacją hosta. Ten poziom zabezpieczeń jest identyfikowany przez <xref:System.AddIn.Hosting.AddInSecurityLevel.Host?displayProperty=nameWithType> wartość wyliczenia i przeszedł do metody <xref:System.AddIn.Hosting.AddInToken.Activate%2A>, gdy dodatek jest aktywowany.

<a name="WPFAddInModelArchitecture"></a>

## <a name="wpf-add-in-architecture"></a>Architektura dodatku WPF

Na najwyższym poziomie, w miarę jak się widzimy, WPF umożliwia .NET Framework dodatków do implementowania interfejsów użytkownika (które pochodzą bezpośrednio lub pośrednio z <xref:System.Windows.FrameworkElement>) przy użyciu <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> i <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>. Wynika to z tego, że aplikacja hosta zwraca <xref:System.Windows.FrameworkElement>, który jest wyświetlany z interfejsu użytkownika w aplikacji hosta.

W przypadku prostych scenariuszy dodatków interfejsu użytkownika jest to tak szczegółowe, jak w przypadku deweloperów. W przypadku bardziej złożonych scenariuszy, szczególnie tych, które próbują korzystać z dodatkowych usług WPF, takich jak układ, zasoby i powiązania danych, bardziej szczegółową wiedzą o tym, jak WPF rozszerza model dodatku .NET Framework z obsługą interfejsu użytkownika, aby zrozumieć jego korzyści i ograniczenia.

W rzeczywistości funkcja WPF nie przekazuje interfejsu użytkownika z dodatku do aplikacji hosta. Zamiast tego, WPF przekazuje uchwyt okna Win32 dla interfejsu użytkownika przy użyciu współdziałania WPF. W związku z tym, gdy interfejs użytkownika z dodatku jest przesyłany do aplikacji hosta, występują następujące sytuacje:

- Na stronie dodatku WPF uzyskuje uchwyt okna dla interfejsu użytkownika, który będzie wyświetlany przez aplikację hosta. Uchwyt okna jest hermetyzowany przez wewnętrzną klasę WPF, która pochodzi z <xref:System.Windows.Interop.HwndSource> i implementuje <xref:System.AddIn.Contract.INativeHandleContract>. Wystąpienie tej klasy jest zwracane przez <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> i jest organizowane z domeny aplikacji dodatku do domeny aplikacji hosta.

- Na stronie aplikacji hosta platforma WPF ponownie pakuje <xref:System.Windows.Interop.HwndSource> jako wewnętrzną klasę WPF, która pochodzi od <xref:System.Windows.Interop.HwndHost> i wykorzystuje <xref:System.AddIn.Contract.INativeHandleContract>. Wystąpienie tej klasy jest zwracane przez <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> do aplikacji hosta.

<xref:System.Windows.Interop.HwndHost> istnieje, aby wyświetlić interfejsy użytkownika, identyfikowane przez uchwyty okna, z interfejsów użytkownika WPF. Aby uzyskać więcej informacji, zobacz [WPF i Win32 — współdziałanie](../advanced/wpf-and-win32-interoperation.md).

Podsumowując, <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>i <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> istnieją, aby zezwolić na przekazywanie uchwytu okna dla interfejsu użytkownika WPF z dodatku do aplikacji hosta, gdzie jest on hermetyzowany przez <xref:System.Windows.Interop.HwndHost> i wyświetla interfejs użytkownika aplikacji hosta.

> [!NOTE]
> Ponieważ aplikacja hosta pobiera <xref:System.Windows.Interop.HwndHost>, aplikacja hosta nie może skonwertować obiektu, który jest zwracany przez <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> do typu, który jest implementowany przez dodatek (na przykład <xref:System.Windows.Controls.UserControl>).

Z natury <xref:System.Windows.Interop.HwndHost> ma pewne ograniczenia, które mają wpływ na sposób ich używania przez aplikacje hosta. Jednak WPF rozszerza <xref:System.Windows.Interop.HwndHost> z kilkoma funkcjami dla scenariuszy dodatków. Te korzyści i ograniczenia są opisane poniżej.

<a name="WPFAddInModelBenefits"></a>

## <a name="wpf-add-in-benefits"></a>Zalety dodatków WPF

Ponieważ interfejsy użytkownika dodatku WPF są wyświetlane z aplikacji hosta przy użyciu wewnętrznej klasy, która pochodzi od <xref:System.Windows.Interop.HwndHost>, te interfejsy użytkownika są ograniczone przez możliwości <xref:System.Windows.Interop.HwndHost> w odniesieniu do usług interfejsu użytkownika WPF, takich jak układ, renderowanie, dane powiązanie, style, szablony i zasoby. Jednak WPF rozszerza swoją wewnętrzną podklasę <xref:System.Windows.Interop.HwndHost> z dodatkowymi możliwościami, które obejmują następujące elementy:

- Tabulacja między interfejsem użytkownika aplikacji hosta i interfejsem użytkownika dodatku. Należy pamiętać, że model programowania "dodatek jest interfejsem użytkownika" wymaga adaptera dodatku, aby przesłonić <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>, aby włączyć funkcję tabulacji, niezależnie od tego, czy dodatek jest w pełni zaufany, czy częściowo zaufany.

- Przestrzeganie wymagań dotyczących ułatwień dostępu dla interfejsów użytkownika dodatku, które są wyświetlane z interfejsów użytkownika aplikacji hosta.

- Włączanie bezpiecznego działania aplikacji WPF w wielu scenariuszach domen aplikacji.

- Zapobiegaj nielegalnemu dostępowi do okna interfejsu użytkownika dodatku, gdy dodatki są uruchamiane z izolacją zabezpieczeń (to jest obszar piaskownicy zabezpieczeń częściowego zaufania). Wywołanie <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> zapewnia następujące zabezpieczenia:

  - W przypadku modelu programowania "dodatek zwraca interfejs użytkownika" jedynym sposobem przekazania uchwytu okna dla interfejsu użytkownika dodatku w granicach izolacji jest wywołanie <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>.

  - W przypadku modelu programowania "dodatek jest interfejsem użytkownika" zastępowanie <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> na adapterze po stronie dodatku i wywoływanie <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> (jak pokazano w powyższych przykładach) jest wymagane, ponieważ wywołuje implementację `QueryContract` z karty sieciowej po stronie hosta.

- Udostępnianie wielu domen aplikacji ochrony przed wykonywaniem. Ze względu na ograniczenia dotyczące domen aplikacji Nieobsłużone wyjątki, które są zgłaszane w domenach aplikacji dodatków, powodują awarię całej aplikacji, nawet jeśli istnieje granica izolacji. Jednak funkcja WPF i .NET Framework model dodatków zapewniają prosty sposób obejścia tego problemu i zwiększenie stabilności aplikacji. Dodatek WPF, który wyświetla interfejs użytkownika tworzy <xref:System.Windows.Threading.Dispatcher> wątku, w którym jest uruchomiona domena aplikacji, jeśli aplikacja hosta jest aplikacją WPF. Można wykryć wszystkie Nieobsłużone wyjątki, które występują w domenie aplikacji przez obsługę zdarzenia <xref:System.Windows.Threading.Dispatcher.UnhandledException> <xref:System.Windows.Threading.Dispatcher>dodatku WPF. <xref:System.Windows.Threading.Dispatcher> można uzyskać z właściwości <xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A>.

<a name="WPFAddInModelLimitations"></a>

## <a name="wpf-add-in-limitations"></a>Ograniczenia dodatku WPF

Poza korzyściami, które program WPF dodaje do domyślnych zachowań dostarczonych przez <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost>i uchwyty okna, istnieją także ograniczenia dotyczące interfejsów użytkownika dodatku, które są wyświetlane z aplikacji hosta:

- Interfejsy użytkownika dodatku wyświetlane z aplikacji hosta nie respektują zachowania wycinka aplikacji hosta.

- Koncepcja *przestrzeni powietrznej* w scenariuszach współdziałania dotyczy również dodatków (zobacz [Omówienie regionów technologicznych](../advanced/technology-regions-overview.md)).

- Usługi interfejsu użytkownika aplikacji hosta, takie jak dziedziczenie zasobów, powiązanie danych i polecenia, nie są automatycznie dostępne dla interfejsów użytkowników dodatków. Aby zapewnić te usługi dla dodatku, należy zaktualizować potoku.

- Nie można obrócić, przeskalować, obchylać lub w inny sposób przekształceniu (zobacz [Przegląd transformacji](../graphics-multimedia/transforms-overview.md)).

- Zawartość wewnątrz interfejsów użytkownika dodatku, które są renderowane przez operacje rysowania z przestrzeni nazw <xref:System.Drawing>, może obejmować mieszanie alfa. Jednak zarówno interfejs użytkownika dodatku, jak i interfejs użytkownika aplikacji hosta, który go zawiera, muszą być 100% nieprzezroczyste; Innymi słowy Właściwość `Opacity` obu tych wartości musi być ustawiona na 1.

- Jeśli właściwość <xref:System.Windows.Window.AllowsTransparency%2A> okna w aplikacji hosta zawierającej interfejs użytkownika dodatku ma wartość `true`, dodatek jest niewidoczny. Jest to prawdziwe, nawet jeśli interfejs użytkownika dodatku ma 100% nieprzezroczysty (oznacza to, że właściwość `Opacity` ma wartość 1).

- Interfejs użytkownika dodatku musi znajdować się na innych elementach WPF w tym samym oknie najwyższego poziomu.

- Żadna część interfejsu użytkownika dodatku nie może być renderowana przy użyciu <xref:System.Windows.Media.VisualBrush>. Zamiast tego dodatek może wykonać migawkę wygenerowanego interfejsu użytkownika w celu utworzenia mapy bitowej, która może zostać przeniesiona do aplikacji hosta przy użyciu metod zdefiniowanych przez umowę.

- Pliki multimedialne nie mogą być odtwarzane z <xref:System.Windows.Controls.MediaElement> w interfejsie użytkownika dodatku.

- Zdarzenia myszy wygenerowane dla interfejsu użytkownika dodatku nie są odbierane ani zgłaszane przez aplikację hosta, a właściwość `IsMouseOver` dla interfejsu użytkownika aplikacji hosta ma wartość `false`.

- Gdy fokus jest przenoszony między kontrolkami w interfejsie użytkownika dodatku, zdarzenia `GotFocus` i `LostFocus` nie są odbierane ani zgłaszane przez aplikację hosta.

- Część aplikacji hosta zawierającej interfejs użytkownika dodatku pojawia się biały podczas drukowania.

- Wszystkie dyspozytory (zobacz <xref:System.Windows.Threading.Dispatcher>) utworzone za pomocą interfejsu użytkownika dodatku muszą być zamykane ręcznie przed wyładowaniem dodatku właściciela, jeśli aplikacja hosta kontynuuje wykonywanie. Umowa może implementować metody, które umożliwiają aplikacji hosta zasygnalizowanie dodatku przed usunięciem dodatku, a tym samym dodanie go do interfejsu użytkownika dodatku.

- Jeśli interfejs użytkownika dodatku jest <xref:System.Windows.Controls.InkCanvas> lub zawiera <xref:System.Windows.Controls.InkCanvas>, nie można zwolnić dodatku.

<a name="PerformanceOptimization"></a>

## <a name="performance-optimization"></a>Optymalizacja wydajności

Domyślnie, gdy są używane wiele domen aplikacji, do domeny tej aplikacji są ładowane różne zestawy .NET Framework wymagane przez poszczególne aplikacje. W związku z tym czas wymagany do tworzenia nowych domen aplikacji i uruchamiania aplikacji w nich może mieć wpływ na wydajność. Jednak .NET Framework umożliwia skrócenie czasu uruchamiania przez nakazujenie aplikacjom udostępniania zestawów w domenach aplikacji, jeśli są już załadowane. W tym celu należy użyć atrybutu <xref:System.LoaderOptimizationAttribute>, który należy zastosować do metody punktu wejścia (`Main`). W takim przypadku należy użyć tylko kodu w celu zaimplementowania definicji aplikacji (zobacz [Omówienie zarządzania aplikacjami](application-management-overview.md)).

## <a name="see-also"></a>Zobacz także

- <xref:System.LoaderOptimizationAttribute>
- [Dodatki i rozszerzalność](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [Domeny aplikacji](../../app-domains/application-domains.md)
- [.NET Framework Omówienie usług zdalnych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kwdt6w2k(v=vs.100))
- [Udostępnianie obiektów zdalnie](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/wcf3swha(v=vs.100))
- [Tematy z instrukcjami](how-to-topics.md)
