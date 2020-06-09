---
title: Konfigurowanie serializacji w usłudze przepływu pracy
ms.date: 03/30/2017
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
ms.openlocfilehash: 5076f3d377a656cb96909cf8df01591dc6ab72b7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597543"
---
# <a name="configuring-serialization-in-a-workflow-service"></a>Konfigurowanie serializacji w usłudze przepływu pracy
Usługi przepływu pracy są usługami Windows Communication Foundation (WCF) i dlatego mają opcję użycia <xref:System.Runtime.Serialization.DataContractSerializer> (wartość domyślna) lub <xref:System.Xml.Serialization.XmlSerializer> . Podczas pisania usług innych niż przepływ pracy typ serializatora do użycia jest określony w kontrakcie usługi lub operacji. Podczas tworzenia usług przepływu pracy WCF nie można określać tych kontraktów w kodzie, ale nie są one generowane w czasie wykonywania przez wnioskowanie kontraktu. Aby uzyskać więcej informacji o wnioskach o kontrakt, zobacz [Korzystanie z kontraktów w przepływie pracy](using-contracts-in-workflow.md).  Serializator jest określony za pomocą <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> właściwości. Tę wartość można ustawić w projektancie, jak pokazano na poniższej ilustracji.  
  
 ![Ustawianie właściwości SerializerOption w oknie właściwości.](./media/configuring-serialization-in-a-workflow-service/setting-serializer-property.png)  
  
 Serializator można także ustawić w kodzie, jak pokazano w poniższym przykładzie.  
  
```csharp  
Receive approveExpense = new Receive  
            {  
                OperationName = "ApproveExpense",  
                CanCreateInstance = true,  
                ServiceContractName = "FinanceService",  
                SerializerOption = SerializerOption.DataContractSerializer,  
                Content = ReceiveContent.Create(new OutArgument<Expense>(expense))  
            };  
```  
  
  Znane typy można także określić w usługach przepływu pracy. Aby uzyskać więcej informacji na temat znanych typów, zobacz [znane typy kontraktu danych](data-contract-known-types.md). Znane typy można określić w projektancie lub w kodzie. Aby określić znane typy w projektancie, kliknij przycisk wielokropka obok właściwości KnownTypes w **oknie właściwości** dla <xref:System.ServiceModel.Activities.Receive> działania, jak pokazano na poniższej ilustracji.
  
 ![Zrzut ekranu przedstawiający okno dialogowe właściwości KnownTypes.](./media/configuring-serialization-in-a-workflow-service/known-types-properties.png)  
  
 Spowoduje to wyświetlenie edytora kolekcji typów, który umożliwia wyszukiwanie i określanie znanych typów.  
  
 ![Zrzut ekranu edytora kolekcji typów.](./media/configuring-serialization-in-a-workflow-service/type-collection-editor.gif)  
  
 Kliknij link **Dodaj nowy typ** i Użyj listy rozwijanej, aby wybrać lub wyszukać typ, który ma zostać dodany do kolekcji znanych typów. Aby określić znane typy w kodzie, użyj <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> właściwości, jak pokazano w poniższym przykładzie.  
  
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
