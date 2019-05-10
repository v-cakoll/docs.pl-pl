---
title: Kontrakty
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], contracts
- contracts [WCF]
- Windows Communication Foundation [WCF], contracts
ms.assetid: c8364183-4ac1-480b-804a-c5e6c59a5d7d
ms.openlocfilehash: 839f7790a5dd300313931672c60e7826af39aeea
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651102"
---
# <a name="contracts"></a>Kontrakty
W tej sekcji dowiesz się, jak zdefiniować i implementowanie kontraktów usług Windows Communication Foundation (WCF). Kontrakt usługi określa punkt końcowy komunikuje na zewnątrz. Na poziomie bardziej konkretne takie jak żądanie/nietypizowana odpowiedź, jednokierunkowe i dwukierunkowego jest poufności informacji na temat zestawu specyficzne komunikaty dotyczące podzielone na podstawowe wiadomości programu exchange wzorców (MEPs). Kontrakt usługi to zestaw logicznie powiązanych wymianę komunikatów, operacja usługi czy exchange pojedynczym komunikacie. Na przykład `Hello` operacji oczywiście akceptują jeden komunikat (tak, aby obiekt wywołujący może poinformować o powitania) i może być lub może nie zwrócić komunikat (w zależności od grzecznościowy operacji).  
  
 Aby uzyskać więcej informacji na temat umów i inne podstawowe pojęcia programu WCF, zobacz [podstawowe pojęcia programu Windows Communication Foundation](../../../../docs/framework/wcf/fundamental-concepts.md). Ten temat koncentruje się na wyjaśnieniu kontraktów usług. Aby uzyskać więcej informacji na temat sposobu tworzenia klientów, którzy używają kontraktów usług, aby połączyć się z usługami, zobacz [Przegląd klienta programu WCF](../../../../docs/framework/wcf/wcf-client-overview.md). Aby uzyskać więcej informacji na temat kanały klientów, architektury klienta i inne problemy z klientem, zobacz [klientów](../../../../docs/framework/wcf/feature-details/clients.md).  
  
## <a name="overview"></a>Omówienie  
 Ten temat zawiera ogólne koncepcyjne orientacji w pakiecie projektowanie i Implementowanie usług WCF. Tematy podrzędne zawierają bardziej szczegółowe informacje na temat szczegółowe informacje na temat projektowania i implementacji. Przed projektowanie i wdrażanie aplikacji WCF, zaleca się że:  
  
- Zrozumieć, jakie kontraktu usługi, jak to działa i jak ją utworzyć.  
  
- Zrozumienie, że kontraktów stanu minimalne wymagania mogą nie obsługiwać takiej konfiguracji czasu wykonywania lub środowisko hostingu.  
  
## <a name="service-contracts"></a>Kontrakty usług  
 Kontrakt usługi jest instrukcję, która zawiera informacje na temat:  
  
- Grupowanie operacji w usłudze.  
  
- Podpis operacje pod kątem komunikatów wymienianych.  
  
- Typy danych tych komunikatów.  
  
- Lokalizacja operacji.  
  
- Określonych protokołów i formatów serializacji, które są używane do obsługi pomyślnej komunikacji z usługą.  
  
 Na przykład może być kontrakt zamówienia zakupu `CreateOrder` operacji, który akceptuje dane wejściowe informacji o zamówieniach typów i zwraca informacje o powodzeniu lub niepowodzeniu, tym identyfikator zamówienia. Może także mieć `GetOrderStatus` operacji, która akceptuje identyfikator zamówienia i zwraca informacje o stanie zamówienia. Określ tego rodzaju kontraktu usługi:  
  
- Kontrakt zamówienia zakupu składa się z `CreateOrder` i `GetOrderStatus` operacji.  
  
- Czy operacje mają określone komunikaty wejściowe i wyjściowe komunikaty.  
  
- Dane, które może wykonywać te komunikaty.  
  
