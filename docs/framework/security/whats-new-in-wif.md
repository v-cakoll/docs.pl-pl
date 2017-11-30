---
title: "Jaki &#39; s Nowość w systemie Windows Identity Foundation 4.5"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b381f04-593b-471f-bd33-0362be1aade5
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 19116aba3049dce6612ca1a7170030f7ced6705e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="what39s-new-in-windows-identity-foundation-45"></a>Jaki &#39; s Nowość w systemie Windows Identity Foundation 4.5
Pierwsza wersja środowiska Windows Identity Foundation (WIF) była dostarczana jako autonomiczny pakiet do pobrania. Jest znana pod nazwą WIF 3.5, ponieważ została wprowadzona mniej więcej w tym samym czasie co platforma .NET 3.5 z dodatkiem SP1. Począwszy od wersji .NET 4.5 środowisko WIF jest częścią oprogramowania .NET Framework. O klasach WIF bezpośrednio dostępne w ramach pozwala na znacznie lepsza integracja tożsamości opartego na oświadczeniach w programie .NET, co ułatwia użyć oświadczeń. Aplikacje napisane dla WIF 3.5 będzie muszą zostać zmodyfikowane, aby korzystać z nowego modelu; Aby uzyskać informacje, zobacz [wskazówki dotyczące migrowania aplikacji utworzony za pomocą programu WIF 3.5 WIF 4.5](../../../docs/framework/security/guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md).  
  
 Poniżej zasygnalizowano kilka najważniejszych zmian.  
  
