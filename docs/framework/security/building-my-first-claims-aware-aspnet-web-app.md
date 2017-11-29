---
title: "Tworzenie mojej pierwszej aplikacji sieci Web ASP.NET obsługujących oświadczenia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ee8ee7f-caba-4267-9343-e313fae2876d
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: aa25f163199652618e35399c6548a9864a17370a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="building-my-first-claims-aware-aspnet-web-application"></a>Tworzenie mojej pierwszej aplikacji sieci Web ASP.NET obsługujących oświadczenia
## <a name="applies-to"></a>Dotyczy:  
  
-   Windows Identity Foundation (WIF)  
  
-   ASP.NET  
  
 W tym temacie opisano scenariusz tworzenia przy użyciu programu WIF aplikacji sieci Web programu ASP.NET obsługującej oświadczenia. W scenariuszu aplikacji obsługującej oświadczenia zazwyczaj uczestniczą trzy strony: sama aplikacja, użytkownik końcowy i usługa tokenu zabezpieczającego (STS). Następujący rysunek opisuje ten scenariusz:  
  
 ![Aplikacja sieci Web podstawowe WIF](../../../docs/framework/security/media/wifbasicwebapp.gif "WIFBasicWebApp")  
  
1.  Aplikacja obsługująca oświadczenia używa programu WIF do identyfikowania nieuwierzytelnionych żądań i przekierowywania ich do usługi STS.  
  
2.  Użytkownik końcowy podaje poświadczenia usłudze STS i po pomyślnym uwierzytelnieniu usługa STS wystawia mu token.  
  
3.  Przy użyciu tokenu wystawionego przez usługę STS w żądaniu użytkownik jest przekierowywany z usługi STS do aplikacji obsługującej oświadczenia.  
  
4.  Aplikacja obsługująca oświadczenia jest skonfigurowana do ufania usłudze STS i wystawianym przez nią tokenem. Aplikacja obsługująca oświadczenia używa programu WIF do weryfikacji i analizy tokenu. Deweloperzy Użyj odpowiedniego interfejsu API WIF i typów, na przykład **ClaimsPrincpal** na potrzeby aplikacji, takich jak wdrażanie autoryzacji dla niego.  
  
 Począwszy od platformy .NET 4.5, WIF jest częścią pakietu .NET Framework. O klasach WIF bezpośrednio dostępne w ramach umożliwia znacznie lepsza integracja tożsamości opartego na oświadczeniach w środowisku .NET, co ułatwia użyć oświadczeń. Mając program WIF 4.5, nie trzeba instalować żadnych składników zewnętrznych, aby rozpocząć projektowanie aplikacji sieci Web obsługujących oświadczenia. Klasy programu WIF rozciągają się obecnie na rozmaite zestawy, z których najważniejsze to System.Security.Claims, System.IdentityModel i System.IdentityModel.Services.  
  
 STS to usługa, która wystawia tokeny po pomyślnym uwierzytelnieniu. Firma Microsoft oferuje dwie usługi STS będące standardami branżowymi:  
  
-   [Usługi Active Directory Federation Services (AD FS) 2.0](http://go.microsoft.com/fwlink/?LinkID=247516) (http://go.microsoft.com/fwlink/?LinkID=247516)  
  
-   [Usługi kontroli dostępu na platformie Azure systemu Windows (ACS)](http://go.microsoft.com/fwlink/?LinkID=247517) (http://go.microsoft.com/fwlink/?LinkID=247517).  
  
 Usługa AD FS 2.0 jest częścią systemu Windows Server R2 i może służyć jako usługa STS w scenariuszach lokalnych. ACS to usługa w chmurze oferowana jako część platformy Microsoft Azure. Na potrzeby testowania lub w celach edukacyjnych można również używać innych usług STS do tworzenia aplikacji obsługujących oświadczenia. Na przykład można użyć lokalnego STS programowanie, który jest częścią [tożsamości i dostępu do narzędzi dla programu Visual Studio](http://go.microsoft.com/fwlink/?LinkID=245849) (http://go.microsoft.com/fwlink/?LinkID=245849) który jest dostępny w trybie online.  
  
 Aby przy użyciu programu WIF utworzyć swoją pierwszą aplikację programu ASP.NET obsługującą oświadczenia, postępuj zgodnie z instrukcjami podanymi w jednym z następujących tematów:  
  
-   [Porady: Tworzenie aplikacji sieci Web obsługujący oświadczenia platformy ASP.NET MVC za pomocą WIF](../../../docs/framework/security/how-to-build-claims-aware-aspnet-mvc-web-app-using-wif.md)  
  
-   [Porady: Tworzenie aplikacji formularzy sieci Web obsługujący oświadczenia ASP.NET za pomocą WIF](../../../docs/framework/security/how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)  
  
-   [Porady: Tworzenie aplikacji obsługującej oświadczenia ASP.NET przy użyciu uwierzytelniania opartego na formularzach](../../../docs/framework/security/claims-aware-aspnet-app-forms-authentication.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do korzystania z programu WIF](../../../docs/framework/security/getting-started-with-wif.md)
