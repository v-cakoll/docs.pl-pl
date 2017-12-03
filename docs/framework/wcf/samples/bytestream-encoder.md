---
title: Koder elementu ByteStream
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e674a8ab-f79a-4a93-b984-54b34392dafc
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7663e0c0073110c0df2e3ece20c240af46a61e92
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="bytestream-encoder"></a><span data-ttu-id="ca1dc-102">Koder elementu ByteStream</span><span class="sxs-lookup"><span data-stu-id="ca1dc-102">ByteStream Encoder</span></span>
<span data-ttu-id="ca1dc-103">Ten przykład przedstawia sposób tworzenia `ByteStreamHttpBinding`, <xref:System.ServiceModel.Channels.Binding> który prezentuje działanie funkcji kodera strumienia bajtów.</span><span class="sxs-lookup"><span data-stu-id="ca1dc-103">This sample demonstrates how to create a `ByteStreamHttpBinding`, a <xref:System.ServiceModel.Channels.Binding> that demonstrates the functionality of the byte stream encoder.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="ca1dc-104">Omówienie</span><span class="sxs-lookup"><span data-stu-id="ca1dc-104">Discussion</span></span>  
 <span data-ttu-id="ca1dc-105">Ten przykład przedstawia sposób tworzenia standardowego <xref:System.ServiceModel.Channels.Binding> za pomocą elementów Powiązanie standardowe <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement> i <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="ca1dc-105">This sample demonstrates how to create a standard <xref:System.ServiceModel.Channels.Binding> using the standard binding elements <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement> and <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span></span> <span data-ttu-id="ca1dc-106">Ten przykład przedstawia sposób użycia kodera strumienia bajtów do przekazywania i pobierania obrazu.</span><span class="sxs-lookup"><span data-stu-id="ca1dc-106">This sample shows how to use the byte stream encoder to upload and download an image.</span></span> <span data-ttu-id="ca1dc-107">Funkcja kodera strumienia bajtów obsługuje tylko transportu HTTP i nie obsługuje funkcji, takich jak niezawodna obsługa komunikatów i zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="ca1dc-107">The byte stream encoder feature only supports the HTTP transport and it does not support features such as reliable messaging or security.</span></span> <span data-ttu-id="ca1dc-108">Jedynym <xref:System.ServiceModel.Channels.MessageVersion> jest obsługiwane <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="ca1dc-108">The only <xref:System.ServiceModel.Channels.MessageVersion> supported is <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ca1dc-109">Jeśli używasz tego przykładu [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)] lub [!INCLUDE[win7_client_firstref](../../../../includes/win7-client-firstref-md.md)], upewnij się, że uruchamiasz [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] z podwyższonym poziomem uprawnień.</span><span class="sxs-lookup"><span data-stu-id="ca1dc-109">If you are running this sample in [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)] or [!INCLUDE[win7_client_firstref](../../../../includes/win7-client-firstref-md.md)], ensure that you are running [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] with elevated privileges.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ca1dc-110">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="ca1dc-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ca1dc-111">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="ca1dc-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ca1dc-112">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="ca1dc-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ca1dc-113">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="ca1dc-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\ByteStreamEncoder`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ca1dc-114">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="ca1dc-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ca1dc-115">Otwórz plik ByteStreamHttpBinding.sln w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ca1dc-115">Open the ByteStreamHttpBinding.sln file in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="ca1dc-116">Uruchom nowe wystąpienie klasy ByteStreamHttpBindingServer projektu prawym przyciskiem myszy projekt w Eksploratorze rozwiązań i wybierając polecenie **debugowania**, a następnie **Start nowe wystąpienie** z menu kontekstowego.</span><span class="sxs-lookup"><span data-stu-id="ca1dc-116">Start a new instance of the ByteStreamHttpBindingServer project by right-clicking the project in the Solution Explorer and selecting **Debug**, and then **Start new instance** from the context menu.</span></span>  
  
3.  <span data-ttu-id="ca1dc-117">Uruchom nowe wystąpienie klasy ByteStreamHttpBindingClient projektu prawym przyciskiem myszy projekt w Eksploratorze rozwiązań i wybierając polecenie **debugowania**, **Start nowe wystąpienie** z menu kontekstowego.</span><span class="sxs-lookup"><span data-stu-id="ca1dc-117">Start a new instance of the ByteStreamHttpBindingClient project by right-clicking the project in the Solution Explorer and selecting **Debug**, **Start new instance** from the context menu.</span></span>
