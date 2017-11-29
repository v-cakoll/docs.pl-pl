---
title: "Konfigurowanie serializacji w usłudze przepływu pracy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9aa50b8e9f29e5dd14f0ff18d253943a73ef3a0b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="configuring-serialization-in-a-workflow-service"></a>Konfigurowanie serializacji w usłudze przepływu pracy
Usługi przepływu pracy są [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usług i dlatego mają możliwość za pomocą <xref:System.Runtime.Serialization.DataContractSerializer> (ustawienie domyślne) lub <xref:System.Xml.Serialization.XmlSerializer>. Podczas zapisywania bez przepływu pracy typu serializatora do użycia usług został określony w kontrakcie usługi lub operacji. Podczas tworzenia [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kontraktów usług przepływu pracy nie można określić w kodzie, ale raczej są one generowane w czasie wykonywania przez wnioskowania kontraktu. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Zwiń wnioskowania, zobacz [za pomocą kontraktów w przepływie pracy](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).  Serializator jest określona za pomocą <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> właściwości. To może można ustawić w projektancie, jak pokazano na poniższej ilustracji.  
  
 ![Ustawienia serializatora](../../../../docs/framework/wcf/feature-details/media/settingserialzier.png "SettingSerialzier")  
  
 Serializator również można ustawić w kodzie, jak pokazano w poniższym przykładzie  
  
```  
Receive approveExpense = new Receive  
            {  
                OperationName = "ApproveExpense",  
                CanCreateInstance = true,  
                ServiceContractName = "FinanceService",  
                SerializerOption = SerializerOption.DataContractSerializer,  
                Content = ReceiveContent.Create(new OutArgument<Expense>(expense))  
            };  
```  
  
 Znane typy można określać również usług przepływu pracy. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Znane typy zobacz [znane typy kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md). Znane typy można określić w Projektancie lub w kodzie. Aby określić znanych typów w projektancie, kliknij przycisk wielokropka obok właściwości element KnownTypes w oknie dialogowym właściwości <xref:System.ServiceModel.Activities.Receive> działania, jak pokazano na poniższej ilustracji.  
  
 ![Element KnownTypes właściwości](../../../../docs/framework/wcf/feature-details/media/knowntypes.png "element KnownTypes")  
  
 Spowoduje to wyświetlenie Edytor kolekcji typów, który umożliwia wyszukiwanie i określ znanych typów.  
  
 ![Dodawanie ze znanych typów](../../../../docs/framework/wcf/feature-details/media/typecollectionseditor.gif "TypeCollectionsEditor")  
  
 Kliknij przycisk **dodać nowy typ** link i użyć listy do wybierania lub wyszukiwania typu można dodać do kolekcji znanych typów. Aby określić znane typy używany kod <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> właściwości, jak pokazano w poniższym przykładzie.  
  
```  
Receive approveExpense = new Receive  
            {  
                OperationName = "ApproveExpense",  
                CanCreateInstance = true,  
                ServiceContractName = "FinanceService",  
                SerializerOption = SerializerOption.DataContractSerializer,  
                Content = ReceiveContent.Create(new OutArgument<Expense>(expense))  
            };  
            approveExpense.KnownTypes.Add(typeof(Travel));  
            approveExpense.KnownTypes.Add(typeof(Meal));  
```  
  
 Aby wyświetlić pełny przykład kodu przedstawiający Konfigurowanie serializacji dla usługi przepływów pracy zobacz [formatowania wiadomości w przepływie pracy usług](../../../../docs/framework/windows-workflow-foundation/samples/formatting-messages-in-workflow-services.md).
