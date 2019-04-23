---
title: Tworzenie pierwszej aplikacji internetowej ASP.NET obsługującej oświadczenia
ms.date: 03/30/2017
ms.assetid: 3ee8ee7f-caba-4267-9343-e313fae2876d
author: BrucePerlerMS
ms.openlocfilehash: 5a24a2117a031bfe49d0c27dbcefae6db00e6045
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59314558"
---
# <a name="building-my-first-claims-aware-aspnet-web-application"></a>Tworzenie pierwszej aplikacji internetowej ASP.NET obsługującej oświadczenia
## <a name="applies-to"></a>Dotyczy:  
  
-   Windows Identity Foundation (WIF)  
  
-   ASP.NET  
  
 W tym temacie opisano scenariusz tworzenia przy użyciu programu WIF aplikacji internetowych programu ASP.NET obsługujących oświadczenia. W scenariuszu aplikacji obsługującej oświadczenia zazwyczaj uczestniczą trzy strony: sama aplikacja, użytkownik końcowy i usługa tokenu zabezpieczającego (STS). Następujący rysunek opisuje ten scenariusz:  
  
 ![Diagram przedstawiający składników WIF podstawową aplikację internetową.](./media/building-my-first-claims-aware-aspnet-web-app/windows-identity-foundation-basic-web-application.gif)  
  
1. Aplikacja obsługująca oświadczenia używa programu WIF do identyfikowania nieuwierzytelnionych żądań i przekierowywania ich do usługi STS.  
  
2. Użytkownik końcowy podaje poświadczenia usłudze STS i po pomyślnym uwierzytelnieniu usługa STS wystawia mu token.  
  
3. Przy użyciu tokenu wystawionego przez usługę STS w żądaniu użytkownik jest przekierowywany z usługi STS do aplikacji obsługującej oświadczenia.  
  
4. Aplikacja obsługująca oświadczenia jest skonfigurowana do ufania usłudze STS i wystawianym przez nią tokenem. Aplikacja obsługująca oświadczenia używa programu WIF do weryfikacji i analizy tokenu. Deweloperzy Użyj odpowiedniego interfejsu API programu WIF i typy, na przykład **ClaimsPrincpal** do potrzeb aplikacji, takich jak zaimplementowanie dla niej autoryzacji.  
  
 Począwszy od .NET 4.5, WIF jest częścią pakietu .NET Framework. Klasy programu WIF bezpośrednio dostępne w ramach pozwala znacznie głębszą integrację tożsamości opartej na oświadczeniach na platformie .NET, ułatwiając korzystanie z oświadczeń. Mając program WIF 4.5, nie trzeba instalować żadnych składników zewnętrznych, aby rozpocząć projektowanie aplikacji internetowych obsługujących oświadczenia. Klasy programu WIF rozciągają się obecnie na rozmaite zestawy, z których najważniejsze to System.Security.Claims, System.IdentityModel i System.IdentityModel.Services.  
  
 STS to usługa, która wystawia tokeny po pomyślnym uwierzytelnieniu. Firma Microsoft oferuje dwie usługi STS będące standardami branżowymi:  
  
-   [Active Directory Federation Services (AD FS) 2.0](https://go.microsoft.com/fwlink/?LinkID=247516)
  
-   [Windows Azure usługa Access Control Service (ACS)](https://go.microsoft.com/fwlink/?LinkID=247517)
  
 Usługa AD FS 2.0 jest częścią systemu Windows Server R2 i może służyć jako usługa STS w scenariuszach lokalnych. ACS to usługa w chmurze oferowana jako część platformy Microsoft Azure. Na potrzeby testowania lub w celach edukacyjnych można również używać innych usług STS do tworzenia aplikacji obsługujących oświadczenia. Na przykład, można użyć Local Development STS, która jest częścią [narzędzie tożsamości i dostępu dla programu Visual Studio](https://go.microsoft.com/fwlink/?LinkID=245849) które jest dostępne bezpłatnie w trybie online.  
  
 Aby przy użyciu programu WIF utworzyć swoją pierwszą aplikację programu ASP.NET obsługującą oświadczenia, postępuj zgodnie z instrukcjami podanymi w jednym z następujących tematów:  
  
-   [Instrukcje: Tworzenie aplikacji sieci Web obsługującej oświadczenia platformy ASP.NET MVC przy użyciu programu WIF](../../../docs/framework/security/how-to-build-claims-aware-aspnet-mvc-web-app-using-wif.md)  
  
-   [Instrukcje: Tworzenie aplikacji formularzy sieci Web programu ASP.NET obsługującej oświadczenia za pomocą programu WIF](../../../docs/framework/security/how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)  
  
-   [Instrukcje: Tworzenie aplikacji programu ASP.NET obsługującej oświadczenia, za pomocą uwierzytelniania opartego na formularzach](../../../docs/framework/security/claims-aware-aspnet-app-forms-authentication.md)  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do korzystania z programu WIF](../../../docs/framework/security/getting-started-with-wif.md)
