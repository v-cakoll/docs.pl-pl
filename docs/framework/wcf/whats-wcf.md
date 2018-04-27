---
title: Co to jest program Windows Communication Foundation
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation [WCF], technology overview
- technology overview [WCF]
- WCF [WCF], technology overview
ms.assetid: 40e1009d-ef15-450b-9848-62eabe5e5738
caps.latest.revision: 51
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2fa6efdc61620647d5c6318746e61e09cdde7a46
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="what-is-windows-communication-foundation"></a>Co to jest program Windows Communication Foundation
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] to platforma do tworzenia aplikacji korzystających z usług. Przy użyciu [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], możesz wysłać dane jako asynchroniczne komunikaty z punktu końcowego jednej usługi do innego. Punkt końcowy usługi mogą być częścią stale dostępna usługa hostowana przez usługi IIS, lub można ją z usługą hostowaną w aplikacji. Punkt końcowy może być klienta usługi, która wysyła żądanie danych z punktu końcowego usługi. Komunikaty może być tak proste, jak pojedynczy znak lub słowo wysyłane w formacie XML lub złożonym, strumień danych binarnych. Kilka przykładowych scenariuszy obejmują:  
  
-   Usługa bezpiecznego przetwarzania transakcji.  
  
-   Usługa, która dostarcza bieżące dane do innych użytkowników, na przykład raport ruchu lub inne usługi monitorowania.  
  
-   Usługa rozmowy, która umożliwia dwóch osób do komunikowania się lub wymiany danych w czasie rzeczywistym.  
  
-   Aplikacja pulpitu nawigacyjnego sondowania jeden lub więcej usług danych, który prezentuje je w prezentacji logiczne.  
  
-   Udostępnianie implementowane za pomocą programu Windows Workflow Foundation jako usługa WCF przepływ pracy.  
  
-   Aplikacja Silverlight sondowanie usługę najnowsze źródła danych.  
  
 Podczas tworzenia takich aplikacji było możliwe przed istnienie [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] ułatwia programowanie punktów końcowych niż kiedykolwiek wcześniej. Podsumowując [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] oferuje proste w zarządzaniu podejście do tworzenia usług sieci Web i klientami usługi sieci Web.  
  
## <a name="features-of-wcf"></a>Funkcje programu WCF  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] zawiera następujący zestaw funkcji. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Szczegóły funkcji WCF](../../../docs/framework/wcf/feature-details/index.md).  
  
-   **Orientacji usługi**  
  
     W wyniku użycia standardów WS jest to, że [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] umożliwia utworzenie *na usługach* aplikacji. Zorientowane na usługę architektura (SOA) jest zależność od usługi sieci Web do wysyłania i odbierania danych. Usługi mają ogólne zaletą jest luźno połączonych zamiast ustalony z jednej aplikacji do innej. Relację luźno połączonych oznacza to, czy każdy klient utworzony na dowolnej platformie połączenie usługi tak długo, jak kontrakty niezbędne są spełnione.  
  
-   **Współdziałanie**  
  
     [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] implementuje standardy branżowe nowoczesnych współdziałania usługi sieci Web. [!INCLUDE[crabout](../../../includes/crabout-md.md)] Obsługiwane standardy, zobacz [współdziałanie i integracja](../../../docs/framework/wcf/feature-details/interoperability-and-integration.md).  
  
-   **Wiele wzorców wiadomości**  
  
     Komunikaty są wymieniane w jednym z kilku. Najbardziej typowe wzorzec jest wzorzec żądanie/odpowiedź, gdzie jeden punkt końcowy żąda danych od drugiego punktu końcowego. Drugi odpowiedzi punktu końcowego. Istnieją inne wzorców, takich jak komunikat jednokierunkowy, w której jeden punkt końcowy wysyła wiadomość bez żadnych oczekiwania odpowiedzi. Bardziej złożone wzorzec jest wzorzec dupleksu programu exchange, gdy dwa punkty końcowe nawiązania połączenia i wysyłania danych i z powrotem, podobnie jak program obsługi wiadomości błyskawicznych. [!INCLUDE[crabout](../../../includes/crabout-md.md)] implementowania wymiany wiadomości różnych wzorców przy użyciu [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] zobacz [kontrakty](../../../docs/framework/wcf/feature-details/contracts.md).  
  
