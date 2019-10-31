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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119975"
---
# <a name="application-domains"></a>Domeny aplikacji

Systemy operacyjne i środowiska uruchomieniowe zwykle zapewniają pewną postać izolacji między aplikacjami. Na przykład system Windows używa procesów do izolowania aplikacji. Ta izolacja jest niezbędna do zapewnienia, że kod uruchomiony w jednej aplikacji nie może mieć negatywnego wpływu na inne niepowiązane aplikacje.  
  
 Domeny aplikacji zapewniają granicę izolacji w zakresie zabezpieczeń, niezawodności i przechowywania wersji oraz do zwalniania zestawów. Domeny aplikacji są zwykle tworzone przez hosty środowiska uruchomieniowego, które są odpowiedzialne za uruchamianie środowiska uruchomieniowego języka wspólnego przed uruchomieniem aplikacji.  
  
## <a name="the-benefits-of-isolating-applications"></a>Zalety izolowania aplikacji

 W przeszłości, granice procesów zostały użyte do izolowania aplikacji uruchomionych na tym samym komputerze. Każda aplikacja jest ładowana do oddzielnego procesu, który izoluje aplikację od innych aplikacji uruchomionych na tym samym komputerze.  
  
 Aplikacje są izolowane, ponieważ adresy pamięci są względne dla procesu; wskaźnika pamięci przesyłanego z jednego procesu do innego nie można użyć w sposób znaczący w procesie docelowym. Ponadto nie można wykonywać bezpośrednich wywołań między dwoma procesami. Zamiast tego należy użyć serwerów proxy, które zapewniają poziom pośredni.  
  
 Kod zarządzany musi być przeszedł przez proces weryfikacji, aby można go było uruchomić (chyba że administrator udzielił uprawnień do pominięcia weryfikacji). Proces weryfikacji określa, czy kod może próbować uzyskać dostęp do nieprawidłowych adresów pamięci lub wykonać inną akcję, która może spowodować, że proces, w którym działa, nie działa prawidłowo. Kod, który przekazuje test weryfikacyjny, jest nazywany bezpiecznym typem. Możliwość weryfikowania kodu jako bezpiecznego pozwala zapewnić, że środowisko uruchomieniowe języka wspólnego zapewnia jak doskonały poziom izolacji w ramach granicy procesu, z znacznie niższym kosztem wydajności.  
  
 Domeny aplikacji zapewniają bardziej bezpieczną i uniwersalną jednostkę przetwarzania, którą środowisko uruchomieniowe języka wspólnego może wykorzystać w celu zapewnienia izolacji między aplikacjami. W pojedynczym procesie można uruchomić kilka domen aplikacji z takim samym poziomem izolacji, który będzie istniał w oddzielnych procesach, ale bez ponoszenia dodatkowych kosztów związanych z wykonywaniem wywołań między procesami lub przełączaniem między procesami. Możliwość uruchamiania wielu aplikacji w ramach jednego procesu znacznie zwiększa skalowalność serwera.  
  
 Izolowanie aplikacji jest również ważne w przypadku zabezpieczeń aplikacji. Można na przykład uruchomić kontrolki z kilku aplikacji sieci Web w ramach pojedynczego procesu przeglądarki w taki sposób, że kontrolki nie będą mogły uzyskać dostępu do danych i zasobów.  
  
 Izolacja zapewniana przez domeny aplikacji ma następujące zalety:  
  
- Błędy w jednej aplikacji nie mogą mieć wpływu na inne aplikacje. Ponieważ kod bezpieczny dla typu nie może spowodować błędów pamięci, korzystanie z domen aplikacji zapewnia, że kod uruchomiony w jednej domenie nie może wpływać na inne aplikacje w procesie.  
  
- Pojedyncze aplikacje można zatrzymać bez zatrzymywania całego procesu. Używanie domen aplikacji umożliwia zwolnienie kodu działającego w pojedynczej aplikacji.  
  
    > [!NOTE]
    > Nie można zwolnić pojedynczych zestawów lub typów. Można zwolnić tylko pełną domenę.  
  
