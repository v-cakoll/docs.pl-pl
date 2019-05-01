---
title: 'Instrukcje: używanie krótkiej nazwy programu Windows Communication Foundation bez rejestracji'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], service monikers without registration
ms.assetid: ee3cf5c0-24f0-4ae7-81da-73a60de4a1a8
ms.openlocfilehash: be4798663d0b39301ec496df45a4a7a5bf9c88e5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61918593"
---
# <a name="how-to-use-the-windows-communication-foundation-service-moniker-without-registration"></a>Instrukcje: używanie krótkiej nazwy programu Windows Communication Foundation bez rejestracji
Aby nawiązać połączenie i komunikować się z usługą Windows Communication Foundation (WCF), aplikacja klienta WCF musi mieć adres usługi, Konfiguracja powiązania i kontraktu usługi.  
  
 Monikera programu WCF zwykle uzyskuje kontrakt wymagane przez wcześniejsze rejestrację typów wymaganego atrybutu, ale może być przypadki, w którym nie jest to możliwe. Zamiast rejestracji, moniker można uzyskać definicję kontraktu w postaci dokumentów sieci Web Services Definition Language (WSDL), za pośrednictwem `wsdl` parametru lub za pośrednictwem wymiany metadanych, korzystając ze `mexAddress` parametr.  
  
 Umożliwia to obsługę scenariuszy, takich jak dystrybucja arkusz kalkulacyjny programu Excel, gdzie niektóre komórki wartościami są obliczane za pośrednictwem interakcje usługi sieci Web. W tym scenariuszu może być nie można zarejestrować zestawu kontraktu usługi na wszystkich klientach, które może otworzyć dokumentu. `wsdl` Parametru lub `mexAddress` parametr umożliwia samodzielne rozwiązanie.  
  
> [!NOTE]
>  Wzajemnego uwierzytelniania musi być używana do ochrony przed żądań i odpowiedzi, modyfikowaniu lub fałszowanie adresów. Ściślej mówiąc jest ważne dla klientów mieć pewność, że punkt końcowy wymiany metadanych, który odpowiada jest zamierzony zaufany.  
  
## <a name="example"></a>Przykład  
 Ten przykład przedstawia użycie monikera za pomocą kontraktu wymiany Metadanych. Usługi za pomocą następujących kontraktu jest uwidaczniany za pomocą wsHttpBinding.  
  
```  
using System.ServiceModel;  
  
...  
  
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
  
 Aby utworzyć klienta WCF usługi zdalnej następujący ciąg monikera przykład można użyć.  
  
```  
service4:mexAddress="http://servername/Affiliates/service.svc/mex",  
address="http://servername/Affiliates/service.svc",  
contract=IAffiliate, contractNamespace=http://Microsoft.ServiceModel.Demo,  
binding=WSHttpBinding_IAffiliate, bindingNamespace=http://tempuri.org/  
```  
  
 Podczas wykonywania aplikacji klienckiej, klient wykonuje `WS-MetadataExchange` z dostępnego `mexAddress`. To może zwrócić adres, powiązania i podrobnosti o kontraktu dla wielu usług. `address`, `contract`, `contractNamespace`, `binding` i `bindingNamespace` parametry są używane do identyfikowania usługi zamierzone. Po dopasowane tych parametrów moniker tworzy klienta programu WCF za pomocą definicję kontraktu odpowiednie, a następnie wywołań za pomocą klienta WCF, podobnie jak w przypadku wpisane kontraktu.  
  
> [!NOTE]
>  Jeśli moniker jest źle sformułowany lub jeśli usługa jest niedostępna, wywołanie `GetObject` zwraca błąd informujący o "Nieprawidłowa składnia". Jeśli zostanie wyświetlony ten błąd, upewnij się, moniker elementu, którego używasz jest poprawna i ta usługa jest dostępna.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Rejestrowanie i konfigurowanie monikera usługi](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
