---
title: Włączanie przepływu transakcji
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF], enabling flow
ms.assetid: a03f5041-5049-43f4-897c-e0292d4718f7
ms.openlocfilehash: 180fc99195444057c5bbb4a1679e948f9ddf1830
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61856665"
---
# <a name="enabling-transaction-flow"></a>Włączanie przepływu transakcji
Windows Communication Foundation (WCF) zapewnia bardzo elastyczne opcje do kontrolowania przepływu transakcji. Ustawienia przepływu transakcji usługi mogą być wyrażone przy użyciu kombinacji atrybutów i konfiguracji.  
  
## <a name="transaction-flow-settings"></a>Ustawienia przepływu transakcji  
 Ustawienia przepływu transakcji są generowane dla punktu końcowego usługi, w wyniku przecięcia trzech następujących wartości:  
  
- <xref:System.ServiceModel.TransactionFlowAttribute> Atrybutu dla każdej metody w kontrakcie usługi.  
  
- `TransactionFlow` Powiązanie właściwości w określonym powiązaniu.  
  
- `TransactionFlowProtocol` Powiązanie właściwości w określonym powiązaniu. `TransactionFlowProtocol` Powiązanie właściwości pozwala na dokonanie wyboru spośród dwóch protokołów innej transakcji, można użyć do przepływu transakcji. W poniższych sekcjach krótko opisano każdego z nich.  
  
### <a name="ws-atomictransaction-protocol"></a>Protokół WS-AtomicTransaction  
 Protokół WS-AtomicTransaction (WS-AT) jest przydatne w scenariuszach, gdy wymagane jest współdziałanie ze stosów protokołu innych firm.  
  
### <a name="oletransactions-protocol"></a>Protokół OleTransactions  
 Protokół OleTransactions jest przydatne w scenariuszach, współdziałanie z stosów protokołu innych firm nie jest wymagana, gdy wdrażania usługi wcześniej wie, że usługi protokołu WS-AT jest wyłączone lokalnie, lub istniejącą topologię sieci nie nie Preferuj użycie WS-AT.  
  
 W poniższej tabeli przedstawiono różne typy przepływów transakcji, które mogą być generowane przy użyciu tych różnych kombinacji.  
  
|transactionFlow<br /><br /> powiązanie|Właściwość powiązania TransactionFlow|Protokół powiązania TransactionFlowProtocol|Typ przepływu transakcji|  
|---------------------------------|--------------------------------------|----------------------------------------------|------------------------------|  
|Obowiązkowy|true|WS-AT|Transakcji musi przepływać format WS-AT międzyoperacyjnych.|  
|Obowiązkowy|true|OleTransactions|Transakcji musi przepływać w formacie WCF OleTransactions.|  
|Obowiązkowy|false|Nie dotyczy|Nie dotyczy, ponieważ jest to nieprawidłowa konfiguracja.|  
|Dozwolone|true|WS-AT|Transakcja może przekazane w formacie WS-AT międzyoperacyjnych.|  
|Dozwolone|true|OleTransactions|Transakcja może przepływać w formacie WCF OleTransactions.|  
|Dozwolone|false|Dowolna wartość|Transakcja nie jest przepływ.|  
|NotAllowed|Dowolna wartość|Dowolna wartość|Transakcja nie jest przepływ.|  
  
 Poniższa tabela zawiera podsumowanie wyników przetwarzania wiadomości.  
  
|Przychodząca wiadomość|Ustawienie TransactionFlow|Nagłówek transakcji|Wynik przetworzenia komunikatu|  
|----------------------|-----------------------------|------------------------|-------------------------------|  
|Transakcja odpowiada protokołu oczekiwanego formatu|Dozwolone lub obowiązkowe|`MustUnderstand` równa się `true`.|Proces|  
|Transakcja nie jest zgodny z formatem oczekiwanym protokołu|Obowiązkowy|`MustUnderstand` równa się `false`.|Odrzucone, ponieważ wymagana jest transakcja|  
|Transakcja nie jest zgodny z formatem oczekiwanym protokołu|Dozwolone|`MustUnderstand` równa się `false`.|Odrzucone, ponieważ nagłówek jest niezrozumiały.|  
|Transakcji, w formacie protokołu|NotAllowed|`MustUnderstand` równa się `false`.|Odrzucone, ponieważ nagłówek jest niezrozumiały.|  
|Nie transakcji|Obowiązkowy|Brak|Odrzucone, ponieważ wymagana jest transakcja|  
|Nie transakcji|Dozwolone|Brak|Proces|  
|Nie transakcji|NotAllowed|Brak|Proces|  
  
 Podczas każdej metody na kontrakt może mieć wymagania dotyczące przepływu innej transakcji, ustawienie protokołu przepływu transakcji ma zakres na poziomie powiązania. Oznacza to, że wszystkie metody, które współużytkują ten sam punkt końcowy (i w związku z tym tego samego powiązania) również udostępniać te same zasady, umożliwiając bądź wymagają takiej przepływu transakcji, a także ten sam protokół transakcji, jeśli ma to zastosowanie.  
  
