---
title: 'Instrukcje: konfiguracja aplikacji do obsługi programu .NET Framework w wersji 4 lub nowszej'
ms.date: 03/30/2017
helpviewer_keywords:
- configuring apps to support .NET Framework
- .NET Framework, configuring apps
ms.assetid: 63c6b9a8-0088-4077-9aa3-521ab7290f79
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 186297c050d81eca130b751c46303083ff025f22
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636107"
---
# <a name="how-to-configure-an-app-to-support-net-framework-4-or-later-versions"></a>Instrukcje: Konfiguracja aplikacji do obsługi platformy .NET Framework 4 lub nowszy

Wszystkie aplikacje obsługujące środowisko uruchomieniowe języka wspólnego (CLR) muszą uruchamiać, lub *aktywować*, środowisko CLR w celu uruchomienia kodu zarządzanego. Zazwyczaj aplikacja programu .NET Framework działa w wersji środowiska CLR, w którym została skompilowana, ale można zmienić to zachowanie dla aplikacji komputerowych, używając pliku konfiguracji aplikacji (czasami określanego jako plik app.config). Przy użyciu pliku konfiguracji aplikacji nie można jednak zmienić domyślnego zachowania aktywacji dla aplikacji do Sklepu Windows lub dla systemu Windows Phone. W tym artykule wyjaśniono, jak włączyć swoją aplikację do uruchamiania w innej wersji programu .NET Framework i zawiera przykładowy sposób do docelowej wersji 4 lub nowszej.

 Wersja programu .NET Framework, w której działa aplikacja, jest określana w następującej kolejności:

- Plik konfiguracji.

     Jeśli plik konfiguracji aplikacji zawiera [ \<supportedRuntime >](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) wpisów, które określają jedną lub kilka wersji .NET Framework i jedna z tych wersji jest obecna na komputerze użytkownika, aplikacja jest uruchamiana z użyciem tej wersji . Plik konfiguracji odczytuje [ \<supportedRuntime >](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) wpisów w kolejności, w jakiej występują na liście i używa pierwszej wersji .NET Framework na liście, która jest zainstalowana na komputerze użytkownika. (Użyj [ \<requiredRuntime > element](../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) dla wersji 1.0.)

- Skompilowana wersja.

     Jeśli nie ma pliku konfiguracji, ale wersja programu .NET Framework, z użyciem której skompilowano aplikację, jest obecna na komputerze użytkownika, aplikacja jest uruchamiana z użyciem tej wersji.

- Najnowsza zainstalowana wersja.

     Jeśli wersja systemu .NET Framework, która została skompilowana aplikacja, nie jest obecna, a plik konfiguracji nie określa wersji w [ \<supportedRuntime > element](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md), aplikacja próbuje działać w najnowszej wersji programu .NET Struktura, która znajduje się na komputerze użytkownika.

     Jednak aplikacje programu .NET Framework 1.0, 1.1, 2.0, 3.0 i 3.5 nie są automatycznie uruchamiane w programie .NET Framework 4 lub nowszym, a w niektórych przypadkach jest wyświetlany błąd i może się pojawić monit o zainstalowanie programu .NET Framework 3.5. Zachowanie aktywacji może także zależeć od systemu operacyjnego użytkownika, ponieważ różne wersje systemu Windows zawierają różne wersje programu .NET Framework. Jeśli aplikacja obsługuje programy .NET Framework 3.5 i 4 lub nowsze, zalecane jest, aby wskazać to za pomocą wielu wpisów w pliku konfiguracji, co pozwoli uniknąć błędów inicjowania programu .NET Framework. Aby uzyskać więcej informacji, zobacz [wersje i zależności](versions-and-dependencies.md).

 Można również skonfigurować aplikacje 3.5.NET Framework do uruchamiania na .NET Framework 4 lub nowszy, nawet na komputerach, które mają zainstalowany, aby móc zalet usprawnień wydajności w wersji 4 i nowsze wersje programu .NET Framework 3.5.

> [!IMPORTANT]
> Zalecane jest, aby zawsze testować aplikację z każdą wersją programu .NET Framework, która jest obsługiwana. Zobacz [zgodność wersji](version-compatibility.md) informacje dotyczące uaktualniania aplikacji do obsługi nowszych wersji .NET Framework.

 Aby uzyskać informacje dotyczące modyfikowania aplikacji programów .NET Framework 1.0 i 1.1 do obsługi Windows 7 i Windows 8, zobacz [migracji z programu .NET Framework 1.1](migrating-from-the-net-framework-1-1.md).

