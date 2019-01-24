---
title: Tworzenie Moje pierwszej usługi WCF obsługującej oświadczenia
ms.date: 03/30/2017
ms.assetid: e0e6d091-9a97-4888-8f2c-cbcee42d90ee
author: BrucePerlerMS
ms.openlocfilehash: 2102ec07a26c02c7181e3422e48939c40b86a8de
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54599208"
---
# <a name="building-my-first-claims-aware-wcf-service"></a>Tworzenie Moje pierwszej usługi WCF obsługującej oświadczenia
## <a name="applies-to"></a>Dotyczy:  
  
-   Windows Identity Foundation (WIF)  
  
-   Windows Communication Foundation (WCF)  
  
## <a name="overview"></a>Omówienie  
 W tym temacie opisano scenariusz tworzenia przy użyciu programu WIF usług WCF obsługujących oświadczenia. W scenariuszu usługi sieci web obsługującej oświadczenia zazwyczaj uczestniczą trzy strony: sama usługa sieci web, użytkownik końcowy i usługa tokenu zabezpieczającego (STS). Następujący rysunek opisuje ten scenariusz:  
  
 ![WIF Basic oświadczeń Aware WCF Service](../../../docs/framework/security/media/wifbasicclaimsawarewcfservice.gif "WIFBasicClaimsAwareWCFService")  
  
1.  Klient usługi WCF (czasami nazywany agentem) używa programu WIF w celu wysłania poświadczeń do usługi STS i po pomyślnym uwierzytelnieniu usługa STS wystawia mu token.  
  
2.  Agent wysyła ten token wystawiony przez usługę STS do usługi WCF.  
  
3.  Usługa WCF obsługująca oświadczenia jest skonfigurowana do ufania usłudze STS i wystawianym przez nią tokenem. Usługa WCF obsługująca oświadczenia używa programu WIF do weryfikacji i analizy tokenu. Deweloperzy Użyj odpowiedniego interfejsu API programu WIF i typy, na przykład **ClaimsPrincipal** do potrzeb aplikacji, takich jak zaimplementowanie dla niej autoryzacji.  
  
 Począwszy od .NET 4.5, WIF jest częścią pakietu .NET Framework. Klasy programu WIF bezpośrednio dostępne w ramach pozwala znacznie głębszą integrację tożsamości opartej na oświadczeniach na platformie .NET, ułatwiając korzystanie z oświadczeń. Mając program WIF 4.5, nie trzeba instalować żadnych składników zewnętrznych, aby rozpocząć projektowanie aplikacji internetowych obsługujących oświadczenia. Klasy programu WIF rozciągają się obecnie na rozmaite zestawy, z których najważniejsze to System.Security.Claims, System.IdentityModel i System.IdentityModel.Services.  
  
 STS to usługa, która wystawia tokeny po pomyślnym uwierzytelnieniu. Firma Microsoft oferuje dwie usługi STS będące standardami branżowymi:  
  
-   [Active Directory Federation Services (AD FS) 2.0](https://go.microsoft.com/fwlink/?LinkID=247516)
  
-   [Windows Azure usługa Access Control Service (ACS)](https://go.microsoft.com/fwlink/?LinkID=247517)
  
 Usługa AD FS 2.0 jest częścią systemu Windows Server R2 i może służyć jako usługa STS w scenariuszach lokalnych. Usługa Azure Active Directory Access Control (znany także jako usługa Access Control Service lub usługi ACS) to usługa w chmurze, oferowane jako część systemu Microsoft Azure. Na potrzeby testowania lub w celach edukacyjnych można również używać innych usług STS do tworzenia aplikacji obsługujących oświadczenia. Na przykład, można użyć Local Development STS, która jest częścią [narzędzie tożsamości i dostępu dla programu Visual Studio](https://go.microsoft.com/fwlink/?LinkID=245849) które jest dostępne bezpłatnie w trybie online.  
  
 Tworzenie pierwszej usługi WCF obsługującej oświadczenia za pomocą programu WIF, zobacz [How to: Włączanie programu WIF dla aplikacji usługi sieci Web WCF](../../../docs/framework/security/how-to-enable-wif-for-a-wcf-web-service-application.md).
  
## <a name="see-also"></a>Zobacz także
- [Wprowadzenie do korzystania z programu WIF](../../../docs/framework/security/getting-started-with-wif.md)
