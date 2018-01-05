---
title: "Usługa"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 999806e1-6376-409e-b998-b0af391adfe7
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f7b631ede7bd011a92003dc5f6083c1c427d990e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="service"></a><span data-ttu-id="23fa3-102">Usługa</span><span class="sxs-lookup"><span data-stu-id="23fa3-102">Service</span></span>
<span data-ttu-id="23fa3-103">Usługa</span><span class="sxs-lookup"><span data-stu-id="23fa3-103">Service</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23fa3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="23fa3-104">Syntax</span></span>  
  
```  
class Service  
{  
  string BaseAddresses[];  
  Behavior Behaviors[];  
  string ConfigurationName;  
  string CounterInstanceName;  
  string DistinguishedName;  
  string Extensions[];  
  string Metadata[];  
  string Name;  
  string Namespace;  
  datetime Opened;  
  Channel OutgoingChannels[];  
  sint32 ProcessId;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="23fa3-105">Metody</span><span class="sxs-lookup"><span data-stu-id="23fa3-105">Methods</span></span>  
 <span data-ttu-id="23fa3-106">Klasa usługi nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="23fa3-106">The Service class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="23fa3-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="23fa3-107">Properties</span></span>  
 <span data-ttu-id="23fa3-108">Klasa usługi ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="23fa3-108">The Service class has the following properties:</span></span>  
  
### <a name="baseaddresses"></a><span data-ttu-id="23fa3-109">BaseAddresses</span><span class="sxs-lookup"><span data-stu-id="23fa3-109">BaseAddresses</span></span>  
 <span data-ttu-id="23fa3-110">Typ danych: tablicy ciągów</span><span class="sxs-lookup"><span data-stu-id="23fa3-110">Data type: string array</span></span>  
  
 <span data-ttu-id="23fa3-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="23fa3-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="23fa3-112">Adres podstawowy używany przez usługę.</span><span class="sxs-lookup"><span data-stu-id="23fa3-112">The base addresses used by the service.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="23fa3-113">Zachowania</span><span class="sxs-lookup"><span data-stu-id="23fa3-113">Behaviors</span></span>  
 <span data-ttu-id="23fa3-114">Typ danych: zachowanie tablicy</span><span class="sxs-lookup"><span data-stu-id="23fa3-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="23fa3-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="23fa3-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="23fa3-116">Zachowania skojarzone z tą usługą.</span><span class="sxs-lookup"><span data-stu-id="23fa3-116">The behaviors associated with this service.</span></span>  
  
### <a name="configurationname"></a><span data-ttu-id="23fa3-117">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="23fa3-117">ConfigurationName</span></span>  
 <span data-ttu-id="23fa3-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="23fa3-118">Data type: string</span></span>  
  
 <span data-ttu-id="23fa3-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="23fa3-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="23fa3-120">ServiceElement_BehaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="23fa3-120">ServiceElement_BehaviorConfiguration</span></span>  
  
### <a name="counterinstancename"></a><span data-ttu-id="23fa3-121">CounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="23fa3-121">CounterInstanceName</span></span>  
 <span data-ttu-id="23fa3-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="23fa3-122">Data type: string</span></span>  
  
 <span data-ttu-id="23fa3-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="23fa3-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="23fa3-124">Nazwa wystąpienia wystąpienia liczników wydajności usługi.</span><span class="sxs-lookup"><span data-stu-id="23fa3-124">Instance name of the instance of the performance counters of the service.</span></span>  
  
### <a name="distinguishedname"></a><span data-ttu-id="23fa3-125">DistinguishedName</span><span class="sxs-lookup"><span data-stu-id="23fa3-125">DistinguishedName</span></span>  
 <span data-ttu-id="23fa3-126">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="23fa3-126">Data type: string</span></span>  
  
 <span data-ttu-id="23fa3-127">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="23fa3-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="23fa3-128">Nazwa usługi pod adresem.</span><span class="sxs-lookup"><span data-stu-id="23fa3-128">Service name at the address.</span></span>  
  
### <a name="extensions"></a><span data-ttu-id="23fa3-129">Rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="23fa3-129">Extensions</span></span>  
 <span data-ttu-id="23fa3-130">Typ danych: tablicy ciągów</span><span class="sxs-lookup"><span data-stu-id="23fa3-130">Data type: string array</span></span>  
  
 <span data-ttu-id="23fa3-131">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="23fa3-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="23fa3-132">Konteksty wystąpienia dla rozszerzeń wystąpienia tej usługi.</span><span class="sxs-lookup"><span data-stu-id="23fa3-132">The instance contexts for the extensions of the service instance.</span></span>  
  
### <a name="metadata"></a><span data-ttu-id="23fa3-133">Metadane</span><span class="sxs-lookup"><span data-stu-id="23fa3-133">Metadata</span></span>  
 <span data-ttu-id="23fa3-134">Typ danych: tablicy ciągów</span><span class="sxs-lookup"><span data-stu-id="23fa3-134">Data type: string array</span></span>  
  
 <span data-ttu-id="23fa3-135">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="23fa3-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="23fa3-136">Ustawienia metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="23fa3-136">The service metadata settings.</span></span>  
  
### <a name="name"></a><span data-ttu-id="23fa3-137">Nazwa</span><span class="sxs-lookup"><span data-stu-id="23fa3-137">Name</span></span>  
 <span data-ttu-id="23fa3-138">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="23fa3-138">Data type: string</span></span>  
  
 <span data-ttu-id="23fa3-139">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="23fa3-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="23fa3-140">Unikatowa nazwa tej usługi.</span><span class="sxs-lookup"><span data-stu-id="23fa3-140">The unique name of this service.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="23fa3-141">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="23fa3-141">Namespace</span></span>  
 <span data-ttu-id="23fa3-142">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="23fa3-142">Data type: string</span></span>  
  
 <span data-ttu-id="23fa3-143">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="23fa3-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="23fa3-144">Przestrzeń nazw usługi.</span><span class="sxs-lookup"><span data-stu-id="23fa3-144">The namespace of the service.</span></span>  
  
### <a name="opened"></a><span data-ttu-id="23fa3-145">Otwarte</span><span class="sxs-lookup"><span data-stu-id="23fa3-145">Opened</span></span>  
 <span data-ttu-id="23fa3-146">Typ danych: daty i godziny</span><span class="sxs-lookup"><span data-stu-id="23fa3-146">Data type: datetime</span></span>  
  
 <span data-ttu-id="23fa3-147">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="23fa3-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="23fa3-148">Czas otwarcia usługi.</span><span class="sxs-lookup"><span data-stu-id="23fa3-148">The time the service was opened.</span></span>  
  
### <a name="outgoingchannels"></a><span data-ttu-id="23fa3-149">OutgoingChannels</span><span class="sxs-lookup"><span data-stu-id="23fa3-149">OutgoingChannels</span></span>  
 <span data-ttu-id="23fa3-150">Typ danych: tablica kanału</span><span class="sxs-lookup"><span data-stu-id="23fa3-150">Data type: Channel array</span></span>  
  
 <span data-ttu-id="23fa3-151">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="23fa3-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="23fa3-152">Kanały wychodzące z wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="23fa3-152">The channels that are outgoing from the service instance.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="23fa3-153">Identyfikator procesu</span><span class="sxs-lookup"><span data-stu-id="23fa3-153">ProcessId</span></span>  
 <span data-ttu-id="23fa3-154">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="23fa3-154">Data type: sint32</span></span>  
  
 <span data-ttu-id="23fa3-155">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="23fa3-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="23fa3-156">Identyfikator procesu obsługującego usługę.</span><span class="sxs-lookup"><span data-stu-id="23fa3-156">The process id of the process that hosts the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23fa3-157">Wymagania</span><span class="sxs-lookup"><span data-stu-id="23fa3-157">Requirements</span></span>  
  
|<span data-ttu-id="23fa3-158">MOF</span><span class="sxs-lookup"><span data-stu-id="23fa3-158">MOF</span></span>|<span data-ttu-id="23fa3-159">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="23fa3-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="23fa3-160">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="23fa3-160">Namespace</span></span>|<span data-ttu-id="23fa3-161">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="23fa3-161">Defined in root\ServiceModel</span></span>|
