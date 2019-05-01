---
title: NamedPipeConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 079bccb8-54b5-4436-a43d-5567763f72ce
ms.openlocfilehash: 8c2d4bfc08a503a8d6eb0e8abf6f1e798b90bc83
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963218"
---
# <a name="namedpipeconnectionpoolsettings"></a><span data-ttu-id="0177a-102">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="0177a-102">NamedPipeConnectionPoolSettings</span></span>
<span data-ttu-id="0177a-103">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="0177a-103">NamedPipeConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0177a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0177a-104">Syntax</span></span>  
  
```csharp
class NamedPipeConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="0177a-105">Metody</span><span class="sxs-lookup"><span data-stu-id="0177a-105">Methods</span></span>  
 <span data-ttu-id="0177a-106">Klasa NamedPipeConnectionPoolSettings nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="0177a-106">The NamedPipeConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="0177a-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="0177a-107">Properties</span></span>  
 <span data-ttu-id="0177a-108">Klasa NamedPipeConnectionPoolSettings ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="0177a-108">The NamedPipeConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="0177a-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="0177a-109">GroupName</span></span>  
 <span data-ttu-id="0177a-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="0177a-110">Data type: string</span></span>  
  
 <span data-ttu-id="0177a-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="0177a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0177a-112">Nazwa grupy puli połączeń używane przez element powiązania.</span><span class="sxs-lookup"><span data-stu-id="0177a-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="0177a-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="0177a-113">IdleTimeout</span></span>  
 <span data-ttu-id="0177a-114">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="0177a-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="0177a-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="0177a-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0177a-116">Maksymalny czas, który połączenie może być bezczynne, zanim zostanie rozłączone.</span><span class="sxs-lookup"><span data-stu-id="0177a-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="0177a-117">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="0177a-117">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="0177a-118">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="0177a-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="0177a-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="0177a-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0177a-120">Maksymalna liczba połączeń wychodzących dla każdego punktu końcowego na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="0177a-120">The maximum number of outbound connections for each endpoint on the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0177a-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0177a-121">Requirements</span></span>  
  
|<span data-ttu-id="0177a-122">MOF</span><span class="sxs-lookup"><span data-stu-id="0177a-122">MOF</span></span>|<span data-ttu-id="0177a-123">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="0177a-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="0177a-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="0177a-124">Namespace</span></span>|<span data-ttu-id="0177a-125">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="0177a-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0177a-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0177a-126">See also</span></span>

- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
