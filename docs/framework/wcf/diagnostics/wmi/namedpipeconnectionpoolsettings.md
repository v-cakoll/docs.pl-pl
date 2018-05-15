---
title: NamedPipeConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 079bccb8-54b5-4436-a43d-5567763f72ce
ms.openlocfilehash: 3548a1f19672a98ad0fc81eec15d5be29e5170bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="namedpipeconnectionpoolsettings"></a><span data-ttu-id="4b03b-102">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="4b03b-102">NamedPipeConnectionPoolSettings</span></span>
<span data-ttu-id="4b03b-103">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="4b03b-103">NamedPipeConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b03b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4b03b-104">Syntax</span></span>  
  
```  
class NamedPipeConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="4b03b-105">Metody</span><span class="sxs-lookup"><span data-stu-id="4b03b-105">Methods</span></span>  
 <span data-ttu-id="4b03b-106">Klasa NamedPipeConnectionPoolSettings nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="4b03b-106">The NamedPipeConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4b03b-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="4b03b-107">Properties</span></span>  
 <span data-ttu-id="4b03b-108">Klasa NamedPipeConnectionPoolSettings ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="4b03b-108">The NamedPipeConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="4b03b-109">Nazwa grupy</span><span class="sxs-lookup"><span data-stu-id="4b03b-109">GroupName</span></span>  
 <span data-ttu-id="4b03b-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="4b03b-110">Data type: string</span></span>  
  
 <span data-ttu-id="4b03b-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4b03b-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4b03b-112">Nazwa grupy puli połączeń używanej przez element powiązania.</span><span class="sxs-lookup"><span data-stu-id="4b03b-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="4b03b-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="4b03b-113">IdleTimeout</span></span>  
 <span data-ttu-id="4b03b-114">Typ danych: daty i godziny</span><span class="sxs-lookup"><span data-stu-id="4b03b-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="4b03b-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4b03b-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4b03b-116">Maksymalny czas, który połączenie może być bezczynne, zanim zostanie rozłączone.</span><span class="sxs-lookup"><span data-stu-id="4b03b-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="4b03b-117">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="4b03b-117">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="4b03b-118">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="4b03b-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="4b03b-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4b03b-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4b03b-120">Maksymalna liczba połączeń wychodzących dla każdego punktu końcowego na kliencie.</span><span class="sxs-lookup"><span data-stu-id="4b03b-120">The maximum number of outbound connections for each endpoint on the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b03b-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4b03b-121">Requirements</span></span>  
  
|<span data-ttu-id="4b03b-122">MOF</span><span class="sxs-lookup"><span data-stu-id="4b03b-122">MOF</span></span>|<span data-ttu-id="4b03b-123">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="4b03b-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4b03b-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="4b03b-124">Namespace</span></span>|<span data-ttu-id="4b03b-125">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4b03b-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4b03b-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4b03b-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
