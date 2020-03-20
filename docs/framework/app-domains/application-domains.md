---
title: Domeny aplikacji
ms.date: 03/30/2017
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
ms.openlocfilehash: a5c9f4248e060d231941269f39cadbc7147ce27f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399876"
---
# <a name="application-domains"></a>Domeny aplikacji

Systemy operacyjne i środowiska uruchomieniowe zazwyczaj zapewniają pewną formę izolacji między aplikacjami. Na przykład system Windows używa procesów do izolowania aplikacji. Ta izolacja jest niezbędna, aby upewnić się, że kod uruchomiony w jednej aplikacji nie może niekorzystnie wpływać na inne, niepowiązane aplikacje.  
  
 Domeny aplikacji zapewniają granicę izolacji dla zabezpieczeń, niezawodności i przechowywania wersji oraz zwalniania zestawów. Domeny aplikacji są zazwyczaj tworzone przez hosty środowiska wykonawczego, które są odpowiedzialne za uruchamianie środowiska uruchomieniowego języka wspólnego przed uruchomieniem aplikacji.  
  
## <a name="the-benefits-of-isolating-applications"></a>Korzyści z izolowania aplikacji

 Historycznie granice procesu były używane do izolowania aplikacji uruchomionych na tym samym komputerze. Każda aplikacja jest ładowana do oddzielnego procesu, który izoluje aplikację od innych aplikacji uruchomionych na tym samym komputerze.  
  
 Aplikacje są izolowane, ponieważ adresy pamięci są względne procesu; wskaźnik pamięci przekazywane z jednego procesu do drugiego nie może być używany w żaden znaczący sposób w procesie docelowym. Ponadto nie można wykonywać bezpośrednich połączeń między dwoma procesami. Zamiast tego należy użyć serwerów proxy, które zapewniają poziom pośredni.  
  
 Kod zarządzany musi zostać przekazany przez proces weryfikacji, zanim będzie można go uruchomić (chyba że administrator udzielił uprawnień do pominięcia weryfikacji). Proces weryfikacji określa, czy kod może próbować uzyskać dostęp do nieprawidłowych adresów pamięci lub wykonać inną akcję, która może spowodować, że proces, w którym jest uruchomiony, nie działa poprawnie. Kod, który przechodzi test weryfikacyjny jest uważane za bezpieczne dla typu. Możliwość weryfikacji kodu jako bezpieczny dla typu umożliwia środowisko uruchomieniowe języka wspólnego, aby zapewnić jak wielki poziom izolacji jako granicy procesu, przy znacznie niższych kosztach wydajności.  
  
 Domeny aplikacji zapewniają bardziej bezpieczną i wszechstronną jednostkę przetwarzania, której środowisko wykonawcze języka wspólnego może używać do zapewnienia izolacji między aplikacjami. Można uruchomić kilka domen aplikacji w jednym procesie z tego samego poziomu izolacji, który istnieje w oddzielnych procesów, ale bez ponoszenia dodatkowych narzutów związanych z wykonywaniem wywołań między procesami lub przełączania między procesami. Możliwość uruchamiania wielu aplikacji w ramach jednego procesu znacznie zwiększa skalowalność serwera.  
  
 Izolowanie aplikacji jest również ważne dla zabezpieczeń aplikacji. Na przykład można uruchomić formanty z kilku aplikacji sieci Web w jednym procesie przeglądarki w taki sposób, że formanty nie mogą uzyskać dostępu do danych i zasobów innych.  
  
 Izolacja zapewniana przez domeny aplikacji ma następujące zalety:  
  
- Błędy w jednej aplikacji nie mogą mieć wpływu na inne aplikacje. Ponieważ kod bezpieczny dla typu nie może powodować błędów pamięci, przy użyciu domen aplikacji zapewnia, że kod uruchomiony w jednej domenie nie może mieć wpływu na inne aplikacje w procesie.  
  
- Poszczególne aplikacje można zatrzymać bez zatrzymywania całego procesu. Za pomocą domen aplikacji umożliwia zwolnienie kodu uruchomionego w jednej aplikacji.  
  
    > [!NOTE]
    > Nie można zwolnić poszczególnych zestawów lub typów. Można zwolnić tylko kompletną domenę.  
  
