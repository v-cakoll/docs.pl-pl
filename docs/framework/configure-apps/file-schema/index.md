---
title: Schemat pliku konfiguracji dla .NET Framework
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
ms.openlocfilehash: c3b5518b4b86c2e6f47825d552f49579c5ac0a6d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921019"
---
# <a name="configuration-file-schema-for-the-net-framework"></a>Schemat pliku konfiguracji dla .NET Framework

Pliki konfiguracji to standardowe pliki XML, których można użyć do zmiany ustawień i ustawienia zasad dla aplikacji. Schemat konfiguracji .NET Framework składa się z elementów, których można użyć w plikach konfiguracji w celu sterowania zachowaniem aplikacji. Spis treści tej sekcji odzwierciedla hierarchię schematu dla uruchamiania, środowiska uruchomieniowego, sieci i innych typów ustawień konfiguracji.

Informacje o typach, formatach i lokalizacji plików konfiguracji znajdują się w artykule [Konfigurowanie aplikacji](../index.md). Zapoznaj się z plikiem XML, jeśli chcesz bezpośrednio edytować pliki konfiguracji.

> [!IMPORTANT]
> W przypadku tagów i atrybutów XML w plikach konfiguracji rozróżniana jest wielkość liter.

## <a name="in-this-section"></a>W tej sekcji

[ **> elementukonfiguracji\<** ](configuration-element.md) `<configuration>` Opisuje element, który jest elementem najwyższego poziomu dla wszystkich plików konfiguracji.

[zestawbinding > element określa zasady powiązań zestawu na poziomie konfiguracji.  **\<** ](assemblybinding-element-for-configuration.md)

[linkedConfiguration > element Określa plik konfiguracji, który ma zostać uwzględniony.  **\<** ](linkedconfiguration-element.md)

[Schemat ustawień uruchamiania](./startup/index.md) Opisuje elementy, które określają, która wersja środowiska uruchomieniowego języka wspólnego ma być używana.

[Schemat ustawień środowiska uruchomieniowego](./runtime/index.md) Opisuje elementy, które konfigurują powiązanie zestawu i zachowanie środowiska uruchomieniowego.

[Schemat ustawień sieciowych](./network/index.md) Opisuje elementy, które określają, w jaki sposób .NET Framework nawiązuje połączenie z Internetem.

[Schemat ustawień kryptografii](./cryptography/index.md) Opisuje elementy, które mapują przyjazne nazwy algorytmów na klasy implementujące algorytmy kryptografii.

[Schemat sekcji konfiguracji](configuration-sections-schema.md) Opisuje elementy używane do tworzenia i używania sekcji konfiguracyjnych ustawień niestandardowych.

[Schemat ustawień śledzenia i debugowania](./trace-debug/index.md) Opisuje elementy, które określają przełączniki śledzenia i odbiorniki.

[Schemat ustawień kompilatora i dostawcy języka](./compiler/index.md) Opisuje elementy, które określają konfigurację kompilatora dla dostępnych dostawców języka.

[Schemat ustawień aplikacji](application-settings-schema.md) Opisuje elementy, które umożliwiają aplikacji Windows Forms lub ASP.NET przechowywanie i pobieranie ustawień zakresu aplikacji i zakresu użytkownika.

[Schemat ustawień aplikacji](./appsettings/index.md) Zawiera niestandardowe ustawienia aplikacji, takie jak ścieżki plików, adresy URL usług sieci Web XML lub inne niestandardowe informacje o konfiguracji dla aplikacji.

[Schemat ustawień sieci Web](./web/index.md) Wszystkie elementy w schemacie ustawień sieci Web, w tym elementy służące do konfigurowania sposobu działania programu ASP.NET z aplikacją hosta, taką jak usługi IIS. Używany w plikach *ASPNET. config* .

[Schemat konfiguracji Windows Forms](winforms/index.md) Wszystkie elementy w sekcji Konfiguracja aplikacji Windows Forms, w tym takie dostosowania, jak obsługa wielomonitorów i wysokiej rozdzielczości DPI.

[Schemat konfiguracji WCF](./wcf/index.md) Wszystkie elementy, które umożliwiają skonfigurowanie usługi WCF i aplikacji klienckich.

[Składnia dyrektywy WCF](./wcf-directive/index.md) `@ServiceHost` Opisuje dyrektywę, która definiuje atrybuty specyficzne dla strony używane przez kompilator SVC.

[Schemat konfiguracji WIF](windows-identity-foundation/index.md) Wszystkie elementy schematu konfiguracji Windows Identity Foundation (WIF).

## <a name="related-sections"></a>Sekcje pokrewne

[Schemat ustawień komunikacji zdalnej](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100)) Opisuje elementy, które konfigurują aplikacje klienta i serwera, które implementują komunikację zdalną.

[Schemat ustawień ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100)) Opisuje elementy kontrolujące zachowanie aplikacji sieci Web ASP.NET.

[Schemat ustawień usług sieci Web](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100)) Opisuje elementy kontrolujące zachowanie usług sieci Web ASP.NET i ich klientów.

[Konfigurowanie aplikacji .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100)) Opisuje sposób konfigurowania zabezpieczeń, powiązań zestawów i komunikacji zdalnej w .NET Framework.
