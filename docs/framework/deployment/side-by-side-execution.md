---
title: Wykonywanie równoczesne w programie .NET Framework
description: Eksploruj Wykonywanie równoczesne w programie .NET. Wykonywanie równoczesne umożliwia uruchamianie wielu wersji aplikacji lub składnika na tym samym komputerze.
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution
ms.assetid: 649f1342-766b-49e6-a90d-5b019a751e11
ms.openlocfilehash: 6cd6fb73b27957fdea85cd9a92bf2aa3bafda1ce
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619406"
---
# <a name="side-by-side-execution-in-the-net-framework"></a>Wykonywanie równoczesne w programie .NET Framework

Wykonywanie równoczesne stwarza możliwość uruchamiania wielu wersji aplikacji lub składnika na jednym komputerze. Można mieć wiele wersji środowiska uruchomieniowego języka wspólnego i wiele wersji aplikacji oraz składników, które używają wersji środowiska uruchomieniowego na jednym komputerze w tym samym czasie.  
  
Na poniższej ilustracji pokazano kilka aplikacji używających dwóch różnych wersji środowiska uruchomieniowego na jednym komputerze. Aplikacje A, B i C używają środowiska uruchomieniowego w wersji 1.0, podczas gdy aplikacja D używa środowiska uruchomieniowego w wersji 1.1.  
  
![Wykonywanie równoczesne różnych wersji środowiska uruchomieniowego,](./media/side-by-side-execution/side-by-side-runtime-execution.gif)  
  
Program .NET Framework składa się ze środowiska uruchomieniowego języka wspólnego i kolekcji zestawów zawierających typy interfejsu API. Wersje środowiska uruchomieniowego i zestawów programu .NET Framework są określane oddzielnie. Na przykład wersja 4.0 środowiska uruchomieniowego jest w rzeczywistości wersją 4.0.319, natomiast wersja 1.0 zestawów programu .NET Framework jest w rzeczywistości wersją 1.0.3300.0.  
  
Na poniższej ilustracji pokazano kilka aplikacji używających dwóch różnych wersji składnika na jednym komputerze. Aplikacje A i B używają wersji 1.0 składnika, podczas gdy aplikacja C używa wersji 2.0 tego samego składnika.  
  
![Diagram, który pokazuje równoczesne wykonywanie składnika.](./media/side-by-side-execution/side-by-side-component-execution.gif)  
  
Wykonywanie równoczesne daje większą kontrolę nad tym, z którymi wersjami składnika jest powiązana aplikacja, a także większą kontrolę nad tym, których wersji środowiska uruchomieniowego używa aplikacja.  
  
## <a name="benefits-of-side-by-side-execution"></a>Korzyści z wykonywania równoczesnego  

Przed wprowadzeniem systemu Windows XP i programu .NET Framework występowały konflikty bibliotek DLL, ponieważ aplikacje nie mogły rozróżnić niezgodnych wersji tego samego kodu. Informacje o typach zawarte w bibliotece DLL były powiązane tylko z nazwą pliku. Aplikacja nie miała żadnej możliwość określenia, czy typy zawarte w bibliotece DLL były tymi samymi typami, z użyciem których aplikacja została skompilowana. W rezultacie nowa wersja składnika mogła zastąpić starszą wersję i spowodować przerwanie działania aplikacji.  
  
Wykonywanie równoczesne i program .NET Framework dostarczają następujące funkcje służące do eliminowania konfliktów bibliotek DLL:  
  
- Zestawy o silnych nazwach.  
  
     Funkcja wykonywania równoczesnego używa zestawów o silnych nazwach w celu powiązania informacji o typie z określoną wersją zestawu. Zapobiega to powiązaniu aplikacji lub składnika z nieprawidłową wersją zestawu. Zestawy o silnych nazwach umożliwiają również istnienie wielu wersji pliku na jednym komputerze i używanie ich przez aplikacje. Aby uzyskać więcej informacji, zobacz [zestawy o silnych nazwach](../../standard/assembly/strong-named.md).  
  
- Magazyn kodu rozpoznający wersje.  
  
     Program .NET Framework dostarcza magazyn kodu rozpoznający wersje w globalnej pamięci podręcznej zestawów. Globalna pamięć podręczna zestawów to pamięć podręczna kodu dla całego komputera, która znajduje się na każdym komputerze z zainstalowanym programem .NET Framework. Zestawy są przechowywane na podstawie wersji, kultury i informacjach o wydawcy, a ponadto jest obsługiwanych wiele wersji składników i aplikacji. Aby uzyskać więcej informacji, zobacz [globalna pamięć podręczna zestawów](../app-domains/gac.md).  
  