## <a name="to-configure-your-app-to-run-on-the-net-framework-4-or-later-versions"></a>Aby skonfigurować aplikację do uruchamiania na .NET Framework 4 lub nowszy

1. Dodaj lub zlokalizuj plik konfiguracji projektu programu .NET Framework. Plik konfiguracji aplikacji znajduje się w tym samym katalogu i ma taką samą nazwę jak aplikacja, ale ma rozszerzenie .config. Na przykład dla aplikacji o nazwie MyExecutable.exe plik konfiguracji aplikacji ma nazwę MyExecutable.exe.config.

     Aby dodać plik konfiguracji, na pasku menu programu Visual Studio wybierz **projektu**, **Dodaj nowy element**. Wybierz **ogólne** z okienka po lewej stronie, a następnie wybierz **pliku konfiguracji**. Nadaj plikowi konfiguracji nazwę *appName*. exe.config. Te opcje menu nie są dostępne dla projektów aplikacji do Sklepu Windows lub dla systemu Windows Phone, ponieważ nie można zmienić zasad aktywacji na tych platformach.

2. Dodaj [ \<supportedRuntime >](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) następujący element pliku konfiguracji aplikacji:

    ```xml
    <configuration>
      <startup>
        <supportedRuntime version="<version>"/>
      </startup>
    </configuration>
    ```

     gdzie  *\<wersji >* Określa wersję środowiska CLR pasującą do wersji .NET Framework, którą obsługuje aplikacja. Użyj następujących ciągów:

    - .NET Framework 1.0: "v1.0.3705"

    - .NET Framework 1.1: "v1.1.4322"

    - .NET Framework 2.0, 3.0 i 3.5: "v2.0.50727"

    - .NET framework 4 i nowsze wersje: "v4.0"

     Można dodawać wiele [ \<supportedRuntime >](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) elementy wymienione w kolejności preferencji, aby określić obsługę wielu wersji programu .NET Framework.

 W poniższej tabeli pokazano, jak na podstawie ustawień w pliku konfiguracji aplikacji i wersji programu .NET Framework zainstalowanych na komputerze można ustalić wersję, w której będzie działać aplikacja przeznaczona dla środowiska .NET Framework 3.5. Przykłady są specyficzne dla aplikacji programu .NET Framework 3.5, ale można używać podobnej logiki w przypadku aplikacjach docelowych, które zostały skompilowane z użyciem starszych wersji programu .NET Framework. Należy zauważyć, że numer wersji programu .NET Framework 2.0 (v2.0.50727) jest używany do określenia programu .NET Framework 3.5 w pliku konfiguracji aplikacji.

|Ustawienie w pliku App.config|Na komputerze z zainstalowaną wersją 3.5|Na komputerze z wersjami 3.5 i 4 lub nowszy zainstalowany|Na tym komputerze w wersji 4 lub nowszy zainstalowany|
|-|-|-|-|
|Brak|Działa w wersji 3.5|Działa w wersji 3.5|Wyświetla komunikat o błędzie, który monituje użytkownika o zainstalowanie poprawnej wersji *|
|`<supportedRuntime version="v2.0.50727"/>`|Działa w wersji 3.5|Działa w wersji 3.5|Wyświetla komunikat o błędzie, który monituje użytkownika o zainstalowanie poprawnej wersji *|
|`<supportedRuntime version="v2.0.50727"/>` <br /> `<supportedRuntime version="v4.0"/>`|Działa w wersji 3.5|Działa w wersji 3.5|Działa w wersji 4 lub nowszy|
|`<supportedRuntime version="v4.0"/>` <br /> `<supportedRuntime version="v2.0.50727"/>`|Działa w wersji 3.5|Działa w wersji 4 lub nowszy|Działa w wersji 4 lub nowszy|
|`<supportedRuntime version="v4.0"/>`|Wyświetla komunikat o błędzie, który monituje użytkownika o zainstalowanie poprawnej wersji *|Działa w wersji 4 lub nowszy|Działa w wersji 4 lub nowszy|

 \* Aby uzyskać więcej informacji na temat tego komunikatu o błędzie i sposobów uniknięcia go, zobacz [błędy inicjowania programu .NET Framework: Zarządzanie wrażeniami użytkownika](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md).

## <a name="see-also"></a>Zobacz także

- [Migracja z programu .NET Framework 1.1](migrating-from-the-net-framework-1-1.md)
- [Przewodnik migracji](index.md)
