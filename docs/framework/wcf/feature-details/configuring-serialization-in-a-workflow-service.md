---
title: Konfigurowanie serializacji w usłudze przepływu pracy
ms.date: 03/30/2017
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
ms.openlocfilehash: 0e0f03a30aa8e8679cf849aa75948e0bc2314fe5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857510"
---
# <a name="configuring-serialization-in-a-workflow-service"></a><span data-ttu-id="0a037-102">Konfigurowanie serializacji w usłudze przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="0a037-102">Configuring Serialization in a Workflow Service</span></span>
<span data-ttu-id="0a037-103">Usługi przepływu pracy są usługi Windows Communication Foundation (WCF) i dlatego mają możliwość korzystania z jednej <xref:System.Runtime.Serialization.DataContractSerializer> (ustawienie domyślne) lub <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="0a037-103">Workflow services are Windows Communication Foundation (WCF) services and so have the option of using either the <xref:System.Runtime.Serialization.DataContractSerializer> (the default) or the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="0a037-104">Podczas pisania niezwiązanej z przepływem pracy typ serializator do użycia usług jest określona w kontrakcie usługi lub operacji.</span><span class="sxs-lookup"><span data-stu-id="0a037-104">When writing non-workflow services the type of serializer to use is specified on the service or operation contract.</span></span> <span data-ttu-id="0a037-105">Podczas tworzenia usługi przepływu pracy WCF nie określisz te kontraktów w kodzie, ale raczej są generowane w czasie wykonywania przez wnioskowania kontraktu.</span><span class="sxs-lookup"><span data-stu-id="0a037-105">When creating WCF workflow services you don’t specify these contracts in code, but rather they are generated at runtime by contract inference.</span></span> <span data-ttu-id="0a037-106">Aby uzyskać więcej informacji na temat umowy wnioskowania zobacz [za pomocą kontraktów w przepływie pracy](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="0a037-106">For more information about contract inference, see  [Using Contracts in Workflow](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span></span>  <span data-ttu-id="0a037-107">Serializator jest określony, przy użyciu <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="0a037-107">The serializer is specified using the <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> property.</span></span> <span data-ttu-id="0a037-108">To może można ustawić w projektancie, jak pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="0a037-108">This can be set in the designer as shown in the following illustration.</span></span>  
  
 ![Ustawianie właściwości SerializerOption w oknie dialogowym właściwości.](./media/configuring-serialization-in-a-workflow-service/setting-serializer-property.png)  
  
 <span data-ttu-id="0a037-110">Serializator również można ustawić w kodzie, jak pokazano w poniższym przykładzie</span><span class="sxs-lookup"><span data-stu-id="0a037-110">The serializer can also be set in code as shown in the following example,</span></span>  
  
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
  
  <span data-ttu-id="0a037-111">Znane typy, można określić na również usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="0a037-111">Known types can be specified on Workflow services as well.</span></span> <span data-ttu-id="0a037-112">Aby uzyskać więcej informacji na temat znanych typów, zobacz [znane typy kontraktu danych](data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="0a037-112">For more information about Known Types, see [Data Contract Known Types](data-contract-known-types.md).</span></span> <span data-ttu-id="0a037-113">Znane typy można określić za pomocą projektanta lub w kodzie.</span><span class="sxs-lookup"><span data-stu-id="0a037-113">Known types can be specified in the designer or in code.</span></span> <span data-ttu-id="0a037-114">Aby określić znanych typów w projektancie, kliknij przycisk wielokropka obok właściwości element KnownTypes w **okno właściwości** dla <xref:System.ServiceModel.Activities.Receive> działania, jak pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="0a037-114">To specify known types in the designer, click the ellipsis button next to the KnownTypes property in the **Properties Window** for a <xref:System.ServiceModel.Activities.Receive> activity as shown in the following illustration.</span></span>   
  
 ![Zrzut ekranu przedstawiający okno dialogowe właściwości element KnownTypes.](./media/configuring-serialization-in-a-workflow-service/known-types-properties.png)  
  
 <span data-ttu-id="0a037-116">Spowoduje to wyświetlenie Edytor kolekcji typów, która umożliwia wyszukiwanie i określanie znanych typów.</span><span class="sxs-lookup"><span data-stu-id="0a037-116">This displays the Type Collections Editor that allows you to search for and specify known types.</span></span>  
  
 ![Zrzut ekranu przedstawiający edytor kolekcji typów.](./media/configuring-serialization-in-a-workflow-service/type-collection-editor.gif)  
  
 <span data-ttu-id="0a037-118">Kliknij przycisk **dodać nowy typ** link i użyć menu rozwijanego wybierz opcję lub wyszukiwania dla typu można dodać do kolekcji znanych typów.</span><span class="sxs-lookup"><span data-stu-id="0a037-118">Click the **Add new type** link and use the drop down to select or search for a type to add to the known types collection.</span></span> <span data-ttu-id="0a037-119">Do określenia znanych typów w kodzie użyj <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> właściwości, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="0a037-119">To specify known types in code use the <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> property as shown in the following example.</span></span>  
  
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
