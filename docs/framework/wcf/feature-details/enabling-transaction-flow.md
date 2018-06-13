---
title: Włączanie przepływu transakcji
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF], enabling flow
ms.assetid: a03f5041-5049-43f4-897c-e0292d4718f7
ms.openlocfilehash: 180fc99195444057c5bbb4a1679e948f9ddf1830
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497094"
---
# <a name="enabling-transaction-flow"></a>Włączanie przepływu transakcji
Windows Communication Foundation (WCF) zapewnia bardzo elastyczne opcje kontroli przepływu transakcji. Ustawienia przepływu transakcji usługi można wyrazić przy użyciu kombinacji atrybutów i konfiguracji.  
  
## <a name="transaction-flow-settings"></a>Ustawienia przepływu transakcji  
 Ustawienia przepływu transakcji są generowane dla punktu końcowego wyniku przecięcia trzech następujących wartości:  
  
-   <xref:System.ServiceModel.TransactionFlowAttribute> Atrybutu dla każdej metody w kontrakcie usługi określono.  
  
-   `TransactionFlow` Właściwości binding określone powiązanie.  
  
-   `TransactionFlowProtocol` Właściwości binding określone powiązanie. `TransactionFlowProtocol` Właściwości binding pozwala wybrać jeden z dwóch protokołów innej transakcji, czy służy do uruchomienia przepływu transakcji. W poniższych sekcjach opisano krótko każdego z nich.  
  
### <a name="ws-atomictransaction-protocol"></a>Protokół WS-AtomicTransaction  
 Protokół WS-AtomicTransaction (WS-AT) jest przydatne w scenariuszach, gdy wymagane jest współdziałanie z stosy protokołu innych firm.  
  
### <a name="oletransactions-protocol"></a>Protokołu OleTransactions  
 Protokołu OleTransactions jest przydatne w scenariuszach, po współdziałanie z stosy protokołu innych firm nie jest wymagane, a narzędzie wdrażania usługi z wyprzedzeniem wie, że Usługa protokołu WS-AT jest wyłączona lokalnie lub nie istniejących topologii sieci Preferuj nie użycia protokołu WS-AT.  
  
 W poniższej tabeli przedstawiono różne typy przepływy transakcji, które mogą być generowane przy użyciu tych różnych kombinacji.  
  
|TransactionFlow<br /><br /> powiązanie|Właściwość powiązania TransactionFlow|Protokół powiązania TransactionFlowProtocol|Typ przepływu transakcji|  
|---------------------------------|--------------------------------------|----------------------------------------------|------------------------------|  
|Obowiązkowy|true|WS-AT.|Transakcja musi przepływ interoperacyjne format WS-AT.|  
|Obowiązkowy|true|OleTransactions|Musi być przepływ transakcji w formacie WCF OleTransactions.|  
|Obowiązkowy|false|Nie dotyczy|Nie dotyczy, ponieważ jest to nieprawidłowa konfiguracja.|  
|Dozwolone|true|WS-AT.|Transakcja może przepływ interoperacyjne format WS-AT.|  
|Dozwolone|true|OleTransactions|Może być przepływ transakcji w formacie WCF OleTransactions.|  
|Dozwolone|false|Dowolna wartość|Transakcja nie jest umieszczane.|  
|NotAllowed|Dowolna wartość|Dowolna wartość|Transakcja nie jest umieszczane.|  
  
 Poniższa tabela zawiera podsumowanie wyników przetwarzania komunikatów.  
  
|Komunikat przychodzący|Ustawienie TransactionFlow|Nagłówek transakcji|Wynik przetwarzania komunikatu|  
|----------------------|-----------------------------|------------------------|-------------------------------|  
|Protokół oczekiwany format jest zgodny transakcji|Dozwolone lub obowiązkowego|`MustUnderstand` Equals `true`.|Proces|  
|Transakcja nie jest zgodny z formatem oczekiwanym protokołu|Obowiązkowy|`MustUnderstand` Equals `false`.|Odrzucone, ponieważ wymagana jest transakcja|  
|Transakcja nie jest zgodny z formatem oczekiwanym protokołu|Dozwolone|`MustUnderstand` Equals `false`.|Odrzucone, ponieważ nagłówek jest niezrozumiały.|  
|Transakcja formacie protokołu|NotAllowed|`MustUnderstand` Equals `false`.|Odrzucone, ponieważ nagłówek jest niezrozumiały.|  
|Brak transakcji|Obowiązkowy|Brak|Odrzucone, ponieważ wymagana jest transakcja|  
|Brak transakcji|Dozwolone|Brak|Proces|  
|Brak transakcji|NotAllowed|Brak|Proces|  
  
 Podczas każdej metody na kontrakt mogą mieć wymagania przepływu innej transakcji, obejmuje ustawienia protokołu przepływ transakcji na poziomie powiązania. Oznacza to, że wszystkie metody, które współużytkują tego samego punktu końcowego (i w związku z tym to samo powiązanie) również udostępniać te same zasady, umożliwiając lub wymagających przepływu transakcji, jak również ten sam protokół transakcji, jeśli ma to zastosowanie.  
  
