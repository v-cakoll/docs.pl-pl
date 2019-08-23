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
ms.openlocfilehash: e7da023c5ab9247cde0ccd1126d4d639c6f355e7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910971"
---
# <a name="deploying-the-net-framework-and-applications"></a>Wdrażanie programu .NET Framework i aplikacji

Ten artykuł pomoże Ci rozpocząć wdrażanie .NET Framework przy użyciu aplikacji. Większość informacji jest przeznaczona dla deweloperów, producentów OEM i administratorów przedsiębiorstwa. Użytkownicy, którzy chcą zainstalować .NET Framework na swoich komputerach, powinni przeczytać [instalowanie .NET Framework](../install/index.md).

## <a name="key-deployment-resources"></a>Zasoby wdrażania kluczy

Skorzystaj z poniższych linków do innych tematów MSDN, aby uzyskać szczegółowe informacje na temat wdrażania i obsługi .NET Framework.

**Instalacja i wdrożenie**

- Ogólne informacje o instalacji i wdrożeniu:

  - Opcje Instalatora:

    - [Instalator sieci Web](../install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)

    - [Instalator w trybie offline](../install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)

  - Tryby instalacji:

    - [Instalacja dyskretna](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining_custom)

    - [Wyświetlanie interfejsu użytkownika](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining_default)

  - [Zmniejszenie liczby ponownych uruchomień systemu podczas instalacji .NET Framework 4,5](../../../docs/framework/deployment/reducing-system-restarts.md)

  - [Rozwiązywanie problemów z zablokowaną instalacją i odinstalowywaniem programu .NET Framework](../install/troubleshoot-blocked-installations-and-uninstallations.md)

