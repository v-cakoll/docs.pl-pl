---
title: Model programowania oświadczeń programu WIF
ms.date: 03/30/2017
ms.assetid: 149cb875-9b1c-4695-b88a-fbf1725a02f9
author: BrucePerlerMS
ms.openlocfilehash: 95df026684f536a64ffe15f65264c470dff164da
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47171715"
---
# <a name="wif-claims-programming-model"></a>Model programowania oświadczeń programu WIF
Deweloperzy platformy ASP.NET i Windows Communication Foundation (WCF) zwykle używać interfejsów IIdentity i IPrincipal do pracy z informacji o tożsamości użytkownika. W .NET 4.5 Windows Identity Foundation (WIF) jest zintegrowana w taki sposób, że oświadczenia są teraz zawsze stosowany w przypadku dowolnego podmiotu zabezpieczeń, jak pokazano na poniższym diagramie:

 ![Program WIF oświadczeń Model programowania](../../../docs/framework/security/media/wifclaimsprogrammingmodel.png "WIFClaimsProgrammingModel")

 W .NET 4.5 System.Security.Claims zawiera nowe klasy ClaimsPrincipal i ClaimsIdentity (zobacz diagram powyżej). Wszystkie podmioty zabezpieczeń w środowisku .NET pochodzą teraz od ClaimsPrincipal. Wszystkie klasy wbudowane tożsamości, takich jak FormsIdentity platformy ASP.NET i teraz WindowsIdentity Dziedzicz z elementu ClaimsIdentity. Podobnie wszystkie wbudowane klasy jednostki, takie jak obiektów GenericPrincipal i WindowsPrincipal pochodzić od elementu ClaimsPrincipal.

 Oświadczenie jest reprezentowany przez <xref:System.Security.Claims.Claim> klasy. Ta klasa ma następujące właściwości ważne:

- <xref:System.Security.Claims.Claim.Type%2A> reprezentuje typ oświadczenia i zazwyczaj jest to identyfikator URI. Na przykład oświadczenia adresu e-mail jest reprezentowany jako `http://schemas.microsoft.com/ws/2008/06/identity/claims/email`.

- <xref:System.Security.Claims.Claim.Value%2A> zawiera wartość oświadczenia i jest reprezentowany jako ciąg. Na przykład adres e-mail może być reprezentowany jako "someone@contoso.com".