- Izolacja.  
  
     Używając programu .NET Framework, można tworzyć aplikacje i składniki, które są wykonywane w izolacji. Izolacja jest istotnym składnikiem funkcji wykonywania równoczesnego. Działanie izolacji obejmuje rozpoznawanie używanych zasobów oraz współużytkowanie zasobów przez wiele wersji aplikacji lub składnika. Izolacja obejmuje również przechowywanie plików w sposób specyficzny dla wersji. Aby uzyskać więcej informacji na temat izolacji, zobacz [wytyczne dotyczące tworzenia składników do wykonywania równoczesnego](guidelines-for-creating-components-for-side-by-side-execution.md).  
  
## <a name="version-compatibility"></a>Zgodność wersji  

Wersje 1.0 i 1.1 programu .NET Framework są zaprojektowane tak, aby zachować zgodność ze sobą. Aplikacja skompilowana przy użyciu programu .NET Framework w wersji 1.0 powinna działać w wersji 1.1, a aplikacja skompilowana przy użyciu programu .NET Framework w wersji 1.1 powinna działać w wersji 1.0. Należy jednak zauważyć, że funkcje interfejsu API dodane w wersji 1.1 programu .NET Framework nie będą działać w wersji 1.0 programu .NET Framework. Aplikacje utworzone przy użyciu wersji 2.0 będzie można uruchomić tylko w wersji 2.0. Aplikacje utworzone w wersji 2.0 nie będą działać w wersji 1.1 lub wcześniejszej.  
  
Wersje programu .NET Framework są traktowane jako pojedyncze jednostki składające się ze środowiska uruchomieniowego i skojarzonych zestawów programu .NET Framework (koncepcja określana jako ujednolicenie zestawów). Można przekierować powiązanie zestawu, tak aby dołączyć inne wersje zestawów .NET Framework, ale zastępowanie domyślnego powiązania zestawu może być ryzykowne, przez co należy je starannie przetestować przed wdrożeniem.  
  
## <a name="locating-runtime-version-information"></a>Lokalizowanie informacji o wersji środowiska uruchomieniowego  

Informacje o wersji środowiska uruchomieniowego, z którą aplikacja lub składnik został skompilowany i które wersje środowiska uruchomieniowego wymagane przez aplikację do uruchomienia są przechowywane w dwóch lokalizacjach. Po skompilowaniu aplikacji lub składnika informacje o wersji środowiska uruchomieniowego używanej do skompilowania są przechowywane w zarządzanym pliku wykonywalnym. Informacje o wersjach środowiska uruchomieniowego wymagane przez aplikację lub składnik są przechowywane w pliku konfiguracyjnym aplikacji.  
  
### <a name="runtime-version-information-in-the-managed-executable"></a>Informacje o wersji środowiska uruchomieniowego w zarządzanym pliku wykonywalnym  

Przenośny plik wykonywalny (PE) dla każdej zarządzanej aplikacji i składnika zawiera informacje o wersji środowiska uruchomieniowego, z którą została skompilowana. Środowisko uruchomieniowe języka wspólnego używa tych informacji do określenia najbardziej prawdopodobną wersję środowiska uruchomieniowego, która musi zostać uruchomiona przez aplikację.  
  
### <a name="runtime-version-information-in-the-application-configuration-file"></a>Informacje o wersji środowiska uruchomieniowego w pliku konfiguracyjnym aplikacji  

Oprócz informacji w nagłówku pliku PE można wdrożyć aplikację z plikiem konfiguracji aplikacji, który zawiera informacje o wersji środowiska uruchomieniowego. Plik konfiguracji aplikacji jest plikiem opartym na formacie XML, który jest tworzony przez dewelopera aplikacji i dostarczany z aplikacją. [ \<requiredRuntime> Element](../configure-apps/file-schema/startup/requiredruntime-element.md) [ \<startup> sekcji](../configure-apps/file-schema/startup/startup-element.md), jeśli znajduje się w tym pliku, określa wersje środowiska uruchomieniowego i wersje składnika obsługiwane przez aplikację. Możesz również użyć tego pliku do testowania, aby przetestować zgodność aplikacji z różnymi wersjami środowiska uruchomieniowego.  
  
