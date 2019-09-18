---
title: Co nowego w programie Windows Identity Foundation 4.5
ms.date: 03/30/2017
ms.assetid: 3b381f04-593b-471f-bd33-0362be1aade5
author: BrucePerlerMS
ms.openlocfilehash: 93631c1171f81ec8b8d94b56a56012343f6c3220
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045283"
---
# <a name="whats-new-in-windows-identity-foundation-45"></a>Co nowego w programie Windows Identity Foundation 4.5
Pierwsza wersja środowiska Windows Identity Foundation (WIF) była dostarczana jako autonomiczny pakiet do pobrania. Jest znana pod nazwą WIF 3.5, ponieważ została wprowadzona mniej więcej w tym samym czasie co platforma .NET 3.5 z dodatkiem SP1. Począwszy od wersji .NET 4.5 środowisko WIF jest częścią oprogramowania .NET Framework. Posiadanie klas WIF bezpośrednio dostępnych w ramach platformy pozwala na znacznie bardziej szczegółową integrację tożsamości opartej na oświadczeniach w programie .NET, ułatwiając korzystanie z oświadczeń. Aplikacje przeznaczone dla WIF 3,5 należy zmodyfikować, aby można było korzystać z nowego modelu; Aby uzyskać więcej informacji, zobacz [wytyczne dotyczące migrowania aplikacji skompilowanej za pomocą WIF 3,5 do WIF 4,5](guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md).  
  
 Poniżej zasygnalizowano kilka najważniejszych zmian.  
  
