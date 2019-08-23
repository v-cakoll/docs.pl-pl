---
title: Migrowanie usług sieci Web na platformie ASP.NET do programu WCF
ms.date: 03/30/2017
ms.assetid: 1adbb931-f0b1-47f3-9caf-169e4edc9907
ms.openlocfilehash: 52e0e499b5338e20377c14b598c045a5173df7d3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965336"
---
# <a name="migrating-aspnet-web-services-to-wcf"></a>Migrowanie usług sieci Web na platformie ASP.NET do programu WCF
ASP.NET oferuje .NET Framework biblioteki klas i narzędzia do tworzenia usług sieci Web, a także funkcje usług hostingu w ramach Internet Information Services (IIS). Windows Communication Foundation (WCF) zapewnia .NET Framework biblioteki klas, narzędzia i usługi hostingu umożliwiające obsługę jednostek oprogramowania w celu komunikowania się przy użyciu dowolnych protokołów, w tym tych używanych przez usługi sieci Web.  Migrowanie usług sieci Web ASP.NET do platformy WCF umożliwia aplikacjom korzystanie z nowych funkcji i ulepszeń, które są unikatowe dla usług WCF.  
  
 Funkcja WCF ma kilka ważnych korzyści względem usług sieci Web ASP.NET. Mimo że narzędzia usług sieci Web ASP.NET są przeznaczone wyłącznie do tworzenia usług sieci Web, funkcja WCF udostępnia narzędzia, których można używać w celu komunikacji między jednostkami oprogramowania. Pozwoli to zmniejszyć liczbę technologii, które deweloperzy muszą znać, aby sprostać różnym scenariuszom komunikacji z oprogramowaniem, co z kolei zmniejsza koszty zasobów programistycznych oprogramowania, a także czas ukończenia oprogramowania projekty programistyczne.  
  
 Nawet w przypadku projektów programistycznych usług sieci Web WCF obsługuje więcej protokołów usług sieci Web niż obsługa usług sieci Web ASP.NET. Te dodatkowe protokoły zapewniają bardziej zaawansowane rozwiązania obejmujące, między innymi, niezawodne sesje i transakcje.  
  
 Usługa WCF obsługuje więcej protokołów do transportowania komunikatów niż usługi sieci Web ASP.NET. Usługi sieci Web ASP.NET obsługują wysyłanie komunikatów przy użyciu protokołu HTTP (Hypertext Transfer Protocol). Usługa WCF obsługuje wysyłanie komunikatów przy użyciu protokołu HTTP, a także Transmission Control Protocol (TCP), nazwane potoki i usługi kolejkowania komunikatów (MSMQ) firmy Microsoft. Ważniejsze, można rozszerzyć obsługę dodatkowych protokołów transportowych. W związku z tym oprogramowanie opracowane przy użyciu programu WCF może zostać dostosowane do pracy z szeroką gamą innego oprogramowania, co zwiększa potencjalne zwroty w odniesieniu do inwestycji.  
  
 Usługa WCF oferuje wiele bogatszych funkcji wdrażania aplikacji i zarządzania nimi, niż zapewnia usługi sieci Web ASP.NET. Oprócz systemu konfiguracji, który ASP.NET również ma, usługa WCF oferuje Edytor konfiguracji, śledzenie działań od nadawców do odbiorców oraz z powrotem przez dowolną liczbę pośredników, Podgląd śledzenia, rejestrowanie komunikatów, ogromną liczbę liczników wydajności i Obsługa Instrumentacja zarządzania Windows.  
  
 Biorąc pod uwagę te potencjalne korzyści wynikające z usług sieci Web ASP.NET w programie WCF, jeśli używasz programu lub rozważasz korzystanie z usług sieci Web ASP.NET, możesz skorzystać z kilku opcji:  
  
- Kontynuuj korzystanie z usług sieci Web ASP.NET i powyżej korzyści proffered przez program WCF.  
  
- Kontynuuj korzystanie z usług sieci Web ASP.NET z zamiarem zastosowania WCF w pewnym momencie w przyszłości. W tematach w tej sekcji wyjaśniono, jak zmaksymalizować potencjalni klienci, aby mogli korzystać z nowych aplikacji usługi sieci Web ASP.NET wraz z przyszłymi aplikacjami WCF. W tematach w tej sekcji wyjaśniono również sposób tworzenia nowych usług sieci Web ASP.NET w celu ułatwienia migracji do programu WCF. Jeśli jednak Zabezpieczanie usług jest ważne lub wymagane są niezawodność lub gwarancje lub jeśli konieczne jest skonstruowanie niestandardowych obiektów zarządzania, jest to lepsza opcja zastosowania funkcji WCF. Funkcja WCF została zaprojektowana w taki sposób, aby dokładnie takie scenariusze.  
  
- Wdrażaj program WCF na potrzeby nowego rozwoju, pozostawiając nadal obsługę istniejących aplikacji usługi sieci Web ASP.NET. Ten wybór jest prawdopodobnie optymalny. Zapewnia korzyści wynikające z używania programu WCF, ograniczając jednocześnie koszty modyfikacji istniejących aplikacji. W tym scenariuszu nowe aplikacje WCF mogą współistnieć z istniejącymi aplikacjami ASP.NET. Nowe aplikacje WCF będą mogły korzystać z istniejących usług sieci Web ASP.NET, a platforma WCF może służyć do programowania nowych możliwości operacyjnych w istniejących aplikacjach ASP.NET na podstawie trybu zgodności ASP.NET WCF.  
  
- Wdrażaj WCF i Migruj istniejące aplikacje usługi sieci Web ASP.NET do platformy WCF. Możesz wybrać tę opcję, aby ulepszyć istniejące aplikacje przy użyciu funkcji udostępnianych przez program WCF, lub odtworzyć funkcjonalność istniejących usług sieci Web ASP.NET w ramach nowych, wydajnych aplikacji WCF.  
  
> [!NOTE]
> Należy zwrócić uwagę, jeśli usługa WCF jest hostowana przez usługi IIS 5. x i ASP.NET zostanie odinstalowany. Gdy usługa WCF jest hostowana przez program IIS 5. x, kod usługi można zażądać, jeśli ASP.NET zostanie odinstalowany. Gdy ASP.NET zostanie odinstalowany w systemie operacyjnym, w którym jest uruchomiony program IIS 5. x, a program WCF zostanie odinstalowany, plik z rozszerzeniem svc jest traktowany jako plik tekstowy i zawartość, łącznie z dowolnym kodem źródłowym, jest zwracany do obiektu żądającego.  
  
 W tej sekcji opisano te opcje szczegółowo, porównanie usług sieci Web ASP.NET z WCF i zawiera instrukcje dotyczące migrowania kodu usług sieci Web ASP.NET do programu WCF.  
  
## <a name="see-also"></a>Zobacz także

- [Przewidywanie przyjęcia Windows Communication Foundation: Przyspieszanie migracji w przyszłości](../../../../docs/framework/wcf/feature-details/anticipating-adopting-wcf-migration.md)
- [Przewidywanie przyjęcia Windows Communication Foundation: Przyspieszanie integracji w przyszłości](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)
- [Adoptowanie programu Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/adopting-wcf.md)
- [Porównanie usług internetowych platformy ASP.NET i architektury WCF na podstawie przeznaczenia oraz stosowanych standardów](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)
- [Porównywanie usług internetowych platformy ASP.NET z programem WCF na podstawie procesów programistycznych](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-development.md)
