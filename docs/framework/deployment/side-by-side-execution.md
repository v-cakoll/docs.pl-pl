---
title: Wykonywanie równoczesne w programie .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution
ms.assetid: 649f1342-766b-49e6-a90d-5b019a751e11
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9ee17426e3ac8d5351490276a8c71cdfe996eb1a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59341078"
---
# <a name="side-by-side-execution-in-the-net-framework"></a>Wykonywanie równoczesne w programie .NET Framework
Wykonywanie równoczesne stwarza możliwość uruchamiania wielu wersji aplikacji lub składnika na jednym komputerze. Można mieć wiele wersji środowiska uruchomieniowego języka wspólnego i wiele wersji aplikacji oraz składników, które używają wersji środowiska uruchomieniowego na jednym komputerze w tym samym czasie.  
  
 Na poniższej ilustracji pokazano kilka aplikacji używających dwóch różnych wersji środowiska uruchomieniowego na jednym komputerze. Aplikacje A, B i C używają środowiska uruchomieniowego w wersji 1.0, podczas gdy aplikacja D używa środowiska uruchomieniowego w wersji 1.1.  
  
 ![Wykonywanie Side-by-side środowiskiem uruchomieniowym w różnych wersjach](./media/side-by-side-execution/side-by-side-runtime-execution.gif)  
  
 Program .NET Framework składa się ze środowiska uruchomieniowego języka wspólnego i kolekcji zestawów zawierających typy interfejsu API. Wersje środowiska uruchomieniowego i zestawów programu .NET Framework są określane oddzielnie. Na przykład wersja 4.0 środowiska uruchomieniowego jest w rzeczywistości wersją 4.0.319, natomiast wersja 1.0 zestawów programu .NET Framework jest w rzeczywistości wersją 1.0.3300.0.  
  
 Na poniższej ilustracji pokazano kilka aplikacji używających dwóch różnych wersji składnika na jednym komputerze. Aplikacje A i B używają wersji 1.0 składnika, podczas gdy aplikacja C używa wersji 2.0 tego samego składnika.  
  
 ![Diagram przedstawiający wykonywania side-by-side składnika.](./media/side-by-side-execution/side-by-side-component-execution.gif)  
  
 Wykonywanie równoczesne daje większą kontrolę nad tym, z którymi wersjami składnika jest powiązana aplikacja, a także większą kontrolę nad tym, których wersji środowiska uruchomieniowego używa aplikacja.  
  
## <a name="benefits-of-side-by-side-execution"></a>Korzyści z wykonywania równoczesnego  
 Przed wprowadzeniem systemu Windows XP i programu .NET Framework występowały konflikty bibliotek DLL, ponieważ aplikacje nie mogły rozróżnić niezgodnych wersji tego samego kodu. Informacje o typach zawarte w bibliotece DLL były powiązane tylko z nazwą pliku. Aplikacja nie miała żadnej możliwość określenia, czy typy zawarte w bibliotece DLL były tymi samymi typami, z użyciem których aplikacja została skompilowana. W rezultacie nowa wersja składnika mogła zastąpić starszą wersję i spowodować przerwanie działania aplikacji.  
  
 Wykonywanie równoczesne i program .NET Framework dostarczają następujące funkcje służące do eliminowania konfliktów bibliotek DLL:  
  
-   Zestawy o silnych nazwach.  
  
     Funkcja wykonywania równoczesnego używa zestawów o silnych nazwach w celu powiązania informacji o typie z określoną wersją zestawu. Zapobiega to powiązaniu aplikacji lub składnika z nieprawidłową wersją zestawu. Zestawy o silnych nazwach umożliwiają również istnienie wielu wersji pliku na jednym komputerze i używanie ich przez aplikacje. Aby uzyskać więcej informacji, zobacz [zestawy Strong-Named](../../../docs/framework/app-domains/strong-named-assemblies.md).  
  
-   Magazyn kodu rozpoznający wersje.  
  
     Program .NET Framework dostarcza magazyn kodu rozpoznający wersje w globalnej pamięci podręcznej zestawów. Globalna pamięć podręczna zestawów to pamięć podręczna kodu dla całego komputera, która znajduje się na każdym komputerze z zainstalowanym programem .NET Framework. Zestawy są przechowywane na podstawie wersji, kultury i informacjach o wydawcy, a ponadto jest obsługiwanych wiele wersji składników i aplikacji. Aby uzyskać więcej informacji, zobacz [Global Assembly Cache](../../../docs/framework/app-domains/gac.md).  
  
