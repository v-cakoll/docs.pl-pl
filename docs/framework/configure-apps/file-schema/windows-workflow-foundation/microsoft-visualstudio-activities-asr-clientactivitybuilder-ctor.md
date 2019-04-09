---
title: Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor
ms.date: 03/30/2017
ms.topic: reference
api_name:
- Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor
api_location:
- Microsoft.VisualStudio.Activities.dll
api_type:
- Assembly
ms.assetid: 6b44b13c-7a23-4df2-8f9f-45e2b1430002
ms.openlocfilehash: 0ce9be30182f9181bcb6449529d9b9796aadbc2b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59133539"
---
# <a name="microsoftvisualstudioactivitiesasrclientactivitybuilderctor"></a><span data-ttu-id="0bac8-102">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor</span><span class="sxs-lookup"><span data-stu-id="0bac8-102">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor</span></span>
<span data-ttu-id="0bac8-103">Tworzy wystąpienie [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md) klasy.</span><span class="sxs-lookup"><span data-stu-id="0bac8-103">Creates an instance of the [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md) class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bac8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0bac8-104">Syntax</span></span>  
  
```csharp  
public ClientActivityBuilder(OperationDescription operationDescription, string configurationName, string proxyNamespace);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0bac8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0bac8-105">Parameters</span></span>  
  
## <a name="parameter-values"></a><span data-ttu-id="0bac8-106">Wartości parametrów</span><span class="sxs-lookup"><span data-stu-id="0bac8-106">Parameter Values</span></span>  
 *<span data-ttu-id="0bac8-107">operationDescription</span><span class="sxs-lookup"><span data-stu-id="0bac8-107">operationDescription</span></span>*  
  
 <span data-ttu-id="0bac8-108">Opisuje operacji do wykonania działania przepływu pracy, który ma zostać wygenerowane, łącznie z nazwą operacji, zwracany typ i informacje o parametrze.</span><span class="sxs-lookup"><span data-stu-id="0bac8-108">Describes the operation to be performed in the workflow activity that is to be generated, including the operation name, return type, and parameter information.</span></span> <span data-ttu-id="0bac8-109">Wartość tego parametru nie może być **null**.</span><span class="sxs-lookup"><span data-stu-id="0bac8-109">The value of this parameter must not be **null**.</span></span> <span data-ttu-id="0bac8-110">Powinien on zawierać synchroniczne operacji, który używa kontraktu komunikatu i używa argumentu z jednej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="0bac8-110">It should describe a synchronous operation which uses a message contract and takes an argument with one message.</span></span> <span data-ttu-id="0bac8-111">Jeśli te warunki nie są spełnione, wynik środowiska wykonawczego przy użyciu konstruktora i inne metody tej klasy jest nieokreślona.</span><span class="sxs-lookup"><span data-stu-id="0bac8-111">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 *<span data-ttu-id="0bac8-112">configurationName</span><span class="sxs-lookup"><span data-stu-id="0bac8-112">configurationName</span></span>*  
  
 <span data-ttu-id="0bac8-113">Określa nazwę konfiguracji punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="0bac8-113">Specifies the endpoint configuration name.</span></span> <span data-ttu-id="0bac8-114">Wartość tego parametru nie może być albo **null** lub jest pusty.</span><span class="sxs-lookup"><span data-stu-id="0bac8-114">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="0bac8-115">Jeśli te warunki nie są spełnione, wynik środowiska wykonawczego przy użyciu konstruktora i inne metody tej klasy jest nieokreślona.</span><span class="sxs-lookup"><span data-stu-id="0bac8-115">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 *<span data-ttu-id="0bac8-116">proxyNamespace</span><span class="sxs-lookup"><span data-stu-id="0bac8-116">proxyNamespace</span></span>*  
  
 <span data-ttu-id="0bac8-117">Określa obszar nazw usługi dla operacji.</span><span class="sxs-lookup"><span data-stu-id="0bac8-117">Specifies the service namespace for the operation.</span></span> <span data-ttu-id="0bac8-118">Wartość tego parametru nie może być albo **null** lub jest pusty.</span><span class="sxs-lookup"><span data-stu-id="0bac8-118">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="0bac8-119">Jeśli te warunki nie są spełnione, wynik środowiska wykonawczego przy użyciu konstruktora i inne metody tej klasy jest nieokreślona.</span><span class="sxs-lookup"><span data-stu-id="0bac8-119">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bac8-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0bac8-120">See also</span></span>

- [<span data-ttu-id="0bac8-121">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span><span class="sxs-lookup"><span data-stu-id="0bac8-121">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md)