- Kod uruchomiony w jednej aplikacji nie może bezpośrednio uzyskać dostępu do kodu lub zasobów z innej aplikacji. Środowisko uruchomieniowe języka wspólnego wymusza tę izolację, uniemożliwiając bezpośrednie wywołania między obiektami w różnych domenach aplikacji. Obiekty, które przechodzą między domenami, są kopiowane lub dostępne przez serwer proxy. Jeśli obiekt jest kopiowany, wywołanie do obiektu jest lokalne. Oznacza to, że zarówno obiekt wywołujący, jak i obiekt, do którego występuje odwołanie, znajdują się w tej samej domenie aplikacji. Jeśli dostęp do obiektu odbywa się za pomocą serwera proxy, wywołanie do obiektu jest zdalne. W takim przypadku obiekt wywołujący i obiekt, do którego się odwołuje się, znajdują się w różnych domenach aplikacji. Wywołania między domenami używają tej samej infrastruktury wywołania zdalnego, co wywołania między dwoma procesami lub między dwoma maszynami. W związku z tym metadane obiektu, do którego odwołuje się odwołanie, muszą być dostępne dla obu domen aplikacji, aby umożliwić wywołanie metody w prawidłowym skompilowaniu JIT. Jeśli domena wywołująca nie ma dostępu do metadanych dla wywoływanego obiektu, kompilacja może zakończyć się niepowodzeniem z wyjątkiem typu <xref:System.IO.FileNotFoundException>. Aby uzyskać więcej informacji, zobacz [obiekty zdalne](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100)). Mechanizm określania sposobu, w jaki obiekty są dostępne między domenami, jest określany przez obiekt. Aby uzyskać więcej informacji, zobacz <xref:System.MarshalByRefObject?displayProperty=nameWithType>.  
  
- Zachowanie kodu jest ograniczone przez aplikację, w której jest uruchomiona. Innymi słowy domena aplikacji udostępnia ustawienia konfiguracji, takie jak zasady wersji aplikacji, lokalizacja dowolnych zestawów zdalnych, do których uzyskuje dostęp, oraz informacje o lokalizacji, w których mają znajdować się zestawy, które są ładowane do domeny.  
  
- Uprawnienia przyznane do kodu mogą być kontrolowane przez domenę aplikacji, w której uruchomiono kod.  
  
## <a name="application-domains-and-assemblies"></a>Domeny aplikacji i zestawy

 W tej sekcji opisano relację między domenami i zestawami aplikacji. Aby można było wykonać kod zawarty w zestawie, należy go załadować do domeny aplikacji. Uruchomienie typowej aplikacji powoduje wczytanie kilku zestawów do domeny aplikacji.  
  
 Sposób ładowania zestawu określa, czy jego kod kompilowany dokładnie na czas (JIT) kod może być współużytkowany przez wiele domen aplikacji uczestniczących w procesie oraz czy zestaw można zwolnić z pamięci procesu.  
  
- Jeśli zestaw został załadowany jako neutralny dla domen, wszystkie domeny aplikacji mające ten sam zestaw uprawnień zabezpieczeń mogą współużytkować ten sam kod skompilowany dokładnie na czas, co zmniejsza zapotrzebowanie aplikacji na pamięć. Jednak zestawu nigdy nie można zwolnić z pamięci procesu.  
  
- Jeśli zestaw nie jest wczytywany jako neutralny dla domen, musi być kompilowany dokładnie na czas w każdej domenie aplikacji, do której jest ładowany. Zestaw można jednak zwolnić z pamięci procesu poprzez zwolnienie wszystkich domen aplikacji, w których został załadowany.  
  
 Host środowiska uruchomieniowego określa, czy podczas ładowania środowiska uruchomieniowego do procesu ma ładować zestawy jako neutralne dla domen. W przypadku zarządzanych aplikacji należy zastosować atrybut <xref:System.LoaderOptimizationAttribute> do metody punktu wejścia procesu oraz określić wartość z powiązanego wyliczenia <xref:System.LoaderOptimization>. W przypadku niezarządzanych aplikacji, które obsługują środowisko uruchomieniowe języka wspólnego, należy określić odpowiednią flagę w przypadku wywołania metody [funkcji CorBindToRuntimeEx](../unmanaged-api/hosting/corbindtoruntimeex-function.md) .  
  
 Istnieją trzy sposoby wczytywania zestawów jako neutralnych dla domen:  
  
- <xref:System.LoaderOptimization.SingleDomain?displayProperty=nameWithType> nie ładuje zestawów jako neutralnych dla domen, z wyjątkiem zestawu Mscorlib, który zawsze jest ładowany jako neutralny dla domen. To ustawienie nosi nazwę pojedynczej domeny, ponieważ jest często używane, gdy host uruchamia tylko jedną aplikację w procesie.

- <xref:System.LoaderOptimization.MultiDomain?displayProperty=nameWithType> wczytuje wszystkie zestawy jako neutralne dla domen. Tego ustawienia należy używać, gdy w procesie istnieje wiele domen aplikacji uruchamiających ten sam kod.

