---
title: Co to jest program Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], technology overview
- technology overview [WCF]
- WCF [WCF], technology overview
ms.assetid: 40e1009d-ef15-450b-9848-62eabe5e5738
ms.openlocfilehash: f202d922b441d86838dd41992104ceecfc9bbabf
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45747338"
---
# <a name="what-is-windows-communication-foundation"></a>Co to jest program Windows Communication Foundation

Windows Communication Foundation (WCF) to architektura służąca do budowania aplikacji usługowych. Przy użyciu usługi WCF, możesz wysłać danych jako asynchroniczną komunikaty z punktu końcowego z jednej usługi do innego. Punkt końcowy usługi może być częścią stale dostępnych usług hostowanych przez usługi IIS lub może być usługą hostowaną w aplikacji. Punkt końcowy może być klientem usługi, która żąda danych z punktu końcowego usługi. Komunikaty można tak proste, jak pojedynczy znak lub słowo wysłana w formacie XML, lub tak złożonego jako strumień danych binarnych. Kilka przykładowe scenariusze obejmują:

-   Usługa bezpiecznego przetwarzania transakcji biznesowych.

-   Usługa, która dostarcza bieżące dane dla innych osób, takich jak raport ruchu lub inną usługą monitorowania.

-   Usługi rozmowy, który umożliwia użytkownikom dwóch komunikacji lub wymiany danych w czasie rzeczywistym.

-   Aplikacja pulpit nawigacyjny, który odpytuje co najmniej jeden usług danych i prezentuje je w prezentacji logiczne.

-   Udostępnianie przepływu pracy implementowana przy użyciu programu Windows Workflow Foundation jako usługa WCF.

-   Źródła danych aplikacji Silverlight, aby sondować usługę najnowsze dane.

Podczas tworzenia takich aplikacji jest możliwe przed istnienie WCF, WCF ułatwia projektowanie punktów końcowych łatwiejsze niż kiedykolwiek wcześniej. Podsumowując WCF jest przeznaczony do oferuje proste w zarządzaniu podejście do tworzenia usług sieci Web i klientów usługi sieci Web.

## <a name="features-of-wcf"></a>Funkcje programu WCF

Usługi WCF zawiera następujący zestaw funkcji. Aby uzyskać więcej informacji, zobacz [Szczegóły funkcji WCF](../../../docs/framework/wcf/feature-details/index.md).

-   **Orientacji usługi**

     W wyniku wprowadzenia przy użyciu standardów WS jest, że WCF pozwala na tworzenie *zorientowanej na usługi* aplikacji. Dotycząca architektury zorientowanej na usługi (SOA) jest zależność od usługi sieci Web do wysyłania i odbierania danych. Usługi muszą ogólne zaletą jest luźno powiązanych zamiast zakodowanych z jednej aplikacji na inny. Relację luźno powiązane oznacza dowolnego klienta, utworzony na dowolnej platformie można nawiązywać połączenie do dowolnej usługi tak długo, jak kontrakty niezbędne są spełnione.

-   **Współdziałanie**

     Usługi WCF implementuje nowoczesnych standardów współdziałania w ramach usługi sieci Web. Aby uzyskać więcej informacji na temat obsługiwanych standardów zobacz [współdziałanie i integracja](../../../docs/framework/wcf/feature-details/interoperability-and-integration.md).

-   **Wielu wzorców wiadomości**

     Komunikaty są wymieniane w jednym z kilku wzorców. Najczęstszym wzorcem jest wzorzec żądanie/nietypizowana odpowiedź, w której jeden punkt końcowy żąda danych od drugiego punktu końcowego. Drugi odpowiedzi punktu końcowego. Istnieją inne wzorców, takich jak komunikat jednokierunkowy, w którym jeden punkt końcowy jest wysyłany komunikat bez żadnych oczekiwania na odpowiedź. Bardziej złożonym wzorcem jest dupleksowy wymiany gdzie dwa punkty końcowe nawiązania połączenia i wysyłanie danych i z powrotem, podobne do programu obsługi wiadomości błyskawicznych. Aby uzyskać więcej informacji o sposobie wdrażania programu exchange w inny komunikat Zobacz wzorce przy użyciu usługi WCF [umów](../../../docs/framework/wcf/feature-details/contracts.md).

