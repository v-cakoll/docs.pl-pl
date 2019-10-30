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
ms.openlocfilehash: 35ed53fc480e218df595794f80af2458f3ecec38
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039156"
---
# <a name="configuration-file-schema-for-the-net-framework"></a>Schemat pliku konfiguracji dla .NET Framework

Pliki konfiguracji to standardowe pliki XML, których można użyć do zmiany ustawień i ustawienia zasad dla aplikacji. Schemat konfiguracji .NET Framework składa się z elementów, których można użyć w plikach konfiguracji w celu sterowania zachowaniem aplikacji. Spis treści tej sekcji odzwierciedla hierarchię schematu dla uruchamiania, środowiska uruchomieniowego, sieci i innych typów ustawień konfiguracji.

Aby uzyskać informacje o typach, formacie i lokalizacji plików konfiguracji, zobacz [Konfigurowanie aplikacji](../index.md). Zapoznaj się z plikiem XML, jeśli chcesz bezpośrednio edytować pliki konfiguracji.

> [!IMPORTANT]
> W przypadku tagów i atrybutów XML w plikach konfiguracji rozróżniana jest wielkość liter.

## <a name="in-this-section"></a>W tej sekcji

[ **\<> elementu konfiguracji** ](configuration-element.md)\
Element najwyższego poziomu dla wszystkich plików konfiguracji.

[Element **\<assemblybinding >** ](assemblybinding-element-for-configuration.md)\
Określa zasady powiązań zestawów na poziomie konfiguracji.

[ **\<element > linkedConfiguration** ](linkedconfiguration-element.md)\
Określa plik konfiguracji, który ma zostać uwzględniony.

\ [schematu ustawień uruchamiania](./startup/index.md)
Elementy określające wersję środowiska uruchomieniowego języka wspólnego do użycia.

[Schemat ustawień środowiska uruchomieniowego](./runtime/index.md)\
Elementy, które konfigurują powiązanie zestawu i zachowanie środowiska uruchomieniowego.

[Schemat ustawień sieciowych](./network/index.md)\
Elementy, które określają, w jaki sposób .NET Framework nawiązuje połączenie z Internetem.

\ [schematu ustawień kryptografii](./cryptography/index.md)
Elementy, które mapują przyjazne nazwy algorytmów na klasy implementujące algorytmy kryptografii.

\ [schematu sekcji konfiguracyjnych](configuration-sections-schema.md)
Elementy służące do tworzenia i używania sekcji konfiguracyjnych ustawień niestandardowych.

[Ustawienia śledzenia i debugowania schematu](./trace-debug/index.md)\
Elementy, które określają przełączniki śledzenia i odbiorniki.

[Schemat ustawień kompilatora i dostawcy języka](./compiler/index.md)\
Elementy, które określają konfigurację kompilatora dla dostępnych dostawców języka.

\ [schematu ustawień aplikacji](application-settings-schema.md)
Elementy, które umożliwiają aplikacji Windows Forms lub ASP.NET przechowywanie i pobieranie ustawień zakresu aplikacji i zakresu użytkownika.

\ [schematu ustawień aplikacji](./appsettings/index.md)
Zawiera niestandardowe ustawienia aplikacji, takie jak ścieżki plików, adresy URL usług sieci Web XML lub inne niestandardowe informacje o konfiguracji dla aplikacji.

\ [schematu ustawień sieci Web](./web/index.md)
Elementy służące do konfigurowania sposobu działania ASP.NET z aplikacją hosta, taką jak usługi IIS. Używany w plikach *ASPNET. config* .

\ [schematu konfiguracji Windows Forms](winforms/index.md)
Wszystkie elementy w sekcji Konfiguracja aplikacji Windows Forms, w tym takie, jak takie dostosowania, jak obsługa wielomonitorów i wysokiej rozdzielczości DPI.

\ [schematu konfiguracji WCF](./wcf/index.md)
Wszystkie elementy, które umożliwiają skonfigurowanie usługi WCF i aplikacji klienckich.

[Składnia dyrektywy WCF](./wcf-directive/index.md)\
Opisuje dyrektywę `@ServiceHost`, która definiuje atrybuty specyficzne dla strony używane przez kompilator SVC.

\ [schematu konfiguracji WIF](windows-identity-foundation/index.md)
Wszystkie elementy schematu konfiguracji Windows Identity Foundation (WIF).

## <a name="related-sections"></a>Sekcje pokrewne

\ [schematu ustawień usług zdalnych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))
Opisuje elementy, które konfigurują aplikacje klienta i serwera, które implementują komunikację zdalną.

\ [schematu ustawień ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))
Opisuje elementy kontrolujące zachowanie aplikacji sieci Web ASP.NET.

\ [schematu ustawień usług sieci Web](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))
Opisuje elementy kontrolujące zachowanie usług sieci Web ASP.NET i ich klientów.

[Konfigurowanie aplikacji .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100))\
Opisuje sposób konfigurowania zabezpieczeń, powiązań zestawów i komunikacji zdalnej w .NET Framework.
