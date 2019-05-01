---
title: Migrowanie usług sieci Web na platformie ASP.NET do programu WCF
ms.date: 03/30/2017
ms.assetid: 1adbb931-f0b1-47f3-9caf-169e4edc9907
ms.openlocfilehash: 703088cdaae69d90d71fb950912538ea0662229b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948099"
---
# <a name="migrating-aspnet-web-services-to-wcf"></a>Migrowanie usług sieci Web na platformie ASP.NET do programu WCF
Program ASP.NET udostępnia narzędzia i biblioteki klas .NET Framework do tworzenia usług sieci Web, a także funkcje służące do hostingu usług w ramach usługi Internet Information Services (IIS). Windows Communication Foundation (WCF) udostępnia biblioteki klas .NET Framework, narzędzia i hostingu funkcje służące do włączania jednostek oprogramowania do komunikowania się za pomocą protokołów, w tym używanych przez usługi sieci Web.  Migrowanie usług sieci Web ASP.NET do programu WCF umożliwia aplikacjom korzystanie z zalet nowych funkcji i ulepszeń, które są unikatowe dla usługi WCF.  
  
 Usługi WCF ma kilka zalet ważne względem usług sieci Web platformy ASP.NET. Mimo że narzędzia usługi sieci Web platformy ASP.NET przeznaczone wyłącznie na potrzeby tworzenia usług sieci Web, usługi WCF zapewnia narzędzia, które mogą być używane podczas jednostek oprogramowania muszą zostać wprowadzone komunikować się ze sobą. Zmniejsza to liczbę technologii, które deweloperzy są wymagane, aby wiedzieć, aby pomieścić scenariuszy komunikacji między różnego oprogramowania, które z kolei zostanie obniżony koszt zasoby do tworzenia oprogramowania, a także czas wymagany do ukończenia oprogramowania projekty rozwoju.  
  
 Nawet w przypadku projektów rozwoju usługi sieci Web WCF obsługuje więcej protokoły usług sieci Web niż Obsługa usług sieci Web platformy ASP.NET. Te dodatkowe protokoły zapewniają bardziej zaawansowanych rozwiązań obejmujące, wśród innych rzeczy, sesje niezawodnej i transakcji.  
  
 Usługi WCF obsługuje więcej protokołów przesyłania wiadomości w usługach sieci Web platformy ASP.NET. Usługi sieci Web programu ASP.NET obsługuje tylko wysyłanie wiadomości przy użyciu protokołu HTTP (Hypertext Transfer). Usługi WCF obsługuje wysyłanie wiadomości przy użyciu protokołu HTTP, a także Transmission Control Protocol (TCP), nazwanych potoków i Microsoft usługi kolejkowania komunikatów (MSMQ). Co ważniejsze, WCF można rozszerzyć do obsługi dodatkowych protokołów. W związku z tym oprogramowanie opracowane przy użyciu usługi WCF, mogą być dostosowane do współpracuje z szerszego zakresu innego oprogramowania, zwiększając w ten sposób potencjalne zwrot z inwestycji.  
  
 Usługi WCF udostępnia znacznie bardziej rozbudowane funkcje służące do wdrażania i zarządzania aplikacjami w usługach sieci Web platformy ASP.NET zawiera. Oprócz system konfiguracji, która posiada również ASP.NET, usługi WCF oferuje edytora konfiguracji, śledzenie aktywności od nadawcy do odbiorców i z powrotem do dowolnej liczby pośredników, przeglądarka śledzenia, rejestrowanie komunikatów, ogromną liczbę liczników wydajności i Pomoc techniczna dla Instrumentacji zarządzania Windows.  
  
 Podane tych potencjalnych korzyści WCF względem programu ASP.NET w sieci Web usługi, jeśli są używane lub są biorąc pod uwagę przy użyciu usług sieci Web programu ASP.NET, masz kilka opcji:  
  
- W dalszym ciągu używać usług sieci Web platformy ASP.NET i przyznano korzyści proffered przez architekturę WCF.  
  
- Nadal korzystać z usług sieci Web platformy ASP.NET zamiarem przyjęcie WCF na pewien czas w przyszłości. Tematy w tej sekcji wyjaśniono, jak zmaksymalizować perspektyw będzie mógł korzystać z nowych aplikacji usługi sieci Web platformy ASP.NET razem z aplikacji tworzonych w przyszłości WCF. Tematy w tej sekcji opisano również sposób tworzenia nowej sieci Web platformy ASP.NET usług tak, aby ułatwić ich migrację do programu WCF. Jednak jeśli ważne jest zabezpieczenie usługi lub gwarancje niezawodności lub transakcji są wymagane, czy niestandardowe zarządzanie usługą będą musiały być skonstruowany, a następnie jest lepszym rozwiązaniem, aby wdrożyć usługę WCF. Usługi WCF jest przeznaczona dla dokładnie takich scenariuszy.  
  
- Przyjęcie WCF w nowych wdrożeniach przerywając Obsługa istniejącej aplikacji usług sieci Web platformy ASP.NET. Ten wybór jest bardzo prawdopodobne optymalny. Zalety usługi WCF, jego daje podczas spare koszt modyfikowania istniejących aplikacji z niego korzystać. W tym scenariuszu nowych aplikacji WCF mogą współistnieć z istniejącymi aplikacjami ASP.NET. Nowe aplikacje WCF będzie można używać istniejących usług sieci Web platformy ASP.NET i WCF może służyć do programu nowe możliwości operacyjne do istniejących aplikacji ASP.NET na podstawie tryb zgodności WCF ASP.NET.  
  
- Przyjmij WCF i Migrowanie istniejących aplikacji usługi sieci Web platformy ASP.NET do programu WCF. Można wybrać tę opcję, aby ulepszyć istniejące aplikacje przy użyciu funkcji oferowanych przez architekturę WCF lub do odtworzenia działania istniejących usług sieci Web platformy ASP.NET w nowe, bardziej zaawansowanych aplikacji WCF.  
  
> [!NOTE]
>  Należy uważać, jeśli usługa WCF jest hostowana przez usługi IIS został odinstalowany 5.x i platformy ASP.NET. Gdy usługa WCF jest hostowana przez usługi IIS można ich żądać 5.x, kod usługi, w przypadku odinstalowania programu ASP.NET. Po odinstalowaniu programu ASP.NET w systemie operacyjnym, które są uruchomione usługi IIS 5.x i WCF zostanie odinstalowany, plik z rozszerzeniem .svc jest traktowane jako plik tekstowy i jego zawartość, łącznie z dowolnego kodu źródłowego, jest zwracany do zleceniodawcy.  
  
 W tej sekcji opisano te opcje szczegółowo, porównuje usług sieci Web ASP.NET do programu WCF i zawiera instrukcje dotyczące sposobu przeprowadzenia migracji kodu usługi sieci Web platformy ASP.NET do programu WCF.  
  
## <a name="see-also"></a>Zobacz także

- [Prognozowanie wdrożeń programu Windows Communication Foundation: Ułatwianie migracji w przyszłości](../../../../docs/framework/wcf/feature-details/anticipating-adopting-wcf-migration.md)
- [Prognozowanie wdrożeń programu Windows Communication Foundation: Ułatwianie integracji w przyszłości](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)
- [Adoptowanie programu Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/adopting-wcf.md)
- [Porównanie usług internetowych platformy ASP.NET i architektury WCF na podstawie przeznaczenia oraz stosowanych standardów](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)
- [Porównywanie usług internetowych platformy ASP.NET z programem WCF na podstawie procesów programistycznych](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-development.md)
