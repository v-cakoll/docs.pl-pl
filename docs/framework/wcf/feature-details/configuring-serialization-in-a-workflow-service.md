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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 78f963f61c7ec67d6104a90c047ce78b0470568a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="configuring-serialization-in-a-workflow-service"></a><span data-ttu-id="227b8-102">Konfigurowanie serializacji w usłudze przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="227b8-102">Configuring Serialization in a Workflow Service</span></span>
<span data-ttu-id="227b8-103">Usługi przepływu pracy są [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usług i dlatego mają możliwość za pomocą <xref:System.Runtime.Serialization.DataContractSerializer> (ustawienie domyślne) lub <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="227b8-103">Workflow services are [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services and so have the option of using either the <xref:System.Runtime.Serialization.DataContractSerializer> (the default) or the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="227b8-104">Podczas zapisywania bez przepływu pracy typu serializatora do użycia usług został określony w kontrakcie usługi lub operacji.</span><span class="sxs-lookup"><span data-stu-id="227b8-104">When writing non-workflow services the type of serializer to use is specified on the service or operation contract.</span></span> <span data-ttu-id="227b8-105">Podczas tworzenia [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kontraktów usług przepływu pracy nie można określić w kodzie, ale raczej są one generowane w czasie wykonywania przez wnioskowania kontraktu.</span><span class="sxs-lookup"><span data-stu-id="227b8-105">When creating [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] workflow services you don’t specify these contracts in code, but rather they are generated at runtime by contract inference.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="227b8-106">Zwiń wnioskowania, zobacz [za pomocą kontraktów w przepływie pracy](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="227b8-106"> contract inference, see  [Using Contracts in Workflow](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span></span>  <span data-ttu-id="227b8-107">Serializator jest określona za pomocą <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="227b8-107">The serializer is specified using the <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> property.</span></span> <span data-ttu-id="227b8-108">To może można ustawić w projektancie, jak pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="227b8-108">This can be set in the designer as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="227b8-109">![Ustawienia serializatora](../../../../docs/framework/wcf/feature-details/media/settingserialzier.png "SettingSerialzier")</span><span class="sxs-lookup"><span data-stu-id="227b8-109">![Setting the serializer](../../../../docs/framework/wcf/feature-details/media/settingserialzier.png "SettingSerialzier")</span></span>  
  
 <span data-ttu-id="227b8-110">Serializator również można ustawić w kodzie, jak pokazano w poniższym przykładzie</span><span class="sxs-lookup"><span data-stu-id="227b8-110">The serializer can also be set in code as shown in the following example,</span></span>  
  
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
  
 <span data-ttu-id="227b8-111">Znane typy można określać również usług przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="227b8-111">Known types can be specified on Workflow services as well.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="227b8-112">Znane typy zobacz [znane typy kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="227b8-112"> Known Types see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span> <span data-ttu-id="227b8-113">Znane typy można określić w Projektancie lub w kodzie.</span><span class="sxs-lookup"><span data-stu-id="227b8-113">Known types can be specified in the designer or in code.</span></span> <span data-ttu-id="227b8-114">Aby określić znanych typów w projektancie, kliknij przycisk wielokropka obok właściwości element KnownTypes w oknie dialogowym właściwości <xref:System.ServiceModel.Activities.Receive> działania, jak pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="227b8-114">To specify known types in the designer, click the ellipsis button next to the KnownTypes property in the properties window for a <xref:System.ServiceModel.Activities.Receive> activity as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="227b8-115">![Element KnownTypes właściwości](../../../../docs/framework/wcf/feature-details/media/knowntypes.png "element KnownTypes")</span><span class="sxs-lookup"><span data-stu-id="227b8-115">![KnownTypes property](../../../../docs/framework/wcf/feature-details/media/knowntypes.png "KnownTypes")</span></span>  
  
 <span data-ttu-id="227b8-116">Spowoduje to wyświetlenie Edytor kolekcji typów, który umożliwia wyszukiwanie i określ znanych typów.</span><span class="sxs-lookup"><span data-stu-id="227b8-116">This will display the Type Collections Editor that will allow you to search for and specify known types.</span></span>  
  
 <span data-ttu-id="227b8-117">![Dodawanie ze znanych typów](../../../../docs/framework/wcf/feature-details/media/typecollectionseditor.gif "TypeCollectionsEditor")</span><span class="sxs-lookup"><span data-stu-id="227b8-117">![Adding Known Types](../../../../docs/framework/wcf/feature-details/media/typecollectionseditor.gif "TypeCollectionsEditor")</span></span>  
  
 <span data-ttu-id="227b8-118">Kliknij przycisk **dodać nowy typ** link i użyć listy do wybierania lub wyszukiwania typu można dodać do kolekcji znanych typów.</span><span class="sxs-lookup"><span data-stu-id="227b8-118">Click the **Add new type** link and use the drop down to select or search for a type to add to the known types collection.</span></span> <span data-ttu-id="227b8-119">Aby określić znane typy używany kod <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> właściwości, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="227b8-119">To specify known types in code use the <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> property as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="227b8-120">Aby wyświetlić pełny przykład kodu przedstawiający Konfigurowanie serializacji dla usługi przepływów pracy zobacz [formatowania wiadomości w przepływie pracy usług](../../../../docs/framework/windows-workflow-foundation/samples/formatting-messages-in-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="227b8-120">To see a complete code example showing how to configure serialization for a workflow service see [Formatting messages in Workflow Services](../../../../docs/framework/windows-workflow-foundation/samples/formatting-messages-in-workflow-services.md).</span></span>
