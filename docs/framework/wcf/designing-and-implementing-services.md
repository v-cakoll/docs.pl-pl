---
title: Projektowanie i implementowanie usług
ms.date: 03/30/2017
helpviewer_keywords:
- defining service contracts [WCF]
ms.assetid: 036fae20-7c55-4002-b71d-ac4466e167a3
ms.openlocfilehash: 0d569d12b5bc555a07e94fa89c5a19f52f4a6b6c
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318402"
---
# <a name="designing-and-implementing-services"></a>Projektowanie i implementowanie usług
W tej sekcji pokazano, jak definiować i implementować kontrakty WCF. Kontrakt usługi określa, co punkt końcowy komunikuje się ze światem zewnętrznym. Na wyższym poziomie jest to zestawienie konkretnych komunikatów zorganizowanych w podstawowe wzorce wymiany komunikatów (MEPs), takie jak żądanie/odpowiedź, jednokierunkowe i dwustronne. Jeśli kontrakt usługi jest związany logicznie z wymianą komunikatów, operacja usługi jest pojedynczą wymianą komunikatów. Na przykład operacja `Hello` musi w oczywisty sposób zaakceptować jeden komunikat (aby obiekt wywołujący mógł ogłosić powitanie) i może lub nie zwracać komunikatu (w zależności od tego, co jest wymagane).  
  
 Aby uzyskać więcej informacji na temat umów i innych podstawowych koncepcji Windows Communication Foundation (WCF), zobacz [podstawowe pojęcia dotyczące Windows Communication Foundation](fundamental-concepts.md). Ten temat koncentruje się na zrozumieniu umów dotyczących usług. Aby uzyskać więcej informacji na temat tworzenia klientów, którzy używają umów usługi do łączenia się z usługami, zobacz [Omówienie klienta programu WCF](wcf-client-overview.md).  
  
## <a name="overview"></a>Omówienie  
 Ten temat zawiera ogólne ukierunkowane na projektowanie i implementowanie usług WCF. Tematy podrzędne zawierają bardziej szczegółowe informacje na temat specyfiki projektu i implementacji. Przed zaprojektowaniem i wdrożeniem aplikacji WCF zaleca się:  
  
- Zapoznaj się z umową usługi, jej działaniem i sposobami ich tworzenia.  
  
- Zapoznaj się z minimalnymi wymaganiami w zakresie umów, które mogą być obsługiwane przez konfigurację środowiska uruchomieniowego lub środowisko hostingu.  
  
## <a name="service-contracts"></a>Kontrakty usług  
 Kontrakt usługi określa następujące elementy:  
  
- Operacje ujawniane przez umowę.  
  
- Podpis operacji w odniesieniu do komunikatów wymienianych.  
  
- Typy danych tych komunikatów.  
  
- Lokalizacja operacji.  
  
- Określone protokoły i formaty serializacji, które są używane do obsługi pomyślnej komunikacji z usługą.  
  
 Na przykład kontrakt zamówienia zakupu może mieć operację `CreateOrder`, która akceptuje dane wejściowe typów informacji o zamówieniach i zwraca informacje o powodzeniu lub niepowodzeniu, w tym o identyfikatorze zamówienia. Może również mieć `GetOrderStatus` operacji, która akceptuje identyfikator zamówienia i zwraca informacje o stanie zamówienia. W ramach tego sortowania kontrakt usługi będzie określać:  
  
1. Umowa zamówienia zakupu obejmuje operacje `CreateOrder` i `GetOrderStatus`.  
  
2. Że operacje zawierają określone komunikaty wejściowe i komunikaty wyjściowe.  
  
3. Dane, które mogą być wykonywane przez te komunikaty.  
  
