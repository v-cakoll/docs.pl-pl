---
title: Projektowanie i implementowanie usług
ms.date: 03/30/2017
helpviewer_keywords:
- defining service contracts [WCF]
ms.assetid: 036fae20-7c55-4002-b71d-ac4466e167a3
ms.openlocfilehash: 5cbf7c16988d8b8858aa75f4e7a956fa371238dd
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64652043"
---
# <a name="designing-and-implementing-services"></a>Projektowanie i implementowanie usług
W tej sekcji dowiesz się, jak zdefiniować i implementowanie kontraktów usług WCF. Kontrakt usługi określa punkt końcowy komunikuje na zewnątrz. Na poziomie bardziej konkretne takie jak żądanie/nietypizowana odpowiedź, jednokierunkowe i dwukierunkowego jest poufności informacji na temat zestawu specyficzne komunikaty dotyczące podzielone na podstawowe wiadomości programu exchange wzorców (MEPs). Kontrakt usługi to zestaw logicznie powiązanych wymianę komunikatów, operacja usługi czy exchange pojedynczym komunikacie. Na przykład `Hello` operacji oczywiście akceptują jeden komunikat (tak, aby obiekt wywołujący może poinformować o powitania) i może być lub może nie zwrócić komunikat (w zależności od grzecznościowy operacji).  
  
 Aby uzyskać więcej informacji na temat umów i inne podstawowe pojęcia usługi Windows Communication Foundation (WCF), zobacz [podstawowe pojęcia programu Windows Communication Foundation](../../../docs/framework/wcf/fundamental-concepts.md). Ten temat koncentruje się na wyjaśnieniu kontraktów usług. Aby uzyskać więcej informacji na temat sposobu tworzenia klientów, którzy używają kontraktów usług, aby połączyć się z usługami, zobacz [Przegląd klienta programu WCF](../../../docs/framework/wcf/wcf-client-overview.md).  
  
## <a name="overview"></a>Omówienie  
 Ten temat zawiera wysokiego poziomu orientację koncepcyjnej, aby projektowanie i Implementowanie usług WCF. Tematy podrzędne zapewniają bardziej szczegółowe informacje o szczegółowe informacje na temat projektowania i implementacji. Przed projektowanie i wdrażanie aplikacji WCF, zaleca się że:  
  
- Zrozumieć, jakie kontraktu usługi, jak to działa i jak ją utworzyć.  
  
- Zrozumienie, że kontraktów stanu minimalne wymagania konfiguracji środowiska uruchomieniowego lub środowisko hostingu mogą nie obsługiwać.  
  
## <a name="service-contracts"></a>Kontrakty usług  
 Kontrakt usługi określa:  
  
- Przedstawia kontrakt operacji.  
  
- Podpis operacje pod kątem komunikatów wymienianych.  
  
- Typy danych tych komunikatów.  
  
- Lokalizacja operacji.  
  
- Określonych protokołów i formatów serializacji, które są używane do obsługi pomyślnej komunikacji z usługą.  
  
 Na przykład może być kontrakt zamówienia zakupu `CreateOrder` operacji, który akceptuje dane wejściowe informacji o zamówieniach typów i zwraca informacje o powodzeniu lub niepowodzeniu, tym identyfikator zamówienia. Może także mieć `GetOrderStatus` operacji, która akceptuje identyfikator zamówienia i zwraca informacje o stanie zamówienia. Określ tego rodzaju kontraktu usługi:  
  
1. Kontrakt zamówienia zakupu składa się z `CreateOrder` i `GetOrderStatus` operacji.  
  
2. Czy operacje mają określone komunikaty wejściowe i wyjściowe komunikaty.  
  
3. Dane, które może wykonywać te komunikaty.  
  
