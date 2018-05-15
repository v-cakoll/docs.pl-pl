---
title: Tworzenie oświadczenia i wartości zasobów
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], creation and resource values
ms.assetid: 30431f76-cbe7-4bad-bad7-8e43e23a82d4
ms.openlocfilehash: cfa697023ca9d4c0b6f43c90c382816993dccc5d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="claim-creation-and-resource-values"></a><span data-ttu-id="039a4-102">Tworzenie oświadczenia i wartości zasobów</span><span class="sxs-lookup"><span data-stu-id="039a4-102">Claim Creation and Resource Values</span></span>
<span data-ttu-id="039a4-103"><xref:System.IdentityModel.Claims.Claim> Klasy zapewnia kilka metod tworzenia wystąpień wbudowanych oświadczeń typów.</span><span class="sxs-lookup"><span data-stu-id="039a4-103">The <xref:System.IdentityModel.Claims.Claim> class provides several methods for creating instances of built-in claims types.</span></span> <span data-ttu-id="039a4-104">Z tych metod poniżej wykonaj semantycznego nie lub sformatuj sprawdzanie na podany zasobów:</span><span class="sxs-lookup"><span data-stu-id="039a4-104">Of these methods, the following perform no semantic or format checking on the supplied resource:</span></span>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateDnsClaim%2A>  
  
-   <span data-ttu-id="039a4-105"><xref:System.IdentityModel.Claims.Claim.CreateHashClaim%2A> (nie sprawdza długość lub zawartości tablicy bajtów)</span><span class="sxs-lookup"><span data-stu-id="039a4-105"><xref:System.IdentityModel.Claims.Claim.CreateHashClaim%2A> (does not check the length or content of the byte array)</span></span>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateNameClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateSpnClaim%2A>  
  
-   <span data-ttu-id="039a4-106"><xref:System.IdentityModel.Claims.Claim.CreateThumbprintClaim%2A> (nie sprawdza długość lub zawartości tablicy bajtów)</span><span class="sxs-lookup"><span data-stu-id="039a4-106"><xref:System.IdentityModel.Claims.Claim.CreateThumbprintClaim%2A> (does not check the length or content of the byte array)</span></span>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateUpnClaim%2A>  
  
 <span data-ttu-id="039a4-107">Ostrożność podczas wywoływania metod powyżej, aby upewnić się, że zasób, do którego przekazano wartości jest poprawny format lub zawiera poprawne rodzaju informacje (lub obie).</span><span class="sxs-lookup"><span data-stu-id="039a4-107">Care should be taken when calling the above methods to ensure that the resource values passed in are of the correct format or contain the correct kind of information (or both).</span></span>  
  
 <span data-ttu-id="039a4-108">Następujące metody przyjmują określonych typów:</span><span class="sxs-lookup"><span data-stu-id="039a4-108">The following methods take specific types:</span></span>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateDenyOnlyWindowsSidClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateMailAddressClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateRsaClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateUriClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateWindowsSidClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateX500DistinguishedNameClaim%2A>  
  
## <a name="see-also"></a><span data-ttu-id="039a4-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="039a4-109">See Also</span></span>  
 <xref:System.IdentityModel.Claims.Claim>  
 <xref:System.IdentityModel.Claims.ClaimSet>  
 [<span data-ttu-id="039a4-110">Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości</span><span class="sxs-lookup"><span data-stu-id="039a4-110">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
