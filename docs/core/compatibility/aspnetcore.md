---
title: ASP.NET Kluczowe zmiany w zerwaniu
titleSuffix: ''
description: Wyświetla listę przełomowych zmian w ASP.NET Core.
ms.date: 03/26/2020
author: scottaddie
ms.author: scaddie
ms.openlocfilehash: 05272032f2b93c8ae89377a20e6fdafc2ff0eb7b
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345327"
---
# <a name="aspnet-core-breaking-changes"></a>ASP.NET Kluczowe zmiany w zerwaniu

ASP.NET Core udostępnia funkcje tworzenia aplikacji sieci web używane przez program .NET Core.

Na tej stronie są udokumentowane następujące zmiany podziału:

- [Usunięto przestarzałe interfejsy API antiforgery, CORS, Diagnostics, MVC i Routing](#obsolete-antiforgery-cors-diagnostics-mvc-and-routing-apis-removed)
- [Uwierzytelnianie: wycofanie google+](#authentication-google-deprecated-and-replaced)
- [Uwierzytelnianie: httpContext.Authentication właściwość usunięta](#authentication-httpcontextauthentication-property-removed)
- [Uwierzytelnianie: zastąpiono typy Newtonsoft.Json](#authentication-newtonsoftjson-types-replaced)
- [Uwierzytelnianie: Zmieniono podpis Programu ExchangeCodeAsync usługi OAuthHandler](#authentication-oauthhandler-exchangecodeasync-signature-changed)
- [Autoryzacja: Przeciążenie addAutoryzacja przeniesione do innego zestawu](#authorization-addauthorization-overload-moved-to-different-assembly)
- [Autoryzacja: IAllowAnonymous usunięte z AuthorizationFilterContext.Filters](#authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters)
- [Autoryzacja: Implementacje IAuthorizationPolicyProvider wymagają nowej metody](#authorization-iauthorizationpolicyprovider-implementations-require-new-method)
- [Platforma Azure: usunięto pakiety integracji platformy Azure z prefiksem platformy Microsoft](#azure-microsoft-prefixed-azure-integration-packages-removed)
- [Buforowanie: Usunięto właściwość CompactOnMemoryPressure](#caching-compactonmemorypressure-property-removed)
- [Buforowanie: Microsoft.Extensions.Caching.SqlServer używa nowego pakietu SqlClient](#caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package)
- [Buforowanie: ResponseCaching "pubternal" typy zmienione na wewnętrzne](#caching-responsecaching-pubternal-types-changed-to-internal)
- [Ochrona danych: DataProtection.AzureStorage używa nowych interfejsów API usługi Azure Storage](#data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis)
- [Hosting: AspNetCoreModule V1 usunięty z pakietu hostingu systemu Windows](#hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle)
- [Hosting: ogólny host ogranicza iniekcję konstruktora uruchamiania](#hosting-generic-host-restricts-startup-constructor-injection)
- [Hosting: przekierowanie HTTPS włączone dla aplikacji poza procesem usług IIS](#hosting-https-redirection-enabled-for-iis-out-of-process-apps)
- [Hosting: IHostingEnvironment i IApplicationLifetime typy zastąpione](#hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced)
- [Hosting: ObjectPoolProvider usunięty z zależności WebHostBuilder](#hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies)
- [HTTP: Zmiany w przeglądarce SameSite wpływają na uwierzytelnianie](#http-browser-samesite-changes-impact-authentication)
- [HTTP: Usunięto domyślną rozszerzalność protokołuHttpContext](#http-defaulthttpcontext-extensibility-removed)
- [HTTP: Pola nazwy nagłówków zmienione na statyczne tylko do odczytu](#http-headernames-constants-changed-to-static-readonly)
- [HTTP: Zmiany w infrastrukturze treści odpowiedzi](#http-response-body-infrastructure-changes)
- [HTTP: Zmieniono niektóre domyślne wartości cookie SameSite](#http-some-cookie-samesite-defaults-changed-to-none)
- [HTTP: Synchroniczne we/wy domyślnie wyłączone](#http-synchronous-io-disabled-in-all-servers)
- [Tożsamość: Usunięto przeciążenie metody AddDefaultUI](#identity-adddefaultui-method-overload-removed)
- [Tożsamość: Zmiana wersji interfejsu użytkownika Bootstrap](#identity-default-bootstrap-version-of-ui-changed)
- [Tożsamość: SignInAsync zgłasza wyjątek dla nieuwierzytezowanej tożsamości](#identity-signinasync-throws-exception-for-unauthenticated-identity)
- [Tożsamość: Konstruktor SignInManager akceptuje nowy parametr](#identity-signinmanager-constructor-accepts-new-parameter)
- [Tożsamość: interfejs użytkownika używa funkcji statycznych zasobów internetowych](#identity-ui-uses-static-web-assets-feature)
- [Pustułka: Usunięte adaptery przyłączeniowe](#kestrel-connection-adapters-removed)
- [Pustułka: Pusty zestaw HTTPS usunięty](#kestrel-empty-https-assembly-removed)
- [Pustułka: Prośba o przeniesienie nagłówków zwiastuna do nowej kolekcji](#kestrel-request-trailer-headers-moved-to-new-collection)
- [Pustułka: Zmiany warstwy abstrakcji transportu](#kestrel-transport-abstractions-removed-and-made-public)
- [Lokalizacja: interfejsy API oznaczone jako przestarzałe](#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete)
- [Rejestrowanie: DebugLogger klasy wykonane wewnętrzne](#logging-debuglogger-class-made-internal)
- [MVC: Usunięto sufiks asynchronii asynchronii](#mvc-async-suffix-trimmed-from-controller-action-names)
- [MVC: JsonResult przeniesiony do Microsoft.AspNetCore.Mvc.Core](#mvc-jsonresult-moved-to-microsoftaspnetcoremvccore)
- [MVC: Narzędzie do wstępnej kompilacji przestarzałe](#mvc-precompilation-tool-deprecated)
- [MVC: Typy zmienione na wewnętrzne](#mvc-pubternal-types-changed-to-internal)
- [MVC: Usunięto podkładkę zgodności interfejsu API sieci Web](#mvc-web-api-compatibility-shim-removed)
- [Razor: Kompilacja środowiska uruchomieniowego przeniesiona do pakietu](#razor-runtime-compilation-moved-to-a-package)
- [Stan sesji: przestarzałe interfejsy API usunięte](#session-state-obsolete-apis-removed)
- [Współużytkowana struktura: usuwanie zestawu z pliku Microsoft.AspNetCore.App](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp)
- [Współużytkowana struktura: Microsoft.AspNetCore.All usunięte](#shared-framework-removed-microsoftaspnetcoreall)
- [SignalR: HandshakeProtocol.SuccessHandshakeData zastąpiony](#signalr-handshakeprotocolsuccesshandshakedata-replaced)
- [SignalR: Metody HubConnection usunięte](#signalr-hubconnection-resetsendping-and-resettimeout-methods-removed)
- [SignalR: HubConnectionContext konstruktory zmienione](#signalr-hubconnectioncontext-constructors-changed)
- [SignalR: Zmiana nazwy pakietu klienta JavaScript](#signalr-javascript-client-package-name-changed)
- [SignalR: MessagePack Hub Protocol przeniesiony do pakietu MessagePack 2.x](#signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package)
- [SignalR: Przestarzałe interfejsy API](#signalr-usesignalr-and-useconnections-methods-marked-obsolete)
- [SignalR: UseSignalR i UseConnections metody usunięte](#signalr-usesignalr-and-useconnections-methods-removed)
- [OSO: SpaServices i NodeServices logger rezerwowy domyślnej zmiany](#spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger)
- [OSO: Usługi Spaservices i NodeServices oznaczone jako przestarzałe](#spas-spaservices-and-nodeservices-marked-obsolete)
- [Struktura docelowa: .NET Framework nie jest obsługiwana](#target-framework-net-framework-support-dropped)

## <a name="aspnet-core-50"></a>ASP.NET Core 5.0

[!INCLUDE[Azure: Microsoft-prefixed Azure integration packages removed](~/includes/core-changes/aspnetcore/5.0/azure-integration-packages-removed.md)]

***

[!INCLUDE[SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package](~/includes/core-changes/aspnetcore/5.0/signalr-messagepack-package.md)]

***

[!INCLUDE[SignalR: UseSignalR and UseConnections methods removed](~/includes/core-changes/aspnetcore/5.0/signalr-usesignalr-useconnections-removed.md)]

***

## <a name="aspnet-core-31"></a>ASP.NET Core 3.1

[!INCLUDE[HTTP: Browser SameSite changes impact authentication](~/includes/core-changes/aspnetcore/3.1/http-cookie-samesite-authn-impacts.md)]

***

## <a name="aspnet-core-30"></a>ASP.NET Core 3.0

[!INCLUDE[Obsolete Antiforgery, CORS, Diagnostics, MVC, and Routing APIs removed](~/includes/core-changes/aspnetcore/3.0/obsolete-apis-removed.md)]

***

[!INCLUDE[Authentication: Google+ deprecation](~/includes/core-changes/aspnetcore/3.0/authn-google-plus-authn-changes.md)]

***

[!INCLUDE[Authentication: HttpContext.Authentication property removed](~/includes/core-changes/aspnetcore/3.0/authn-httpcontext-property-removed.md)]

***

[!INCLUDE[Authentication: Newtonsoft.Json types replaced](~/includes/core-changes/aspnetcore/3.0/authn-apis-json-types.md)]

***

[!INCLUDE[Authentication: OAuthHandler ExchangeCodeAsync signature changed](~/includes/core-changes/aspnetcore/3.0/authn-exchangecodeasync-signature-change.md)]

***

[!INCLUDE[Authorization: AddAuthorization overload assembly change](~/includes/core-changes/aspnetcore/3.0/authz-assembly-change.md)]

***

[!INCLUDE[Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters](~/includes/core-changes/aspnetcore/3.0/authz-iallowanonymous-removed-from-collection.md)]

***

[!INCLUDE[Authorization: IAuthorizationPolicyProvider implementations require new method](~/includes/core-changes/aspnetcore/3.0/authz-iauthzpolicyprovider-new-method.md)]

***

[!INCLUDE[Caching: CompactOnMemoryPressure property removed](~/includes/core-changes/aspnetcore/3.0/caching-memory-property-removed.md)]

***

[!INCLUDE[Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package](~/includes/core-changes/aspnetcore/3.0/caching-new-sqlclient-package.md)]

***

[!INCLUDE[Caching: ResponseCaching types changed to internal](~/includes/core-changes/aspnetcore/3.0/caching-response-pubternal-to-internal.md)]

***

[!INCLUDE[Data Protection: DataProtection.AzureStorage uses new Azure Storage APIs](~/includes/core-changes/aspnetcore/3.0/dataprotection-azstorage-using-azstorage-apis.md)]

***

[!INCLUDE[Hosting: ANCM version 1 removed from hosting bundle](~/includes/core-changes/aspnetcore/3.0/hosting-ancmv1-hosting-bundle-removal.md)]

***

[!INCLUDE[Hosting: Generic host restriction on Startup constructor injection](~/includes/core-changes/aspnetcore/3.0/hosting-generic-host-startup-ctor-restriction.md)]

***

[!INCLUDE[Hosting: HTTPS redirection enabled for IIS OutOfProcess](~/includes/core-changes/aspnetcore/3.0/hosting-https-redirection-iis-outofprocess.md)]

***

[!INCLUDE[Hosting: IHostingEnvironment and IApplicationLifetime types replaced](~/includes/core-changes/aspnetcore/3.0/hosting-ihostingenv-iapplifetime-types-replaced.md)]

***

[!INCLUDE[Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies](~/includes/core-changes/aspnetcore/3.0/hosting-objectpoolprovider-webhostbuilder-dependencies.md)]

***

[!INCLUDE[HTTP: DefaultHttpContext extensibility removed](~/includes/core-changes/aspnetcore/3.0/http-defaulthttpcontext-extensibility-removed.md)]

***

[!INCLUDE[HTTP: HeaderNames fields changed to static readonly](~/includes/core-changes/aspnetcore/3.0/http-headernames-constants-staticreadonly.md)]

***

[!INCLUDE[HTTP: Response body infrastructure changes](~/includes/core-changes/aspnetcore/3.0/http-response-body-changes.md)]

***

[!INCLUDE[HTTP: Some cookie SameSite default values changed](~/includes/core-changes/aspnetcore/3.0/http-cookie-samesite-defaults-change.md)]

***

[!INCLUDE[HTTP: Synchronous IO disabled by default](~/includes/core-changes/aspnetcore/3.0/http-synchronous-io-disabled.md)]

***

[!INCLUDE[Identity: AddDefaultUI method overload removed](~/includes/core-changes/aspnetcore/3.0/identity-ui-adddefaultui-overload-removed.md)]

***

[!INCLUDE[Identity: UI Bootstrap version change](~/includes/core-changes/aspnetcore/3.0/identity-ui-bootstrap-version.md)]

***

[!INCLUDE[Identity: SignInAsync throws exception for unauthenticated identity](~/includes/core-changes/aspnetcore/3.0/identity-signinasync-throws-exception.md)]

***

[!INCLUDE[Identity: SignInManager constructor accepts new parameter](~/includes/core-changes/aspnetcore/3.0/identity-signinmanager-ctor-parameter.md)]

***

[!INCLUDE[Identity: UI uses static web assets feature](~/includes/core-changes/aspnetcore/3.0/identity-ui-static-web-assets.md)]

***

[!INCLUDE[Kestrel: Connection adapters removed](~/includes/core-changes/aspnetcore/3.0/kestrel-connection-adapters-removed.md)]

***

[!INCLUDE[Kestrel: Empty HTTPS assembly removed](~/includes/core-changes/aspnetcore/3.0/kestrel-empty-assembly-removed.md)]

***

[!INCLUDE[Kestrel: Request trailer headers moved to new collection](~/includes/core-changes/aspnetcore/3.0/kestrel-request-trailer-headers.md)]

***

[!INCLUDE[Kestrel: Transport abstraction layer changes](~/includes/core-changes/aspnetcore/3.0/kestrel-transport-abstractions.md)]

***

[!INCLUDE[Localization: APIs marked obsolete](~/includes/core-changes/aspnetcore/3.0/localization-apis-marked-obsolete.md)]

***

[!INCLUDE[Logging: DebugLogger class made internal](~/includes/core-changes/aspnetcore/3.0/logging-debuglogger-to-internal.md)]

***

[!INCLUDE[MVC: Controller action Async suffix removed](~/includes/core-changes/aspnetcore/3.0/mvc-action-async-suffix-trimmed.md)]

***

[!INCLUDE[MVC: JsonResult moved to Microsoft.AspNetCore.Mvc.Core](~/includes/core-changes/aspnetcore/3.0/mvc-jsonresult-moved.md)]

***

[!INCLUDE[MVC: Precompilation tool deprecated](~/includes/core-changes/aspnetcore/3.0/mvc-precompilation-tool-deprecated.md)]

***

[!INCLUDE[MVC: Types changed to internal](~/includes/core-changes/aspnetcore/3.0/mvc-pubternal-to-internal.md)]

***

[!INCLUDE[MVC: Web API compatibility shim removed](~/includes/core-changes/aspnetcore/3.0/mvc-webapi-compat-shim-removed.md)]

***

[!INCLUDE[Razor: Runtime compilation moved to a package](~/includes/core-changes/aspnetcore/3.0/razor-runtime-compilation-package.md)]

***

[!INCLUDE[Session state: Obsolete APIs removed](~/includes/core-changes/aspnetcore/3.0/session-obsolete-apis-removed.md)]

***

[!INCLUDE[Shared framework: Assembly removal from Microsoft.AspNetCore.App](~/includes/core-changes/aspnetcore/3.0/sharedfx-app-shared-framework-assemblies.md)]

***

[!INCLUDE[Shared framework: Microsoft.AspNetCore.All removed](~/includes/core-changes/aspnetcore/3.0/sharedfx-all-framework-removed.md)]

***

[!INCLUDE[SignalR: HandshakeProtocol.SuccessHandshakeData replaced](~/includes/core-changes/aspnetcore/3.0/signalr-successhandshakedata-replaced.md)]

***

[!INCLUDE[SignalR: HubConnection methods removed](~/includes/core-changes/aspnetcore/3.0/signalr-hubconnection-methods-removed.md)]

***

[!INCLUDE[SignalR: HubConnectionContext constructors changed](~/includes/core-changes/aspnetcore/3.0/signalr-hubconnectioncontext-ctors.md)]

***

[!INCLUDE[SignalR: JavaScript client package name change](~/includes/core-changes/aspnetcore/3.0/signalr-js-client-package-name.md)]

***

[!INCLUDE[SignalR: Obsolete APIs](~/includes/core-changes/aspnetcore/3.0/signalr-obsolete-apis.md)]

***

[!INCLUDE[SPAs: SpaServices and NodeServices marked obsolete](~/includes/core-changes/aspnetcore/3.0/spas-spaservices-nodeservices-obsolete.md)]

***

[!INCLUDE[SPAs: SpaServices and NodeServices console logger fallback default change](~/includes/core-changes/aspnetcore/3.0/spas-spaservices-nodeservices-fallback.md)]

***

[!INCLUDE[Target framework: .NET Framework not supported](~/includes/core-changes/aspnetcore/3.0/targetfx-netfx-tfm-support.md)]

***
