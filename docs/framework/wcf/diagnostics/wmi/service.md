---
title: Usługa
ms.date: 03/30/2017
ms.assetid: 999806e1-6376-409e-b998-b0af391adfe7
ms.openlocfilehash: 0cfeb178e26f6c93e29210accf5d7866cc1fca02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="service"></a><span data-ttu-id="16cd7-102">Usługa</span><span class="sxs-lookup"><span data-stu-id="16cd7-102">Service</span></span>
<span data-ttu-id="16cd7-103">Usługa</span><span class="sxs-lookup"><span data-stu-id="16cd7-103">Service</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16cd7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="16cd7-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="16cd7-105">Metody</span><span class="sxs-lookup"><span data-stu-id="16cd7-105">Methods</span></span>  
 <span data-ttu-id="16cd7-106">Klasa usługi nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="16cd7-106">The Service class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="16cd7-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="16cd7-107">Properties</span></span>  
 <span data-ttu-id="16cd7-108">Klasa usługi ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="16cd7-108">The Service class has the following properties:</span></span>  
  
### <a name="baseaddresses"></a><span data-ttu-id="16cd7-109">BaseAddresses</span><span class="sxs-lookup"><span data-stu-id="16cd7-109">BaseAddresses</span></span>  
 <span data-ttu-id="16cd7-110">Typ danych: tablicy ciągów</span><span class="sxs-lookup"><span data-stu-id="16cd7-110">Data type: string array</span></span>  
  
 <span data-ttu-id="16cd7-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="16cd7-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="16cd7-112">Adres podstawowy używany przez usługę.</span><span class="sxs-lookup"><span data-stu-id="16cd7-112">The base addresses used by the service.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="16cd7-113">Zachowania</span><span class="sxs-lookup"><span data-stu-id="16cd7-113">Behaviors</span></span>  
 <span data-ttu-id="16cd7-114">Typ danych: zachowanie tablicy</span><span class="sxs-lookup"><span data-stu-id="16cd7-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="16cd7-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="16cd7-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="16cd7-116">Zachowania skojarzone z tą usługą.</span><span class="sxs-lookup"><span data-stu-id="16cd7-116">The behaviors associated with this service.</span></span>  
  
### <a name="configurationname"></a><span data-ttu-id="16cd7-117">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="16cd7-117">ConfigurationName</span></span>  
 <span data-ttu-id="16cd7-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="16cd7-118">Data type: string</span></span>  
  
 <span data-ttu-id="16cd7-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="16cd7-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="16cd7-120">ServiceElement_BehaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="16cd7-120">ServiceElement_BehaviorConfiguration</span></span>  
  
### <a name="counterinstancename"></a><span data-ttu-id="16cd7-121">CounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="16cd7-121">CounterInstanceName</span></span>  
 <span data-ttu-id="16cd7-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="16cd7-122">Data type: string</span></span>  
  
 <span data-ttu-id="16cd7-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="16cd7-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="16cd7-124">Nazwa wystąpienia wystąpienia liczników wydajności usługi.</span><span class="sxs-lookup"><span data-stu-id="16cd7-124">Instance name of the instance of the performance counters of the service.</span></span>  
  
### <a name="distinguishedname"></a><span data-ttu-id="16cd7-125">DistinguishedName</span><span class="sxs-lookup"><span data-stu-id="16cd7-125">DistinguishedName</span></span>  
 <span data-ttu-id="16cd7-126">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="16cd7-126">Data type: string</span></span>  
  
 <span data-ttu-id="16cd7-127">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="16cd7-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="16cd7-128">Nazwa usługi pod adresem.</span><span class="sxs-lookup"><span data-stu-id="16cd7-128">Service name at the address.</span></span>  
  
