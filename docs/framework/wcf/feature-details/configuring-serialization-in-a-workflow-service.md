---
title: Konfigurowanie serializacji w usłudze przepływu pracy
ms.date: 03/30/2017
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
ms.openlocfilehash: 63a5860bd428fd4ce7fe01d7901427c85b2d5609
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53154115"
---
# <a name="configuring-serialization-in-a-workflow-service"></a><span data-ttu-id="b1d35-102">Konfigurowanie serializacji w usłudze przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="b1d35-102">Configuring Serialization in a Workflow Service</span></span>
<span data-ttu-id="b1d35-103">Usługi przepływu pracy są usługi Windows Communication Foundation (WCF) i dlatego mają możliwość korzystania z jednej <xref:System.Runtime.Serialization.DataContractSerializer> (ustawienie domyślne) lub <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="b1d35-103">Workflow services are Windows Communication Foundation (WCF) services and so have the option of using either the <xref:System.Runtime.Serialization.DataContractSerializer> (the default) or the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="b1d35-104">Podczas pisania niezwiązanej z przepływem pracy typ serializator do użycia usług jest określona w kontrakcie usługi lub operacji.</span><span class="sxs-lookup"><span data-stu-id="b1d35-104">When writing non-workflow services the type of serializer to use is specified on the service or operation contract.</span></span> <span data-ttu-id="b1d35-105">Podczas tworzenia usługi przepływu pracy WCF nie określisz te kontraktów w kodzie, ale raczej są generowane w czasie wykonywania przez wnioskowania kontraktu.</span><span class="sxs-lookup"><span data-stu-id="b1d35-105">When creating WCF workflow services you don’t specify these contracts in code, but rather they are generated at runtime by contract inference.</span></span> <span data-ttu-id="b1d35-106">Aby uzyskać więcej informacji na temat umowy wnioskowania zobacz [za pomocą kontraktów w przepływie pracy](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="b1d35-106">For more information about contract inference, see  [Using Contracts in Workflow](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span></span>  <span data-ttu-id="b1d35-107">Serializator jest określony, przy użyciu <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="b1d35-107">The serializer is specified using the <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> property.</span></span> <span data-ttu-id="b1d35-108">To może można ustawić w projektancie, jak pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="b1d35-108">This can be set in the designer as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="b1d35-109">![Ustawienia serializatora](../../../../docs/framework/wcf/feature-details/media/settingserialzier.png "SettingSerialzier")</span><span class="sxs-lookup"><span data-stu-id="b1d35-109">![Setting the serializer](../../../../docs/framework/wcf/feature-details/media/settingserialzier.png "SettingSerialzier")</span></span>  
  
 <span data-ttu-id="b1d35-110">Serializator również można ustawić w kodzie, jak pokazano w poniższym przykładzie</span><span class="sxs-lookup"><span data-stu-id="b1d35-110">The serializer can also be set in code as shown in the following example,</span></span>  
  
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
  
 <span data-ttu-id="b1d35-111">Znane typy, można określić na również usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b1d35-111">Known types can be specified on Workflow services as well.</span></span> <span data-ttu-id="b1d35-112">Aby uzyskać więcej informacji na temat znanych typów zobacz [znane typy kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="b1d35-112">For more information about Known Types see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span> <span data-ttu-id="b1d35-113">Znane typy można określić za pomocą projektanta lub w kodzie.</span><span class="sxs-lookup"><span data-stu-id="b1d35-113">Known types can be specified in the designer or in code.</span></span> <span data-ttu-id="b1d35-114">Aby określić znanych typów w projektancie, kliknij przycisk wielokropka obok właściwości element KnownTypes w oknie dialogowym właściwości <xref:System.ServiceModel.Activities.Receive> działania, jak pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="b1d35-114">To specify known types in the designer, click the ellipsis button next to the KnownTypes property in the properties window for a <xref:System.ServiceModel.Activities.Receive> activity as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="b1d35-115">![Element KnownTypes właściwość](../../../../docs/framework/wcf/feature-details/media/knowntypes.png "element KnownTypes")</span><span class="sxs-lookup"><span data-stu-id="b1d35-115">![KnownTypes property](../../../../docs/framework/wcf/feature-details/media/knowntypes.png "KnownTypes")</span></span>  
  
 <span data-ttu-id="b1d35-116">Spowoduje to wyświetlenie Edytor kolekcji typów, która umożliwi Ci do wyszukiwania i określ znane typy.</span><span class="sxs-lookup"><span data-stu-id="b1d35-116">This will display the Type Collections Editor that will allow you to search for and specify known types.</span></span>  
  
 <span data-ttu-id="b1d35-117">![Dodawanie znane typy](../../../../docs/framework/wcf/feature-details/media/typecollectionseditor.gif "TypeCollectionsEditor")</span><span class="sxs-lookup"><span data-stu-id="b1d35-117">![Adding Known Types](../../../../docs/framework/wcf/feature-details/media/typecollectionseditor.gif "TypeCollectionsEditor")</span></span>  
  
 <span data-ttu-id="b1d35-118">Kliknij przycisk **dodać nowy typ** link i użyć menu rozwijanego wybierz opcję lub wyszukiwania dla typu można dodać do kolekcji znanych typów.</span><span class="sxs-lookup"><span data-stu-id="b1d35-118">Click the **Add new type** link and use the drop down to select or search for a type to add to the known types collection.</span></span> <span data-ttu-id="b1d35-119">Do określenia znanych typów w kodzie użyj <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> właściwości, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b1d35-119">To specify known types in code use the <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> property as shown in the following example.</span></span>  
  
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