- <xref:System.LoaderOptimization.MultiDomainHost?displayProperty=nameWithType> ładuje zestawy o silnych nazwach jako neutralne dla domen, jeśli zestawy i ich obiekty zależne zostały zainstalowane w globalnej pamięć podręcznej zestawów. Inne zestawy są wczytywane i kompilowane dokładnie na czas osobno dla każdej domeny aplikacji, do której zostały wczytane, dlatego można je zwolnić z pamięci procesu. Ustawienie należy stosować w przypadku, gdy w tym samym procesie działa więcej niż jedna aplikacja w tym samym procesie albo jeśli istnieje zbiór zestawów współużytkowanych przez wiele domen aplikacji oraz zestawów, które muszą być zwalniane z pamięci procesu.
  
 Kod kompilowany dokładnie na czas nie może być współużytkowany przez zestawy ładowane w kontekście ich źródła pochodzenia za pomocą metody <xref:System.Reflection.Assembly.LoadFrom%2A> klasy <xref:System.Reflection.Assembly> ani ładowane z obrazów przy użyciu przeciążeń metody <xref:System.Reflection.Assembly.Load%2A>, która określa tablice bajtowe.  
  
 Zestawy, które zostały skompilowane do kodu natywnego przy użyciu programu [Ngen. exe (Generator obrazu natywnego)](../tools/ngen-exe-native-image-generator.md) , mogą być współużytkowane między domenami aplikacji, jeśli są załadowane jako niezależne od domeny podczas pierwszego ładowania do procesu.  
  
 Kod zestawu kompilowany dokładnie na czas, który zawiera punkt wejścia aplikacji, jest udostępniany tylko wtedy, gdy można współużytkować jego wszystkie zależności.  
  
 Zestawy neutralny dla domen można kompilować dokładnie na czas więcej niż jeden raz. Na przykład gdy dwie domeny aplikacji mają różne zestawy uprawnień zabezpieczeń, nie mogą używać tego samego kodu kompilowanego dokładnie na czas. Jednak każdą kopię zestawu kompilowanego dokładnie na czas można udostępnić innym domenom aplikacji, które mają taki sam zestaw uprawnień.  
  
 Decydując, czy zestawy mają być wczytywane jako neutralne dla domen, należy wziąć pod uwagę kompromis między ograniczeniem użycia pamięci a innymi czynnikami wydajnościowymi.  
  
- Zestawy neutralne dla domen mają wolniejszy dostęp do statycznych danych i metod, ponieważ zestawy trzeba izolować. Każda domena aplikacji uzyskująca dostęp do zestawu musi mieć oddzielną kopię danych statycznych, aby uniemożliwić odwołaniom w statycznych polach przekraczanie granic domeny. W rezultacie środowisko uruchomieniowe zawiera dodatkową logikę, która przekierowuje obiekt wywołujący do odpowiedniej kopii statycznych danych lub metody. Ta dodatkowa logika spowalnia wywołanie.  
  
- Gdy zestaw jest wczytywany jako niezależny od domen, muszą być odnajdowane i ładowane jego wszystkie zależności, ponieważ zależność, której nie można wczytać jako neutralnej dla domen, uniemożliwia wczytanie w ten sposób całego zestawu.  
  
## <a name="application-domains-and-threads"></a>Domeny aplikacji i wątki

 Domena aplikacji tworzy granicę izolacji w celu zapewnienia bezpieczeństwa, przechowywania wersji, niezawodności i zwalniania kodu zarządzanego. Wątek to konstrukcja systemu operacyjnego używana przez środowisko uruchomieniowe języka wspólnego do wykonywania kodu. W czasie wykonywania cały kod zarządzany jest ładowany do domeny aplikacji i uruchamiany przez co najmniej jeden zarządzany wątek.  
  
 Między domenami i wątkami aplikacji nie istnieje korelacja typu jeden-do-jednego. Kilka wątków można wykonać w jednej domenie aplikacji w dowolnym momencie, a określony wątek nie jest ograniczany do pojedynczej domeny aplikacji. Oznacza to, że wątki są bezpłatne, aby przekroczyć granice domeny aplikacji; dla każdej domeny aplikacji nie jest tworzony nowy wątek.  
  
 W danym momencie każdy wątek jest wykonywany w domenie aplikacji. W każdej domenie aplikacji może być wykonywane zero, jeden lub wiele wątków. Środowisko uruchomieniowe śledzi, które wątki działają w ramach których domen aplikacji. Można zlokalizować domenę, w której wykonywany jest wątek w dowolnym momencie, wywołując metodę <xref:System.Threading.Thread.GetDomain%2A?displayProperty=nameWithType>.

