---
title: 'Jak: Konfigurowanie aplikacji do obsługi wersji programu .NET Framework 4 lub nowszych'
ms.date: 03/30/2017
helpviewer_keywords:
- configuring apps to support .NET Framework
- .NET Framework, configuring apps
ms.assetid: 63c6b9a8-0088-4077-9aa3-521ab7290f79
ms.openlocfilehash: 30fb1da8d758b0e8996b4fcdebbb7fbf545a46c1
ms.sourcegitcommit: b75a45f0cfe012b71b45dd9bf723adf32369d40c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80228758"
---
# <a name="how-to-configure-an-app-to-support-net-framework-4-or-later-versions"></a>Jak: Konfigurowanie aplikacji do obsługi wersji programu .NET Framework 4 lub nowszych

Wszystkie aplikacje, które hostują środowisko uruchomieniowe języka wspólnego (CLR) trzeba uruchomić lub *aktywować*, CLR w celu uruchomienia kodu zarządzanego. Zazwyczaj aplikacja programu .NET Framework działa w wersji środowiska CLR, w którym została skompilowana, ale można zmienić to zachowanie dla aplikacji komputerowych, używając pliku konfiguracji aplikacji (czasami określanego jako plik app.config). Przy użyciu pliku konfiguracji aplikacji nie można jednak zmienić domyślnego zachowania aktywacji dla aplikacji do Sklepu Windows lub dla systemu Windows Phone. W tym artykule wyjaśniono, jak włączyć aplikację klasyczną do uruchamiania w innej wersji programu .NET Framework i zawiera przykład sposobu kierowania wersji 4 lub nowszej.

 Wersja programu .NET Framework, w której działa aplikacja, jest określana w następującej kolejności:

- Plik konfiguracji.

     Jeśli plik konfiguracji aplikacji zawiera [ \<obsługiwaneRuntime>](../configure-apps/file-schema/startup/supportedruntime-element.md) wpisy, które określają jedną lub więcej wersji programu .NET Framework, a jedna z tych wersji jest obecna na komputerze użytkownika, aplikacja działa na tej wersji. Plik konfiguracyjny odczytuje [ \<obsługiwaneRuntime>](../configure-apps/file-schema/startup/supportedruntime-element.md) wpisy w kolejności, w jakiej są wymienione i używa pierwszej wersji programu .NET Framework wymienionej na komputerze użytkownika. (Użyj [ \<wymaganego elementu>runtime](../configure-apps/file-schema/startup/requiredruntime-element.md) dla wersji 1.0.)

- Skompilowana wersja.

     Jeśli nie ma pliku konfiguracji, ale wersja programu .NET Framework, z użyciem której skompilowano aplikację, jest obecna na komputerze użytkownika, aplikacja jest uruchamiana z użyciem tej wersji.

- Najnowsza zainstalowana wersja.

     Jeśli wersja programu .NET Framework, na podstawie których została zbudowana aplikacja, nie jest obecna, a plik konfiguracyjny nie określa wersji w [ \<obsługiwanym elementu>Runtime,](../configure-apps/file-schema/startup/supportedruntime-element.md)aplikacja próbuje uruchomić na najnowszej wersji programu .NET Framework, która jest obecna na komputerze użytkownika.

     Jednak aplikacje programu .NET Framework 1.0, 1.1, 2.0, 3.0 i 3.5 nie są automatycznie uruchamiane w programie .NET Framework 4 lub nowszym, a w niektórych przypadkach jest wyświetlany błąd i może się pojawić monit o zainstalowanie programu .NET Framework 3.5. Zachowanie aktywacji może także zależeć od systemu operacyjnego użytkownika, ponieważ różne wersje systemu Windows zawierają różne wersje programu .NET Framework. Jeśli aplikacja obsługuje programy .NET Framework 3.5 i 4 lub nowsze, zalecane jest, aby wskazać to za pomocą wielu wpisów w pliku konfiguracji, co pozwoli uniknąć błędów inicjowania programu .NET Framework. Aby uzyskać więcej informacji, zobacz [Wersje i zależności](versions-and-dependencies.md).

 Można również skonfigurować aplikacje .NET Framework 3.5 do uruchamiania w wersjach .NET Framework 4 lub nowszych, nawet na komputerach z zainstalowanym programem .NET Framework 3.5, aby skorzystać z ulepszeń wydajności w wersjach 4 i nowszych.

> [!IMPORTANT]
> Zalecane jest, aby zawsze testować aplikację z każdą wersją programu .NET Framework, która jest obsługiwana. Zobacz [Zgodność wersji, aby](version-compatibility.md) uzyskać informacje na temat uaktualniania aplikacji do obsługi nowszych wersji programu .NET Framework.

 Aby uzyskać informacje dotyczące modyfikowania aplikacji .NET Framework 1.0 i 1.1 w celu obsługi systemów Windows 7 i Windows 8, zobacz [Migrowanie z programu .NET Framework 1.1](migrating-from-the-net-framework-1-1.md).

