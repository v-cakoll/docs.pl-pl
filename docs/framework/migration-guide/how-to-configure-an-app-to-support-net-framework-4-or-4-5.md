---
title: "Porady: Konfiguracja aplikacji do obsługi w programie .NET Framework 4 lub 4.5"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring apps to support .NET Framework 4
- .NET Framework 4, configuring apps
- .NET Framework 4.5, configuring apps
ms.assetid: 63c6b9a8-0088-4077-9aa3-521ab7290f79
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4ba3d248dbdd81cf2e2e4445d1e1eb160605542c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-an-app-to-support-net-framework-4-or-45"></a>Porady: Konfiguracja aplikacji do obsługi w programie .NET Framework 4 lub 4.5
Wszystkie aplikacje, które obsługują środowisko uruchomieniowe języka wspólnego (CLR) należy uruchomić, lub *aktywować*, CLR, aby można było uruchamiać kodu zarządzanego. Zazwyczaj aplikacja programu .NET Framework działa w wersji środowiska CLR, w którym została skompilowana, ale można zmienić to zachowanie dla aplikacji komputerowych, używając pliku konfiguracji aplikacji (czasami określanego jako plik app.config). Przy użyciu pliku konfiguracji aplikacji nie można jednak zmienić domyślnego zachowania aktywacji dla aplikacji do Sklepu Windows lub dla systemu Windows Phone. W tym artykule wyjaśniono, jak umożliwić uruchomienie aplikacji komputerowej w innej wersji programu .NET Framework i przedstawiono przykład określania jako platformy docelowej wersji 4 lub 4.5.  
  
 Wersja programu .NET Framework, w której działa aplikacja, jest określana w następującej kolejności:  
  
-   Plik konfiguracji.  
  
     Jeśli plik konfiguracji aplikacji zawiera [ \<supportedRuntime >](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) wpisów, które określają jedną lub kilka wersji .NET Framework i jednej z tych wersji znajduje się na komputerze użytkownika, aplikacja jest uruchamiana w tej wersji . Odczytuje plik konfiguracji [ \<supportedRuntime >](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) wpisów w kolejności, w jakiej występują i używa pierwszej wersji .NET Framework na liście, które znajduje się na komputerze użytkownika. (Użyj [ \<requiredRuntime > elementu](../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) dla wersji 1.0.)  
  
-   Skompilowana wersja.  
  
     Jeśli nie ma pliku konfiguracji, ale wersja programu .NET Framework, z użyciem której skompilowano aplikację, jest obecna na komputerze użytkownika, aplikacja jest uruchamiana z użyciem tej wersji.  
  
-   Najnowsza zainstalowana wersja.  
  
     Jeśli nie ma wersji programu .NET Framework, utworzony aplikacji i pliku konfiguracji nie określono wersji w [ \<supportedRuntime > element](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md), aplikacja próbuje uruchomić z najnowszą wersją programu .NET Platforma, która występuje na komputerze użytkownika.  
  
     Jednak aplikacje programu .NET Framework 1.0, 1.1, 2.0, 3.0 i 3.5 nie są automatycznie uruchamiane w programie .NET Framework 4 lub nowszym, a w niektórych przypadkach jest wyświetlany błąd i może się pojawić monit o zainstalowanie programu .NET Framework 3.5. Zachowanie aktywacji może także zależeć od systemu operacyjnego użytkownika, ponieważ różne wersje systemu Windows zawierają różne wersje programu .NET Framework. Jeśli aplikacja obsługuje programy .NET Framework 3.5 i 4 lub nowsze, zalecane jest, aby wskazać to za pomocą wielu wpisów w pliku konfiguracji, co pozwoli uniknąć błędów inicjowania programu .NET Framework. Aby uzyskać więcej informacji, zobacz [wersje i zależności](../../../docs/framework/migration-guide/versions-and-dependencies.md).  
  
 Aby wykorzystać ulepszenia wydajności wprowadzone w wersjach 4 i 4.5, można również skonfigurować aplikacje programu .NET Framework 3.5 tak, aby działały w programie .NET Framework 4 lub 4.5, nawet na komputerach, na których zainstalowano program .NET Framework 3.5.  
  
> [!IMPORTANT]
>  Zalecane jest, aby zawsze testować aplikację z każdą wersją programu .NET Framework, która jest obsługiwana. Zobacz [zgodność wersji](../../../docs/framework/migration-guide/version-compatibility.md) informacje dotyczące uaktualniania aplikacji do obsługi nowsze wersje programu .NET Framework.  
  
 Informacje dotyczące modyfikowania aplikacji .NET Framework 1.0 i 1.1 do obsługi systemu Windows 7 i Windows 8, zobacz [Migrowanie z programu .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md).  
  
