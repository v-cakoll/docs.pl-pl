---
title: "Wykonywanie równoczesne w programie .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: side-by-side execution
ms.assetid: 649f1342-766b-49e6-a90d-5b019a751e11
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 25a5092da1526bc266c5cc483cc3cd81d2ac3385
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="side-by-side-execution-in-the-net-framework"></a>Wykonywanie równoczesne w programie .NET Framework
Wykonywanie równoczesne stwarza możliwość uruchamiania wielu wersji aplikacji lub składnika na jednym komputerze. Można mieć wiele wersji środowiska uruchomieniowego języka wspólnego i wiele wersji aplikacji oraz składników, które używają wersji środowiska uruchomieniowego na jednym komputerze w tym samym czasie.  
  
 Na poniższej ilustracji pokazano kilka aplikacji używających dwóch różnych wersji środowiska uruchomieniowego na jednym komputerze. Aplikacje A, B i C używają środowiska uruchomieniowego w wersji 1.0, podczas gdy aplikacja D używa środowiska uruchomieniowego w wersji 1.1.  
  
 ![Po stronie &#45; przez &#45; wykonanie po stronie](../../../docs/framework/deployment/media/simplesbs.gif "simplesbs")  
Wykonywanie równoczesne dwóch wersji środowiska uruchomieniowego  
  
 Program .NET Framework składa się ze środowiska uruchomieniowego języka wspólnego i kolekcji zestawów zawierających typy interfejsu API. Wersje środowiska uruchomieniowego i zestawów programu .NET Framework są określane oddzielnie. Na przykład wersja 4.0 środowiska uruchomieniowego jest w rzeczywistości wersją 4.0.319, natomiast wersja 1.0 zestawów programu .NET Framework jest w rzeczywistości wersją 1.0.3300.0.  
  
 Na poniższej ilustracji pokazano kilka aplikacji używających dwóch różnych wersji składnika na jednym komputerze. Aplikacje A i B używają wersji 1.0 składnika, podczas gdy aplikacja C używa wersji 2.0 tego samego składnika.  
  
 ![Po stronie &#45; przez &#45; wykonanie po stronie](../../../docs/framework/deployment/media/compsbs.gif "compsbs")  
Wykonywanie równoczesne dwóch wersji składnika  
  
 Wykonywanie równoczesne daje większą kontrolę nad tym, z którymi wersjami składnika jest powiązana aplikacja, a także większą kontrolę nad tym, których wersji środowiska uruchomieniowego używa aplikacja.  
  
## <a name="benefits-of-side-by-side-execution"></a>Korzyści z wykonywania równoczesnego  
 Przed wprowadzeniem systemu Windows XP i programu .NET Framework występowały konflikty bibliotek DLL, ponieważ aplikacje nie mogły rozróżnić niezgodnych wersji tego samego kodu. Informacje o typach zawarte w bibliotece DLL były powiązane tylko z nazwą pliku. Aplikacja nie miała żadnej możliwość określenia, czy typy zawarte w bibliotece DLL były tymi samymi typami, z użyciem których aplikacja została skompilowana. W rezultacie nowa wersja składnika mogła zastąpić starszą wersję i spowodować przerwanie działania aplikacji.  
  
 Wykonywanie równoczesne i program .NET Framework dostarczają następujące funkcje służące do eliminowania konfliktów bibliotek DLL:  
  
-   Zestawy o silnych nazwach.  
  
     Funkcja wykonywania równoczesnego używa zestawów o silnych nazwach w celu powiązania informacji o typie z określoną wersją zestawu. Zapobiega to powiązaniu aplikacji lub składnika z nieprawidłową wersją zestawu. Zestawy o silnych nazwach umożliwiają również istnienie wielu wersji pliku na jednym komputerze i używanie ich przez aplikacje. Aby uzyskać więcej informacji, zobacz [zestawy Strong-Named](../../../docs/framework/app-domains/strong-named-assemblies.md).  
  
-   Magazyn kodu rozpoznający wersje.  
  
     Program .NET Framework dostarcza magazyn kodu rozpoznający wersje w globalnej pamięci podręcznej zestawów. Globalna pamięć podręczna zestawów to pamięć podręczna kodu dla całego komputera, która znajduje się na każdym komputerze z zainstalowanym programem .NET Framework. Zestawy są przechowywane na podstawie wersji, kultury i informacjach o wydawcy, a ponadto jest obsługiwanych wiele wersji składników i aplikacji. Aby uzyskać więcej informacji, zobacz [Global Assembly Cache](../../../docs/framework/app-domains/gac.md).  
  
-   Izolacja.  
  
     Używając programu .NET Framework, można tworzyć aplikacje i składniki, które są wykonywane w izolacji. Izolacja jest istotnym składnikiem funkcji wykonywania równoczesnego. Działanie izolacji obejmuje rozpoznawanie używanych zasobów oraz współużytkowanie zasobów przez wiele wersji aplikacji lub składnika. Izolacja obejmuje również przechowywanie plików w sposób specyficzny dla wersji. Aby uzyskać więcej informacji na temat izolacji, zobacz [wytyczne dotyczące tworzenia składników do wykonania Side-by-Side](../../../docs/framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).  
  
## <a name="version-compatibility"></a>Zgodność wersji  
 Wersje 1.0 i 1.1 programu .NET Framework są zaprojektowane tak, aby zachować zgodność ze sobą. Aplikacja skompilowana przy użyciu programu .NET Framework w wersji 1.0 powinna działać w wersji 1.1, a aplikacja skompilowana przy użyciu programu .NET Framework w wersji 1.1 powinna działać w wersji 1.0. Należy jednak zauważyć, że funkcje interfejsu API dodane w wersji 1.1 programu .NET Framework nie będą działać w wersji 1.0 programu .NET Framework. Aplikacje utworzone przy użyciu wersji 2.0 będzie można uruchomić tylko w wersji 2.0. Aplikacje utworzone w wersji 2.0 nie będą działać w wersji 1.1 lub wcześniejszej.  
  
 Wersje programu .NET Framework są traktowane jako pojedyncze jednostki składające się ze środowiska uruchomieniowego i skojarzonych zestawów programu .NET Framework (koncepcja określana jako ujednolicenie zestawów). Można przekierować powiązanie zestawu, tak aby dołączyć inne wersje zestawów .NET Framework, ale zastępowanie domyślnego powiązania zestawu może być ryzykowne, przez co należy je starannie przetestować przed wdrożeniem.  
  
## <a name="locating-runtime-version-information"></a>Lokalizowanie informacji o wersji środowiska uruchomieniowego  
 Informacje o którym środowiska uruchomieniowego wersji aplikację lub składnik, został skompilowany z i które wersje środowiska uruchomieniowego aplikacji wymaga, aby uruchomić są przechowywane w dwóch lokalizacjach. Podczas kompilowania aplikacji lub składnika informacji na temat wersji środowiska uruchomieniowego umożliwia go skompilować są przechowywane w pliku wykonywalnego zarządzanych. Informacje w wersjach środowiska uruchomieniowego wymagane przez aplikację lub składnik są przechowywane w pliku konfiguracyjnym aplikacji.  
  
### <a name="runtime-version-information-in-the-managed-executable"></a>Informacje o wersji środowiska uruchomieniowego w zarządzanych pliku wykonywalnego  
 Przenośne nagłówka pliku wykonywalnego (PE) w każdej zarządzanych aplikacji i składnika zawiera informacje o wersji środowiska uruchomieniowego, który został utworzony z. Środowisko uruchomieniowe języka wspólnego używa tych informacji do ustalenia najprawdopodobniej wersji środowiska uruchomieniowego potrzebne do uruchomienia aplikacji.  
  
### <a name="runtime-version-information-in-the-application-configuration-file"></a>Informacje o wersji środowiska uruchomieniowego w pliku konfiguracji aplikacji  
 Oprócz informacji w nagłówku pliku PE można wdrożyć aplikacji z pliku konfiguracji aplikacji, która zapewnia informacje o wersji środowiska wykonawczego. Plik konfiguracji aplikacji jest plikiem opartych na języku XML utworzonego przez dewelopera aplikacji i który jest dostarczany z aplikacją. [ \<RequiredRuntime > Element](../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) z [ \<uruchamiania > sekcji](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md), jeśli jest obecny w tym pliku Określa, które wersje środowiska uruchomieniowego i które wersje programu Składnik aplikacji obsługuje. Ten plik do testowania służy również do testowania zgodności aplikacji z różnych wersji środowiska uruchomieniowego.  
  
 Niezarządzany kod, łącznie z aplikacjami COM i COM +, może zawierać pliki konfiguracji aplikacji, używane przez środowisko uruchomieniowe do interakcji z kodu zarządzanego. W pliku konfiguracyjnym aplikacji ma wpływ na kod zarządzany, który można aktywować za pomocą modelu COM. Plik można określić, które obsługuje wersje środowiska uruchomieniowego, a także zestaw przekierowuje. Domyślnie aplikacje międzyoperacyjne COM, wywołanie do zarządzanego kodu użyj najnowszej wersji środowiska uruchomieniowego zainstalowany na komputerze.  
  
 Aby uzyskać więcej informacji o plikach konfiguracji aplikacji, zobacz [konfigurowania aplikacji](../../../docs/framework/configure-apps/index.md).  
  
## <a name="determining-which-version-of-the-runtime-to-load"></a>Określanie wersji środowiska uruchomieniowego do załadowania  
 Środowisko uruchomieniowe języka wspólnego używa następujących informacji, aby ustalić, która wersja środowiska uruchomieniowego można załadować aplikacji:  
  
-   Wersje środowiska uruchomieniowego, które są dostępne.  
  
-   Wersje środowiska uruchomieniowego obsługiwanych przez aplikację.  
  
### <a name="supported-runtime-versions"></a>Wersje obsługiwane środowiska wykonawczego  
 Środowisko uruchomieniowe korzysta z pliku konfiguracji aplikacji i przenośnych nagłówka pliku wykonywalnego (PE), aby określić, obsługuje aplikację wersji środowiska uruchomieniowego. Jeśli plik konfiguracji aplikacji nie jest obecny, środowisko uruchomieniowe ładuje określona w nagłówku pliku PE aplikacji, wersja środowiska uruchomieniowego, jeśli ta wersja jest dostępna.  
  
 Jeśli istnieje plik konfiguracji aplikacji, środowisko uruchomieniowe określa wersji środowiska uruchomieniowego odpowiednie załadować oparte na wynikach następujący proces:  
  
1.  Sprawdza, czy środowisko uruchomieniowe [ \<supportedRuntime > Element](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) elementu w pliku konfiguracyjnym aplikacji. Jeśli co najmniej jeden z obsługiwanych środowiska uruchomieniowego wersje określone w  **\<supportedRuntime >** elementu, środowisko uruchomieniowe ładuje określona przez pierwszy wersja środowiska uruchomieniowego  **\< supportedRuntime >** elementu. Jeśli ta wersja nie jest dostępna, środowisko uruchomieniowe sprawdza, czy Następna  **\<supportedRuntime >** element i próbuje załadować określona wersja środowiska uruchomieniowego. Jeśli ta wersja środowiska uruchomieniowego nie jest dostępna, kolejne  **\<supportedRuntime >** elementy są sprawdzane. W przypadku wersji środowiska uruchomieniowego obsługiwanych nie jest dostępna żadna, środowisko uruchomieniowe nie udało się załadować wersji środowiska uruchomieniowego i jest wyświetlany komunikat (zobacz krok 3).  
  
2.  Środowisko uruchomieniowe odczytuje nagłówek PE pliku plik wykonywalny aplikacji. Jeśli określona w nagłówku pliku PE wersja środowiska uruchomieniowego jest dostępny, środowisko uruchomieniowe ładuje tej wersji. Jeśli określona wersja środowiska uruchomieniowego nie jest dostępna, środowisko uruchomieniowe wyszukuje określone przez firmę Microsoft, aby był zgodny z wersją środowiska uruchomieniowego w nagłówku PE wersji środowiska uruchomieniowego. Jeśli ta wersja nie zostanie znaleziony, proces jest kontynuowany do kroku 3.  
  
3.  Środowisko uruchomieniowe wyświetla komunikat z informacją o niedostępności wersja środowiska uruchomieniowego obsługiwanych przez aplikację. Nie załadowano środowiska uruchomieniowego.  
  
    > [!NOTE]
    >  Wyświetlanie ten komunikat można pominąć przy użyciu wartości NoGuiFromShim w kluczu rejestru HKLM\Software\Microsoft\\. NETFramework lub za pomocą zmiennej środowiskowej COMPLUS_NoGuiFromShim. Na przykład można pominąć komunikat dla aplikacji, które nie zwykle mieć interakcji z użytkownikiem, takie jak instalacji nienadzorowanej lub usług systemu Windows. Gdy ten komunikat o błędzie jest pominięty, środowisko uruchomieniowe zapisuje komunikat w dzienniku zdarzeń.  Ustaw wartość rejestru NoGuiFromShim 1, aby pominąć ten komunikat dla wszystkich aplikacji na komputerze. Alternatywnie można ustawić zmiennej środowiskowej COMPLUS_NoGuiFromShim 1, aby pominąć komunikat dla aplikacji działających w kontekście konkretnego użytkownika.  
  
> [!NOTE]
>  Po załadowaniu wersji środowiska uruchomieniowego zestawu przekierowania powiązań można określić, że jest załadowana inna wersja poszczególnych zestawu .NET Framework. Te przekierowania powiązania wpływa na tylko określonego zestawu, który jest przekierowywany.  
  
## <a name="partially-qualified-assembly-names-and-side-by-side-execution"></a>Częściowo kwalifikowane nazwy zestawów a wykonywanie równoczesne  
 Ponieważ są one źródłem potencjalnych problemów side-by-side, odwołania do zestawów częściowo kwalifikowanej może służyć tylko powiązać zestawy w katalogu aplikacji. Unikaj częściowo kwalifikowanej zestawu odwołania w kodzie.  
  
 Aby uniknąć częściowo kwalifikowanej zestawu odwołania w kodzie, można użyć [ \<qualifyassembly — >](../../../docs/framework/configure-apps/file-schema/runtime/qualifyassembly-element.md) elementu w pliku konfiguracyjnym aplikacji do pełnej kwalifikacji częściowo kwalifikowanej odwołania do zestawów występujących w kodzie. Użyj  **\<qualifyassembly — >** element, aby określić tylko pola, które nie zostały określone w częściowe odwołanie. Na liście tożsamości zestawu **imię i nazwisko** atrybutu musi zawierać wszystkie informacje wymagane do pełnej kwalifikacji nazwy zestawu: Nazwa zestawu, klucz publiczny, kultury i wersji.  
  
 W poniższym przykładzie przedstawiono wpis pliku konfiguracji aplikacji do pełnej kwalifikacji zestawu o nazwie `myAssembly`.  
  
```xml  
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">   
<qualifyAssembly partialName="myAssembly"   
fullName="myAssembly,  
      version=1.0.0.0,   
publicKeyToken=...,   
      culture=neutral"/>   
</assemblyBinding>   
```  
  
 Zawsze, gdy zestaw obciążenia odwołuje się do instrukcji `myAssembly`, te ustawienia konfiguracji pliku spowodować środowiska uruchomieniowego automatycznie tłumaczenie częściowo kwalifikowanej `myAssembly` odwołania do w pełni kwalifikowane odwołanie. Na przykład Assembly.Load("myAssembly") staje się metody Assembly.Load ("myAssembly, wersja = 1.0.0.0, publicKeyToken =..., culture = neutral").  
  
> [!NOTE]
>  Można użyć **LoadWithPartialName** metodę obejścia typowych ograniczeń języka środowiska uruchomieniowego częściowo zabrania się do niego odwoływać zestawy ładowane z globalnej pamięci podręcznej zestawów. Ta metoda stosuje się tylko w scenariuszach remoting, łatwo może spowodować problemy podczas wykonywania side-by-side.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Porady: Włączanie i wyłączanie automatycznego przekierowania powiązań](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)|Opis sposobu tworzenia powiązania aplikacji z określoną wersją zestawu.|  
|[Konfigurowanie przekierowywania powiązań zestawów](../../../docs/framework/deployment/configuring-assembly-binding-redirection.md)|Opis sposobu przekierowywania odwołań do powiązań zestawów do określonej wersji zestawów programu .NET Framework.|  
|[W trakcie wykonywania Side-by-Side](../../../docs/framework/deployment/in-process-side-by-side-execution.md)|Omówienie sposobu używania aktywacji hosta środowiska uruchomieniowego wewnątrzprocesowego wykonywania równoczesnego w celu uruchamiania wielu wersji środowiska CLR w pojedynczym procesie.|  
|[Zestawy w środowisko uruchomieniowe języka wspólnego](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)|Omówienie koncepcyjne zestawów.|  
|[Domeny aplikacji](../../../docs/framework/app-domains/application-domains.md)|Omówienie koncepcyjne domen aplikacji.|  
  
## <a name="reference"></a>Tematy pomocy  
 [\<supportedRuntime > — Element](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)
