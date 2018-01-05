---
title: "Oświadczenia i tokeny"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: claims [WCF], and tokens
ms.assetid: eff167f3-33f8-483d-a950-aa3e9f97a189
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b2e571e8526581269cedb65b83c9ea0d8a81e280
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="claims-and-tokens"></a>Oświadczenia i tokeny
W tym temacie opisano różne typy roszczeń [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] tworzy na podstawie tokenów domyślnych, które obsługuje.  
  
 Oświadczenia poświadczeń klienta można sprawdzić za pomocą <xref:System.IdentityModel.Claims.ClaimSet> i <xref:System.IdentityModel.Claims.Claim> klasy. `ClaimSet` Zawiera kolekcję `Claim` obiektów. Każdy `Claim` ma następujące ważne elementy członkowskie:  
  
-   <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> Właściwość zwraca zasobów identyfikator URI (Uniform) określający typ oświadczenia odniesienia. Na przykład typ oświadczenia mogą być odcisk palca certyfikatu, w których przypadku identyfikator URI jest http:schemas.microsoft.com/ws/20005/05/identity/claims/thumprint.  
  
-   <xref:System.IdentityModel.Claims.Claim.Right%2A> Właściwość zwraca identyfikator URI, który określa prawo żądania. Wstępnie zdefiniowane prawa znajdują się w <xref:System.IdentityModel.Claims.Rights> klasy (<xref:System.IdentityModel.Claims.Rights.Identity%2A>, <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>).  
  
-   <xref:System.IdentityModel.Claims.Claim.Resource%2A> Właściwość zwraca zasób skojarzony z oświadczeniem.  
  
 Każdy <xref:System.IdentityModel.Claims.ClaimSet> ma również <xref:System.IdentityModel.Claims.ClaimSet.Issuer%2A> właściwość, która reprezentuje <xref:System.IdentityModel.Claims.ClaimSet> z `Issuer`.  
  
## <a name="windows-accounts"></a>Konta systemu Windows  
 Gdzie poświadczeń klienta mapowany na konto użytkownika systemu Windows, powstałe w ten sposób <xref:System.IdentityModel.Claims.ClaimSet> z następującymi wartościami:  
  
-   `Issuer` Jest wartość zwracana przez właściwość Windows statycznych <xref:System.IdentityModel.Claims.ClaimSet> klasy.  
  
-   Oświadczenia w kolekcji są:  
  
    -   A <xref:System.IdentityModel.Claims.Claim> z <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> wartość identyfikatora zabezpieczeń (SID), <xref:System.IdentityModel.Claims.Claim.Right%2A> wartość właściwości `Identity`, a <xref:System.IdentityModel.Claims.Claim.Resource%2A> zwracającą rzeczywista wartość identyfikatora SID. Identyfikator SID to unikatowa wartość wystawia kontrolera domeny dla każdego użytkownika. Identyfikator SID jest używana do identyfikacji użytkownika w interakcji z zabezpieczeń systemu Windows.  
  
    -   A <xref:System.IdentityModel.Claims.Claim> z <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> wartością identyfikatora SID, <xref:System.IdentityModel.Claims.Claim.Right%2A> z `PossessProperty`, a <xref:System.IdentityModel.Claims.Claim.Resource%2A> wartości identyfikatora SID.  
  
    -   A <xref:System.IdentityModel.Claims.Claim> z <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> z <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, <xref:System.IdentityModel.Claims.Claim.Right%2A> z `PossessProperty` i <xref:System.IdentityModel.Claims.Claim.Resource%2A> ciągu zawierającego nazwę użytkownika (na przykład "MYMACHINE\Bob").  
  
    -   Oświadczenia dodatkowe identyfikatora SID z <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> dla różnych grup należy użytkownik.  
  
## <a name="certificates"></a>Certyfikaty  
 Gdzie poświadczeń klienta to certyfikat, powstałe w ten sposób <xref:System.IdentityModel.Claims.ClaimSet> z następującymi wartościami:  
  