Kod niezarządzany, w tym aplikacje COM i COM+, może mieć pliki konfiguracyjne aplikacji używane przez środowisko uruchomieniowe do współdziałania z kodem zarządzanym. Plik konfiguracji aplikacji ma wpływ na dowolny zarządzany kod, który można aktywować za pomocą modelu COM. Plik może określać, które wersje środowiska uruchomieniowego obsługuje, a także przekierowania zestawu. Domyślnie aplikacje międzyoperacyjności modelu COM wywołujące kod zarządzany używają najnowszej wersji środowiska uruchomieniowego zainstalowanej na komputerze.  
  
 Aby uzyskać więcej informacji na temat plików konfiguracji aplikacji, zobacz [Konfigurowanie aplikacji](../configure-apps/index.md).  
  
## <a name="determining-which-version-of-the-runtime-to-load"></a>Określanie wersji środowiska uruchomieniowego do załadowania  

Środowisko uruchomieniowe języka wspólnego używa poniższych informacji w celu określenia wersji środowiska uruchomieniowego do załadowania dla aplikacji:  
  
- Dostępne wersje środowiska uruchomieniowego.  
  
- Wersje środowiska uruchomieniowego obsługiwane przez aplikację.  
  
### <a name="supported-runtime-versions"></a>Obsługiwane wersje środowiska uruchomieniowego  

Środowisko uruchomieniowe używa pliku konfiguracji aplikacji oraz nagłówka pliku przenośnego wykonywalnego (PE) do określenia wersji środowiska uruchomieniowego obsługiwanego przez aplikację. Jeśli plik konfiguracji aplikacji nie jest obecny, środowisko uruchomieniowe ładuje wersję środowiska uruchomieniowego określoną w nagłówku pliku PE aplikacji, jeśli ta wersja jest dostępna.  
  
Jeśli istnieje plik konfiguracji aplikacji, środowisko uruchomieniowe określa odpowiednią wersję środowiska uruchomieniowego do załadowania na podstawie wyników następującego procesu:  
  
1. Środowisko uruchomieniowe bada element [ \<supportedRuntime> elementu](../configure-apps/file-schema/startup/supportedruntime-element.md) w pliku konfiguracyjnym aplikacji. Jeśli co najmniej jedna obsługiwana wersja środowiska uruchomieniowego określona w **\<supportedRuntime>** elemencie jest obecna, środowisko uruchomieniowe ładuje wersję środowiska uruchomieniowego określoną przez pierwszy **\<supportedRuntime>** element. Jeśli ta wersja jest niedostępna, środowisko uruchomieniowe sprawdzi następny **\<supportedRuntime>** element i podejmie próbę załadowania określonej wersji środowiska uruchomieniowego. Jeśli ta wersja środowiska uruchomieniowego jest niedostępna, kolejne **\<supportedRuntime>** elementy są badane. Jeśli żadna z obsługiwanych wersji środowiska uruchomieniowego nie jest dostępna, środowisko uruchomieniowe nie może załadować wersji środowiska uruchomieniowego i wyświetla komunikat dla użytkownika (zobacz krok 3).  
  
2. Środowisko uruchomieniowe odczytuje nagłówek pliku wykonywalnego aplikacji. Jeśli dostępna jest wersja środowiska uruchomieniowego określona przez nagłówek pliku PE, środowisko uruchomieniowe ładuje tę wersję. Jeśli określona wersja środowiska uruchomieniowego jest niedostępna, środowisko uruchomieniowe wyszukuje wersję środowiska uruchomieniowego określoną przez firmę Microsoft, aby była zgodna z wersją środowiska uruchomieniowego w nagłówku PE. Jeśli ta wersja nie zostanie znaleziona, proces przechodzi do kroku 3.  
  
3. Środowisko uruchomieniowe wyświetla komunikat informujący o tym, że wersja środowiska uruchomieniowego obsługiwana przez aplikację jest niedostępna. Środowisko uruchomieniowe nie zostało załadowane.  
  
    > [!NOTE]
    > Możesz pominąć wyświetlanie komunikatu przy użyciu wartości NoGuiFromShim w kluczu rejestru HKLM\Software\Microsoft \\ . NETFramework lub przy użyciu zmiennej środowiskowej COMPLUS_NoGuiFromShim. Można na przykład pominąć komunikat dla aplikacji, które zazwyczaj nie współpracują z użytkownikiem, np. w przypadku instalacji nienadzorowanych lub usług systemu Windows. Gdy ten komunikat zostanie pominięty, środowisko uruchomieniowe zapisuje komunikat w dzienniku zdarzeń.  Ustaw wartość rejestru NoGuiFromShim na 1, aby pominąć ten komunikat dla wszystkich aplikacji na komputerze. Alternatywnie Ustaw zmienną środowiskową COMPLUS_NoGuiFromShim na 1, aby pominąć komunikat dla aplikacji działających w określonym kontekście użytkownika.  
  
