---
title: Klasa kanału
ms.date: 03/30/2017
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
ms.openlocfilehash: 108d5f8e3cd092863dbd48e2bb9d180798b091a4
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50047374"
---
# <a name="channel-class"></a><span data-ttu-id="abb21-102">Klasa kanału</span><span class="sxs-lookup"><span data-stu-id="abb21-102">Channel class</span></span>
<span data-ttu-id="abb21-103">Kanał</span><span class="sxs-lookup"><span data-stu-id="abb21-103">Channel</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abb21-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="abb21-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="abb21-105">Metody</span><span class="sxs-lookup"><span data-stu-id="abb21-105">Methods</span></span>  
 <span data-ttu-id="abb21-106">Klasa kanału nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="abb21-106">The Channel class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="abb21-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="abb21-107">Properties</span></span>  
 <span data-ttu-id="abb21-108">Klasa kanału ma następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="abb21-108">The Channel class has the following properties.</span></span>  
  
### <a name="localaddress"></a><span data-ttu-id="abb21-109">LocalAddress</span><span class="sxs-lookup"><span data-stu-id="abb21-109">LocalAddress</span></span>  
 <span data-ttu-id="abb21-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="abb21-110">Data type: string</span></span>  
  
 <span data-ttu-id="abb21-111">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="abb21-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="abb21-112">Lokalny punkt końcowy dla kanału.</span><span class="sxs-lookup"><span data-stu-id="abb21-112">The local endpoint for the channel.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="abb21-113">ref</span><span class="sxs-lookup"><span data-stu-id="abb21-113">ref</span></span>  
 <span data-ttu-id="abb21-114">Typ danych: punkt końcowy</span><span class="sxs-lookup"><span data-stu-id="abb21-114">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="abb21-115">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="abb21-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="abb21-116">Łączy się z odwołaniem do punktu końcowego kanału.</span><span class="sxs-lookup"><span data-stu-id="abb21-116">A reference to the endpoint the channel connects to.</span></span>  
  
### <a name="remoteaddress"></a><span data-ttu-id="abb21-117">Obiekt RemoteAddress</span><span class="sxs-lookup"><span data-stu-id="abb21-117">RemoteAddress</span></span>  
 <span data-ttu-id="abb21-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="abb21-118">Data type: string</span></span>  
  
 <span data-ttu-id="abb21-119">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="abb21-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="abb21-120">Zdalny adres skojarzony z kanałem.</span><span class="sxs-lookup"><span data-stu-id="abb21-120">The remote address associated with the channel.</span></span>  
  
### <a name="sessionid"></a><span data-ttu-id="abb21-121">SessionId</span><span class="sxs-lookup"><span data-stu-id="abb21-121">SessionId</span></span>  
 <span data-ttu-id="abb21-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="abb21-122">Data type: string</span></span>  
  
 <span data-ttu-id="abb21-123">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="abb21-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="abb21-124">Identyfikator bieżącej sesji, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="abb21-124">The current session Id, if any.</span></span>  
  
### <a name="type"></a><span data-ttu-id="abb21-125">Typ</span><span class="sxs-lookup"><span data-stu-id="abb21-125">Type</span></span>  
 <span data-ttu-id="abb21-126">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="abb21-126">Data type: string</span></span>  
  
 <span data-ttu-id="abb21-127">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="abb21-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="abb21-128">Typ kanału.</span><span class="sxs-lookup"><span data-stu-id="abb21-128">The type of the channel.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abb21-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="abb21-129">Requirements</span></span>  
  
|<span data-ttu-id="abb21-130">PLIK MOF</span><span class="sxs-lookup"><span data-stu-id="abb21-130">MOF</span></span>|<span data-ttu-id="abb21-131">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="abb21-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="abb21-132">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="abb21-132">Namespace</span></span>|<span data-ttu-id="abb21-133">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="abb21-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="abb21-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="abb21-134">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ChannelBase>
