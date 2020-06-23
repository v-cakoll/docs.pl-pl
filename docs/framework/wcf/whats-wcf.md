---
title: Co to jest program Windows Communication Foundation
description: Dowiedz się więcej na temat Windows Communication Foundation, który jest strukturą do tworzenia aplikacji zorientowanych na usługę.
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], technology overview
- technology overview [WCF]
- WCF [WCF], technology overview
ms.assetid: 40e1009d-ef15-450b-9848-62eabe5e5738
ms.openlocfilehash: 84cb45d62409769a79fa6a401fdb1aa6934c4099
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245612"
---
# <a name="what-is-windows-communication-foundation"></a>Co to jest program Windows Communication Foundation
Windows Communication Foundation (WCF) to platforma służąca do tworzenia aplikacji zorientowanych na usługę. Korzystając z programu WCF, można wysyłać dane jako komunikaty asynchroniczne z jednego punktu końcowego usługi do innego. Punkt końcowy usługi może być częścią stale dostępnej usługi hostowanej przez usługi IIS lub może być usługą hostowaną w aplikacji. Punktem końcowym może być klient usługi, która żąda danych z punktu końcowego usługi. Komunikaty mogą być proste jako pojedynczy znak lub słowo wysyłane jako XML lub jako strumień danych binarnych. Oto kilka przykładowych scenariuszy:

- Bezpieczna usługa do przetwarzania transakcji roboczych.

- Usługa dostarczająca bieżące dane do innych, takich jak raport o ruchu lub inna usługa monitorowania.

- Usługa czatu, która umożliwia dwóm osobom komunikowanie się lub wymianę danych w czasie rzeczywistym.

- Aplikacja pulpitu nawigacyjnego, która sonduje co najmniej jedną usługę danych i przedstawia ją w prezentacji logicznej.

- Uwidacznianie przepływu pracy zaimplementowanego przy użyciu Windows Workflow Foundation jako usługi WCF.

- Aplikacja Silverlight do sondowania usługi dla najnowszych strumieniowych źródeł danych.

Podczas tworzenia takich aplikacji było możliwe przed istnieniem programu WCF, funkcja WCF sprawia, że tworzenie punktów końcowych jest prostsze niż kiedykolwiek wcześniej. Podsumowując, funkcja WCF została zaprojektowana w celu zapewnienia możliwości zarządzania w celu tworzenia usług sieci Web i klientów usług sieci Web.

## <a name="features-of-wcf"></a>Funkcje programu WCF

Program WCF obejmuje następujący zestaw funkcji. Aby uzyskać więcej informacji, zobacz [Szczegóły funkcji usługi WCF](./feature-details/index.md).

- **Orientacja usługi**

     Jedną z postanowień dotyczących korzystania ze standardów WS jest możliwość tworzenia aplikacji *zorientowanych na usługi* . Architektura zorientowana na usługi (SOA) to zależność od usług sieci Web do wysyłania i odbierania danych. Usługi programu mają ogólne zalety, które nie są luźno powiązane, zamiast być kodowane z jednej aplikacji do innej. Relacja luźno sprzężona polega na tym, że każdy klient utworzony na dowolnej platformie może połączyć się z dowolną usługą, o ile są spełnione zasadnicze umowy.

- **Współdziałanie**

     Funkcja WCF implementuje nowoczesne standardy dla współdziałania usługi sieci Web. Aby uzyskać więcej informacji o obsługiwanych standardach, zobacz [współdziałanie i integracja](./feature-details/interoperability-and-integration.md).

- **Wzorzec wielu komunikatów**

     Komunikaty są wymieniane w jednym z kilku wzorców. Najbardziej typowym wzorcem jest wzorzec żądania/odpowiedzi, gdzie jeden punkt końcowy żąda danych z drugiego punktu końcowego. Odpowiedzi drugiego punktu końcowego. Istnieją inne wzorce, takie jak jednokierunkowa wiadomość, w której jeden punkt końcowy wysyła komunikat bez oczekiwania na odpowiedź. Bardziej skomplikowanym wzorcem jest wzorzec wymiany dwukierunkowej, w którym dwa punkty końcowe nawiązują połączenie i wysyłają dane ponownie, podobnie jak program obsługi wiadomości błyskawicznych. Aby uzyskać więcej informacji o implementowaniu różnych wzorców wymiany komunikatów przy użyciu usług WCF, zobacz [kontrakt](./feature-details/contracts.md).

