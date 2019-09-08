---
title: Rozszerzanie warstwy kanału
ms.date: 03/30/2017
helpviewer_keywords:
- extending channels [WCF]
ms.assetid: 4238db74-2fb6-4dc8-a326-f58527230810
ms.openlocfilehash: 76ca76d7973403c657b8f68bfde9619df36f220e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797137"
---
# <a name="extending-the-channel-layer"></a><span data-ttu-id="6658e-102">Rozszerzanie warstwy kanału</span><span class="sxs-lookup"><span data-stu-id="6658e-102">Extending the Channel Layer</span></span>
<span data-ttu-id="6658e-103">Warstwa kanału jest odpowiedzialna za wymianę komunikatów między klientami i usługami.</span><span class="sxs-lookup"><span data-stu-id="6658e-103">The channel layer is responsible for the exchange of messages between clients and services.</span></span> <span data-ttu-id="6658e-104">Rozszerzenia kanału mogą implementować nowe funkcje protokołu, takie jak zabezpieczenia lub funkcje transportu, takie jak implementacja nowego transportu sieciowego do przenoszenia komunikatów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="6658e-104">Channel extensions can implement new protocol functionality, such as security, or transport functionality, such as implementing a new network transport to carry SOAP messages.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6658e-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="6658e-105">In This Section</span></span>  
 [<span data-ttu-id="6658e-106">Przegląd modelu kanału</span><span class="sxs-lookup"><span data-stu-id="6658e-106">Channel Model Overview</span></span>](channel-model-overview.md)  
 <span data-ttu-id="6658e-107">Zawiera ogólny przegląd informacji o kanałach, funkcjach, które zapewnia i jak działają zarówno w usłudze, jak i w aplikacji klienckiej.</span><span class="sxs-lookup"><span data-stu-id="6658e-107">Provides a high-level overview of what channels are, the features that they provide and how they work both in a service and a client application.</span></span>  
  
 [<span data-ttu-id="6658e-108">Opracowywanie kanałów</span><span class="sxs-lookup"><span data-stu-id="6658e-108">Developing Channels</span></span>](developing-channels.md)  
 <span data-ttu-id="6658e-109">Szczegółowo opisano role, które są odtwarzane przez różne typy infrastruktury kanałów, jak działa aparat stanu i cykl życia stanu, jak obsługiwać wyjątki i błędy, jak zaimplementować obsługę metadanych oraz jak kanały pracują z koderami komunikatów.</span><span class="sxs-lookup"><span data-stu-id="6658e-109">Describes in depth the roles that the various channel infrastructure types play, how the state engine and state lifecycle works, how to handle exceptions and faults, how to implement metadata support, and how channels work with message encoders.</span></span>  
  
 [<span data-ttu-id="6658e-110">Niestandardowe kodery</span><span class="sxs-lookup"><span data-stu-id="6658e-110">Custom Encoders</span></span>](custom-encoders.md)  
 <span data-ttu-id="6658e-111">Opisuje rolę, jaką odgrywa kodery wiadomości w kanałach i jak ją skompilować.</span><span class="sxs-lookup"><span data-stu-id="6658e-111">Describes the role that message encoders play in channels and how to build one.</span></span>  
  
 [<span data-ttu-id="6658e-112">Niestandardowe uaktualnienia strumienia</span><span class="sxs-lookup"><span data-stu-id="6658e-112">Custom Stream Upgrades</span></span>](custom-stream-upgrades.md)  
 <span data-ttu-id="6658e-113">Opisuje proces uaktualniania strumieni dostarczonych przez transporty ukierunkowane na strumień.</span><span class="sxs-lookup"><span data-stu-id="6658e-113">Describes the process of upgrading the streams provided by stream-oriented transports.</span></span>
