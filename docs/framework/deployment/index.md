---
title: Wdrażanie programu .NET Framework i aplikacji
ms.date: 03/30/2017
helpviewer_keywords:
- deploying applications [.NET Framework], packaging
- deploying applications [.NET Framework]
- deploying applications [.NET Framework], features
- deploying applications [.NET Framework], distribution
- .NET Framework, deploying
- .NET Framework application deployment
ms.assetid: 238d8284-6042-4a38-a7f6-1ee8efd719da
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a650fa0340ce63a573074746eef60994e2254c86
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2018
ms.locfileid: "49453232"
---
# <a name="deploying-the-net-framework-and-applications"></a>Wdrażanie programu .NET Framework i aplikacji
Ten artykuł pomoże rozpocząć wdrażanie programu .NET Framework z aplikacją. Większość informacji jest przeznaczona dla deweloperów, producentów OEM i Administratorzy przedsiębiorstwa. Użytkownicy, którzy chcą zainstalować program .NET Framework na swoich komputerach powinni przeczytać [Instalowanie programu .NET Framework](~/docs/framework/install/index.md).  
  
## <a name="key-deployment-resources"></a>Zasoby dotyczące wdrażania klucza  
 Informacje na temat wdrażania i obsługi programu .NET Framework, należy użyć następujących łączy do innych tematów MSDN.  
  
 **Instalacja i wdrożenie**  
  
-   Informacje ogólne Instalatora i wdrażania:  
  
    -   Opcje Instalatora:  
  
        -   [Instalator sieci Web](~/docs/framework/install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)  
  
        -   [Instalator w trybie offline](~/docs/framework/install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)  
  
    -   Tryby instalacji:  
  
        -   [Instalacja dyskretna](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining_custom)  
  
        -   [Wyświetlanie interfejsu użytkownika](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining_default)  
  
    -   [Zmniejszenie liczby system ponownych uruchomień podczas instalowania programu .NET Framework 4.5](../../../docs/framework/deployment/reducing-system-restarts.md)  
  
    -   [Rozwiązywanie problemów z zablokowaną instalacją i odinstalowywaniem programu .NET Framework](~/docs/framework/install/troubleshoot-blocked-installations-and-uninstallations.md)  
  
