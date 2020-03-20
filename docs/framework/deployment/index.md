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
ms.openlocfilehash: b1ba9810b4b0d5a1688318db1093a9ce9bdf8fda
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75716463"
---
# <a name="deploying-the-net-framework-and-applications"></a>Wdrażanie programu .NET Framework i aplikacji

Ten artykuł ułatwia rozpoczęcie wdrażania programu .NET Framework za pomocą aplikacji. Większość informacji jest przeznaczona dla deweloperów, producentów OEM i administratorów przedsiębiorstwa. Użytkownicy, którzy chcą zainstalować program .NET Framework na swoich komputerach, powinni przeczytać artykuł [Instalowanie programu .NET Framework](../install/index.md).

## <a name="key-deployment-resources"></a>Kluczowe zasoby wdrażania

Skorzystaj z poniższych łączy do innych tematów msdn, aby uzyskać szczegółowe informacje na temat wdrażania i obsługi programu .NET Framework.

**Konfiguracja i wdrażanie**

- Ogólne informacje o instalatorze i wdrożeniu:

  - Opcje instalatora:

    - [Instalator sieci Web](../install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)

    - [Instalator w trybie offline](../install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)

  - Tryby instalacji:

    - [Instalacja w trybie dyskretnym](deployment-guide-for-developers.md#chaining_custom)

    - [Wyświetlanie interfejsu użytkownika](deployment-guide-for-developers.md#chaining_default)

  - [Redukcja ponownego uruchamiania systemu podczas instalacji programu .NET Framework 4.5](reducing-system-restarts.md)

  - [Rozwiązywanie problemów z zablokowaną instalacją i odinstalowywaniem programu .NET Framework](../install/troubleshoot-blocked-installations-and-uninstallations.md)

- Wdrażanie programu .NET Framework za pomocą aplikacji klienckiej (dla deweloperów):

  - [Korzystanie z installshield](deployment-guide-for-developers.md#installshield-deployment) w projekcie instalacji i wdrażania

  - [Korzystanie z aplikacji ClickOnce programu Visual Studio](deployment-guide-for-developers.md#clickonce-deployment)

  - [Tworzenie pakietu instalacyjnego WiX](deployment-guide-for-developers.md#wix)

  - [Korzystanie z instalatora niestandardowego](deployment-guide-for-developers.md#chaining)

  - [Dodatkowe informacje](deployment-guide-for-developers.md) dla deweloperów

- Wdrażanie programu .NET Framework (dla pracowników OEM i administratorów):

  - [Zestaw Windows Assessment and Deployment Kit (ADK)](https://go.microsoft.com/fwlink/p/?LinkId=254976)

  - [Przewodnik administratora](guide-for-administrators.md)

**Obsługa techniczna**

- Aby uzyskać ogólne informacje, zobacz [blog programu .NET Framework](https://devblogs.microsoft.com/dotnet/).

- [Wykrywanie wersji](../migration-guide/how-to-determine-which-versions-are-installed.md)

- [Wykrywanie dodatków Service Pack i aktualizacji](../migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)

## <a name="features-that-simplify-deployment"></a>Funkcje, które upraszczają wdrażanie

Program .NET Framework udostępnia szereg podstawowych funkcji ułatwiające wdrażanie aplikacji:

- Aplikacje bez wpływu.

     Ta funkcja zapewnia izolację aplikacji i eliminuje konflikty DLL. Domyślnie składniki nie mają wpływu na inne aplikacje.

- Składniki prywatne domyślnie.

     Domyślnie składniki są wdrażane w katalogu aplikacji i są widoczne tylko dla aplikacji zawierającej.

- Kontrolowane udostępnianie kodu.

     Udostępnianie kodu wymaga jawnego udostępnienia kodu do udostępniania, a nie zachowania domyślnego.

- Przechowywanie wersji obok siebie.

     Wiele wersji składnika lub aplikacji może współistnieć, można wybrać, które wersje do użycia, a środowisko wykonawcze języka wspólnego wymusza zasady przechowywania wersji.

- XCOPY wdrożenia i replikacji.

     Samodzielnie opisane i samodzielne składniki i aplikacje mogą być wdrażane bez wpisów rejestru lub zależności.

- Aktualizacje w locie.

     Administratorzy mogą używać hostów, takich jak ASP.NET, do aktualizowania bibliotek DLL programu, nawet na komputerach zdalnych.

- Integracja z Instalatorem Windows.

     Anons, publikowanie, naprawa i instalowanie na żądanie są dostępne podczas wdrażania aplikacji.

- Wdrożenie w przedsiębiorstwie.

     Ta funkcja zapewnia łatwą dystrybucję oprogramowania, w tym korzystanie z usługi Active Directory.

- Pobieranie i buforowanie.

     Pobieranie przyrostowe zmniejsza pobieranie, a składniki mogą być izolowane do użytku tylko przez aplikację do wdrażania o niskim wpływie.

- Częściowo zaufany kod.

     Tożsamość jest oparta na kodzie zamiast użytkownika i nie są wyświetlane żadne okna dialogowe certyfikatu.

## <a name="packaging-and-distributing-net-framework-applications"></a>Pakowanie i dystrybucja aplikacji .NET Framework

Niektóre informacje o pakowaniu i wdrażaniu programu .NET Framework są opisane w innych sekcjach dokumentacji. Te sekcje zawierają informacje o jednostek samookryzyskujących o nazwie [zestawy](../../standard/assembly/index.md), które nie wymagają wpisów rejestru, [zestawy o silnych nazwach](../../standard/assembly/strong-named.md), które zapewniają unikatowość nazwy i zapobiegają fałszowaniu nazw i [przechowywanie wersji zestawu,](../../standard/assembly/versioning.md)co rozwiązuje wiele problemów związanych z konfliktami biblioteki DLL. Poniższe sekcje zawierają informacje dotyczące pakowania i dystrybucji aplikacji .NET Framework.

### <a name="packaging"></a>Tworzenie pakietów

Program .NET Framework udostępnia następujące opcje dla aplikacji do pakowania:

- Jako pojedynczy zestaw lub jako zbiór zestawów.

     Dzięki tej opcji wystarczy użyć plików .dll lub .exe, które zostały zbudowane.

- Jako szafka (CAB).

     Ta opcja umożliwia kompresowanie plików do plików cab w celu zmniejszenia czasu dystrybucji lub pobierania.

- Jako pakiet Instalatora Windows lub w innych formatach instalatora.

     Za pomocą tej opcji można utworzyć pliki msi do użytku z Instalatorem Windows lub spakować aplikację do użycia z innym instalatorem.

### <a name="distribution"></a>Dystrybucja

Program .NET Framework udostępnia następujące opcje dystrybucji aplikacji:

- Użyj XCOPY lub FTP.

     Ponieważ aplikacje środowiska wykonawczego języka wspólnego są samoopisujące i nie wymagają żadnych wpisów rejestru, można użyć XCOPY lub FTP, aby po prostu skopiować aplikację do odpowiedniego katalogu. Aplikację można następnie uruchomić z tego katalogu.

- Użyj pobierania kodu.

     Jeśli rozprowadzasz aplikację przez Internet lub za pośrednictwem firmowego intranetu, możesz po prostu pobrać kod na komputer i uruchomić aplikację.

- Użyj programu instalacyjnego, takiego jak Instalator Windows 2.0.

     Instalator Windows 2.0 może instalować, naprawiać lub usuwać zestawy programu .NET Framework w globalnej pamięci podręcznej zestawów i w katalogach prywatnych.

### <a name="installation-location"></a>Lokalizacja instalacji

Aby określić, gdzie wdrożyć zestawy aplikacji, aby można je było znaleźć w czasie wykonywania, zobacz [Jak środowisko wykonawcze lokalizuje zestawy](how-the-runtime-locates-assemblies.md).

Zagadnienia dotyczące zabezpieczeń mogą również mieć wpływ na sposób wdrażania aplikacji. Uprawnienia zabezpieczeń są przyznawane kodowi zarządzanego zgodnie z miejscem, w którym znajduje się kod. Wdrażanie aplikacji lub składnika w lokalizacji, w której otrzymuje niewielkie zaufanie, takie jak Internet, ogranicza to, co może zrobić aplikacja lub składnik. Aby uzyskać więcej informacji na temat zagadnień dotyczących wdrażania i zabezpieczeń, zobacz [Podstawy zabezpieczeń dostępu do kodu](../misc/code-access-security-basics.md).

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](how-the-runtime-locates-assemblies.md)|W tym artykule opisano, jak środowisko uruchomieniowe języka wspólnego określa, który zestaw do użycia do spełnienia żądania powiązania.|
|[Najlepsze praktyki dotyczące ładowania zestawu](best-practices-for-assembly-loading.md)|W tym artykule omówiono sposoby <xref:System.InvalidCastException>unikania problemów z tożsamością typu, które mogą prowadzić do , <xref:System.MissingMethodException>i innych błędów.|
|[Zmniejszenie liczby ponownych uruchomień systemu podczas instalowania programu .NET Framework 4.5](reducing-system-restarts.md)|W tym artykule opisano Menedżera ponownego uruchamiania, który zapobiega ponownemu uruchomieniu, gdy jest to możliwe, i wyjaśniono, jak aplikacje, które instalują program .NET Framework mogą z niego korzystać.|
|[Przewodnik wdrażania dla administratorów](guide-for-administrators.md)|W tym artykule wyjaśniono, jak administrator systemu może wdrażać program .NET Framework i jego zależności systemowe w sieci przy użyciu programu Microsoft Endpoint Configuration Manager.|
|[Przewodnik wdrażania dla deweloperów](deployment-guide-for-developers.md)|W tym artykule wyjaśniono, jak deweloperzy mogą instalować program .NET Framework na komputerach swoich użytkowników za pomocą aplikacji.|
|[Wdrażanie aplikacji, usług i składników](/visualstudio/deployment/deploying-applications-services-and-components)|W tym artykule omówiono opcje wdrażania w programie Visual Studio, w tym instrukcje dotyczące publikowania aplikacji przy użyciu technologii ClickOnce i Windows Installer.|
|[Publikowanie aplikacji ClickOnce](/visualstudio/deployment/publishing-clickonce-applications)|W tym artykule opisano sposób pakowania aplikacji Windows Forms i wdrażania jej za pomocą funkcji ClickOnce na komputerach klienckich w sieci.|
|[Opakowanie i wdrażanie zasobów](../resources/packaging-and-deploying-resources-in-desktop-apps.md)|W tym artykule opisano model koncentratora i szprychy, który jest używany przez program .NET Framework do pakowania i wdrażania zasobów; obejmuje konwencje nazewnictwa zasobów, proces rezerwowy i alternatywy pakowania.|
|[Wdrażanie aplikacji międzyoperacyjnych](../interop/deploying-an-interop-application.md)|W tym artykule wyjaśniono, jak wysyłać i instalować aplikacje interop, które zazwyczaj obejmują zestaw klienta .NET Framework, jeden lub więcej zestawów międzyoperacyjnych reprezentujących odrębne biblioteki typu COM i jeden lub więcej zarejestrowanych składników COM.|
|[Porady: pobieranie danych o postępie z Instalatora .NET Framework 4.5](how-to-get-progress-from-the-dotnet-installer.md)|W tym artykule opisano sposób dyskretnego uruchamiania i śledzenia procesu instalacji programu .NET Framework, podczas gdy wyświetlany jest własny widok postępu instalacji.|

## <a name="see-also"></a>Zobacz też

- [Podręcznik programowania](../development-guide.md)