## <a name="wif-is-now-part-of-the-net-framework"></a>Program WIF jest obecnie częścią środowiska .NET Framework  
 Klasy WIF są `mscorlib`teraz rozłożone na kilka zestawów, głównych `System.IdentityModel` `System.IdentityModel.Services`,, i `System.ServiceModel`. Podobnie klasy WIF są rozłożone na kilka przestrzeni nazw: <xref:System.Security.Claims?displayProperty=nameWithType>, kilka przestrzeni nazw [System. IdentityModel](https://go.microsoft.com/fwlink/?LinkId=272004) i <xref:System.ServiceModel.Security?displayProperty=nameWithType>. Przestrzeń nazw zawiera nowe <xref:System.Security.Claims.ClaimsPrincipal> i <xref:System.Security.Claims.ClaimsIdentity> klasy (patrz poniżej). <xref:System.Security.Claims?displayProperty=nameWithType> Wszystkie podmioty zabezpieczeń w programie .NET pochodzą od <xref:System.Security.Claims.ClaimsPrincipal>. Aby uzyskać szczegółowe informacje na temat przestrzeni nazw WIF i rodzajów klas, które zawierają, zobacz [WIF API Reference](wif-api-reference.md). Aby uzyskać informacje na temat sposobu mapowania przestrzeni nazw między WIF 3,5 i WIF 4,5, zobacz [mapowanie przestrzeni nazw między WIF 3,5 i WIF 4,5](namespace-mapping-between-wif-3-5-and-wif-4-5.md).  
  
## <a name="new-claims-model-and-principal-object"></a>Nowy model oświadczeń i podmiotu zabezpieczeń  
 Funkcjonalność oświadczeń jest sercem środowiska .NET Framework 4.5. Podstawowe<xref:System.Security.Claims.Claim>klasy roszczeń (, <xref:System.Security.Claims.ClaimsIdentity>, <xref:System.Security.Claims.ClaimsPrincipal> <xref:System.Security.Claims.ClaimTypes>, i `mscorlib` <xref:System.Security.Claims?displayProperty=nameWithType> ) wszystkie aktywne bezpośrednio w przestrzeni nazw. <xref:System.Security.Claims.ClaimValueTypes> Nie jest już konieczne używanie interfejsów w celu podłączenia oświadczeń do systemu <xref:System.Security.Principal.WindowsPrincipal>tożsamości .NET:, <xref:System.Security.Principal.GenericPrincipal>, i <xref:System.Web.Security.RolePrincipal> teraz dziedziczenia z <xref:System.Security.Claims.ClaimsPrincipal>; i <xref:System.Security.Principal.WindowsIdentity>, <xref:System.Security.Principal.GenericIdentity>, i <xref:System.Web.Security.FormsIdentity> teraz dziedziczenia z <xref:System.Security.Claims.ClaimsIdentity>programu. Innymi słowy teraz każda klasa podmiotów zabezpieczeń obsługuje oświadczenia. Klasy i interfejsy integracji WIF 3,5`WindowsClaimsIdentity`(, `WindowsClaimsPrincipal`, `IClaimsPrincipal` `IClaimsIdentity`,) zostały usunięte. Ponadto <xref:System.Security.Claims.ClaimsIdentity> Klasa uwidacznia teraz metody, które ułatwiają zapytanie do kolekcji oświadczeń tożsamości.  
  
## <a name="changes-to-the-wif-45-visual-studio-experience"></a>Zmiany funkcjonalności programu Visual Studio w środowisku WIF 4.5  
  
- **Dodawanie odwołania do usługi STS...** Funkcja programu Visual Studio (Narzędzie Cmdlines FedUtil) już nie istnieje; Zamiast tego możesz użyć nowej usługi Visual Studio Extension **Identity i Access Tool dla programu Visual studio 2012**. Dzięki niemu w celu przetestowania rozwiązania można utworzyć federację z istniejącą usługą STS albo skorzystać z usługi LocalSTS. Po zainstalowaniu rozszerzenia można kliknąć prawym przyciskiem myszy projekt i poszukać **tożsamości i dostępu** w menu kontekstowym.  
  
- Nie ma już szablonów środowiska ASP.NET ani usługi STS, ponieważ oświadczeń można obecnie używać bezpośrednio w istniejących szablonach projektów środowiska ASP.Net, witryn internetowych i środowiska WCF.  
  
- Kontrolki w `Microsoft.IdentityModel.Web.Controls` przestrzeni nazw (`SignInControl`, `FederatedPassiveSignInControl`i `FederatedPassiveSignInStatus`) nie są przenoszone do WIF 4,5.  
  
## <a name="changes-to-the-wif-45-api"></a>Zmiany w interfejsie API programu WIF 4.5  
  
- Ogólnie rzecz biorąc, powiązane klasy oświadczeń znajdują <xref:System.Security.Claims?displayProperty=nameWithType> się w przestrzeni nazw; Klasy pokrewne WCF — kontrakty usług, kanały, fabryki kanałów i hosty usług, które są używane na potrzeby scenariuszy usługi WS-Trust — są <xref:System.ServiceModel.Security?displayProperty=nameWithType>w systemie; i wszystkie inne klasy WIF są rozproszone w różnych przestrzeniach nazw [System. IdentityModel](https://go.microsoft.com/fwlink/?LinkId=272004) — obejmują one na przykład klasy reprezentujące artefakty WS-* i SAML, programy obsługi tokenów i klasy pokrewne oraz klasy używane w scenariuszach usługi WS-Federation. Aby uzyskać więcej informacji, zobacz [mapowanie przestrzeni nazw między WIF 3,5 i WIF 4,5](namespace-mapping-between-wif-3-5-and-wif-4-5.md) i [WIF API Reference](wif-api-reference.md).  
  
- W scenariuszach z farmami internetowymi można w plikach cookie sesji używać klucza komputera. Aby uzyskać więcej informacji, zobacz [WIF i farmy serwerów sieci Web](wif-and-web-farms.md).  
  
- Teraz można deklaratywnie skonfigurować WIF pod [ \<kątem elementów > System. IdentityModel >](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) i [ \<system. IdentityModel. Services](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) . Aby uzyskać więcej informacji na temat konfiguracji WIF, zobacz [WIF Configuration Reference](wif-configuration-reference.md).  
  
## <a name="other-notable-net-changes-or-features-that-are-caused-by-the-integration-of-wif-into-net"></a>Inne znaczące zmiany lub funkcje w środowisku .NET spowodowane zintegrowaniem z nim środowiska WIF  
  
- Funkcjonalność wykonywania autoryzacji opartej na oświadczeniach (CBAC) jest teraz zintegrowana w środowisku .NET. Można skonfigurować <xref:System.Security.Claims.ClaimsAuthorizationManager> obiekt, a następnie <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> użyć klas i <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> do wykonywania bezwzględnych i deklaratywnych kontroli dostępu w kodzie. Autoryzacja CBAC zapewnia większą elastyczność i szczegółowość tradycyjna kontrola dostępu oparta na rolach (RBAC). Umożliwia również szersze rozdzielenie zasad autoryzacji z logiki biznesowej, ponieważ logika biznesowa może opierać się na sprawdzaniu dostępu do określonego oświadczenia lub zestawu oświadczeń, a zasady autoryzacji dla tych oświadczeń można skonfigurować deklaratywnie w ramach [ składnikaClaimsAuthorizationManager\<>](../configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md) elementu.  
  
## <a name="wcf-changes-as-a-result-of-wif-integration"></a>Zmiany w środowisku WCF wskutek zintegrowania środowiska WIF:  
  
- Model zarządzania tożsamościami oparty na oświadczeniach stosowany w środowisku WCF jest zastąpiony modelem ze środowiska WIF. Oznacza to, że klasy w <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType>i i <xref:System.IdentityModel.Selectors?displayProperty=nameWithType> przestrzenie nazw powinny być porzucane na korzyść przy użyciu klas WIF.  
  
- Usługa WIF jest teraz włączona w usłudze WCF, określając `useIdentityConfiguration` atrybut `<system.serviceModel>` `<behaviors>` / `<serviceBehaviors>` / w elemencie,jakwponiższymkodzieXML:/ `<serviceCredentials>`  
  
    ```xml  
    <serviceCredentials useIdentityConfiguration="true">  
        <!--Certificate added by Identity And Access VS Package.  Subject='CN=localhost', Issuer='CN=localhost'. Make sure you have this certificate installed. The Identity and Access tool does not install this certificate.-->  
        <serviceCertificate findValue="CN=localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectDistinguishedName" />  
    </serviceCredentials>  
    ```  
  
     W przypadku korzystania z **Narzędzia do obsługi tożsamości i dostępu dla programu Visual Studio 2012** (zobacz zmiany w powyższym **doświadczeniu programu Visual Studio** ) `<serviceCredentials>` narzędzie dodaje `useIdentityConfiguration` element z atrybutem ustawionym na plik konfiguracji. Dodaje również odpowiedni [ \<element System. IdentityModel >](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) , który zawiera ustawienia konfiguracji WIF i dodaje powiązanie i inne ustawienia niezbędne do uwierzytelnienia w ramach wybranej usługi STS.  
  
## <a name="see-also"></a>Zobacz także

- [Wskazówki dotyczące migrowania aplikacji utworzonych za pomocą programu WIF 3.5 do wersji WIF 4.5](guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md)
- [Mapowanie przestrzeni nazw między programami WIF 3.5 i WIF 4.5](namespace-mapping-between-wif-3-5-and-wif-4-5.md)
- [Dokumentacja interfejsu API programu WIF](wif-api-reference.md)
- [Odwołanie konfiguracji programu WIF](wif-configuration-reference.md)
