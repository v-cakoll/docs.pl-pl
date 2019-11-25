---
title: Włączanie przepływu transakcji
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF], enabling flow
ms.assetid: a03f5041-5049-43f4-897c-e0292d4718f7
ms.openlocfilehash: 8aff6afb09c97d7d01f5e7b7f1b92ae24bb99fb7
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141756"
---
# <a name="enabling-transaction-flow"></a>Włączanie przepływu transakcji
Windows Communication Foundation (WCF) zapewnia wysoce elastyczne opcje kontroli przepływu transakcji. Ustawienia przepływu transakcji usługi mogą być wyrażone przy użyciu kombinacji atrybutów i konfiguracji.  
  
## <a name="transaction-flow-settings"></a>Ustawienia przepływu transakcji  
 Ustawienia przepływu transakcji są generowane dla punktu końcowego usługi w wyniku przecięcia następujących trzech wartości:  
  
- Atrybut <xref:System.ServiceModel.TransactionFlowAttribute> określony dla każdej metody w kontrakcie usługi.  
  
- Właściwość powiązania `TransactionFlow` określonego powiązania.  
  
- Właściwość powiązania `TransactionFlowProtocol` określonego powiązania. Właściwość powiązania `TransactionFlowProtocol` umożliwia wybranie spośród dwóch różnych protokołów transakcji, których można użyć do przepływu transakcji. W poniższych sekcjach krótko opisano każdą z nich.  
  
### <a name="ws-atomictransaction-protocol"></a>Protokół WS-AtomicTransaction  
 Protokół WS-AtomicTransaction (WS-AT) jest użyteczny w scenariuszach, gdy wymagane jest współdziałanie z stosami protokołu innych firm.  
  
### <a name="oletransactions-protocol"></a>Protokół OleTransactions  
 Protokół OleTransactions jest użyteczny w scenariuszach, gdy współdziałanie z stosami protokołu innych firm nie jest wymagane, a program wdrażania usługi wie z wyprzedzeniem, że usługa protokołu WS-AT jest wyłączona lokalnie lub istniejąca topologia sieci nie Preferuj użycia usługi WS-AT.  
  
 W poniższej tabeli przedstawiono różne typy przepływów transakcji, które można wygenerować przy użyciu tych różnych kombinacji.  
  
|TransactionFlow<br /><br /> powiązanie|Właściwość powiązania TransactionFlow|Protokół powiązania TransactionFlowProtocol|Typ przepływu transakcji|  
|---------------------------------|--------------------------------------|----------------------------------------------|------------------------------|  
|Obowiązkowy|true|WS-AT|Transakcja musi być przepływa w formacie międzyoperacyjnym WS-AT.|  
|Obowiązkowy|true|OleTransactions|Transakcja musi być przepływa w formacie OleTransactions WCF.|  
|Obowiązkowy|false|Nie dotyczy|Nie dotyczy, ponieważ jest to nieprawidłowa konfiguracja.|  
|Występować|true|WS-AT|Transakcja może być przepływa w formacie międzyoperacyjnym WS-AT.|  
|Występować|true|OleTransactions|Transakcja może być przepływa w formacie OleTransactions WCF.|  
|Występować|false|Dowolna wartość|Transakcja nie jest przepływa.|  
|NotAllowed|Dowolna wartość|Dowolna wartość|Transakcja nie jest przepływa.|  
  
 Poniższa tabela zawiera podsumowanie wyników przetwarzania komunikatów.  
  
|Komunikat przychodzący|Ustawienie TransactionFlow|Nagłówek transakcji|Wynik przetwarzania komunikatu|  
|----------------------|-----------------------------|------------------------|-------------------------------|  
|Transakcja jest zgodna z oczekiwanym formatem protokołu|Dozwolone lub obowiązkowe|`MustUnderstand` równe `true`.|Proces|  
|Transakcja nie jest zgodna z oczekiwanym formatem protokołu|Obowiązkowy|`MustUnderstand` równe `false`.|Odrzucono, ponieważ jest wymagana transakcja|  
|Transakcja nie jest zgodna z oczekiwanym formatem protokołu|Występować|`MustUnderstand` równe `false`.|Odrzucono, ponieważ nagłówek nie jest zrozumiały|  
|Transakcja przy użyciu dowolnego formatu protokołu|NotAllowed|`MustUnderstand` równe `false`.|Odrzucono, ponieważ nagłówek nie jest zrozumiały|  
|Brak transakcji|Obowiązkowy|Brak|Odrzucono, ponieważ jest wymagana transakcja|  
|Brak transakcji|Występować|Brak|Proces|  
|Brak transakcji|NotAllowed|Brak|Proces|  
  
 Chociaż każda metoda w kontrakcie może mieć różne wymagania dotyczące przepływu transakcji, ustawienie protokołu przepływu transakcji jest ograniczone na poziomie powiązania. Oznacza to, że wszystkie metody, które współużytkują ten sam punkt końcowy (i w związku z tym to samo powiązanie), również współużytkują te same zasady, które umożliwiają lub wymagają przepływu transakcji, a także ten sam protokół transakcji, jeśli ma to zastosowanie.  
  