4. Podzielone na kategorie instrukcji dotyczących infrastruktury komunikacji konieczne pomyślnie przetwarzania komunikatów. Na przykład, obejmują one czy i jakie rodzaje zabezpieczeń są wymagane do nawiązania komunikacji pomyślnie.  
  
 W celu przekazania tego rodzaju informacji do innych aplikacji na wiele platform (w tym platformy firmy Microsoft), kontraktów usług XML są publicznie wyrażone w standardowych formatów XML, takie jak [Web Services Description Language](https://go.microsoft.com/fwlink/?LinkId=94952) () WSDL) i [schematu XML](https://go.microsoft.com/fwlink/?LinkId=94953) (XSD), między innymi. Deweloperów na wielu platformach, można użyć tych informacji zamówienia publicznego do tworzenia aplikacji, które mogą się komunikować z usługą, zarówno ponieważ rozumieją języka specyfikacji, a te języki są ustalono, aby umożliwić współdziałanie poprzez opisanie publicznych formularzy, formatów i protokołów obsługiwanych przez usługę. Aby uzyskać więcej informacji na temat usługi WCF obsługi tego rodzaju informacje, zobacz [metadanych](../../../docs/framework/wcf/feature-details/metadata.md).  
  
 Kontrakty mogą być wyrażone na wiele sposobów i WSDL i XSD są doskonałe języków do opisu usługi w łatwy sposób, jest trudne języków do użycia bezpośrednio i jedynie opisano usługi, nie implementacji kontraktu usługi. Dlatego aplikacji WCF użycie klasy, interfejsy i atrybuty zarządzanych zarówno do definiowania struktury usługi, jak i do jego wdrożenia.  
  
 Wynikowy kontrakt zdefiniowany w typami zarządzanymi mogą być *wyeksportowane* jako metadane — WSDL i XSD — w razie przez klientów lub inne implementacje usługi. Wynik jest prosty model programowania, który można opisać (przy użyciu metadanych publicznej), aby każda aplikacja kliencka. Szczegółowe informacje o podstawowej komunikaty protokołu SOAP transportu i informacji związanych z zabezpieczeniami i tak dalej, można pozostawić WCF, który automatycznie wykonuje konwersje niezbędne do i z systemu typu kontraktu usługi do systemu typów XML.  
  
 Aby uzyskać więcej informacji na temat Projektowanie kontraktów zobacz [projektowanie kontraktów usług](../../../docs/framework/wcf/designing-service-contracts.md). Aby uzyskać więcej informacji na temat Implementowanie kontraktów zobacz [Implementowanie kontraktów usług](../../../docs/framework/wcf/implementing-service-contracts.md).  
  
### <a name="messages-up-front-and-center"></a>Komunikaty w górę Centrum  
 Zarządzane interfejsy, klasy i metody służące do operacji usługi modelu jest prosta, gdy są używane do zdalnego wywołania procedury (RPC)-stylu podpisy metod, w których przekazywanie parametrów do metody i odbieranie wartości zwracane jest formą normalny żądania funkcji lub inny rodzaj kodu obiektu. Na przykład Programiści używający języków zarządzanych, takich jak Visual Basic i C++ COM można zastosować swojej wiedzy na temat podejścia stylu RPC (czy przy użyciu obiektów lub interfejsy) do utworzenia kontraktów usług WCF bez występują problemy związane z Obiekt systemów rozproszonych się w stylu RPC. Orientacja usługa zapewnia korzyści luźno powiązanych, ukierunkowane programowania przy zachowaniu łatwy i znajomości języka RPC środowisko programowania.  
  
 Wielu programistów jest wygodniejsze przy użyciu interfejsów, takich jak kolejki komunikatów, takich jak Microsoft MSMQ programowania aplikacji ukierunkowane <xref:System.Messaging> przestrzeniach nazw programu .NET Framework lub wysyłania XML bez struktury w żądaniach HTTP, kilka. Aby uzyskać więcej informacji na temat programowania na poziomie komunikatu zobacz [za pomocą kontraktów komunikatu](../../../docs/framework/wcf/feature-details/using-message-contracts.md), [programowania na poziomie kanału usługi](../../../docs/framework/wcf/extending/service-channel-level-programming.md), i [współdziałanie z aplikacjami POX](../../../docs/framework/wcf/feature-details/interoperability-with-pox-applications.md).  
  
### <a name="understanding-the-hierarchy-of-requirements"></a>Informacje o hierarchii wymagania  
 Kontrakt usługi grupy operacji; Określa wymiany komunikatów, typy komunikatów i danych typów przeniesienia tych wiadomości; Wskazuje kategorii do umowy dotyczącej pomocy technicznej jest posiadanie implementacji zachowania w czasie wykonywania (na przykład może wymagać zaszyfrowana i podpisana wiadomości). Kontrakt usługi nie określa dokładne jak te wymagania, tylko, muszą one być. Typ szyfrowania lub sposób, w którym komunikat jest podpisany, zależy od implementacji i konfiguracji zgodnej usługi.  
  
 Zwróć uwagę, sposób, że kontrakt wymaga pewnych elementów w implementacji kontraktu usługi i konfigurację uruchomieniową dodanie zachowania. Zestaw wymagań, które muszą zostać spełnione, aby uwidocznić usługę do używania opiera się na poprzedni zestaw wymagań. Jeśli kontrakt sprawia, że wymagania dotyczące wdrażania, implementacja może wymagać jeszcze więcej konfiguracji i powiązań, które umożliwiają usługa ma zostać uruchomiona. Na koniec aplikacji hosta, również musi obsługiwać żadnych wymagań dotyczących dodających konfiguracji usługi i powiązania.  
  
 Ten proces dodawania wymaganie ważne jest, aby należy wziąć pod uwagę podczas projektowania, wdrażania, konfigurowania i hostowania aplikacji usługi Windows Communication Foundation (WCF). Na przykład kontrakt może określać, czy należy go obsługuje sesji. Jeśli tak, musisz skonfigurować powiązania w celu spełnienia tego wymagania umownych lub implementacji usługi nie będzie działać. Lub jeśli usługa wymaga zintegrowanego uwierzytelniania Windows i jest hostowana w Internet Information Services (IIS), aplikacji sieci Web, w którym znajduje się usługa musi mieć zintegrowane uwierzytelnianie Windows włączona i anonimowe pomocy technicznej, wyłączony. Aby uzyskać więcej informacji o funkcjach i wpływ typów aplikacji hosta innej usługi, zobacz [usług obsługującego](../../../docs/framework/wcf/hosting-services.md).  
  
## <a name="see-also"></a>Zobacz także

- [Projektowanie kontraktów usług](../../../docs/framework/wcf/designing-service-contracts.md)
- [Implementowanie kontraktów usług](../../../docs/framework/wcf/implementing-service-contracts.md)
