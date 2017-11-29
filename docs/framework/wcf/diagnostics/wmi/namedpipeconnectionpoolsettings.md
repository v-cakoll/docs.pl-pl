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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cf9c39334289cb30d1a01917c0be37da02fcdc5b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="namedpipeconnectionpoolsettings"></a><span data-ttu-id="dd411-102">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="dd411-102">NamedPipeConnectionPoolSettings</span></span>
<span data-ttu-id="dd411-103">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="dd411-103">NamedPipeConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd411-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dd411-104">Syntax</span></span>  
  
```  
class NamedPipeConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="dd411-105">Metody</span><span class="sxs-lookup"><span data-stu-id="dd411-105">Methods</span></span>  
 <span data-ttu-id="dd411-106">Klasa NamedPipeConnectionPoolSettings nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="dd411-106">The NamedPipeConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="dd411-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="dd411-107">Properties</span></span>  
 <span data-ttu-id="dd411-108">Klasa NamedPipeConnectionPoolSettings ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="dd411-108">The NamedPipeConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="dd411-109">Nazwa grupy</span><span class="sxs-lookup"><span data-stu-id="dd411-109">GroupName</span></span>  
 <span data-ttu-id="dd411-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="dd411-110">Data type: string</span></span>  
  
 <span data-ttu-id="dd411-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="dd411-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dd411-112">Nazwa grupy puli połączeń używanej przez element powiązania.</span><span class="sxs-lookup"><span data-stu-id="dd411-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="dd411-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="dd411-113">IdleTimeout</span></span>  
 <span data-ttu-id="dd411-114">Typ danych: daty i godziny</span><span class="sxs-lookup"><span data-stu-id="dd411-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="dd411-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="dd411-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dd411-116">Maksymalny czas, który połączenie może być bezczynne, zanim zostanie rozłączone.</span><span class="sxs-lookup"><span data-stu-id="dd411-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="dd411-117">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="dd411-117">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="dd411-118">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="dd411-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="dd411-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="dd411-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dd411-120">Maksymalna liczba połączeń wychodzących dla każdego punktu końcowego na kliencie.</span><span class="sxs-lookup"><span data-stu-id="dd411-120">The maximum number of outbound connections for each endpoint on the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd411-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dd411-121">Requirements</span></span>  
  
|<span data-ttu-id="dd411-122">MOF</span><span class="sxs-lookup"><span data-stu-id="dd411-122">MOF</span></span>|<span data-ttu-id="dd411-123">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="dd411-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="dd411-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="dd411-124">Namespace</span></span>|<span data-ttu-id="dd411-125">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="dd411-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dd411-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dd411-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
