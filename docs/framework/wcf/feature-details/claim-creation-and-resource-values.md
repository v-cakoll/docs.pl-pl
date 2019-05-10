---
title: Tworzenie oświadczenia i wartości zasobów
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], creation and resource values
ms.assetid: 30431f76-cbe7-4bad-bad7-8e43e23a82d4
ms.openlocfilehash: 5c2904f68ba50df99504e2f70c9170490ca54f73
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645572"
---
# <a name="claim-creation-and-resource-values"></a><span data-ttu-id="b7e19-102">Tworzenie oświadczenia i wartości zasobów</span><span class="sxs-lookup"><span data-stu-id="b7e19-102">Claim Creation and Resource Values</span></span>
<span data-ttu-id="b7e19-103"><xref:System.IdentityModel.Claims.Claim> Klasa udostępnia kilka metod tworzenia wystąpień wbudowanych oświadczeń typów.</span><span class="sxs-lookup"><span data-stu-id="b7e19-103">The <xref:System.IdentityModel.Claims.Claim> class provides several methods for creating instances of built-in claims types.</span></span> <span data-ttu-id="b7e19-104">Z tych metod poniżej wykonaj semantycznego nie lub formatowania, sprawdzając dostarczonego zasobu:</span><span class="sxs-lookup"><span data-stu-id="b7e19-104">Of these methods, the following perform no semantic or format checking on the supplied resource:</span></span>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateDnsClaim%2A>  
  
- <span data-ttu-id="b7e19-105"><xref:System.IdentityModel.Claims.Claim.CreateHashClaim%2A> (nie sprawdza długość lub zawartości elementu tablicy bajtów)</span><span class="sxs-lookup"><span data-stu-id="b7e19-105"><xref:System.IdentityModel.Claims.Claim.CreateHashClaim%2A> (does not check the length or content of the byte array)</span></span>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateNameClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateSpnClaim%2A>  
  
- <span data-ttu-id="b7e19-106"><xref:System.IdentityModel.Claims.Claim.CreateThumbprintClaim%2A> (nie sprawdza długość lub zawartości elementu tablicy bajtów)</span><span class="sxs-lookup"><span data-stu-id="b7e19-106"><xref:System.IdentityModel.Claims.Claim.CreateThumbprintClaim%2A> (does not check the length or content of the byte array)</span></span>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateUpnClaim%2A>  
  
 <span data-ttu-id="b7e19-107">Ostrożność podczas wywoływania metod powyżej, aby upewnić się, że zasób, którego wartości przekazywane w są w poprawnym formacie lub zawierać prawidłowe rodzaj informacji (lub obu).</span><span class="sxs-lookup"><span data-stu-id="b7e19-107">Care should be taken when calling the above methods to ensure that the resource values passed in are of the correct format or contain the correct kind of information (or both).</span></span>  
  
 <span data-ttu-id="b7e19-108">Następujące metody przyjmują określonych typów:</span><span class="sxs-lookup"><span data-stu-id="b7e19-108">The following methods take specific types:</span></span>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateDenyOnlyWindowsSidClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateMailAddressClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateRsaClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateUriClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateWindowsSidClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateX500DistinguishedNameClaim%2A>  
  
## <a name="see-also"></a><span data-ttu-id="b7e19-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b7e19-109">See also</span></span>

- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.ClaimSet>
- [<span data-ttu-id="b7e19-110">Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości</span><span class="sxs-lookup"><span data-stu-id="b7e19-110">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
