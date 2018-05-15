---
title: Konfigurowanie serializacji w usłudze przepływu pracy
ms.date: 03/30/2017
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
ms.openlocfilehash: 74d9a812b9e0cd51a401fa3526c947d52413807a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="configuring-serialization-in-a-workflow-service"></a><span data-ttu-id="30eda-102">Konfigurowanie serializacji w usłudze przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="30eda-102">Configuring Serialization in a Workflow Service</span></span>
<span data-ttu-id="30eda-103">Usługi przepływu pracy są usług Windows Communication Foundation (WCF), więc za pomocą opcji <xref:System.Runtime.Serialization.DataContractSerializer> (ustawienie domyślne) lub <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="30eda-103">Workflow services are Windows Communication Foundation (WCF) services and so have the option of using either the <xref:System.Runtime.Serialization.DataContractSerializer> (the default) or the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="30eda-104">Podczas zapisywania bez przepływu pracy typu serializatora do użycia usług został określony w kontrakcie usługi lub operacji.</span><span class="sxs-lookup"><span data-stu-id="30eda-104">When writing non-workflow services the type of serializer to use is specified on the service or operation contract.</span></span> <span data-ttu-id="30eda-105">Podczas tworzenia usługi przepływu pracy WCF w kodzie braku określenia tych umów, ale raczej są one generowane w czasie wykonywania przez wnioskowania kontraktu.</span><span class="sxs-lookup"><span data-stu-id="30eda-105">When creating WCF workflow services you don’t specify these contracts in code, but rather they are generated at runtime by contract inference.</span></span> <span data-ttu-id="30eda-106">Aby uzyskać więcej informacji na temat wnioskowania kontraktu, zobacz [za pomocą kontraktów w przepływie pracy](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="30eda-106">For more information about contract inference, see  [Using Contracts in Workflow](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span></span>  <span data-ttu-id="30eda-107">Serializator jest określona za pomocą <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="30eda-107">The serializer is specified using the <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> property.</span></span> <span data-ttu-id="30eda-108">To może można ustawić w projektancie, jak pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="30eda-108">This can be set in the designer as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="30eda-109">![Ustawienia serializatora](../../../../docs/framework/wcf/feature-details/media/settingserialzier.png "SettingSerialzier")</span><span class="sxs-lookup"><span data-stu-id="30eda-109">![Setting the serializer](../../../../docs/framework/wcf/feature-details/media/settingserialzier.png "SettingSerialzier")</span></span>  
  
 <span data-ttu-id="30eda-110">Serializator również można ustawić w kodzie, jak pokazano w poniższym przykładzie</span><span class="sxs-lookup"><span data-stu-id="30eda-110">The serializer can also be set in code as shown in the following example,</span></span>  
  
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
  
 <span data-ttu-id="30eda-111">Znane typy można określać również usług przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="30eda-111">Known types can be specified on Workflow services as well.</span></span> <span data-ttu-id="30eda-112">Aby uzyskać więcej informacji na temat znanych typów zobacz [znane typy kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="30eda-112">For more information about Known Types see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span> <span data-ttu-id="30eda-113">Znane typy można określić w Projektancie lub w kodzie.</span><span class="sxs-lookup"><span data-stu-id="30eda-113">Known types can be specified in the designer or in code.</span></span> <span data-ttu-id="30eda-114">Aby określić znanych typów w projektancie, kliknij przycisk wielokropka obok właściwości element KnownTypes w oknie dialogowym właściwości <xref:System.ServiceModel.Activities.Receive> działania, jak pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="30eda-114">To specify known types in the designer, click the ellipsis button next to the KnownTypes property in the properties window for a <xref:System.ServiceModel.Activities.Receive> activity as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="30eda-115">![Element KnownTypes właściwości](../../../../docs/framework/wcf/feature-details/media/knowntypes.png "element KnownTypes")</span><span class="sxs-lookup"><span data-stu-id="30eda-115">![KnownTypes property](../../../../docs/framework/wcf/feature-details/media/knowntypes.png "KnownTypes")</span></span>  
  
 <span data-ttu-id="30eda-116">Spowoduje to wyświetlenie Edytor kolekcji typów, który umożliwia wyszukiwanie i określ znanych typów.</span><span class="sxs-lookup"><span data-stu-id="30eda-116">This will display the Type Collections Editor that will allow you to search for and specify known types.</span></span>  
  
 <span data-ttu-id="30eda-117">![Dodawanie ze znanych typów](../../../../docs/framework/wcf/feature-details/media/typecollectionseditor.gif "TypeCollectionsEditor")</span><span class="sxs-lookup"><span data-stu-id="30eda-117">![Adding Known Types](../../../../docs/framework/wcf/feature-details/media/typecollectionseditor.gif "TypeCollectionsEditor")</span></span>  
  
 <span data-ttu-id="30eda-118">Kliknij przycisk **dodać nowy typ** link i użyć listy do wybierania lub wyszukiwania typu można dodać do kolekcji znanych typów.</span><span class="sxs-lookup"><span data-stu-id="30eda-118">Click the **Add new type** link and use the drop down to select or search for a type to add to the known types collection.</span></span> <span data-ttu-id="30eda-119">Aby określić znane typy używany kod <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> właściwości, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="30eda-119">To specify known types in code use the <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> property as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="30eda-120">Aby wyświetlić pełny przykład kodu przedstawiający Konfigurowanie serializacji dla usługi przepływów pracy zobacz [formatowania wiadomości w przepływie pracy usług](../../../../docs/framework/windows-workflow-foundation/samples/formatting-messages-in-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="30eda-120">To see a complete code example showing how to configure serialization for a workflow service see [Formatting messages in Workflow Services](../../../../docs/framework/windows-workflow-foundation/samples/formatting-messages-in-workflow-services.md).</span></span>
