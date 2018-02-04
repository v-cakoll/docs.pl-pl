---
title: "Model programowania oświadczeń WIF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 149cb875-9b1c-4695-b88a-fbf1725a02f9
caps.latest.revision: 
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 1bd84e6a1e6fb0d4808dca42af2e2916be1133a3
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
---
# <a name="wif-claims-programming-model"></a>Model programowania oświadczeń WIF
ASP.NET i Windows Communication Foundation (WCF) deweloperzy zazwyczaj używać interfejsów tożsamości i IPrincipal do pracy z informacji o tożsamości użytkownika. W programie .NET 4.5 Windows Identity Foundation (WIF) jest zintegrowana w taki sposób, że istnieją oświadczenia teraz zawsze dla dowolnego podmiotu, jak pokazano na poniższym diagramie:  
  
 ![Model programowania oświadczeń WIF](../../../docs/framework/security/media/wifclaimsprogrammingmodel.png "WIFClaimsProgrammingModel")  
  
 W programie .NET 4.5 System.Security.Claims zawiera nowe klasy ClaimsPrincipal i ClaimsIdentity (patrz rysunek powyżej). Wszystkich podmiotów zabezpieczeń w programie .NET teraz pochodzić od ClaimsPrincipal. Wszystkie klasy wbudowane tożsamości, takich jak FormsIdentity dla platformy ASP.NET i teraz WindowsIdentity pochodzić od elementu ClaimsIdentity. Podobnie wszystkie wbudowanych klas głównych, takich jak GenericPrincipal i WindowsPrincipal pochodzić od ClaimsPrincipal.  
  
 Oświadczenia jest reprezentowana przez <xref:System.Security.Claims.Claim> klasy. Ta klasa ma następujące właściwości ważne:  
  
-   <xref:System.Security.Claims.Claim.Type%2A>reprezentuje typ oświadczenia i zwykle jest identyfikatorem URI. Na przykład oświadczenia adresu e-mail jest reprezentowany jako `http://schemas.microsoft.com/ws/2008/06/identity/claims/email`.  
  
-   <xref:System.Security.Claims.Claim.Value%2A>zawiera wartość oświadczenia i jest reprezentowany jako ciąg. Na przykład adres e-mail może być reprezentowana jako "someone@contoso.com".  
  
