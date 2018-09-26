---
title: Omówienie programu Windows Identity Foundation 4.5
ms.date: 03/30/2017
ms.assetid: 5f723345-7270-49e2-b638-b3a34bd40517
author: BrucePerlerMS
ms.openlocfilehash: 41829bee3df3e47c0ccd712ecc9a314e5971aba0
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47070230"
---
# <a name="windows-identity-foundation-45-overview"></a>Omówienie programu Windows Identity Foundation 4.5
Program Windows Identity Foundation 4.5 to zestaw klas programu .NET Framework służących do wdrożenia mechanizmu tożsamości opartych na oświadczeniach w aplikacjach. Korzystając z niego, łatwiej możesz czerpać korzyści z aplikacji i usług obsługujących oświadczenia. Programu WIF 4.5 można użyć w dowolnej aplikacji internetowej lub usłudze internetowej, która korzysta z programu .NET Framework w wersji 4.5 lub nowszej. Program WIF to tylko jeden element rodziny oprogramowania tożsamości federacyjnych firmy Microsoft, który implementuje wspólną wizję branżową opartą na otwartych standardach. Tożsamość federacyjna składa się z trzech składników: [Active Directory® Federation Services](https://go.microsoft.com/fwlink/?LinkID=247516) (AD FS) 2.0, [usługi kontroli dostępu Azure Windows](https://go.microsoft.com/fwlink/?LinkID=247517) (ACS) i programu WIF. Te trzy elementy tworzą razem jądro nowej, opracowanej przez firmę Microsoft platformy tożsamości i dostępu opartej na oświadczeniach i działającej w chmurze.  
  
 Aby uzyskać więcej informacji dotyczących programu WIF, zobacz [witryny sieci Web programu Windows Identity Foundation](https://go.microsoft.com/fwlink/?LinkId=149009) w Centrum deweloperów zabezpieczeń w witrynie MSDN. Wprowadzenie do tworzenia aplikacji przy użyciu programu WIF, zobacz [programowania Windows Identity Foundation](https://go.microsoft.com/fwlink/?LinkId=210158) przez Vittorio Bertocci (opublikowany przez wydawnictwo Microsoft Press).  
  
## <a name="wif-45-features"></a>Funkcje programu WIF 4.5  
 Program WIF 4.5 to struktura służąca do tworzenia aplikacji obsługujących tożsamości. Łączy ona podstawowe funkcje protokołów WS-Trust i WS-Federation i prezentuje deweloperom interfejsy API do tworzenia aplikacji obsługujących oświadczenia i, w razie potrzeby, usług tokenu zabezpieczającego (STS). Aplikacje mogą używać programu WIF do przetwarzania tokenów wystawionych przez usługi STS, takie jak AD FS 2.0 i ACS, oraz do podejmowania decyzji na podstawie tożsamości w aplikacji internetowej lub usłudze internetowej.  
  
 Program WIF 4.5 ma następujące główne funkcje:  
  
-   Tworzenie aplikacji obsługujących oświadczenia (aplikacji jednostek uzależnionych). Program WIF ułatwia deweloperom tworzenie aplikacji obsługujących oświadczenia. Oprócz modelu oświadczeń oferuje deweloperom aplikacji bogaty zestaw interfejsów API pomocny w podejmowaniu decyzji dotyczących dostępu użytkownika na podstawie oświadczeń.  Ponadto program WIF zapewnia deweloperom spójny sposób programowania, niezależnie od tego, czy decydują się na tworzenie aplikacji w środowisku programu ASP.NET, czy usługi WCF.  
  
-   Wbudowywanie obsługi delegowania tożsamości w aplikacje obsługujące oświadczenia.  Program WIF oferuje możliwości zachowywania tożsamości oryginalnych obiektów żądających przy przekraczaniu granic wielu usług. Tę możliwość można osiągnąć, stosując funkcję „ActAs” lub „OnBehalfOf” w strukturze, a ponadto deweloperzy mają możliwość dodawania obsługi delegowania tożsamości do ich aplikacji obsługujących oświadczenia.  
  
-   Tworzenie niestandardowych usług STS.  Program WIF znacznie ułatwia utworzenie niestandardowej usługi STS, która obsługuje protokół WS-Trust. Taką usługę STS nazywa się również aktywną usługą STS.  
  
     Ponadto struktura ta oferuje możliwość utworzenia usługi STS, która obsługuje protokół WS-Federation na potrzeby klientów przeglądarki sieci Web. Taką usługę STS nazywa się również pasywną usługą STS.  
  
-   Nowe narzędzie tożsamości i dostępu dla programu Visual Studio 11, które umożliwia zabezpieczenie aplikacji za pomocą tożsamości opartej na oświadczeniach i akceptowanie użytkowników z wielu dostawców tożsamości. To narzędzie programu WIF możesz pobrać z następującego adresu URL: [ https://go.microsoft.com/fwlink/?LinkID=245849 ](https://go.microsoft.com/fwlink/?LinkID=245849) lub bezpośrednio z poziomu programu Visual Studio 11, wyszukując "tożsamość" w Menedżerze rozszerzeń. Aby uzyskać więcej informacji, zobacz [narzędzie tożsamości i dostępu dla programu Visual Studio 2012](../../../docs/framework/security/identity-and-access-tool-for-vs.md).  
  
 Program WIF obsługuje następujące główne scenariusze:  
  
-   Federacja.  Program WIF umożliwia włączenie federacji między dwoma lub większą liczbą partnerów. Jego obsługa tworzenia aplikacji obsługujących oświadczenia (jednostek uzależnionych) i niestandardowych usług STS pomaga deweloperom w realizacji tego scenariusza.  
  
-   Delegowanie tożsamości.  Program WIF ułatwia zachowywanie tożsamości przy przekraczaniu granic różnych usług, dzięki czemu deweloperzy mogą zrealizować scenariusz delegowania tożsamości.  
  
-   Stopniowo rosnące wymaganie dotyczące uwierzytelniania. Wymagania dotyczące uwierzytelniania dla różnych zasobów w obrębie aplikacji mogą się zmieniać. Program WIF oferuje deweloperom możliwość tworzenia aplikacji, których wymagania dotyczące uwierzytelniania mogą stopniowo rosnąć (na przykład: początkowe logowanie przy użyciu uwierzytelniania na podstawie nazwy użytkownika/hasła, a następnie przejście do uwierzytelniania przy użyciu karty inteligentnej).  
  
 Korzystając z programu WIF, łatwiej możesz czerpać korzyści z modelu tożsamości opartych na oświadczeniach. Aby uzyskać więcej informacji, zobacz [Windows Identity Foundation oficjalny dokument dla deweloperów](https://download.microsoft.com/download/7/d/0/7d0b5166-6a8a-418a-addd-95ee9b046994/windowsidentityfoundationwhitepaperfordevelopers-rtw.pdf).