-   Izolacja.  
  
     Używając programu .NET Framework, można tworzyć aplikacje i składniki, które są wykonywane w izolacji. Izolacja jest istotnym składnikiem funkcji wykonywania równoczesnego. Działanie izolacji obejmuje rozpoznawanie używanych zasobów oraz współużytkowanie zasobów przez wiele wersji aplikacji lub składnika. Izolacja obejmuje również przechowywanie plików w sposób specyficzny dla wersji. Aby uzyskać więcej informacji dotyczących izolacji, zobacz [wytyczne dotyczące tworzenia składników Side-by-Side Execution](../../../docs/framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).  
  
## <a name="version-compatibility"></a>Zgodność wersji  
 Wersje 1.0 i 1.1 programu .NET Framework są zaprojektowane tak, aby zachować zgodność ze sobą. Aplikacja skompilowana przy użyciu programu .NET Framework w wersji 1.0 powinna działać w wersji 1.1, a aplikacja skompilowana przy użyciu programu .NET Framework w wersji 1.1 powinna działać w wersji 1.0. Należy jednak zauważyć, że funkcje interfejsu API dodane w wersji 1.1 programu .NET Framework nie będą działać w wersji 1.0 programu .NET Framework. Aplikacje utworzone przy użyciu wersji 2.0 będzie można uruchomić tylko w wersji 2.0. Aplikacje utworzone w wersji 2.0 nie będą działać w wersji 1.1 lub wcześniejszej.  
  
 Wersje programu .NET Framework są traktowane jako pojedyncze jednostki składające się ze środowiska uruchomieniowego i skojarzonych zestawów programu .NET Framework (koncepcja określana jako ujednolicenie zestawów). Można przekierować powiązanie zestawu, tak aby dołączyć inne wersje zestawów .NET Framework, ale zastępowanie domyślnego powiązania zestawu może być ryzykowne, przez co należy je starannie przetestować przed wdrożeniem.  
  
## <a name="locating-runtime-version-information"></a>Lokalizowanie informacji o wersji środowiska uruchomieniowego  
 Informacje na temat której środowisko uruchomieniowe wersji aplikacji lub składnika został skompilowany przy użyciu, oraz wersje środowiska uruchomieniowego, które aplikacja wymaga do uruchomienia są przechowywane w dwóch lokalizacjach. Podczas kompilowania aplikacji lub składnika, informacje o wersji środowiska uruchomieniowego, można go skompilować są przechowywane w zarządzanych pliku wykonywalnego. Informacje na temat wersji środowiska uruchomieniowego, których wymaga aplikacja lub składnik znajduje się w pliku konfiguracyjnym aplikacji.  
  
### <a name="runtime-version-information-in-the-managed-executable"></a>Informacje o wersji środowiska uruchomieniowego w zarządzanych pliku wykonywalnego  
 Przenośne nagłówka pliku wykonywalnego (PE) w każdej aplikacji zarządzanej i składnik zawiera informacje o wersji środowiska uruchomieniowego, który został skompilowany. Środowisko uruchomieniowe języka wspólnego używa tych informacji do określenia najprawdopodobniej wersję środowiska uruchomieniowego, które aplikacja potrzebuje do uruchomienia.  
  
### <a name="runtime-version-information-in-the-application-configuration-file"></a>Informacje o wersji środowiska uruchomieniowego w pliku konfiguracji aplikacji  
 Oprócz informacji w nagłówku pliku PE można wdrożyć aplikację za pomocą pliku konfiguracji aplikacji, który dostarcza informacje o wersji środowiska uruchomieniowego. Plik konfiguracji aplikacji jest plikiem opartych na języku XML utworzonego przez dewelopera aplikacji i który jest dostarczany z aplikacją. [ \<RequiredRuntime > Element](../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) z [ \<uruchamiania > sekcji](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md), jeśli jest obecny w tym pliku Określa, które wersje środowiska uruchomieniowego i które wersje Składnik aplikacji obsługuje. Umożliwia także ten plik podczas testowania do testowania zgodności aplikacji z użyciem różnych wersji środowiska uruchomieniowego.  
  
 Niezarządzany kod, łącznie z aplikacjami COM i COM +, może mieć pliki konfiguracyjne aplikacji używanych przez środowisko uruchomieniowe do interakcji z kodu zarządzanego. Plik konfiguracyjny aplikacji wpływa na kod zarządzany, który można aktywować za pomocą modelu COM. Plik można określić, które wersje środowiska uruchomieniowego, które obsługuje, a także zestaw przekierowuje. Domyślnie aplikacje międzyoperacyjne COM, wywołanie do zarządzanego kodu, użyj najnowszej wersji środowiska uruchomieniowego zainstalowanego na komputerze.  
  
 Aby uzyskać więcej informacji o plikach konfiguracji aplikacji, zobacz [konfigurowania aplikacji](../../../docs/framework/configure-apps/index.md).  
  
