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
# <a name="configuring-serialization-in-a-workflow-service"></a><span data-ttu-id="f5a4f-102">Konfigurowanie serializacji w usłudze przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="f5a4f-102">Configuring Serialization in a Workflow Service</span></span>
<span data-ttu-id="f5a4f-103">Usługi przepływu pracy są usługami Windows Communication Foundation (WCF) i dlatego mają opcję użycia <xref:System.Runtime.Serialization.DataContractSerializer> (wartość domyślna) lub <xref:System.Xml.Serialization.XmlSerializer> .</span><span class="sxs-lookup"><span data-stu-id="f5a4f-103">Workflow services are Windows Communication Foundation (WCF) services and so have the option of using either the <xref:System.Runtime.Serialization.DataContractSerializer> (the default) or the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="f5a4f-104">Podczas pisania usług innych niż przepływ pracy typ serializatora do użycia jest określony w kontrakcie usługi lub operacji.</span><span class="sxs-lookup"><span data-stu-id="f5a4f-104">When writing non-workflow services the type of serializer to use is specified on the service or operation contract.</span></span> <span data-ttu-id="f5a4f-105">Podczas tworzenia usług przepływu pracy WCF nie można określać tych kontraktów w kodzie, ale nie są one generowane w czasie wykonywania przez wnioskowanie kontraktu.</span><span class="sxs-lookup"><span data-stu-id="f5a4f-105">When creating WCF workflow services you don’t specify these contracts in code, but rather they are generated at runtime by contract inference.</span></span> <span data-ttu-id="f5a4f-106">Aby uzyskać więcej informacji o wnioskach o kontrakt, zobacz [Korzystanie z kontraktów w przepływie pracy](using-contracts-in-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="f5a4f-106">For more information about contract inference, see  [Using Contracts in Workflow](using-contracts-in-workflow.md).</span></span>  <span data-ttu-id="f5a4f-107">Serializator jest określony za pomocą <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f5a4f-107">The serializer is specified using the <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> property.</span></span> <span data-ttu-id="f5a4f-108">Tę wartość można ustawić w projektancie, jak pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="f5a4f-108">This can be set in the designer as shown in the following illustration.</span></span>  
  
 ![Ustawianie właściwości SerializerOption w oknie właściwości.](./media/configuring-serialization-in-a-workflow-service/setting-serializer-property.png)  
  
 <span data-ttu-id="f5a4f-110">Serializator można także ustawić w kodzie, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f5a4f-110">The serializer can also be set in code as shown in the following example,</span></span>  
  
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
  
  <span data-ttu-id="f5a4f-111">Znane typy można także określić w usługach przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="f5a4f-111">Known types can be specified on Workflow services as well.</span></span> <span data-ttu-id="f5a4f-112">Aby uzyskać więcej informacji na temat znanych typów, zobacz [znane typy kontraktu danych](data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="f5a4f-112">For more information about Known Types, see [Data Contract Known Types](data-contract-known-types.md).</span></span> <span data-ttu-id="f5a4f-113">Znane typy można określić w projektancie lub w kodzie.</span><span class="sxs-lookup"><span data-stu-id="f5a4f-113">Known types can be specified in the designer or in code.</span></span> <span data-ttu-id="f5a4f-114">Aby określić znane typy w projektancie, kliknij przycisk wielokropka obok właściwości KnownTypes w **oknie właściwości** dla <xref:System.ServiceModel.Activities.Receive> działania, jak pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="f5a4f-114">To specify known types in the designer, click the ellipsis button next to the KnownTypes property in the **Properties Window** for a <xref:System.ServiceModel.Activities.Receive> activity as shown in the following illustration.</span></span>
  
 ![Zrzut ekranu przedstawiający okno dialogowe właściwości KnownTypes.](./media/configuring-serialization-in-a-workflow-service/known-types-properties.png)  
  
 <span data-ttu-id="f5a4f-116">Spowoduje to wyświetlenie edytora kolekcji typów, który umożliwia wyszukiwanie i określanie znanych typów.</span><span class="sxs-lookup"><span data-stu-id="f5a4f-116">This displays the Type Collections Editor that allows you to search for and specify known types.</span></span>  
  
 ![Zrzut ekranu edytora kolekcji typów.](./media/configuring-serialization-in-a-workflow-service/type-collection-editor.gif)  
  
 <span data-ttu-id="f5a4f-118">Kliknij link **Dodaj nowy typ** i Użyj listy rozwijanej, aby wybrać lub wyszukać typ, który ma zostać dodany do kolekcji znanych typów.</span><span class="sxs-lookup"><span data-stu-id="f5a4f-118">Click the **Add new type** link and use the drop down to select or search for a type to add to the known types collection.</span></span> <span data-ttu-id="f5a4f-119">Aby określić znane typy w kodzie, użyj <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> właściwości, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f5a4f-119">To specify known types in code use the <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> property as shown in the following example.</span></span>  
  
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
