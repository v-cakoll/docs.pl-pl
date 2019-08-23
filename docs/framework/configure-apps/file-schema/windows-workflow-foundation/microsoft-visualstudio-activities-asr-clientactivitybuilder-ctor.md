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
ms.openlocfilehash: 99f2eb9447bdf43cb57cfe86f35d2c09044ed470
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947625"
---
# <a name="microsoftvisualstudioactivitiesasrclientactivitybuilderctor"></a><span data-ttu-id="ee4b6-102">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor</span><span class="sxs-lookup"><span data-stu-id="ee4b6-102">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor</span></span>
<span data-ttu-id="ee4b6-103">Tworzy wystąpienie klasy [Microsoft. VisualStudio. Activities. ASR. ClientActivityBuilder](microsoft-visualstudio-activities-asr-clientactivitybuilder.md) .</span><span class="sxs-lookup"><span data-stu-id="ee4b6-103">Creates an instance of the [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](microsoft-visualstudio-activities-asr-clientactivitybuilder.md) class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee4b6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ee4b6-104">Syntax</span></span>  
  
```csharp  
public ClientActivityBuilder(OperationDescription operationDescription, string configurationName, string proxyNamespace);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee4b6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ee4b6-105">Parameters</span></span>  
  
## <a name="parameter-values"></a><span data-ttu-id="ee4b6-106">Wartości parametrów</span><span class="sxs-lookup"><span data-stu-id="ee4b6-106">Parameter Values</span></span>  
 <span data-ttu-id="ee4b6-107">*Obiekt OperationDescription*</span><span class="sxs-lookup"><span data-stu-id="ee4b6-107">*operationDescription*</span></span>  
  
 <span data-ttu-id="ee4b6-108">Opisuje operacji do wykonania działania przepływu pracy, który ma zostać wygenerowane, łącznie z nazwą operacji, zwracany typ i informacje o parametrze.</span><span class="sxs-lookup"><span data-stu-id="ee4b6-108">Describes the operation to be performed in the workflow activity that is to be generated, including the operation name, return type, and parameter information.</span></span> <span data-ttu-id="ee4b6-109">Wartość tego parametru nie może być równa **null**.</span><span class="sxs-lookup"><span data-stu-id="ee4b6-109">The value of this parameter must not be **null**.</span></span> <span data-ttu-id="ee4b6-110">Powinien on zawierać synchroniczne operacji, który używa kontraktu komunikatu i używa argumentu z jednej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="ee4b6-110">It should describe a synchronous operation which uses a message contract and takes an argument with one message.</span></span> <span data-ttu-id="ee4b6-111">Jeśli te warunki nie są spełnione, wynik środowiska wykonawczego przy użyciu konstruktora i inne metody tej klasy jest nieokreślona.</span><span class="sxs-lookup"><span data-stu-id="ee4b6-111">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 <span data-ttu-id="ee4b6-112">*configurationName*</span><span class="sxs-lookup"><span data-stu-id="ee4b6-112">*configurationName*</span></span>  
  
 <span data-ttu-id="ee4b6-113">Określa nazwę konfiguracji punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="ee4b6-113">Specifies the endpoint configuration name.</span></span> <span data-ttu-id="ee4b6-114">Wartość tego parametru nie może mieć **wartości null** ani być pusta.</span><span class="sxs-lookup"><span data-stu-id="ee4b6-114">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="ee4b6-115">Jeśli te warunki nie są spełnione, wynik środowiska wykonawczego przy użyciu konstruktora i inne metody tej klasy jest nieokreślona.</span><span class="sxs-lookup"><span data-stu-id="ee4b6-115">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 <span data-ttu-id="ee4b6-116">*proxyNamespace*</span><span class="sxs-lookup"><span data-stu-id="ee4b6-116">*proxyNamespace*</span></span>  
  
 <span data-ttu-id="ee4b6-117">Określa obszar nazw usługi dla operacji.</span><span class="sxs-lookup"><span data-stu-id="ee4b6-117">Specifies the service namespace for the operation.</span></span> <span data-ttu-id="ee4b6-118">Wartość tego parametru nie może mieć **wartości null** ani być pusta.</span><span class="sxs-lookup"><span data-stu-id="ee4b6-118">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="ee4b6-119">Jeśli te warunki nie są spełnione, wynik środowiska wykonawczego przy użyciu konstruktora i inne metody tej klasy jest nieokreślona.</span><span class="sxs-lookup"><span data-stu-id="ee4b6-119">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee4b6-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ee4b6-120">See also</span></span>

- [<span data-ttu-id="ee4b6-121">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span><span class="sxs-lookup"><span data-stu-id="ee4b6-121">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span></span>](microsoft-visualstudio-activities-asr-clientactivitybuilder.md)