- <xref:System.Security.Claims.Claim.ValueType%2A> reprezentuje typ wartości oświadczenia i zazwyczaj jest to identyfikator URI. Na przykład typ string jest reprezentowany jako `http://www.w3.org/2001/XMLSchema#string`. Typ wartości musi mieć postać QName zgodnie ze schematem XML. Wartość powinna być w formacie `namespace#format` umożliwiające programu WIF do wypełniania wyjściowego prawidłową wartość QName. Jeśli przestrzeń nazw nie jest dobrze zdefiniowany przestrzeni nazw, wygenerowany kod XML prawdopodobnie nie może być schematu sprawdzania poprawności, ponieważ nie będzie opublikowana plik XSD dla tej przestrzeni nazw. Typ wartości domyślnej jest `http://www.w3.org/2001/XMLSchema#string`. Zobacz [ http://www.w3.org/2001/XMLSchema ](https://go.microsoft.com/fwlink/?LinkId=209155) dla typów dobrze znaną wartością, która umożliwia bezpieczne.

- <xref:System.Security.Claims.Claim.Issuer%2A> jest to identyfikator usługę tokenu zabezpieczającego (STS), który wystawił oświadczenie. To może być reprezentowana jako adres URL usługi STS lub nazwę, która reprezentuje usługi STS, takie jak `https://sts1.contoso.com/sts`.

- <xref:System.Security.Claims.Claim.OriginalIssuer%2A> jest identyfikatorem usługi STS, które początkowo wystawił oświadczenie, niezależnie od tego, ile usługi STS w łańcuchu. To jest reprezentowana w podobny sposób jak <xref:System.Security.Claims.Claim.Issuer%2A>.

- <xref:System.Security.Claims.Claim.Subject%2A> to podmiot, którego tożsamość jest sprawdzane. Zawiera on element <xref:System.Security.Claims.ClaimsIdentity>.

- <xref:System.Security.Claims.Claim.Properties%2A> jest słownik, który umożliwia deweloperowi Podaj dane specyficzne dla aplikacji do przeniesienia na potrzeby przesyłu wraz z innymi właściwościami i może służyć do niestandardowego sprawdzania poprawności.

## <a name="identity-delegation"></a>Delegowanie tożsamości
Ważne właściwości <xref:System.Security.Claims.ClaimsIdentity> jest <xref:System.Security.Claims.ClaimsIdentity.Actor%2A>. Ta właściwość umożliwia delegowanie poświadczeń w systemie wielowarstwowych, w której warstwy środkowej działa jako klient, aby wysyłać żądania do usługi zaplecza.

### <a name="accessing-claims-through-threadcurrentprincipal"></a>Dostęp do oświadczenia, za pośrednictwem SE vlastnost Thread.CurrentPrincipal
Aby uzyskać dostęp do bieżącego użytkownika zestaw oświadczeń w aplikacji jednostki Uzależnionej, należy użyć `Thread.CurrentPrincipal`.

Poniższy przykładowy kod przedstawia sposób użycia tej metody, aby uzyskać System.Security.Claims.ClaimsIdentity:

```csharp
ClaimsPrincipal claimsPrincipal = Thread.CurrentPrincipal as ClaimsPrincipal;
```

Aby uzyskać więcej informacji, zobacz <xref:System.Security.Claims>.

### <a name="role-claim-type"></a>Typ oświadczenia roli
Część konfigurowania aplikacji jednostki Uzależnionej ma na celu określenie, jakie Twoja rola oświadczeń, powinien być typu. Ten typ oświadczenia jest używany przez System.Security.Claims.ClaimsPrincipal.IsInRole(System.String). Domyślny typ oświadczenia jest `http://schemas.microsoft.com/ws/2008/06/identity/claims/role`.

### <a name="claims-extracted-by-windows-identity-foundation-from-different-token-types"></a>Wyodrębnionych przez program Windows Identity Foundation z różnych typów tokenu oświadczeń
Program WIF obsługuje kilku kombinacji mechanizmów uwierzytelniania poza pole. W poniższej tabeli wymieniono oświadczenia, które program WIF wyodrębnia z różnych typów tokenu.

|Typ tokenu|Oświadczenia generowane|Mapy do Windows tokenu dostępu|
|-|-|-|
|SAML 1.1|1.  Wszystkie roszczenia z System.IdentityModel.SecurityTokenService.GetOutputClaimsIdentity(System.Security.Claims.ClaimsPrincipal,System.IdentityModel.Protocols.WSTrust.RequestSecurityToken,System.IdentityModel.Scope).<br />2.  `http://schemas.microsoft.com/ws/2008/06/identity/claims/confirmationkey` Oświadczenia, który zawiera klucz potwierdzenia serializacji XML, jeśli token zawiera token potwierdzenia.<br />3.  `http://schemas.microsoft.com/ws/2008/06/identity/claims/samlissuername` Oświadczeń z elementu wystawcy.<br />4.  AuthenticationMethod AuthenticationInstant oświadczeń i, jeśli token zawiera instrukcję uwierzytelniania.|Oprócz oświadczenia na liście "SAML 1.1", z wyjątkiem oświadczeń typu `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name`, oświadczenia będą dodawane i tożsamości, które będą reprezentowane przez WindowsClaimsIdentity związane z uwierzytelnianiem Windows.|
|SAML 2.0|Taka sama jak "SAML 1.1".|Taka sama jak "SAML 1.1 mapowany do konta Windows".|
|X509|1.  Oświadczenia, za pomocą X500 odróżnić nazwy, nazwa_e-mail, dnsName, SimpleName, UpnName, UrlName, odcisk palca, RsaKey (to można wyodrębnić przy użyciu metody RSACryptoServiceProvider.ExportParameters z właściwości X509Certificate2.PublicKey.Key), DsaKey () to można wyodrębnić przy użyciu metody DSACryptoServiceProvider.ExportParameters z właściwości X509Certificate2.PublicKey.Key), z X509 właściwości numer seryjny certyfikatu.<br />2.  AuthenticationMethod oświadczenie z wartością `http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/x509`. AuthenticationInstant oświadczenie z wartością czasu, gdy certyfikat został zweryfikowany w formacie daty/godziny schematu XML.|1.  Używa ona Windows konto pełni kwalifikowaną nazwę domeny jako `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name` wartości oświadczenia. .<br />2.  Oświadczeń z X509 certyfikat nie jest zamapowany na Windows i z konta systemu windows, uzyskaną przez mapowania certyfikatu do Windows.|
|UPN|1.  Oświadczenia są podobne do oświadczeń w sekcji uwierzytelnianie Windows.<br />2.  AuthenticationMethod oświadczenie z wartością `http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/password`. AuthenticationInstant oświadczenie z wartością czasu, gdy hasło zostało zweryfikowane w formacie daty/godziny schematu XML.||
|Windows (Kerberos lub NTLM)|1.  Oświadczenia generowane z tokenu dostępu, takich jak: PrimarySID, DenyOnlyPrimarySID, PrimaryGroupSID, DenyOnlyPrimaryGroupSID, identyfikatora GroupSID, DenyOnlySID i nazwa<br />2.  AuthenticationMethod wartością `http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/windows`. AuthenticationInstant z wartością czasu, gdy token dostępu Windows został utworzony w formacie daty/godziny schematu XML.||
|Pary kluczy RSA|1.  `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/rsa` Oświadczenie z wartością RSAKeyValue.<br />2.  AuthenticationMethod oświadczenie z wartością `http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/signature`. AuthenticationInstant oświadczenie z wartością czasu, gdy klucz RSA został uwierzytelniony (to znaczy, że podpis została zweryfikowana) w formacie daty/godziny schematu XML.||

|Typ uwierzytelniania|Identyfikator URI emitowane w oświadczenie "AuthenticationMethod"|
|-|-|
|Hasło|`urn:oasis:names:tc:SAML:1.0:am:password`|
|Kerberos|`urn:ietf:rfc:1510`|
|SecureRemotePassword|`urn:ietf:rfc:2945`|
|TLSClient|`urn:ietf:rfc:2246`|
|X509|`urn:oasis:names:tc:SAML:1.0:am:X509-PKI`|
|PGP|`urn:oasis:names:tc:SAML:1.0:am:PGP`|
|Spki|`urn:oasis:names:tc:SAML:1.0:am:SPKI`|
|XmlDSig|`urn:ietf:rfc:3075`|
|Nie określono tego parametru|`urn:oasis:names:tc:SAML:1.0:am:unspecified`|