## <a name="to-configure-your-app-to-run-on-the-net-framework-4-or-later-versions"></a>Aby skonfigurować aplikację do uruchamiania w wersjach programu .NET Framework 4 lub nowszych

1. Dodaj lub zlokalizuj plik konfiguracji projektu programu .NET Framework. Plik konfiguracji aplikacji znajduje się w tym samym katalogu i ma taką samą nazwę jak aplikacja, ale ma rozszerzenie .config. Na przykład dla aplikacji o nazwie MyExecutable.exe plik konfiguracji aplikacji ma nazwę MyExecutable.exe.config.

     Aby dodać plik konfiguracyjny, na pasku menu programu Visual Studio wybierz pozycję **Project**, **Dodaj nowy element**. Z lewego okienka wybierz pozycję **Ogólne,** a następnie wybierz pozycję **Plik konfiguracji**. Nazwij *plik konfiguracyjny appName*.exe.config. Te opcje menu nie są dostępne dla projektów aplikacji ze Sklepu Windows lub aplikacji dla systemu Windows Phone, ponieważ nie można zmienić zasad aktywacji na tych platformach.

2. Dodaj [ \<obsługiwany element>runtime](../configure-apps/file-schema/startup/supportedruntime-element.md) w następujący sposób do pliku konfiguracji aplikacji:

    ```xml
    <configuration>
      <startup>
        <supportedRuntime version="version"/>
      </startup>
    </configuration>
    ```

     gdzie * \<wersja>* określa wersję CLR, która jest zgodna z wersją programu .NET Framework, która obsługuje aplikację. Użyj następujących ciągów:

    - .NET Framework 1.0: "v1.0.3705"

    - .NET Framework 1.1: "v1.1.4322"

    - .NET Framework 2.0, 3.0 i 3.5: "v2.0.50727"

    - .NET Framework 4 i nowsze wersje: "v4.0"

     Można dodać wiele [ \<obsługiwanychruntime>](../configure-apps/file-schema/startup/supportedruntime-element.md) elementów, wymienione w kolejności preferencji, aby określić obsługę wielu wersji programu .NET Framework.

 W poniższej tabeli pokazano, jak na podstawie ustawień w pliku konfiguracji aplikacji i wersji programu .NET Framework zainstalowanych na komputerze można ustalić wersję, w której będzie działać aplikacja przeznaczona dla środowiska .NET Framework 3.5. Przykłady są specyficzne dla aplikacji programu .NET Framework 3.5, ale można używać podobnej logiki w przypadku aplikacjach docelowych, które zostały skompilowane z użyciem starszych wersji programu .NET Framework. Należy zauważyć, że numer wersji programu .NET Framework 2.0 (v2.0.50727) jest używany do określenia programu .NET Framework 3.5 w pliku konfiguracji aplikacji.

|Ustawienie w pliku App.config|Na komputerze z zainstalowaną wersją 3.5|Na komputerze z zainstalowanymi wersjami 3.5 i 4 lub nowszymi|Na komputerze z zainstalowaną wersją 4 lub nowszą|
|-|-|-|-|
|Brak|Działa w wersji 3.5|Działa w wersji 3.5|Wyświetla komunikat o błędzie, który monituje użytkownika o zainstalowanie poprawnej wersji *|
|`<supportedRuntime version="v2.0.50727"/>`|Działa w wersji 3.5|Działa w wersji 3.5|Wyświetla komunikat o błędzie, który monituje użytkownika o zainstalowanie poprawnej wersji *|
|`<supportedRuntime version="v2.0.50727"/>` <br /> `<supportedRuntime version="v4.0"/>`|Działa w wersji 3.5|Działa w wersji 3.5|Działa w wersjach 4 lub nowszych|
|`<supportedRuntime version="v4.0"/>` <br /> `<supportedRuntime version="v2.0.50727"/>`|Działa w wersji 3.5|Działa w wersjach 4 lub nowszych|Działa w wersjach 4 lub nowszych|
|`<supportedRuntime version="v4.0"/>`|Wyświetla komunikat o błędzie, który monituje użytkownika o zainstalowanie poprawnej wersji *|Działa w wersjach 4 lub nowszych|Działa w wersjach 4 lub nowszych|

 \*Aby uzyskać więcej informacji na temat tego komunikatu o błędzie i sposobów jego uniknięcia, zobacz [Błędy inicjowania programu .NET Framework: Zarządzanie środowiskami użytkownika](../deployment/initialization-errors-managing-the-user-experience.md).

## <a name="see-also"></a>Zobacz też

- [Migracja z programu .NET Framework 1.1](migrating-from-the-net-framework-1-1.md)
- [Przewodnik po migracji](index.md)
