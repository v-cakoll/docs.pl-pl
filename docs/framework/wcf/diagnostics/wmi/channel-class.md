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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1df634a61cce695fca74fdfe53beea6c0f83d082
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="channel-class"></a><span data-ttu-id="b0919-102">Klasa kanału</span><span class="sxs-lookup"><span data-stu-id="b0919-102">Channel class</span></span>
<span data-ttu-id="b0919-103">Kanał</span><span class="sxs-lookup"><span data-stu-id="b0919-103">Channel</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0919-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b0919-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="b0919-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b0919-105">Methods</span></span>  
 <span data-ttu-id="b0919-106">Klasa kanału nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="b0919-106">The Channel class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b0919-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="b0919-107">Properties</span></span>  
 <span data-ttu-id="b0919-108">Klasa kanału ma następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="b0919-108">The Channel class has the following properties.</span></span>  
  
### <a name="localaddress"></a><span data-ttu-id="b0919-109">LocalAddress</span><span class="sxs-lookup"><span data-stu-id="b0919-109">LocalAddress</span></span>  
 <span data-ttu-id="b0919-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="b0919-110">Data type: string</span></span>  
  
 <span data-ttu-id="b0919-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b0919-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b0919-112">Lokalny punkt końcowy kanału.</span><span class="sxs-lookup"><span data-stu-id="b0919-112">The local endpoint for the channel.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="b0919-113">ref</span><span class="sxs-lookup"><span data-stu-id="b0919-113">ref</span></span>  
 <span data-ttu-id="b0919-114">Typ danych: punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="b0919-114">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="b0919-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b0919-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b0919-116">Łączy się z odwołaniem do punktu końcowego kanału.</span><span class="sxs-lookup"><span data-stu-id="b0919-116">A reference to the endpoint the channel connects to.</span></span>  
  
### <a name="remoteaddress"></a><span data-ttu-id="b0919-117">RemoteAddress</span><span class="sxs-lookup"><span data-stu-id="b0919-117">RemoteAddress</span></span>  
 <span data-ttu-id="b0919-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="b0919-118">Data type: string</span></span>  
  
 <span data-ttu-id="b0919-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b0919-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b0919-120">Zdalny adres skojarzony z kanałem.</span><span class="sxs-lookup"><span data-stu-id="b0919-120">The remote address associated with the channel.</span></span>  
  
### <a name="sessionid"></a><span data-ttu-id="b0919-121">SessionId</span><span class="sxs-lookup"><span data-stu-id="b0919-121">SessionId</span></span>  
 <span data-ttu-id="b0919-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="b0919-122">Data type: string</span></span>  
  
 <span data-ttu-id="b0919-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b0919-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b0919-124">Identyfikator bieżącej sesji, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="b0919-124">The current session Id, if any.</span></span>  
  
### <a name="type"></a><span data-ttu-id="b0919-125">Typ</span><span class="sxs-lookup"><span data-stu-id="b0919-125">Type</span></span>  
 <span data-ttu-id="b0919-126">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="b0919-126">Data type: string</span></span>  
  
 <span data-ttu-id="b0919-127">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b0919-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b0919-128">Typ kanału.</span><span class="sxs-lookup"><span data-stu-id="b0919-128">The type of the channel.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0919-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b0919-129">Requirements</span></span>  
  
|<span data-ttu-id="b0919-130">MOF</span><span class="sxs-lookup"><span data-stu-id="b0919-130">MOF</span></span>|<span data-ttu-id="b0919-131">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="b0919-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b0919-132">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="b0919-132">Namespace</span></span>|<span data-ttu-id="b0919-133">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b0919-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b0919-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b0919-134">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ChannelBase>
