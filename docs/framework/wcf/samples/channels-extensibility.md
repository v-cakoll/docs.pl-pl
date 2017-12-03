---
title: "Rozszerzalność kanałów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4cc3b20b-778a-4ae8-b58c-a3822fb13065
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bcda7f9edc741e8f0c9c56214119255ca2777d77
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="channels-extensibility"></a><span data-ttu-id="ebd98-102">Rozszerzalność kanałów</span><span class="sxs-lookup"><span data-stu-id="ebd98-102">Channels Extensibility</span></span>
<span data-ttu-id="ebd98-103">Ta sekcja zawiera przykłady ilustrujące kanałów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="ebd98-103">This section contains samples that demonstrate custom channels.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ebd98-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="ebd98-104">In This Section</span></span>  
 [<span data-ttu-id="ebd98-105">Lokalny kanał</span><span class="sxs-lookup"><span data-stu-id="ebd98-105">Local Channel</span></span>](../../../../docs/framework/wcf/samples/local-channel.md)  
 <span data-ttu-id="ebd98-106">Pokazuje lokalnego kanału [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kanał transportu, który jest używany do komunikacji w obrębie tej samej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ebd98-106">Demonstrates the local channel, a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transport channel that is used for communication within the same application domain.</span></span>  
  
 [<span data-ttu-id="ebd98-107">Niezawodny bezpieczny profil</span><span class="sxs-lookup"><span data-stu-id="ebd98-107">Reliable Secure Profile</span></span>](../../../../docs/framework/wcf/samples/reliable-secure-profile.md)  
 <span data-ttu-id="ebd98-108">Pokazuje, jak utworzyć [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] i niezawodny bezpieczny profil (źródło).</span><span class="sxs-lookup"><span data-stu-id="ebd98-108">Demonstrates how to compose [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] and Reliable Secure Profile (RSP).</span></span>  
  
 [<span data-ttu-id="ebd98-109">Niestandardowy Dyspozytor kanału</span><span class="sxs-lookup"><span data-stu-id="ebd98-109">Custom Channel Dispatcher</span></span>](../../../../docs/framework/wcf/samples/custom-channel-dispatcher.md)  
 <span data-ttu-id="ebd98-110">Demonstruje sposób tworzenia kanału stosu w niestandardowy sposób z zastosowaniem <xref:System.ServiceModel.ServiceHostBase> bezpośrednio oraz sposobu tworzenia dyspozytora niestandardowym kanale w środowisku hosta sieci Web.</span><span class="sxs-lookup"><span data-stu-id="ebd98-110">Demonstrates how to build the channel stack in a custom way by implementing <xref:System.ServiceModel.ServiceHostBase> directly and how to create a custom channel dispatcher in Web host environment.</span></span>  
  
 [<span data-ttu-id="ebd98-111">Kanał dzielący na fragmenty</span><span class="sxs-lookup"><span data-stu-id="ebd98-111">Chunking Channel</span></span>](../../../../docs/framework/wcf/samples/chunking-channel.md)  
 <span data-ttu-id="ebd98-112">Pokazuje, jak ograniczyć ilość pamięci użytej do zbuforowania dużych komunikatów wysyłanych za pomocą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ebd98-112">Demonstrates how to limit the amount of memory used to buffer large messages sent using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="ebd98-113">Kanał potwierdzania HTTP</span><span class="sxs-lookup"><span data-stu-id="ebd98-113">HTTP Acknowledgement Channel</span></span>](../../../../docs/framework/wcf/samples/http-acknowledgement-channel.md)  
 <span data-ttu-id="ebd98-114">Pokazuje warstwowego kanału, która zmienia jednokierunkowe wzorzec przesyłania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="ebd98-114">Demonstrates a layered channel which changes the one-way messaging pattern.</span></span>  
  
 [<span data-ttu-id="ebd98-115">HttpCookieSession</span><span class="sxs-lookup"><span data-stu-id="ebd98-115">HttpCookieSession</span></span>](../../../../docs/framework/wcf/samples/httpcookiesession.md)  
 <span data-ttu-id="ebd98-116">Pokazuje, jak zbudować kanału używać plików cookie protokołu HTTP do zarządzania sesji protokołu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="ebd98-116">Demonstrates how to build a custom protocol channel to use HTTP cookies for session management.</span></span>  
  
 [<span data-ttu-id="ebd98-117">Niestandardowy element przechwytujący</span><span class="sxs-lookup"><span data-stu-id="ebd98-117">Custom Message Interceptor</span></span>](../../../../docs/framework/wcf/samples/custom-message-interceptor.md)  
 <span data-ttu-id="ebd98-118">Pokazuje, jak wdrożyć element niestandardowego powiązania, który tworzy fabryk kanałów i odbiorników kanału do przechwycenia wszystkich wiadomości przychodzących i wychodzących w określonym punkcie w stosie środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="ebd98-118">Demonstrates how to implement a custom binding element that creates channel factories and channel listeners to intercept all incoming and outgoing messages at a particular point in the run-time stack.</span></span>
