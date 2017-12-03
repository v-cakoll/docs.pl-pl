---
title: NamedPipeConnectionPoolSettings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 079bccb8-54b5-4436-a43d-5567763f72ce
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 18740c4c87aaeafcd0a28991376e0c45fe688223
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="namedpipeconnectionpoolsettings"></a><span data-ttu-id="2b092-102">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="2b092-102">NamedPipeConnectionPoolSettings</span></span>
<span data-ttu-id="2b092-103">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="2b092-103">NamedPipeConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b092-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2b092-104">Syntax</span></span>  
  
```  
class NamedPipeConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="2b092-105">Metody</span><span class="sxs-lookup"><span data-stu-id="2b092-105">Methods</span></span>  
 <span data-ttu-id="2b092-106">Klasa NamedPipeConnectionPoolSettings nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="2b092-106">The NamedPipeConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="2b092-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="2b092-107">Properties</span></span>  
 <span data-ttu-id="2b092-108">Klasa NamedPipeConnectionPoolSettings ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="2b092-108">The NamedPipeConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="2b092-109">Nazwa grupy</span><span class="sxs-lookup"><span data-stu-id="2b092-109">GroupName</span></span>  
 <span data-ttu-id="2b092-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="2b092-110">Data type: string</span></span>  
  
 <span data-ttu-id="2b092-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="2b092-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2b092-112">Nazwa grupy puli połączeń używanej przez element powiązania.</span><span class="sxs-lookup"><span data-stu-id="2b092-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="2b092-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="2b092-113">IdleTimeout</span></span>  
 <span data-ttu-id="2b092-114">Typ danych: daty i godziny</span><span class="sxs-lookup"><span data-stu-id="2b092-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="2b092-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="2b092-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2b092-116">Maksymalny czas, który połączenie może być bezczynne, zanim zostanie rozłączone.</span><span class="sxs-lookup"><span data-stu-id="2b092-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="2b092-117">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="2b092-117">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="2b092-118">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="2b092-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="2b092-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="2b092-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2b092-120">Maksymalna liczba połączeń wychodzących dla każdego punktu końcowego na kliencie.</span><span class="sxs-lookup"><span data-stu-id="2b092-120">The maximum number of outbound connections for each endpoint on the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b092-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2b092-121">Requirements</span></span>  
  
|<span data-ttu-id="2b092-122">MOF</span><span class="sxs-lookup"><span data-stu-id="2b092-122">MOF</span></span>|<span data-ttu-id="2b092-123">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="2b092-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="2b092-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="2b092-124">Namespace</span></span>|<span data-ttu-id="2b092-125">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="2b092-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2b092-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2b092-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