## <a name="wif-is-now-part-of-the-net-framework"></a>Program WIF jest obecnie częścią środowiska .NET Framework  
 Klasy WIF teraz są rozkładane między kilka zestawów, podstawowe są `mscorlib`, `System.IdentityModel`, `System.IdentityModel.Services`, i `System.ServiceModel`. Podobnie, klas WIF są rozkładane między kilka przestrzeni nazw: <xref:System.Security.Claims?displayProperty=nameWithType>, kilka [System.IdentityModel](http://go.microsoft.com/fwlink/?LinkId=272004) przestrzeni nazw, i <xref:System.ServiceModel.Security?displayProperty=nameWithType>. <xref:System.Security.Claims?displayProperty=nameWithType> Przestrzeń nazw zawiera nowe <xref:System.Security.Claims.ClaimsPrincipal> i <xref:System.Security.Claims.ClaimsIdentity> klasy (patrz poniżej). Teraz dziedziczyć wszystkich podmiotów zabezpieczeń w programie .NET <xref:System.Security.Claims.ClaimsPrincipal>. Aby uzyskać szczegółowe informacje o przestrzeni nazw WIF i rodzajami klas, które zawierają, zobacz [dokumentacja interfejsu API WIF](../../../docs/framework/security/wif-api-reference.md). Aby uzyskać informacje dotyczące sposobu mapowania przestrzeni nazw między WIF 3.5 i WIF 4.5, zobacz [Namespace mapowanie między WIF 3.5 i WIF 4.5](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md).  
  
## <a name="new-claims-model-and-principal-object"></a>Nowy model oświadczeń i podmiotu zabezpieczeń  
 Funkcjonalność oświadczeń jest sercem środowiska .NET Framework 4.5. Podstawowym oświadczeń klasy (<xref:System.Security.Claims.Claim>, <xref:System.Security.Claims.ClaimsIdentity>, <xref:System.Security.Claims.ClaimsPrincipal>, <xref:System.Security.Claims.ClaimTypes>, i <xref:System.Security.Claims.ClaimValueTypes>) na żywo wszystkie bezpośrednio w `mscorlib` w <xref:System.Security.Claims?displayProperty=nameWithType> przestrzeni nazw. Nie jest już używać interfejsów, aby podłączyć oświadczenia do systemu tożsamości platformy .NET: <xref:System.Security.Principal.WindowsPrincipal>, <xref:System.Security.Principal.GenericPrincipal>, i <xref:System.Web.Security.RolePrincipal> teraz dziedziczyć <xref:System.Security.Claims.ClaimsPrincipal>; i <xref:System.Security.Principal.WindowsIdentity>, <xref:System.Security.Principal.GenericIdentity>, i <xref:System.Web.Security.FormsIdentity> teraz dziedziczą z <xref:System.Security.Claims.ClaimsIdentity>. Innymi słowy teraz każda klasa podmiotów zabezpieczeń obsługuje oświadczenia. WIF 3.5 integracji klasy i interfejsy (`WindowsClaimsIdentity`, `WindowsClaimsPrincipal`, `IClaimsPrincipal`, `IClaimsIdentity`) w związku z tym zostały usunięte. Ponadto <xref:System.Security.Claims.ClaimsIdentity> klasy teraz udostępnia metody, które ułatwiają zapytania tożsamości oświadczeń kolekcji.  
  
## <a name="changes-to-the-wif-45-visual-studio-experience"></a>Zmiany funkcjonalności programu Visual Studio w środowisku WIF 4.5  
  
-   **Dodaj odwołanie do usługi STS...** Visual Studio funkcji (narzędzie cmdline FedUtil) już istnieje; Zamiast tego można użyć nowego rozszerzenia programu Visual Studio **tożsamości i dostępu do narzędzi dla programu Visual Studio 2012**. Dzięki niemu w celu przetestowania rozwiązania można utworzyć federację z istniejącą usługą STS albo skorzystać z usługi LocalSTS. Po zainstalowaniu rozszerzenia kliknij prawym przyciskiem myszy projekt i poszukaj **tożsamościami i dostępem** w menu kontekstowym.  
  
-   Nie ma już szablonów środowiska ASP.NET ani usługi STS, ponieważ oświadczeń można obecnie używać bezpośrednio w istniejących szablonach projektów środowiska ASP.Net, witryn internetowych i środowiska WCF.  
  
-   Formanty w `Microsoft.IdentityModel.Web.Controls` przestrzeni nazw (`SignInControl`, `FederatedPassiveSignInControl`, i `FederatedPassiveSignInStatus`) nie są przenoszone do wersji WIF 4.5.  
  
## <a name="changes-to-the-wif-45-api"></a>Zmiany w interfejsie API programu WIF 4.5  
  
-   Ogólnie rzecz biorąc, powiązanymi klasami oświadczenia są w <xref:System.Security.Claims?displayProperty=nameWithType> przestrzeni nazw; WCF związane z klasy — — usługa umów, kanały, fabryk kanałów i hosty usługi, które są używane w scenariuszach WS-Trust — są w <xref:System.ServiceModel.Security?displayProperty=nameWithType>; oraz wszystkich innych klas WIF są rozkładane między różnymi [System.IdentityModel](http://go.microsoft.com/fwlink/?LinkId=272004) przestrzenie nazw — do nich, na przykład klasy reprezentujące WS-* i artefaktów SAML token programów obsługi i powiązanych klas i klasy używane w scenariuszach WS-Federation. Aby uzyskać więcej informacji, zobacz [Namespace mapowanie między WIF 3.5 i WIF 4.5](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md) i [dokumentacja interfejsu API WIF](../../../docs/framework/security/wif-api-reference.md).  
  
-   W scenariuszach z farmami internetowymi można w plikach cookie sesji używać klucza komputera. Aby uzyskać więcej informacji, zobacz [WIF i farmy serwerów sieci Web](../../../docs/framework/security/wif-and-web-farms.md).  
  
-   Teraz deklaratywnie skonfigurować WIF w obszarze [ \<system.identityModel >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) i [ \<system.identityModel.services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) elementów. Aby uzyskać więcej informacji na temat konfiguracji WIF zobacz [WIF konfiguracji odwołania](../../../docs/framework/security/wif-configuration-reference.md).  
  
## <a name="other-notable-net-changes-or-features-that-are-caused-by-the-integration-of-wif-into-net"></a>Inne znaczące zmiany lub funkcje w środowisku .NET spowodowane zintegrowaniem z nim środowiska WIF  
  
-   Funkcjonalność wykonywania autoryzacji opartej na oświadczeniach (CBAC) jest teraz zintegrowana w środowisku .NET. Można skonfigurować <xref:System.Security.Claims.ClaimsAuthorizationManager> obiekt, a następnie użyj <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> i <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> klasy do wykonywania kontroli dostępu konieczne a declarative w kodzie. Autoryzacja CBAC zapewnia większą elastyczność i szczegółowość tradycyjna kontrola dostępu oparta na rolach (RBAC). Umożliwia także większa rozdzielenie zasady autoryzacji logiki biznesowej ponieważ logiki biznesowej można oprzeć kontroli dostępu określone oświadczenie lub zestaw oświadczeń i zasady autoryzacji dla tych oświadczeń można skonfigurować w obszarze deklaratywnie[ \<claimsAuthorizationManager >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md) elementu.  
  
## <a name="wcf-changes-as-a-result-of-wif-integration"></a>Zmiany w środowisku WCF wskutek zintegrowania środowiska WIF:  
  
-   Model zarządzania tożsamościami oparty na oświadczeniach stosowany w środowisku WCF jest zastąpiony modelem ze środowiska WIF. Oznacza to, że klasy w <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType>, i <xref:System.IdentityModel.Selectors?displayProperty=nameWithType> przestrzenie nazw powinny być odrzucane na rzecz przy użyciu klasy WIF.  
  
-   WIF jest teraz włączone usługi WCF, określając `useIdentityConfiguration` atrybutu `<system.serviceModel>` / `<behaviors>` / `<serviceBehaviors>` / `<serviceCredentials>` element jak następujący kod XML:  
  
    ```xml  
    <serviceCredentials useIdentityConfiguration="true">  
        <!--Certificate added by Identity And Access VS Package.  Subject='CN=localhost', Issuer='CN=localhost'. Make sure you have this certificate installed. The Identity and Access tool does not install this certificate.-->  
        <serviceCertificate findValue="CN=localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectDistinguishedName" />  
    </serviceCredentials>  
    ```  
  
     Korzystając **tożsamości i dostępu do narzędzi dla programu Visual Studio 2012** (zobacz **zmiany do środowiska Visual Studio** powyżej), dodaje `<serviceCredentials>` element z `useIdentityConfiguration` ustawić atrybutu Plik konfiguracyjny dla Ciebie. Dodano również odpowiedniego [ \<system.identityModel >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) element, który zawiera ustawienia konfiguracji WIF i dodaje powiązania i inne ustawienia, które są wymagane do uwierzytelniania wybranego STS zewnętrzny.  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki dotyczące migrowania aplikacji utworzony za pomocą programu WIF 3.5 do wersji WIF 4.5](../../../docs/framework/security/guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md)  
 [Namespace mapowanie między WIF 3.5 i WIF 4.5](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md)  
 [Dokumentacja interfejsu API WIF](../../../docs/framework/security/wif-api-reference.md)  
 [Odwołanie do konfiguracji WIF](../../../docs/framework/security/wif-configuration-reference.md)
