---
title: Rozszerzanie warstwy kanału
ms.date: 03/30/2017
helpviewer_keywords:
- extending channels [WCF]
ms.assetid: 4238db74-2fb6-4dc8-a326-f58527230810
ms.openlocfilehash: e60d8ef1a5191c6407b01eb1a2456a06aeeb1914
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857912"
---
# <a name="extending-the-channel-layer"></a><span data-ttu-id="23192-102">Rozszerzanie warstwy kanału</span><span class="sxs-lookup"><span data-stu-id="23192-102">Extending the Channel Layer</span></span>
<span data-ttu-id="23192-103">Warstwy kanału jest odpowiedzialny za wymiana wiadomości między klientami i usługami.</span><span class="sxs-lookup"><span data-stu-id="23192-103">The channel layer is responsible for the exchange of messages between clients and services.</span></span> <span data-ttu-id="23192-104">Rozszerzenia kanału można zaimplementować nowych funkcji protokołu, takie jak zabezpieczenia czy funkcji transportu, takich jak zaimplementowanie nowy transport do sieci, żeby komunikaty protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="23192-104">Channel extensions can implement new protocol functionality, such as security, or transport functionality, such as implementing a new network transport to carry SOAP messages.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="23192-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="23192-105">In This Section</span></span>  
 [<span data-ttu-id="23192-106">Przegląd modelu kanału</span><span class="sxs-lookup"><span data-stu-id="23192-106">Channel Model Overview</span></span>](../../../../docs/framework/wcf/extending/channel-model-overview.md)  
 <span data-ttu-id="23192-107">Zawiera ogólne omówienie kanałów, jakie są funkcje, które zapewniają i jak działają zarówno w usłudze i aplikację kliencką.</span><span class="sxs-lookup"><span data-stu-id="23192-107">Provides a high-level overview of what channels are, the features that they provide and how they work both in a service and a client application.</span></span>  
  
 [<span data-ttu-id="23192-108">Opracowywanie kanałów</span><span class="sxs-lookup"><span data-stu-id="23192-108">Developing Channels</span></span>](../../../../docs/framework/wcf/extending/developing-channels.md)  
 <span data-ttu-id="23192-109">W tym artykule opisano szczegółowo role, które odtwarzania różnych typów kanałów w infrastrukturze, sposobu działania cyklu życia aparatu i stan stanu, sposób obsługi wyjątków i błędów, jak zaimplementować obsługę metadanych i za pomocą koderów wiadomości na temat działania kanałów.</span><span class="sxs-lookup"><span data-stu-id="23192-109">Describes in depth the roles that the various channel infrastructure types play, how the state engine and state lifecycle works, how to handle exceptions and faults, how to implement metadata support, and how channels work with message encoders.</span></span>  
  
 [<span data-ttu-id="23192-110">Niestandardowe kodery</span><span class="sxs-lookup"><span data-stu-id="23192-110">Custom Encoders</span></span>](../../../../docs/framework/wcf/extending/custom-encoders.md)  
 <span data-ttu-id="23192-111">W tym artykule opisano rolę pełniące koderów wiadomości w kanałach oraz sposób zbudować ją.</span><span class="sxs-lookup"><span data-stu-id="23192-111">Describes the role that message encoders play in channels and how to build one.</span></span>  
  
 [<span data-ttu-id="23192-112">Niestandardowe uaktualnienia strumienia</span><span class="sxs-lookup"><span data-stu-id="23192-112">Custom Stream Upgrades</span></span>](../../../../docs/framework/wcf/extending/custom-stream-upgrades.md)  
 <span data-ttu-id="23192-113">W tym artykule opisano proces uaktualniania strumieni, dostarczone przez zorientowane na strumień transportu.</span><span class="sxs-lookup"><span data-stu-id="23192-113">Describes the process of upgrading the streams provided by stream-oriented transports.</span></span>