-   **Metadane usługi**  
  
     [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Obsługa publikowania metadanych usługi formatu określonego w standardy branżowe, takie jak WSDL, schemat XML i WS-Policy. Te metadane, można automatycznie wygenerować i skonfigurować klientów do uzyskiwania dostępu do [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usług. Metadane mogą być publikowane za pośrednictwem protokołu HTTP i HTTPS lub przy użyciu standardu wymiany metadanych usługi sieci Web. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Metadane](../../../docs/framework/wcf/feature-details/metadata.md).  
  
-   **Kontrakty danych**  
  
     Ponieważ [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] jest utworzony przy użyciu [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], zawiera także kod przyjaznego metod podawania kontrakty mają zostać wymuszone. Jeden z uniwersalnych typów kontraktów jest kontraktu danych. W zasadzie jak kodu usługi za pomocą Visual C# lub Visual Basic, najprostszym sposobem obsługi danych jest przez utworzenie klas reprezentujących jednostki danych z właściwościami, które należą do obiektu danych. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Zawiera kompleksowe system do pracy z danymi w ten sposób łatwe. Po utworzeniu klasy, które przedstawiają dane z usługą automatycznie generuje metadanych, które umożliwia klientom są zgodne z typami danych, które zostały zaprojektowane. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Używanie kontraktów danych](../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
  
-   **Zabezpieczenia**  
  
     Komunikaty mogą być szyfrowane, aby chronić prywatność i można wymagać od użytkowników uwierzytelnić się przed uzyskaniem dostępu do odbierania wiadomości. Za pomocą dobrze znanych standardy, takie jak protokół SSL lub WS-SecureConversation można zaimplementować zabezpieczeń. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Zabezpieczenia](../../../docs/framework/wcf/feature-details/security.md).  
  
-   **Wiele transport i kodowanie**  
  
     Na dowolnym kilka wbudowanych protokołów i kodowania można wysłać wiadomości. Najbardziej typowe protokołu i kodowanie jest wysłanie wiadomości SOAP przy użyciu protokołu HTTP (HyperText Transfer) do użytku w sieci World Wide Web kodowany tekst. Alternatywnie [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] umożliwia wysyłanie komunikatów za pośrednictwem protokołu TCP, nazwanych potoków lub usługi MSMQ. Te komunikaty mogą być kodowane jako tekst lub za pomocą zoptymalizowanego formatu binarnego.  Dane binarne mogą być wysyłane efektywne wykorzystanie standardowego mechanizmu MTOM. Brak podanego transportu lub kodowania własnych potrzeb można utworzyć własny transportu lub kodowania. [!INCLUDE[crabout](../../../includes/crabout-md.md)] transport i kodowanie obsługiwane przez [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] zobacz [transportów](../../../docs/framework/wcf/feature-details/transports.md).  
  
-   **Niezawodne i umieszczonych w kolejce wiadomości**  
  
     [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] obsługuje wymianę komunikatów niezawodnej przy użyciu sesji niezawodnej implementowane za pośrednictwem usługi WS-Reliable Messaging i przy użyciu usługi MSMQ. [!INCLUDE[crabout](../../../includes/crabout-md.md)] Obsługa komunikatów niezawodnej i umieszczonych w kolejce w [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] zobacz [kolejki i sesje niezawodne](../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md).  
  
-   **Trwałe wiadomości**  
  
     Trwałe komunikatu to taki, który nigdy nie zostaną utracone z powodu przerw w działaniu w komunikacie. Wiadomości we wzorcu komunikatów trwałe zawsze są zapisywane w bazie danych. W przypadku zakłóceń bazy danych umożliwia wznowienie wymiany wiadomości po przywróceniu połączenia. Można również utworzyć trwałe wiadomości przy użyciu systemu Windows Workflow Foundation (WF). [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Usługi przepływu pracy](../../../docs/framework/wcf/feature-details/workflow-services.md).  
  
-   **Transakcje**  
  
     Usługi WCF obsługuje również transakcji przy użyciu jednej z trzech modele transakcji: WS-AtomicTtransactions, interfejsy API w <xref:System.Transactions> przestrzeni nazw i Microsoft Distributed Transaction Coordinator. [!INCLUDE[crabout](../../../includes/crabout-md.md)] Obsługa transakcji w [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] zobacz [transakcji](../../../docs/framework/wcf/feature-details/transactions-in-wcf.md).  
  
