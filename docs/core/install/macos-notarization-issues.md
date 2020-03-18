---
title: Praca z systemem macOS Catalina Notariacja
description: Jak obsługiwać problemy z notarialnie i certyfikatami z systemem macOS po zainstalowaniu programu .NET Core, SDK i aplikacji utworzonych przy golu .NET Core.
author: thraka
ms.author: adegeo
ms.date: 02/14/2020
ms.openlocfilehash: be39c1ea56699f84736a2b37bc958507b16e826b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146752"
---
# <a name="macos-catalina-notarization-and-the-impact-on-net-core-downloads-and-projects"></a>Notarizacja catalina dla systemu macOS oraz wpływ na pobieranie i projekty programu .NET Core

Począwszy od systemu macOS Catalina (wersja 10.15), całe oprogramowanie zbudowane po 1 czerwca 2019 r. i dystrybuowane z identyfikatorem dewelopera musi być notarialnie notarialnie. To wymaganie dotyczy programu .NET Core, .NET Core SDK i oprogramowania utworzonego za pomocą programu .NET Core. W tym artykule opisano typowe scenariusze, z którymi mogą wystąpić programy .NET Core i notarization systemu macOS.

## <a name="installing-net-core"></a>Instalowanie programu .NET Core

Instalatory .NET Core (zarówno w czasie wykonywania, jak i SDK) w wersjach 3.1, 3.0 i 2.1 zostały notarialnie notarialnie od lutego 18, 2020. Wcześniej wydane wersje nie są notarialnie. Można ręcznie zainstalować nienotarialnie wersję programu .NET Core, najpierw pobierając `sudo installer` instalator, a następnie używając polecenia. Aby uzyskać więcej informacji, zobacz [Pobieranie i ręczne instalowanie systemu macOS](sdk.md?pivots=os-macos#download-and-manually-install).

Począwszy od następujących wersji instalatorów .NET Core są notarialnie:

- Środowisko uruchomieniowe platformy .NET Core
  - 2.1.16
  - 3.0.3
  - 3.1.2

- Zestaw .NET Core SDK
  - 2.1.512
  - 3.0.103
  - 3.1.102

## <a name="apphost-is-disabled-by-default"></a>appHost jest domyślnie wyłączony

Domyślnie nienotaryzowane wersje .NET Core SDK 3.0 i powyżej produkują natywny plik wykonywalny Mach-O (znany jako **appHost)** po kompilacji projektu, opublikowaniu lub uruchomieniu. Ten plik wykonywalny jest wygodnym sposobem uruchamiania aplikacji. W przeciwnym razie aplikacja musi `dotnet <filename.dll>`zostać uruchomiona przez uruchomienie . Gdy appHost jest włączona, `dotnet run` polecenie jest wywoływane w kontekście appHost. Aby uzyskać więcej informacji, zobacz [Kontekst aplikacjiHost](#context-of-the-apphost).

Począwszy od notarialnie wersji .NET Core SDK 3.0 i powyżej, plik wykonywalny appHost nie jest generowany domyślnie. Możesz włączyć generowanie appHost [`UseAppHost`](../project-sdk/msbuild-props.md#useapphost) z ustawieniem logicznym w pliku projektu. Można również przełączyć appHost z `-p:UseAppHost` parametrem w wierszu `dotnet` polecenia dla określonego polecenia, które uruchamiasz:

- Plik projektu

  ```xml
  <PropertyGroup>
    <UseAppHost>true</UseAppHost>
  </PropertyGroup>
  ```

- Parametr wiersza polecenia

  ```dotnetcli
  dotnet run -p:UseAppHost=true
  ```

AppHost jest zawsze tworzony podczas publikowania aplikacji [niezależne .](../deploying/index.md#publish-self-contained)

Aby uzyskać więcej `UseAppHost` informacji o tym ustawieniu, zobacz [WŁAŚCIWOŚCI MSBuild dla programu Microsoft.NET.Sdk](../project-sdk/msbuild-props.md#useapphost).

### <a name="context-of-the-apphost"></a>Kontekst aplikacjiHost

Gdy appHost jest włączona w projekcie i `dotnet run` używasz polecenia do uruchamiania aplikacji, aplikacja jest wywoływana w kontekście appHost, `dotnet` a nie domyślnego hosta (domyślnym hostem jest polecenie). Jeśli appHost jest wyłączony w projekcie, `dotnet run` polecenie uruchamia aplikację w kontekście hosta domyślnego. Nawet jeśli appHost jest wyłączony, publikowanie aplikacji jako niezależne generuje plik wykonywalny appHost, a użytkownicy używają tego pliku wykonywalnego do uruchamiania aplikacji. Uruchamianie aplikacji `dotnet <filename.dll>` z wywołuje aplikację z domyślnym hostem, udostępnionym czasie wykonywania.

Gdy aplikacja korzystająca z appHost jest wywoływana, partycja certyfikatu dostępna przez aplikację różni się od notarialnie domyślnego hosta. Jeśli aplikacja musi uzyskać dostęp do certyfikatów zainstalowanych za pośrednictwem hosta domyślnego, użyj `dotnet run` polecenia, aby uruchomić aplikację z pliku projektu lub użyj `dotnet <filename.dll>` polecenia, aby uruchomić aplikację bezpośrednio.

Więcej informacji na temat tego scenariusza znajduje się w [sekcji ASP.NET Core i macOS oraz certyfikatów.](#aspnet-core-and-macos-and-certificates)

## <a name="aspnet-core-and-macos-and-certificates"></a>ASP.NET Core i macOS oraz certyfikaty

Program .NET Core umożliwia zarządzanie certyfikatami w pęku <xref:System.Security.Cryptography.X509Certificates> kluczy systemu macOS za pomocą tej klasy. Dostęp do pęku kluczy systemu macOS używa tożsamości aplikacji jako kluczpodstawowy przy podejmowaniu decyzji, która partycja należy wziąć pod uwagę. Na przykład niepodpisane aplikacje przechowują klucze tajne w niepodpisanej partycji, ale podpisane aplikacje przechowują swoje wpisy tajne w partycjach, do których tylko oni mogą uzyskać dostęp. Źródło wykonania, które wywołuje aplikację decyduje, która partycja do użycia.

.NET Core udostępnia trzy źródła wykonania: [appHost](#apphost-is-disabled-by-default), host domyślny `dotnet` (polecenie) i host niestandardowy. Każdy model wykonywania może mieć różne tożsamości, podpisane lub niepodpisane i ma dostęp do różnych partycji w pęku kluczy. Certyfikaty importowane przez jeden tryb mogą nie być dostępne z innego. Na przykład notarialnie wersje programu .NET Core mają domyślny host, który jest podpisany. Certyfikaty są importowane do bezpiecznej partycji na podstawie jego tożsamości. Certyfikaty te nie są dostępne z wygenerowanego appHost, ponieważ appHost jest niepodpisany.

W innym przykładzie domyślnie ASP.NET Core importuje domyślny certyfikat SSL za pośrednictwem hosta domyślnego. ASP.NET Podstawowe aplikacje korzystające z appHost nie będą miały dostępu do tego certyfikatu i otrzymają błąd, gdy program .NET Core wykryje, że certyfikat nie jest dostępny. Komunikat o błędzie zawiera instrukcje dotyczące sposobu rozwiązania tego problemu.

Jeśli wymagane jest udostępnianie certyfikatów, system macOS udostępnia opcje konfiguracji z narzędziem. `security`

Aby uzyskać więcej informacji na temat rozwiązywania problemów z certyfikatem ASP.NET Core, zobacz [Wymuszanie protokołu HTTPS w ASP.NET Core](/aspnet/core/security/enforcing-ssl?view=aspnetcore-3.1&tabs=visual-studio#troubleshoot-certificate-problems).

## <a name="default-entitlements"></a>Uprawnienia domyślne

Domyślny host programu .NET `dotnet` Core (polecenie) ma zestaw uprawnień domyślnych. Uprawnienia te są wymagane do prawidłowego działania programu .NET Core. Jest możliwe, że aplikacja może wymagać dodatkowych uprawnień, w którym to przypadku musisz wygenerować i użyć [appHost,](#apphost-is-disabled-by-default) a następnie dodać niezbędne uprawnienia lokalnie.

Domyślny zestaw uprawnień dla programu .NET Core:

- `com.apple.security.cs.allow-jit`
- `com.apple.security.cs.allow-unsigned-executable-memory`
- `com.apple.security.cs.allow-dyld-environment-variables`
- `com.apple.security.cs.disable-library-validation`

## <a name="notarize-a-net-core-app"></a>Notarize aplikacji .NET Core

Jeśli chcesz uruchomić aplikację w systemie macOS Catalina (wersja 10.15) lub nowszej, należy powiadomić o tym aplikacji. AppHost, który przesyłasz wraz z aplikacją do notarializacji, powinien być używany z co najmniej tymi [samymi uprawnieniami domyślnymi](#default-entitlements) dla .NET Core.

## <a name="next-steps"></a>Następne kroki

- [Zależności i wymagania programu .NET Core](dependencies.md).
- [Zainstaluj zestaw SDK .NET Core](sdk.md).
- [Instalowanie programu runowego .NET Core](runtime.md)