- **Metadane usługi**

     Program WCF obsługuje Publikowanie metadanych usługi przy użyciu formatów określonych w standardach branżowych, takich jak WSDL, schemat XML i WS-Policy. Przy użyciu tych metadanych można automatycznie generować i konfigurować klientów na potrzeby uzyskiwania dostępu do usług WCF. Metadane można publikować za pośrednictwem protokołów HTTP i HTTPS albo przy użyciu standardu wymiany metadanych usługi sieci Web. Aby uzyskać więcej informacji, zobacz [metadane](./feature-details/metadata.md).

- **Kontrakty danych**

     Ponieważ platforma WCF została skompilowana przy użyciu .NET Framework, zawiera również przyjazne dla kodu metody dostarczania kontraktów, które mają zostać wymuszone. Jednym z uniwersalnych typów kontraktów jest kontrakt danych. W zasadzie, podczas pisania kodu usługi przy użyciu języka Visual C# lub Visual Basic, najprostszym sposobem obsługi danych jest utworzenie klas reprezentujących jednostkę danych z właściwościami należącymi do jednostki danych. Usługa WCF oferuje kompleksowy system do pracy z danymi w ten prosty sposób. Po utworzeniu klas, które reprezentują dane, usługa automatycznie generuje metadane, które umożliwiają klientom przestrzeganie typów danych, które zostały zaprojektowane. Aby uzyskać więcej informacji, zobacz [Korzystanie z kontraktów danych](feature-details/using-data-contracts.md).

- **Bezpieczeństwo**

     Komunikaty mogą być szyfrowane, aby chronić prywatność i można wymagać od użytkowników uwierzytelniania się przed zezwoleniem na odbieranie komunikatów. Zabezpieczenia można zaimplementować przy użyciu dobrze znanych standardów, takich jak SSL lub WS-SecureConversation. Aby uzyskać więcej informacji, zobacz [zabezpieczenia](./feature-details/security.md).

- **Wiele transportów i kodowań**

     Komunikaty mogą być wysyłane przy użyciu dowolnego z kilku wbudowanych protokołów i kodowań transportowych. Najbardziej typowym protokołem i kodowaniem jest wysyłanie komunikatów SOAP zakodowanych przy użyciu protokołu HTTP (HyperText Transfer Protocol) do użycia w World Wide Web. Alternatywnie Funkcja WCF umożliwia wysyłanie komunikatów za pośrednictwem protokołu TCP, nazwanych potoków lub usługi MSMQ. Te komunikaty mogą być kodowane jako tekst lub przy użyciu zoptymalizowanego formatu binarnego.  Dane binarne można wydajnie wysyłać przy użyciu standardu MTOM. Jeśli żadna z podanych transportów lub kodowań nie odpowiada Twoim potrzebom, możesz utworzyć własne, niestandardowe transport lub kodowanie. Aby uzyskać więcej informacji na temat transportów i kodowań obsługiwanych przez WCF, zobacz [Transports](./feature-details/transports.md).

- **Niezawodne i kolejkowane komunikaty**

     Program WCF obsługuje niezawodną wymianę komunikatów przy użyciu niezawodnych sesji implementowanych za pośrednictwem usługi WS-niezawodny i przy użyciu usługi MSMQ Aby uzyskać więcej informacji na temat obsługi komunikatów niezawodnych i w kolejce w ramach usługi WCF, zobacz [kolejki i sesje niezawodne](./feature-details/queues-and-reliable-sessions.md).

- **Komunikaty trwałe**

     Trwały komunikat to taki, który nigdy nie jest tracony ze względu na zakłócenia komunikacji. Komunikaty ze wzorca wiadomości w postaci trwałej są zawsze zapisywane w bazie danych. Jeśli wystąpi zakłócenie, baza danych umożliwia wznowienie wymiany komunikatów po przywróceniu połączenia. Możesz również utworzyć trwały komunikat przy użyciu Windows Workflow Foundation (WF). Aby uzyskać więcej informacji, zobacz [usługi Workflow Services](./feature-details/workflow-services.md).

