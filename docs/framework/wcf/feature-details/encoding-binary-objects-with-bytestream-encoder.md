---
title: "Kodowanie obiektów binarnych za pomocą kodera elementu ByteStream"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 020ee981-c889-4b12-a3ea-91823ef46444
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2cf68356ffa5fe20de7bd417c77388cd214ca718
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="encoding-binary-objects-with-bytestream-encoder"></a><span data-ttu-id="90c62-102">Kodowanie obiektów binarnych za pomocą kodera elementu ByteStream</span><span class="sxs-lookup"><span data-stu-id="90c62-102">Encoding Binary Objects with ByteStream Encoder</span></span>
<span data-ttu-id="90c62-103">Wysyłanie i odbieranie nieprzetworzone dane binarne z [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] jest konfigurowana przy użyciu <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="90c62-103">Sending and receiving raw binary data with [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is configured using <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>.</span></span>  
  
## <a name="byte-stream-message-encoder-architecture"></a><span data-ttu-id="90c62-104">Architektura kodera wiadomości strumień bajtów</span><span class="sxs-lookup"><span data-stu-id="90c62-104">Byte Stream Message Encoder Architecture</span></span>  
 <span data-ttu-id="90c62-105">Używane przez koder komunikatów binarnych [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ma nie funkcje przetwarzania, sprawdzanie poprawności lub identyfikowanie danych binarnych w komunikacie.</span><span class="sxs-lookup"><span data-stu-id="90c62-105">The binary message encoder used by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] has no facility for processing, validating, or identifying the underlying binary data in the message.</span></span> <span data-ttu-id="90c62-106">Pakiet danych jest zakodowany w formacie XML, wysyłane odebranych i zdekodowane.</span><span class="sxs-lookup"><span data-stu-id="90c62-106">The data package is encoded into XML, sent, received, and decoded.</span></span> <span data-ttu-id="90c62-107">Koder przetwarza dane po przekazywany do transportu i przed wysłaniem wiadomości do kolejki wiadomości.</span><span class="sxs-lookup"><span data-stu-id="90c62-107">The encoder processes the data after being passed to the transport and before the message is sent to the message queue.</span></span> <span data-ttu-id="90c62-108">Funkcjonalnie kodera binarnego koduje dane wiadomości w `<binary>` elementy do wysyłania i usuwa elementy po odebraniu komunikatu.</span><span class="sxs-lookup"><span data-stu-id="90c62-108">Functionally, the binary encoder wraps the message data in `<binary>` elements for sending and removes the elements after the message is received.</span></span>  
  
## <a name="using-the-byte-stream-message-encoder"></a><span data-ttu-id="90c62-109">Za pomocą kodera wiadomości strumień bajtów</span><span class="sxs-lookup"><span data-stu-id="90c62-109">Using the Byte Stream Message Encoder</span></span>  
 <span data-ttu-id="90c62-110">W poniższym przykładzie przedstawiono kontraktu usługi, który implementuje kodera wiadomości strumienia bajtów.</span><span class="sxs-lookup"><span data-stu-id="90c62-110">The following example shows a service contract that implements the byte stream message encoder.</span></span>  
  
```csharp  
[OperationContract]  
Void Myfunction(Stream stream);  
```  
  
 <span data-ttu-id="90c62-111">Poniższy przykład przedstawia wywoływanie usługi.</span><span class="sxs-lookup"><span data-stu-id="90c62-111">The following example shows the service being invoked.</span></span>  
  
```csharp  
proxy.MyFunction(stream);  
```  
  
 <span data-ttu-id="90c62-112">W przypadku przy użyciu usługa, która implementuje infrastrukturze wiadomości (na przykład router), komunikat jest przetwarzany bez sprawdzania, sprawdzanie poprawności lub inny sposób interakcji z komunikatu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="90c62-112">In the case of using a service that implements a message infrastructure (such as a router), the message is processed without inspecting, validating, or otherwise interacting with the message, as shown in the following example.</span></span>  
  
```csharp  
[OperationContract]  
void ProcessMessage(Message message) ;  
```  
  
## <a name="scenarios"></a><span data-ttu-id="90c62-113">Scenariusze</span><span class="sxs-lookup"><span data-stu-id="90c62-113">Scenarios</span></span>  
 <span data-ttu-id="90c62-114">Koder strumień bajtów jest przydatne w następujących scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="90c62-114">The Byte Stream Encoder is useful in the following scenarios.</span></span>  
  
-   <span data-ttu-id="90c62-115">Przesyłanie obrazu JPEG między komputerami za pomocą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="90c62-115">Transferring a JPEG image between computers using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="90c62-116">W tym scenariuszu obraz pojawią się za pomocą transportu ze źródła zewnętrznego, a dane przesyłane będzie raw bajtów, które tworzą obrazu.</span><span class="sxs-lookup"><span data-stu-id="90c62-116">In this scenario, the image will arrive through the transport from an outside source, and the data sent will be the raw bytes that make up the image.</span></span> <span data-ttu-id="90c62-117">Usługi będzie odbierać dane binarne i wyświetlić obraz.</span><span class="sxs-lookup"><span data-stu-id="90c62-117">A service will receive the binary data and display the image.</span></span>  
  
-   <span data-ttu-id="90c62-118">Odczytywanie informacji poza kolejki komunikatów i jego przetwarzanie.</span><span class="sxs-lookup"><span data-stu-id="90c62-118">Reading information out of a message queue and processing it.</span></span> <span data-ttu-id="90c62-119">Komunikat będzie odczytywać menedżera kolejki komunikatów i przekazywane kanał kolejki wiadomości mają być obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="90c62-119">The message will be read from a message queue manager, and passed up the message queue channel to be handled.</span></span> <span data-ttu-id="90c62-120">Kanał wiadomości w kolejce będzie pełnił rolę menedżera kolejki w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] stosu kanału.</span><span class="sxs-lookup"><span data-stu-id="90c62-120">The message queue channel will act as a queue manager in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] channel stack.</span></span>  
  
 <span data-ttu-id="90c62-121">W przypadku wysyłania wiadomości kanałem kolejki komunikatów, nadawca nie ma kontroli nad bajtów odebranych z menedżera kolejek.</span><span class="sxs-lookup"><span data-stu-id="90c62-121">In the case of sending a message over a message queue channel, the sender has no control over the bytes received from the queue manager.</span></span> <span data-ttu-id="90c62-122">Odbierania proces nie ma funkcji do odczytywania bajtów raw, wiadomość zostanie odebrana nieprawidłowo sformatowane i nie będą przetwarzane; zakłada się, że proces odbierania możliwości tłumaczenia odebrane bajty do można używać formatu.</span><span class="sxs-lookup"><span data-stu-id="90c62-122">If the receiving process has no capability to read raw bytes, the message will be received as badly formatted and will not be processed; it is assumed that the receiving process will have the capability of translating the received bytes back into a usable format.</span></span>
