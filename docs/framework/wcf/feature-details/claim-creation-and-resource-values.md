---
title: Tworzenie oświadczenia i wartości zasobów
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], creation and resource values
ms.assetid: 30431f76-cbe7-4bad-bad7-8e43e23a82d4
ms.openlocfilehash: bd9a8b7faf3cd7a648ff6b2a50ac68f21561497c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766912"
---
# <a name="claim-creation-and-resource-values"></a>Tworzenie oświadczenia i wartości zasobów
<xref:System.IdentityModel.Claims.Claim> Klasa udostępnia kilka metod tworzenia wystąpień wbudowanych oświadczeń typów. Z tych metod poniżej wykonaj semantycznego nie lub formatowania, sprawdzając dostarczonego zasobu:  
  
- <xref:System.IdentityModel.Claims.Claim.CreateDnsClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateHashClaim%2A> (nie sprawdza długość lub zawartości elementu tablicy bajtów)  
  
- <xref:System.IdentityModel.Claims.Claim.CreateNameClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateSpnClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateThumbprintClaim%2A> (nie sprawdza długość lub zawartości elementu tablicy bajtów)  
  
- <xref:System.IdentityModel.Claims.Claim.CreateUpnClaim%2A>  
  
 Ostrożność podczas wywoływania metod powyżej, aby upewnić się, że zasób, którego wartości przekazywane w są w poprawnym formacie lub zawierać prawidłowe rodzaj informacji (lub obu).  
  
 Następujące metody przyjmują określonych typów:  
  
- <xref:System.IdentityModel.Claims.Claim.CreateDenyOnlyWindowsSidClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateMailAddressClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateRsaClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateUriClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateWindowsSidClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateX500DistinguishedNameClaim%2A>  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.ClaimSet>
- [Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