- Kod uruchomiony w jednej aplikacji nie może bezpośrednio uzyskać dostępu do kodu lub zasobów z innej aplikacji. Środowisko wykonawcze języka wspólnego wymusza tę izolację, zapobiegając bezpośrednim wywołaniom między obiektami w różnych domenach aplikacji. Obiekty, które przechodzą między domenami są kopiowane lub dostępne przez serwer proxy. Jeśli obiekt zostanie skopiowany, wywołanie obiektu jest lokalne. Oznacza to, że zarówno obiekt wywołujący, jak i obiekt, do którego się odwołuje, znajdują się w tej samej domenie aplikacji. Jeśli obiekt jest dostępny za pośrednictwem serwera proxy, wywołanie obiektu jest zdalne. W takim przypadku obiekt wywołujący i obiekt, do którego się odwołuje, znajdują się w różnych domenach aplikacji. Wywołania między domenami używają tej samej infrastruktury połączeń zdalnych, co wywołania między dwoma procesami lub między dwoma komputerami. W związku z tym metadane dla obiektu, do którego odwołuje się musi być dostępna dla obu domen aplikacji, aby umożliwić wywołanie metody być JIT-compiled poprawnie. Jeśli domena wywołująca nie ma dostępu do metadanych wywoływanego obiektu, kompilacja <xref:System.IO.FileNotFoundException>może zakończyć się niepowodzeniem z wyjątkiem typu . Aby uzyskać więcej informacji, zobacz [Obiekty zdalne](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100)). Mechanizm określania, jak obiekty mogą być dostępne w domenach jest określana przez obiekt. Aby uzyskać więcej informacji, zobacz <xref:System.MarshalByRefObject?displayProperty=nameWithType>.  
  
- Zachowanie kodu jest zakres przez aplikację, w której działa. Innymi słowy domena aplikacji zawiera ustawienia konfiguracji, takie jak zasady wersji aplikacji, lokalizacja wszystkich zestawów zdalnych, do których uzyskuje dostęp, oraz informacje o tym, gdzie można zlokalizować zestawy, które są ładowane do domeny.  
  
- Uprawnienia przyznane do kodu mogą być kontrolowane przez domenę aplikacji, w której kod jest uruchomiony.  
  
## <a name="application-domains-and-assemblies"></a>Domeny aplikacji i zestawy

 W tej sekcji opisano relację między domenami aplikacji i zestawami. Aby można było wykonać kod zawarty w zestawie, należy go załadować do domeny aplikacji. Uruchomienie typowej aplikacji powoduje wczytanie kilku zestawów do domeny aplikacji.  
  
 Sposób ładowania zestawu określa, czy jego kod kompilowany dokładnie na czas (JIT) kod może być współużytkowany przez wiele domen aplikacji uczestniczących w procesie oraz czy zestaw można zwolnić z pamięci procesu.  
  
- Jeśli zestaw został załadowany jako neutralny dla domen, wszystkie domeny aplikacji mające ten sam zestaw uprawnień zabezpieczeń mogą współużytkować ten sam kod skompilowany dokładnie na czas, co zmniejsza zapotrzebowanie aplikacji na pamięć. Jednak zestawu nigdy nie można zwolnić z pamięci procesu.  
  
- Jeśli zestaw nie jest wczytywany jako neutralny dla domen, musi być kompilowany dokładnie na czas w każdej domenie aplikacji, do której jest ładowany. Zestaw można jednak zwolnić z pamięci procesu poprzez zwolnienie wszystkich domen aplikacji, w których został załadowany.  
  
 Host środowiska uruchomieniowego określa, czy podczas ładowania środowiska uruchomieniowego do procesu ma ładować zestawy jako neutralne dla domen. W przypadku zarządzanych aplikacji należy zastosować atrybut <xref:System.LoaderOptimizationAttribute> do metody punktu wejścia procesu oraz określić wartość z powiązanego wyliczenia <xref:System.LoaderOptimization>. W przypadku aplikacji niezarządzanych, które hostują środowisko uruchomieniowe języka wspólnego, określ odpowiednią flagę podczas wywoływania metody [funkcji CorBindToRuntimeEx.](../unmanaged-api/hosting/corbindtoruntimeex-function.md)  
  
 Istnieją trzy sposoby wczytywania zestawów jako neutralnych dla domen:  
  
