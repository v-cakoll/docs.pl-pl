---
title: Oświadczenia i tokeny
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], and tokens
ms.assetid: eff167f3-33f8-483d-a950-aa3e9f97a189
ms.openlocfilehash: cbc97f2224bce640757e1cef88fe325db477cfd7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84587030"
---
# <a name="claims-and-tokens"></a>Oświadczenia i tokeny

W tym temacie opisano różne typy zgłoszeń, które program Windows Communication Foundation (WCF) tworzy z domyślnych tokenów, które obsługuje.

Oświadczenia poświadczeń klienta można przeanalizować przy użyciu <xref:System.IdentityModel.Claims.ClaimSet> <xref:System.IdentityModel.Claims.Claim> klas i. `ClaimSet`Zawiera kolekcję `Claim` obiektów. Każdy `Claim` z nich ma następujące ważne elementy członkowskie:

- <xref:System.IdentityModel.Claims.Claim.ClaimType%2A>Właściwość zwraca Uniform Resource Identifier (URI), który określa typ podejmowanych roszczeń. Na przykład typ zgłoszenia może być odciskiem palca certyfikatu, w tym przypadku identyfikator URI to `http://schemas.microsoft.com/ws/20005/05/identity/claims/thumprint` .

- <xref:System.IdentityModel.Claims.Claim.Right%2A>Właściwość zwraca identyfikator URI, który określa prawo od żądania. Wstępnie zdefiniowane prawa są dostępne w <xref:System.IdentityModel.Claims.Rights> klasie ( <xref:System.IdentityModel.Claims.Rights.Identity%2A> , <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> ).

- <xref:System.IdentityModel.Claims.Claim.Resource%2A>Właściwość zwraca zasób skojarzony z tym powiązaniem.

Każdy <xref:System.IdentityModel.Claims.ClaimSet> z nich ma również <xref:System.IdentityModel.Claims.ClaimSet.Issuer%2A> Właściwość, która reprezentuje <xref:System.IdentityModel.Claims.ClaimSet> `Issuer` .

## <a name="windows-accounts"></a>Konta systemu Windows

Gdy poświadczenia klienta są mapowane na konto użytkownika systemu Windows, wynikiem <xref:System.IdentityModel.Claims.ClaimSet> są następujące wartości:

- `Issuer`Jest wartością zwracaną przez statyczną właściwość systemu Windows <xref:System.IdentityModel.Claims.ClaimSet> klasy.

- Oświadczenia w kolekcji są następujące:

  - A <xref:System.IdentityModel.Claims.Claim> o <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> wartości identyfikatora zabezpieczeń (SID), <xref:System.IdentityModel.Claims.Claim.Right%2A> wartości właściwości `Identity` i, <xref:System.IdentityModel.Claims.Claim.Resource%2A> która zwraca rzeczywistą wartość identyfikatora SID. Identyfikator SID to unikatowa wartość, którą kontroler domeny wystawia każdemu użytkownikowi. Identyfikator SID służy do identyfikowania użytkownika w interakcje z zabezpieczeniami systemu Windows.

  - A <xref:System.IdentityModel.Claims.Claim> o <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> wartości SID, a <xref:System.IdentityModel.Claims.Claim.Right%2A> `PossessProperty` i a <xref:System.IdentityModel.Claims.Claim.Resource%2A> wartości identyfikatora SID.

  - A z i a z <xref:System.IdentityModel.Claims.Claim> <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A> <xref:System.IdentityModel.Claims.Claim.Right%2A> `PossessProperty` i z i z z i a z z i a z, z i a <xref:System.IdentityModel.Claims.Claim.Resource%2A> z o

  - Dodatkowe oświadczenia SID <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> dla różnych grup, do których należy użytkownik.

## <a name="certificates"></a>Certyfikaty

Gdy poświadczenie klienta jest certyfikatem, wynikiem są <xref:System.IdentityModel.Claims.ClaimSet> następujące wartości:

