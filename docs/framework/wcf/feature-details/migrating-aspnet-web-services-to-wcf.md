---
title: Migrowanie usług sieci Web na platformie ASP.NET do programu WCF
ms.date: 03/30/2017
ms.assetid: 1adbb931-f0b1-47f3-9caf-169e4edc9907
ms.openlocfilehash: 7d43c66952d17a91e38ae1b086478b9416321b8a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33494565"
---
# <a name="migrating-aspnet-web-services-to-wcf"></a>Migrowanie usług sieci Web na platformie ASP.NET do programu WCF
Program ASP.NET udostępnia biblioteki klas .NET Framework i narzędzia do tworzenia usług sieci Web, a także urządzenia do hostingu usług w ramach usługi Internet Information Services (IIS). Windows Communication Foundation (WCF) oferuje biblioteki klas .NET Framework, narzędzia i hostingu urządzenia do włączania jednostek oprogramowania do komunikowania się przy użyciu protokołów, w tym używanych przez usługi sieci Web.  Migrowanie usług sieci Web ASP.NET do programu WCF umożliwia aplikacjom korzystać z nowych funkcji i ulepszeń, które są unikatowe dla usługi WCF.  
  
 Usługi WCF ma kilka zalet ważne względem usługi sieci Web ASP.NET. Narzędzia usług sieci Web ASP.NET są przeznaczone wyłącznie na potrzeby tworzenia usług sieci Web, usługi WCF udostępnia narzędzia, które mogą być używane, gdy oprogramowanie jednostek muszą być wprowadzane do komunikowania się ze sobą. Zmniejszy to liczbę technologie wymagane do uwzględnienia scenariusze komunikacji innego oprogramowania, które z kolei zostanie obniżony koszt zasobów rozwoju oprogramowania, a także czas wymagany do ukończenia oprogramowania deweloperów rozwoju projektów.  
  
 Nawet w przypadku projektów rozwoju usług sieci Web usługi WCF obsługuje więcej protokoły usług sieci Web niż Obsługa usług sieci Web ASP.NET. Te dodatkowe protokoły zapewniają bardziej zaawansowanych rozwiązań obejmujące, między inne rzeczy, niezawodne sesje i transakcji.  
  
 Usługi WCF obsługuje protokoły więcej do transportu wiadomości niż usługi sieci Web ASP.NET. Usługi sieci Web programu ASP.NET obsługują tylko wysyłanie wiadomości przy użyciu protokołu HTTP (Hypertext Transfer). Usługi WCF obsługuje wysyłanie wiadomości przy użyciu protokołu HTTP, a także Transmission Control Protocol (TCP), nazwanych potoków i usługi kolejkowania wiadomości firmy Microsoft (MSMQ). Większe znaczenie WCF może zostać rozszerzony do obsługi dodatkowych protokołów. W związku z tym oprogramowania utworzony przy użyciu programu WCF można dostosować do współdziała z szeroką gamę innego oprogramowania, zwiększając potencjalnych zwrot z inwestycji.  
  
 WCF oferuje znacznie bardziej zaawansowane funkcje urządzeń do wdrażania i zarządzania aplikacjami niż usługi sieci Web programu ASP.NET zapewnia. Oprócz system konfiguracji, który ma także ASP.NET, usługi WCF oferuje edytora konfiguracji, śledzenie działania od nadawcy do odbiorcy i z powrotem przy użyciu dowolnej liczby pośredników, przeglądarka śledzenia, rejestrowanie komunikatów, ogromną liczbę liczników wydajności i Obsługa Instrumentacji zarządzania Windows.  
  
 Podane tych potencjalnych korzyści WCF względem sieci Web ASP.NET usługi, jeśli są używane lub są biorąc pod uwagę przy użyciu usługi sieci Web ASP.NET, dostępnych jest kilka opcji:  
  
-   Nadal używać usług sieci Web ASP.NET i przyznano korzyści proffered przez usługę WCF.  
  
-   Zachowaj przy użyciu usług sieci Web ASP.NET w celu przyjęcia usługi WCF w czasie w przyszłości. Tematy w tej sekcji opisano sposób zmaksymalizować perspektyw było go używać nowej aplikacji usługi sieci Web ASP.NET oraz przyszłych aplikacji WCF. Tematy w tej sekcji opisano również sposób tworzenia nowej sieci Web ASP.NET usług, aby ułatwić ich migracja do programu WCF. Jednak jeśli ważne jest zabezpieczenie usługi lub gwarancje niezawodności lub transakcji są wymagane, czy niestandardowych obiektów zarządzania musi być skonstruowany, a następnie jest lepszym rozwiązaniem do przyjęcia usługi WCF. Usługi WCF jest przeznaczona dla dokładnie takich scenariuszy.  
  
-   Przyjmuje WCF dla nowych aplikacji, pozostawiając Obsługa istniejących aplikacji usługi sieci Web ASP.NET. Ten wybór jest bardzo prawdopodobne optymalny. Zalety usługi WCF, go daje podczas Reserve Sparing Table koszt modyfikacji istniejących aplikacji z niego korzystać. W tym scenariuszu nowych aplikacji WCF mogą współistnieć z istniejących aplikacji ASP.NET. Nowe aplikacje WCF będą mogli używać istniejących usług sieci Web ASP.NET i WCF może służyć do programu nowe funkcje operacyjne w aplikacji ASP.NET z tryb zgodności WCF ASP.NET.  
  
-   Przyjmuje WCF i migracji istniejącej aplikacji usługi sieci Web ASP.NET do programu WCF. Możesz wybrać tę opcję w celu zwiększenia istniejących aplikacji z funkcji udostępnianych przez usługi WCF lub do odtworzenia funkcjonalności istniejących usług sieci Web ASP.NET w ramach nowych, bardziej zaawansowanych aplikacji WCF.  
  
> [!NOTE]
>  Należy zwrócić uwagę, jeśli usługa WCF jest hostowana przez usługi IIS 5.x i platformy ASP.NET został odinstalowany. Gdy usługa WCF jest hostowana przez usługi IIS 5.x, kod usługi może wystąpić w przypadku odinstalowania programu ASP.NET. Po odinstalowaniu programu ASP.NET w systemie operacyjnym, który jest uruchomiony program IIS 5.x i WCF zostanie odinstalowana, plik z rozszerzeniem .svc jest traktowane jako plik tekstowy i zawartość, łącznie z dowolnego kodu źródłowego, jest zwracany do obiektu żądającego.  
  
 W tej sekcji opisano te opcje szczegółowo, porównanie usług sieci Web ASP.NET do programu WCF i zawiera instrukcje dotyczące sposobu przeprowadzenia migracji do programu WCF kodu usługi sieci Web programu ASP.NET.  
  
## <a name="see-also"></a>Zobacz też  
 [Prognozowanie wdrożeń programu Windows Communication Foundation: ułatwianie migracji w przyszłości](../../../../docs/framework/wcf/feature-details/anticipating-adopting-wcf-migration.md)  
 [Prognozowanie wdrożeń programu Windows Communication Foundation: ułatwianie integracji w przyszłości](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)  
 [Adoptowanie programu Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/adopting-wcf.md)  
 [Porównanie usług internetowych platformy ASP.NET i architektury WCF na podstawie przeznaczenia oraz stosowanych standardów](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)  
 [Porównywanie usług internetowych platformy ASP.NET z programem WCF na podstawie procesów programistycznych](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-development.md)
