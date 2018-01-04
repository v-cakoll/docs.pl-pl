---
title: "Klasa kanału"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 073f0a2a2731a08acd914a7dd85cb2b419d98128
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="channel-class"></a><span data-ttu-id="22d41-102">Klasa kanału</span><span class="sxs-lookup"><span data-stu-id="22d41-102">Channel class</span></span>
<span data-ttu-id="22d41-103">Kanał</span><span class="sxs-lookup"><span data-stu-id="22d41-103">Channel</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22d41-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="22d41-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="22d41-105">Metody</span><span class="sxs-lookup"><span data-stu-id="22d41-105">Methods</span></span>  
 <span data-ttu-id="22d41-106">Klasa kanału nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="22d41-106">The Channel class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="22d41-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="22d41-107">Properties</span></span>  
 <span data-ttu-id="22d41-108">Klasa kanału ma następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="22d41-108">The Channel class has the following properties.</span></span>  
  
### <a name="localaddress"></a><span data-ttu-id="22d41-109">LocalAddress</span><span class="sxs-lookup"><span data-stu-id="22d41-109">LocalAddress</span></span>  
 <span data-ttu-id="22d41-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="22d41-110">Data type: string</span></span>  
  
 <span data-ttu-id="22d41-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="22d41-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="22d41-112">Lokalny punkt końcowy kanału.</span><span class="sxs-lookup"><span data-stu-id="22d41-112">The local endpoint for the channel.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="22d41-113">ref</span><span class="sxs-lookup"><span data-stu-id="22d41-113">ref</span></span>  
 <span data-ttu-id="22d41-114">Typ danych: punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="22d41-114">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="22d41-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="22d41-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="22d41-116">Łączy się z odwołaniem do punktu końcowego kanału.</span><span class="sxs-lookup"><span data-stu-id="22d41-116">A reference to the endpoint the channel connects to.</span></span>  
  
### <a name="remoteaddress"></a><span data-ttu-id="22d41-117">RemoteAddress</span><span class="sxs-lookup"><span data-stu-id="22d41-117">RemoteAddress</span></span>  
 <span data-ttu-id="22d41-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="22d41-118">Data type: string</span></span>  
  
 <span data-ttu-id="22d41-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="22d41-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="22d41-120">Zdalny adres skojarzony z kanałem.</span><span class="sxs-lookup"><span data-stu-id="22d41-120">The remote address associated with the channel.</span></span>  
  
### <a name="sessionid"></a><span data-ttu-id="22d41-121">SessionId</span><span class="sxs-lookup"><span data-stu-id="22d41-121">SessionId</span></span>  
 <span data-ttu-id="22d41-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="22d41-122">Data type: string</span></span>  
  
 <span data-ttu-id="22d41-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="22d41-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="22d41-124">Identyfikator bieżącej sesji, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="22d41-124">The current session Id, if any.</span></span>  
  
### <a name="type"></a><span data-ttu-id="22d41-125">Typ</span><span class="sxs-lookup"><span data-stu-id="22d41-125">Type</span></span>  
 <span data-ttu-id="22d41-126">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="22d41-126">Data type: string</span></span>  
  
 <span data-ttu-id="22d41-127">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="22d41-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="22d41-128">Typ kanału.</span><span class="sxs-lookup"><span data-stu-id="22d41-128">The type of the channel.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22d41-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="22d41-129">Requirements</span></span>  
  
|<span data-ttu-id="22d41-130">MOF</span><span class="sxs-lookup"><span data-stu-id="22d41-130">MOF</span></span>|<span data-ttu-id="22d41-131">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="22d41-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="22d41-132">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="22d41-132">Namespace</span></span>|<span data-ttu-id="22d41-133">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="22d41-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="22d41-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="22d41-134">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ChannelBase>