### <a name="to-configure-your-app-to-run-on-the-net-framework-4-or-45"></a>Aby skonfigurować aplikację do działania w programie .NET Framework 4 lub 4.5  
  
1.  Dodaj lub zlokalizuj plik konfiguracji projektu programu .NET Framework. Plik konfiguracji aplikacji znajduje się w tym samym katalogu i ma taką samą nazwę jak aplikacja, ale ma rozszerzenie .config. Na przykład dla aplikacji o nazwie MyExecutable.exe plik konfiguracji aplikacji ma nazwę MyExecutable.exe.config.  
  
     Aby dodać plik konfiguracji, na pasku menu programu Visual Studio wybierz **projektu**, **Dodaj nowy element**. Wybierz **ogólne** w lewym okienku, a następnie wybierz pozycję **pliku konfiguracyjnego**.  Nazwa pliku konfiguracji *appName*. exe.config. Te opcje menu nie są dostępne dla projektów aplikacji do Sklepu Windows lub dla systemu Windows Phone, ponieważ nie można zmienić zasad aktywacji na tych platformach.  
  
2.  Dodaj [ \<supportedRuntime >](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) elementu następujący do pliku konfiguracji aplikacji:  
  
    ```xml  
    <configuration>  
      <startup>  
        <supportedRuntime version="<version>"/>  
      </startup>  
    </configuration>  
    ```  
  
     gdzie  *\<wersji >* Określa wersję środowiska CLR, aby była zgodna z wersją .NET Framework, która obsługuje aplikację. Użyj następujących ciągów:  
  
    -   .NET Framework 1.0: "v1.0.3705"  
  
    -   .NET Framework 1.1: "v1.1.4322"  
  
    -   .NET Framework 2.0, 3.0 i 3.5: "v2.0.50727"  
  
    -   .NET Framework 4 i 4.5 (w tym wydania punktowe, takie jak 4.5.1): "v4.0"  
  
     Można dodawać wiele [ \<supportedRuntime >](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) elementy wymienione w kolejności preferencji, aby określić obsługę wielu wersji programu .NET Framework.  
  
 W poniższej tabeli pokazano, jak na podstawie ustawień w pliku konfiguracji aplikacji i wersji programu .NET Framework zainstalowanych na komputerze można ustalić wersję, w której będzie działać aplikacja przeznaczona dla środowiska .NET Framework 3.5. Przykłady są specyficzne dla aplikacji programu .NET Framework 3.5, ale można używać podobnej logiki w przypadku aplikacjach docelowych, które zostały skompilowane z użyciem starszych wersji programu .NET Framework. Należy zauważyć, że numer wersji programu .NET Framework 2.0 (v2.0.50727) jest używany do określenia programu .NET Framework 3.5 w pliku konfiguracji aplikacji.  
  
|Ustawienie w pliku App.config|Na komputerze z zainstalowaną wersją 3.5|Na komputerze z zainstalowanymi wersjami 3.5 oraz 4 lub 4.5|Na komputerze z zainstalowaną wersją 4 lub 4.5|  
|-|-|-|-|  
|Brak|Działa w wersji 3.5|Działa w wersji 3.5|Wyświetla komunikat o błędzie, który monituje użytkownika o zainstalowanie poprawnej wersji *|  
|`<supportedRuntime version="v2.0.50727"/>`|Działa w wersji 3.5|Działa w wersji 3.5|Wyświetla komunikat o błędzie, który monituje użytkownika o zainstalowanie poprawnej wersji *|  
|`<supportedRuntime version="v2.0.50727"/>` <br /> `<supportedRuntime version="v4.0"/>`|Działa w wersji 3.5|Działa w wersji 3.5|Działa w wersji 4 lub 4.5|  
|`<supportedRuntime version="v4.0"/>` <br /> `<supportedRuntime version="v2.0.50727"/>`|Działa w wersji 3.5|Działa w wersji 4 lub 4.5|Działa w wersji 4 lub 4.5|  
|`<supportedRuntime version="v4.0"/>`|Wyświetla komunikat o błędzie, który monituje użytkownika o zainstalowanie poprawnej wersji *|Działa w wersji 4 lub 4.5|Działa w wersji 4 lub 4.5|  
  
 \*Aby uzyskać więcej informacji na temat tego komunikatu o błędzie i sposobów, aby uniknąć tego problemu, zobacz [błędy inicjowania programu .NET Framework: Zarządzanie wrażeniami użytkownika](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Migracja z programu .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md)  
 [Przewodnik migracji](../../../docs/framework/migration-guide/index.md)
