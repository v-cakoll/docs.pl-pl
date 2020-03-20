---
title: Wykonywanie równoczesne w programie .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution
ms.assetid: 649f1342-766b-49e6-a90d-5b019a751e11
ms.openlocfilehash: e965702943149d3ed34be39bb2923ad52dcf90ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181642"
---
# <a name="side-by-side-execution-in-the-net-framework"></a>Wykonywanie równoczesne w programie .NET Framework

Wykonywanie równoczesne stwarza możliwość uruchamiania wielu wersji aplikacji lub składnika na jednym komputerze. Można mieć wiele wersji środowiska uruchomieniowego języka wspólnego i wiele wersji aplikacji oraz składników, które używają wersji środowiska uruchomieniowego na jednym komputerze w tym samym czasie.  
  
Na poniższej ilustracji pokazano kilka aplikacji używających dwóch różnych wersji środowiska uruchomieniowego na jednym komputerze. Aplikacje A, B i C używają środowiska uruchomieniowego w wersji 1.0, podczas gdy aplikacja D używa środowiska uruchomieniowego w wersji 1.1.  
  
![Wykonywanie obok siebie różnych wersji środowiska uruchomieniowego,](./media/side-by-side-execution/side-by-side-runtime-execution.gif)  
  
Program .NET Framework składa się ze środowiska uruchomieniowego języka wspólnego i kolekcji zestawów zawierających typy interfejsu API. Wersje środowiska uruchomieniowego i zestawów programu .NET Framework są określane oddzielnie. Na przykład wersja 4.0 środowiska uruchomieniowego jest w rzeczywistości wersją 4.0.319, natomiast wersja 1.0 zestawów programu .NET Framework jest w rzeczywistości wersją 1.0.3300.0.  
  
Na poniższej ilustracji pokazano kilka aplikacji używających dwóch różnych wersji składnika na jednym komputerze. Aplikacje A i B używają wersji 1.0 składnika, podczas gdy aplikacja C używa wersji 2.0 tego samego składnika.  
  
![Diagram, który pokazuje wykonanie składnika obok siebie.](./media/side-by-side-execution/side-by-side-component-execution.gif)  
  
Wykonywanie równoczesne daje większą kontrolę nad tym, z którymi wersjami składnika jest powiązana aplikacja, a także większą kontrolę nad tym, których wersji środowiska uruchomieniowego używa aplikacja.  
  
## <a name="benefits-of-side-by-side-execution"></a>Korzyści z wykonywania równoczesnego  

Przed wprowadzeniem systemu Windows XP i programu .NET Framework występowały konflikty bibliotek DLL, ponieważ aplikacje nie mogły rozróżnić niezgodnych wersji tego samego kodu. Informacje o typach zawarte w bibliotece DLL były powiązane tylko z nazwą pliku. Aplikacja nie miała żadnej możliwość określenia, czy typy zawarte w bibliotece DLL były tymi samymi typami, z użyciem których aplikacja została skompilowana. W rezultacie nowa wersja składnika mogła zastąpić starszą wersję i spowodować przerwanie działania aplikacji.  
  
Wykonywanie równoczesne i program .NET Framework dostarczają następujące funkcje służące do eliminowania konfliktów bibliotek DLL:  
  
- Zestawy o silnych nazwach.  
  
     Funkcja wykonywania równoczesnego używa zestawów o silnych nazwach w celu powiązania informacji o typie z określoną wersją zestawu. Zapobiega to powiązaniu aplikacji lub składnika z nieprawidłową wersją zestawu. Zestawy o silnych nazwach umożliwiają również istnienie wielu wersji pliku na jednym komputerze i używanie ich przez aplikacje. Aby uzyskać więcej informacji, zobacz [Zestawy o silnych nazwach](../../standard/assembly/strong-named.md).  
  
- Magazyn kodu rozpoznający wersje.  
  
     Program .NET Framework dostarcza magazyn kodu rozpoznający wersje w globalnej pamięci podręcznej zestawów. Globalna pamięć podręczna zestawów to pamięć podręczna kodu dla całego komputera, która znajduje się na każdym komputerze z zainstalowanym programem .NET Framework. Zestawy są przechowywane na podstawie wersji, kultury i informacjach o wydawcy, a ponadto jest obsługiwanych wiele wersji składników i aplikacji. Aby uzyskać więcej informacji, zobacz [Globalna pamięć podręczna zestawów](../app-domains/gac.md).  
  
