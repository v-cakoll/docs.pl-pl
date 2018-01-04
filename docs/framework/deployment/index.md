---
title: "Wdrażanie programu .NET Framework i aplikacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying applications [.NET Framework], packaging
- deploying applications [.NET Framework]
- deploying applications [.NET Framework], features
- deploying applications [.NET Framework], distribution
- .NET Framework, deploying
- .NET Framework application deployment
ms.assetid: 238d8284-6042-4a38-a7f6-1ee8efd719da
caps.latest.revision: "56"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c88aabf046ac720d14db3e68c8e04092188a7ef1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="deploying-the-net-framework-and-applications"></a>Wdrażanie programu .NET Framework i aplikacji
Ten artykuł pomoże rozpocząć wdrażanie programu .NET Framework z aplikacją. Większość informacji jest przeznaczony dla deweloperów, OEM i Administratorzy przedsiębiorstwa. Użytkownicy chcący zainstalować program .NET Framework na swoich komputerach należy przeczytać [Instalowanie programu .NET Framework](~/docs/framework/install/index.md).  
  
## <a name="key-deployment-resources"></a>Zasoby dotyczące wdrażania klucza  
 Informacje na temat wdrażania i obsługi programu .NET Framework, użyj następujących łączy do innych tematów w witrynie MSDN.  
  
 **Instalacji i wdrażania**  
  
-   Ogólne informacje dotyczące Instalatora i wdrażania:  
  
    -   Opcje Instalatora:  
  
        -   [Instalator sieci Web](~/docs/framework/install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)  
  
        -   [Instalatora w trybie offline](~/docs/framework/install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)  
  
    -   Tryby instalacji:  
  
        -   [Instalacja w trybie dyskretnym](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining_custom)  
  
        -   [Wyświetlanie interfejsu użytkownika](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining_default)  
  
    -   [Zmniejszenie liczby systemu ponownych uruchomień podczas instalacji programu .NET Framework 4.5](../../../docs/framework/deployment/reducing-system-restarts.md)  
  
    -   [Rozwiązywanie problemów z zablokowaną instalacją i odinstalowywaniem programu .NET Framework](~/docs/framework/install/troubleshoot-blocked-installations-and-uninstallations.md)  
  
