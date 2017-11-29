---
title: Domeny aplikacji
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- process boundaries for isolation
- application isolation
- application domains, about
- common language runtime, application domains
- application domains
- runtime, application domains
- isolation between applications
- code, verification process
- verification testing code
ms.assetid: 113a8bbf-6875-4a72-a49d-ca2d92e19cc8
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7a41a6bf29ec9310d88778b55aa0c27672ba0568
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="application-domains"></a>Domeny aplikacji
Systemy operacyjne i środowiska wykonawcze zwykle zapewnia jakiegoś izolacja pomiędzy aplikacjami. Na przykład system Windows używa procesów do izolowania aplikacji. Izolacja jest niezbędne do zapewnienia, że kod działający w jednej aplikacji nie może niekorzystnie wpłynąć na innych, niezależnych aplikacji.  
  
 Domeny aplikacji zawierają granica izolacji dla bezpieczeństwa, niezawodności i przechowywanie wersji i zwalnianie zestawów. Domeny aplikacji są zwykle tworzone przez hosty środowiska uruchomieniowego, które są odpowiedzialne za uruchamianie plików wykonywalnych języka przed uruchomieniem aplikacji.  
  
 Tematy w tej sekcji dokumentacji opisano sposób użycia domen aplikacji do rozdzielenia zestawów.  
  
 Ten przegląd zawiera następujące sekcje:  
  
