---
title: Kontrakty
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], contracts
- contracts [WCF]
- Windows Communication Foundation [WCF], contracts
ms.assetid: c8364183-4ac1-480b-804a-c5e6c59a5d7d
ms.openlocfilehash: 1cd7e54d50e7116c71c040df1965674a4fdaff13
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595599"
---
# <a name="contracts"></a>Kontrakty
W tej sekcji przedstawiono sposób definiowania i implementowania kontraktów Windows Communication Foundation (WCF). Kontrakt usługi określa, co punkt końcowy komunikuje się ze światem zewnętrznym. Na wyższym poziomie jest to zestawienie konkretnych komunikatów zorganizowanych w podstawowe wzorce wymiany komunikatów (MEPs), takie jak żądanie/odpowiedź, jednokierunkowe i dwustronne. Jeśli kontrakt usługi jest związany logicznie z wymianą komunikatów, operacja usługi jest pojedynczą wymianą komunikatów. Na przykład `Hello` operacja musi w dowolny sposób zaakceptować jeden komunikat (aby obiekt wywołujący mógł ogłosić powitanie) i może lub nie zwracać komunikatu (w zależności od tego, co jest wymagane).  
  
 Aby uzyskać więcej informacji na temat umów i innych podstawowych koncepcji programu WCF, zobacz [podstawowe pojęcia dotyczące Windows Communication Foundation](../fundamental-concepts.md). Ten temat koncentruje się na zrozumieniu umów dotyczących usług. Aby uzyskać więcej informacji na temat tworzenia klientów, którzy używają umów usługi do łączenia się z usługami, zobacz [Omówienie klienta programu WCF](../wcf-client-overview.md). Aby uzyskać więcej informacji na temat kanałów klienta, architektury klienta i innych problemów z klientami, zobacz [klienci](clients.md)programu.  
  
## <a name="overview"></a>Omówienie  
 Ten temat zawiera ogólne ukierunkowane na projektowanie i implementowanie usług WCF. Tematy podrzędne zawierają bardziej szczegółowe informacje dotyczące projektowania i implementacji. Przed zaprojektowaniem i wdrożeniem aplikacji WCF zaleca się:  
  
- Zapoznaj się z umową usługi, jej działaniem i sposobami ich tworzenia.  
  
- Informacje o minimalnych wymaganiach dotyczących konfiguracji w czasie wykonywania lub środowiska hostingu przez umowę.  
  
## <a name="service-contracts"></a>Kontrakty usług  
 Kontrakt usługi jest instrukcją, która zawiera informacje o:  
  
- Grupowanie operacji w usłudze.  
  
- Podpis operacji w odniesieniu do komunikatów wymienianych.  
  
- Typy danych tych komunikatów.  
  
- Lokalizacja operacji.  
  
- Określone protokoły i formaty serializacji, które są używane do obsługi pomyślnej komunikacji z usługą.  
  
 Na przykład kontrakt zamówienia zakupu może mieć `CreateOrder` operację, która akceptuje dane wejściowe typów informacji o zamówieniach i zwraca informacje o powodzeniu lub niepowodzeniu, w tym o identyfikatorze zamówienia. Może również mieć `GetOrderStatus` operację, która akceptuje identyfikator zamówienia i zwraca informacje o stanie zamówienia. W ramach tego sortowania kontrakt usługi będzie określać:  
  
- Umowa zamówienia zakupu obejmuje `CreateOrder` `GetOrderStatus` operacje i.  
  
- Że operacje zawierają określone komunikaty wejściowe i komunikaty wyjściowe.  
  
- Dane, które mogą być wykonywane przez te komunikaty.  
  