-   <xref:System.Security.Claims.Claim.ValueType%2A>reprezentuje typ wartości oświadczenia i zwykle jest identyfikatorem URI. Na przykład typ string jest reprezentowany jako `http://www.w3.org/2001/XMLSchema#string`. Typ wartości musi być QName schemat XML. Wartość powinna być w formacie `namespace#format` umożliwiające WIF do wyjściowego Nieprawidłowa nazwa QName. Jeśli przestrzeń nazw nie jest dobrze zdefiniowany przestrzeni nazw, XML wygenerowanych prawdopodobnie nie może być schemat sprawdzania poprawności, ponieważ nie będzie opublikowanego pliku XSD dla tej przestrzeni nazw. Typ wartości domyślnej jest `http://www.w3.org/2001/XMLSchema#string`. Zobacz [http://www.w3.org/2001/XMLSchema](http://go.microsoft.com/fwlink/?LinkId=209155) dla wartości dobrze znane typy, które można bezpiecznie.  
  
-   <xref:System.Security.Claims.Claim.Issuer%2A>jest to identyfikator usługę tokenu zabezpieczającego (STS), który wystawił oświadczenie. To może być reprezentowana jako adres URL usługi STS lub nazwę, która reprezentuje STS, takich jak `https://sts1.contoso.com/sts`.  
  
-   <xref:System.Security.Claims.Claim.OriginalIssuer%2A>to identyfikator Usługa tokenu Zabezpieczającego, które wystawił oryginalne oświadczenie, niezależnie od tego, ile STSs znajdują się w łańcuchu. To jest reprezentowana w podobny sposób jak <xref:System.Security.Claims.Claim.Issuer%2A>.  
  
-   <xref:System.Security.Claims.Claim.Subject%2A>jest podmiotu, której tożsamość jest kontrolowany. Zawiera on element <xref:System.Security.Claims.ClaimsIdentity>.  
  
-   <xref:System.Security.Claims.Claim.Properties%2A>jest słownikiem deweloperom zawierają dane specyficzne dla aplikacji do przeniesienia umieszczonego wraz z innymi właściwościami i może służyć do niestandardowego sprawdzania poprawności.  
  
## <a name="identity-delegation"></a>Delegowanie tożsamości  
 Ważną właściwością <xref:System.Security.Claims.ClaimsIdentity> jest <xref:System.Security.Claims.ClaimsIdentity.Actor%2A>. Ta właściwość umożliwia delegowanie poświadczeń w systemie wielowarstwowych, w którym warstwy środkowej działa jako klient na wysyłanie żądań do usługi zaplecza.  
  
### <a name="accessing-claims-through-threadcurrentprincipal"></a>Dostęp do oświadczeń za pośrednictwem Thread.CurrentPrincipal  
 Aby uzyskać dostęp do bieżącego użytkownika zestaw oświadczeń w aplikacji planu odzyskiwania, należy użyć `Thread.CurrentPrincipal`.  
  
 Poniższy przykładowy kod przedstawia sposób użycia tej metody, aby uzyskać System.Security.Claims.ClaimsIdentity:  
  
```  
ClaimsPrincipal claimsPrincipal = Thread.CurrentPrincipal as ClaimsPrincipal;  
```  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Security.Claims>.  
  
### <a name="role-claim-type"></a>Typ oświadczenia roli  
 Część konfigurowania aplikacji planu odzyskiwania ma na celu określenie, jakie rola użytkownika oświadczeń powinien być typu. Ten typ oświadczenia jest używany przez System.Security.Claims.ClaimsPrincipal.IsInRole(System.String). Domyślny typ oświadczenia jest `http://schemas.microsoft.com/ws/2008/06/identity/claims/role`.  
  
### <a name="claims-extracted-by-windows-identity-foundation-from-different-token-types"></a>Wyodrębniony przez środowisko Windows Identity Foundation z różnych typów tokenu oświadczeń  
 WIF obsługuje kilku kombinacji mechanizmów uwierzytelniania poza pole. W poniższej tabeli wymieniono oświadczenia, które WIF wyodrębnia z różnych typów tokenu.  
  
|Typ tokenu|Oświadczenia generowane|Mapy do tokena dostępu systemu Windows|  
|-|-|-|  
|SAML 1.1|1.  Wszystkie oświadczenia z System.IdentityModel.SecurityTokenService.GetOutputClaimsIdentity(System.Security.Claims.ClaimsPrincipal,System.IdentityModel.Protocols.WSTrust.RequestSecurityToken,System.IdentityModel.Scope).<br />2.  `http://schemas.microsoft.com/ws/2008/06/identity/claims/confirmationkey` Oświadczenie, które zawiera serializacja XML klucza potwierdzającego, jeśli token zawiera token potwierdzenia.<br />3.  `http://schemas.microsoft.com/ws/2008/06/identity/claims/samlissuername` Oświadczeń z elementu wystawcy.<br />4.  AuthenticationMethod AuthenticationInstant oświadczeń i, jeśli token zawiera instrukcję uwierzytelniania.|Oprócz oświadczenia na liście "SAML 1.1", z wyjątkiem oświadczeń typu `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name`, zostaną dodane oświadczenia i tożsamość będą reprezentowane przez WindowsClaimsIdentity związane z uwierzytelnianiem systemu Windows.|  
|SAML 2.0|Taka sama jak "SAML 1.1".|Taka sama jak "SAML 1.1 mapowane na konta systemu Windows".|  
|X509|1.  Oświadczenia o X500 rozróżnianych nazwę, nazwa_e-mail, dnsName, SimpleName, UpnName, UrlName, odcisku palca, RsaKey (to można wyodrębnić przy użyciu metody RSACryptoServiceProvider.ExportParameters z właściwości X509Certificate2.PublicKey.Key), DsaKey () to można wyodrębnić przy użyciu metody DSACryptoServiceProvider.ExportParameters z właściwości X509Certificate2.PublicKey.Key), z X509 właściwości numer seryjny certyfikatu.<br />2.  AuthenticationMethod oświadczenie z wartością `http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/x509`. AuthenticationInstant oświadczenie z wartością czasu, jeśli certyfikat został zweryfikowany w formacie daty/godziny schematu XML.|1.  Używa nazwy FQDN konta systemu Windows jako `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name` wartości oświadczenia. .<br />2.  Oświadczeń z X509 certyfikat nie jest zamapowany do systemu Windows i z konta systemu windows uzyskany przez mapowanie certyfikat do systemu Windows.|  
|UPN|1.  Oświadczenia są podobne do oświadczeń w sekcji uwierzytelnianie systemu Windows.<br />2.  AuthenticationMethod oświadczenie z wartością `http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/password`. AuthenticationInstant oświadczenie z wartością czasu, jeśli hasło zostało zweryfikowane w formacie daty/godziny schematu XML.||  
|Systemu Windows (Kerberos lub NTLM)|1.  Oświadczenia generowane z tokenu dostępu, takich jak: PrimarySID, DenyOnlyPrimarySID PrimaryGroupSID, DenyOnlyPrimaryGroupSID, identyfikatora GroupSID, DenyOnlySID i nazwy<br />2.  AuthenticationMethod z wartością `http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/windows`. AuthenticationInstant z wartością czas, kiedy tokenu dostępu systemu Windows została utworzona w formacie daty/godziny schematu XML.||  
|Pary kluczy RSA|1.  `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/rsa` Oświadczenie z wartością RSAKeyValue.<br />2.  AuthenticationMethod oświadczenie z wartością `http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/signature`. AuthenticationInstant oświadczenie z wartością czas po klucz RSA został uwierzytelniony (to znaczy podpis została zweryfikowana) w formacie daty/godziny schematu XML.||  
  
|Typ uwierzytelniania|Identyfikator URI emitowanych w oświadczenia "AuthenticationMethod"|  
|-|-|  
|Hasło|`urn:oasis:names:tc:SAML:1.0:am:password`|  
|Kerberos|`urn:ietf:rfc:1510`|  
|SecureRemotePassword|`urn:ietf:rfc:2945`|  
|TLSClient|`urn:ietf:rfc:2246`|  
|X509|`urn:oasis:names:tc:SAML:1.0:am:X509-PKI`|  
|PGP|`urn:oasis:names:tc:SAML:1.0:am:PGP`|  
|Spki|`urn:oasis:names:tc:SAML:1.0:am:SPKI`|  
|XmlDSig|`urn:ietf:rfc:3075`|  
|Nieokreślony|`urn:oasis:names:tc:SAML:1.0:am:unspecified`|