- Podzielone na kategorie instrukcji dotyczących infrastruktury komunikacji konieczne pomyślnie przetwarzania komunikatów. Na przykład, obejmują one czy i jakie rodzaje zabezpieczeń są wymagane do nawiązania komunikacji pomyślnie.  
  
 W celu przekazania tego rodzaju informacje do aplikacji na innych platformach (w tym platformy firmy Microsoft), kontraktów usług XML są publicznie wyrażone w standardowych formatów XML, takie jak [Web Services Description Language (WSDL)](https://go.microsoft.com/fwlink/?LinkId=87004) i [schematu XML (XSD)](https://go.microsoft.com/fwlink/?LinkId=87005), między innymi. Deweloperów na wielu platformach, można użyć tych informacji zamówienia publicznego do tworzenia aplikacji, które mogą się komunikować z usługą, zarówno ponieważ rozumieją języka specyfikacji, a te języki są ustalono, aby umożliwić współdziałanie poprzez opisanie publicznych formularzy, formatów i protokołów obsługiwanych przez usługę. Aby uzyskać więcej informacji na temat usługi WCF obsługi tego rodzaju informacje, zobacz [metadanych](../../../../docs/framework/wcf/feature-details/metadata.md).  
  
 Kontrakty mogą być wyrażone wiele sposobów, jednak i WSDL i XSD są doskonałe języków do opisu usługi w łatwy sposób, są one języków trudne do użycia bezpośrednio — w każdym przypadku są one jedynie opisy kontraktu usługi, nie usługi implementacje. Dlatego aplikacji WCF użycie klasy, interfejsy i atrybuty zarządzanych zarówno w celu zdefiniowania struktury, jak i implementację usługi.  
  
 Wynikowy kontrakt zdefiniowany w typami zarządzanymi mogą być konwertowane (nazywane również *wyeksportowane*) jako metadane — WSDL i XSD — w razie przez klientów lub inne implementacje usługi, zwłaszcza na innych platformach. Wynik jest prosty model programowania, który można opisać za pomocą publicznego metadane, aby każda aplikacja kliencka. Szczegółowe informacje o podstawowych komunikaty protokołu SOAP, takie jak transportu i informacje dotyczące zabezpieczeń, można pozostawić WCF, który automatycznie wykonuje konwersje niezbędne do i z systemu typu kontraktu usługi do systemu typów XML.  
  
 Aby uzyskać więcej informacji na temat Projektowanie kontraktów zobacz [projektowanie kontraktów usług](../../../../docs/framework/wcf/designing-service-contracts.md). Aby uzyskać więcej informacji na temat Implementowanie kontraktów zobacz [Implementowanie kontraktów usług](../../../../docs/framework/wcf/implementing-service-contracts.md).  
  
 Ponadto WCF zapewnia również możliwość opracowywania kontraktów usług całkowicie na poziomie komunikatu. Aby uzyskać więcej informacji o tworzeniu kontraktów usług na poziomie komunikatu, zobacz [za pomocą kontraktów komunikatu](../../../../docs/framework/wcf/feature-details/using-message-contracts.md). Aby uzyskać więcej informacji na temat tworzenia usług w XML bez protokołu SOAP, zobacz [współdziałanie z aplikacjami POX](../../../../docs/framework/wcf/feature-details/interoperability-with-pox-applications.md).  
  
### <a name="understanding-the-hierarchy-of-requirements"></a>Informacje o hierarchii wymagania  
 Kontrakt usługi grupy operacji; Określa MEP, typy komunikatów i przeniesienia tych wiadomości; typy danych Wskazuje kategorii do umowy dotyczącej pomocy technicznej jest posiadanie implementacji zachowania w czasie wykonywania (na przykład może wymagać zaszyfrowana i podpisana wiadomości). Kontrakt usługi, jednak nie określić dokładne jak te wymagania, tylko, muszą one być. Jakiego typu szyfrowanie lub jak wiadomość jest podpisany, zależy od implementacji i konfiguracji zgodnej usługi.  
  
 Zwróć uwagę, sposób, że kontrakt wymaga pewnych elementów w implementacji kontraktu usługi i konfigurację uruchomieniową dodanie zachowania. Zestaw wymagań, które muszą zostać spełnione, aby uwidocznić usługę do używania opiera się na poprzedni zestaw wymagań. Jeśli kontrakt sprawia, że wymagania dotyczące wdrażania, implementacja może wymagać jeszcze więcej konfiguracji i powiązań, które umożliwiają usługa ma zostać uruchomiona. Na koniec aplikacji hosta, również musi obsługiwać żadnych wymagań dotyczących dodających konfiguracji usługi i powiązania.  
  
 Ten proces dodawania wymaganie ważne jest, aby należy wziąć pod uwagę podczas projektowania, wdrażania, konfigurowania i hostowania aplikacji usługi Windows Communication Foundation (WCF). Na przykład kontrakt może określać, czy należy go obsługuje sesji. Jeśli tak, musisz skonfigurować powiązania w celu spełnienia tego wymagania umownych lub implementacji usługi nie będzie działać. Lub jeśli usługa wymaga uwierzytelniania zintegrowanego Windows i jest hostowana w Internet Information Services (IIS), aplikacji sieci Web, w którym znajduje się usługa musi mieć uwierzytelniania zintegrowanego Windows włączona i anonimowe pomocy technicznej, wyłączony. Aby uzyskać więcej informacji o funkcjach i wpływ typów aplikacji hosta innej usługi, zobacz [hostingu](../../../../docs/framework/wcf/feature-details/hosting.md).  
  
## <a name="see-also"></a>Zobacz także

- [Punkty końcowe: Adresy, powiązania i kontrakty](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [Projektowanie kontraktów usług](../../../../docs/framework/wcf/designing-service-contracts.md)
- [Implementowanie kontraktów usług](../../../../docs/framework/wcf/implementing-service-contracts.md)