4. Instrukcje kategorii dotyczące infrastruktury komunikacyjnej niezbędnej do pomyślnego przetworzenia komunikatów. Na przykład te szczegóły zawierają informacje o tym, czy i jakie formy zabezpieczeń są wymagane do pomyślnego nawiązania komunikacji.  
  
 Aby przekazać ten rodzaj informacji do innych aplikacji na wielu platformach (w tym na platformach innych niż Microsoft), kontrakty usługi XML są publicznie wyrażane w standardowych formatach XML, takich jak [Web Services Description Language](https://go.microsoft.com/fwlink/?LinkId=94952) (WSDL) i [schemat XML ](https://go.microsoft.com/fwlink/?LinkId=94953)(XSD), między innymi. Deweloperzy dla wielu platform mogą używać tych informacji o publicznej umowie do tworzenia aplikacji, które mogą komunikować się z usługą, zarówno ponieważ rozumieją język specyfikacji, jak i ponieważ te języki zostały zaprojektowane w celu włączenia współdziałania przez opisywanie publicznych formularzy, formatów i protokołów obsługiwanych przez usługę. Aby uzyskać więcej informacji o tym, jak WCF obsługuje ten rodzaj informacji, zobacz [Metadata](./feature-details/metadata.md).  
  
 Kontrakty mogą być wyrażane na wiele sposobów, a w przypadku, gdy język WSDL i XSD to doskonałe Języki opisujące usługi w dostępnym sposób, są trudne do użycia bezpośrednio i są tylko opisami usługi, a nie implementacją kontraktu usług. W związku z tym aplikacje WCF używają zarówno atrybutów zarządzanych, interfejsów i klas, aby definiować strukturę usługi i wdrażać ją.  
  
 Kontrakt wynikający zdefiniowany w typach zarządzanych można *eksportować* jako metadane — WSDL i XSD — w razie konieczności przez klientów lub innych realizatorów usług. Wynikiem jest prosty model programowania, który można opisać (przy użyciu publicznych metadanych) do dowolnej aplikacji klienckiej. Szczegóły źródłowych komunikatów protokołu SOAP, informacje o transporcie i zabezpieczeniach itd. mogą pozostać w programie WCF, które przeprowadzają automatyczne konwersje do i z systemu typu kontraktu usługi do systemu typu XML.  
  
 Aby uzyskać więcej informacji na temat projektowania kontraktów, zobacz [Projektowanie kontraktów usług](designing-service-contracts.md). Aby uzyskać więcej informacji na temat implementowania kontraktów, zobacz [implementowanie kontraktów usług](implementing-service-contracts.md).  
  
### <a name="messages-up-front-and-center"></a>Komunikaty w przód i w środku  
 Używanie zarządzanych interfejsów, klas i metod do modelowania operacji usługi jest proste, gdy używane do zdalnego wywołania procedury (RPC) — sygnatury metod w stylu, w którym przekazywanie parametrów do metody i otrzymywanie zwracanych wartości jest normalną formą żądanie funkcjonalności z obiektu lub innego typu kodu. Na przykład programiści korzystający z języków zarządzanych, takich jak C++ Visual Basic i com, mogą stosować swoją wiedzę o podejściu do stylu wywołania RPC (niezależnie od tego, czy używają obiektów lub interfejsów) do tworzenia kontraktów usługi WCF bez występowania problemów związanych z w systemach obiektów rozproszonych w stylu RPC. Orientacja usługi oferuje korzyści płynące z luźno powiązanego programowania zorientowanego na komunikaty, zachowując prostotę i znajomość środowiska programowania RPC.  
  
 Wielu programistów jest bardziej wygodnym sposobem używania interfejsów programowania aplikacji zorientowanych na komunikaty, takich jak kolejki komunikatów, takie jak Microsoft MSMQ, przestrzenie nazw <xref:System.Messaging> w .NET Framework, lub wysyłanie danych XML bez struktury w żądaniach HTTP, aby nazwać kilka. Aby uzyskać więcej informacji na temat programowania na poziomie wiadomości, zobacz [Korzystanie z kontraktów komunikatów](./feature-details/using-message-contracts.md), [Programowanie na poziomie kanału usługi](./extending/service-channel-level-programming.md)i [współdziałanie z aplikacjami POX](./feature-details/interoperability-with-pox-applications.md).  
  
### <a name="understanding-the-hierarchy-of-requirements"></a>Informacje o hierarchii wymagań  
 Kontrakt usługi grupuje operacje; określa wzorzec wymiany komunikatów, typy komunikatów i typy danych, które są wykonywane przez te wiadomości; i wskazuje kategorie zachowania w czasie wykonywania, które musi mieć implementacja do obsługi kontraktu (na przykład może wymagać zaszyfrowania i podpisania wiadomości). Sama umowa serwisowa nie określa dokładnie tego, jak te wymagania są spełnione, tylko muszą być. Typ szyfrowania lub sposób, w jaki komunikat jest podpisywany, jest zgodny z implementacją i konfiguracją zgodnej usługi.  
  
 Zwróć uwagę na sposób, w jaki kontrakt wymaga pewnego działania implementacji kontraktu usługi i konfiguracji czasu wykonywania, aby dodać zachowanie. Zestaw wymagań, które muszą zostać spełnione, aby uwidocznić usługę do użycia w ramach wcześniejszego zestawu wymagań. Jeśli kontrakt spełnia wymagania implementacji, implementacja może wymagać jeszcze większej liczby konfiguracji i powiązań, które umożliwiają uruchomienie usługi. Na koniec aplikacja hosta musi również obsługiwać wszelkie wymagania, które dodaje konfiguracja usługi i powiązania.  
  
 Ten proces wymagania dodatku jest istotny, aby mieć świadomość podczas projektowania, implementowania, konfigurowania i hostowania aplikacji usługi Windows Communication Foundation (WCF). Na przykład kontrakt może określać, że musi obsługiwać sesję. W takim przypadku należy skonfigurować powiązanie do obsługi tego wymagania umownego lub implementacja usługi nie będzie działała. Lub jeśli usługa wymaga zintegrowanego uwierzytelniania systemu Windows i jest hostowana w usłudze Internet Information Services (IIS), aplikacja sieci Web, w której znajduje się usługa, musi mieć włączone zintegrowane uwierzytelnianie systemu Windows, a obsługa anonimowa jest wyłączona. Aby uzyskać więcej informacji na temat funkcji i wpływu różnych typów aplikacji hosta usługi, zobacz [usługi hostingu](hosting-services.md).  
  
## <a name="see-also"></a>Zobacz także

- [Projektowanie kontraktów usług](designing-service-contracts.md)
- [Implementowanie kontraktów usług](implementing-service-contracts.md)
