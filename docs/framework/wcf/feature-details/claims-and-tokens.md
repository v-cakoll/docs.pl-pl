---
title: Oświadczenia i tokeny
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], and tokens
ms.assetid: eff167f3-33f8-483d-a950-aa3e9f97a189
ms.openlocfilehash: 21172ccda5f5f8070d81726d5f4dc6f9d80ab071
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569010"
---
# <a name="claims-and-tokens"></a>Oświadczenia i tokeny
W tym temacie opisano różne typy oświadczeń, które tworzy Windows Communication Foundation (WCF) na podstawie tokenów domyślne, które obsługuje.  
  
 Oświadczenia poświadczeń klienta można sprawdzić za pomocą <xref:System.IdentityModel.Claims.ClaimSet> i <xref:System.IdentityModel.Claims.Claim> klasy. `ClaimSet` Zawiera zbiór `Claim` obiektów. Każdy `Claim` ma następujące ważne elementy członkowskie:  
  
-   <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> Właściwość zwraca jednolite zasobów identyfikator (URI) określający typ oświadczenia, które zostaną wprowadzone. Na przykład typ oświadczenia mogą być odcisku palca certyfikatu, w którym to przypadku identyfikatora URI `http://schemas.microsoft.com/ws/20005/05/identity/claims/thumprint`.  
  
-   <xref:System.IdentityModel.Claims.Claim.Right%2A> Właściwość zwraca identyfikator URI, który określa prawo żądania. Wstępnie zdefiniowane prawa znajdują się w <xref:System.IdentityModel.Claims.Rights> klasy (<xref:System.IdentityModel.Claims.Rights.Identity%2A>, <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>).  
  
-   <xref:System.IdentityModel.Claims.Claim.Resource%2A> Właściwość zwraca zasób skojarzony z oświadczeniem.  
  
 Każdy <xref:System.IdentityModel.Claims.ClaimSet> ma również <xref:System.IdentityModel.Claims.ClaimSet.Issuer%2A> właściwość, która reprezentuje <xref:System.IdentityModel.Claims.ClaimSet> z `Issuer`.  
  
## <a name="windows-accounts"></a>Kont Windows  
 Gdzie mapuje poświadczeń klienta na konto użytkownika Windows wynikowy <xref:System.IdentityModel.Claims.ClaimSet> następującymi wartościami:  
  
-   `Issuer` Jest wartość zwracana przez Windows właściwość statyczna <xref:System.IdentityModel.Claims.ClaimSet> klasy.  
  
-   Oświadczenia w kolekcji są:  
  
    -   A <xref:System.IdentityModel.Claims.Claim> z <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> wartość identyfikatora zabezpieczeń (SID) <xref:System.IdentityModel.Claims.Claim.Right%2A> wartość właściwości `Identity`, a <xref:System.IdentityModel.Claims.Claim.Resource%2A> zwracającego rzeczywista wartość identyfikatora SID. Identyfikator SID to unikatowa wartość kontroler domeny wystawia każdemu użytkownikowi. Identyfikator SID jest używany do identyfikowania użytkownika w interakcji z usługą Windows security.  
  
    -   A <xref:System.IdentityModel.Claims.Claim> z <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> wartością identyfikatora SID, <xref:System.IdentityModel.Claims.Claim.Right%2A> z `PossessProperty`, a <xref:System.IdentityModel.Claims.Claim.Resource%2A> wartości identyfikatora SID.  
  
    -   A <xref:System.IdentityModel.Claims.Claim> z <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> z <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, <xref:System.IdentityModel.Claims.Claim.Right%2A> z `PossessProperty` i <xref:System.IdentityModel.Claims.Claim.Resource%2A> ciąg zawierający nazwę użytkownika (na przykład "MYMACHINE\Bob").  
  
    -   Identyfikator SID dodatkowe oświadczenia za pomocą <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> dla różnych grup należy użytkownik.  
  
## <a name="certificates"></a>Certyfikaty  
 Gdzie poświadczeń klienta jest certyfikat wynikowy <xref:System.IdentityModel.Claims.ClaimSet> następującymi wartościami:  
  
