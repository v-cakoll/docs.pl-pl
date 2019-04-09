---
title: TcpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 33bbc1e5-44e4-4ee3-b7b5-801dc78956e4
ms.openlocfilehash: 6d2717bc2d1d14e369af2b9c5a8c0affb67501d9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124231"
---
# <a name="tcptransportbindingelement"></a><span data-ttu-id="ab147-102">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="ab147-102">TcpTransportBindingElement</span></span>
<span data-ttu-id="ab147-103">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="ab147-103">TcpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab147-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ab147-104">Syntax</span></span>  
  
```csharp
class TcpTransportBindingElement : ConnectionOrientedTransportBindingElement  
{  
  TcpConnectionPoolSettings ConnectionPoolSettings;  
  sint32 ListenBacklog;  
  boolean PortSharingEnabled;  
  boolean TeredoEnabled;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ab147-105">Metody</span><span class="sxs-lookup"><span data-stu-id="ab147-105">Methods</span></span>  
 <span data-ttu-id="ab147-106">Klasa TcpTransportBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="ab147-106">The TcpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ab147-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="ab147-107">Properties</span></span>  
 <span data-ttu-id="ab147-108">Klasa TcpTransportBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="ab147-108">The TcpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="connectionpoolsettings"></a><span data-ttu-id="ab147-109">ConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="ab147-109">ConnectionPoolSettings</span></span>  
 <span data-ttu-id="ab147-110">Typ danych: TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="ab147-110">Data type: TcpConnectionPoolSettings</span></span>  
  
 <span data-ttu-id="ab147-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="ab147-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ab147-112">Ustawienia puli połączeń.</span><span class="sxs-lookup"><span data-stu-id="ab147-112">The connection pool settings.</span></span>  
  
### <a name="listenbacklog"></a><span data-ttu-id="ab147-113">ListenBacklog</span><span class="sxs-lookup"><span data-stu-id="ab147-113">ListenBacklog</span></span>  
 <span data-ttu-id="ab147-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="ab147-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="ab147-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="ab147-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ab147-116">Maksymalna liczba żądań w kolejce połączeń, które może być oczekujące.</span><span class="sxs-lookup"><span data-stu-id="ab147-116">The maximum number of queued connection requests that can be pending.</span></span>  
  
### <a name="portsharingenabled"></a><span data-ttu-id="ab147-117">PortSharingEnabled</span><span class="sxs-lookup"><span data-stu-id="ab147-117">PortSharingEnabled</span></span>  
 <span data-ttu-id="ab147-118">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="ab147-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="ab147-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="ab147-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ab147-120">Wartość logiczna określająca, czy włączone jest udostępnianie portów TCP dla tego połączenia.</span><span class="sxs-lookup"><span data-stu-id="ab147-120">A boolean value that specifies whether TCP port sharing is enabled for this connection.</span></span>  
  
### <a name="teredoenabled"></a><span data-ttu-id="ab147-121">TeredoEnabled</span><span class="sxs-lookup"><span data-stu-id="ab147-121">TeredoEnabled</span></span>  
 <span data-ttu-id="ab147-122">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="ab147-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="ab147-123">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="ab147-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ab147-124">Wartość logiczna określająca, czy jest włączony protokół Teredo (technologia adresować klientów znajdujących się za zaporami).</span><span class="sxs-lookup"><span data-stu-id="ab147-124">A boolean value that specifies whether Teredo (a technology for addressing clients that are behind firewalls) is enabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab147-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ab147-125">Requirements</span></span>  
  
|<span data-ttu-id="ab147-126">MOF</span><span class="sxs-lookup"><span data-stu-id="ab147-126">MOF</span></span>|<span data-ttu-id="ab147-127">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="ab147-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ab147-128">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="ab147-128">Namespace</span></span>|<span data-ttu-id="ab147-129">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ab147-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ab147-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ab147-130">See also</span></span>

- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
