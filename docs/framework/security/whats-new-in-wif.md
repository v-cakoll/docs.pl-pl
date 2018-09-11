---
title: Co&#39;s Nowość w wersji Windows Identity Foundation 4.5
ms.date: 03/30/2017
ms.assetid: 3b381f04-593b-471f-bd33-0362be1aade5
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 2a275c32caefb54b11cc605c1339526465c8319a
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44269335"
---
# <a name="what39s-new-in-windows-identity-foundation-45"></a>Co&#39;s Nowość w wersji Windows Identity Foundation 4.5
Pierwsza wersja środowiska Windows Identity Foundation (WIF) była dostarczana jako autonomiczny pakiet do pobrania. Jest znana pod nazwą WIF 3.5, ponieważ została wprowadzona mniej więcej w tym samym czasie co platforma .NET 3.5 z dodatkiem SP1. Począwszy od wersji .NET 4.5 środowisko WIF jest częścią oprogramowania .NET Framework. Klasy programu WIF bezpośrednio dostępne w ramach pozwala na znacznie głębszą integrację tożsamości opartej na oświadczeniach na platformie .NET, ułatwiając korzystanie z oświadczeń. Aplikacje napisane dla środowiska WIF 3.5 należy można zmodyfikować, aby można było korzystać z zalet nowego modelu; Aby uzyskać informacje, zobacz [Guidelines for Migrating an Application Built Using WIF 3.5 to WIF 4.5](../../../docs/framework/security/guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md).  
  
 Poniżej zasygnalizowano kilka najważniejszych zmian.  
  
