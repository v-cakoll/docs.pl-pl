---
title: TcpConnectionPoolSettings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19acfba3-c057-4dbc-bac7-8674d7844d83
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5038d093333eca9ca191c3ecae4cfa889d723276
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="tcpconnectionpoolsettings"></a><span data-ttu-id="6136f-102">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="6136f-102">TcpConnectionPoolSettings</span></span>
<span data-ttu-id="6136f-103">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="6136f-103">TcpConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6136f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6136f-104">Syntax</span></span>  
  
```  
class TcpConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="6136f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="6136f-105">Methods</span></span>  
 <span data-ttu-id="6136f-106">Klasa TcpConnectionPoolSettings nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="6136f-106">The TcpConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="6136f-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="6136f-107">Properties</span></span>  
 <span data-ttu-id="6136f-108">Klasa TcpConnectionPoolSettings ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="6136f-108">The TcpConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="6136f-109">Nazwa grupy</span><span class="sxs-lookup"><span data-stu-id="6136f-109">GroupName</span></span>  
 <span data-ttu-id="6136f-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="6136f-110">Data type: string</span></span>  
  
 <span data-ttu-id="6136f-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="6136f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6136f-112">Nazwa grupy puli połączeń używanej przez element powiązania.</span><span class="sxs-lookup"><span data-stu-id="6136f-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="6136f-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="6136f-113">IdleTimeout</span></span>  
 <span data-ttu-id="6136f-114">Typ danych: daty i godziny</span><span class="sxs-lookup"><span data-stu-id="6136f-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="6136f-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="6136f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6136f-116">Maksymalny czas, który połączenie może być bezczynne, zanim zostanie rozłączone.</span><span class="sxs-lookup"><span data-stu-id="6136f-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="6136f-117">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="6136f-117">LeaseTimeout</span></span>  
 <span data-ttu-id="6136f-118">Typ danych: daty i godziny</span><span class="sxs-lookup"><span data-stu-id="6136f-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="6136f-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="6136f-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6136f-120">Maksymalny czas na ukończenie przed przekroczeniem limitu czasu operacji dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="6136f-120">The maximum time for the lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="6136f-121">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="6136f-121">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="6136f-122">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="6136f-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="6136f-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="6136f-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6136f-124">Maksymalna liczba połączeń wychodzących dla każdego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="6136f-124">The maximum outbound connections for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6136f-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6136f-125">Requirements</span></span>  
  
|<span data-ttu-id="6136f-126">MOF</span><span class="sxs-lookup"><span data-stu-id="6136f-126">MOF</span></span>|<span data-ttu-id="6136f-127">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="6136f-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="6136f-128">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="6136f-128">Namespace</span></span>|<span data-ttu-id="6136f-129">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="6136f-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6136f-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6136f-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
