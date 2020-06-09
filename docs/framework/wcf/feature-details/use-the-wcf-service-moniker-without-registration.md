---
title: 'Instrukcje: używanie monikera programu Windows Communication Foundation bez rejestracji'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], service monikers without registration
ms.assetid: ee3cf5c0-24f0-4ae7-81da-73a60de4a1a8
ms.openlocfilehash: f69314948a0e0a69e49ec148f94572f17d0b8e3c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595053"
---
# <a name="how-to-use-the-windows-communication-foundation-service-moniker-without-registration"></a>Instrukcje: używanie monikera programu Windows Communication Foundation bez rejestracji
Aby nawiązać połączenie z usługą Windows Communication Foundation (WCF) i komunikować się z nią, aplikacja kliencka programu WCF musi mieć szczegóły dotyczące adresu usługi, konfiguracji powiązania i kontraktu usługi.  
  
 Moniker usługi WCF zwykle uzyskuje wymagany kontrakt za pomocą wcześniejszej rejestracji wymaganych typów atrybutów, ale mogą wystąpić sytuacje, w których nie jest to możliwe. W miejscu rejestracji moniker może uzyskać definicję kontraktu w formie dokumentu języka definicji usług sieci Web (WSDL), poprzez użycie `wsdl` parametru lub za pomocą wymiany metadanych przy użyciu `mexAddress` parametru.  
  
 Pozwala to na takie scenariusze, jak dystrybucja arkusza kalkulacyjnego programu Excel, w którym niektóre wartości komórek są obliczane za pomocą interakcji usługi sieci Web. W tym scenariuszu może nie być możliwe zarejestrowanie zestawu kontraktu usługi na wszystkich klientach, który może otworzyć ten dokument. `wsdl`Parametr lub `mexAddress` parametr włącza samodzielne rozwiązanie.  
  
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
  
 Podczas wykonywania aplikacji klienckiej Klient wykonuje `WS-MetadataExchange` przy użyciu podanej wartości `mexAddress` . Może to zwrócić szczegóły dotyczące adresu, powiązania i kontraktu dla wielu usług. `address`Parametry, `contract` , `contractNamespace` i służą `binding` `bindingNamespace` do identyfikowania zamierzonej usługi. Po dopasowaniu tych parametrów moniker konstruuje klienta WCF przy użyciu odpowiedniej definicji kontraktu, a następnie wywołania można wykonać przy użyciu klienta WCF, podobnie jak w przypadku kontraktu o określonym typie.  
  
> [!NOTE]
> Jeśli moniker jest źle sformułowany lub usługa jest niedostępna, wywołanie do `GetObject` zwraca błąd mówiąc "Nieprawidłowa składnia". Jeśli wystąpi ten błąd, upewnij się, że moniker, którego używasz, jest poprawna i że usługa jest dostępna.  
  
## <a name="see-also"></a>Zobacz też

- [Instrukcje: rejestrowanie i konfigurowanie monikera usługi](how-to-register-and-configure-a-service-moniker.md)