-   Wdrażanie programu .NET Framework z aplikacją klienta (dla deweloperów):  
  
    -   [Za pomocą programu InstallShield](../../../docs/framework/deployment/deployment-guide-for-developers.md#installshield-deployment) w projekcie instalacja i wdrożenie  
  
    -   [Za pomocą aplikacji Visual Studio ClickOnce](../../../docs/framework/deployment/deployment-guide-for-developers.md#clickonce-deployment)  
  
    -   [Tworzenie pakietu instalacyjnego WiX](../../../docs/framework/deployment/deployment-guide-for-developers.md#wix)  
  
    -   [Za pomocą niestandardowego Instalatora](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining)  
  
    -   [Dodatkowe informacje](../../../docs/framework/deployment/deployment-guide-for-developers.md) dla deweloperów  
  
-   Wdrażanie programu .NET Framework (dla producentów OEM i administratorów):  
  
    -   [Windows Assessment and Deployment Kit (ADK)](https://go.microsoft.com/fwlink/p/?LinkId=254976)  
  
    -   [Podręcznik administratora](../../../docs/framework/deployment/guide-for-administrators.md)  
  
 **Obsługa techniczna**  
  
-   Aby uzyskać ogólne informacje, zobacz [blog programu .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=254977)  
  
-   [Wykrywania wersji](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)  
  
-   [Wykrywanie, dodatki service pack i aktualizacje](../../../docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)  
  
## <a name="features-that-simplify-deployment"></a>Funkcje, które upraszczają wdrożenia  
 .NET Framework oferuje podstawowe funkcje, które ułatwiają wdrażanie aplikacji:  
  
-   Aplikacje bez zakłócania normalnej.  
  
     Ta funkcja zapewnia izolację aplikacji i eliminuje konflikty biblioteki DLL. Domyślnie składniki nie wpływać na inne aplikacje.  
  
-   Składniki prywatnej domyślnie.  
  
     Domyślnie składniki są wdrażane w katalogu aplikacji i są widoczne tylko dla aplikacji zawierających.  
  
-   Kontrolowane, udostępniania kodu.  
  
     Udostępnianie kodu wymaga jawnego udostępniania kodu na potrzeby udostępniania zamiast domyślnego zachowania.  
  
-   Przechowywanie wersji obok siebie.  
  
     Wiele wersji składnika lub aplikacji mogą współistnieć, można wybrać, które wersje do użycia i środowisko uruchomieniowe języka wspólnego wymusza zasady przechowywania wersji.  
  
-   Umożliwia wdrażanie XCOPY i replikacji.  
  
     Składniki własnym opisem, niezależna i aplikacje mogą być wdrażane bez wpisów rejestru lub zależności.  
  
-   Aktualizacje na bieżąco.  
  
     Administratorzy mogą używać hostów, takich jak ASP.NET, aby zaktualizować program bibliotek DLL, nawet na komputerach zdalnych.  
  
-   Integracja z Instalatora Windows.  
  
     Anons, publikowania, naprawy i instalacji na żądanie są dostępne w przypadku wdrażania aplikacji.  
  
-   Wdrażanie w przedsiębiorstwie.  
  
     Ta funkcja zapewnia dystrybucja oprogramowania proste, w tym o korzystaniu z usługi Active Directory.  
  
-   Pobieranie i buforowania.  
  
     Przyrostowe pobieranie zachować mniejsze pliki do pobrania i składniki mogą być izolowane do użytku tylko przez aplikację na potrzeby o niskim wpływie na wdrożenie.  
  
-   Częściowo zaufanego kodu.  
  
     Tożsamość jest oparty na kodzie, zamiast użytkownika, a nie certyfikat okien dialogowych.  
  
## <a name="packaging-and-distributing-net-framework-applications"></a>Pakowanie i rozpowszechnianie aplikacji .NET Framework  
 Niektóre pakowania i informacje na temat wdrażania programu .NET Framework jest opisany w innych sekcji dokumentacji. Te sekcje zawierają informacje o samoopisujące jednostki o nazwie [zestawy](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md), które nie wymagają żadnych wpisów rejestru [zestawy o silnych nazwach](../../../docs/framework/app-domains/strong-named-assemblies.md), która zapewnić unikatowość nazwy i zapobiec nazwy fałszowanie adresów, a [przechowywanie wersji zestawu](../../../docs/framework/app-domains/assembly-versioning.md), która rozwiązuje wiele problemów związanych z konflikty biblioteki DLL. Poniższe sekcje zawierają informacje dotyczące tworzenia pakietów i rozpowszechnianie aplikacji programu .NET Framework.  
  
### <a name="packaging"></a>Tworzenie pakietów  
 .NET Framework zawiera następujące opcje dla pakietu aplikacji:  
  
-   Jako pojedynczy zestaw lub kolekcję zestawów.  
  
     Po wybraniu tej opcji możesz po prostu użyć pliki .dll i .exe, ponieważ zostały skompilowane.  
  
-   Jako pliki cabinet (CAB).  
  
     Po wybraniu tej opcji Kompresuj pliki na pliki cab dystrybucji lub pobrać mniej czasochłonne.  
  
-   Jako pakiet Instalatora Windows lub w innych formatach Instalatora.  
  
     Po wybraniu tej opcji tworzenia pliku .msi do użycia przy użyciu Instalatora Windows lub pakietu aplikacji do użytku z niektórych innych Instalatora.  
  
### <a name="distribution"></a>Dystrybucji  
 .NET Framework zawiera następujące opcje dystrybucji aplikacji:  
  
-   Za pomocą polecenia XCOPY lub FTP.  
  
     Ponieważ typowych aplikacji środowiska uruchomieniowego języka są samoopisujące i wymagają żadnych wpisów rejestru, można użyć polecenia XCOPY lub FTP można po prostu skopiować ją do odpowiedniego katalogu. Aplikacja może następnie uruchamiana z tego katalogu.  
  
-   Za pomocą pobierania kodu.  
  
     Jeśli aplikacja jest rozpowszechniana przez Internet lub za pomocą firmowego intranetu, można po prostu pobrać kod na komputerze i uruchamiania aplikacji istnieje.  
  
-   Użyj programu instalacyjnego, takich jak Instalator Windows w wersji 2.0.  
  
     Instalator Windows w wersji 2.0 można zainstalować, naprawę lub usunięcie zestawów .NET Framework, w globalnej pamięci podręcznej i prywatne katalogów.  
  
### <a name="installation-location"></a>Lokalizacja instalacji  
 Aby określić miejsce wdrażania zestawów Twojej aplikacji, dzięki czemu można je znaleźć w czasie wykonywania, zobacz [jak środowisko uruchomieniowe lokalizuje zestawy](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
 Zagadnienia dotyczące zabezpieczeń może także mieć wpływ na sposób wdrażania aplikacji. Uprawnienia zabezpieczeń są przyznawane kodu zarządzanego, zgodnie z którym znajduje się kod. Wdrażanie aplikacji lub składnika do lokalizacji, w której otrzymuje nieco zaufania, na przykład Internet, limity aplikacji lub składnika czynności. Aby uzyskać więcej informacji dotyczących wdrażania i zagadnienia dotyczące zabezpieczeń, zobacz [podstawy zabezpieczeń dostępu kodu](../../../docs/framework/misc/code-access-security-basics.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)|W tym artykule opisano, jak środowisko uruchomieniowe języka wspólnego Określa, które zestawu do używania w celu spełnienia żądania powiązania.|  
|[Najlepsze praktyki dotyczące ładowania zestawu](../../../docs/framework/deployment/best-practices-for-assembly-loading.md)|W tym artykule omówiono sposób, aby uniknąć problemów tożsamości typu, który może prowadzić do <xref:System.InvalidCastException>, <xref:System.MissingMethodException>i inne błędy.|  
|[Zmniejszenie liczby ponownych uruchomień systemu podczas instalowania programu .NET Framework 4.5](../../../docs/framework/deployment/reducing-system-restarts.md)|W tym artykule opisano Menedżera ponownego uruchamiania co uniemożliwia ponowne uruchomienie, jeśli to możliwe i wyjaśniono, jak aplikacje, zainstaluj program .NET Framework, które można z niej korzystać.|  
|[Przewodnik wdrażania dla administratorów](../../../docs/framework/deployment/guide-for-administrators.md)|W tym artykule wyjaśniono, jak administrator systemu może wdrożyć środowiska .NET Framework i jego zależności systemowe przez sieć przy użyciu programu System Center Configuration Manager (SCCM).|  
|[Przewodnik wdrażania dla deweloperów](../../../docs/framework/deployment/deployment-guide-for-developers.md)|W tym artykule wyjaśniono, jak deweloperzy mogą zainstalować program .NET Framework na komputerach swoich użytkowników przy użyciu swoich aplikacji.|  
|[Wdrażanie aplikacji, usług i składników](/visualstudio/deployment/deploying-applications-services-and-components)|W tym artykule omówiono opcje wdrażania w programie Visual Studio, w tym instrukcje dotyczące publikowania aplikacji przy użyciu technologii ClickOnce i Instalator Windows.| 
|[Publikowanie aplikacji ClickOnce](/visualstudio/deployment/publishing-clickonce-applications)|Opis pakietu aplikacji Windows Forms i wdrożyć ją za pomocą technologii ClickOnce do komputerów klienckich w sieci.|  
|[Opakowanie i wdrażanie zasobów](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)|W tym artykule opisano model gwiazdy, który używa programu .NET Framework w celu pakowanie i wdrażanie zasobów. opisano konwencje nazewnictwa, proces rezerwowy i alternatywne opakowanie zasobów.|  
|[Wdrażanie aplikacji międzyoperacyjnych](../../../docs/framework/interop/deploying-an-interop-application.md)|Wyjaśnia, jak dostarczanie i zainstaluj aplikacje współdziałania, obejmujących zazwyczaj zestawie klienta programu .NET Framework jednego lub więcej zestawów międzyoperacyjnych reprezentująca różne biblioteki typów COM, i co najmniej jeden zarejestrowany składnik COM.|  
|[Instrukcje: Pobieranie danych o postępie z Instalatora .NET Framework 4.5](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)|Opisuje sposób dyskretnie Uruchom i Śledź proces instalacji programu .NET Framework podczas wyświetlania własnego widoku postępu instalacji.|  
  
## <a name="see-also"></a>Zobacz też  
- [Podręcznik programowania](../../../docs/framework/development-guide.md)