- Wdrażanie .NET Framework za pomocą aplikacji klienckiej (dla deweloperów):

  - [Korzystanie z InstallShield](../../../docs/framework/deployment/deployment-guide-for-developers.md#installshield-deployment) w projekcie instalacji i wdrażania

  - [Korzystanie z aplikacji ClickOnce programu Visual Studio](../../../docs/framework/deployment/deployment-guide-for-developers.md#clickonce-deployment)

  - [Tworzenie pakietu instalacyjnego WiX](../../../docs/framework/deployment/deployment-guide-for-developers.md#wix)

  - [Używanie instalatora niestandardowego](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining)

  - [Dodatkowe informacje](../../../docs/framework/deployment/deployment-guide-for-developers.md) dla deweloperów

- Wdrażanie .NET Framework (dla producentów OEM i administratorów):

  - [Zestaw do oceny i wdrażania systemu Windows (ADK)](https://go.microsoft.com/fwlink/p/?LinkId=254976)

  - [Podręcznik administratora](../../../docs/framework/deployment/guide-for-administrators.md)

**Obsługa techniczna**

- Aby uzyskać ogólne informacje, zobacz [blog .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=254977)

- [Wykrywanie wersji](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)

- [Wykrywanie pakietów usług i aktualizacji](../../../docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)

## <a name="features-that-simplify-deployment"></a>Funkcje upraszczające wdrażanie

.NET Framework udostępnia wiele podstawowych funkcji, które ułatwiają wdrażanie aplikacji:

- Aplikacje bez wpływu.

     Ta funkcja zapewnia izolację aplikacji i eliminuje konflikty bibliotek DLL. Domyślnie składniki nie wpływają na inne aplikacje.

- Składniki prywatne domyślnie.

     Domyślnie składniki są wdrażane w katalogu aplikacji i są widoczne tylko dla aplikacji zawierającej.

- Kontrolowane udostępnianie kodu.

     Udostępnianie kodu wymaga jawnego udostępnienia kodu do udostępnienia zamiast zachowania domyślnego.

- Przechowywanie wersji równoległych.

     Wiele wersji składnika lub aplikacji może współistnieć, możesz wybrać wersje, które mają być używane, a środowisko uruchomieniowe języka wspólnego wymusza zasady przechowywania wersji.

- Wdrażanie i replikacja polecenia XCOPY.

     Samodzielne i samodzielne składniki i aplikacje można wdrażać bez wpisów lub zależności rejestru.

- Aktualizacje na bieżąco.

     Administratorzy mogą używać hostów, takich jak ASP.NET, do aktualizowania bibliotek DLL programu, nawet na komputerach zdalnych.

- Integracja z Instalator Windows.

     Podczas wdrażania aplikacji są dostępne anonse, publikowanie, naprawa i instalacja na żądanie.

- Wdrażanie w przedsiębiorstwie.

     Ta funkcja zapewnia łatwą dystrybucję oprogramowania, w tym za pomocą Active Directory.

- Pobieranie i buforowanie.

     Pobieranie przyrostowe zachowuje mniejsze ilości plików, a składniki mogą być izolowane do użytku tylko przez aplikację w przypadku wdrożenia o niskim wpływie.

- Kod częściowo zaufany.

     Tożsamość jest oparta na kodzie zamiast użytkownika i nie pojawiają się okna dialogowe certyfikatu.

## <a name="packaging-and-distributing-net-framework-applications"></a>Pakowanie i dystrybucja .NET Framework aplikacji

Niektóre informacje dotyczące pakowania i wdrażania dla .NET Framework są opisane w innych sekcjach dokumentacji. Te sekcje zawierają informacje o samoopisywanych jednostkach nazywanych [zestawami](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md), które nie wymagają wpisów rejestru, [zestawów o silnych nazwach](../../../docs/framework/app-domains/strong-named-assemblies.md), które zapewniają unikatowość nazw i uniemożliwiają fałszowanie nazw oraz [przechowywanie wersji zestawu](../../../docs/framework/app-domains/assembly-versioning.md) , który dotyczy wielu problemów związanych z konfliktami DLL. Poniższe sekcje zawierają informacje o pakowaniu i dystrybucji aplikacji .NET Framework.

### <a name="packaging"></a>Pakowanie

.NET Framework udostępnia następujące opcje dla aplikacji pakietów:

- Jako pojedynczy zestaw lub zbiór zestawów.

     Po wybraniu tej opcji wystarczy użyć plików. dll lub. exe, ponieważ zostały one skompilowane.

- Jako pliki cabinet (CAB).

     W przypadku tej opcji kompresujesz pliki do plików CAB, aby dokonać dystrybucji lub pobrać mniej czasochłonne.

- Jako pakiet Instalator Windows lub w innych formatach Instalatora.

     Za pomocą tej opcji można tworzyć pliki MSI do użycia w Instalator Windows lub spakować aplikację do użycia z innym instalatorem.

### <a name="distribution"></a>Dystrybucja

.NET Framework udostępnia następujące opcje dystrybucji aplikacji:

- Użyj polecenia XCOPY lub FTP.

     Ponieważ aplikacje środowiska uruchomieniowego języka wspólnego nie opisują ani nie wymagają żadnych wpisów rejestru, można użyć polecenia XCOPY lub FTP, aby po prostu skopiować aplikację do odpowiedniego katalogu. Aplikację można następnie uruchomić z tego katalogu.

- Użyj pobierania kodu.

     Jeśli aplikacja jest dystrybuowana przez Internet lub za pośrednictwem firmowej sieci intranet, można po prostu pobrać kod na komputer i uruchomić aplikację.

- Użyj programu Instalatora, takiego jak Instalator Windows 2,0.

     Instalator Windows 2,0 może instalować, naprawiać lub usuwać zestawy .NET Framework w globalnej pamięci podręcznej zestawów i w katalogach prywatnych.

### <a name="installation-location"></a>Lokalizacja instalacji

Aby określić, gdzie wdrożyć zestawy aplikacji, aby można je było znaleźć w środowisku uruchomieniowym, zobacz [jak środowisko uruchomieniowe lokalizuje zestawy](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).

Zagadnienia dotyczące zabezpieczeń mogą również mieć wpływ na sposób wdrażania aplikacji. Uprawnienia zabezpieczeń są udzielane do kodu zarządzanego zgodnie z miejscem, w którym znajduje się kod. Wdrożenie aplikacji lub składnika w lokalizacji, w której odbierze małe zaufanie, takie jak Internet, ogranicza działanie aplikacji lub składnika. Aby uzyskać więcej informacji na temat zagadnień dotyczących wdrażania i zabezpieczeń, zobacz podstawowe informacje o [zabezpieczeniach dostępu kodu](../../../docs/framework/misc/code-access-security-basics.md).

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)|Opisuje, jak środowisko uruchomieniowe języka wspólnego określa zestaw, który ma być używany do realizacji żądania powiązania.|
|[Najlepsze praktyki dotyczące ładowania zestawu](../../../docs/framework/deployment/best-practices-for-assembly-loading.md)|Omawia sposoby, <xref:System.MissingMethodException>aby uniknąć problemów z tożsamością typu, które <xref:System.InvalidCastException>mogą prowadzić do innych błędów.|
|[Zmniejszenie liczby ponownych uruchomień systemu podczas instalowania programu .NET Framework 4.5](../../../docs/framework/deployment/reducing-system-restarts.md)|Opisuje Menedżera ponownego uruchamiania, który uniemożliwia ponowne uruchomienie w miarę możliwości, i wyjaśnia, jak aplikacje instalujące .NET Framework mogą korzystać z tej funkcji.|
|[Przewodnik wdrażania dla administratorów](../../../docs/framework/deployment/guide-for-administrators.md)|Wyjaśnia, w jaki sposób administrator systemu może wdrożyć .NET Framework i zależności systemu w sieci przy użyciu System Center Configuration Manager (SCCM).|
|[Przewodnik wdrażania dla deweloperów](../../../docs/framework/deployment/deployment-guide-for-developers.md)|Wyjaśnia, w jaki sposób deweloperzy mogą instalować .NET Framework na komputerach użytkowników przy użyciu ich aplikacji.|
|[Wdrażanie aplikacji, usług i składników](/visualstudio/deployment/deploying-applications-services-and-components)|W tym artykule omówiono opcje wdrażania w programie Visual Studio, w tym instrukcje dotyczące publikowania aplikacji przy użyciu technologii ClickOnce i Instalator Windows.|
|[Publikowanie aplikacji ClickOnce](/visualstudio/deployment/publishing-clickonce-applications)|Opisuje sposób tworzenia pakietów aplikacji Windows Forms i wdrażania jej przy użyciu technologii ClickOnce na komputerach klienckich w sieci.|
|[Opakowanie i wdrażanie zasobów](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)|Opisuje model gwiazdy, którego .NET Framework używa do pakowania i wdrażania zasobów; obejmuje konwencje nazewnictwa zasobów, proces rezerwowy i alternatywy pakietów.|
|[Wdrażanie aplikacji międzyoperacyjnych](../../../docs/framework/interop/deploying-an-interop-application.md)|Wyjaśnia sposób dostarczania i instalowania aplikacji międzyoperacyjnych, które zwykle zawierają zestaw .NET Framework klienta, co najmniej jeden zestaw międzyoperacyjny reprezentujący różne biblioteki typów modelu COM oraz co najmniej jeden zarejestrowany składnik COM.|
|[Instrukcje: Pobierz postęp z Instalatora .NET Framework 4,5](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)|Opisuje sposób dyskretnego uruchamiania i śledzenia procesu instalacji .NET Framework podczas wyświetlania własnego widoku postępu instalacji.|

## <a name="see-also"></a>Zobacz także

- [Podręcznik programowania](../../../docs/framework/development-guide.md)
