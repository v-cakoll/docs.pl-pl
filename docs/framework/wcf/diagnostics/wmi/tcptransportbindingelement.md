---
title: TcpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 33bbc1e5-44e4-4ee3-b7b5-801dc78956e4
ms.openlocfilehash: 0d5dc5c9b9bf2313d18c9fadb1a2adb87c1b11b1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54610789"
---
# <a name="tcptransportbindingelement"></a><span data-ttu-id="f2128-102">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="f2128-102">TcpTransportBindingElement</span></span>
<span data-ttu-id="f2128-103">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="f2128-103">TcpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2128-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f2128-104">Syntax</span></span>  
  
```csharp
class TcpTransportBindingElement : ConnectionOrientedTransportBindingElement  
{  
  TcpConnectionPoolSettings ConnectionPoolSettings;  
  sint32 ListenBacklog;  
  boolean PortSharingEnabled;  
  boolean TeredoEnabled;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="f2128-105">Metody</span><span class="sxs-lookup"><span data-stu-id="f2128-105">Methods</span></span>  
 <span data-ttu-id="f2128-106">Klasa TcpTransportBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="f2128-106">The TcpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f2128-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="f2128-107">Properties</span></span>  
 <span data-ttu-id="f2128-108">Klasa TcpTransportBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="f2128-108">The TcpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="connectionpoolsettings"></a><span data-ttu-id="f2128-109">ConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="f2128-109">ConnectionPoolSettings</span></span>  
 <span data-ttu-id="f2128-110">Typ danych: TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="f2128-110">Data type: TcpConnectionPoolSettings</span></span>  
  
 <span data-ttu-id="f2128-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f2128-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f2128-112">Ustawienia puli połączeń.</span><span class="sxs-lookup"><span data-stu-id="f2128-112">The connection pool settings.</span></span>  
  
### <a name="listenbacklog"></a><span data-ttu-id="f2128-113">ListenBacklog</span><span class="sxs-lookup"><span data-stu-id="f2128-113">ListenBacklog</span></span>  
 <span data-ttu-id="f2128-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="f2128-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="f2128-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f2128-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f2128-116">Maksymalna liczba żądań w kolejce połączeń, które może być oczekujące.</span><span class="sxs-lookup"><span data-stu-id="f2128-116">The maximum number of queued connection requests that can be pending.</span></span>  
  
### <a name="portsharingenabled"></a><span data-ttu-id="f2128-117">PortSharingEnabled</span><span class="sxs-lookup"><span data-stu-id="f2128-117">PortSharingEnabled</span></span>  
 <span data-ttu-id="f2128-118">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="f2128-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="f2128-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f2128-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f2128-120">Wartość logiczna określająca, czy włączone jest udostępnianie portów TCP dla tego połączenia.</span><span class="sxs-lookup"><span data-stu-id="f2128-120">A boolean value that specifies whether TCP port sharing is enabled for this connection.</span></span>  
  
### <a name="teredoenabled"></a><span data-ttu-id="f2128-121">TeredoEnabled</span><span class="sxs-lookup"><span data-stu-id="f2128-121">TeredoEnabled</span></span>  
 <span data-ttu-id="f2128-122">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="f2128-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="f2128-123">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f2128-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f2128-124">Wartość logiczna określająca, czy jest włączony protokół Teredo (technologia adresować klientów znajdujących się za zaporami).</span><span class="sxs-lookup"><span data-stu-id="f2128-124">A boolean value that specifies whether Teredo (a technology for addressing clients that are behind firewalls) is enabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2128-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f2128-125">Requirements</span></span>  
  
|<span data-ttu-id="f2128-126">MOF</span><span class="sxs-lookup"><span data-stu-id="f2128-126">MOF</span></span>|<span data-ttu-id="f2128-127">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="f2128-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f2128-128">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="f2128-128">Namespace</span></span>|<span data-ttu-id="f2128-129">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f2128-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f2128-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f2128-130">See also</span></span>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