## <a name="wif-is-now-part-of-the-net-framework"></a>Program WIF jest obecnie częścią środowiska .NET Framework  
 Klasy WIF są teraz rozproszone między kilka zestawów. najważniejsze z nich jest `mscorlib`, `System.IdentityModel`, `System.IdentityModel.Services`, i `System.ServiceModel`. Analogicznie klasy środowiska WIF są rozproszone między różne przestrzenie nazw: <xref:System.Security.Claims?displayProperty=nameWithType>, kilka [System.IdentityModel](https://go.microsoft.com/fwlink/?LinkId=272004) przestrzeni nazw, a <xref:System.ServiceModel.Security?displayProperty=nameWithType>. <xref:System.Security.Claims?displayProperty=nameWithType> Przestrzeń nazw zawiera nowe <xref:System.Security.Claims.ClaimsPrincipal> i <xref:System.Security.Claims.ClaimsIdentity> klasy (patrz poniżej). Wszystkie podmioty zabezpieczeń w środowisku .NET pochodzą teraz od <xref:System.Security.Claims.ClaimsPrincipal>. Aby uzyskać szczegółowe informacje o przestrzeniach nazw środowiska WIF oraz rodzajach klas, które zawierają, zobacz [WIF API Reference](../../../docs/framework/security/wif-api-reference.md). Aby uzyskać informacji na temat sposobu mapowania przestrzeni nazw między WIF 3.5 i WIF 4.5, zobacz [Namespace mapowanie między WIF 3.5 i WIF 4.5](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md).  
  
## <a name="new-claims-model-and-principal-object"></a>Nowy model oświadczeń i podmiotu zabezpieczeń  
 Funkcjonalność oświadczeń jest sercem środowiska .NET Framework 4.5. Podstawowe klasy oświadczeń (<xref:System.Security.Claims.Claim>, <xref:System.Security.Claims.ClaimsIdentity>, <xref:System.Security.Claims.ClaimsPrincipal>, <xref:System.Security.Claims.ClaimTypes>, i <xref:System.Security.Claims.ClaimValueTypes>) bezpośrednio w `mscorlib` w <xref:System.Security.Claims?displayProperty=nameWithType> przestrzeni nazw. Nie jest już używać interfejsów, aby podłączyć oświadczenia do systemu tożsamości platformy .NET: <xref:System.Security.Principal.WindowsPrincipal>, <xref:System.Security.Principal.GenericPrincipal>, i <xref:System.Web.Security.RolePrincipal> teraz dziedziczyć <xref:System.Security.Claims.ClaimsPrincipal>; i <xref:System.Security.Principal.WindowsIdentity>, <xref:System.Security.Principal.GenericIdentity>, i <xref:System.Web.Security.FormsIdentity> teraz dziedziczenie z <xref:System.Security.Claims.ClaimsIdentity>. Innymi słowy teraz każda klasa podmiotów zabezpieczeń obsługuje oświadczenia. Program WIF 3.5 integracji klasy i interfejsy (`WindowsClaimsIdentity`, `WindowsClaimsPrincipal`, `IClaimsPrincipal`, `IClaimsIdentity`) związku z tym została usunięta. Ponadto <xref:System.Security.Claims.ClaimsIdentity> kolekcji oświadczeń klasy teraz udostępnia metody, które ułatwiają zapytania o tożsamości.  
  
## <a name="changes-to-the-wif-45-visual-studio-experience"></a>Zmiany funkcjonalności programu Visual Studio w środowisku WIF 4.5  
  
-   **Dodaj odwołanie do usługi STS...** Visual Studio funkcji (narzędzie wiersza polecenia fedutil) już nie istnieje; Zamiast tego można użyć nowego rozszerzenia programu Visual Studio **narzędzie tożsamości i dostępu dla programu Visual Studio 2012**. Dzięki niemu w celu przetestowania rozwiązania można utworzyć federację z istniejącą usługą STS albo skorzystać z usługi LocalSTS. Po zainstalowaniu rozszerzenia można kliknąć prawym przyciskiem myszy nad projektem i poszukaj **tożsamościami i dostępem** w menu kontekstowym.  
  
-   Nie ma już szablonów środowiska ASP.NET ani usługi STS, ponieważ oświadczeń można obecnie używać bezpośrednio w istniejących szablonach projektów środowiska ASP.Net, witryn internetowych i środowiska WCF.  
  
-   Formanty w `Microsoft.IdentityModel.Web.Controls` przestrzeni nazw (`SignInControl`, `FederatedPassiveSignInControl`, i `FederatedPassiveSignInStatus`) nie są przenoszone do programu WIF 4.5.  
  
## <a name="changes-to-the-wif-45-api"></a>Zmiany w interfejsie API programu WIF 4.5  
  
-   Ogólnie rzecz biorąc, klasy pokrewne oświadczeń znajdują się w <xref:System.Security.Claims?displayProperty=nameWithType> przestrzeni nazw; WCF pokrewne klasy — — kontraktów usług, kanały, fabryki kanałów i hosty usług, które są używane na potrzeby scenariuszy, WS-Trust znajdują się w <xref:System.ServiceModel.Security?displayProperty=nameWithType>; i wszystkie pozostałe klasy środowiska WIF są rozproszone między różne [System.IdentityModel](https://go.microsoft.com/fwlink/?LinkId=272004) przestrzenie nazw — obejmują one, na przykład klas, które reprezentują WS-* i artefaktów SAML, programy obsługi tokenów i powiązanych klas i klasy używane w scenariuszach WS-Federation. Aby uzyskać więcej informacji, zobacz [Namespace mapowanie między WIF 3.5 i WIF 4.5](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md) i [WIF API Reference](../../../docs/framework/security/wif-api-reference.md).  
  
-   W scenariuszach z farmami internetowymi można w plikach cookie sesji używać klucza komputera. Aby uzyskać więcej informacji, zobacz [programu WIF i farmy serwerów sieci Web](../../../docs/framework/security/wif-and-web-farms.md).  
  
-   Możesz teraz sposób deklaratywny można skonfigurować środowisko WIF [ \<system.identityModel >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) i [ \<system.identityModel.services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) elementów. Aby uzyskać więcej informacji na temat konfiguracji programu WIF, zobacz [WIF Configuration Reference](../../../docs/framework/security/wif-configuration-reference.md).  
  
## <a name="other-notable-net-changes-or-features-that-are-caused-by-the-integration-of-wif-into-net"></a>Inne znaczące zmiany lub funkcje w środowisku .NET spowodowane zintegrowaniem z nim środowiska WIF  
  
-   Funkcjonalność wykonywania autoryzacji opartej na oświadczeniach (CBAC) jest teraz zintegrowana w środowisku .NET. Można skonfigurować <xref:System.Security.Claims.ClaimsAuthorizationManager> obiektu, a następnie użyj <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> i <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> klasy do wykonywania kontroli dostępu imperatywną lub deklaratywną w kodzie. Autoryzacja CBAC zapewnia większą elastyczność i szczegółowość tradycyjna kontrola dostępu oparta na rolach (RBAC). Umożliwia również mocniej zasady autoryzacji od logiki biznesowej, ponieważ logika biznesowa może opierać kontrolę dostępu na określonych oświadczenia lub zestaw oświadczeń i zasady autoryzacji tych oświadczeń można skonfigurować deklaratywnie w obszarze [ \<składnika claimsAuthorizationManager >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md) elementu.  
  
## <a name="wcf-changes-as-a-result-of-wif-integration"></a>Zmiany w środowisku WCF wskutek zintegrowania środowiska WIF:  
  
-   Model zarządzania tożsamościami oparty na oświadczeniach stosowany w środowisku WCF jest zastąpiony modelem ze środowiska WIF. Oznacza to, że klasy w <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType>, i <xref:System.IdentityModel.Selectors?displayProperty=nameWithType> przestrzenie nazw powinny być odrzucane na rzecz klas środowiska WIF.  
  
-   Program WIF jest teraz włączony w usłudze WCF poprzez określenie `useIdentityConfiguration` atrybutu na `<system.serviceModel>` / `<behaviors>` / `<serviceBehaviors>` / `<serviceCredentials>` elementu, tak jak następujący kod XML:  
  
    ```xml  
    <serviceCredentials useIdentityConfiguration="true">  
        <!--Certificate added by Identity And Access VS Package.  Subject='CN=localhost', Issuer='CN=localhost'. Make sure you have this certificate installed. The Identity and Access tool does not install this certificate.-->  
        <serviceCertificate findValue="CN=localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectDistinguishedName" />  
    </serviceCredentials>  
    ```  
  
     Kiedy używasz **narzędzie tożsamości i dostępu dla programu Visual Studio 2012** (zobacz **zmieni się na środowisko programu Visual Studio** powyżej), narzędzie automatycznie dodaje `<serviceCredentials>` element z `useIdentityConfiguration` ustawioną wartość atrybutu plik konfiguracji dla Ciebie. Ponadto dodaje odnośny [ \<system.identityModel >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) element, który zawiera ustawienia konfiguracji programu WIF i dodaje powiązanie i inne ustawienia, które są wymagane w celu oddelegowania procesów uwierzytelniania do wybranej usługi STS.  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki dotyczące migrowania aplikacji utworzonych za pomocą programu WIF 3.5 do wersji WIF 4.5](../../../docs/framework/security/guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md)  
 [Mapowanie przestrzeni nazw między programami WIF 3.5 i WIF 4.5](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md)  
 [Dokumentacja interfejsu API programu WIF](../../../docs/framework/security/wif-api-reference.md)  
 [Odwołanie konfiguracji programu WIF](../../../docs/framework/security/wif-configuration-reference.md)
