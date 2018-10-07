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
ms.openlocfilehash: 4543802c3918a4761daa5a4fbbab366695823f73
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48839052"
---
# <a name="configuration-file-schema-for-the-net-framework"></a>Schemat pliku konfiguracji dla programu .NET Framework

Pliki konfiguracyjne są standardowymi plikami XML, które służy do zmiany ustawień i ustawienia zasad dla aplikacji. Schemat konfiguracji .NET Framework składa się z elementów, w której można w plikach konfiguracyjnych do sterowania zachowaniem aplikacji. Spis treści dla tej sekcji odzwierciedla hierarchię schematów dla uruchamiania, środowisko uruchomieniowe, sieci i innych rodzajów ustawień konfiguracji.

Aby uzyskać informacje o typach, formatu i lokalizacji plików konfiguracji, zobacz artykuł [konfigurowania aplikacji](~/docs/framework/configure-apps/index.md). Zapoznaj się z danymi XML, jeśli chcesz bezpośrednio edytować pliki konfiguracyjne.

> [!IMPORTANT]
> Znaczniki i atrybuty w plikach konfiguracji XML jest rozróżniana wielkość liter.

## <a name="in-this-section"></a>W tej sekcji

[**\<Konfiguracja >** elementu](~/docs/framework/configure-apps/file-schema/configuration-element.md) w tym artykule opisano `<configuration>` element, który jest elementem najwyższego poziomu dla wszystkich plików konfiguracyjnych.

[**\<assemblybinding — >** elementu](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) określa politykę powiązania zestawu na poziomie konfiguracji.

[**\<linkedconfiguration — >** elementu](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) określa wymagający uwzględnienia plik konfiguracji.

[Schemat ustawień uruchamiania](~/docs/framework/configure-apps/file-schema/startup/index.md) w tym artykule opisano elementy określające, która wersja środowiska uruchomieniowego języka wspólnego do użycia.

[Schemat ustawień środowiska uruchomieniowego](~/docs/framework/configure-apps/file-schema/runtime/index.md) w tym artykule opisano elementy, które konfigurują zachowanie zestawu powiązania i środowiska wykonawczego.

[Schemat ustawień sieci](~/docs/framework/configure-apps/file-schema/network/index.md) opisano elementy, które określają, jak .NET Framework łączy się z Internetem.

[Schemat ustawień kryptografii](~/docs/framework/configure-apps/file-schema/cryptography/index.md) opisano elementy, które mapują przyjazne nazwy algorytmu na klasy, które implementują algorytmy kryptograficzne.

[Schemat sekcji konfiguracji](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) opisano elementy używane do tworzenia i korzystanie z sekcji konfiguracji dla ustawień niestandardowych.

[Debugowanie schemat ustawień śledzenia i](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) opisano elementy, które określają przełączniki śledzenia i detektory.

[Schemat ustawień dostawcy języka kompilatora i](~/docs/framework/configure-apps/file-schema/compiler/index.md) opisano elementy, które określają konfigurację kompilatora dla dostępnych dostawców języka.

[Schemat ustawień aplikacji](~/docs/framework/configure-apps/file-schema/application-settings-schema.md) opisano elementy, które umożliwiają aplikacji Windows Forms i ASP.NET w do przechowywania i pobierania ustawień o zakresie aplikacji i zakresie użytkownika.

[Schemat ustawień aplikacji](~/docs/framework/configure-apps/file-schema/appsettings/index.md) zawiera ustawienia aplikacji niestandardowych, takich jak ścieżki do plików, adresy URL usługi sieci Web XML lub inne informacje konfiguracji niestandardowej dla aplikacji.

[Schemat ustawień internetowych](~/docs/framework/configure-apps/file-schema/web/index.md) wszystkie elementy w schemacie ustawień sieci Web zawierają elementy umożliwiające konfigurację działania programu ASP.NET z aplikacją hosta, takich jak usługi IIS. Używane w *Aspnet.config* plików.

[Schemat konfiguracji programu Windows Forms](winforms/index.md) wszystkie elementy w sekcji Konfiguracja aplikacji Windows Forms, która zawiera dostosowania, takie jak obsługa rozdzielczości DPI wielu monitorów i wysoka.

[Schemat konfiguracji programu WCF](~/docs/framework/configure-apps/file-schema/wcf/index.md) wszystkie elementy, które umożliwiają konfigurowanie aplikacji usługi i klienta WCF.

[Składnia dyrektywy programu WCF](~/docs/framework/configure-apps/file-schema/wcf-directive/index.md) w tym artykule opisano `@ServiceHost` dyrektywy, który definiuje atrybuty specyficzne dla strony, używane przez kompilator .svc.

[Schemat konfiguracji programu WIF](windows-identity-foundation/index.md) wszystkie elementy schematu konfiguracji Windows Identity Foundation (WIF).

## <a name="related-sections"></a>Sekcje pokrewne

[Schemat ustawień komunikacji zdalnej](https://msdn.microsoft.com/library/dc2d1e62-9af7-4ca1-99fd-98b93bb4db9e) w tym artykule opisano elementy, które konfigurują aplikacje klienckie i serwerowe, które implementują komunikację zdalną.

[ASP.NET Settings Schema](https://msdn.microsoft.com/library/b5ysx397\(v=vs.100\).aspx) opisano elementy, które kontrolują zachowanie aplikacji sieci Web ASP.NET.

[Schemat ustawień usługi w sieci Web](https://msdn.microsoft.com/library/f84d6d55-1add-4eb7-ae46-33df5833ea2e) opisano elementy, które kontrolują zachowanie swoich klientów i usług sieci Web platformy ASP.NET.

[Konfigurowanie aplikacji programu .NET Framework](https://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42) opisano, jak skonfigurować zabezpieczenia, zmontować zestaw i komunikacji zdalnej w programie .NET Framework.
