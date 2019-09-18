---
title: Tworzenie pierwszej usługi WCF obsługującej oświadczenia
ms.date: 03/30/2017
ms.assetid: e0e6d091-9a97-4888-8f2c-cbcee42d90ee
author: BrucePerlerMS
ms.openlocfilehash: 330d785721cb434f74ec746310a71bfd39fefd0b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045557"
---
# <a name="building-my-first-claims-aware-wcf-service"></a>Tworzenie pierwszej usługi WCF obsługującej oświadczenia
## <a name="applies-to"></a>Dotyczy:  
  
- Windows Identity Foundation (WIF)  
  
- Windows Communication Foundation (WCF)  
  
## <a name="overview"></a>Omówienie  
 W tym temacie opisano scenariusz tworzenia przy użyciu programu WIF usług WCF obsługujących oświadczenia. W scenariuszu usługi sieci web obsługującej oświadczenia zazwyczaj uczestniczą trzy strony: sama usługa sieci web, użytkownik końcowy i usługa tokenu zabezpieczającego (STS). Następujący rysunek opisuje ten scenariusz:  
  
 ![Diagram przedstawiający WIF podstawowe składniki usługi WCF obsługujące oświadczenia.](./media/building-my-first-claims-aware-wcf-service/windows-identify-foundation-basic-claims-aware-windows-communication-foundation-service.gif)  
  
1. Klient usługi WCF (czasami nazywany agentem) używa programu WIF w celu wysłania poświadczeń do usługi STS i po pomyślnym uwierzytelnieniu usługa STS wystawia mu token.  
  
2. Agent wysyła ten token wystawiony przez usługę STS do usługi WCF.  
  
3. Usługa WCF obsługująca oświadczenia jest skonfigurowana do ufania usłudze STS i wystawianym przez nią tokenem. Usługa WCF obsługująca oświadczenia używa programu WIF do weryfikacji i analizy tokenu. Deweloperzy używają odpowiedniego interfejsu API WIF i typów, na przykład **ClaimsPrincipal** dla potrzeb aplikacji, takich jak implementacja autoryzacji dla tego programu.  
  
 Począwszy od platformy .NET 4,5, WIF jest częścią pakietu .NET Framework. Posiadanie klas WIF bezpośrednio dostępnych w ramach platformy pozwala znacznie lepiej przeprowadzić integrację tożsamości opartej na oświadczeniach w programie .NET, ułatwiając korzystanie z oświadczeń. Mając program WIF 4.5, nie trzeba instalować żadnych składników zewnętrznych, aby rozpocząć projektowanie aplikacji internetowych obsługujących oświadczenia. Klasy programu WIF rozciągają się obecnie na rozmaite zestawy, z których najważniejsze to System.Security.Claims, System.IdentityModel i System.IdentityModel.Services.  
  
 STS to usługa, która wystawia tokeny po pomyślnym uwierzytelnieniu. Firma Microsoft oferuje dwie usługi STS będące standardami branżowymi:  
  
- [Active Directory Federation Services (AD FS) 2.0](https://go.microsoft.com/fwlink/?LinkID=247516)
  
- [Access Control Service systemu Windows Azure (ACS)](https://docs.microsoft.com/previous-versions/azure/azure-services/hh147631(v=azure.100))
  
 Usługa AD FS 2.0 jest częścią systemu Windows Server R2 i może służyć jako usługa STS w scenariuszach lokalnych. Azure Active Directory Access Control (znany również jako Access Control Service lub ACS) to usługa w chmurze oferowana jako część Microsoft Azure. Na potrzeby testowania lub w celach edukacyjnych można również używać innych usług STS do tworzenia aplikacji obsługujących oświadczenia. Można na przykład użyć lokalnego programu STS do tworzenia [tożsamości i narzędzia dostępu dla programu Visual Studio](https://go.microsoft.com/fwlink/?LinkID=245849) , co jest dostępne w trybie online.  
  
 Aby skompilować pierwszą usługę WCF obsługującą oświadczenia za pomocą WIF, zobacz [How to: Włącz WIF dla aplikacji](how-to-enable-wif-for-a-wcf-web-service-application.md)usługi sieci Web WCF.
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do korzystania z programu WIF](getting-started-with-wif.md)
