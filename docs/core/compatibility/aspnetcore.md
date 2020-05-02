---
title: ASP.NET Core istotne zmiany
titleSuffix: ''
description: Wyświetla listę istotnych zmian w ASP.NET Core.
ms.date: 04/29/2020
author: scottaddie
ms.author: scaddie
ms.openlocfilehash: 63d39b1aa6e46b6bcbeb5a409efacac01dea4262
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728335"
---
# <a name="aspnet-core-breaking-changes"></a>ASP.NET Core istotne zmiany

ASP.NET Core udostępnia funkcje deweloperskie aplikacji sieci Web używane przez platformę .NET Core.

Następujące istotne zmiany zostały udokumentowane na tej stronie:

- [Usunięto przestarzałe interfejsy API "antysfałszowane", "CORS, Diagnostics, MVC i Routing"](#obsolete-antiforgery-cors-diagnostics-mvc-and-routing-apis-removed)
- [Uwierzytelnianie: Google + zaniechana](#authentication-google-deprecated-and-replaced)
- [Uwierzytelnianie: Właściwość HttpContext. Authentication została usunięta](#authentication-httpcontextauthentication-property-removed)
- [Uwierzytelnianie: zamieniono typy Newtonsoft. JSON](#authentication-newtonsoftjson-types-replaced)
- [Uwierzytelnianie: OAuthHandler ExchangeCodeAsync zmieniono sygnaturę](#authentication-oauthhandler-exchangecodeasync-signature-changed)
- [Autoryzacja: Przeciążenie metody addauthorization przeniesiono do innego zestawu](#authorization-addauthorization-overload-moved-to-different-assembly)
- [Autoryzacja: Usunięto IAllowAnonymous z AuthorizationFilterContext. filters](#authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters)
- [Autoryzacja: implementacje IAuthorizationPolicyProvider wymagają nowej metody](#authorization-iauthorizationpolicyprovider-implementations-require-new-method)
- [Azure: Usunięto wstępnie ustalone pakiety integracji platformy Azure](#azure-microsoft-prefixed-azure-integration-packages-removed)
- [Buforowanie: Usunięto Właściwość CompactOnMemoryPressure](#caching-compactonmemorypressure-property-removed)
- [Buforowanie: Microsoft. Extensions. buforowanie. SqlServer używa nowego pakietu SqlClient](#caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package)
- [Buforowanie: typy ResponseCaching "pubternal" zostały zmienione na wewnętrzne](#caching-responsecaching-pubternal-types-changed-to-internal)
- [Ochrona danych: usługa dataprotection. AzureStorage używa nowych interfejsów API usługi Azure Storage](#data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis)
- [Rozszerzenia: zmiany odwołania do pakietów wpływające na niektóre pakiety NuGet](#extensions-package-reference-changes-affecting-some-nuget-packages)
- [Hosting: AspNetCoreModule V1 został usunięty z pakietu hostingu systemu Windows](#hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle)
- [Hosting: Host ogólny ogranicza iniekcję konstruktora startowego](#hosting-generic-host-restricts-startup-constructor-injection)
- [Hosting: włączono przekierowywanie protokołu HTTPS dla aplikacji pozaprocesowych usług IIS](#hosting-https-redirection-enabled-for-iis-out-of-process-apps)
- [Hosting: zamieniono typy IHostingEnvironment i IApplicationLifetime](#hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced)
- [Hosting: ObjectPoolProvider usunięte z zależności WebHostBuilder](#hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies)
- [HTTP: Kestrel i IIS BadHttpRequestException typy oznaczone jako przestarzałe i zastąpione](#http-kestrel-and-iis-badhttprequestexception-types-marked-obsolete-and-replaced)
- [HTTP: zmiana SameSite w przeglądarce wpływa na uwierzytelnianie](#http-browser-samesite-changes-impact-authentication)
- [HTTP: Usunięto rozszerzalność DefaultHttpContext](#http-defaulthttpcontext-extensibility-removed)
- [HTTP: pola HeaderNames zostały zmienione na statyczny tylko do odczytu](#http-headernames-constants-changed-to-static-readonly)
- [HTTP: wystąpienia HttpClient utworzone przez kody stanu liczby całkowitej dziennika IHttpClientFactory](#http-httpclient-instances-created-by-ihttpclientfactory-log-integer-status-codes)
- [HTTP: zmiany infrastruktury treści odpowiedzi](#http-response-body-infrastructure-changes)
- [HTTP: zmieniono domyślne wartości SameSite w pliku cookie](#http-some-cookie-samesite-defaults-changed-to-none)
- [HTTP: synchroniczne operacje we/wy są wyłączone domyślnie](#http-synchronous-io-disabled-in-all-servers)
- [Tożsamość: Usunięto Przeciążenie metody AddDefaultUI](#identity-adddefaultui-method-overload-removed)
- [Tożsamość: zmiana wersji ładowania początkowego interfejsu użytkownika](#identity-default-bootstrap-version-of-ui-changed)
- [Tożsamość: SignInAsync zgłasza wyjątek dla nieuwierzytelnionej tożsamości](#identity-signinasync-throws-exception-for-unauthenticated-identity)
- [Tożsamość: Konstruktor SignInManager akceptuje nowy parametr](#identity-signinmanager-constructor-accepts-new-parameter)
- [Tożsamość: interfejs użytkownika używa funkcji statyczne zasoby sieci Web](#identity-ui-uses-static-web-assets-feature)
- [Kestrel: Usunięto karty połączeń](#kestrel-connection-adapters-removed)
- [Kestrel: Usunięto pusty zestaw HTTPS](#kestrel-empty-https-assembly-removed)
- [Kestrel: przeniesiono nagłówki przyczepki do nowej kolekcji](#kestrel-request-trailer-headers-moved-to-new-collection)
- [Kestrel: transportowe zmiany warstwy abstrakcji](#kestrel-transport-abstractions-removed-and-made-public)
- [Lokalizacja: interfejsy API oznaczone jako przestarzałe](#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete)
- [Lokalizacja: Usunięto klasę ResourceManagerWithCultureStringLocalizer i element członkowski interfejsu WithCulture](#localization-resourcemanagerwithculturestringlocalizer-class-and-withculture-interface-member-removed)
- [Rejestrowanie: Klasa DebugLogger wykonana wewnętrznie](#logging-debuglogger-class-made-internal)
- [MVC: Usunięto sufiks asynchroniczny akcji kontrolera](#mvc-async-suffix-trimmed-from-controller-action-names)
- [MVC: JsonResult przeniesiony do Microsoft. AspNetCore. MVC. Core](#mvc-jsonresult-moved-to-microsoftaspnetcoremvccore)
- [MVC: Narzędzie wstępnej kompilacji zostało zaniechane](#mvc-precompilation-tool-deprecated)
- [MVC: zmieniono typy na wewnętrzne](#mvc-pubternal-types-changed-to-internal)
- [MVC: Usunięto podkładkę zgodności z interfejsem API sieci Web](#mvc-web-api-compatibility-shim-removed)
- [Razor: Kompilacja środowiska uruchomieniowego została przeniesiona do pakietu](#razor-runtime-compilation-moved-to-a-package)
- [Stan sesji: Usunięto przestarzałe interfejsy API](#session-state-obsolete-apis-removed)
- [Współdzielona struktura: usuwanie zestawu z Microsoft. AspNetCore. App](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp)
- [Współdzielona struktura: Microsoft. AspNetCore. All usunięte](#shared-framework-removed-microsoftaspnetcoreall)
- [Sygnalizujący: HandshakeProtocol. SuccessHandshakeData został zastąpiony](#signalr-handshakeprotocolsuccesshandshakedata-replaced)
- [Sygnalizacja: Usunięto metody HubConnection](#signalr-hubconnection-resetsendping-and-resettimeout-methods-removed)
- [Sygnalizacja: zmieniono konstruktory HubConnectionContext](#signalr-hubconnectioncontext-constructors-changed)
- [Sygnalizacja: zmiana nazwy pakietu klienta języka JavaScript](#signalr-javascript-client-package-name-changed)
- [Sygnalizacja: przeniesiono protokół MessagePack Hub do pakietu MessagePack 2. x](#signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package)
- [Sygnalizacja: Zmieniono typ opcji protokołu MessagePack Hub](#signalr-messagepack-hub-protocol-options-type-changed)
- [Sygnalizujący: przestarzałe interfejsy API](#signalr-usesignalr-and-useconnections-methods-marked-obsolete)
- [Sygnalizacja: Usunięto metody UseSignalR i UseConnections](#signalr-usesignalr-and-useconnections-methods-removed)
- [Aplikacji jednostronicowych: SpaServices i NodeServices domyślna zmiana ustawień rejestru](#spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger)
- [Aplikacji jednostronicowych: SpaServices i NodeServices oznaczone jako przestarzałe](#spas-spaservices-and-nodeservices-marked-obsolete)
- [Pliki statyczne: typ zawartości CSV został zmieniony na zgodny ze standardami](#static-files-csv-content-type-changed-to-standards-compliant)
- [Platforma docelowa: nie .NET Framework obsługiwana](#target-framework-net-framework-support-dropped)

## <a name="aspnet-core-50"></a>ASP.NET Core 5,0

[!INCLUDE[Azure: Microsoft-prefixed Azure integration packages removed](~/includes/core-changes/aspnetcore/5.0/azure-integration-packages-removed.md)]

***

[!INCLUDE[Extensions: Package reference changes](~/includes/core-changes/aspnetcore/5.0/extensions-package-reference-changes.md)]

***

[!INCLUDE[HTTP: HttpClient instances created by IHttpClientFactory log integer status codes](~/includes/core-changes/aspnetcore/5.0/http-httpclient-instances-log-integer-status-codes.md)]

***

[!INCLUDE[HTTP: Kestrel and IIS BadHttpRequestException types marked obsolete and replaced](~/includes/core-changes/aspnetcore/5.0/http-badhttprequestexception-obsolete.md)]

***

[!INCLUDE[Localization: ResourceManagerWithCultureStringLocalizer class and WithCulture interface member removed](~/includes/core-changes/aspnetcore/5.0/localization-members-removed.md)]

***

[!INCLUDE[SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package](~/includes/core-changes/aspnetcore/5.0/signalr-messagepack-package.md)]

***

[!INCLUDE[SignalR: MessagePack Hub Protocol options type changed](~/includes/core-changes/aspnetcore/5.0/signalr-messagepack-hub-protocol-options-changed.md)]

***

[!INCLUDE[SignalR: UseSignalR and UseConnections methods removed](~/includes/core-changes/aspnetcore/5.0/signalr-usesignalr-useconnections-removed.md)]

***

[!INCLUDE[Static files: CSV content type changed to standards-compliant](~/includes/core-changes/aspnetcore/5.0/static-files-csv-content-type-changed.md)]

***

## <a name="aspnet-core-31"></a>ASP.NET Core 3,1

[!INCLUDE[HTTP: Browser SameSite changes impact authentication](~/includes/core-changes/aspnetcore/3.1/http-cookie-samesite-authn-impacts.md)]

***

## <a name="aspnet-core-30"></a>ASP.NET Core 3,0

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