- Izolacja.  
  
     Używając programu .NET Framework, można tworzyć aplikacje i składniki, które są wykonywane w izolacji. Izolacja jest istotnym składnikiem funkcji wykonywania równoczesnego. Działanie izolacji obejmuje rozpoznawanie używanych zasobów oraz współużytkowanie zasobów przez wiele wersji aplikacji lub składnika. Izolacja obejmuje również przechowywanie plików w sposób specyficzny dla wersji. Aby uzyskać więcej informacji na temat izolacji, zobacz [Wskazówki dotyczące tworzenia składników do wykonywania obok siebie](guidelines-for-creating-components-for-side-by-side-execution.md).  
  
## <a name="version-compatibility"></a>Zgodność wersji  

Wersje 1.0 i 1.1 programu .NET Framework są zaprojektowane tak, aby zachować zgodność ze sobą. Aplikacja skompilowana przy użyciu programu .NET Framework w wersji 1.0 powinna działać w wersji 1.1, a aplikacja skompilowana przy użyciu programu .NET Framework w wersji 1.1 powinna działać w wersji 1.0. Należy jednak zauważyć, że funkcje interfejsu API dodane w wersji 1.1 programu .NET Framework nie będą działać w wersji 1.0 programu .NET Framework. Aplikacje utworzone przy użyciu wersji 2.0 będzie można uruchomić tylko w wersji 2.0. Aplikacje utworzone w wersji 2.0 nie będą działać w wersji 1.1 lub wcześniejszej.  
  
Wersje programu .NET Framework są traktowane jako pojedyncze jednostki składające się ze środowiska uruchomieniowego i skojarzonych zestawów programu .NET Framework (koncepcja określana jako ujednolicenie zestawów). Można przekierować powiązanie zestawu, tak aby dołączyć inne wersje zestawów .NET Framework, ale zastępowanie domyślnego powiązania zestawu może być ryzykowne, przez co należy je starannie przetestować przed wdrożeniem.  
  
## <a name="locating-runtime-version-information"></a>Lokalizowanie informacji o wersji środowiska uruchomieniowego  

Informacje o tym, z którą wersją środowiska wykonawczego została skompilowana aplikacja lub składnik i które wersje środowiska wykonawczego, które aplikacja wymaga do uruchomienia, są przechowywane w dwóch lokalizacjach. Podczas kompilowania aplikacji lub składnika informacje o wersji środowiska wykonawczego używanej do skompilowania są przechowywane w zarządzanym pliku wykonywalnym. Informacje o wersjach środowiska wykonawczego, które wymaga aplikacja lub składnik, są przechowywane w pliku konfiguracji aplikacji.  
  
### <a name="runtime-version-information-in-the-managed-executable"></a>Informacje o wersji środowiska wykonawczego w zarządzanym pliku wykonywalnym  

Przenośny nagłówek pliku wykonywalnego (PE) każdej zarządzanej aplikacji i składnika zawiera informacje o wersji środowiska uruchomieniowego, z którym została zbudowana. Środowisko wykonawcze języka wspólnego używa tych informacji do określenia najbardziej prawdopodobnej wersji środowiska wykonawczego, którego aplikacja musi uruchomić.  
  
### <a name="runtime-version-information-in-the-application-configuration-file"></a>Informacje o wersji środowiska uruchomieniowego w pliku konfiguracji aplikacji  

Oprócz informacji w nagłówku pliku pe, aplikacja może być wdrożona z plikiem konfiguracji aplikacji, który zawiera informacje o wersji środowiska wykonawczego. Plik konfiguracji aplikacji jest plikiem opartym na języku XML, który jest tworzony przez dewelopera aplikacji i dostarczany z aplikacją. [ \<WymaganeRuntime> Element](../configure-apps/file-schema/startup/requiredruntime-element.md) [ \<sekcji> uruchamiania](../configure-apps/file-schema/startup/startup-element.md), jeśli jest obecny w tym pliku, określa, które wersje środowiska wykonawczego i które wersje składnika obsługuje aplikacja. Można również użyć tego pliku w testowaniu, aby przetestować zgodność aplikacji z różnymi wersjami środowiska wykonawczego.  
  
