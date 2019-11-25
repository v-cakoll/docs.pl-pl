---
title: 'Instrukcje: korzystanie z monikera usługi Windows Communication Foundation bez rejestracji'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], service monikers without registration
ms.assetid: ee3cf5c0-24f0-4ae7-81da-73a60de4a1a8
ms.openlocfilehash: c08fc362694469560eb7368eb5e536c08ec19bdf
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975998"
---
# <a name="how-to-use-the-windows-communication-foundation-service-moniker-without-registration"></a>Instrukcje: korzystanie z monikera usługi Windows Communication Foundation bez rejestracji
Aby nawiązać połączenie z usługą Windows Communication Foundation (WCF) i komunikować się z nią, aplikacja kliencka programu WCF musi mieć szczegóły dotyczące adresu usługi, konfiguracji powiązania i kontraktu usługi.  
  
 Moniker usługi WCF zwykle uzyskuje wymagany kontrakt za pomocą wcześniejszej rejestracji wymaganych typów atrybutów, ale mogą wystąpić sytuacje, w których nie jest to możliwe. W przypadku rejestracji moniker może uzyskać definicję kontraktu w formie dokumentu języka definicji usług sieci Web (WSDL), poprzez użycie parametru `wsdl` lub za pomocą wymiany metadanych przy użyciu parametru `mexAddress`.  
  
 Pozwala to na takie scenariusze, jak dystrybucja arkusza kalkulacyjnego programu Excel, w którym niektóre wartości komórek są obliczane za pomocą interakcji usługi sieci Web. W tym scenariuszu może nie być możliwe zarejestrowanie zestawu kontraktu usługi na wszystkich klientach, który może otworzyć ten dokument. Parametr `wsdl` lub parametr `mexAddress` włącza samodzielne rozwiązanie.  
  
> [!NOTE]
> Wzajemne uwierzytelnianie musi być używane do ochrony przed manipulacjami lub fałszowaniem żądań i odpowiedzi. Szczególnie ważne jest, aby klienci mogli zapewnić, że punkt końcowy wymiany metadanych, który odpowiada, jest zamierzoną stroną zaufaną.  
  
## <a name="example"></a>Przykład  
 Ten przykład pokazuje użycie monikera usługi z kontraktem MEX. Usługa z następującym kontraktem jest udostępniona z wsHttpBinding.  
  
```csharp
using System.ServiceModel;  
  
// ...
  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Demo")]  
public interface IAffiliate  
{  
    [OperationContract]  
    bool NewAffiliate(string ID, string company, string fullname, string accountsCode);  
    [OperationContract]  
    bool RemoveAffiliate(string ID);  
    [OperationContract]  
    double RevenueCheckMonthly(ref string ID);  
    [OperationContract]  
    double RevenueCheckTotal(ref string ID);  
}  
```  
  
 Aby utworzyć klienta WCF dla usługi zdalnej, można użyć następującego przykładowego ciągu monikera.  
  
```
service4:mexAddress="http://servername/Affiliates/service.svc/mex",  
address="http://servername/Affiliates/service.svc",  
contract=IAffiliate, contractNamespace=http://Microsoft.ServiceModel.Demo,  
binding=WSHttpBinding_IAffiliate, bindingNamespace=http://tempuri.org/  
```  
  
 Podczas wykonywania aplikacji klienckiej Klient wykonuje `WS-MetadataExchange` przy użyciu podanej `mexAddress`. Może to zwrócić szczegóły dotyczące adresu, powiązania i kontraktu dla wielu usług. Parametry `address`, `contract`, `contractNamespace`, `binding` i `bindingNamespace` są używane do identyfikowania zamierzonej usługi. Po dopasowaniu tych parametrów moniker konstruuje klienta WCF przy użyciu odpowiedniej definicji kontraktu, a następnie wywołania można wykonać przy użyciu klienta WCF, podobnie jak w przypadku kontraktu o określonym typie.  
  
> [!NOTE]
> Jeśli moniker jest źle sformułowany lub usługa jest niedostępna, wywołanie do `GetObject` zwraca błąd informujący o nieprawidłowej składni. Jeśli wystąpi ten błąd, upewnij się, że moniker, którego używasz, jest poprawna i że usługa jest dostępna.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: rejestrowanie i konfigurowanie monikera usługi](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
