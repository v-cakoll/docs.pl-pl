---
title: TcpTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33bbc1e5-44e4-4ee3-b7b5-801dc78956e4
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4b9aa7e0d9eaba0181b17b44da1bf871c10af814
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="tcptransportbindingelement"></a><span data-ttu-id="40744-102">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="40744-102">TcpTransportBindingElement</span></span>
<span data-ttu-id="40744-103">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="40744-103">TcpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40744-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="40744-104">Syntax</span></span>  
  
```  
class TcpTransportBindingElement : ConnectionOrientedTransportBindingElement  
{  
  TcpConnectionPoolSettings ConnectionPoolSettings;  
  sint32 ListenBacklog;  
  boolean PortSharingEnabled;  
  boolean TeredoEnabled;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="40744-105">Metody</span><span class="sxs-lookup"><span data-stu-id="40744-105">Methods</span></span>  
 <span data-ttu-id="40744-106">Klasa TcpTransportBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="40744-106">The TcpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="40744-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="40744-107">Properties</span></span>  
 <span data-ttu-id="40744-108">Klasa TcpTransportBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="40744-108">The TcpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="connectionpoolsettings"></a><span data-ttu-id="40744-109">ConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="40744-109">ConnectionPoolSettings</span></span>  
 <span data-ttu-id="40744-110">Typ danych: TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="40744-110">Data type: TcpConnectionPoolSettings</span></span>  
  
 <span data-ttu-id="40744-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="40744-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="40744-112">Ustawienia puli połączeń.</span><span class="sxs-lookup"><span data-stu-id="40744-112">The connection pool settings.</span></span>  
  
### <a name="listenbacklog"></a><span data-ttu-id="40744-113">ListenBacklog</span><span class="sxs-lookup"><span data-stu-id="40744-113">ListenBacklog</span></span>  
 <span data-ttu-id="40744-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="40744-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="40744-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="40744-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="40744-116">Maksymalna liczba oczekujących żądań połączenia w kolejce.</span><span class="sxs-lookup"><span data-stu-id="40744-116">The maximum number of queued connection requests that can be pending.</span></span>  
  
### <a name="portsharingenabled"></a><span data-ttu-id="40744-117">PortSharingEnabled</span><span class="sxs-lookup"><span data-stu-id="40744-117">PortSharingEnabled</span></span>  
 <span data-ttu-id="40744-118">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="40744-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="40744-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="40744-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="40744-120">Wartość logiczna określająca, czy włączone jest udostępnianie portów TCP dla tego połączenia.</span><span class="sxs-lookup"><span data-stu-id="40744-120">A boolean value that specifies whether TCP port sharing is enabled for this connection.</span></span>  
  
### <a name="teredoenabled"></a><span data-ttu-id="40744-121">TeredoEnabled</span><span class="sxs-lookup"><span data-stu-id="40744-121">TeredoEnabled</span></span>  
 <span data-ttu-id="40744-122">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="40744-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="40744-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="40744-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="40744-124">Wartość logiczna określająca czy włączona jest obsługa technologii Teredo (pozwalającej adresować klientów znajdujących się za zaporą).</span><span class="sxs-lookup"><span data-stu-id="40744-124">A boolean value that specifies whether Teredo (a technology for addressing clients that are behind firewalls) is enabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40744-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="40744-125">Requirements</span></span>  
  
|<span data-ttu-id="40744-126">MOF</span><span class="sxs-lookup"><span data-stu-id="40744-126">MOF</span></span>|<span data-ttu-id="40744-127">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="40744-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="40744-128">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="40744-128">Namespace</span></span>|<span data-ttu-id="40744-129">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="40744-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="40744-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="40744-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