## <a name="enabling-transaction-flow-at-the-method-level"></a>Włączanie przepływu transakcji na poziomie — metoda  
 Wymagania dotyczące przepływu transakcji nie zawsze są takie same dla wszystkich metod w kontrakcie usługi. W związku z tym WCF także opartych na atrybutach mechanizm, dzięki czemu preferencje przepływu transakcji każdej metody wyrażane. Jest to osiągane przez <xref:System.ServiceModel.TransactionFlowAttribute> , który określa poziom, w którym operacji usługi akceptuje Nagłówek transakcji. Należy oznaczyć metody kontraktu usługi z tym atrybutem, jeśli chcesz włączyć przepływu transakcji. Ten atrybut ma jedną z wartości <xref:System.ServiceModel.TransactionFlowOption> wyliczenia, w którym wartość domyślna to <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>. Jeśli wszystkie wartości z wyjątkiem <xref:System.ServiceModel.TransactionFlowOption.NotAllowed> jest określona metoda jest wymagana będzie jednokierunkowe. Projektant można użyć tego atrybutu, aby określić wymagania dotyczące przepływu transakcji poziomie metody lub ograniczenia w czasie projektowania.  
  
## <a name="enabling-transaction-flow-at-the-endpoint-level"></a>Włączanie przepływu transakcji na poziomie punktu końcowego  
 Oprócz ustawienia przepływ transakcji na poziomie metody <xref:System.ServiceModel.TransactionFlowAttribute> zawiera atrybut WCF zawiera ustawienia dla punktu końcowego dla przepływu transakcji umożliwia administratorom przepływ transakcji na wyższym poziomie.  
  
 Jest to osiągane przez <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, co umożliwia włączanie lub wyłączanie przychodzący transakcji w punkcie końcowym powiązania ustawienia, a także określenie transakcji żądany format protokołu przychodzących transakcji.  
  
 Jeśli powiązanie wyłączył przepływu transakcji, ale wymaga jednej z operacji na kontrakt usługi transakcji przychodzącej, podczas uruchamiania usługi jest zgłaszany wyjątek sprawdzania poprawności.  
  
 Większość powiązań stałego WCF zapewnia zawierają `transactionFlow` i `transactionProtocol` atrybutów w celu włączenia, skonfigurowania określone powiązanie do akceptowania przychodzących transakcji. Aby uzyskać więcej informacji na temat ustawiania elementów konfiguracji, zobacz [ \<powiązania >](../../../../docs/framework/misc/binding.md).  
  
 Administrator lub narzędzia wdrażania umożliwia przepływu transakcji poziomie punktu końcowego skonfigurować wymagania dotyczące przepływu transakcji lub ograniczenia w czasie wdrażania przy użyciu pliku konfiguracji.  
  
## <a name="security"></a>Zabezpieczenia  
 Aby zapewnić bezpieczeństwo systemu i integralności, należy zabezpieczyć wymiany komunikatów podczas przepływu transakcji między aplikacjami. Nie należy przepływu ani ujawnić szczegóły transakcji do dowolnej aplikacji, która nie jest uprawniony do udziału w tej samej transakcji.  
  
 Podczas generowania klienci WCF do nieznanej lub niezaufanej usług sieci Web za pomocą wymiany metadanych, wywołania operacji na te usługi sieci Web ma pomijać bieżącą transakcję, jeśli to możliwe. Poniższy przykład demonstruje, jak to zrobić.  
  
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
  
 Ponadto należy skonfigurować usług do akceptowania przychodzących transakcji tylko od klientów, którzy mają one uwierzytelnieniu i autoryzacji. Przychodzące transakcje powinna być akceptowana tylko, jeśli pochodzą z wysoce zaufanych klientów.  
  
## <a name="policy-assertions"></a>Asercji zasad  
 WCF używa potwierdzenia zasad w celu kontroli przepływu transakcji. Potwierdzenia zasad można znaleźć w dokumencie zasad usługi, która jest generowana przez agregację kontrakty, konfiguracji i atrybuty. Klient może pobrać dokument zasad usługi przy użyciu HTTP GET lub WS-MetadataExchange żądanie odpowiedź. Klienci mogą następnie przetworzyć dokument zasad, aby ustalić, jakie operacje na kontrakt usługi może obsługuje ani nie wymaga przepływu transakcji.  
  
 Potwierdzenia zasad przepływu transakcji wpływają na przepływu transakcji, określając nagłówki SOAP czy klienta należy wysłać do usługi do reprezentowania transakcji. Wszystkie nagłówki transakcji musi być oznaczone `MustUnderstand` równa `true`. Dowolny komunikat z nagłówkiem, w przeciwnym razie oznaczone jest odrzucane błędu protokołu SOAP.  
  
 Tylko jeden potwierdzenia zasad dotyczących transakcji mogą być obecne w ramach jednej operacji. Dokumenty zasad z więcej niż jednego potwierdzenia transakcji w przypadku operacji są uznawane za nieprawidłowe i są odrzucane przez usługę WCF. Ponadto tylko jednej transakcji protokołu może znajdować się wewnątrz każdego typu portu. Zasady dokumentów za pomocą operacji odwołuje się do więcej niż jeden protokół transakcji wewnątrz typu jednego portu są uznawane za nieprawidłowe i są odrzucane przez [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Zasady dokumentów za pomocą transakcji potwierdzenia znajduje się on na komunikaty wyjściowe lub jednokierunkowe komunikaty wejściowe również są uznawane za nieprawidłowe.