- W przypadku certyfikatów wystawionych przez siebie `Issuer` jest to <xref:System.IdentityModel.Claims.ClaimSet> sama sama. <xref:System.IdentityModel.Claims.ClaimSet>Zwraca wartość a <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> z <xref:System.IdentityModel.Claims.ClaimTypes.Thumbprint%2A> <xref:System.IdentityModel.Claims.Claim.Right%2A> `Identity` i <xref:System.IdentityModel.Claims.Claim.Resource%2A> jest <xref:System.Byte> tablicą zawierającą odcisk palca certyfikatu.

- Dla certyfikatu wystawionego przez urząd certyfikacji wystawca `ClaimSet` reprezentuje certyfikat urzędu certyfikacji.

- `Claims`W kolekcji należą:

  - A z `Claim` `ClaimType` odciskiem palca, a `Right` z PossessProperty i `Resource` jest tablicą bajtową zawierającą odcisk palca certyfikatu

  - Dodatkowe oświadczenia PossessProperty różnych typów, w tym X500DistinguishedName, DNS, Name, UPN i RSA, reprezentują różne właściwości certyfikatu. Zasób dla żądania RSA jest kluczem publicznym skojarzonym z certyfikatem. **Uwaga** W przypadku, gdy typ poświadczeń klienta to certyfikat, który usługa mapuje na konto systemu Windows, `ClaimSet` generowane są dwa obiekty. Pierwszy zawiera wszystkie oświadczenia powiązane z kontem systemu Windows, a drugi zawiera wszystkie oświadczenia powiązane z certyfikatem.

## <a name="user-namepassword"></a>Nazwa użytkownika/hasło

Gdzie poświadczenie klienta to nazwa użytkownika/hasło (lub równoważne), które nie jest mapowane na konto systemu Windows, wynikiem `ClaimSet` jest wystawienie przez właściwość statyczną <xref:System.IdentityModel.Claims.ClaimSet.System%2A> `ClaimSet` klasy. `ClaimSet`Zawiera typ, `Identity` <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A> którego zasób jest nazwą użytkownika dostarczaną przez klienta. Odpowiadające mu wnioski mają `Right` `PossessProperty` .

## <a name="rsa-keys"></a>Klucze RSA

Jeśli używany jest klucz RSA, który nie jest skojarzony z certyfikatem, zostanie `ClaimSet` wystawiony własny komunikat i zawiera ono zgłoszenie `Identity` typu, <xref:System.IdentityModel.Claims.ClaimTypes.Rsa%2A> którego zasób jest kluczem RSA. Odpowiadające mu wnioski mają `Right` `PossessProperty` .

## <a name="saml"></a>SAML

W przypadku, gdy klient uwierzytelnia się za pomocą tokenu potwierdzeń zabezpieczeń (SAML), `ClaimSet` wydawane przez jednostkę, która podpisał token SAML, często certyfikat usługi tokenu zabezpieczającego (STS), która wystawiła token języka SAML. `ClaimSet`Zawiera różne oświadczenia, które znajdują się w tokenie SAML. Jeśli token SAML zawiera element `SamlSubject` o wartości innej niż `null` Nazwa, to zostanie utworzone wystąpienie z `Identity` typem <xref:System.IdentityModel.Claims.ClaimTypes.NameIdentifier%2A> i typem zasobu <xref:System.IdentityModel.Tokens.SamlNameIdentifierClaimResource> .

## <a name="identity-claims-and-servicesecuritycontextisanonymous"></a>Oświadczenia tożsamości i ServiceSecurityContext. IsAnonymous

Jeśli żaden z `ClaimSet` obiektów wynikających z poświadczeń klienta nie zawiera roszczeń z, a `Right` `Identity,` następnie <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> zwraca wartość właściwości `true` . Jeśli istnieją co najmniej jedno takie oświadczenie, `IsAnonymous` Właściwość zwraca `false` .

## <a name="see-also"></a>Zobacz też

- <xref:System.IdentityModel.Claims.ClaimSet>
- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims.ClaimTypes>
- [Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości](managing-claims-and-authorization-with-the-identity-model.md)