- <xref:System.LoaderOptimization.SingleDomain?displayProperty=nameWithType> nie ładuje zestawów jako neutralnych dla domen, z wyjątkiem zestawu Mscorlib, który zawsze jest ładowany jako neutralny dla domen. To ustawienie jest nazywane pojedynczą domeną, ponieważ jest często używane, gdy na hoście jest uruchomiona tylko jedna aplikacja w procesie.

- <xref:System.LoaderOptimization.MultiDomain?displayProperty=nameWithType> wczytuje wszystkie zestawy jako neutralne dla domen. Tego ustawienia należy używać, gdy w procesie istnieje wiele domen aplikacji uruchamiających ten sam kod.

- <xref:System.LoaderOptimization.MultiDomainHost?displayProperty=nameWithType> ładuje zestawy o silnych nazwach jako neutralne dla domen, jeśli zestawy i ich obiekty zależne zostały zainstalowane w globalnej pamięć podręcznej zestawów. Inne zestawy są wczytywane i kompilowane dokładnie na czas osobno dla każdej domeny aplikacji, do której zostały wczytane, dlatego można je zwolnić z pamięci procesu. Ustawienie należy stosować w przypadku, gdy w tym samym procesie działa więcej niż jedna aplikacja w tym samym procesie albo jeśli istnieje zbiór zestawów współużytkowanych przez wiele domen aplikacji oraz zestawów, które muszą być zwalniane z pamięci procesu.
  
 Kod kompilowany dokładnie na czas nie może być współużytkowany przez zestawy ładowane w kontekście ich źródła pochodzenia za pomocą metody <xref:System.Reflection.Assembly.LoadFrom%2A> klasy <xref:System.Reflection.Assembly> ani ładowane z obrazów przy użyciu przeciążeń metody <xref:System.Reflection.Assembly.Load%2A>, która określa tablice bajtowe.  
  
 Zestawy, które zostały skompilowane do kodu macierzystego przy użyciu [Ngen.exe (Generator natywnych obrazów)](../tools/ngen-exe-native-image-generator.md) mogą być współużytkowane między domenami aplikacji, jeśli są one ładowane domeny neutralne przy pierwszym załadowaniu do procesu.  
  
 Kod zestawu kompilowany dokładnie na czas, który zawiera punkt wejścia aplikacji, jest udostępniany tylko wtedy, gdy można współużytkować jego wszystkie zależności.  
  
 Zestawy neutralny dla domen można kompilować dokładnie na czas więcej niż jeden raz. Na przykład gdy dwie domeny aplikacji mają różne zestawy uprawnień zabezpieczeń, nie mogą używać tego samego kodu kompilowanego dokładnie na czas. Jednak każdą kopię zestawu kompilowanego dokładnie na czas można udostępnić innym domenom aplikacji, które mają taki sam zestaw uprawnień.  
  
 Decydując, czy zestawy mają być wczytywane jako neutralne dla domen, należy wziąć pod uwagę kompromis między ograniczeniem użycia pamięci a innymi czynnikami wydajnościowymi.  
  
- Zestawy neutralne dla domen mają wolniejszy dostęp do statycznych danych i metod, ponieważ zestawy trzeba izolować. Każda domena aplikacji uzyskująca dostęp do zestawu musi mieć oddzielną kopię danych statycznych, aby uniemożliwić odwołaniom w statycznych polach przekraczanie granic domeny. W rezultacie środowisko uruchomieniowe zawiera dodatkową logikę, która przekierowuje obiekt wywołujący do odpowiedniej kopii statycznych danych lub metody. Ta dodatkowa logika spowalnia wywołanie.  
  
- Gdy zestaw jest wczytywany jako niezależny od domen, muszą być odnajdowane i ładowane jego wszystkie zależności, ponieważ zależność, której nie można wczytać jako neutralnej dla domen, uniemożliwia wczytanie w ten sposób całego zestawu.  
  