-   **Metadane usługi**

     Usługi WCF obsługuje Publikowanie metadanych usługi przy użyciu formatów określone w standardy branżowe, takie jak WSDL, schemat XML i WS-Policy. Te metadane może służyć do automatycznego generowania i skonfiguruj klientów do uzyskiwania dostępu do usług WCF. Metadane mogą być publikowane za pośrednictwem protokołów HTTP i HTTPS lub przy użyciu standardu wymiany metadanych usługi sieci Web. Aby uzyskać więcej informacji, zobacz [metadanych](../../../docs/framework/wcf/feature-details/metadata.md).

-   **Kontrakty danych**

     Ponieważ WCF został skompilowany przy użyciu [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], obejmuje także przyjaznego dla kodu metody podawania kontrakty, które chcesz zastosować. Jeden z typów universal zamówień jest kontraktu danych. W zasadzie zgodnie z kodem usługi za pomocą programu Visual C# lub Visual Basic, najprostszym sposobem obsługi danych jest utworzenie klas, które reprezentują jednostki danych z właściwościami, które należą do jednostki danych. Usługi WCF zawiera kompleksowe system do pracy z danymi w ten sposób łatwe. Po utworzeniu klasy reprezentujące danych usługa automatycznie generuje metadanych, które umożliwia klientom są zgodne z typami danych, które zostały tak zaprojektowane. Aby uzyskać więcej informacji, zobacz [za pomocą kontraktów danych](../../../docs/framework/wcf/feature-details/using-data-contracts.md)

-   **Zabezpieczenia**

     Komunikaty mogą być szyfrowane w celu ochrony prywatności i można wymagać od użytkowników uwierzytelniania się przed uzyskaniem dostępu do odbierania komunikatów. Za pomocą dobrze znanych standardów, takich jak protokół SSL lub WS-SecureConversation można zaimplementować zabezpieczenia. Aby uzyskać więcej informacji, zobacz [zabezpieczeń](../../../docs/framework/wcf/feature-details/security.md).

-   **Wiele transport i kodowanie**

     Komunikaty mogą być wysyłane na dowolnym z kilku wbudowanych protokołów i kodowania. Najbardziej typowe protokołami i kodowaniem jest wysłanie ich tekst zakodowany komunikaty protokołu SOAP, przy użyciu protokołu HTTP (HyperText Transfer) do użytku w sieci World Wide Web. Alternatywnie WCF umożliwia wysyłanie komunikatów za pośrednictwem protokołu TCP, o nazwie potoków lub usługi MSMQ. Te komunikaty mogą być zakodowane jako tekst lub przy użyciu zoptymalizowanego format binarny.  Dane binarne mogą być wysyłane efektywnie są używane standardowe MTOM. Podana transportów ani kodowania własnych potrzeb można utworzyć własną niestandardową transportu lub kodowania. Aby uzyskać więcej informacji na temat transport i kodowanie obsługiwane przez architekturę WCF zobacz [transportów](../../../docs/framework/wcf/feature-details/transports.md).

-   **Niezawodne i umieszczonych w kolejce wiadomości**

     Usługi WCF obsługuje exchange niezawodnych komunikatów za pomocą niezawodnej sesji implementowane za pośrednictwem usługi WS-Reliable Messaging i przy użyciu usługi MSMQ. Aby uzyskać więcej informacji o niezawodnych i umieszczonych w kolejce obsługi komunikatów w architekturze WCF zobacz [kolejki i sesje niezawodne](../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md).

-   **Trwałe wiadomości**

     Trwały komunikat jest taki, który nigdy nie jest utracone z powodu przerw w działaniu w komunikacie. Wiadomości we wzorcu komunikatów trwałe są zawsze zapisywane do bazy danych. W przypadku przerwy w działaniu bazy danych umożliwia wznowienie wymianę komunikatów, po przywróceniu połączenia. Można również utworzyć trwały komunikat przy użyciu Windows Workflow Foundation (WF). Aby uzyskać więcej informacji, zobacz [usług przepływu pracy](../../../docs/framework/wcf/feature-details/workflow-services.md).

-   **Transakcje**

     Usługi WCF obsługuje również transakcji przy użyciu jednej z trzech modele transakcji: WS AtomicTtransactions, interfejsów API w <xref:System.Transactions> przestrzeni nazw i Microsoft Distributed Transaction Coordinator. Aby uzyskać więcej informacji o transakcji zobacz temat pomocy technicznej w programie WCF [transakcji](../../../docs/framework/wcf/feature-details/transactions-in-wcf.md).