-   W przypadku certyfikatów wystawiony samodzielnie `Issuer` jest <xref:System.IdentityModel.Claims.ClaimSet> sam. <xref:System.IdentityModel.Claims.ClaimSet> Zwraca <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> z <xref:System.IdentityModel.Claims.ClaimTypes.Thumbprint%2A>, <xref:System.IdentityModel.Claims.Claim.Right%2A> z `Identity`, a <xref:System.IdentityModel.Claims.Claim.Resource%2A> wartość, która jest <xref:System.Byte> tablica zawierająca odcisk palca certyfikatu.  
  
-   Certyfikat wystawiony przez urząd certyfikacji, wystawca ma `ClaimSet` reprezentujący certyfikatu urzędu certyfikacji.  
  
-   `Claims` w kolekcji obejmują:  
  
    -   A `Claim` z `ClaimType` odcisk palca, `Right` z PossessProperty, a `Resource` oznacza to tablica bajtów zawierająca odcisk palca certyfikatu  
  
    -   Dodatkowe oświadczenia PossessProperty różnych typów, w tym X500DistinguishedName, Dns, nazwę, nazwy Upn i Rsa, reprezentują różne właściwości certyfikatu. Zasób oświadczenia Rsa jest klucza publicznego skojarzonego z certyfikatem. **Uwaga** typu poświadczeń klienta w przypadku certyfikatu, który mapuje usługę Windows konto, 2 `ClaimSet` obiekty są generowane. Pierwszy zawiera wszystkie oświadczenia, które są związane z kontem Windows, a drugi zawiera wszystkie oświadczenia, które są związane z certyfikatem.  
  
## <a name="user-namepassword"></a>Nazwa użytkownika/hasło  
 Gdzie poświadczeń klienta jest nazwa i hasło użytkownika (lub odpowiednik), nie jest mapowany do konta Windows, wynikowy `ClaimSet` wystawiony przez statyczną <xref:System.IdentityModel.Claims.ClaimSet.System%2A> właściwość `ClaimSet` klasy. `ClaimSet` Zawiera `Identity` oświadczenia typu <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A> zapewnia którego zasób jest nazwą użytkownika klienta. Odpowiadające oświadczenie ma `Right` z `PossessProperty`.  
  
## <a name="rsa-keys"></a>Klucze RSA  
 W przypadku, gdy jest używany klucz RSA, nie jest skojarzony z certyfikatem, wynikowy `ClaimSet` własnym wystawiony i zawiera `Identity` oświadczenia typu <xref:System.IdentityModel.Claims.ClaimTypes.Rsa%2A> którego zasób jest kluczem RSA. Odpowiadające oświadczenie ma `Right` z `PossessProperty`.  
  
## <a name="saml"></a>SAML  
 Gdy klient uwierzytelnia się za pomocą tokenu potwierdzenia języka SAML (Security Markup), wynikowy `ClaimSet` wystawiony przez jednostki, który podpisał token SAML, często certyfikat usługę tokenu zabezpieczającego (STS), który wystawił SAML token. `ClaimSet` Zawiera różne oświadczenia, tak jak w tokenie języka SAML. Jeśli zawiera SAML token `SamlSubject` przy użyciu innej niż`null` nazwę, a następnie `Identity` oświadczenie z typem <xref:System.IdentityModel.Claims.ClaimTypes.NameIdentifier%2A> i typu zasobu <xref:System.IdentityModel.Tokens.SamlNameIdentifierClaimResource> są tworzone.  
  
## <a name="identity-claims-and-servicesecuritycontextisanonymous"></a>Tożsamość oświadczeń i ServiceSecurityContext.IsAnonymous  
 Jeśli żadna z `ClaimSet` obiektów wynikające z poświadczeniami klienta zawierają roszczenia z `Right` z `Identity,` , a następnie <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> właściwość zwraca `true`. Jeśli jeden lub więcej takich oświadczenia są obecne, `IsAnonymous` właściwość zwraca `false`.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.IdentityModel.Claims.ClaimSet>
- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims.ClaimTypes>
- [Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
