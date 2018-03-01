---
title: Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder... ctor
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor
api_location:
- Microsoft.VisualStudio.Activities.dll
api_type:
- Assembly
ms.assetid: 6b44b13c-7a23-4df2-8f9f-45e2b1430002
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4c50d9754b71386e6809d46cd9666987a704fbf7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="microsoftvisualstudioactivitiesasrclientactivitybuilderctor"></a><span data-ttu-id="4bd66-102">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder... ctor</span><span class="sxs-lookup"><span data-stu-id="4bd66-102">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor</span></span>
<span data-ttu-id="4bd66-103">Tworzy wystąpienie [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md) klasy.</span><span class="sxs-lookup"><span data-stu-id="4bd66-103">Creates an instance of the [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md) class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bd66-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4bd66-104">Syntax</span></span>  
  
```csharp  
public ClientActivityBuilder(OperationDescription operationDescription, string configurationName, string proxyNamespace);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4bd66-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4bd66-105">Parameters</span></span>  
  
## <a name="parameter-values"></a><span data-ttu-id="4bd66-106">Wartości parametrów</span><span class="sxs-lookup"><span data-stu-id="4bd66-106">Parameter Values</span></span>  
 <span data-ttu-id="4bd66-107">*operationDescription*</span><span class="sxs-lookup"><span data-stu-id="4bd66-107">*operationDescription*</span></span>  
  
 <span data-ttu-id="4bd66-108">Opisuje operacji do wykonania działania przepływu pracy, który ma zostać wygenerowane, łącznie z nazwą operacji, zwracany typ i informacje o parametrze.</span><span class="sxs-lookup"><span data-stu-id="4bd66-108">Describes the operation to be performed in the workflow activity that is to be generated, including the operation name, return type, and parameter information.</span></span> <span data-ttu-id="4bd66-109">Wartość tego parametru nie może być **null**.</span><span class="sxs-lookup"><span data-stu-id="4bd66-109">The value of this parameter must not be **null**.</span></span> <span data-ttu-id="4bd66-110">Powinien on zawierać synchroniczne operacji, który używa kontraktu komunikatu i używa argumentu z jednej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="4bd66-110">It should describe a synchronous operation which uses a message contract and takes an argument with one message.</span></span> <span data-ttu-id="4bd66-111">Jeśli te warunki nie są spełnione, wynik środowiska wykonawczego przy użyciu konstruktora i inne metody tej klasy jest nieokreślona.</span><span class="sxs-lookup"><span data-stu-id="4bd66-111">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 <span data-ttu-id="4bd66-112">*configurationName*</span><span class="sxs-lookup"><span data-stu-id="4bd66-112">*configurationName*</span></span>  
  
 <span data-ttu-id="4bd66-113">Określa nazwę konfiguracji punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="4bd66-113">Specifies the endpoint configuration name.</span></span> <span data-ttu-id="4bd66-114">Wartość tego parametru nie może być albo **null** lub jest pusty.</span><span class="sxs-lookup"><span data-stu-id="4bd66-114">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="4bd66-115">Jeśli te warunki nie są spełnione, wynik środowiska wykonawczego przy użyciu konstruktora i inne metody tej klasy jest nieokreślona.</span><span class="sxs-lookup"><span data-stu-id="4bd66-115">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 <span data-ttu-id="4bd66-116">*proxyNamespace*</span><span class="sxs-lookup"><span data-stu-id="4bd66-116">*proxyNamespace*</span></span>  
  
 <span data-ttu-id="4bd66-117">Określa obszar nazw usługi dla operacji.</span><span class="sxs-lookup"><span data-stu-id="4bd66-117">Specifies the service namespace for the operation.</span></span> <span data-ttu-id="4bd66-118">Wartość tego parametru nie może być albo **null** lub jest pusty.</span><span class="sxs-lookup"><span data-stu-id="4bd66-118">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="4bd66-119">Jeśli te warunki nie są spełnione, wynik środowiska wykonawczego przy użyciu konstruktora i inne metody tej klasy jest nieokreślona.</span><span class="sxs-lookup"><span data-stu-id="4bd66-119">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bd66-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4bd66-120">See Also</span></span>  
 [<span data-ttu-id="4bd66-121">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span><span class="sxs-lookup"><span data-stu-id="4bd66-121">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md)
