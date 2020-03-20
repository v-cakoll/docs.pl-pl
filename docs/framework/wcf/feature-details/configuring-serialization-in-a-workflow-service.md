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
# <a name="configuring-serialization-in-a-workflow-service"></a><span data-ttu-id="cbdd2-102">Konfigurowanie serializacji w usłudze przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="cbdd2-102">Configuring Serialization in a Workflow Service</span></span>
<span data-ttu-id="cbdd2-103">Usługi przepływu pracy są usługami Windows Communication Foundation (WCF), <xref:System.Runtime.Serialization.DataContractSerializer> a więc mają <xref:System.Xml.Serialization.XmlSerializer>możliwość korzystania z (domyślnie) lub .</span><span class="sxs-lookup"><span data-stu-id="cbdd2-103">Workflow services are Windows Communication Foundation (WCF) services and so have the option of using either the <xref:System.Runtime.Serialization.DataContractSerializer> (the default) or the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="cbdd2-104">Podczas pisania usług niezwiązanych z przepływem pracy typ serializatora do użycia jest określony w umowie usługi lub operacji.</span><span class="sxs-lookup"><span data-stu-id="cbdd2-104">When writing non-workflow services the type of serializer to use is specified on the service or operation contract.</span></span> <span data-ttu-id="cbdd2-105">Podczas tworzenia usług przepływu pracy WCF nie należy określać tych umów w kodzie, ale raczej są one generowane w czasie wykonywania przez wnioskowanie o kontrakt.</span><span class="sxs-lookup"><span data-stu-id="cbdd2-105">When creating WCF workflow services you don’t specify these contracts in code, but rather they are generated at runtime by contract inference.</span></span> <span data-ttu-id="cbdd2-106">Aby uzyskać więcej informacji na temat wnioskowania o kontraktach, zobacz [Korzystanie z kontraktów w przepływie pracy](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="cbdd2-106">For more information about contract inference, see  [Using Contracts in Workflow](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span></span>  <span data-ttu-id="cbdd2-107">Serializator jest określony <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> przy użyciu właściwości.</span><span class="sxs-lookup"><span data-stu-id="cbdd2-107">The serializer is specified using the <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> property.</span></span> <span data-ttu-id="cbdd2-108">Można to ustawić w projektancie, jak pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="cbdd2-108">This can be set in the designer as shown in the following illustration.</span></span>  
  
 ![Ustawianie właściwości SerializerOption w oknie Właściwości.](./media/configuring-serialization-in-a-workflow-service/setting-serializer-property.png)  
  
 <span data-ttu-id="cbdd2-110">Serializator można również ustawić w kodzie, jak pokazano w poniższym przykładzie,</span><span class="sxs-lookup"><span data-stu-id="cbdd2-110">The serializer can also be set in code as shown in the following example,</span></span>  
  
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
  
  <span data-ttu-id="cbdd2-111">Znane typy można określić również w usługach przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="cbdd2-111">Known types can be specified on Workflow services as well.</span></span> <span data-ttu-id="cbdd2-112">Aby uzyskać więcej informacji na temat znanych typów, zobacz [Znane typy kontraktu danych](data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="cbdd2-112">For more information about Known Types, see [Data Contract Known Types](data-contract-known-types.md).</span></span> <span data-ttu-id="cbdd2-113">Znane typy można określić w projektancie lub w kodzie.</span><span class="sxs-lookup"><span data-stu-id="cbdd2-113">Known types can be specified in the designer or in code.</span></span> <span data-ttu-id="cbdd2-114">Aby określić znane typy w projektancie, kliknij przycisk wielokropka obok właściwości <xref:System.ServiceModel.Activities.Receive> KnownTypes w oknie **Właściwości** dla działania, jak pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="cbdd2-114">To specify known types in the designer, click the ellipsis button next to the KnownTypes property in the **Properties Window** for a <xref:System.ServiceModel.Activities.Receive> activity as shown in the following illustration.</span></span>
  
 ![Zrzut ekranu przedstawiający okno dialogowe właściwości Znane typy.](./media/configuring-serialization-in-a-workflow-service/known-types-properties.png)  
  
 <span data-ttu-id="cbdd2-116">Spowoduje to wyświetlenie Edytora kolekcji typów, który umożliwia wyszukiwanie i określanie znanych typów.</span><span class="sxs-lookup"><span data-stu-id="cbdd2-116">This displays the Type Collections Editor that allows you to search for and specify known types.</span></span>  
  
 ![Zrzut ekranu przedstawiający Edytor kolekcji typów.](./media/configuring-serialization-in-a-workflow-service/type-collection-editor.gif)  
  
 <span data-ttu-id="cbdd2-118">Kliknij łącze **Dodaj nowy typ** i użyj listy rozwijanej, aby wybrać lub wyszukać typ, który ma być dodawany do kolekcji znanych typów.</span><span class="sxs-lookup"><span data-stu-id="cbdd2-118">Click the **Add new type** link and use the drop down to select or search for a type to add to the known types collection.</span></span> <span data-ttu-id="cbdd2-119">Aby określić znane typy w kodzie <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> należy użyć właściwości, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="cbdd2-119">To specify known types in code use the <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> property as shown in the following example.</span></span>  
  
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