-   **AJAX i obsługa REST**  
  
     REST jest przykładem rozwijającą się technologia Web 2.0. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] można skonfigurować do przetwarzania danych XML "zwykły", który nie jest opakowany koperty protokołu SOAP. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] można również rozszerzyć w celu obsługi określonych formatów XML, takie jak ATOM popularnych RSS (standardowe), a nawet z systemem innym niż XML formatach, takich jak JavaScript Object Notation (JSON).  
  
-   **Rozszerzalność**  
  
     [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Architektura ma kilka punktów rozszerzalności. Jeśli wymagana jest dodatkowa możliwość, istnieje wiele punktów wejścia, które pozwalają dostosować zachowanie usługi. [!INCLUDE[crabout](../../../includes/crabout-md.md)] punkty rozszerzeń dostępnych w temacie [rozszerzanie WCF](../../../docs/framework/wcf/extending/index.md).  
  
## <a name="wcf-integration-with-other-microsoft-technologies"></a>Integracja WCF z innych technologii firmy Microsoft  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] to elastyczna platforma. Ze względu na to wyjątkową elastyczność [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] służy również kilka innych produktów firmy Microsoft. Zrozumienie podstaw [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], masz natychmiastowe korzyści, jeśli również przy użyciu jednej z tych produktów.  
  
 Pierwszy technologię tak, aby skojarzyć [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] został Windows Workflow Foundation (WF). Przepływy pracy uprościć tworzenie aplikacji przez Hermetyzowanie kroki w przepływie pracy jako "działania". W pierwszej wersji programu Windows Workflow Foundation Deweloper było utworzenie hosta przepływu pracy. Na następną wersję programu Windows Workflow Foundation została zintegrowana z [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]. Który dozwolone każdy przepływ pracy ma być łatwo obsługiwana w [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi; można to zrobić, wybierając automatycznie WCF/WF typu projektu w [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].  
  
 Microsoft BizTalk Server R2 również używa [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] technologii komunikacji. BizTalk zaprojektowano w celu odbierania i przekształcanie danych z jednego formatu standardowych. Wiadomości musi być dostarczane do jej centralnej komunikat w przypadku, gdy wiadomość można je przekształcać za pomocą strict mapowania lub za pomocą funkcji BizTalk, takie jak jego aparatu przepływu pracy. Teraz można używać BizTalk [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] karty Linia biznesowych (LOB) na dostarczenie wiadomości do okna komunikatu.  
  
 Program Microsoft Silverlight to platforma do tworzenia interoperacyjne, rozbudowanych aplikacji sieci Web, które umożliwiają deweloperom tworzenie witryn sieci Web intensywnie nośnika (na przykład klip wideo przesyłany strumieniowo). Począwszy od wersji 2, Silverlight ma włączone [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] technologii komunikacji, aby połączyć aplikacje Silverlight do [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] punktów końcowych.  
  
 [!INCLUDE[dublin](../../../includes/dublin-md.md)] Serwera aplikacji w szczególności zaprojektowano pod kątem wdrażania i zarządzania aplikacjami, które używają [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] komunikacji. [!INCLUDE[dublin2](../../../includes/dublin2-md.md)] Obejmuje zaawansowane opcje narzędzi i konfiguracji zaprojektowane specjalnie dla [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]-aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel>  
 [Podstawowe pojęcia programu Windows Communication Foundation](../../../docs/framework/wcf/fundamental-concepts.md)  
 [Architektura WCF (Windows Communication Foundation)](../../../docs/framework/wcf/architecture.md)  
 [Wskazówki i najlepsze rozwiązania](../../../docs/framework/wcf/guidelines-and-best-practices.md)  
 [Wprowadzenie — samouczek](../../../docs/framework/wcf/getting-started-tutorial.md)  
 [Przewodnik po dokumentacji](../../../docs/framework/wcf/guide-to-the-documentation.md)  
 [Podstawy programowania przy użyciu programu WCF](../../../docs/framework/wcf/basic-wcf-programming.md)  
 [Windows Communication Foundation — przykłady](http://msdn.microsoft.com/library/8ec9d192-5d81-4f64-bfd3-90c5e5858c91)