-   W przypadku certyfikatów wystawionej samodzielnie `Issuer` jest <xref:System.IdentityModel.Claims.ClaimSet> samej siebie. <xref:System.IdentityModel.Claims.ClaimSet> Zwraca <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> z <xref:System.IdentityModel.Claims.ClaimTypes.Thumbprint%2A>, <xref:System.IdentityModel.Claims.Claim.Right%2A> z `Identity`, a <xref:System.IdentityModel.Claims.Claim.Resource%2A> wartość, czyli <xref:System.Byte> tablica zawierająca odcisk palca certyfikatu.  
  
-   Certyfikat wystawiony przez urząd certyfikacji, wystawca ma `ClaimSet` reprezentujący certyfikatu urzędu certyfikacji.  
  
-   `Claims` w kolekcji obejmują:  
  
    -   A `Claim` z `ClaimType` odcisk palca, `Right` z PossessProperty, a `Resource` oznacza to tablica bajtów zawierająca odcisk palca certyfikatu  
  
    -   Dodatkowe oświadczenia PossessProperty różnych typów, w tym X500DistinguishedName, Dns, nazwy, głównej nazwy użytkownika i Rsa, reprezentują różne właściwości certyfikatu. Zasób oświadczenia Rsa jest klucza publicznego skojarzonego z certyfikatem. **Uwaga** typu poświadczeń klienta w przypadku certyfikatu, który mapuje usługi systemu Windows konta, dwa `ClaimSet` obiekty są generowane. Pierwszy zawiera wszystkie żądania dotyczące konta systemu Windows, a drugi zawiera wszystkie oświadczenia, które są związane z certyfikatem.  
  
## <a name="user-namepassword"></a>Nazwa użytkownika/hasło  
 Gdzie poświadczeń klienta jest nazwa i hasło użytkownika (lub odpowiednik) który mapuje konto systemu Windows, powstałe w ten sposób `ClaimSet` wystawiony przez statycznych <xref:System.IdentityModel.Claims.ClaimSet.System%2A> właściwość `ClaimSet` klasy. `ClaimSet` Zawiera `Identity` oświadczenie typu <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A> zapewnia którego zasób jest nazwą użytkownika klienta. Odpowiednie oświadczenie ma `Right` z `PossessProperty`.  
  
## <a name="rsa-keys"></a>Klucze RSA  
 W przypadku kluczy RSA, nie jest skojarzony z certyfikatem powstałe w ten sposób `ClaimSet` samodzielnie wystawionego i zawiera `Identity` oświadczenie typu <xref:System.IdentityModel.Claims.ClaimTypes.Rsa%2A> którego zasób jest kluczem RSA. Odpowiednie oświadczenie ma `Right` z `PossessProperty`.  
  
## <a name="saml"></a>SAML  
 Gdy klient jest uwierzytelniany w usłudze tokenu zabezpieczeń potwierdzenia Markup Language (SAML) powstałe w ten sposób `ClaimSet` wystawiony przez jednostki, który podpisał token SAML, często certyfikat usługę tokenu zabezpieczającego (STS), który wystawił tokenu SAML. `ClaimSet` Zawiera różne oświadczenia, tak jak w tokenie SAML. Jeśli SAML token zawiera `SamlSubject` z innej`null` nazwę, a następnie `Identity` oświadczeń z typem <xref:System.IdentityModel.Claims.ClaimTypes.NameIdentifier%2A> i typu zasobu <xref:System.IdentityModel.Tokens.SamlNameIdentifierClaimResource> są tworzone.  
  
## <a name="identity-claims-and-servicesecuritycontextisanonymous"></a>Tożsamość oświadczeń i ServiceSecurityContext.IsAnonymous  
 Jeśli żadna z `ClaimSet` obiekty wynikające z poświadczeń klienta zawierają oświadczenie o `Right` z `Identity,` , a następnie <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> zwraca właściwość `true`. Jeśli podano jeden lub więcej takich oświadczeń `IsAnonymous` zwraca właściwość `false`.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IdentityModel.Claims.ClaimSet>  
 <xref:System.IdentityModel.Claims.Claim>  
 <xref:System.IdentityModel.Claims.Rights>  
 <xref:System.IdentityModel.Claims.ClaimTypes>  
 [Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