-   **AJAX i pomoc techniczna REST**

     POZOSTAŁE elementy są przykładem rozwijające się technologie sieci Web 2.0. Usługi WCF można skonfigurować do przetwarzania danych XML "zwykły" nie jest ujęty w kopercie SOAP. Można również rozszerzać WCF do obsługi określonych formatów XML, takie jak ATOM popularnych RSS (standardowa), a nawet XML inny niż formatów, takich jak JavaScript Object Notation (JSON).

-   **Rozszerzalność**

     Architektura WCF numerem punkty rozszerzeń. Jeśli wymagane jest dodatkowe możliwości, istnieje wiele punktów wejścia, które umożliwiają dostosowanie zachowania usługi. Aby uzyskać więcej informacji na temat rozszerzania dostępne punkty zobacz [rozszerzenia WCF](../../../docs/framework/wcf/extending/index.md).

## <a name="wcf-integration-with-other-microsoft-technologies"></a>Integracja usług WCF za pomocą innych technologii firmy Microsoft

Usługi WCF jest elastyczna platforma. Z powodu tej elastyczności skrajne WCF jest również używany w kilku innych produktów firmy Microsoft. Poznawszy podstawy usługi WCF, masz natychmiastowe korzyści, gdy również użyć dowolnego z tych produktów.

Pierwszy technologii parowanie WCF jest Windows Workflow Foundation (WF). Przepływy pracy uprościć tworzenie aplikacji dzięki hermetyzowany kroki w przepływie pracy jako "działania". W pierwszej wersji programu Windows Workflow Foundation Deweloper było utworzenie hosta przepływu pracy. Następna wersja programu Windows Workflow Foundation została zintegrowana z usługą WCF. Każdy przepływ pracy łatwo znajdować się w usłudze WCF, dozwolone. Można to zrobić, wybierając automatycznie WF/WCF typ projektu w programie Visual Studio 2012 lub nowszym.

Program Microsoft BizTalk Server R2 również korzysta z usługi WCF jako technologia komunikacji. BizTalk zaprojektowano w celu odbierania i przekształcać dane z jednego standardowego formatu do innego. Wiadomości musi być dostarczana do jej centralnej komunikat w przypadku, gdy komunikat mogą zostać przekształcone przy użyciu strict mapowania lub przy użyciu jednej z funkcje BizTalk, takie jak jego aparatu przepływu pracy. BizTalk mogą teraz używać karty WCF Line of Business (LOB), dostarczania wiadomości do okna komunikatu.

Program Microsoft Silverlight to platforma do tworzenia międzyoperacyjnych, rozbudowanych aplikacji sieci Web, które umożliwiają deweloperom tworzenie witryn sieci Web intensywnie korzystających z multimediów (np. przesyłania strumieniowego wideo). Począwszy od wersji 2, Silverlight, ma włączone WCF jako technologia komunikacji do łączenia aplikacji Silverlight z punktami końcowymi programu WCF.

[!INCLUDE[dublin](../../../includes/dublin-md.md)] Serwera aplikacji specjalnie zaprojektowano pod kątem wdrażania i zarządzania aplikacji, które używają usługi WCF do komunikacji. [!INCLUDE[dublin2](../../../includes/dublin2-md.md)] Zawiera zaawansowane narzędzia i opcje konfiguracji zaprojektowane specjalnie dla aplikacji obsługujących usługi WCF.

## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel>
- [Podstawowe pojęcia programu Windows Communication Foundation](../../../docs/framework/wcf/fundamental-concepts.md)
- [Architektura WCF (Windows Communication Foundation)](../../../docs/framework/wcf/architecture.md)
- [Wskazówki i najlepsze rozwiązania](../../../docs/framework/wcf/guidelines-and-best-practices.md)
- [Wprowadzenie — samouczek](../../../docs/framework/wcf/getting-started-tutorial.md)
- [Przewodnik po dokumentacji](../../../docs/framework/wcf/guide-to-the-documentation.md)
- [Podstawy programowania przy użyciu programu WCF](../../../docs/framework/wcf/basic-wcf-programming.md)
- [Windows Communication Foundation — przykłady](http://msdn.microsoft.com/library/8ec9d192-5d81-4f64-bfd3-90c5e5858c91)