Niezarządzany kod, w tym aplikacje COM i COM+, może mieć pliki konfiguracji aplikacji używane przez środowisko wykonawcze do interakcji z kodem zarządzanym. Plik konfiguracji aplikacji ma wpływ na każdy kod zarządzany aktywowany za pośrednictwem usługi COM. Plik można określić, które wersje środowiska wykonawczego obsługuje, a także przekierowania zestawu. Domyślnie aplikacje współdziałania COM wywołujące kod zarządzany używają najnowszej wersji środowiska wykonawczego zainstalowanego na komputerze.  
  
 Aby uzyskać więcej informacji na temat plików konfiguracyjnych aplikacji, zobacz [Konfigurowanie aplikacji](../configure-apps/index.md).  
  
## <a name="determining-which-version-of-the-runtime-to-load"></a>Określanie wersji środowiska uruchomieniowego do załadowania  

Środowisko wykonawcze języka wspólnego używa następujących informacji, aby określić, która wersja środowiska wykonawczego do załadowania dla aplikacji:  
  
- Dostępne wersje środowiska wykonawczego.  
  
- Wersje środowiska wykonawczego, które obsługuje aplikacja.  
  
### <a name="supported-runtime-versions"></a>Obsługiwane wersje środowiska wykonawczego  

Środowisko wykonawcze używa pliku konfiguracji aplikacji i przenośnego nagłówka pliku wykonywalnego (PE), aby określić, która wersja środowiska wykonawczego jest dostępna dla aplikacji. Jeśli nie ma pliku konfiguracji aplikacji, środowisko wykonawcze ładuje wersję środowiska uruchomieniowego określoną w nagłówku pliku PE aplikacji, jeśli ta wersja jest dostępna.  
  
Jeśli plik konfiguracji aplikacji jest obecny, środowisko wykonawcze określa odpowiednią wersję środowiska uruchomieniowego do załadowania na podstawie wyników następującego procesu:  
  
1. Środowisko wykonawcze sprawdza [ \<obsługiwaneRuntime> Element](../configure-apps/file-schema/startup/supportedruntime-element.md) element w pliku konfiguracji aplikacji. Jeśli jedna lub więcej obsługiwanych wersji środowiska uruchomieniowego określonych w ** \<obsługiwanymruntime>** element są obecne, środowisko wykonawcze ładuje wersję środowiska uruchomieniowego określoną przez pierwszy ** \<obsługiwanyruntime>** element. Jeśli ta wersja nie jest dostępna, środowisko wykonawcze sprawdza następny ** \<obsługiwanyruntime>** element i próbuje załadować określoną wersję środowiska uruchomieniowego. Jeśli ta wersja środowiska uruchomieniowego nie jest dostępna, badane są kolejne ** \<obsługiwaneruntime>** elementy. Jeśli żadna z obsługiwanych wersji środowiska uruchomieniowego nie jest dostępna, środowisko wykonawcze nie może załadować wersji środowiska wykonawczego i wyświetli komunikat do użytkownika (zobacz krok 3).  
  
2. Środowisko wykonawcze odczytuje nagłówek pliku PE pliku wykonywalnego aplikacji. Jeśli dostępna jest wersja środowiska wykonawczego określona przez nagłówek pliku PE, środowisko wykonawcze ładuje tę wersję. Jeśli określona wersja środowiska wykonawczego nie jest dostępna, środowisko wykonawcze wyszukuje wersję środowiska uruchomieniowego określoną przez firmę Microsoft jako zgodną z wersją środowiska wykonawczego w nagłówku pe. Jeśli ta wersja nie zostanie znaleziona, proces jest kontynuowany w kroku 3.  
  
3. Środowisko wykonawcze wyświetla komunikat informujący, że wersja środowiska wykonawczego obsługiwana przez aplikację jest niedostępna. Środowisko wykonawcze nie jest ładowane.  
  
    > [!NOTE]
    > Wyświetlanie tego komunikatu można pominąć przy użyciu wartości NoGuiFromShim pod kluczem\\rejestru HKLM\Software\Microsoft . NETFramework lub przy użyciu zmiennej środowiskowej COMPLUS_NoGuiFromShim. Na przykład można pominąć komunikat dla aplikacji, które zazwyczaj nie wchodzą w interakcje z użytkownikiem, takich jak instalacje nienadzorowane lub usługi systemu Windows. Gdy ten komunikat jest wyłączony, środowisko wykonawcze zapisuje komunikat do dziennika zdarzeń.  Ustaw wartość rejestru NoGuiFromShim na 1, aby pominąć ten komunikat dla wszystkich aplikacji na komputerze. Alternatywnie ustaw zmienną środowiskową COMPLUS_NoGuiFromShim na 1, aby pominąć komunikat dla aplikacji uruchomionych w określonym kontekście użytkownika.  
  