### <a name="application-domains-and-cultures"></a>Domeny aplikacji i kultury

 Kultura, która jest reprezentowana przez obiekt <xref:System.Globalization.CultureInfo>, jest skojarzona z wątkami. Można uzyskać kulturę, która jest skojarzona z aktualnie wykonywanym wątkiem za pomocą właściwości <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> i można pobrać lub ustawić kulturę skojarzoną z aktualnie wykonywanym wątkiem przy użyciu właściwości <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType>. Jeśli kultura skojarzona z wątkiem została jawnie ustawiona przy użyciu właściwości <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType>, będzie ona nadal skojarzona z tym wątkiem, gdy wątek przekroczy granice domeny aplikacji. W przeciwnym razie kultura, która jest skojarzona z wątkiem w danym momencie jest określona przez wartość właściwości <xref:System.Globalization.CultureInfo.DefaultThreadCurrentCulture%2A?displayProperty=nameWithType> w domenie aplikacji, w której jest wykonywany wątek:  
  
- Jeśli wartość właściwości nie jest `null`, kultura zwracana przez właściwość jest skojarzona z wątkiem (i w związku z tym jest zwracana przez właściwości <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> i <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>).  
  
- Jeśli wartość właściwości jest `null`, bieżąca kultura systemu jest skojarzona z wątkiem.  
  
## <a name="programming-with-application-domains"></a>Programowanie przy użyciu domen aplikacji

 Zazwyczaj domeny aplikacji tworzy się i wykonuje na nich operacje programowo za pomocą hostów środowiska uruchomieniowego. Czasami jednak z domenami aplikacji chcą pracować programy. Na przykład program może wczytywać składnik aplikacji do domeny, aby umożliwić zwolnienie domeny (i składnika) z pamięci bez konieczności zatrzymywania całej aplikacji.  
  
 <xref:System.AppDomain> jest interfejs programistyczny dla domen aplikacji. Zawiera ona metody tworzenia domen i zwalniania ich z pamięci, tworzenia wystąpień typów w domenach oraz rejestrowania w celu otrzymywania różnych powiadomień, np. o zwalnianiu domen aplikacji z pamięci. W poniższej tabeli wymieniono często używane metody <xref:System.AppDomain>.  
  
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

 Zmienna środowiskowa, która ustawia domyślne zasady optymalizacji modułu ładującego aplikacji wykonywalnej.  
  
### <a name="syntax"></a>Składnia  
  
```env  
COMPLUS_LoaderOptimization = 1  
```  
  
### <a name="remarks"></a>Uwagi

 Typowa aplikacja ładuje kilka zestawów do domeny aplikacji przed wykonaniem zawartego w nim kodu.  
  
 Sposób ładowania zestawu określa, czy jego kod skompilowany just-in-Time (JIT) może być współużytkowany przez wiele domen aplikacji w procesie.  
  
- Jeśli zestaw jest ładowany jako neutralny dla domen, wszystkie domeny aplikacji, które mają ten sam zestaw uprawnień zabezpieczeń, mogą współużytkować ten sam kod skompilowany przez JIT. Zmniejsza to ilość pamięci wymaganej przez aplikację.  
  
- Jeśli zestaw nie jest ładowany jako niezależny od domeny, musi być skompilowany w trybie JIT w każdej domenie aplikacji, w której jest załadowany, i moduł ładujący nie może udostępniać zasobów wewnętrznych między domenami aplikacji.  
  
 W przypadku ustawienia wartości 1 Flaga środowiska COMPLUS_LoaderOptimization wymusza załadowanie przez hosta środowiska uruchomieniowego wszystkich zestawów w sposób nieneutralny dla domeny, znany jako SingleDomain. SingleDomain nie ładuje żadnych zestawów jako neutralnych dla domen, z wyjątkiem mscorlib, który jest zawsze ładowany jako neutralny dla domeny. To ustawienie nosi nazwę pojedynczej domeny, ponieważ jest często używane, gdy host uruchamia tylko jedną aplikację w procesie.  
  
> [!CAUTION]
> Flaga środowiska COMPLUS_LoaderOptimization została zaprojektowana tak, aby była używana w scenariuszach diagnostycznych i testowych. Włączenie flagi może spowodować poważne spowolnienie i zwiększenie użycia pamięci.  
  
### <a name="code-example"></a>Przykład kodu

 Aby wymusić, że wszystkie zestawy nie mają zostać załadowane jako niezależne od domeny dla usługi IISADMIN można osiągnąć przez dołączenie `COMPLUS_LoaderOptimization=1` do wartości wielociągowej środowiska w kluczu HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\IISADMIN.  
  
```env  
Key = HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\IISADMIN  
Name = Environment  
Type = REG_MULTI_SZ  
Value (to append) = COMPLUS_LoaderOptimization=1  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.AppDomain?displayProperty=nameWithType>
- <xref:System.MarshalByRefObject?displayProperty=nameWithType>
- [Programowanie przy użyciu domen i zestawów aplikacji](index.md)
- [Używanie domen aplikacji](use.md)
