---
title: "Porady: Użyj Moniker usługi Windows Communication Foundation bez rejestracji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: COM [WCF], service monikers without registration
ms.assetid: ee3cf5c0-24f0-4ae7-81da-73a60de4a1a8
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 18f575e9bae37b66526d7b61a641374266ba627b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-windows-communication-foundation-service-moniker-without-registration"></a>Porady: Użyj Moniker usługi Windows Communication Foundation bez rejestracji
Aby nawiązać połączenie i komunikować się z [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacja kliencka musi mieć szczegóły adresu usługi, Konfiguracja powiązania i kontraktu usługi.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Moniker usługi zwykle uzyskuje kontrakt wymagane przez wcześniejsze rejestrację typów wymaganego atrybutu, ale może być przypadki, w którym nie jest to możliwe. Zamiast rejestracji moniker można uzyskać definicję kontraktu w formularzu sieci Web Services Definition Language (WSDL) dokumentu, za pośrednictwem `wsdl` parametru lub za pomocą wymiany metadanych, korzystając ze `mexAddress` parametr.  
  
 Dzięki temu scenariuszy, takich jak dystrybucji arkusz kalkulacyjny programu Excel, gdzie niektórych wartości komórki są obliczane przy użyciu interakcje usługi sieci Web. W tym scenariuszu może nie być możliwe do zarejestrowania zestawu kontraktu usługi na wszystkich klientach, które może otworzyć dokumentu. `wsdl` Parametru lub `mexAddress` parametru zapewnia rozwiązanie niezależne.  
  
> [!NOTE]
>  Uwierzytelnianie wzajemne, należy użyć do ochrony przed żądań i odpowiedzi, modyfikowaniu lub fałszowania. W szczególności jest ważna w przypadku klientów mieć pewność, że punkt końcowy wymiany metadanych, który odpowiada jest zamierzone zaufany.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano sposób użycia moniker usługi z kontraktem MEX. Usługi za pomocą następujących kontrakt jest narażony na wsHttpBinding.  
  
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
  
 Aby utworzyć [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta dla usługi zdalnej może służyć następujący przykład ciąg krótkiej nazwy.  
  
```  
service4:mexAddress="http://servername/Affiliates/service.svc/mex",  
address="http://servername/Affiliates/service.svc",  
contract=IAffiliate, contractNamespace=http://Microsoft.ServiceModel.Demo,  
binding=WSHttpBinding_IAffiliate, bindingNamespace=http://tempuri.org/  
```  
  
 Podczas wykonywania aplikacji klienckiej, klient wykonuje `WS-MetadataExchange` się za pomocą podanych `mexAddress`. Może to zwrócić address, binding i szczegóły umowy wielu usług. `address`, `contract`, `contractNamespace`, `binding` i `bindingNamespace` parametry są używane do identyfikowania usługi zamierzone. Po dopasowane tych parametrów, tworzy moniker [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta z definicję kontraktu odpowiednie i wywołania można następnie utworzone za pomocą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, jak w przypadku typu kontraktu.  
  
> [!NOTE]
>  Jeśli krótka nazwa jest nieprawidłowo sformułowany lub usługa jest niedostępna, wywołanie `GetObject` zwraca błąd informujący o tym "Nieprawidłowa składnia". Jeśli zostanie wyświetlony ten błąd, upewnij się, krótkiej nazwy, którego używasz, jest poprawny i usługa jest dostępna.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: rejestrowanie i konfigurowanie monikera usługi](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
