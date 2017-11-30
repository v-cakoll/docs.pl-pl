---
title: "Implementowanie kontraktów usług"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: implementing service contracts [WCF]
ms.assetid: aefb6f56-47e3-4f24-ab0a-9bc07bf9885f
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0b40b93b33e57bf15b7ab614405ccffa44abb8df
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-service-contracts"></a>Implementowanie kontraktów usług
Usługa jest klasa, która udostępnia funkcje dostępne dla klientów na jeden lub więcej punktów końcowych. Aby utworzyć usługę, należy zapisać klasy, która implementuje [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] kontraktu. Można w tym na dwa sposoby. Można zdefiniować kontrakt oddzielnie jako interfejs, a następnie utworzyć klasę, która implementuje ten interfejs. Alternatywnie można utworzyć klasy i kontraktu bezpośrednio przez umieszczenie <xref:System.ServiceModel.ServiceContractAttribute> atrybutu w samej klasy i <xref:System.ServiceModel.OperationContractAttribute> atrybutu w metodach dostępne dla klientów usługi.  
  
## <a name="creating-a-service-class"></a>Tworzenie klasy usługi  
 Poniżej przedstawiono przykład usługa, która implementuje `IMath` kontraktu, który został zdefiniowany oddzielnie.  
  
```csharp  
// Define the IMath contract.  
[ServiceContract]  
public interface IMath  
{  
    [OperationContract]   
    double Add(double A, double B);  
  
    [OperationContract]  
    double Multiply (double A, double B);  
}  
  
// Implement the IMath contract in the MathService class.  
public class MathService : IMath  
{  
    public double Add (double A, double B) { return A + B; }  
    public double Multiply (double A, double B) { return A * B; }  
}  
```  
  
 Alternatywnie usługa może bezpośrednio ujawnianie kontraktu. Poniżej przedstawiono przykład klasy usługi, która określa i wykonuje `MathService` kontraktu.  
  
```csharp  
// Define the MathService contract directly on the service class.  
[ServiceContract]  
class MathService  
{  
    [OperationContract]  
    public double Add(double A, double B) { return A + B; }  
    [OperationContract]  
    private double Multiply (double A, double B) { return A * B; }  
}  
```  
  
 Należy pamiętać, poprzedniego usług ujawnić różne kontrakty, ponieważ nazwy kontraktu różnią się. W pierwszym przypadku narażonych kontraktu o nazwie "`IMath`"podczas w drugim przypadku nosi nazwę kontraktu"`MathService`".  
  
 Kilka rzeczy można ustawić na usługi i operacji poziomy wdrożenia, takich jak współbieżności i wystąpień. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Projektowanie i Implementowanie usług](../../../docs/framework/wcf/designing-and-implementing-services.md).  
  
 Po wdrożeniu kontraktu usługi, należy utworzyć jeden lub więcej punktów końcowych dla usługi. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Przegląd tworzenia punktów końcowych](../../../docs/framework/wcf/endpoint-creation-overview.md). [!INCLUDE[crabout](../../../includes/crabout-md.md)]Uruchamianie usługi, zobacz [Hosting usług](../../../docs/framework/wcf/hosting-services.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Projektowanie i Implementowanie usług](../../../docs/framework/wcf/designing-and-implementing-services.md)  
 [Porady: Tworzenie usługi za pomocą klasy kontraktu](../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-contract-with-a-class.md)  
 [Porady: Tworzenie usługi przy użyciu interfejsu kontraktu](../../../docs/framework/wcf/feature-details/how-to-create-a-service-with-a-contract-interface.md)  
 [Określanie zachowania środowiska uruchomieniowego usługi](../../../docs/framework/wcf/specifying-service-run-time-behavior.md)
