---
title: Schemat pliku konfiguracji dla programu .NET Framework
ms.date: 05/01/2017
helpviewer_keywords:
- .NET Framework application configuration, configuration schema
- machine configuration files
- application configuration files, schema
- app.config files, schema
- schema configuration settings
- schemas, configuration settings
- enterprisesec.config files
- well-formed XML
- enterprisesec configuration files
- security.config files
- security [.NET Framework], configuration files
- application development [.NET Framework], schema
- XML tags
- container tags
- machine.config files
- configuration schema [.NET Framework]
- configuration settings [.NET Framework], applications
- configuration file reference [.NET Framework]
ms.assetid: 69003d39-dc8a-460c-a6be-e6d93e690b38
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b227ba343db7996d38d5a485b54629a1f4ed28bd
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="configuration-file-schema-for-the-net-framework"></a>Schemat pliku konfiguracji dla programu .NET Framework

Pliki konfiguracji są standardowe pliki XML, które można zmienić ustawienia, a następnie ustawić zasady dla aplikacji. Schemat konfiguracji .NET Framework składa się z elementów, że można użyć w plikach konfiguracji, aby kontrolować działanie aplikacji. Spis treści dla tej sekcji przedstawiają dane hierarchii schematu na potrzeby uruchamiania, środowisko uruchomieniowe sieci i innych ustawień konfiguracji.

Dla informacji o typach, format i lokalizację plików konfiguracji, zobacz artykuł [konfigurowania aplikacji](~/docs/framework/configure-apps/index.md). Zapoznaj się z XML, jeśli chcesz bezpośrednio modyfikować pliki konfiguracyjne.

> [!IMPORTANT]
> Tagi XML oraz atrybuty w plikach konfiguracji jest rozróżniana wielkość liter.

## <a name="in-this-section"></a>W tej sekcji

[**\<Konfiguracja >** elementu](~/docs/framework/configure-apps/file-schema/configuration-element.md) w tym artykule opisano `<configuration>` element, który jest elementem najwyższego poziomu dla wszystkich plików konfiguracji.

[**\<assemblybinding — >** elementu](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) określa zestaw powiązania zasad na poziomie konfiguracji.

[**\<linkedconfiguration — >** elementu](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) Określa plik konfiguracji do uwzględnienia.

[Schemat ustawień uruchamiania](~/docs/framework/configure-apps/file-schema/startup/index.md) opisano elementy, które określenie, którą wersję środowiska CLR do użycia.

[Schemat ustawień środowiska uruchomieniowego](~/docs/framework/configure-apps/file-schema/runtime/index.md) opisano elementy, które skonfigurować zachowanie zestawu powiązania i środowiska uruchomieniowego.

[Schemat ustawień sieci](~/docs/framework/configure-apps/file-schema/network/index.md) opisano elementy, które określają sposób programu .NET Framework łączy się z Internetem.

[Schemat ustawień kryptografii](~/docs/framework/configure-apps/file-schema/cryptography/index.md) opisano elementy, które mapują algorytm przyjaznej nazwy klasy, które implementują algorytmów kryptograficznych.

[Schemat sekcji konfiguracji](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) opisano elementy służące do tworzenia i Użyj sekcji konfiguracji w celu ustawienia niestandardowe.

[Schemat ustawień debugowania i śledzenia](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) opisano elementy określające przełączniki śledzenia i odbiorników.

[Schemat ustawień dostawcy języka i kompilatora](~/docs/framework/configure-apps/file-schema/compiler/index.md) opisano elementy, które będzie określić konfigurację kompilatora dla dostawcy dostępnych języków.

[Schemat ustawień aplikacji](~/docs/framework/configure-apps/file-schema/application-settings-schema.md) opisano elementy, które umożliwiają aplikacji dla formularzy systemu Windows lub programu ASP.NET do przechowywania i pobierania ustawień zakresu aplikacji i zakresu użytkownika.

[Schemat ustawień aplikacji](~/docs/framework/configure-apps/file-schema/appsettings/index.md) zawiera ustawienia aplikacji niestandardowych, takich jak ścieżki plików, adresy URL usługi XML sieci Web lub inne informacje konfiguracji niestandardowej dla aplikacji.

[Schemat ustawień w sieci Web](~/docs/framework/configure-apps/file-schema/web/index.md) wszystkie elementy w schemat ustawień sieci Web, który zawiera elementy dotyczące konfigurowania, jak działa ASP.NET przy użyciu aplikacji hosta, takich jak IIS. Używane w *konfigurację Aspnet.config* plików.

[Schemat konfiguracji formularzy systemu Windows](winforms/index.md) wszystkie elementy w sekcji konfiguracji aplikacji formularzy systemu Windows, która zawiera dostosowania, takie jak obsługa DPI wielu monitorów i wysoki.

[Schemat konfiguracji programu WCF](~/docs/framework/configure-apps/file-schema/wcf/index.md) wszystkie elementy, które umożliwiają skonfigurowanie WCF usługi i aplikacje klienckie.

[Składnia dyrektywy WCF](~/docs/framework/configure-apps/file-schema/wcf-directive/index.md) w tym artykule opisano `@ServiceHost` dyrektywy, który definiuje atrybuty specyficzne dla strony używany przez kompilator .svc.

[Schemat konfiguracji WIF](windows-identity-foundation/index.md) wszystkie elementy schemat konfiguracji systemu Windows Identity Foundation (WIF).

## <a name="related-sections"></a>Sekcje pokrewne

[Schemat ustawień komunikacji zdalnej](http://msdn.microsoft.com/library/dc2d1e62-9af7-4ca1-99fd-98b93bb4db9e) opisano elementy służące do konfiguracji klienta i serwera aplikacji, które implementuje komunikacji zdalnej.

[Schemat ustawień programu ASP.NET](http://msdn.microsoft.com/library/b5ysx397\(v=vs.100\).aspx) opisano elementy, które określają zachowanie aplikacji sieci Web ASP.NET.

[Schemat ustawień usługi w sieci Web](http://msdn.microsoft.com/library/f84d6d55-1add-4eb7-ae46-33df5833ea2e) opisano elementy, które kontrolują zachowanie usługi sieci Web ASP.NET i klientów.

[Konfigurowanie aplikacji programu .NET Framework](http://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42) opisano sposób konfigurowania zabezpieczeń, powiązań zestawów i komunikacji zdalnej w programie .NET Framework.