- **Transakcje**

     WCF obsługuje również transakcje przy użyciu jednego z trzech modeli transakcji: WS-AtomicTransaction, interfejsów API w <xref:System.Transactions> przestrzeni nazw i Microsoft Distributed Transaction Coordinator. Aby uzyskać więcej informacji na temat obsługi transakcji w programie WCF, zobacz [transakcje](./feature-details/transactions-in-wcf.md).

- **Obsługa technologii AJAX i REST**

     REST to przykład rozwijającej się technologii sieci Web 2,0. Funkcję WCF można skonfigurować do przetwarzania "zwykłych" danych XML, które nie są opakowane w kopercie protokołu SOAP. Można również rozszerzyć obsługę określonych formatów XML, takich jak ATOM (popularny Standard RSS), a nawet formatów niexml, takich jak JavaScript Object Notation (JSON).

- **Rozszerzalność**

     Architektura WCF ma wiele punktów rozszerzalności. Jeśli wymagana jest dodatkowa możliwość, istnieje kilka punktów wejścia, które umożliwiają dostosowanie zachowania usługi. Aby uzyskać więcej informacji na temat dostępnych punktów rozszerzalności, zobacz [rozszerzanie WCF](./extending/index.md).

## <a name="wcf-integration-with-other-microsoft-technologies"></a>Integracja WCF z innymi technologiami firmy Microsoft

WCF jest elastyczną platformą. Ze względu na tę skrajną elastyczność program WCF jest również używany w kilku innych produktach firmy Microsoft. Zrozumienie podstaw programu WCF pozwala korzystać z natychmiastowej usługi, jeśli również używasz dowolnego z tych produktów.

Pierwszą technologią sparowaną z WCF była Windows Workflow Foundation (WF). Przepływy pracy upraszczają tworzenie aplikacji przez hermetyzację kroków w przepływie pracy jako "działania". W pierwszej wersji Windows Workflow Foundation deweloper musiał utworzyć hosta dla przepływu pracy. Następna wersja Windows Workflow Foundation została zintegrowana z programem WCF. To pozwoliło na łatwą obsługę każdego przepływu pracy w usłudze WCF. Można to zrobić przez automatyczne wybranie typu projektu WF/WCF w programie Visual Studio 2012 lub nowszym.

Program Microsoft BizTalk Server R2 korzysta również z funkcji WCF jako technologii komunikacji. Program BizTalk został zaprojektowany do odbierania i przekształcania danych z jednego standardowego formatu na inny. Komunikaty muszą być dostarczane do centralnego okna komunikatów, w którym można przekształcać komunikat przy użyciu ścisłego mapowania lub jednej z funkcji programu BizTalk, takich jak aparat przepływu pracy. Usługa BizTalk może teraz korzystać z karty biznesowej (LOB) usługi WCF w celu dostarczania komunikatów do okna komunikatu.

Microsoft Silverlight to platforma służąca do tworzenia międzyoperacyjnych, rozbudowanych aplikacji sieci Web, które umożliwiają deweloperom tworzenie witryn sieci Web intensywnie korzystających z multimediów (na przykład wideo przesyłania strumieniowego). Począwszy od wersji 2, program Silverlight ma wbudowaną funkcję WCF jako technologię komunikacji do łączenia aplikacji Silverlight z punktami końcowymi WCF.

Funkcje hostingu serwera aplikacji systemu Windows Server AppFabric są przeznaczone specjalnie do wdrażania aplikacji, które używają programu WCF do komunikacji i zarządzania nimi. Funkcje hostingu obejmują rozbudowane narzędzia i opcje konfiguracji zaprojektowane specjalnie dla aplikacji obsługujących WCF.

## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel>
- [Podstawowe pojęcia programu Windows Communication Foundation](fundamental-concepts.md)
- [Architektura WCF (Windows Communication Foundation)](architecture.md)
- [Wskazówki i najlepsze rozwiązania](guidelines-and-best-practices.md)
- [Wprowadzenie — samouczek](getting-started-tutorial.md)
- [Przewodnik po dokumentacji](guide-to-the-documentation.md)
- [Podstawy programowania przy użyciu programu WCF](basic-wcf-programming.md)
- [Windows Communication Foundation — przykłady](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751514%28v=vs.90%29)