## <a name="application-domains-and-threads"></a>Domeny i wątki aplikacji

 Domena aplikacji tworzy granicę izolacji dla zabezpieczeń, przechowywania wersji, niezawodności i zwalniania kodu zarządzanego. Wątek jest konstrukcją systemu operacyjnego używaną przez środowisko uruchomieniowe języka wspólnego do wykonywania kodu. W czasie wykonywania cały kod zarządzany jest ładowany do domeny aplikacji i jest uruchamiany przez jeden lub więcej wątków zarządzanych.  
  
 Nie ma korelacji jeden do jednego między domenami aplikacji i wątków. Kilka wątków można wykonać w jednej domenie aplikacji w danym momencie, a określony wątek nie jest ograniczona do domeny pojedynczej aplikacji. Oznacza to, że wątki mogą przekraczać granice domeny aplikacji; nowy wątek nie jest tworzony dla każdej domeny aplikacji.  
  
 W danym momencie każdy wątek jest wykonywany w domenie aplikacji. Zero, jeden lub wiele wątków może być wykonywanych w dowolnej domenie aplikacji. Środowisko wykonawcze śledzi, które wątki są uruchomione, w których domenach aplikacji. Można zlokalizować domenę, w której wątek jest <xref:System.Threading.Thread.GetDomain%2A?displayProperty=nameWithType> wykonywany w dowolnym momencie, wywołując metodę.

### <a name="application-domains-and-cultures"></a>Domeny i kultury aplikacji

 Kultura, która jest reprezentowana przez <xref:System.Globalization.CultureInfo> obiekt, jest skojarzona z wątkami. Można uzyskać kultury, która jest skojarzona z aktualnie <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> wykonywania wątku przy użyciu właściwości i można uzyskać lub ustawić kultury, <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> która jest skojarzona z aktualnie wykonywania wątku przy użyciu właściwości. Jeśli kultury, która jest skojarzona z wątku został <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> jawnie ustawiony przy użyciu właściwości, nadal jest skojarzony z tym wątku, gdy wątek przekracza granice domeny aplikacji. W przeciwnym razie kultury, która jest skojarzona z wątku w <xref:System.Globalization.CultureInfo.DefaultThreadCurrentCulture%2A?displayProperty=nameWithType> danym momencie jest określana przez wartość właściwości w domenie aplikacji, w którym wątek jest wykonywany:  
  
- Jeśli wartość właściwości nie `null`jest , kultury, która jest zwracana przez właściwość jest skojarzony z wątku (i dlatego zwracany przez <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> i <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> właściwości).  
  
- Jeśli wartość właściwości jest `null`, bieżąca kultura systemowa jest skojarzona z wątkiem.  
  
## <a name="programming-with-application-domains"></a>Programowanie z domenami aplikacji

 Zazwyczaj domeny aplikacji tworzy się i wykonuje na nich operacje programowo za pomocą hostów środowiska uruchomieniowego. Czasami jednak z domenami aplikacji chcą pracować programy. Na przykład program może wczytywać składnik aplikacji do domeny, aby umożliwić zwolnienie domeny (i składnika) z pamięci bez konieczności zatrzymywania całej aplikacji.  
  
 Jest <xref:System.AppDomain> to interfejs programowy do domen aplikacji. Zawiera ona metody tworzenia domen i zwalniania ich z pamięci, tworzenia wystąpień typów w domenach oraz rejestrowania w celu otrzymywania różnych powiadomień, np. o zwalnianiu domen aplikacji z pamięci. W poniższej tabeli <xref:System.AppDomain> wymieniono często używane metody.  
  
|Metoda klasy AppDomain|Opis|  
|----------------------|-----------------|  
|<xref:System.AppDomain.CreateDomain%2A>|Tworzenie nowej domeny aplikacji. Zaleca się używanie przeciążenia tej metody, które określa obiekt <xref:System.AppDomainSetup>. Jest to preferowany sposób konfigurowania właściwości nowej domeny, takich jak baza aplikacji czy główny katalog aplikacji, lokalizacja pliku konfiguracji domeny oraz ścieżka wyszukiwania, z której środowisko uruchomieniowe języka wspólnego ma ładować zestawy do domeny.|  
|<xref:System.AppDomain.ExecuteAssembly%2A> i <xref:System.AppDomain.ExecuteAssemblyByName%2A>|Wykonywanie zestawu w domenie aplikacji. To jest metoda wystąpienia, dlatego może służyć do wykonywania kodu w innej domenie aplikacji, do której prowadzi odwołanie.|  
|<xref:System.AppDomain.CreateInstanceAndUnwrap%2A>|Tworzenie wystąpienie wskazanego typu w domenie aplikacji oraz zwracanie danych serwera proxy. Ta metoda pozwala uniknąć wczytywania zestawu zawierającego utworzony typ do wywoływanego zestawu.|  
|<xref:System.AppDomain.Unload%2A>|Uporządkowanie wyłączanie domeny. Domena aplikacji zostanie zwolniona z pamięci dopiero wtedy, gdy wszystkie wątki uruchomione w domenie zostaną zatrzymane lub przestaną być obecne w domenie.|  
  
