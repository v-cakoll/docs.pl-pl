---
title: TcpConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 19acfba3-c057-4dbc-bac7-8674d7844d83
ms.openlocfilehash: 4a30ad3ddfef5d39942345b0e0d5274eeff8e596
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485925"
---
# <a name="tcpconnectionpoolsettings"></a><span data-ttu-id="3bc74-102">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="3bc74-102">TcpConnectionPoolSettings</span></span>
<span data-ttu-id="3bc74-103">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="3bc74-103">TcpConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bc74-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3bc74-104">Syntax</span></span>  
  
```  
class TcpConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="3bc74-105">Metody</span><span class="sxs-lookup"><span data-stu-id="3bc74-105">Methods</span></span>  
 <span data-ttu-id="3bc74-106">Klasa TcpConnectionPoolSettings nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="3bc74-106">The TcpConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="3bc74-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="3bc74-107">Properties</span></span>  
 <span data-ttu-id="3bc74-108">Klasa TcpConnectionPoolSettings ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="3bc74-108">The TcpConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="3bc74-109">Nazwa grupy</span><span class="sxs-lookup"><span data-stu-id="3bc74-109">GroupName</span></span>  
 <span data-ttu-id="3bc74-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="3bc74-110">Data type: string</span></span>  
  
 <span data-ttu-id="3bc74-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="3bc74-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3bc74-112">Nazwa grupy puli połączeń używanej przez element powiązania.</span><span class="sxs-lookup"><span data-stu-id="3bc74-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="3bc74-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="3bc74-113">IdleTimeout</span></span>  
 <span data-ttu-id="3bc74-114">Typ danych: daty i godziny</span><span class="sxs-lookup"><span data-stu-id="3bc74-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="3bc74-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="3bc74-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3bc74-116">Maksymalny czas, który połączenie może być bezczynne, zanim zostanie rozłączone.</span><span class="sxs-lookup"><span data-stu-id="3bc74-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="3bc74-117">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="3bc74-117">LeaseTimeout</span></span>  
 <span data-ttu-id="3bc74-118">Typ danych: daty i godziny</span><span class="sxs-lookup"><span data-stu-id="3bc74-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="3bc74-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="3bc74-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3bc74-120">Maksymalny czas na ukończenie przed przekroczeniem limitu czasu operacji dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="3bc74-120">The maximum time for the lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="3bc74-121">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="3bc74-121">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="3bc74-122">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="3bc74-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="3bc74-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="3bc74-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3bc74-124">Maksymalna liczba połączeń wychodzących dla każdego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="3bc74-124">The maximum outbound connections for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3bc74-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3bc74-125">Requirements</span></span>  
  
|<span data-ttu-id="3bc74-126">MOF</span><span class="sxs-lookup"><span data-stu-id="3bc74-126">MOF</span></span>|<span data-ttu-id="3bc74-127">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="3bc74-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="3bc74-128">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="3bc74-128">Namespace</span></span>|<span data-ttu-id="3bc74-129">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="3bc74-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3bc74-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3bc74-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
