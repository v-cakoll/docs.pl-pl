---
title: Tworzenie pierwszej aplikacji internetowej ASP.NET obsługującej oświadczenia
ms.date: 03/30/2017
ms.assetid: 3ee8ee7f-caba-4267-9343-e313fae2876d
author: BrucePerlerMS
ms.openlocfilehash: 900ee49b4bf51eeb6e3b0c0cf6879cc12a0cb071
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045588"
---
# <a name="building-my-first-claims-aware-aspnet-web-application"></a>Tworzenie pierwszej aplikacji internetowej ASP.NET obsługującej oświadczenia
## <a name="applies-to"></a>Dotyczy:  
  
- Windows Identity Foundation (WIF)  
  
- ASP.NET  
  
 W tym temacie opisano scenariusz tworzenia przy użyciu programu WIF aplikacji internetowych programu ASP.NET obsługujących oświadczenia. W scenariuszu aplikacji obsługującej oświadczenia zazwyczaj uczestniczą trzy strony: sama aplikacja, użytkownik końcowy i usługa tokenu zabezpieczającego (STS). Następujący rysunek opisuje ten scenariusz:  
  
 ![Diagram przedstawiający WIF podstawowe składniki aplikacji sieci Web.](./media/building-my-first-claims-aware-aspnet-web-app/windows-identity-foundation-basic-web-application.gif)  
  
1. Aplikacja obsługująca oświadczenia używa programu WIF do identyfikowania nieuwierzytelnionych żądań i przekierowywania ich do usługi STS.  
  
2. Użytkownik końcowy podaje poświadczenia usłudze STS i po pomyślnym uwierzytelnieniu usługa STS wystawia mu token.  
  
3. Przy użyciu tokenu wystawionego przez usługę STS w żądaniu użytkownik jest przekierowywany z usługi STS do aplikacji obsługującej oświadczenia.  
  
4. Aplikacja obsługująca oświadczenia jest skonfigurowana do ufania usłudze STS i wystawianym przez nią tokenem. Aplikacja obsługująca oświadczenia używa programu WIF do weryfikacji i analizy tokenu. Deweloperzy używają odpowiedniego interfejsu API WIF i typów, na przykład **ClaimsPrincipal** dla potrzeb aplikacji, takich jak implementacja autoryzacji dla tego programu.  
  
 Począwszy od platformy .NET 4,5, WIF jest częścią pakietu .NET Framework. Posiadanie klas WIF bezpośrednio dostępnych w ramach platformy pozwala znacznie lepiej przeprowadzić integrację tożsamości opartej na oświadczeniach w programie .NET, ułatwiając korzystanie z oświadczeń. Mając program WIF 4.5, nie trzeba instalować żadnych składników zewnętrznych, aby rozpocząć projektowanie aplikacji internetowych obsługujących oświadczenia. Klasy programu WIF rozciągają się obecnie na rozmaite zestawy, z których najważniejsze to System.Security.Claims, System.IdentityModel i System.IdentityModel.Services.  
  
 STS to usługa, która wystawia tokeny po pomyślnym uwierzytelnieniu. Firma Microsoft oferuje dwie usługi STS będące standardami branżowymi:  
  
- [Active Directory Federation Services (AD FS) 2.0](https://go.microsoft.com/fwlink/?LinkID=247516)
  
- [Access Control Service systemu Windows Azure (ACS)](https://go.microsoft.com/fwlink/?LinkID=247517)
  
 Usługa AD FS 2.0 jest częścią systemu Windows Server R2 i może służyć jako usługa STS w scenariuszach lokalnych. ACS to usługa w chmurze oferowana jako część platformy Microsoft Azure. Na potrzeby testowania lub w celach edukacyjnych można również używać innych usług STS do tworzenia aplikacji obsługujących oświadczenia. Można na przykład użyć lokalnego programu STS do tworzenia [tożsamości i narzędzia dostępu dla programu Visual Studio](https://go.microsoft.com/fwlink/?LinkID=245849) , co jest dostępne w trybie online.  
  
 Aby przy użyciu programu WIF utworzyć swoją pierwszą aplikację programu ASP.NET obsługującą oświadczenia, postępuj zgodnie z instrukcjami podanymi w jednym z następujących tematów:  
  
- [Instrukcje: Tworzenie aplikacji sieci Web ASP.NET MVC z obsługą oświadczeń przy użyciu WIF](how-to-build-claims-aware-aspnet-mvc-web-app-using-wif.md)  
  
- [Instrukcje: Tworzenie aplikacji opartych na oświadczeniach ASP.NET Web Forms przy użyciu WIF](how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)  
  
- [Instrukcje: Tworzenie aplikacji ASP.NET obsługującej oświadczenia przy użyciu uwierzytelniania opartego na formularzach](claims-aware-aspnet-app-forms-authentication.md)  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do korzystania z programu WIF](getting-started-with-wif.md)
