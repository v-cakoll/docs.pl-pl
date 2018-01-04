---
title: "Rozszerzanie warstwy kanału"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: extending channels [WCF]
ms.assetid: 4238db74-2fb6-4dc8-a326-f58527230810
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5a1a1bb0b1f2c5e6b42ee793f18f5ad442b1fe8e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="extending-the-channel-layer"></a><span data-ttu-id="a6b5b-102">Rozszerzanie warstwy kanału</span><span class="sxs-lookup"><span data-stu-id="a6b5b-102">Extending the Channel Layer</span></span>
<span data-ttu-id="a6b5b-103">Warstwie kanału jest odpowiedzialny za wymiana wiadomości między klientami i usługami.</span><span class="sxs-lookup"><span data-stu-id="a6b5b-103">The channel layer is responsible for the exchange of messages between clients and services.</span></span> <span data-ttu-id="a6b5b-104">Rozszerzenia kanału można zaimplementować nowych funkcji protokołu, takiego jak zabezpieczenia czy funkcje transportu, takie jak wdrażanie nowego transportu sieciowego do przenoszenia wiadomości SOAP.</span><span class="sxs-lookup"><span data-stu-id="a6b5b-104">Channel extensions can implement new protocol functionality, such as security, or transport functionality, such as implementing a new network transport to carry SOAP messages.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a6b5b-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="a6b5b-105">In This Section</span></span>  
 [<span data-ttu-id="a6b5b-106">Przegląd modelu kanału</span><span class="sxs-lookup"><span data-stu-id="a6b5b-106">Channel Model Overview</span></span>](../../../../docs/framework/wcf/extending/channel-model-overview.md)  
 <span data-ttu-id="a6b5b-107">Zawiera ogólne omówienie kanały są funkcje, które zapewniają i jak działają usługi i aplikacji klienckiej.</span><span class="sxs-lookup"><span data-stu-id="a6b5b-107">Provides a high-level overview of what channels are, the features that they provide and how they work both in a service and a client application.</span></span>  
  
 [<span data-ttu-id="a6b5b-108">Opracowywanie kanałów</span><span class="sxs-lookup"><span data-stu-id="a6b5b-108">Developing Channels</span></span>](../../../../docs/framework/wcf/extending/developing-channels.md)  
 <span data-ttu-id="a6b5b-109">Opisano szczegółowo ról, które odtwarzania różnych typów infrastruktury kanału, jak działa stan aparatu i stan cyklu życia sposób obsługi wyjątków i błędów, implementowania Obsługa metadanych i działanie kanały za pomocą koderów wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a6b5b-109">Describes in depth the roles that the various channel infrastructure types play, how the state engine and state lifecycle works, how to handle exceptions and faults, how to implement metadata support, and how channels work with message encoders.</span></span>  
  
 [<span data-ttu-id="a6b5b-110">Niestandardowe kodery</span><span class="sxs-lookup"><span data-stu-id="a6b5b-110">Custom Encoders</span></span>](../../../../docs/framework/wcf/extending/custom-encoders.md)  
 <span data-ttu-id="a6b5b-111">Zawiera opis roli, który koderów wiadomości odtwarzane w kanałów i jak utworzyć.</span><span class="sxs-lookup"><span data-stu-id="a6b5b-111">Describes the role that message encoders play in channels and how to build one.</span></span>  
  
 [<span data-ttu-id="a6b5b-112">Niestandardowe uaktualnienia strumienia</span><span class="sxs-lookup"><span data-stu-id="a6b5b-112">Custom Stream Upgrades</span></span>](../../../../docs/framework/wcf/extending/custom-stream-upgrades.md)  
 <span data-ttu-id="a6b5b-113">W tym artykule opisano proces uaktualniania strumieni podał zorientowanych strumieniowo transportów.</span><span class="sxs-lookup"><span data-stu-id="a6b5b-113">Describes the process of upgrading the streams provided by stream-oriented transports.</span></span>
