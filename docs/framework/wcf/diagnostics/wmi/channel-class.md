---
title: Klasa kanału
ms.date: 03/30/2017
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
ms.openlocfilehash: 108d5f8e3cd092863dbd48e2bb9d180798b091a4
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2018
ms.locfileid: "50197876"
---
# <a name="channel-class"></a><span data-ttu-id="278be-102">Klasa kanału</span><span class="sxs-lookup"><span data-stu-id="278be-102">Channel class</span></span>
<span data-ttu-id="278be-103">Kanał</span><span class="sxs-lookup"><span data-stu-id="278be-103">Channel</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="278be-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="278be-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="278be-105">Metody</span><span class="sxs-lookup"><span data-stu-id="278be-105">Methods</span></span>  
 <span data-ttu-id="278be-106">Klasa kanału nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="278be-106">The Channel class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="278be-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="278be-107">Properties</span></span>  
 <span data-ttu-id="278be-108">Klasa kanału ma następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="278be-108">The Channel class has the following properties.</span></span>  
  
### <a name="localaddress"></a><span data-ttu-id="278be-109">LocalAddress</span><span class="sxs-lookup"><span data-stu-id="278be-109">LocalAddress</span></span>  
 <span data-ttu-id="278be-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="278be-110">Data type: string</span></span>  
  
 <span data-ttu-id="278be-111">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="278be-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="278be-112">Lokalny punkt końcowy dla kanału.</span><span class="sxs-lookup"><span data-stu-id="278be-112">The local endpoint for the channel.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="278be-113">ref</span><span class="sxs-lookup"><span data-stu-id="278be-113">ref</span></span>  
 <span data-ttu-id="278be-114">Typ danych: punkt końcowy</span><span class="sxs-lookup"><span data-stu-id="278be-114">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="278be-115">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="278be-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="278be-116">Łączy się z odwołaniem do punktu końcowego kanału.</span><span class="sxs-lookup"><span data-stu-id="278be-116">A reference to the endpoint the channel connects to.</span></span>  
  
### <a name="remoteaddress"></a><span data-ttu-id="278be-117">Obiekt RemoteAddress</span><span class="sxs-lookup"><span data-stu-id="278be-117">RemoteAddress</span></span>  
 <span data-ttu-id="278be-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="278be-118">Data type: string</span></span>  
  
 <span data-ttu-id="278be-119">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="278be-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="278be-120">Zdalny adres skojarzony z kanałem.</span><span class="sxs-lookup"><span data-stu-id="278be-120">The remote address associated with the channel.</span></span>  
  
### <a name="sessionid"></a><span data-ttu-id="278be-121">SessionId</span><span class="sxs-lookup"><span data-stu-id="278be-121">SessionId</span></span>  
 <span data-ttu-id="278be-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="278be-122">Data type: string</span></span>  
  
 <span data-ttu-id="278be-123">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="278be-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="278be-124">Identyfikator bieżącej sesji, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="278be-124">The current session Id, if any.</span></span>  
  
### <a name="type"></a><span data-ttu-id="278be-125">Typ</span><span class="sxs-lookup"><span data-stu-id="278be-125">Type</span></span>  
 <span data-ttu-id="278be-126">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="278be-126">Data type: string</span></span>  
  
 <span data-ttu-id="278be-127">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="278be-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="278be-128">Typ kanału.</span><span class="sxs-lookup"><span data-stu-id="278be-128">The type of the channel.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="278be-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="278be-129">Requirements</span></span>  
  
|<span data-ttu-id="278be-130">PLIK MOF</span><span class="sxs-lookup"><span data-stu-id="278be-130">MOF</span></span>|<span data-ttu-id="278be-131">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="278be-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="278be-132">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="278be-132">Namespace</span></span>|<span data-ttu-id="278be-133">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="278be-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="278be-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="278be-134">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ChannelBase>
