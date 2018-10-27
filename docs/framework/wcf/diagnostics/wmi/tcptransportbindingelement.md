---
title: TcpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 33bbc1e5-44e4-4ee3-b7b5-801dc78956e4
ms.openlocfilehash: 04326484bbf1f07c66ad8fb401642880f9ba8c6e
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50193932"
---
# <a name="tcptransportbindingelement"></a><span data-ttu-id="b539f-102">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="b539f-102">TcpTransportBindingElement</span></span>
<span data-ttu-id="b539f-103">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="b539f-103">TcpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b539f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b539f-104">Syntax</span></span>  
  
```csharp
class TcpTransportBindingElement : ConnectionOrientedTransportBindingElement  
{  
  TcpConnectionPoolSettings ConnectionPoolSettings;  
  sint32 ListenBacklog;  
  boolean PortSharingEnabled;  
  boolean TeredoEnabled;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b539f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b539f-105">Methods</span></span>  
 <span data-ttu-id="b539f-106">Klasa TcpTransportBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="b539f-106">The TcpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b539f-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="b539f-107">Properties</span></span>  
 <span data-ttu-id="b539f-108">Klasa TcpTransportBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="b539f-108">The TcpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="connectionpoolsettings"></a><span data-ttu-id="b539f-109">connectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="b539f-109">ConnectionPoolSettings</span></span>  
 <span data-ttu-id="b539f-110">Typ danych: TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="b539f-110">Data type: TcpConnectionPoolSettings</span></span>  
  
 <span data-ttu-id="b539f-111">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b539f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b539f-112">Ustawienia puli połączeń.</span><span class="sxs-lookup"><span data-stu-id="b539f-112">The connection pool settings.</span></span>  
  
### <a name="listenbacklog"></a><span data-ttu-id="b539f-113">listenBacklog</span><span class="sxs-lookup"><span data-stu-id="b539f-113">ListenBacklog</span></span>  
 <span data-ttu-id="b539f-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="b539f-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="b539f-115">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b539f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b539f-116">Maksymalna liczba żądań w kolejce połączeń, które może być oczekujące.</span><span class="sxs-lookup"><span data-stu-id="b539f-116">The maximum number of queued connection requests that can be pending.</span></span>  
  
### <a name="portsharingenabled"></a><span data-ttu-id="b539f-117">portSharingEnabled</span><span class="sxs-lookup"><span data-stu-id="b539f-117">PortSharingEnabled</span></span>  
 <span data-ttu-id="b539f-118">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="b539f-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="b539f-119">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b539f-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b539f-120">Wartość logiczna określająca, czy włączone jest udostępnianie portów TCP dla tego połączenia.</span><span class="sxs-lookup"><span data-stu-id="b539f-120">A boolean value that specifies whether TCP port sharing is enabled for this connection.</span></span>  
  
### <a name="teredoenabled"></a><span data-ttu-id="b539f-121">teredoEnabled</span><span class="sxs-lookup"><span data-stu-id="b539f-121">TeredoEnabled</span></span>  
 <span data-ttu-id="b539f-122">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="b539f-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="b539f-123">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b539f-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b539f-124">Wartość logiczna określająca, czy jest włączony protokół Teredo (technologia adresować klientów znajdujących się za zaporami).</span><span class="sxs-lookup"><span data-stu-id="b539f-124">A boolean value that specifies whether Teredo (a technology for addressing clients that are behind firewalls) is enabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b539f-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b539f-125">Requirements</span></span>  
  
|<span data-ttu-id="b539f-126">PLIK MOF</span><span class="sxs-lookup"><span data-stu-id="b539f-126">MOF</span></span>|<span data-ttu-id="b539f-127">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="b539f-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b539f-128">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="b539f-128">Namespace</span></span>|<span data-ttu-id="b539f-129">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b539f-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b539f-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b539f-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