## <a name="determining-which-version-of-the-runtime-to-load"></a>Określanie wersji środowiska uruchomieniowego do załadowania  
 Środowisko uruchomieniowe języka wspólnego używa następujących informacji, aby określić, która wersja środowiska uruchomieniowego do załadowania dla aplikacji:  
  
-   Wersje środowiska uruchomieniowego, które są dostępne.  
  
-   Wersje środowiska uruchomieniowego, obsługiwanych przez aplikację.  
  
### <a name="supported-runtime-versions"></a>Obsługiwane wersje środowiska uruchomieniowego  
 Środowisko wykonawcze używa pliku konfiguracji aplikacji i przenośnych nagłówka pliku wykonywalnego (PE), aby określić, która wersja środowiska uruchomieniowego aplikacji obsługuje. Jeśli plik konfiguracji aplikacji, nie jest obecny, środowisko uruchomieniowe ładuje wersji środowiska uruchomieniowego, określony w nagłówku pliku PE aplikacji, jeśli ta wersja jest dostępna.  
  
 Jeśli plik konfiguracji aplikacji jest obecny, środowisko wykonawcze określa wersję odpowiedniego środowiska uruchomieniowego do załadowania w oparciu o wyniki następującego procesu:  
  
1. Sprawdza, czy środowisko uruchomieniowe [ \<supportedRuntime > Element](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) elementu w pliku konfiguracyjnym aplikacji. Jeśli co najmniej jeden obsługiwane wersje środowiska uruchomieniowego określone w  **\<supportedRuntime >** elementu, środowisko uruchomieniowe ładuje wersji środowiska uruchomieniowego, w określonym przez pierwszy  **\< supportedRuntime >** elementu. Jeśli ta wersja nie jest dostępna, środowisko uruchomieniowe sprawdza, czy następnego  **\<supportedRuntime >** elementu i próbuje załadować określona wersja środowiska uruchomieniowego. Jeśli ta wersja środowiska uruchomieniowego nie jest dostępna, kolejne  **\<supportedRuntime >** elementy są sprawdzane. Jeśli żaden z obsługiwane wersje środowiska uruchomieniowego są dostępne, środowisko wykonawcze nie można załadować wersji środowiska uruchomieniowego, a następnie wyświetla komunikat dla użytkownika (zobacz krok 3).  
  
2. Środowisko uruchomieniowe odczytuje nagłówek pliku PE pliku wykonywalnego aplikacji. Jeśli dostępna jest wersja środowiska uruchomieniowego, określony w nagłówku pliku PE, środowisko uruchomieniowe ładuje tej wersji. Jeśli określona wersja środowiska uruchomieniowego nie jest dostępna, środowisko uruchomieniowe wyszukuje wersji środowiska uruchomieniowego, określane przez firmę Microsoft, aby był zgodny z wersją środowiska uruchomieniowego w nagłówku PE. Jeśli ta wersja nie zostanie znaleziony, proces jest kontynuowany do kroku 3.  
  
3. Środowisko uruchomieniowe wyświetla komunikat informujący, że wersja środowiska uruchomieniowego, obsługiwanych przez aplikację jest niedostępna. Nie załadowano środowiska uruchomieniowego.  
  
    > [!NOTE]
    >  Wyświetlanie ten komunikat można pominąć przy użyciu wartości NoGuiFromShim w kluczu rejestru HKLM\Software\Microsoft\\. NETFramework lub przy użyciu zmiennej środowiskowej COMPLUS_NoGuiFromShim. Na przykład można pominąć wiadomości dla aplikacji, które zazwyczaj wchodzi w interakcję z użytkownikiem, takich jak instalacji nienadzorowanej lub usługi Windows. Gdy ten komunikat o błędzie jest pominięty, środowisko uruchomieniowe zapisuje komunikat w dzienniku zdarzeń.  Ustaw wartość rejestru NoGuiFromShim 1, aby pominąć ten komunikat dla wszystkich aplikacji na komputerze. Możesz również ustawić zmienną środowiskową COMPLUS_NoGuiFromShim 1, aby pominąć komunikat dla aplikacji uruchamianych w kontekście danego użytkownika.  
  
