---
title: TcpConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 19acfba3-c057-4dbc-bac7-8674d7844d83
ms.openlocfilehash: 6fa68eed241edaea40b66c31240a4201e05779f4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59975356"
---
# <a name="tcpconnectionpoolsettings"></a><span data-ttu-id="5d07f-102">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="5d07f-102">TcpConnectionPoolSettings</span></span>
<span data-ttu-id="5d07f-103">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="5d07f-103">TcpConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d07f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5d07f-104">Syntax</span></span>  
  
```csharp
class TcpConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="5d07f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="5d07f-105">Methods</span></span>  
 <span data-ttu-id="5d07f-106">Klasa TcpConnectionPoolSettings nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="5d07f-106">The TcpConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="5d07f-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="5d07f-107">Properties</span></span>  
 <span data-ttu-id="5d07f-108">Klasa TcpConnectionPoolSettings ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="5d07f-108">The TcpConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="5d07f-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="5d07f-109">GroupName</span></span>  
 <span data-ttu-id="5d07f-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="5d07f-110">Data type: string</span></span>  
  
 <span data-ttu-id="5d07f-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="5d07f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5d07f-112">Nazwa grupy puli połączeń używane przez element powiązania.</span><span class="sxs-lookup"><span data-stu-id="5d07f-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="5d07f-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="5d07f-113">IdleTimeout</span></span>  
 <span data-ttu-id="5d07f-114">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="5d07f-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="5d07f-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="5d07f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5d07f-116">Maksymalny czas, który połączenie może być bezczynne, zanim zostanie rozłączone.</span><span class="sxs-lookup"><span data-stu-id="5d07f-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="5d07f-117">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="5d07f-117">LeaseTimeout</span></span>  
 <span data-ttu-id="5d07f-118">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="5d07f-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="5d07f-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="5d07f-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5d07f-120">Maksymalny czas na ukończenie przed przekroczeniem limitu czasu operacji dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="5d07f-120">The maximum time for the lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="5d07f-121">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="5d07f-121">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="5d07f-122">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="5d07f-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="5d07f-123">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="5d07f-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5d07f-124">Maksymalna liczba połączeń wychodzących dla każdego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="5d07f-124">The maximum outbound connections for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d07f-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5d07f-125">Requirements</span></span>  
  
|<span data-ttu-id="5d07f-126">MOF</span><span class="sxs-lookup"><span data-stu-id="5d07f-126">MOF</span></span>|<span data-ttu-id="5d07f-127">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="5d07f-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="5d07f-128">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="5d07f-128">Namespace</span></span>|<span data-ttu-id="5d07f-129">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="5d07f-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5d07f-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5d07f-130">See also</span></span>

- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
