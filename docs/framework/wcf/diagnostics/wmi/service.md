---
title: Usługa
ms.date: 03/30/2017
ms.assetid: 999806e1-6376-409e-b998-b0af391adfe7
ms.openlocfilehash: c59672b3b7617d9c28d99f7d534b6e7f2f2e9fbb
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2018
ms.locfileid: "49633953"
---
# <a name="service"></a><span data-ttu-id="f333e-102">Usługa</span><span class="sxs-lookup"><span data-stu-id="f333e-102">Service</span></span>
<span data-ttu-id="f333e-103">Usługa</span><span class="sxs-lookup"><span data-stu-id="f333e-103">Service</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f333e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f333e-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="f333e-105">Metody</span><span class="sxs-lookup"><span data-stu-id="f333e-105">Methods</span></span>  
 <span data-ttu-id="f333e-106">Klasa usługi nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="f333e-106">The Service class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f333e-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="f333e-107">Properties</span></span>  
 <span data-ttu-id="f333e-108">Klasa usługi ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="f333e-108">The Service class has the following properties:</span></span>  
  
### <a name="baseaddresses"></a><span data-ttu-id="f333e-109">BaseAddresses</span><span class="sxs-lookup"><span data-stu-id="f333e-109">BaseAddresses</span></span>  
 <span data-ttu-id="f333e-110">Typ danych: tablica ciągów</span><span class="sxs-lookup"><span data-stu-id="f333e-110">Data type: string array</span></span>  
  
 <span data-ttu-id="f333e-111">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f333e-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f333e-112">Adres podstawowy używany przez usługę.</span><span class="sxs-lookup"><span data-stu-id="f333e-112">The base addresses used by the service.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="f333e-113">Zachowania</span><span class="sxs-lookup"><span data-stu-id="f333e-113">Behaviors</span></span>  
 <span data-ttu-id="f333e-114">Typ danych: zachowanie tablicy</span><span class="sxs-lookup"><span data-stu-id="f333e-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="f333e-115">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f333e-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f333e-116">Zachowania skojarzone z tą usługą.</span><span class="sxs-lookup"><span data-stu-id="f333e-116">The behaviors associated with this service.</span></span>  
  
### <a name="configurationname"></a><span data-ttu-id="f333e-117">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="f333e-117">ConfigurationName</span></span>  
 <span data-ttu-id="f333e-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="f333e-118">Data type: string</span></span>  
  
 <span data-ttu-id="f333e-119">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f333e-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f333e-120">ServiceElement_BehaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="f333e-120">ServiceElement_BehaviorConfiguration</span></span>  
  
### <a name="counterinstancename"></a><span data-ttu-id="f333e-121">CounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="f333e-121">CounterInstanceName</span></span>  
 <span data-ttu-id="f333e-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="f333e-122">Data type: string</span></span>  
  
 <span data-ttu-id="f333e-123">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f333e-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f333e-124">Nazwa wystąpienia wystąpienia liczników wydajności usługi.</span><span class="sxs-lookup"><span data-stu-id="f333e-124">Instance name of the instance of the performance counters of the service.</span></span>  
  
### <a name="distinguishedname"></a><span data-ttu-id="f333e-125">DistinguishedName</span><span class="sxs-lookup"><span data-stu-id="f333e-125">DistinguishedName</span></span>  
 <span data-ttu-id="f333e-126">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="f333e-126">Data type: string</span></span>  
  
 <span data-ttu-id="f333e-127">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f333e-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f333e-128">Nazwa usługi pod adresem.</span><span class="sxs-lookup"><span data-stu-id="f333e-128">Service name at the address.</span></span>  
  
### <a name="extensions"></a><span data-ttu-id="f333e-129">Rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="f333e-129">Extensions</span></span>  
 <span data-ttu-id="f333e-130">Typ danych: tablica ciągów</span><span class="sxs-lookup"><span data-stu-id="f333e-130">Data type: string array</span></span>  
  
 <span data-ttu-id="f333e-131">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f333e-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f333e-132">Konteksty wystąpień dla rozszerzeń wystąpienie usługi.</span><span class="sxs-lookup"><span data-stu-id="f333e-132">The instance contexts for the extensions of the service instance.</span></span>  
  
### <a name="metadata"></a><span data-ttu-id="f333e-133">Metadane</span><span class="sxs-lookup"><span data-stu-id="f333e-133">Metadata</span></span>  
 <span data-ttu-id="f333e-134">Typ danych: tablica ciągów</span><span class="sxs-lookup"><span data-stu-id="f333e-134">Data type: string array</span></span>  
  
 <span data-ttu-id="f333e-135">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f333e-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f333e-136">Ustawienia metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="f333e-136">The service metadata settings.</span></span>  
  
### <a name="name"></a><span data-ttu-id="f333e-137">Nazwa</span><span class="sxs-lookup"><span data-stu-id="f333e-137">Name</span></span>  
 <span data-ttu-id="f333e-138">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="f333e-138">Data type: string</span></span>  
  
 <span data-ttu-id="f333e-139">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f333e-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f333e-140">Unikatowa nazwa tej usługi.</span><span class="sxs-lookup"><span data-stu-id="f333e-140">The unique name of this service.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="f333e-141">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="f333e-141">Namespace</span></span>  
 <span data-ttu-id="f333e-142">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="f333e-142">Data type: string</span></span>  
  
 <span data-ttu-id="f333e-143">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f333e-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f333e-144">Przestrzeń nazw usługi.</span><span class="sxs-lookup"><span data-stu-id="f333e-144">The namespace of the service.</span></span>  
  
### <a name="opened"></a><span data-ttu-id="f333e-145">Otwarte</span><span class="sxs-lookup"><span data-stu-id="f333e-145">Opened</span></span>  
 <span data-ttu-id="f333e-146">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="f333e-146">Data type: datetime</span></span>  
  
 <span data-ttu-id="f333e-147">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f333e-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f333e-148">Czas otwarcia usługi.</span><span class="sxs-lookup"><span data-stu-id="f333e-148">The time the service was opened.</span></span>  
  
### <a name="outgoingchannels"></a><span data-ttu-id="f333e-149">OutgoingChannels</span><span class="sxs-lookup"><span data-stu-id="f333e-149">OutgoingChannels</span></span>  
 <span data-ttu-id="f333e-150">Typ danych: tablica kanału</span><span class="sxs-lookup"><span data-stu-id="f333e-150">Data type: Channel array</span></span>  
  
 <span data-ttu-id="f333e-151">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f333e-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f333e-152">Kanały wychodzące z wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="f333e-152">The channels that are outgoing from the service instance.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="f333e-153">Identyfikator procesu</span><span class="sxs-lookup"><span data-stu-id="f333e-153">ProcessId</span></span>  
 <span data-ttu-id="f333e-154">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="f333e-154">Data type: sint32</span></span>  
  
 <span data-ttu-id="f333e-155">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f333e-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f333e-156">Identyfikator procesu procesu, który hostuje usługę.</span><span class="sxs-lookup"><span data-stu-id="f333e-156">The process id of the process that hosts the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f333e-157">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f333e-157">Requirements</span></span>  
  
|<span data-ttu-id="f333e-158">PLIK MOF</span><span class="sxs-lookup"><span data-stu-id="f333e-158">MOF</span></span>|<span data-ttu-id="f333e-159">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="f333e-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f333e-160">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="f333e-160">Namespace</span></span>|<span data-ttu-id="f333e-161">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f333e-161">Defined in root\ServiceModel</span></span>|