> [!NOTE]
> Po załadowaniu wersji środowiska uruchomieniowego przekierowania powiązania zestawu można określić, że inna wersja pojedynczego zestawu .NET Framework być ładowane. Te przekierowania powiązania mają wpływ tylko na określony zestaw, który jest przekierowywane.  
  
## <a name="partially-qualified-assembly-names-and-side-by-side-execution"></a>Częściowo kwalifikowane nazwy zestawów a wykonywanie równoczesne  

Ponieważ są one potencjalnym źródłem problemów side-by-side, częściowo kwalifikowane odwołania do zestawu mogą być używane tylko do powiązania z zestawami w katalogu aplikacji. Należy unikać częściowo kwalifikowanych odwołań do zestawu w kodzie.  
  
Aby ograniczyć częściowo kwalifikowane odwołania do zestawu w kodzie, można użyć [ \<elementu qualifyAssembly>](../configure-apps/file-schema/runtime/qualifyassembly-element.md) w pliku konfiguracji aplikacji, aby w pełni zakwalifikować częściowo kwalifikowane odwołania do zestawu, które występują w kodzie. Użyj ** \<elementu qualifyAssembly>,** aby określić tylko pola, które nie zostały ustawione w odwołaniu częściowym. Tożsamość zestawu wymieniona w **atrybutie fullName** musi zawierać wszystkie informacje potrzebne do pełnej kwalifikacji nazwy zestawu: nazwa zestawu, klucz publiczny, kultura i wersja.  
  
 W poniższym przykładzie pokazano wpis pliku konfiguracji `myAssembly`aplikacji, aby w pełni zakwalifikować zestaw o nazwie .  
  
```xml  
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
<qualifyAssembly partialName="myAssembly"
fullName="myAssembly,  
      version=1.0.0.0,
publicKeyToken=...,
      culture=neutral"/>
</assemblyBinding>
```  
  
 Za każdym razem, gdy `myAssembly`odwołuje się instrukcja obciążenia zestawu, te ustawienia `myAssembly` pliku konfiguracji powodują, że środowisko uruchomieniowe automatycznie tłumaczy częściowo kwalifikowane odwołanie do w pełni kwalifikowanego odwołania. Na przykład Assembly.Load("myAssembly") staje się Assembly.Load("myAssembly, version=1.0.0.0, publicKeyToken=..., culture=neutral").  
  
> [!NOTE]
> Można użyć **LoadWithPartialName** metody, aby pominąć ograniczenie środowiska uruchomieniowego języka wspólnego, który zabrania częściowo odwołuje się zestawy z ładowanych z globalnej pamięci podręcznej zestawu. Ta metoda powinna być używana tylko w scenariuszach komunikacji zdalnej, ponieważ może łatwo powodować problemy w wykonaniu side-by-side.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Porady: włączanie i wyłączanie automatycznego przekierowania powiązań](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)|Opis sposobu tworzenia powiązania aplikacji z określoną wersją zestawu.|  
|[Konfigurowanie przekierowywania powiązań zestawów](configuring-assembly-binding-redirection.md)|Opis sposobu przekierowywania odwołań do powiązań zestawów do określonej wersji zestawów programu .NET Framework.|  
|[Wykonywanie równoczesne i wewnątrzprocesowe](in-process-side-by-side-execution.md)|Omówienie sposobu używania aktywacji hosta środowiska uruchomieniowego wewnątrzprocesowego wykonywania równoczesnego w celu uruchamiania wielu wersji środowiska CLR w pojedynczym procesie.|  
|[Zestawy w środowisku .NET](../../standard/assembly/index.md)|Omówienie koncepcyjne zestawów.|  
|[Domeny aplikacji](../app-domains/application-domains.md)|Omówienie koncepcyjne domen aplikacji.|  
  
## <a name="reference"></a>Dokumentacja  

[\<supportedRuntime> Element](../configure-apps/file-schema/startup/supportedruntime-element.md)
