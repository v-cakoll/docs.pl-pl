---
title: Koder elementu ByteStream
ms.date: 03/30/2017
ms.assetid: e674a8ab-f79a-4a93-b984-54b34392dafc
ms.openlocfilehash: cbd4110ecc04923b79d6b910fcf7ab4ca2012680
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43480695"
---
# <a name="bytestream-encoder"></a><span data-ttu-id="3c9bb-102">Koder elementu ByteStream</span><span class="sxs-lookup"><span data-stu-id="3c9bb-102">ByteStream Encoder</span></span>
<span data-ttu-id="3c9bb-103">Ten przykład przedstawia sposób tworzenia `ByteStreamHttpBinding`, <xref:System.ServiceModel.Channels.Binding> którym przedstawiono funkcje Encoder w warstwie strumienia bajtów.</span><span class="sxs-lookup"><span data-stu-id="3c9bb-103">This sample demonstrates how to create a `ByteStreamHttpBinding`, a <xref:System.ServiceModel.Channels.Binding> that demonstrates the functionality of the byte stream encoder.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="3c9bb-104">Dyskusja</span><span class="sxs-lookup"><span data-stu-id="3c9bb-104">Discussion</span></span>  
 <span data-ttu-id="3c9bb-105">Ten przykład przedstawia sposób tworzenia standardowego <xref:System.ServiceModel.Channels.Binding> za pomocą elementów powiązania standardowa <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement> i <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="3c9bb-105">This sample demonstrates how to create a standard <xref:System.ServiceModel.Channels.Binding> using the standard binding elements <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement> and <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span></span> <span data-ttu-id="3c9bb-106">W tym przykładzie pokazano, jak przekazywanie i pobieranie obrazu za pomocą kodera strumienia bajtów.</span><span class="sxs-lookup"><span data-stu-id="3c9bb-106">This sample shows how to use the byte stream encoder to upload and download an image.</span></span> <span data-ttu-id="3c9bb-107">Funkcja Encoder w warstwie strumienia bajtów obsługuje tylko transportu HTTP i nie obsługuje funkcji, takich jak niezawodna obsługa komunikatów lub zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="3c9bb-107">The byte stream encoder feature only supports the HTTP transport and it does not support features such as reliable messaging or security.</span></span> <span data-ttu-id="3c9bb-108">Tylko <xref:System.ServiceModel.Channels.MessageVersion> jest obsługiwane <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="3c9bb-108">The only <xref:System.ServiceModel.Channels.MessageVersion> supported is <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3c9bb-109">Jeśli są uruchomione w tym przykładzie w [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)] lub [!INCLUDE[win7_client_firstref](../../../../includes/win7-client-firstref-md.md)], upewnij się, że używasz [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] z podwyższonym poziomem uprawnień.</span><span class="sxs-lookup"><span data-stu-id="3c9bb-109">If you are running this sample in [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)] or [!INCLUDE[win7_client_firstref](../../../../includes/win7-client-firstref-md.md)], ensure that you are running [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] with elevated privileges.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3c9bb-110">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="3c9bb-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3c9bb-111">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="3c9bb-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3c9bb-112">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="3c9bb-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3c9bb-113">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="3c9bb-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\ByteStreamEncoder`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3c9bb-114">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="3c9bb-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="3c9bb-115">Otwórz plik ByteStreamHttpBinding.sln w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3c9bb-115">Open the ByteStreamHttpBinding.sln file in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="3c9bb-116">Uruchom nowe wystąpienie projektu ByteStreamHttpBindingServer kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań i wybierając polecenie **debugowania**, a następnie **Uruchom nowe wystąpienie** z menu kontekstowego.</span><span class="sxs-lookup"><span data-stu-id="3c9bb-116">Start a new instance of the ByteStreamHttpBindingServer project by right-clicking the project in the Solution Explorer and selecting **Debug**, and then **Start new instance** from the context menu.</span></span>  
  
3.  <span data-ttu-id="3c9bb-117">Uruchom nowe wystąpienie projektu ByteStreamHttpBindingClient kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań i wybierając polecenie **debugowania**, **Uruchom nowe wystąpienie** z menu kontekstowego.</span><span class="sxs-lookup"><span data-stu-id="3c9bb-117">Start a new instance of the ByteStreamHttpBindingClient project by right-clicking the project in the Solution Explorer and selecting **Debug**, **Start new instance** from the context menu.</span></span>
