---
title: 'Instrukcje: Konfigurowanie aplikacji do obsługi .NET Framework 4 lub nowszej wersji'
ms.date: 03/30/2017
helpviewer_keywords:
- configuring apps to support .NET Framework
- .NET Framework, configuring apps
ms.assetid: 63c6b9a8-0088-4077-9aa3-521ab7290f79
ms.openlocfilehash: 586f39fc9b50dcd45bb959ebd0063e3c38d9c3ed
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716244"
---
# <a name="how-to-configure-an-app-to-support-net-framework-4-or-later-versions"></a>Instrukcje: Konfigurowanie aplikacji do obsługi .NET Framework 4 lub nowszej wersji

Wszystkie aplikacje obsługujące środowisko uruchomieniowe języka wspólnego (CLR) muszą uruchamiać, lub *aktywować*, środowisko CLR w celu uruchomienia kodu zarządzanego. Zazwyczaj aplikacja programu .NET Framework działa w wersji środowiska CLR, w którym została skompilowana, ale można zmienić to zachowanie dla aplikacji komputerowych, używając pliku konfiguracji aplikacji (czasami określanego jako plik app.config). Przy użyciu pliku konfiguracji aplikacji nie można jednak zmienić domyślnego zachowania aktywacji dla aplikacji do Sklepu Windows lub dla systemu Windows Phone. W tym artykule wyjaśniono, jak umożliwić uruchamianie aplikacji klasycznej w innej wersji .NET Framework i przedstawiono przykład sposobu, w jaki jest przeznaczony dla wersji 4 lub nowszej.

 Wersja programu .NET Framework, w której działa aplikacja, jest określana w następującej kolejności:

- Plik konfiguracji.

     Jeśli plik konfiguracji aplikacji zawiera [\<supportedRuntime >](../configure-apps/file-schema/startup/supportedruntime-element.md) wpisów, które określają jedną lub kilka wersji .NET Framework i jedna z tych wersji jest obecna na komputerze użytkownika, aplikacja jest uruchamiana w tej wersji. Plik konfiguracyjny odczytuje [\<supportedRuntime >](../configure-apps/file-schema/startup/supportedruntime-element.md) wpisów w kolejności, w jakiej są wyświetlane, i używa pierwszej .NET Framework wersji na liście, która jest obecna na komputerze użytkownika. (Użyj [\<requiredRuntime > elementu](../configure-apps/file-schema/startup/requiredruntime-element.md) w wersji 1,0).

- Skompilowana wersja.

     Jeśli nie ma pliku konfiguracji, ale wersja programu .NET Framework, z użyciem której skompilowano aplikację, jest obecna na komputerze użytkownika, aplikacja jest uruchamiana z użyciem tej wersji.

- Najnowsza zainstalowana wersja.

     Jeśli wersja .NET Framework, w której została skompilowana aplikacja, nie jest obecna, a plik konfiguracji nie określa wersji w [elemencie\<supportedRuntime >](../configure-apps/file-schema/startup/supportedruntime-element.md), aplikacja podejmie próbę uruchomienia na najnowszej wersji .NET Framework, która jest obecna na komputerze użytkownika.

     Jednak aplikacje programu .NET Framework 1.0, 1.1, 2.0, 3.0 i 3.5 nie są automatycznie uruchamiane w programie .NET Framework 4 lub nowszym, a w niektórych przypadkach jest wyświetlany błąd i może się pojawić monit o zainstalowanie programu .NET Framework 3.5. Zachowanie aktywacji może także zależeć od systemu operacyjnego użytkownika, ponieważ różne wersje systemu Windows zawierają różne wersje programu .NET Framework. Jeśli aplikacja obsługuje programy .NET Framework 3.5 i 4 lub nowsze, zalecane jest, aby wskazać to za pomocą wielu wpisów w pliku konfiguracji, co pozwoli uniknąć błędów inicjowania programu .NET Framework. Aby uzyskać więcej informacji, zobacz [wersje i zależności](versions-and-dependencies.md).

 Możesz również skonfigurować aplikacje .NET Framework 3,5 do uruchamiania w .NET Framework 4 lub nowszych wersjach, nawet na komputerach, na których zainstalowano .NET Framework 3,5, aby skorzystać z ulepszeń wydajności w wersjach 4 i nowszych.

> [!IMPORTANT]
> Zalecane jest, aby zawsze testować aplikację z każdą wersją programu .NET Framework, która jest obsługiwana. Zobacz [zgodność wersji](version-compatibility.md) , aby uzyskać informacje dotyczące uaktualniania aplikacji do obsługi nowszych wersji .NET Framework.

 Aby uzyskać informacje dotyczące modyfikowania aplikacji .NET Framework 1,0 i 1,1 do obsługi systemów Windows 7 i Windows 8, zobacz [Migrowanie z .NET Framework 1,1](migrating-from-the-net-framework-1-1.md).