### <a name="extensions"></a><span data-ttu-id="16cd7-129">Rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="16cd7-129">Extensions</span></span>  
 <span data-ttu-id="16cd7-130">Typ danych: tablicy ciągów</span><span class="sxs-lookup"><span data-stu-id="16cd7-130">Data type: string array</span></span>  
  
 <span data-ttu-id="16cd7-131">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="16cd7-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="16cd7-132">Konteksty wystąpienia dla rozszerzeń wystąpienia tej usługi.</span><span class="sxs-lookup"><span data-stu-id="16cd7-132">The instance contexts for the extensions of the service instance.</span></span>  
  
### <a name="metadata"></a><span data-ttu-id="16cd7-133">Metadane</span><span class="sxs-lookup"><span data-stu-id="16cd7-133">Metadata</span></span>  
 <span data-ttu-id="16cd7-134">Typ danych: tablicy ciągów</span><span class="sxs-lookup"><span data-stu-id="16cd7-134">Data type: string array</span></span>  
  
 <span data-ttu-id="16cd7-135">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="16cd7-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="16cd7-136">Ustawienia metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="16cd7-136">The service metadata settings.</span></span>  
  
### <a name="name"></a><span data-ttu-id="16cd7-137">Nazwa</span><span class="sxs-lookup"><span data-stu-id="16cd7-137">Name</span></span>  
 <span data-ttu-id="16cd7-138">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="16cd7-138">Data type: string</span></span>  
  
 <span data-ttu-id="16cd7-139">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="16cd7-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="16cd7-140">Unikatowa nazwa tej usługi.</span><span class="sxs-lookup"><span data-stu-id="16cd7-140">The unique name of this service.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="16cd7-141">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="16cd7-141">Namespace</span></span>  
 <span data-ttu-id="16cd7-142">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="16cd7-142">Data type: string</span></span>  
  
 <span data-ttu-id="16cd7-143">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="16cd7-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="16cd7-144">Przestrzeń nazw usługi.</span><span class="sxs-lookup"><span data-stu-id="16cd7-144">The namespace of the service.</span></span>  
  
### <a name="opened"></a><span data-ttu-id="16cd7-145">Otwarte</span><span class="sxs-lookup"><span data-stu-id="16cd7-145">Opened</span></span>  
 <span data-ttu-id="16cd7-146">Typ danych: daty i godziny</span><span class="sxs-lookup"><span data-stu-id="16cd7-146">Data type: datetime</span></span>  
  
 <span data-ttu-id="16cd7-147">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="16cd7-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="16cd7-148">Czas otwarcia usługi.</span><span class="sxs-lookup"><span data-stu-id="16cd7-148">The time the service was opened.</span></span>  
  
### <a name="outgoingchannels"></a><span data-ttu-id="16cd7-149">OutgoingChannels</span><span class="sxs-lookup"><span data-stu-id="16cd7-149">OutgoingChannels</span></span>  
 <span data-ttu-id="16cd7-150">Typ danych: tablica kanału</span><span class="sxs-lookup"><span data-stu-id="16cd7-150">Data type: Channel array</span></span>  
  
 <span data-ttu-id="16cd7-151">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="16cd7-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="16cd7-152">Kanały wychodzące z wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="16cd7-152">The channels that are outgoing from the service instance.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="16cd7-153">Identyfikator procesu</span><span class="sxs-lookup"><span data-stu-id="16cd7-153">ProcessId</span></span>  
 <span data-ttu-id="16cd7-154">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="16cd7-154">Data type: sint32</span></span>  
  
 <span data-ttu-id="16cd7-155">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="16cd7-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="16cd7-156">Identyfikator procesu obsługującego usługę.</span><span class="sxs-lookup"><span data-stu-id="16cd7-156">The process id of the process that hosts the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16cd7-157">Wymagania</span><span class="sxs-lookup"><span data-stu-id="16cd7-157">Requirements</span></span>  
  
|<span data-ttu-id="16cd7-158">MOF</span><span class="sxs-lookup"><span data-stu-id="16cd7-158">MOF</span></span>|<span data-ttu-id="16cd7-159">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="16cd7-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="16cd7-160">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="16cd7-160">Namespace</span></span>|<span data-ttu-id="16cd7-161">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="16cd7-161">Defined in root\ServiceModel</span></span>|