> [!NOTE]
>  Po załadowaniu wersji środowiska uruchomieniowego, przekierowania powiązań zestawu można określić, że załadowane inną wersję poszczególnych zestawów .NET Framework. Te przekierowania powiązań wpływa na tylko określony zestaw jest przekierowany.  
  
## <a name="partially-qualified-assembly-names-and-side-by-side-execution"></a>Częściowo kwalifikowane nazwy zestawów a wykonywanie równoczesne  
 Ponieważ są one potencjalnym źródłem problemów side-by-side, częściowo kwalifikowane odwołania do zestawów może służyć tylko do powiązania do zestawów w katalogu aplikacji. Należy unikać częściowo kwalifikowane odwołania do zestawów w kodzie.  
  
 Aby uniknąć częściowo kwalifikowane odwołania do zestawów w kodzie, można użyć [ \<qualifyassembly — >](../../../docs/framework/configure-apps/file-schema/runtime/qualifyassembly-element.md) elementu w pliku konfiguracji aplikacji do pełnej kwalifikacji częściowo kwalifikowanych odwołań do zestawów, które występują w kodzie. Użyj  **\<qualifyassembly — >** elementu, aby określić tylko pola, które nie zostały ustawione w częściowe odwołanie. Tożsamość zestawu, na liście **imię i nazwisko** atrybutu musi zawierać wszystkie informacje wymagane do pełnej kwalifikacji Nazwa zestawu: Nazwa zestawu, klucz publiczny, kultury i wersji.  
  
 W poniższym przykładzie pokazano wpis w pliku konfiguracji aplikacji do pełnej kwalifikacji zestaw o nazwie `myAssembly`.  
  
```xml  
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">   
<qualifyAssembly partialName="myAssembly"   
fullName="myAssembly,  
      version=1.0.0.0,   
publicKeyToken=...,   
      culture=neutral"/>   
</assemblyBinding>   
```  
  
 Zawsze, gdy zestaw obciążenia odwołuje się do instrukcji `myAssembly`, te ustawienia w pliku konfiguracji, że środowisko uruchomieniowe automatycznie Tłumacz częściowo kwalifikowane `myAssembly` odwołanie do w pełni kwalifikowane odwołanie. Na przykład Assembly.Load("myAssembly") staje się Assembly.Load ("myAssembly, wersja = 1.0.0.0, publicKeyToken =..., culture = neutral").  
  
> [!NOTE]
>  Możesz użyć **loadwithpartialname —** metodę, aby pominąć typowe ograniczenie środowiska uruchomieniowego języka, które częściowo zabrania zestawów występujących w odwołaniu z ładowane z globalnej pamięci podręcznej. Ta metoda powinna służyć tylko w scenariuszach komunikacji zdalnej, jak łatwo może powodować problemy podczas wykonywania side-by-side.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Instrukcje: Włączanie i wyłączanie automatycznego przekierowania powiązań](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)|Opis sposobu tworzenia powiązania aplikacji z określoną wersją zestawu.|  
|[Konfigurowanie przekierowywania powiązań zestawów](../../../docs/framework/deployment/configuring-assembly-binding-redirection.md)|Opis sposobu przekierowywania odwołań do powiązań zestawów do określonej wersji zestawów programu .NET Framework.|  
|[Wykonywanie równoczesne i wewnątrzprocesowe](../../../docs/framework/deployment/in-process-side-by-side-execution.md)|Omówienie sposobu używania aktywacji hosta środowiska uruchomieniowego wewnątrzprocesowego wykonywania równoczesnego w celu uruchamiania wielu wersji środowiska CLR w pojedynczym procesie.|  
|[Zestawy w środowisku uruchomieniowym CLR](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)|Omówienie koncepcyjne zestawów.|  
|[Domeny aplikacji](../../../docs/framework/app-domains/application-domains.md)|Omówienie koncepcyjne domen aplikacji.|  
  
## <a name="reference"></a>Tematy pomocy  
 [\<supportedRuntime> Element](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)