## <a name="enabling-transaction-flow-at-the-method-level"></a>Włączanie przepływu transakcji na poziomie — metoda  
 Wymagania dotyczące przepływu transakcji nie zawsze są takie same dla wszystkich metod w kontrakcie usługi. W związku z tym usługi WCF także opartych na atrybutach mechanizm umożliwia każdej metody preferencje dotyczące przepływu transakcji wyrażane. Jest to osiągane przez <xref:System.ServiceModel.TransactionFlowAttribute> , który określa poziom, w którym operacji usługi akceptuje Nagłówek transakcji. Jeśli chcesz włączyć przepływ transakcji, należy oznaczyć metody kontraktu usługi za pomocą tego atrybutu. Ten atrybut ma jedną z wartości <xref:System.ServiceModel.TransactionFlowOption> wyliczenia, w którym wartość domyślna to <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>. Jeśli wszystkie wartości z wyjątkiem <xref:System.ServiceModel.TransactionFlowOption.NotAllowed> jest określony, metoda jest wymagany, nie są jednokierunkowe. Deweloper może użyć tego atrybutu, aby określić wymagania dotyczące przepływu transakcji na poziomie lub ograniczenia w czasie projektowania.  
  
## <a name="enabling-transaction-flow-at-the-endpoint-level"></a>Włączanie przepływu transakcji na poziomie punktu końcowego  
 Oprócz ustawienia przepływu transakcji na poziomie <xref:System.ServiceModel.TransactionFlowAttribute> zawiera atrybut WCF zawiera ustawienia dla punktu końcowego dla przepływu transakcji umożliwia ona administratorom do sterowania przepływem transakcji na wyższym poziomie.  
  
 Jest to osiągane przez <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, co umożliwia włączanie lub wyłączanie przychodzącego przepływu transakcji w punkcie końcowym powiązania ustawienia, a także określenie transakcji żądany format protokół transakcji przychodzących.  
  
 Jeśli wiązanie wyłączył przepływu transakcji, ale jedna z operacji w kontrakcie usługi wymaga transakcja przychodzące, podczas uruchamiania usługi jest zgłaszany wyjątek sprawdzania poprawności.  
  
 Większość powiązania stałego WCF zapewnia zawierają `transactionFlow` i `transactionProtocol` atrybutów, które mają umożliwiać użytkownikowi konfigurowanie określonych powiązania do akceptowania przychodzących transakcji. Aby uzyskać więcej informacji na temat ustawiania elementów konfiguracji, zobacz [ \<powiązania >](../../../../docs/framework/misc/binding.md).  
  
 Administrator lub wdrażania umożliwia przepływ transakcji na poziomie punktu końcowego Skonfiguruj wymagania dotyczące przepływu transakcji lub ograniczenia w czasie wdrażania przy użyciu pliku konfiguracji.  
  
## <a name="security"></a>Zabezpieczenia  
 Aby upewnić się, system bezpieczeństwa i integralności, należy zabezpieczyć wymianę komunikatów podczas przepływu transakcji między aplikacjami. Nie należy przepływu lub ujawniania szczegółów transakcji do dowolnej aplikacji, która nie jest uprawniony do wzięcia udziału w ramach jednej transakcji.  
  
 Podczas generowania klientów usługi WCF do nieznanej lub niezaufanej usług sieci Web za pomocą wymiany metadanych, wywołania operacji na te usługi sieci Web ma pomijać bieżącej transakcji, jeśli jest to możliwe. Poniższy przykład demonstruje, jak to zrobić.  
  
```  
//client code which has an ambient transaction  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Suppress))  
{  
    // No transaction will flow to this operation  
    untrustedProxy.Operation1(...);  
    scope.Complete();  
}  
//remainder of client code  
```  
  
 Ponadto usługi należy skonfigurować do akceptowania przychodzących transakcji tylko od klientów, którzy mają uwierzytelniony i autoryzowany. Przychodzące transakcje powinny być akceptowane tylko, jeśli pochodzą z wysoce zaufanych klientów.  
  
## <a name="policy-assertions"></a>Asercji zasad  
 Usługi WCF używa asercji zasad w celu sterowania przepływem transakcji. Asercji zasad można znaleźć w dokumencie zasady usługi, którym jest generowany przez agregację kontrakty, konfiguracji i atrybutów. Klient może pobrać dokumentu zasad usługi za pomocą żądania HTTP GET lub WS-MetadataExchange typu żądanie odpowiedź. Klienci mogą następnie przetwarzać dokument zasad, aby określić, jakie operacje w kontrakcie usługi może obsługi lub wymagania przepływu transakcji.  
  
 Asercji zasad przepływu transakcji wpływać na przepływ transakcji, określając nagłówków protokołu SOAP, klienta należy wysłać do usługi do reprezentowania transakcji. Wszystkie nagłówki transakcji musi być oznaczony przez `MustUnderstand` równa `true`. Każdy komunikat z nagłówkiem, w przeciwnym razie oznaczone jest odrzucana przy użyciu protokołu SOAP.  
  
 Tylko jedną asercję zasad związanych z transakcji może znajdować się w ramach jednej operacji. Zasady dokumentów za pomocą więcej niż jeden potwierdzenie transakcji w przypadku operacji są uznawane za nieprawidłowe i są odrzucane przez architekturę WCF. Ponadto tylko protokół pojedyncza transakcja może być obecne w każdego typu portu. Dokumentów zasad z operacjami, które odwołuje się do więcej niż jeden protokół transakcji wewnątrz typu jednego portu są uznawane za nieprawidłowe i zostały odrzucone prze [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Zasady dokumentów za pomocą transakcji potwierdzenia znajduje się on na komunikaty wyjściowe lub jednokierunkowe komunikaty wejściowe także są uznawane za nieprawidłowe.