-   Wdrażanie programu .NET Framework z aplikacją klienta (dla deweloperów):  
  
    -   [Przy użyciu InstallShield](../../../docs/framework/deployment/deployment-guide-for-developers.md#installshield-deployment) w projekcie instalacji i wdrażania  
  
    -   [Przy użyciu aplikacji ClickOnce usługi Visual Studio](../../../docs/framework/deployment/deployment-guide-for-developers.md#clickonce-deployment)  
  
    -   [Tworzenie pakietu instalacyjnego WiX](../../../docs/framework/deployment/deployment-guide-for-developers.md#wix)  
  
    -   [Za pomocą instalatora niestandardowego](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining)  
  
    -   [Dodatkowe informacje](../../../docs/framework/deployment/deployment-guide-for-developers.md) dla deweloperów  
  
-   Wdrażanie programu .NET Framework (dla producentów OEM i Administratorzy):  
  
    -   [Windows Assessment and Deployment Kit (ADK)](http://go.microsoft.com/fwlink/p/?LinkId=254976)  
  
    -   [Podręcznik administratora](../../../docs/framework/deployment/guide-for-administrators.md)  
  
 **Obsługi**  
  
-   Aby uzyskać ogólne informacje, zobacz [blogu .NET Framework](http://go.microsoft.com/fwlink/p/?LinkId=254977)  
  
-   [Wykrywanie wersji](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)  
  
-   [Wykrywanie dodatków service pack i aktualizacje](../../../docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)  
  
## <a name="features-that-simplify-deployment"></a>Funkcje, które upraszczają proces wdrażania  
 .NET Framework udostępnia wiele podstawowych funkcji, które ułatwiają wdrażanie aplikacji:  
  
-   Aplikacje nie wpływu.  
  
     Ta funkcja zapewnia izolację aplikacji i eliminuje konflikty biblioteki DLL. Domyślnie składniki nie wpływa na inne aplikacje.  
  
-   Składniki prywatnej domyślnie.  
  
     Domyślnie składniki są wdrażane do katalogu aplikacji i są widoczne tylko dla aplikacji zawierających.  
  
-   Udostępnianie kodu kontrolowany.  
  
     Udostępnianie kodu wymaga jawnie udostępnić kodu do udostępniania zamiast domyślnego zachowania.  
  
-   Przechowywanie wersji Side-by-side.  
  
     Wiele wersji składnika lub aplikacji mogą współistnieć, można wybrać, które wersje do użycia i środowisko uruchomieniowe języka wspólnego wymusza zasady przechowywania wersji.  
  
-   Wdrażanie XCOPY i replikacji.  
  
     Składniki własnym opisane, niezależna i aplikacje można wdrożyć bez wpisy rejestru lub zależności.  
  
-   Aktualizacje na bieżąco.  
  
     Administratorzy mogą używać hostów, takich jak ASP.NET, aby zaktualizować program bibliotek DLL, nawet na komputerach zdalnych.  
  
-   Integracja z Instalatora Windows.  
  
     Anonsu, publikowania, naprawy i instalacji na żądanie są wszystkie dostępne podczas wdrażania aplikacji.  
  
-   Wdrożenia w przedsiębiorstwie.  
  
     Ta funkcja zapewnia dystrybucji oprogramowania łatwe, w tym o korzystaniu z usługi Active Directory.  
  
-   Pobieranie i buforowania.  
  
     Pobieranie przyrostowe Zachowaj mniejsze pliki do pobrania i składniki mogą być izolowane do użycia tylko przez aplikację do wdrożenia niskiego wpływu.  
  
-   Częściowo zaufany kod.  
  
     Tożsamość jest oparty na kodzie zamiast użytkownika, a pola dialogowe certyfikat, nie pojawiają się.  
  
## <a name="packaging-and-distributing-net-framework-applications"></a>Pakowanie i dystrybucja aplikacji .NET Framework  
 Niektóre z pakowaniem i informacje na temat wdrażania dla programu .NET Framework jest opisane w innych częściach dokumentacji. Te sekcje zawierają informacje dotyczące samoopisujące jednostki o nazwie [zestawy](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md), które nie wymagają żadnych wpisów rejestru [zestawy o silnych nazwach](../../../docs/framework/app-domains/strong-named-assemblies.md), co zapewnić unikatowość nazwy i zapobiec nazwy fałszowanie zawartości, i [przechowywanie wersji zestawu](../../../docs/framework/app-domains/assembly-versioning.md), która rozwiązuje wiele problemów związanych z konflikty biblioteki DLL. Poniższe sekcje zawierają informacje dotyczące tworzenia pakietów i dystrybucja aplikacji .NET Framework.  
  
### <a name="packaging"></a>Tworzenie pakietów  
 .NET Framework udostępnia następujące opcje dla pakietów aplikacji:  
  
-   Jako pojedynczy zestaw lub zbiór zestawów.  
  
     Ta opcja służy po prostu plików .dll lub .exe zgodnie z ich zostały skompilowane.  
  
-   Jako pliki w formacie cabinet (CAB).  
  
     Po wybraniu tej opcji należy kompresuje pliki do plików cab dystrybucji lub pobrać szybciej.  
  
-   Jako pakiet Instalatora systemu Windows lub w innych formatach Instalatora.  
  
     Po wybraniu tej opcji tworzenia pliku .msi do użycia przy użyciu Instalatora Windows lub pakietu aplikacji do użycia z niektórych innych Instalatora.  
  
### <a name="distribution"></a>Dystrybucji  
 Platforma .NET Framework zapewnia następujące opcje dystrybucji aplikacji:  
  
-   Użyj polecenia XCOPY lub FTP.  
  
     Ponieważ typowych aplikacji środowiska wykonawczego języka są samoopisujące i wymagają żadnych wpisów rejestru, wystarczy skopiować do odpowiedniego katalogu aplikacji można użyć polecenia XCOPY lub FTP. Aplikacja może następnie uruchamiana z tego katalogu.  
  
-   Użyj Pobieranie kodu.  
  
     Jeśli aplikacja jest rozpowszechniana przez Internet lub przez firmową sieć intranet, można po prostu Pobierz kod na komputer i uruchomić aplikację.  
  
-   Użyj programu instalacyjnego, takich jak Instalator Windows 2.0.  
  
     Instalatora systemu Windows w wersji 2.0 można zainstalować, naprawę lub usunięcie zestawy .NET Framework w pamięci podręcznej GAC i prywatnych katalogów.  
  
### <a name="installation-location"></a>Lokalizacja instalacji  
 Aby ustalić, gdzie można wdrażać zestawów aplikacji, tak aby można je znaleźć w czasie wykonywania, zobacz [jak zestawy środowiska wykonawczego lokalizuje](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
 Zagadnienia dotyczące zabezpieczeń może wpłynąć na sposób wdrażania aplikacji. Kod zarządzany zgodnie z którym znajduje się kod są przyznawane uprawnienia zabezpieczeń. Wdrażanie aplikacji lub składnika do lokalizacji, w którym odbiera małego zaufania, na przykład Internet, limity aplikację lub składnik czynności. Aby uzyskać więcej informacji na temat wdrażania i zagadnienia dotyczące zabezpieczeń, zobacz [podstawy zabezpieczeń dostępu kodu](../../../docs/framework/misc/code-access-security-basics.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)|W tym artykule opisano, jak środowisko uruchomieniowe języka wspólnego Określa, które zestawu do używania w celu spełnienia żądania powiązania.|  
|[Najlepsze praktyki dotyczące ładowania zestawu](../../../docs/framework/deployment/best-practices-for-assembly-loading.md)|W tym artykule omówiono sposób, aby uniknąć problemów tożsamości typu, który może prowadzić do <xref:System.InvalidCastException>, <xref:System.MissingMethodException>oraz innych błędów.|  
|[Zmniejszenie liczby ponownych uruchomień systemu podczas instalowania programu .NET Framework 4.5](../../../docs/framework/deployment/reducing-system-restarts.md)|Opisano Menedżera ponownego uruchomienia, co uniemożliwia uruchamiany ponownie, jeśli to możliwe i wyjaśniono, jak aplikacje, które Zainstaluj program .NET Framework mogą wykorzystać go.|  
|[Przewodnik wdrażania dla administratorów](../../../docs/framework/deployment/guide-for-administrators.md)|W tym artykule wyjaśniono, jak administrator systemu może wdrożenia programu .NET Framework i jego zależności systemu w sieci za pomocą programu System Center Configuration Manager (SCCM).|  
|[Przewodnik wdrażania dla deweloperów](../../../docs/framework/deployment/deployment-guide-for-developers.md)|W tym artykule wyjaśniono, jak deweloperzy można zainstalować środowiska .NET Framework na ich komputerów z ich aplikacji.|  
|[Wdrażanie aplikacji, usług i składników](/visualstudio/deployment/deploying-applications-services-and-components)|W tym artykule omówiono opcje wdrażania w programie Visual Studio, w tym instrukcje dotyczące publikowania aplikacji przy użyciu technologii ClickOnce i Instalatora Windows.| 
|[Publikowanie aplikacji ClickOnce](/visualstudio/deployment/publishing-clickonce-applications)|Opisuje sposób pakietu aplikacji formularzy systemu Windows, a następnie wdrożyć go za pomocą technologii ClickOnce do komputerów klienckich w sieci.|  
|[Opakowanie i wdrażanie zasobów](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)|W tym artykule opisano model gwiazdy używający programu .NET Framework do pakietu i wdrażanie zasobów; obejmuje zasobów nazewnictwa konwencje, proces rezerwowy i pakowania alternatyw.|  
|[Wdrażanie aplikacji międzyoperacyjnych](../../../docs/framework/interop/deploying-an-interop-application.md)|Wyjaśniono, jak wysłać i zainstaluj międzyoperacyjnego aplikacji, które zwykle obejmują zestawu klienta .NET Framework, jeden lub więcej zestawów międzyoperacyjnych reprezentujących różne biblioteki typów COM, i co najmniej jeden zarejestrowany składników COM.|  
|[Instrukcje: Pobieranie danych o postępie z Instalatora .NET Framework 4.5](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)|Opisuje sposób dyskretnie uruchamianie i śledzić proces instalacji platformy .NET Framework podczas pokazywania widoku postęp instalacji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Podręcznik programowania](../../../docs/framework/development-guide.md)
