---
title: NamedPipeConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 079bccb8-54b5-4436-a43d-5567763f72ce
ms.openlocfilehash: 77d8403947d341ea2efcef98bbf166f94f75f31f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188732"
---
# <a name="namedpipeconnectionpoolsettings"></a><span data-ttu-id="c5929-102">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="c5929-102">NamedPipeConnectionPoolSettings</span></span>
<span data-ttu-id="c5929-103">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="c5929-103">NamedPipeConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5929-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c5929-104">Syntax</span></span>  
  
```csharp
class NamedPipeConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="c5929-105">Metody</span><span class="sxs-lookup"><span data-stu-id="c5929-105">Methods</span></span>  
 <span data-ttu-id="c5929-106">Klasa NamedPipeConnectionPoolSettings nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="c5929-106">The NamedPipeConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c5929-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="c5929-107">Properties</span></span>  
 <span data-ttu-id="c5929-108">Klasa NamedPipeConnectionPoolSettings ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="c5929-108">The NamedPipeConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="c5929-109">Nazwa grupy</span><span class="sxs-lookup"><span data-stu-id="c5929-109">GroupName</span></span>  
 <span data-ttu-id="c5929-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="c5929-110">Data type: string</span></span>  
  
 <span data-ttu-id="c5929-111">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="c5929-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c5929-112">Nazwa grupy puli połączeń używane przez element powiązania.</span><span class="sxs-lookup"><span data-stu-id="c5929-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="c5929-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="c5929-113">IdleTimeout</span></span>  
 <span data-ttu-id="c5929-114">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="c5929-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="c5929-115">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="c5929-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c5929-116">Maksymalny czas, który połączenie może być bezczynne, zanim zostanie rozłączone.</span><span class="sxs-lookup"><span data-stu-id="c5929-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="c5929-117">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="c5929-117">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="c5929-118">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="c5929-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="c5929-119">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="c5929-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c5929-120">Maksymalna liczba połączeń wychodzących dla każdego punktu końcowego na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="c5929-120">The maximum number of outbound connections for each endpoint on the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5929-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c5929-121">Requirements</span></span>  
  
|<span data-ttu-id="c5929-122">PLIK MOF</span><span class="sxs-lookup"><span data-stu-id="c5929-122">MOF</span></span>|<span data-ttu-id="c5929-123">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="c5929-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="c5929-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="c5929-124">Namespace</span></span>|<span data-ttu-id="c5929-125">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c5929-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c5929-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c5929-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