## <a name="enabling-transaction-flow-at-the-method-level"></a>Włączanie przepływu transakcji na poziomie metody  
 Wymagania przepływu transakcji nie są zawsze takie same dla wszystkich metod w kontrakcie usługi. W związku z tym WCF zapewnia również mechanizm oparty na atrybutach, aby umożliwić wyrażanie preferencji przepływu transakcji poszczególnych metod. Jest to osiągane przez <xref:System.ServiceModel.TransactionFlowAttribute>, który określa poziom, w którym operacja usługi akceptuje Nagłówek transakcji. Jeśli chcesz włączyć przepływ transakcji, należy oznaczyć metody kontraktu usługi z tym atrybutem. Ten atrybut przyjmuje jedną z wartości wyliczenia <xref:System.ServiceModel.TransactionFlowOption>, w którym wartość domyślna to <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>. Jeśli dowolna wartość z wyjątkiem <xref:System.ServiceModel.TransactionFlowOption.NotAllowed> jest określona, metoda jest wymagana, aby nie była jednokierunkowa. Deweloper może użyć tego atrybutu, aby określić wymagania lub ograniczenia przepływu transakcji na poziomie metody w czasie projektowania.  
  
## <a name="enabling-transaction-flow-at-the-endpoint-level"></a>Włączanie przepływu transakcji na poziomie punktu końcowego  
 Oprócz ustawienia przepływu transakcji na poziomie metody, który udostępnia atrybut <xref:System.ServiceModel.TransactionFlowAttribute>, funkcja WCF zapewnia ustawienie dla przepływu transakcji dla całego punktu końcowego, co umożliwia administratorom sterowanie przepływem transakcji na wyższym poziomie.  
  
 Jest to osiągane przez <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, co umożliwia włączenie lub wyłączenie przychodzącego przepływu transakcji w ustawieniach powiązań punktu końcowego, a także określenie formatu żądanego protokołu transakcji dla przychodzących transakcji.  
  
 Jeśli powiązanie wyłączyło przepływ transakcji, ale jedna z operacji w kontrakcie usługi wymaga transakcji przychodzącej, podczas uruchamiania usługi jest zgłaszany wyjątek sprawdzania poprawności.  
  
 Większość stałych powiązań WCF zawiera atrybuty `transactionFlow` i `transactionProtocol`, które umożliwiają skonfigurowanie określonego powiązania w celu akceptowania przychodzących transakcji. Aby uzyskać więcej informacji na temat ustawiania elementów konfiguracji, zobacz [\<powiązywanie >](../../configure-apps/file-schema/wcf/bindings.md).  
  
 Administrator lub program do wdrażania może użyć przepływu transakcji na poziomie punktu końcowego w celu skonfigurowania wymagań przepływu transakcji lub ograniczeń w czasie wdrażania przy użyciu pliku konfiguracji.  
  
## <a name="security"></a>Zabezpieczenia  
 Aby zapewnić bezpieczeństwo i integralność systemu, należy zabezpieczyć wymianę komunikatów podczas przepływu transakcji między aplikacjami. Nie należy przepływać ani ujawniać szczegółowych informacji o transakcji do żadnej aplikacji, która nie jest uprawniona do uczestniczenia w tej samej transakcji.  
  
 Podczas generowania klientów WCF do nieznanych lub niezaufanych usług sieci Web za pomocą wymiany metadanych, wywołania operacji na tych usługach sieci Web powinny pomijać bieżącą transakcję, jeśli jest to możliwe. Poniższy przykład demonstruje, jak to zrobić.  
  
```csharp
//client code which has an ambient transaction  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Suppress))  
{  
    // No transaction will flow to this operation  
    untrustedProxy.Operation1(...);  
    scope.Complete();  
}  
//remainder of client code  
```  
  
 Ponadto usługi należy skonfigurować w taki sposób, aby akceptowały transakcje przychodzące tylko od klientów, którzy zostali uwierzytelnieni i autoryzowani. Przychodzące transakcje powinny być akceptowane tylko wtedy, gdy pochodzą z wysoce zaufanych klientów.  
  
## <a name="policy-assertions"></a>Potwierdzenia zasad  
 Funkcja WCF używa potwierdzeń zasad do sterowania przepływem transakcji. Potwierdzenia zasad znajdują się w dokumencie zasad usługi, który jest generowany przez agregowanie kontraktów, konfiguracji i atrybutów. Klient może uzyskać dokument zasad usługi przy użyciu polecenia HTTP GET lub żądania WS-MetadataExchange. Klienci mogą następnie przetwarzać dokument zasad, aby określić, które operacje w kontrakcie usługi mogą obsługiwać lub wymagać przepływu transakcji.  
  
 Potwierdzenia zasad przepływu transakcji mają wpływ na przepływ transakcji przez określenie nagłówków protokołu SOAP, które klient powinien wysłać do usługi, aby reprezentować transakcję. Wszystkie nagłówki transakcji muszą być oznaczone `MustUnderstand` równe `true`. Wszystkie komunikaty z nagłówkiem oznaczonym inaczej są odrzucane z błędem SOAP.  
  
 Tylko jedno potwierdzenie zasad związanych z transakcją może być obecne w jednej operacji. Dokumenty zasad z więcej niż jedną potwierdzeniem transakcji w operacji są uznawane za nieprawidłowe i są odrzucane przez WCF. Ponadto tylko jeden protokół transakcji może być obecny w obrębie każdego typu portu. Dokumenty zasad z operacjami odwołującymi się do więcej niż jednego protokołu transakcji wewnątrz jednego typu portu są uznawane za nieprawidłowe i są odrzucane przez narzędzie do obsługi [metadanych ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Dokumenty zasad z potwierdzeniami transakcji znajdującymi się w wiadomościach wyjściowych lub jednokierunkowymi komunikatami wejściowymi są również uznawane za nieprawidłowe.