-   [Zalety izolowania aplikacji](#benefits)  
  
-   [Odwołanie](#reference)  
  
<a name="benefits"></a>   
## <a name="the-benefits-of-isolating-applications"></a>Zalety izolowania aplikacji  
 W przeszłości były używane granice procesu do izolowania aplikacji uruchomionych na tym samym komputerze. Każda aplikacja została załadowana do osobnych procesach, która wyodrębnia ją spośród innych aplikacji uruchomionych na tym samym komputerze.  
  
 Aplikacje są izolowane, ponieważ adresy pamięci są względem procesu; wskaźnik pamięci przekazywane z jednego procesu do innego nie można używać w znaczący sposób w procesie docelowym. Ponadto nie można wprowadzić bezpośrednich połączeń między dwoma procesami. Zamiast tego należy użyć serwerów proxy, zapewniających poziomu pośrednie.  
  
 Zarządzany kod muszą być przekazywane przez proces weryfikacji przed uruchomieniem (chyba że administrator ma uprawnienia do pominięcia weryfikacji). Proces weryfikacji Określa, czy kod może próbować dostępu adresów pamięci nieprawidłowy lub wykonywać inne akcje, które może spowodować, że proces, w którym jest uruchomiona, nie może działać prawidłowo. Kod, który przekazuje testu weryfikacji jest określany jako bezpieczne. Możliwość weryfikowania kodu jako bezpieczny włącza środowisko uruchomieniowe języka wspólnego zapewnienie dużego poziomu izolacji jako granica procesu, na znacznie mniejszą wydajność kosztem.  
  
 Domeny aplikacji zawierają bardziej bezpieczne i elastyczne jednostki przetwarzania, używaną przez środowisko uruchomieniowe języka wspólnego do rozdzielenia aplikacji. Można uruchomić wiele domen aplikacji w ramach jednego procesu o tym samym poziomie izolacji, który będzie istnieć w osobnych procesach, ale bez ponoszenia dodatkowe obciążenie wykonywanie wywołań między procesami lub przełączanie między procesami. Możliwość uruchamiania wielu aplikacji w ramach jednego procesu znacznie zwiększa skalowalność serwera.  
  
 Izolowanie aplikacji są też ważne dla zabezpieczeń aplikacji. Na przykład można uruchamiać formantów z kilku aplikacji sieci Web w przeglądarce jednego procesu w taki sposób, że kontrolki nie dostęp do danych i zasobów siebie nawzajem.  
  
 Izolacja pochodzącymi z domeny aplikacji ma następujące zalety:  
  
-   Błędy w jednej aplikacji nie może mieć wpływ na inne aplikacje. Ponieważ bezpieczny kod nie może spowodować błędy pamięci, korzystanie z domeny aplikacji zapewnia, że kodu uruchamianego w jednej domenie nie mogą wpływać na inne aplikacje w procesie.  
  
-   Bez zatrzymywania cały proces można zatrzymać poszczególnych aplikacji. Używanie domeny aplikacji umożliwia zwolnienia z kodem uruchomionym w pojedynczej aplikacji.  
  
    > [!NOTE]
    >  Nie można zwolnić pojedyncze zestawy lub typów. Zakończenie domeny może być usunięty z pamięci.  
  
-   Kodu uruchamianego w jednej aplikacji nie może bezpośrednio kod dostępu lub zasobów z innej aplikacji. Środowisko uruchomieniowe języka wspólnego wymusza izolacja, zapobiegając bezpośrednich połączeń między obiektami w różnych domenach aplikacji. Obiekty, które przekazują między domenami są kopiowane lub dostęp do serwera proxy. Jeśli obiekt jest kopiowana, wywołania do obiektu jest lokalny. Oznacza to, że zarówno wywołującego i obiektu, do którego nastąpiło odwołanie znajdują się w tej samej domenie aplikacji. Jeśli obiekt jest dostępny za pośrednictwem serwera proxy, wywołanie do obiektu jest zdalny. W takim przypadku wywołującego i obiektu, do którego nastąpiło odwołanie znajdują się w różnych domenach aplikacji. Wywołania między domenami korzystać z tej samej infrastruktury zdalne wywołanie jako wywołań między dwoma procesami lub między dwoma komputerami. W efekcie metadanych dla obiektu, do którego nastąpiło odwołanie muszą być dostępne dla obu domen aplikacji, która umożliwia wywołanie metody są prawidłowo kompilacji JIT. Jeśli domena wywołujący nie ma dostępu do metadanych dla obiekt wywoływany, może się nie powieść kompilacji za pomocą wyjątku typu **System.IO.FileNotFound**. Zobacz [obiektów zdalnych](http://msdn.microsoft.com/en-us/515686e6-0a8d-42f7-8188-73abede57c58) więcej szczegółów. Mechanizm ustalania sposobu dostępnych obiektów między domenami jest określana przez obiekt. Aby uzyskać więcej informacji, zobacz <xref:System.MarshalByRefObject?displayProperty=nameWithType>.  
  
-   Zachowanie kodu jest ograniczone w zależności od aplikacji, w której jest uruchamiana. Innymi słowy domeny aplikacji zawiera ustawienia konfiguracji, takich jak zasady wersji aplikacji, lokalizację wszystkie zestawy zdalnego, który uzyskuje dostęp do oraz informacje o tym, gdzie można znaleźć zestawy, które są ładowane do domeny.  
  
-   Uprawnienia do kodu mogą być kontrolowane przez domeny aplikacji, w którym wykonywany jest kod.  
  
  
## <a name="application-domains-and-assemblies"></a>Domeny aplikacji i zestawy  
 W tym temacie opisano relacje między domenami aplikacji a zestawami. Aby można było wykonać kod zawarty w zestawie, należy go załadować do domeny aplikacji. Uruchomienie typowej aplikacji powoduje wczytanie kilku zestawów do domeny aplikacji.  
  
 Sposób ładowania zestawu określa, czy jego kod kompilowany dokładnie na czas (JIT) kod może być współużytkowany przez wiele domen aplikacji uczestniczących w procesie oraz czy zestaw można zwolnić z pamięci procesu.  
  
-   Jeśli zestaw został załadowany jako neutralny dla domen, wszystkie domeny aplikacji mające ten sam zestaw uprawnień zabezpieczeń mogą współużytkować ten sam kod skompilowany dokładnie na czas, co zmniejsza zapotrzebowanie aplikacji na pamięć. Jednak zestawu nigdy nie można zwolnić z pamięci procesu.  
  
-   Jeśli zestaw nie jest wczytywany jako neutralny dla domen, musi być kompilowany dokładnie na czas w każdej domenie aplikacji, do której jest ładowany. Zestaw można jednak zwolnić z pamięci procesu poprzez zwolnienie wszystkich domen aplikacji, w których został załadowany.  
  
 Host środowiska uruchomieniowego określa, czy podczas ładowania środowiska uruchomieniowego do procesu ma ładować zestawy jako neutralne dla domen. W przypadku zarządzanych aplikacji należy zastosować atrybut <xref:System.LoaderOptimizationAttribute> do metody punktu wejścia procesu oraz określić wartość z powiązanego wyliczenia <xref:System.LoaderOptimization>. Dla niezarządzanych aplikacji obsługujących środowisko uruchomieniowe języka wspólnego, określ odpowiednią flagę podczas wywoływania [CorBindToRuntimeEx — funkcja](../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) metody.  
  
 Istnieją trzy sposoby wczytywania zestawów jako neutralnych dla domen:  
  
-   <xref:System.LoaderOptimization> nie ładuje zestawów jako neutralnych dla domen, z wyjątkiem zestawu Mscorlib, który zawsze jest ładowany jako neutralny dla domen. To ustawienie jest wywoływana pojedynczej domeny, ponieważ jest ona używana najczęściej, gdy na hoście działa tylko jednej aplikacji w procesie.  
  
-   <xref:System.LoaderOptimization> wczytuje wszystkie zestawy jako neutralne dla domen. Tego ustawienia należy używać, gdy w procesie istnieje wiele domen aplikacji uruchamiających ten sam kod.  
  
-   <xref:System.LoaderOptimization> ładuje zestawy o silnych nazwach jako neutralne dla domen, jeśli zestawy i ich obiekty zależne zostały zainstalowane w globalnej pamięć podręcznej zestawów. Inne zestawy są wczytywane i kompilowane dokładnie na czas osobno dla każdej domeny aplikacji, do której zostały wczytane, dlatego można je zwolnić z pamięci procesu. Ustawienie należy stosować w przypadku, gdy w tym samym procesie działa więcej niż jedna aplikacja w tym samym procesie albo jeśli istnieje zbiór zestawów współużytkowanych przez wiele domen aplikacji oraz zestawów, które muszą być zwalniane z pamięci procesu.  
  
 Kod kompilowany dokładnie na czas nie może być współużytkowany przez zestawy ładowane w kontekście ich źródła pochodzenia za pomocą metody <xref:System.Reflection.Assembly.LoadFrom%2A> klasy <xref:System.Reflection.Assembly> ani ładowane z obrazów przy użyciu przeciążeń metody <xref:System.Reflection.Assembly.Load%2A>, która określa tablice bajtowe.  
  
 Zestawy, które zostały skompilowane do kodu natywnego za pomocą [Ngen.exe (Generator obrazu natywnego)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) można udostępniać między domenami aplikacji, jeśli są one ładowane neutralne dla domen są załadowane do procesu po raz pierwszy.  
  
 Kod zestawu kompilowany dokładnie na czas, który zawiera punkt wejścia aplikacji, jest udostępniany tylko wtedy, gdy można współużytkować jego wszystkie zależności.  
  
 Zestawy neutralny dla domen można kompilować dokładnie na czas więcej niż jeden raz. Na przykład gdy dwie domeny aplikacji mają różne zestawy uprawnień zabezpieczeń, nie mogą używać tego samego kodu kompilowanego dokładnie na czas. Jednak każdą kopię zestawu kompilowanego dokładnie na czas można udostępnić innym domenom aplikacji, które mają taki sam zestaw uprawnień.  
  
 Decydując, czy zestawy mają być wczytywane jako neutralne dla domen, należy wziąć pod uwagę kompromis między ograniczeniem użycia pamięci a innymi czynnikami wydajnościowymi.  
  
-   Zestawy neutralne dla domen mają wolniejszy dostęp do statycznych danych i metod, ponieważ zestawy trzeba izolować. Każda domena aplikacji uzyskująca dostęp do zestawu musi mieć oddzielną kopię danych statycznych, aby uniemożliwić odwołaniom w statycznych polach przekraczanie granic domeny. W rezultacie środowisko uruchomieniowe zawiera dodatkową logikę, która przekierowuje obiekt wywołujący do odpowiedniej kopii statycznych danych lub metody. Ta dodatkowa logika spowalnia wywołanie.  
  
-   Gdy zestaw jest wczytywany jako niezależny od domen, muszą być odnajdowane i ładowane jego wszystkie zależności, ponieważ zależność, której nie można wczytać jako neutralnej dla domen, uniemożliwia wczytanie w ten sposób całego zestawu.  
  
## <a name="application-domains-and-threads"></a>Domeny aplikacji i wątki  
 Domeny aplikacji jest izolowana zabezpieczeń, wersji, niezawodności i zwalnianie kodu zarządzanego. Wątek jest konstrukcja systemu operacyjnego używany przez środowisko uruchomieniowe języka wspólnego do wykonywania kodu. W czasie wykonywania cały kod zarządzany jest ładowany do domeny aplikacji i uruchomieniu przez jeden lub więcej wątków zarządzanych.  
  
 Nie jest sygnałowych domeny aplikacji i wątków. Kilka wątków może zostać uruchomiony w domenie, w jednej aplikacji w danym momencie i określonego wątku nie jest ograniczona do domeny pojedynczej aplikacji. Oznacza to wątki mogą przekraczać granice domeny aplikacji; nowego wątku nie jest tworzony dla każdej domeny aplikacji.  
  
 W dowolnym momencie każdego wątku wykonuje się w domenie aplikacji. Zero, jeden lub wiele wątków może wykonywać w dowolnej domenie danej aplikacji. Przechowuje informacje o czasie wykonywania wątków, które są uruchomione w domen aplikacji. Można znaleźć domeny, w którym wątek jest wykonywany w dowolnym momencie przez wywołanie metody <xref:System.Threading.Thread.GetDomain%2A?displayProperty=nameWithType> metody.  
  
### <a name="application-domains-and-cultures"></a>Domeny aplikacji i kultur  
 Kultura, która jest reprezentowana przez <xref:System.Globalization.CultureInfo> obiektu, jest skojarzona z wątków. Możesz uzyskać kultury, który jest skojarzony z wątkiem aktualnie wykonywane przy użyciu <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> właściwości oraz można pobrać lub ustawić kultury, który jest skojarzony z wątkiem aktualnie wykonywane przy użyciu <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> właściwości. Jeśli kultura, która jest skojarzona z wątku zostały jawnie skonfigurowane przy użyciu <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> właściwości, nadal być skojarzone z tym wątku, gdy wątek przecina granice domeny aplikacji. W przeciwnym razie kultury, który jest skojarzony z wątkiem w danym momencie jest określana przez wartość <xref:System.Globalization.CultureInfo.DefaultThreadCurrentCulture%2A?displayProperty=nameWithType> właściwości w domenie aplikacji, w którym jest wykonywany wątku:  
  
-   Jeśli wartość właściwości nie jest `null`, kultury, która jest zwracana przez właściwość jest skojarzony z wątkiem (i w związku z tym zwrócone przez <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> i <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> właściwości).  
  
-   Jeśli wartość właściwości jest `null`, bieżącego ustawienia kulturowego systemu jest skojarzony z wątkiem.  
  
## <a name="programming-with-application-domains"></a>Programowanie za pomocą domen aplikacji  
 Zazwyczaj domeny aplikacji tworzy się i wykonuje na nich operacje programowo za pomocą hostów środowiska uruchomieniowego. Czasami jednak z domenami aplikacji chcą pracować programy. Na przykład program może wczytywać składnik aplikacji do domeny, aby umożliwić zwolnienie domeny (i składnika) z pamięci bez konieczności zatrzymywania całej aplikacji.  
  
 <xref:System.AppDomain> Jest interfejs programistyczny do domen aplikacji. Zawiera ona metody tworzenia domen i zwalniania ich z pamięci, tworzenia wystąpień typów w domenach oraz rejestrowania w celu otrzymywania różnych powiadomień, np. o zwalnianiu domen aplikacji z pamięci. Poniższa tabela zawiera listę często używane <xref:System.AppDomain> metody.  
  
|Metoda klasy AppDomain|Opis|  
|----------------------|-----------------|  
|<xref:System.AppDomain.CreateDomain%2A>|Tworzenie nowej domeny aplikacji. Zaleca się używanie przeciążenia tej metody, które określa obiekt <xref:System.AppDomainSetup>. Jest to preferowany sposób konfigurowania właściwości nowej domeny, takich jak baza aplikacji czy główny katalog aplikacji, lokalizacja pliku konfiguracji domeny oraz ścieżka wyszukiwania, z której środowisko uruchomieniowe języka wspólnego ma ładować zestawy do domeny.|  
|<xref:System.AppDomain.ExecuteAssembly%2A>i<xref:System.AppDomain.ExecuteAssemblyByName%2A>|Wykonywanie zestawu w domenie aplikacji. To jest metoda wystąpienia, dlatego może służyć do wykonywania kodu w innej domenie aplikacji, do której prowadzi odwołanie.|  
|<xref:System.AppDomain.CreateInstanceAndUnwrap%2A>|Tworzenie wystąpienie wskazanego typu w domenie aplikacji oraz zwracanie danych serwera proxy. Ta metoda pozwala uniknąć wczytywania zestawu zawierającego utworzony typ do wywoływanego zestawu.|  
|<xref:System.AppDomain.Unload%2A>|Uporządkowanie wyłączanie domeny. Domena aplikacji zostanie zwolniona z pamięci dopiero wtedy, gdy wszystkie wątki uruchomione w domenie zostaną zatrzymane lub przestaną być obecne w domenie.|  
  
> [!NOTE]
>  Środowisko uruchomieniowe języka wspólnego nie obsługuje serializacji metod globalnych, dlatego delegaci nie mogą wykonywać globalnych metod w innych domenach aplikacji.  
  
 Dostęp do domen aplikacji zapewniają również niezarządzane interfejsy opisane w specyfikacji interfejsów hostujących środowiska uruchomieniowego języka wspólnego. Hosty środowiska uruchomieniowego mogą za pomocą interfejsów z niezarządzanego kodu tworzyć domeny aplikacji i uzyskiwać do nich dostęp wewnątrz procesu.  
  
## <a name="complusloaderoptimization-environment-variable"></a>COMPLUS_LoaderOptimization — Zmienna środowiskowa  
 Zmienna środowiskowa, która ustawia domyślną zasadę optymalizacji modułu ładującego aplikacji pliku wykonywalnego.  
  
### <a name="syntax"></a>Składnia  
  
```  
COMPLUS_LoaderOptimization = 1  
```  
  
### <a name="remarks"></a>Uwagi  
 Typowa aplikacja ładuje wiele zestawów do domeny aplikacji, kodu, które zawierają można było wykonać.  
  
 Sposób zestaw jest ładowany Określa, czy jego just-in-time (JIT) skompilowany kod może być współużytkowany przez wielu domen aplikacji w procesie.  
  
-   Jeśli zestaw jest załadowany neutralne dla domen, wszystkie domeny aplikacji, które współużytkują ten sam zestaw grant zabezpieczeń mogą współużytkować ten sam kod kompilacji JIT. Zmniejsza to ilość pamięci wymaganej przez aplikację.  
  
-   Jeśli zestaw nie jest załadowany, neutralne dla domen, musi być skompilowany JIT w każdej domenie aplikacji, w którym jest on załadowany i moduł ładujący nie mogą mieć wewnętrznych zasobów domen aplikacji.  
  
 Ustawiona na wartość 1, Flaga środowiska COMPLUS_LoaderOptimization wymusza host czasu wykonywania załadować wszystkie zestawy w sposób niezależny z systemem innym niż domena, znany jako SingleDomain. SingleDomain ładuje żadnych zestawów jako neutralne dla domen, z wyjątkiem Mscorlib, który jest ładowany zawsze neutralne dla domen. To ustawienie jest wywoływana pojedynczej domeny, ponieważ jest ona używana najczęściej, gdy na hoście działa tylko jednej aplikacji w procesie.  
  
> [!CAUTION]
>  Flaga środowiska COMPLUS_LoaderOptimization został zaprojektowany do użycia w diagnostyce i testowania scenariuszy. O flagi włączone może spowodować pociągnięcie spowolnienia i zwiększyć użycie pamięci.  
  
### <a name="code-example"></a>Przykład kodu  
 Aby wymusić wszystkie zestawy nie można załadować jako neutralne dla domen dla usługę usługi można osiągnąć przez dodanie `COMPLUS_LoaderOptimization=1` w kluczu HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\IISADMIN wartość ciągu wielokrotnego w środowisku.  
  
```  
Key = HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\IISADMIN  
Name = Environment  
Type = REG_MULTI_SZ  
Value (to append) = COMPLUS_LoaderOptimization=1  
```  
  
<a name="reference"></a>   
## <a name="reference"></a>Tematy pomocy  
 <xref:System.MarshalByRefObject?displayProperty=nameWithType>