- Instrukcje kategorii dotyczące infrastruktury komunikacyjnej niezbędnej do pomyślnego przetworzenia komunikatów. Na przykład te szczegóły zawierają informacje o tym, czy i jakie formy zabezpieczeń są wymagane do pomyślnego nawiązania komunikacji.  
  
 Aby przekazać ten rodzaj informacji do aplikacji na innych platformach (w tym na platformach innych niż Microsoft), kontrakty usługi XML są publicznie wyrażane w standardowych formatach XML, takich jak [Web Services Description Language (WSDL)](https://www.w3.org/TR/2001/NOTE-wsdl-20010315) i [schemat XML (XSD)](https://www.w3.org/XML/Schema), między innymi. Deweloperzy dla wielu platform mogą używać tych informacji o publicznej umowie do tworzenia aplikacji, które mogą komunikować się z usługą, zarówno ponieważ rozumieją język specyfikacji, jak i ponieważ te języki zostały zaprojektowane w celu umożliwienia współdziałania przez opisywanie publicznych formularzy, formatów i protokołów obsługiwanych przez usługę. Aby uzyskać więcej informacji o tym, jak WCF obsługuje ten rodzaj informacji, zobacz [Metadata](metadata.md).  
  
 Kontrakty mogą być wyrażane na wiele sposobów, ale w przypadku języków WSDL i XSD, aby opisywać usługi w dostępnym sposób, są one trudne do użycia bezpośrednio — w każdym przypadku są to tylko opisy usługi, a nie implementacje kontraktu usługi. W związku z tym aplikacje WCF wykorzystują zarządzane atrybuty, interfejsy i klasy zarówno do definiowania struktury, jak i do implementowania usługi.  
  
 Kontrakt wynikający zdefiniowany w typach zarządzanych może być konwertowany (nazywany również *eksportowany*) jako metadane — WSDL i XSD — gdy jest to wymagane przez klientów lub innych realizatorów usług, zwłaszcza w przypadku innych platform. Jest to prosty model programowania, który można opisać przy użyciu publicznych metadanych do dowolnej aplikacji klienckiej. Szczegóły źródłowych komunikatów protokołu SOAP, takie jak informacje o transportach i zabezpieczeniach, mogą pozostać w programie WCF, które automatycznie wykonuje wymagane konwersje do i z systemu typu kontraktu usługi do systemu typu XML.  
  
 Aby uzyskać więcej informacji na temat projektowania kontraktów, zobacz [Projektowanie kontraktów usług](../designing-service-contracts.md). Aby uzyskać więcej informacji na temat implementowania kontraktów, zobacz [implementowanie kontraktów usług](../implementing-service-contracts.md).  
  
 Ponadto funkcja WCF oferuje również możliwość tworzenia umów dotyczących usług wyłącznie na poziomie wiadomości. Aby uzyskać więcej informacji na temat opracowywania kontraktów usług na poziomie wiadomości, zobacz [Używanie kontraktów komunikatów](using-message-contracts.md). Aby uzyskać więcej informacji na temat tworzenia usług w formacie innym niż SOAP, zobacz [współdziałanie z aplikacjami POX](interoperability-with-pox-applications.md).  
  
### <a name="understanding-the-hierarchy-of-requirements"></a>Informacje o hierarchii wymagań  
 Kontrakt usługi grupuje operacje; Określa unikatowy MEP, typy komunikatów i typy danych, które są wykonywane przez te wiadomości; i wskazuje kategorie zachowania w czasie wykonywania, które musi mieć implementacja do obsługi kontraktu (na przykład może wymagać zaszyfrowania i podpisania wiadomości). Jednak sama umowa serwisowa nie określa dokładnej, jak te wymagania są spełnione, tylko muszą być. Jakiego typu szyfrowanie lub w jaki sposób komunikat jest podpisywany, do implementacji i konfiguracji zgodnej usługi.  
  
 Zwróć uwagę na sposób, w jaki kontrakt wymaga pewnego działania implementacji kontraktu usługi i konfiguracji czasu wykonywania, aby dodać zachowanie. Zestaw wymagań, które muszą zostać spełnione, aby uwidocznić usługę do użycia w ramach wcześniejszego zestawu wymagań. Jeśli kontrakt spełnia wymagania implementacji, implementacja może wymagać jeszcze większej liczby konfiguracji i powiązań, które umożliwiają uruchomienie usługi. Na koniec aplikacja hosta musi również obsługiwać wszelkie wymagania, które dodaje konfiguracja usługi i powiązania.  
  
 Ten proces wymagania dodatku jest istotny, gdy projektowanie, wdrażanie, Konfigurowanie i hostowanie aplikacji usługi Windows Communication Foundation (WCF). Na przykład kontrakt może określać, że musi obsługiwać sesję. W takim przypadku należy skonfigurować powiązanie do obsługi tego wymagania umownego lub implementacja usługi nie będzie działała. Lub jeśli usługa wymaga zintegrowanego uwierzytelniania systemu Windows i jest hostowana w usłudze Internet Information Services (IIS), aplikacja sieci Web, w której znajduje się usługa, musi mieć włączone zintegrowane uwierzytelnianie systemu Windows, a obsługa anonimowa jest wyłączona. Aby uzyskać więcej informacji na temat funkcji i wpływu różnych typów aplikacji hosta usługi, zobacz [hosting](hosting.md).  
  
## <a name="see-also"></a>Zobacz też

- [Punkty końcowe: Adresy, powiązania i kontrakty](endpoints-addresses-bindings-and-contracts.md)
- [Projektowanie kontraktów usług](../designing-service-contracts.md)
- [Implementowanie kontraktów usług](../implementing-service-contracts.md)
