---
title: Konfigurowanie serializacji w usłudze przepływu pracy
ms.date: 03/30/2017
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
ms.openlocfilehash: f894f2e044e35bb278f975ef2385a6b22a8bea49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185336"
---
# <a name="configuring-serialization-in-a-workflow-service"></a>Konfigurowanie serializacji w usłudze przepływu pracy
Usługi przepływu pracy są usługami Windows Communication Foundation (WCF), <xref:System.Runtime.Serialization.DataContractSerializer> a więc mają <xref:System.Xml.Serialization.XmlSerializer>możliwość korzystania z (domyślnie) lub . Podczas pisania usług niezwiązanych z przepływem pracy typ serializatora do użycia jest określony w umowie usługi lub operacji. Podczas tworzenia usług przepływu pracy WCF nie należy określać tych umów w kodzie, ale raczej są one generowane w czasie wykonywania przez wnioskowanie o kontrakt. Aby uzyskać więcej informacji na temat wnioskowania o kontraktach, zobacz [Korzystanie z kontraktów w przepływie pracy](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).  Serializator jest określony <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> przy użyciu właściwości. Można to ustawić w projektancie, jak pokazano na poniższej ilustracji.  
  
 ![Ustawianie właściwości SerializerOption w oknie Właściwości.](./media/configuring-serialization-in-a-workflow-service/setting-serializer-property.png)  
  
 Serializator można również ustawić w kodzie, jak pokazano w poniższym przykładzie,  
  
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
  
  Znane typy można określić również w usługach przepływu pracy. Aby uzyskać więcej informacji na temat znanych typów, zobacz [Znane typy kontraktu danych](data-contract-known-types.md). Znane typy można określić w projektancie lub w kodzie. Aby określić znane typy w projektancie, kliknij przycisk wielokropka obok właściwości <xref:System.ServiceModel.Activities.Receive> KnownTypes w oknie **Właściwości** dla działania, jak pokazano na poniższej ilustracji.
  
 ![Zrzut ekranu przedstawiający okno dialogowe właściwości Znane typy.](./media/configuring-serialization-in-a-workflow-service/known-types-properties.png)  
  
 Spowoduje to wyświetlenie Edytora kolekcji typów, który umożliwia wyszukiwanie i określanie znanych typów.  
  
 ![Zrzut ekranu przedstawiający Edytor kolekcji typów.](./media/configuring-serialization-in-a-workflow-service/type-collection-editor.gif)  
  
 Kliknij łącze **Dodaj nowy typ** i użyj listy rozwijanej, aby wybrać lub wyszukać typ, który ma być dodawany do kolekcji znanych typów. Aby określić znane typy w kodzie <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> należy użyć właściwości, jak pokazano w poniższym przykładzie.  
  
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