> [!NOTE]
> Środowisko uruchomieniowe języka wspólnego nie obsługuje serializacji metod globalnych, dlatego delegaci nie mogą wykonywać globalnych metod w innych domenach aplikacji.  
  
 Dostęp do domen aplikacji zapewniają również niezarządzane interfejsy opisane w specyfikacji interfejsów hostujących środowiska uruchomieniowego języka wspólnego. Hosty środowiska uruchomieniowego mogą za pomocą interfejsów z niezarządzanego kodu tworzyć domeny aplikacji i uzyskiwać do nich dostęp wewnątrz procesu.  
  
## <a name="the-complus_loaderoptimization-environment-variable"></a>Zmienna środowiskowa COMPLUS_LoaderOptimization

 Zmienna środowiskowa, która ustawia domyślną zasadę optymalizacji modułu ładującego aplikacji wykonywalnej.  
  
### <a name="syntax"></a>Składnia  
  
```env  
COMPLUS_LoaderOptimization = 1  
```  
  
### <a name="remarks"></a>Uwagi

 Typowa aplikacja ładuje kilka zestawów do domeny aplikacji, zanim kod, który zawierają mogą być wykonywane.  
  
 Sposób, w jaki zestaw jest ładowany określa, czy jego kod skompilowany just-in-time (JIT) może być współużytkowany przez wiele domen aplikacji w procesie.  
  
- Jeśli zestaw jest ładowany bez domeny, wszystkie domeny aplikacji, które współużytkują ten sam zestaw dotacji zabezpieczeń może współużytkować ten sam kod Skompilowany JIT. Zmniejsza to pamięć wymaganą przez aplikację.  
  
- Jeśli zestaw nie jest ładowany neutralny domeny, musi być Skompilowany JIT w każdej domenie aplikacji, w której jest ładowany i moduł ładujący nie może udostępniać zasobów wewnętrznych w domenach aplikacji.  
  
 Po ustawieniu na 1 flaga COMPLUS_LoaderOptimization środowiska wymusza hosta środowiska wykonawczego, aby załadować wszystkie zestawy w sposób nieo neutralny dla domeny znany jako SingleDomain. SingleDomain nie ładuje żadnych zestawów jako neutralnych dla domeny, z wyjątkiem mscorlib, który jest zawsze ładowany neutralny domeny. To ustawienie jest nazywane pojedynczą domeną, ponieważ jest często używane, gdy na hoście jest uruchomiona tylko jedna aplikacja w procesie.  
  
> [!CAUTION]
> Flaga COMPLUS_LoaderOptimization środowiska została zaprojektowana do użycia w scenariuszach diagnostycznych i testowych. Po włączeniu flagi może spowodować poważne spowolnienie i wzrost użycia pamięci.  
  
### <a name="code-example"></a>Przykładowy kod

 Aby wymusić, że wszystkie zestawy nie będą ładowane jako neutralne dla domeny `COMPLUS_LoaderOptimization=1` dla usługi IISADMIN, można uzyskać, dołączając do wartości wielostrunowej środowiska w kluczu HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\IISADMIN.  
  
```env  
Key = HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\IISADMIN  
Name = Environment  
Type = REG_MULTI_SZ  
Value (to append) = COMPLUS_LoaderOptimization=1  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.AppDomain?displayProperty=nameWithType>
- <xref:System.MarshalByRefObject?displayProperty=nameWithType>
- [Programowanie przy użyciu zestawów i domen aplikacji](index.md)
- [Używanie domeny aplikacji](use.md)
