---
title: Usługa
ms.date: 03/30/2017
ms.assetid: 999806e1-6376-409e-b998-b0af391adfe7
ms.openlocfilehash: c59672b3b7617d9c28d99f7d534b6e7f2f2e9fbb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991448"
---
# <a name="service"></a><span data-ttu-id="4602f-102">Usługa</span><span class="sxs-lookup"><span data-stu-id="4602f-102">Service</span></span>
<span data-ttu-id="4602f-103">Usługa</span><span class="sxs-lookup"><span data-stu-id="4602f-103">Service</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4602f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4602f-104">Syntax</span></span>  
  
```csharp
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
  
## <a name="methods"></a><span data-ttu-id="4602f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="4602f-105">Methods</span></span>  
 <span data-ttu-id="4602f-106">Klasa usługi nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="4602f-106">The Service class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4602f-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="4602f-107">Properties</span></span>  
 <span data-ttu-id="4602f-108">Klasa usługi ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="4602f-108">The Service class has the following properties:</span></span>  
  
### <a name="baseaddresses"></a><span data-ttu-id="4602f-109">BaseAddresses</span><span class="sxs-lookup"><span data-stu-id="4602f-109">BaseAddresses</span></span>  
 <span data-ttu-id="4602f-110">Typ danych: tablica ciągów</span><span class="sxs-lookup"><span data-stu-id="4602f-110">Data type: string array</span></span>  
  
 <span data-ttu-id="4602f-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4602f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4602f-112">Adres podstawowy używany przez usługę.</span><span class="sxs-lookup"><span data-stu-id="4602f-112">The base addresses used by the service.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="4602f-113">Zachowania</span><span class="sxs-lookup"><span data-stu-id="4602f-113">Behaviors</span></span>  
 <span data-ttu-id="4602f-114">Typ danych: Zachowanie tablicy</span><span class="sxs-lookup"><span data-stu-id="4602f-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="4602f-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4602f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4602f-116">Zachowania skojarzone z tą usługą.</span><span class="sxs-lookup"><span data-stu-id="4602f-116">The behaviors associated with this service.</span></span>  
  
### <a name="configurationname"></a><span data-ttu-id="4602f-117">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="4602f-117">ConfigurationName</span></span>  
 <span data-ttu-id="4602f-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="4602f-118">Data type: string</span></span>  
  
 <span data-ttu-id="4602f-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4602f-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4602f-120">ServiceElement_BehaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="4602f-120">ServiceElement_BehaviorConfiguration</span></span>  
  
### <a name="counterinstancename"></a><span data-ttu-id="4602f-121">CounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="4602f-121">CounterInstanceName</span></span>  
 <span data-ttu-id="4602f-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="4602f-122">Data type: string</span></span>  
  
 <span data-ttu-id="4602f-123">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4602f-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4602f-124">Nazwa wystąpienia wystąpienia liczników wydajności usługi.</span><span class="sxs-lookup"><span data-stu-id="4602f-124">Instance name of the instance of the performance counters of the service.</span></span>  
  
### <a name="distinguishedname"></a><span data-ttu-id="4602f-125">DistinguishedName</span><span class="sxs-lookup"><span data-stu-id="4602f-125">DistinguishedName</span></span>  
 <span data-ttu-id="4602f-126">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="4602f-126">Data type: string</span></span>  
  
 <span data-ttu-id="4602f-127">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4602f-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4602f-128">Nazwa usługi pod adresem.</span><span class="sxs-lookup"><span data-stu-id="4602f-128">Service name at the address.</span></span>  
  
### <a name="extensions"></a><span data-ttu-id="4602f-129">Rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="4602f-129">Extensions</span></span>  
 <span data-ttu-id="4602f-130">Typ danych: tablica ciągów</span><span class="sxs-lookup"><span data-stu-id="4602f-130">Data type: string array</span></span>  
  
 <span data-ttu-id="4602f-131">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4602f-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4602f-132">Konteksty wystąpień dla rozszerzeń wystąpienie usługi.</span><span class="sxs-lookup"><span data-stu-id="4602f-132">The instance contexts for the extensions of the service instance.</span></span>  
  
### <a name="metadata"></a><span data-ttu-id="4602f-133">Metadane</span><span class="sxs-lookup"><span data-stu-id="4602f-133">Metadata</span></span>  
 <span data-ttu-id="4602f-134">Typ danych: tablica ciągów</span><span class="sxs-lookup"><span data-stu-id="4602f-134">Data type: string array</span></span>  
  
 <span data-ttu-id="4602f-135">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4602f-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4602f-136">Ustawienia metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="4602f-136">The service metadata settings.</span></span>  
  
### <a name="name"></a><span data-ttu-id="4602f-137">Nazwa</span><span class="sxs-lookup"><span data-stu-id="4602f-137">Name</span></span>  
 <span data-ttu-id="4602f-138">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="4602f-138">Data type: string</span></span>  
  
 <span data-ttu-id="4602f-139">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4602f-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4602f-140">Unikatowa nazwa tej usługi.</span><span class="sxs-lookup"><span data-stu-id="4602f-140">The unique name of this service.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="4602f-141">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="4602f-141">Namespace</span></span>  
 <span data-ttu-id="4602f-142">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="4602f-142">Data type: string</span></span>  
  
 <span data-ttu-id="4602f-143">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4602f-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4602f-144">Przestrzeń nazw usługi.</span><span class="sxs-lookup"><span data-stu-id="4602f-144">The namespace of the service.</span></span>  
  
### <a name="opened"></a><span data-ttu-id="4602f-145">Otwarte</span><span class="sxs-lookup"><span data-stu-id="4602f-145">Opened</span></span>  
 <span data-ttu-id="4602f-146">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="4602f-146">Data type: datetime</span></span>  
  
 <span data-ttu-id="4602f-147">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4602f-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4602f-148">Czas otwarcia usługi.</span><span class="sxs-lookup"><span data-stu-id="4602f-148">The time the service was opened.</span></span>  
  
### <a name="outgoingchannels"></a><span data-ttu-id="4602f-149">OutgoingChannels</span><span class="sxs-lookup"><span data-stu-id="4602f-149">OutgoingChannels</span></span>  
 <span data-ttu-id="4602f-150">Typ danych: Tablica kanału</span><span class="sxs-lookup"><span data-stu-id="4602f-150">Data type: Channel array</span></span>  
  
 <span data-ttu-id="4602f-151">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4602f-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4602f-152">Kanały wychodzące z wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="4602f-152">The channels that are outgoing from the service instance.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="4602f-153">Identyfikator procesu</span><span class="sxs-lookup"><span data-stu-id="4602f-153">ProcessId</span></span>  
 <span data-ttu-id="4602f-154">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="4602f-154">Data type: sint32</span></span>  
  
 <span data-ttu-id="4602f-155">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4602f-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4602f-156">Identyfikator procesu procesu, który hostuje usługę.</span><span class="sxs-lookup"><span data-stu-id="4602f-156">The process id of the process that hosts the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4602f-157">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4602f-157">Requirements</span></span>  
  
|<span data-ttu-id="4602f-158">MOF</span><span class="sxs-lookup"><span data-stu-id="4602f-158">MOF</span></span>|<span data-ttu-id="4602f-159">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="4602f-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4602f-160">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="4602f-160">Namespace</span></span>|<span data-ttu-id="4602f-161">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4602f-161">Defined in root\ServiceModel</span></span>|
