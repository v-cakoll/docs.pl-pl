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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ddf8f52ab98d0188235d8c9f97293adced4bfe90
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44190036"
---
# <a name="application-domains"></a>Domeny aplikacji
Systemy operacyjne i środowiska uruchomieniowe zwykle zapewniają pewną formę izolacji między aplikacjami. Na przykład Windows używa procesów do izolowania aplikacji. Ta Izolacja jest niezbędna do zapewnienia, że kod uruchomiony w jednej aplikacji nie może niekorzystnie wpłynąć na inne, niezależne aplikacje.  
  
 Domeny aplikacji umożliwiają wyznaczanie granic izolacji w zakresie bezpieczeństwa, niezawodności i przechowywanie wersji i zwalniania zestawów. Domeny aplikacji są zwykle tworzone przez hosty środowiska uruchomieniowego, które są odpowiedzialne za ładowanie początkowe środowiska uruchomieniowego języka wspólnego, przed uruchomieniem aplikacji.  
  
 Tematy w tej sekcji dokumentacji wyjaśniają sposób używania domen aplikacji w celu uzyskania izolacji między zestawami.  
  
 Ten przegląd zawiera następujące sekcje:  
  
-   [Korzyści wynikające z izolowania aplikacji](#benefits)  
  
-   [Dokumentacja](#reference)  
  
<a name="benefits"></a>   
## <a name="the-benefits-of-isolating-applications"></a>Korzyści wynikające z izolowania aplikacji  
 Historycznie granice procesów były używane do izolowania aplikacji uruchomionych na tym samym komputerze. Każda aplikacja jest ładowana w oddzielnym procesie, który izoluje ją od innych aplikacji działających na tym samym komputerze.  
  
 Aplikacje są odizolowane, ponieważ adresy pamięci są względne dla procesu; wskaźnik pamięci przekazywany z jednego procesu do innego nie można używać w żaden znaczący sposób w procesie docelowym. Ponadto nie można wykonywać bezpośrednich wywołań między dwoma procesami. Zamiast tego należy użyć serwerów proxy, które zapewniają poziom pośrednictwa.  
  
 Kod zarządzany musi przechodzić przez proces weryfikacji przed uruchomieniem (chyba że administrator ma uprawnienia do pominięcia weryfikacji). Proces weryfikacji Określa, czy kod może podjąć próbę dostępu do nieprawidłowych adresów pamięci lub wykonać inne działania, które może spowodować, że proces, w której jest uruchomiony, aby mógł działać prawidłowo. Kod, który przejdzie test weryfikacji, jest określany jako bezpieczne. Możliwość sprawdzenia kodu jako bezpiecznego umożliwia środowiska uruchomieniowego języka wspólnego zapewniało tak wielki poziom izolacji, jak granica procesu, przy znacznie niższych kosztach.  
  
 Domen aplikacji zapewniają bardziej bezpieczne i elastyczne jednostki przetwarzania, środowisko uruchomieniowe języka wspólnego, można użyć do rozdzielenia aplikacji. Możesz uruchomić kilka domen aplikacji w pojedynczym procesie na tym samym poziomie izolacji, który istniałby w osobnych procesach, ale bez powodowania dodatkowego obciążenia związanego z wywołań między procesami lub przełączaniem między procesami. Możliwość uruchamiania wielu aplikacji w pojedynczym procesie znacznie zwiększa skalowalność serwera.  
  
 Izolowanie aplikacji jest również ważne dla bezpieczeństwa aplikacji. Na przykład można uruchomić formanty z kilku aplikacji sieci Web w jednym procesie przeglądarki w taki sposób, że formanty nie dostęp do danych i zasobów siebie nawzajem.  
  
 Izolacja świadczona przez domeny aplikacji ma następujące zalety:  
  
-   Błędy w jednej aplikacji nie może mieć wpływ na inne aplikacje. Ponieważ kod bezpiecznego typu nie może powodować błędów pamięci, korzystanie z domen aplikacji zapewnia, że kod uruchomiony w jednej domenie nie może wpływać na inne aplikacje w procesie.  
  
-   Poszczególne aplikacje mogą zostać zatrzymane bez zatrzymywania całego procesu. Używanie domen aplikacji pozwala zwolnić kod uruchomiony w jednej aplikacji.  
  
    > [!NOTE]
    >  Nie można rozładować poszczególnych zespołów lub typów. Tylko kompletna domena może być zwolniony.  
  
-   Kod uruchomiony w jednej aplikacji nie może mieć bezpośredniego dostępu do kodu lub zasobów z innej aplikacji. Środowisko uruchomieniowe języka wspólnego wymusza tę izolację poprzez zapobieganie bezpośrednim wywołaniom między obiektami w różnych domenach aplikacji. Obiekty, które przechodzą między domenami, są kopiowane lub używane przez serwery proxy. Jeśli obiekt jest kopiowany, wywołanie do obiektu jest lokalne. Oznacza to, że zarówno obiekt wywołujący i obiekt, do którego nastąpiło odwołanie znajdują się w tej samej domenie aplikacji. Jeśli obiekt jest dostępny za pośrednictwem serwera proxy, wywołanie do obiektu jest zdalne. W tym przypadku obiekt wywołujący i obiekt, do którego nastąpiło odwołanie znajdują się w różnych domenach aplikacji. Wywołania między domenami korzystać z tej samej infrastruktury zdalnego wywołania jako wywołania między dwoma procesami lub między dwoma komputerami. Jako takie metadane dla obiektu, do którego nastąpiło odwołanie, muszą być dostępne dla obu domen aplikacji, aby zezwolić na wywołania metody, które ma być kompilowany dokładnie na czas poprawnie. Jeśli domena wywołujący nie ma dostępu do metadanych dla wywoływanego obiektu, może się nie powieść kompilacja ze zgłoszeniem wyjątku typu **System.IO.FileNotFound**. Zobacz [obiekty zdalne](https://msdn.microsoft.com/library/515686e6-0a8d-42f7-8188-73abede57c58) Aby uzyskać więcej informacji. Mechanizm ustalania, jak obiekty są dostępne między domenami jest określany przez obiekt. Aby uzyskać więcej informacji, zobacz <xref:System.MarshalByRefObject?displayProperty=nameWithType>.  
  
-   Zachowanie kodu jest objęte zakresem aplikacji, w której jest uruchamiany. Innymi słowy domena aplikacji zawiera ustawienia konfiguracji, takie jak zasady wersji aplikacji, lokalizacja wszelkich zestawów zdalnych, do których uzyskuje dostęp, oraz informacje o tym, gdzie umieścić zestawy, które są ładowane do domeny.  
  
-   Uprawnienia udzielone do kodu mogą być kontrolowane przez domenę aplikacji, w którym wykonywany jest kod.  
  
  
## <a name="application-domains-and-assemblies"></a>Domeny aplikacji i zestawy  
 W tym temacie opisano relacje między domenami aplikacji a zestawami. Aby można było wykonać kod zawarty w zestawie, należy go załadować do domeny aplikacji. Uruchomienie typowej aplikacji powoduje wczytanie kilku zestawów do domeny aplikacji.  
  
 Sposób ładowania zestawu określa, czy jego kod kompilowany dokładnie na czas (JIT) kod może być współużytkowany przez wiele domen aplikacji uczestniczących w procesie oraz czy zestaw można zwolnić z pamięci procesu.  
  
-   Jeśli zestaw został załadowany jako neutralny dla domen, wszystkie domeny aplikacji mające ten sam zestaw uprawnień zabezpieczeń mogą współużytkować ten sam kod skompilowany dokładnie na czas, co zmniejsza zapotrzebowanie aplikacji na pamięć. Jednak zestawu nigdy nie można zwolnić z pamięci procesu.  
  
-   Jeśli zestaw nie jest wczytywany jako neutralny dla domen, musi być kompilowany dokładnie na czas w każdej domenie aplikacji, do której jest ładowany. Zestaw można jednak zwolnić z pamięci procesu poprzez zwolnienie wszystkich domen aplikacji, w których został załadowany.  
  
 Host środowiska uruchomieniowego określa, czy podczas ładowania środowiska uruchomieniowego do procesu ma ładować zestawy jako neutralne dla domen. W przypadku zarządzanych aplikacji należy zastosować atrybut <xref:System.LoaderOptimizationAttribute> do metody punktu wejścia procesu oraz określić wartość z powiązanego wyliczenia <xref:System.LoaderOptimization>. Dla niezarządzanych aplikacji, które hostują środowisko uruchomieniowe języka wspólnego, należy określić odpowiednią flagę podczas wywoływania [corbindtoruntimeex — funkcja](../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) metody.  
  
 Istnieją trzy sposoby wczytywania zestawów jako neutralnych dla domen:  
  
- <xref:System.LoaderOptimization.SingleDomain?displayProperty=nameWithType> nie ładuje zestawów jako neutralnych dla domen, z wyjątkiem zestawu Mscorlib, który zawsze jest ładowany jako neutralny dla domen. To ustawienie jest nazywane pojedynczą domeną, ponieważ jest często używane, gdy host jest uruchomiona tylko jedną aplikację w procesie.

- <xref:System.LoaderOptimization.MultiDomain?displayProperty=nameWithType> wczytuje wszystkie zestawy jako neutralne dla domen. Tego ustawienia należy używać, gdy w procesie istnieje wiele domen aplikacji uruchamiających ten sam kod.

- <xref:System.LoaderOptimization.MultiDomainHost?displayProperty=nameWithType> ładuje zestawy o silnych nazwach jako neutralne dla domen, jeśli zestawy i ich obiekty zależne zostały zainstalowane w globalnej pamięć podręcznej zestawów. Inne zestawy są wczytywane i kompilowane dokładnie na czas osobno dla każdej domeny aplikacji, do której zostały wczytane, dlatego można je zwolnić z pamięci procesu. Ustawienie należy stosować w przypadku, gdy w tym samym procesie działa więcej niż jedna aplikacja w tym samym procesie albo jeśli istnieje zbiór zestawów współużytkowanych przez wiele domen aplikacji oraz zestawów, które muszą być zwalniane z pamięci procesu.
  
 Kod kompilowany dokładnie na czas nie może być współużytkowany przez zestawy ładowane w kontekście ich źródła pochodzenia za pomocą metody <xref:System.Reflection.Assembly.LoadFrom%2A> klasy <xref:System.Reflection.Assembly> ani ładowane z obrazów przy użyciu przeciążeń metody <xref:System.Reflection.Assembly.Load%2A>, która określa tablice bajtowe.  
  
 Zestawy, które zostały skompilowane do kodu natywnego za pomocą [Ngen.exe (Generator obrazu natywnego)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) mogą być współużytkowane między domenami aplikacji, jeśli zostały wczytane jako neutralne dla domen są załadowane do procesu po raz pierwszy.  
  
 Kod zestawu kompilowany dokładnie na czas, który zawiera punkt wejścia aplikacji, jest udostępniany tylko wtedy, gdy można współużytkować jego wszystkie zależności.  
  
 Zestawy neutralny dla domen można kompilować dokładnie na czas więcej niż jeden raz. Na przykład gdy dwie domeny aplikacji mają różne zestawy uprawnień zabezpieczeń, nie mogą używać tego samego kodu kompilowanego dokładnie na czas. Jednak każdą kopię zestawu kompilowanego dokładnie na czas można udostępnić innym domenom aplikacji, które mają taki sam zestaw uprawnień.  
  
 Decydując, czy zestawy mają być wczytywane jako neutralne dla domen, należy wziąć pod uwagę kompromis między ograniczeniem użycia pamięci a innymi czynnikami wydajnościowymi.  
  
-   Zestawy neutralne dla domen mają wolniejszy dostęp do statycznych danych i metod, ponieważ zestawy trzeba izolować. Każda domena aplikacji uzyskująca dostęp do zestawu musi mieć oddzielną kopię danych statycznych, aby uniemożliwić odwołaniom w statycznych polach przekraczanie granic domeny. W rezultacie środowisko uruchomieniowe zawiera dodatkową logikę, która przekierowuje obiekt wywołujący do odpowiedniej kopii statycznych danych lub metody. Ta dodatkowa logika spowalnia wywołanie.  
  
-   Gdy zestaw jest wczytywany jako niezależny od domen, muszą być odnajdowane i ładowane jego wszystkie zależności, ponieważ zależność, której nie można wczytać jako neutralnej dla domen, uniemożliwia wczytanie w ten sposób całego zestawu.  
  
## <a name="application-domains-and-threads"></a>Domeny aplikacji i wątki  
 Domeny aplikacji tworzą izolującą granicę dla zabezpieczeń, obsługi wersji, niezawodności i zwalnianie kodu zarządzanego. Wątek jest konstrukcji systemu operacyjnego używany przez środowisko uruchomieniowe języka wspólnego do wykonywania kodu. W czasie wykonywania wszystkich zarządzanych kodów jest ładowany do domeny aplikacji i jest uruchamiane przez jeden lub więcej wątków zarządzanych.  
  
 Nie jest sygnałowych domeny aplikacji i wątków. Wiele wątków można wykonać w domenie pojedynczej aplikacji w dowolnym momencie i określonego wątku nie ogranicza się do domeny pojedynczej aplikacji. Oznacza to, że wątki mogą przekraczać granice domeny aplikacji; nowy wątek nie jest tworzony dla każdej domeny aplikacji.  
  
 W dowolnym momencie każdy wątek wykonuje w domenie aplikacji. Zero, jeden lub wiele wątków może wykonywać w dowolnej domenie danej aplikacji. Przechowuje informacje o czasie wykonywania, wątki, które są uruchomione w domenach aplikacji, które. Można znaleźć domeny, w którym wykonywany jest wątek, w dowolnym momencie przez wywołanie metody <xref:System.Threading.Thread.GetDomain%2A?displayProperty=nameWithType> metody.  
  
### <a name="application-domains-and-cultures"></a>Domeny aplikacji i kultur  
 Kultury, która jest reprezentowana przez <xref:System.Globalization.CultureInfo> obiektu, jest skojarzona z wątków. Możesz uzyskać kultury, który jest skojarzony z aktualnie wykonywany wątek przy użyciu <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> właściwości, na które można uzyskać lub ustawić kulturę, który jest skojarzony z aktualnie wykonywany wątek przy użyciu <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> właściwości. Jeśli jawnie ustawiono kultury, który jest skojarzony z wątkiem, za pomocą <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> właściwości go w dalszym ciągu być skojarzone z tym wątkiem, gdy wątek przekracza granice domen aplikacji. W przeciwnym razie kultury, który jest skojarzony z wątkiem w danym momencie jest określana przez wartość <xref:System.Globalization.CultureInfo.DefaultThreadCurrentCulture%2A?displayProperty=nameWithType> właściwości w domenie aplikacji, w którym wykonywany jest wątek:  
  
-   Jeśli wartość właściwości nie jest `null`, kultury, który jest zwracany przez właściwość jest skojarzony z wątkiem (i w związku z tym zwrócone przez <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> i <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> właściwości).  
  
-   Jeśli wartość właściwości jest `null`, bieżącą kulturą systemu jest skojarzony z wątkiem.  
  
## <a name="programming-with-application-domains"></a>Programowanie za pomocą domen aplikacji  
 Zazwyczaj domeny aplikacji tworzy się i wykonuje na nich operacje programowo za pomocą hostów środowiska uruchomieniowego. Czasami jednak z domenami aplikacji chcą pracować programy. Na przykład program może wczytywać składnik aplikacji do domeny, aby umożliwić zwolnienie domeny (i składnika) z pamięci bez konieczności zatrzymywania całej aplikacji.  
  
 <xref:System.AppDomain> Jest interfejsem programistycznym domen aplikacji. Zawiera ona metody tworzenia domen i zwalniania ich z pamięci, tworzenia wystąpień typów w domenach oraz rejestrowania w celu otrzymywania różnych powiadomień, np. o zwalnianiu domen aplikacji z pamięci. Poniższa tabela zawiera listę najczęściej używanych <xref:System.AppDomain> metody.  
  
|Metoda klasy AppDomain|Opis|  
|----------------------|-----------------|  
|<xref:System.AppDomain.CreateDomain%2A>|Tworzenie nowej domeny aplikacji. Zaleca się używanie przeciążenia tej metody, które określa obiekt <xref:System.AppDomainSetup>. Jest to preferowany sposób konfigurowania właściwości nowej domeny, takich jak baza aplikacji czy główny katalog aplikacji, lokalizacja pliku konfiguracji domeny oraz ścieżka wyszukiwania, z której środowisko uruchomieniowe języka wspólnego ma ładować zestawy do domeny.|  
|<xref:System.AppDomain.ExecuteAssembly%2A> i <xref:System.AppDomain.ExecuteAssemblyByName%2A>|Wykonywanie zestawu w domenie aplikacji. To jest metoda wystąpienia, dlatego może służyć do wykonywania kodu w innej domenie aplikacji, do której prowadzi odwołanie.|  
|<xref:System.AppDomain.CreateInstanceAndUnwrap%2A>|Tworzenie wystąpienie wskazanego typu w domenie aplikacji oraz zwracanie danych serwera proxy. Ta metoda pozwala uniknąć wczytywania zestawu zawierającego utworzony typ do wywoływanego zestawu.|  
|<xref:System.AppDomain.Unload%2A>|Uporządkowanie wyłączanie domeny. Domena aplikacji zostanie zwolniona z pamięci dopiero wtedy, gdy wszystkie wątki uruchomione w domenie zostaną zatrzymane lub przestaną być obecne w domenie.|  
  
> [!NOTE]
>  Środowisko uruchomieniowe języka wspólnego nie obsługuje serializacji metod globalnych, dlatego delegaci nie mogą wykonywać globalnych metod w innych domenach aplikacji.  
  
 Dostęp do domen aplikacji zapewniają również niezarządzane interfejsy opisane w specyfikacji interfejsów hostujących środowiska uruchomieniowego języka wspólnego. Hosty środowiska uruchomieniowego mogą za pomocą interfejsów z niezarządzanego kodu tworzyć domeny aplikacji i uzyskiwać do nich dostęp wewnątrz procesu.  
  
## <a name="complusloaderoptimization-environment-variable"></a>COMPLUS_LoaderOptimization — Zmienna środowiskowa  
 Zmienna środowiskowa, który ustawia domyślną zasadę optymalizacji programu ładującego pliku wykonywalnego aplikacji.  
  
### <a name="syntax"></a>Składnia  
  
```  
COMPLUS_LoaderOptimization = 1  
```  
  
### <a name="remarks"></a>Uwagi  
 Typowa aplikacja ładuje kilka zestawów do domeny aplikacji przed wykonaniem kodu, które zawierają.  
  
 Sposób zestaw jest ładowany Określa, czy kod skompilowany jego just-in-time (JIT) może być współużytkowany przez wiele domen aplikacji w procesie.  
  
-   Jeśli zestaw jest załadowany jako neutralny, wszystkie domeny aplikacji, które współużytkują ten sam przyznany zestaw zabezpieczeń mogą udostępniać tego samego kodu kompilowanego dokładnie na czas. Zmniejsza to ilość pamięci wymaganej przez aplikację.  
  
-   Jeśli zestaw nie jest załadowany jako neutralny, musi być kompilowany dokładnie na czas w każdej domenie aplikacji, w której jest załadowany, a moduł ładujący nie może współużytkować zasobów wewnętrznych w domenach aplikacji.  
  
 Ustawiona na wartość 1, Flaga środowiska COMPLUS_LoaderOptimization wymusza od hosta czasu wykonywania ładowanie wszystkich zestawów w sposób nie-niezależne od domeny, znany również jako SingleDomain. SingleDomain nie ładuje zespołów jako domena Neutralna, z wyjątkiem Mscorlib, który jest zawsze ładowany jako neutralny. To ustawienie jest nazywane pojedynczą domeną, ponieważ jest często używane, gdy host jest uruchomiona tylko jedną aplikację w procesie.  
  
> [!CAUTION]
>  Flaga środowiska COMPLUS_LoaderOptimization została zaprojektowana do użycia w diagnostyce oraz testowania scenariuszy. Posiadanie włączonej flagi może spowodować poważne spowolnienie i wzrost użycia pamięci.  
  
### <a name="code-example"></a>Przykład kodu  
 Aby wymusić wszystkie zestawy nie można załadować jako niezależne od domeny dla usługi IISADMIN usługi można osiągnąć, dodając `COMPLUS_LoaderOptimization=1` do wartości wielociągu środowiska w kluczu HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\IISADMIN.  
  
```  
Key = HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\IISADMIN  
Name = Environment  
Type = REG_MULTI_SZ  
Value (to append) = COMPLUS_LoaderOptimization=1  
```  
  
<a name="reference"></a>   
## <a name="reference"></a>Tematy pomocy  
 <xref:System.MarshalByRefObject?displayProperty=nameWithType>
