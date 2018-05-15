---
title: Klasa kanału
ms.date: 03/30/2017
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
ms.openlocfilehash: 4b7c66560c0c136a258c527d8a681d491eb50aae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="channel-class"></a><span data-ttu-id="cf150-102">Klasa kanału</span><span class="sxs-lookup"><span data-stu-id="cf150-102">Channel class</span></span>
<span data-ttu-id="cf150-103">Kanał</span><span class="sxs-lookup"><span data-stu-id="cf150-103">Channel</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf150-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cf150-104">Syntax</span></span>  
  
```  
class Channel  
{  
  string LocalAddress;  
  Endpoint ref;  
  string RemoteAddress;  
  string SessionId;  
  string Type;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="cf150-105">Metody</span><span class="sxs-lookup"><span data-stu-id="cf150-105">Methods</span></span>  
 <span data-ttu-id="cf150-106">Klasa kanału nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="cf150-106">The Channel class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="cf150-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="cf150-107">Properties</span></span>  
 <span data-ttu-id="cf150-108">Klasa kanału ma następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="cf150-108">The Channel class has the following properties.</span></span>  
  
### <a name="localaddress"></a><span data-ttu-id="cf150-109">LocalAddress</span><span class="sxs-lookup"><span data-stu-id="cf150-109">LocalAddress</span></span>  
 <span data-ttu-id="cf150-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="cf150-110">Data type: string</span></span>  
  
 <span data-ttu-id="cf150-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="cf150-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cf150-112">Lokalny punkt końcowy kanału.</span><span class="sxs-lookup"><span data-stu-id="cf150-112">The local endpoint for the channel.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="cf150-113">ref</span><span class="sxs-lookup"><span data-stu-id="cf150-113">ref</span></span>  
 <span data-ttu-id="cf150-114">Typ danych: punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="cf150-114">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="cf150-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="cf150-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cf150-116">Łączy się z odwołaniem do punktu końcowego kanału.</span><span class="sxs-lookup"><span data-stu-id="cf150-116">A reference to the endpoint the channel connects to.</span></span>  
  
### <a name="remoteaddress"></a><span data-ttu-id="cf150-117">RemoteAddress</span><span class="sxs-lookup"><span data-stu-id="cf150-117">RemoteAddress</span></span>  
 <span data-ttu-id="cf150-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="cf150-118">Data type: string</span></span>  
  
 <span data-ttu-id="cf150-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="cf150-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cf150-120">Zdalny adres skojarzony z kanałem.</span><span class="sxs-lookup"><span data-stu-id="cf150-120">The remote address associated with the channel.</span></span>  
  
### <a name="sessionid"></a><span data-ttu-id="cf150-121">SessionId</span><span class="sxs-lookup"><span data-stu-id="cf150-121">SessionId</span></span>  
 <span data-ttu-id="cf150-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="cf150-122">Data type: string</span></span>  
  
 <span data-ttu-id="cf150-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="cf150-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cf150-124">Identyfikator bieżącej sesji, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="cf150-124">The current session Id, if any.</span></span>  
  
### <a name="type"></a><span data-ttu-id="cf150-125">Typ</span><span class="sxs-lookup"><span data-stu-id="cf150-125">Type</span></span>  
 <span data-ttu-id="cf150-126">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="cf150-126">Data type: string</span></span>  
  
 <span data-ttu-id="cf150-127">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="cf150-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cf150-128">Typ kanału.</span><span class="sxs-lookup"><span data-stu-id="cf150-128">The type of the channel.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf150-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cf150-129">Requirements</span></span>  
  
|<span data-ttu-id="cf150-130">MOF</span><span class="sxs-lookup"><span data-stu-id="cf150-130">MOF</span></span>|<span data-ttu-id="cf150-131">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="cf150-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="cf150-132">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="cf150-132">Namespace</span></span>|<span data-ttu-id="cf150-133">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="cf150-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cf150-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cf150-134">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ChannelBase>
