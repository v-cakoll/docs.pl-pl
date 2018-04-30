---
title: Kontrakty
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
- WCF [WCF], contracts
- contracts [WCF]
- Windows Communication Foundation [WCF], contracts
ms.assetid: c8364183-4ac1-480b-804a-c5e6c59a5d7d
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: adfa43e411a3b4b71edcac8938851b3abfcda2f8
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="contracts"></a>Kontrakty
W tej sekcji przedstawiono sposób definiowania i wdrożenie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]umów. Kontrakt usługi określa punkt końcowy komunikuje się publicznie. Na poziomie bardziej konkretną jest oświadczenie o zestaw określonych komunikatów podzielone na wzorce wymiany wiadomości podstawowe (MEPs), takich jak żądanie/odpowiedź, jednokierunkowe i dupleksowych. Jeśli kontrakt usługi to zestaw logicznie powiązanych wymiany komunikatów, operacji usługi jest exchange pojedynczym komunikacie. Na przykład `Hello` operacji oczywiście zaakceptować jeden komunikat (aby wywołujący może poinformować o powitanie) i może lub nie może zwracać komunikat (w zależności od uprzejmości operacji).  
  
 Aby uzyskać więcej informacji na temat umów oraz innych podstawowych [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pojęć, zobacz [podstawowe pojęcia programu Windows Communication Foundation](../../../../docs/framework/wcf/fundamental-concepts.md). Ten temat koncentruje się na kontraktów usług. Aby uzyskać więcej informacji o sposobie budowania klientów, którzy używają kontraktów usług do nawiązania połączenia usługi, zobacz [Przegląd klienta programu WCF](../../../../docs/framework/wcf/wcf-client-overview.md). Aby uzyskać więcej informacji o kanały klienta, architektury klienta i inne problemy klienta, zobacz [klientów](../../../../docs/framework/wcf/feature-details/clients.md).  
  
## <a name="overview"></a>Omówienie  
 W tym temacie przedstawiono ogólny orientacji koncepcyjnej projektowanie i implementowanie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług. Tematy podrzędne zawierają bardziej szczegółowe informacje o szczegółowe informacje na temat projektowania i implementacji. Przed projektowanie i implementowanie Twojej [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji, zaleca się że:  
  
-   Zrozumienie kontraktu usługi, jak to działa i jak go utworzyć.  
  
-   Zrozumienie, że kontrakty stanu minimalnych wymagań tej konfiguracji środowiska wykonawczego lub środowisko macierzyste mogą nie obsługiwać.  
  
## <a name="service-contracts"></a>Kontrakty usług  
 Kontrakt usługi jest instrukcję, która zawiera informacje na temat:  
  
-   Grupowanie operacji w usłudze.  
  
-   Podpis operacje kategoriach wiadomości wymieniane.  
  
-   Typy danych tych wiadomości.  
  
-   Lokalizacja operacje.  
  
-   Określonych protokołów i formatów serializacji, które są używane do obsługi łączność z usługą.  
  
 Na przykład może być kontrakt zamówienia zakupu `CreateOrder` operacja, która akceptuje dane wejściowe informacji o zamówieniu typów i zwraca informacje o powodzeniu lub niepowodzeniu, tym identyfikator zamówienia. Może także mieć `GetOrderStatus` operacji, które akceptuje identyfikator kolejności i zwraca informacje o stanie zamówienia. Określ tego rodzaju kontraktu usługi:  
  
-   Czy kontrakt zamówienia zakupu obejmował `CreateOrder` i `GetOrderStatus` operacji.  
  
-   Określono operacje wejścia wiadomości i wyjścia wiadomości.  
  
-   Dane, które umożliwiają wykonanie tych wiadomości.  
  
-   Podzielone na kategorie instrukcje dotyczące infrastruktury komunikacji niezbędne do pomyślnie przetwarzania komunikatów. Informacje te zawierają na przykład czy i jakie rodzaje zabezpieczeń są wymagane do nawiązania komunikacji powiodło się.  
  
 W celu przekazania tego rodzaju informacje do aplikacji na innych platformach (takie jak platformy firmy Microsoft), kontraktów usług XML publicznie wyrażone są w standardowych formatów XML, takich jak [Web Services Description Language (WSDL)](http://go.microsoft.com/fwlink/?LinkId=87004) i [schematu XML (XSD)](http://go.microsoft.com/fwlink/?LinkId=87005), między innymi. Deweloperzy dla wielu platform mogą używać tych informacji publicznego kontraktu do tworzenia aplikacji, które mogą komunikować się z usługą, zarówno ponieważ zrozumieniu języka specyfikacji i pozwalają włączyć współdziałanie języków przez opisujące publicznego formularzy, formaty i protokołów obsługiwanych przez usługę. Aby uzyskać więcej informacji o tym, jak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dojść tego rodzaju informacje, zobacz [metadanych](../../../../docs/framework/wcf/feature-details/metadata.md).  
  
 Kontrakty można wyrazić wiele sposobów, jednak i podczas WSDL i XSD to doskonałe języki do opisywania usług w łatwy sposób, są trudne języki do użycia bezpośrednio — w każdym przypadku są jedynie opisy kontraktu usługi, nie usługi implementacje. W związku z tym [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacje używają klasy, interfejsy i atrybuty zarządzanych do definiowania struktury i zaimplementować usługi.  
  
 Wynikowa kontrakt zdefiniowany w typach zarządzanych można przekonwertować (nazywane również *wyeksportowane*) jak metadanych — WSDL i XSD — w razie potrzeby przez klientów lub inne implementacje usługi, zwłaszcza na innych platformach. Wynik jest model programowania prostego można przedstawić przy użyciu publicznego metadanych dla wszystkich aplikacji klienckich. Szczegółowe informacje o podstawowej wiadomości SOAP, takie jak transportu i informacji związanych z zabezpieczeniami, możesz je zostawić do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], który automatycznie wykonuje niezbędne konwersje do i z systemu typ kontraktu usługi w systemie typu XML.  
  
 Aby uzyskać więcej informacji na temat opracowywania umów, zobacz [projektowanie kontraktów usług](../../../../docs/framework/wcf/designing-service-contracts.md). Aby uzyskać więcej informacji na temat Implementowanie kontraktów, zobacz [Implementowanie kontraktów usług](../../../../docs/framework/wcf/implementing-service-contracts.md).  
  
 Ponadto [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oferuje możliwość tworzenia kontraktów usług wyłącznie na poziomie wiadomości. Aby uzyskać więcej informacji o tworzeniu kontraktów usług na poziomie komunikatu, zobacz [za pomocą kontraktów komunikatu](../../../../docs/framework/wcf/feature-details/using-message-contracts.md). Aby uzyskać więcej informacji na temat tworzenia usług w XML z systemem innym niż SOAP, zobacz [współdziałanie z aplikacjami POX](../../../../docs/framework/wcf/feature-details/interoperability-with-pox-applications.md).  
  
### <a name="understanding-the-hierarchy-of-requirements"></a>Opis hierarchii wymagania  
 Kontrakt usługi grup działań; Określa MEP, typy komunikatu i przenoszące tych wiadomości; typy danych wskazuje kategorie implementacja musi mieć do obsługi kontrakt zachowania w czasie wykonywania (na przykład może wymagać zaszyfrowana i podpisana wiadomości). Kontrakt usługi, jednak nie został określony dokładnie jak te warunki zostały spełnione, tylko że muszą być. Jakiego typu szyfrowania lub sposób wiadomość jest podpisany, zależy od implementacji i konfiguracji usługi zgodne.  
  
 Zwróć uwagę, czy kontrakt wymaga pewne zagadnienia implementacji kontraktu usługi i konfigurację środowiska wykonawczego, aby dodać zachowanie sposób. Zestaw wymagań, które muszą zostać spełnione do udostępnienia usługi do użycia opiera się na poprzedni zestaw wymagań. Jeśli kontrakt sprawia, że wymagania dotyczące wdrażania, implementacja może wymagać jeszcze więcej konfiguracji i powiązania, które Włącz usługę w celu uruchomienia. Ponadto aplikacja hosta muszą również obsługiwać wszelkie wymagania, które Dodaj konfigurację usługi i powiązania.  
  
 Ten proces dodawania wymaganie jest ważne, należy wziąć pod uwagę podczas projektowania, wdrażania, konfigurowanie i hostingu sieci [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikacji usługi. Na przykład kontrakt można określić, że musi obsługiwać sesji. Jeśli tak, musisz skonfigurować powiązania w celu spełnienia tego wymagania umownymi lub implementacji usługi nie będą działać. Lub jeśli usługa wymaga zintegrowanego uwierzytelniania systemu Windows i znajduje się w Internet Information Services (IIS), aplikacji sieci Web, w którym znajduje się usługa musi mieć włączone uwierzytelnianie zintegrowane systemu Windows i obsługa anonimowe wyłączone. Aby uzyskać więcej informacji o funkcjach i wpływ typów aplikacji hosta innej usługi, zobacz [hostingu](../../../../docs/framework/wcf/feature-details/hosting.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Punkty końcowe: adresy, powiązania i kontrakty](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
 [Projektowanie kontraktów usług](../../../../docs/framework/wcf/designing-service-contracts.md)  
 [Implementowanie kontraktów usług](../../../../docs/framework/wcf/implementing-service-contracts.md)
