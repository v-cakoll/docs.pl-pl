---
title: "Tworzenie Moje pierwszej usługi WCF obsługujący oświadczenia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e0e6d091-9a97-4888-8f2c-cbcee42d90ee
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 791c86b8f833c6b1a8acb6da3b03cfccdafca0e5
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="building-my-first-claims-aware-wcf-service"></a>Tworzenie Moje pierwszej usługi WCF obsługujący oświadczenia
## <a name="applies-to"></a>Dotyczy:  
  
-   Windows Identity Foundation (WIF)  
  
-   Windows Communication Foundation (WCF)  
  
## <a name="overview"></a>Omówienie  
 W tym temacie opisano scenariusz tworzenia przy użyciu programu WIF usług WCF obsługujących oświadczenia. W scenariuszu usługi sieci web obsługującej oświadczenia zazwyczaj uczestniczą trzy strony: sama usługa sieci web, użytkownik końcowy i usługa tokenu zabezpieczającego (STS). Następujący rysunek opisuje ten scenariusz:  
  
 ![WIF Basic oświadczeń usługi WCF pamiętać](../../../docs/framework/security/media/wifbasicclaimsawarewcfservice.gif "WIFBasicClaimsAwareWCFService")  
  
1.  Klient usługi WCF (czasami nazywany agentem) używa programu WIF w celu wysłania poświadczeń do usługi STS i po pomyślnym uwierzytelnieniu usługa STS wystawia mu token.  
  
2.  Agent wysyła ten token wystawiony przez usługę STS do usługi WCF.  
  
3.  Usługa WCF obsługująca oświadczenia jest skonfigurowana do ufania usłudze STS i wystawianym przez nią tokenem. Usługa WCF obsługująca oświadczenia używa programu WIF do weryfikacji i analizy tokenu. Deweloperzy Użyj odpowiedniego interfejsu API WIF i typów, na przykład **ClaimsPrincipal** na potrzeby aplikacji, takich jak wdrażanie autoryzacji dla niego.  
  
 Począwszy od platformy .NET 4.5, WIF jest częścią pakietu .NET Framework. O klasach WIF bezpośrednio dostępne w ramach umożliwia znacznie lepsza integracja tożsamości opartego na oświadczeniach w środowisku .NET, co ułatwia użyć oświadczeń. Mając program WIF 4.5, nie trzeba instalować żadnych składników zewnętrznych, aby rozpocząć projektowanie aplikacji sieci Web obsługujących oświadczenia. Klasy programu WIF rozciągają się obecnie na rozmaite zestawy, z których najważniejsze to System.Security.Claims, System.IdentityModel i System.IdentityModel.Services.  
  
 STS to usługa, która wystawia tokeny po pomyślnym uwierzytelnieniu. Firma Microsoft oferuje dwie usługi STS będące standardami branżowymi:  
  
-   [Usługi Active Directory Federation Services (AD FS) 2.0](http://go.microsoft.com/fwlink/?LinkID=247516) (http://go.microsoft.com/fwlink/?LinkID=247516)  
  
-   [Usługi kontroli dostępu na platformie Azure systemu Windows (ACS)](http://go.microsoft.com/fwlink/?LinkID=247517) (http://go.microsoft.com/fwlink/?LinkID=247517).  
  
 Usługa AD FS 2.0 jest częścią systemu Windows Server R2 i może służyć jako usługa STS w scenariuszach lokalnych. Azure Active Directory kontroli dostępu (znanej także jako usługa kontroli dostępu lub ACS) to usługa w chmurze, wchodzących w skład systemu Microsoft Azure. Na potrzeby testowania lub w celach edukacyjnych można również używać innych usług STS do tworzenia aplikacji obsługujących oświadczenia. Na przykład można użyć lokalnego STS programowanie, który jest częścią [tożsamości i dostępu do narzędzi dla programu Visual Studio](http://go.microsoft.com/fwlink/?LinkID=245849) (http://go.microsoft.com/fwlink/?LinkID=245849) który jest dostępny w trybie online.  
  
 Aby utworzyć pierwszy obsługujący oświadczenia WCF usługi przy użyciu WIF, zobacz [jak: tworzenie oświadczeń WCF usługi przy użyciu WIF](http://msdn.microsoft.com/library/431e6415-62ed-4a9f-af03-f14d2b4dfe6d).  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do korzystania z programu WIF](../../../docs/framework/security/getting-started-with-wif.md)