> [!NOTE]
> Po załadowaniu wersji środowiska uruchomieniowego przekierowania powiązań zestawu mogą określać, że załadowana zostanie inna wersja pojedynczego zestawu .NET Framework. Te przekierowania powiązań dotyczą tylko określonego zestawu, który został przekierowany.  
  
## <a name="partially-qualified-assembly-names-and-side-by-side-execution"></a>Częściowo kwalifikowane nazwy zestawów a wykonywanie równoczesne  

Ponieważ są to potencjalne źródło problemów równoległych, częściowo kwalifikowane odwołania do zestawów mogą być używane tylko do tworzenia powiązań z zestawami w katalogu aplikacji. Unikaj częściowo kwalifikowanych odwołań do zestawów w kodzie.  
  
Aby wyeliminować częściowo kwalifikowane odwołania do zestawów w kodzie, można użyć [\<qualifyAssembly>](../configure-apps/file-schema/runtime/qualifyassembly-element.md) elementu w pliku konfiguracyjnym aplikacji do w pełni kwalifikujących się częściowo kwalifikowanych odwołań do zestawów, które występują w kodzie. Użyj **\<qualifyAssembly>** elementu, aby określić tylko pola, które nie zostały ustawione w odwołaniu częściowym. Tożsamość zestawu wymieniona w atrybucie **FullName** musi zawierać wszystkie informacje niezbędne do pełnej kwalifikacji nazwy zestawu: Nazwa zestawu, klucz publiczny, kultura i wersja.  
  
 Poniższy przykład przedstawia wpis pliku konfiguracji aplikacji w celu uzyskania pełnej kwalifikacji zestawu o nazwie `myAssembly` .  
  
```xml  
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
<qualifyAssembly partialName="myAssembly"
fullName="myAssembly,  
      version=1.0.0.0,
publicKeyToken=...,
      culture=neutral"/>
</assemblyBinding>
```  
  
 Za każdym razem, gdy następuje odwołanie do instrukcji ładowania zestawu `myAssembly` , te ustawienia pliku konfiguracji powodują, że środowisko uruchomieniowe automatycznie przetłumaczy częściowo kwalifikowane `myAssembly` odwołanie na w pełni kwalifikowane odwołanie. Na przykład zestaw. Load ("Moja Assembly") staną się zestawem. Load ("Moja Assembly, Version = 1.0.0.0, publicKeyToken =..., Culture = neutral").  
  
> [!NOTE]
> Można użyć metody **LoadWithPartialName** , aby pominąć ograniczenie środowiska uruchomieniowego języka wspólnego, które zabrania ładowania częściowo przywołanych zestawów z globalnej pamięci podręcznej zestawów. Ta metoda powinna być używana tylko w scenariuszach komunikacji zdalnej, ponieważ może łatwo spowodować problemy podczas wykonywania równoczesnego.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Instrukcje: Włączanie i wyłączanie automatycznego przekierowania powiązań](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)|Opis sposobu tworzenia powiązania aplikacji z określoną wersją zestawu.|  
|[Konfigurowanie przekierowywania powiązań zestawów](configuring-assembly-binding-redirection.md)|Opis sposobu przekierowywania odwołań do powiązań zestawów do określonej wersji zestawów programu .NET Framework.|  
|[Wykonywanie równoczesne i wewnątrzprocesowe](in-process-side-by-side-execution.md)|Omówienie sposobu używania aktywacji hosta środowiska uruchomieniowego wewnątrzprocesowego wykonywania równoczesnego w celu uruchamiania wielu wersji środowiska CLR w pojedynczym procesie.|  
|[Zestawy w środowisku .NET](../../standard/assembly/index.md)|Omówienie koncepcyjne zestawów.|  
|[Domeny aplikacji](../app-domains/application-domains.md)|Omówienie koncepcyjne domen aplikacji.|  
  
## <a name="reference"></a>Dokumentacja  

[\<supportedRuntime>Postaci](../configure-apps/file-schema/startup/supportedruntime-element.md)
