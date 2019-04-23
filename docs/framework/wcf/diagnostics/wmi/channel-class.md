---
title: Klasa kanału
ms.date: 03/30/2017
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
ms.openlocfilehash: f60a3946617b0994db1ba9e9ddf43be863be81f9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59767451"
---
# <a name="channel-class"></a><span data-ttu-id="68b37-102">Klasa kanału</span><span class="sxs-lookup"><span data-stu-id="68b37-102">Channel class</span></span>
<span data-ttu-id="68b37-103">Kanał</span><span class="sxs-lookup"><span data-stu-id="68b37-103">Channel</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68b37-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="68b37-104">Syntax</span></span>  
  
```csharp
class Channel  
{  
  string LocalAddress;  
  Endpoint ref;  
  string RemoteAddress;  
  string SessionId;  
  string Type;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="68b37-105">Metody</span><span class="sxs-lookup"><span data-stu-id="68b37-105">Methods</span></span>  
 <span data-ttu-id="68b37-106">Klasa kanału nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="68b37-106">The Channel class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="68b37-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="68b37-107">Properties</span></span>  
 <span data-ttu-id="68b37-108">Klasa kanału ma następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="68b37-108">The Channel class has the following properties.</span></span>  
  
### <a name="localaddress"></a><span data-ttu-id="68b37-109">LocalAddress</span><span class="sxs-lookup"><span data-stu-id="68b37-109">LocalAddress</span></span>  
 <span data-ttu-id="68b37-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="68b37-110">Data type: string</span></span>  
  
 <span data-ttu-id="68b37-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="68b37-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="68b37-112">Lokalny punkt końcowy dla kanału.</span><span class="sxs-lookup"><span data-stu-id="68b37-112">The local endpoint for the channel.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="68b37-113">ref</span><span class="sxs-lookup"><span data-stu-id="68b37-113">ref</span></span>  
 <span data-ttu-id="68b37-114">Typ danych: Punkt końcowy</span><span class="sxs-lookup"><span data-stu-id="68b37-114">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="68b37-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="68b37-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="68b37-116">Łączy się z odwołaniem do punktu końcowego kanału.</span><span class="sxs-lookup"><span data-stu-id="68b37-116">A reference to the endpoint the channel connects to.</span></span>  
  
### <a name="remoteaddress"></a><span data-ttu-id="68b37-117">RemoteAddress</span><span class="sxs-lookup"><span data-stu-id="68b37-117">RemoteAddress</span></span>  
 <span data-ttu-id="68b37-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="68b37-118">Data type: string</span></span>  
  
 <span data-ttu-id="68b37-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="68b37-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="68b37-120">Zdalny adres skojarzony z kanałem.</span><span class="sxs-lookup"><span data-stu-id="68b37-120">The remote address associated with the channel.</span></span>  
  
### <a name="sessionid"></a><span data-ttu-id="68b37-121">SessionId</span><span class="sxs-lookup"><span data-stu-id="68b37-121">SessionId</span></span>  
 <span data-ttu-id="68b37-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="68b37-122">Data type: string</span></span>  
  
 <span data-ttu-id="68b37-123">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="68b37-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="68b37-124">Identyfikator bieżącej sesji, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="68b37-124">The current session Id, if any.</span></span>  
  
### <a name="type"></a><span data-ttu-id="68b37-125">Typ</span><span class="sxs-lookup"><span data-stu-id="68b37-125">Type</span></span>  
 <span data-ttu-id="68b37-126">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="68b37-126">Data type: string</span></span>  
  
 <span data-ttu-id="68b37-127">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="68b37-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="68b37-128">Typ kanału.</span><span class="sxs-lookup"><span data-stu-id="68b37-128">The type of the channel.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68b37-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="68b37-129">Requirements</span></span>  
  
|<span data-ttu-id="68b37-130">MOF</span><span class="sxs-lookup"><span data-stu-id="68b37-130">MOF</span></span>|<span data-ttu-id="68b37-131">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="68b37-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="68b37-132">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="68b37-132">Namespace</span></span>|<span data-ttu-id="68b37-133">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="68b37-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="68b37-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="68b37-134">See also</span></span>

- <xref:System.ServiceModel.Channels.ChannelBase>