## <a name="to-configure-your-app-to-run-on-the-net-framework-4-or-later-versions"></a>Aby skonfigurować aplikację do uruchamiania w .NET Framework 4 lub nowszych wersjach

1. Dodaj lub zlokalizuj plik konfiguracji projektu programu .NET Framework. Plik konfiguracji aplikacji znajduje się w tym samym katalogu i ma taką samą nazwę jak aplikacja, ale ma rozszerzenie .config. Na przykład dla aplikacji o nazwie MyExecutable.exe plik konfiguracji aplikacji ma nazwę MyExecutable.exe.config.

     Aby dodać plik konfiguracji, na pasku menu programu Visual Studio wybierz **projekt**, **Dodaj nowy element**. W okienku po lewej stronie wybierz pozycję **Ogólne** , a następnie wybierz pozycję **plik konfiguracji**. Nazwij plik konfiguracji *nazwa_aplikacji*. exe. config. Te opcje menu nie są dostępne dla projektów aplikacji ze sklepu Windows lub aplikacji systemu Windows Phone, ponieważ nie można zmienić zasad aktywacji na tych platformach.

2. Dodaj element [\<supportedRuntime >](../configure-apps/file-schema/startup/supportedruntime-element.md) w następujący sposób do pliku konfiguracji aplikacji:

    ```xml
    <configuration>
      <startup>
        <supportedRuntime version="<version>"/>
      </startup>
    </configuration>
    ```

     gdzie *\<wersja >* określa wersję środowiska CLR, która jest wyrównana do wersji .NET Framework obsługiwanej przez aplikację. Użyj następujących ciągów:

    - .NET Framework 1.0: "v1.0.3705"

    - .NET Framework 1.1: "v1.1.4322"

    - .NET Framework 2.0, 3.0 i 3.5: "v2.0.50727"

    - .NET Framework 4 i nowsze wersje: "v 4.0"

     Aby określić obsługę wielu wersji .NET Framework, można dodać wiele [\<elementów > supportedRuntime](../configure-apps/file-schema/startup/supportedruntime-element.md) .

 W poniższej tabeli pokazano, jak na podstawie ustawień w pliku konfiguracji aplikacji i wersji programu .NET Framework zainstalowanych na komputerze można ustalić wersję, w której będzie działać aplikacja przeznaczona dla środowiska .NET Framework 3.5. Przykłady są specyficzne dla aplikacji programu .NET Framework 3.5, ale można używać podobnej logiki w przypadku aplikacjach docelowych, które zostały skompilowane z użyciem starszych wersji programu .NET Framework. Należy zauważyć, że numer wersji programu .NET Framework 2.0 (v2.0.50727) jest używany do określenia programu .NET Framework 3.5 w pliku konfiguracji aplikacji.

|Ustawienie w pliku App.config|Na komputerze z zainstalowaną wersją 3.5|Na komputerze z zainstalowanymi wersjami 3,5 i 4 lub nowszymi wersjami|Na komputerze z zainstalowaną wersją 4 lub nowszą|
|-|-|-|-|
|Brak|Działa w wersji 3.5|Działa w wersji 3.5|Wyświetla komunikat o błędzie, który monituje użytkownika o zainstalowanie poprawnej wersji *|
|`<supportedRuntime version="v2.0.50727"/>`|Działa w wersji 3.5|Działa w wersji 3.5|Wyświetla komunikat o błędzie, który monituje użytkownika o zainstalowanie poprawnej wersji *|
|`<supportedRuntime version="v2.0.50727"/>` <br /> `<supportedRuntime version="v4.0"/>`|Działa w wersji 3.5|Działa w wersji 3.5|Działa w wersji 4 lub nowszej|
|`<supportedRuntime version="v4.0"/>` <br /> `<supportedRuntime version="v2.0.50727"/>`|Działa w wersji 3.5|Działa w wersji 4 lub nowszej|Działa w wersji 4 lub nowszej|
|`<supportedRuntime version="v4.0"/>`|Wyświetla komunikat o błędzie, który monituje użytkownika o zainstalowanie poprawnej wersji *|Działa w wersji 4 lub nowszej|Działa w wersji 4 lub nowszej|

 \* Aby uzyskać więcej informacji o tym komunikacie o błędzie i sposobach ich unikania, zobacz [.NET Framework Błędy inicjowania: Zarządzanie czynnościami użytkownika](../deployment/initialization-errors-managing-the-user-experience.md).

## <a name="see-also"></a>Zobacz także

- [Migracja z programu .NET Framework 1.1](migrating-from-the-net-framework-1-1.md)
- [Przewodnik migracji](index.md)
