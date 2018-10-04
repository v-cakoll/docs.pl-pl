---
title: Konfigurowanie serializacji w usłudze przepływu pracy
ms.date: 03/30/2017
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
ms.openlocfilehash: 67d8807e5ff45db2e8662586861d969e14ceaa8d
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48583713"
---
# <a name="configuring-serialization-in-a-workflow-service"></a>Konfigurowanie serializacji w usłudze przepływu pracy
Usługi przepływu pracy są usługi Windows Communication Foundation (WCF) i dlatego mają możliwość korzystania z jednej <xref:System.Runtime.Serialization.DataContractSerializer> (ustawienie domyślne) lub <xref:System.Xml.Serialization.XmlSerializer>. Podczas pisania niezwiązanej z przepływem pracy typ serializator do użycia usług jest określona w kontrakcie usługi lub operacji. Podczas tworzenia usługi przepływu pracy WCF nie określisz te kontraktów w kodzie, ale raczej są generowane w czasie wykonywania przez wnioskowania kontraktu. Aby uzyskać więcej informacji na temat umowy wnioskowania zobacz [za pomocą kontraktów w przepływie pracy](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).  Serializator jest określony, przy użyciu <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> właściwości. To może można ustawić w projektancie, jak pokazano na poniższej ilustracji.  
  
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
  
 Znane typy, można określić na również usługi przepływu pracy. Aby uzyskać więcej informacji na temat znanych typów zobacz [znane typy kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md). Znane typy można określić za pomocą projektanta lub w kodzie. Aby określić znanych typów w projektancie, kliknij przycisk wielokropka obok właściwości element KnownTypes w oknie dialogowym właściwości <xref:System.ServiceModel.Activities.Receive> działania, jak pokazano na poniższej ilustracji.  
  
 ![Element KnownTypes właściwość](../../../../docs/framework/wcf/feature-details/media/knowntypes.png "element KnownTypes")  
  
 Spowoduje to wyświetlenie Edytor kolekcji typów, która umożliwi Ci do wyszukiwania i określ znane typy.  
  
 ![Dodawanie znane typy](../../../../docs/framework/wcf/feature-details/media/typecollectionseditor.gif "TypeCollectionsEditor")  
  
 Kliknij przycisk **dodać nowy typ** link i użyć menu rozwijanego wybierz opcję lub wyszukiwania dla typu można dodać do kolekcji znanych typów. Do określenia znanych typów w kodzie użyj <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> właściwości, jak pokazano w poniższym przykładzie.  
  
```csharp
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
