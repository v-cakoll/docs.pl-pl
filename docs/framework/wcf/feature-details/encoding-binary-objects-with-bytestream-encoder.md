---
title: Kodowanie obiektów binarnych za pomocą kodera elementu ByteStream
ms.date: 03/30/2017
ms.assetid: 020ee981-c889-4b12-a3ea-91823ef46444
ms.openlocfilehash: 09a919e11971f81bc76dca0e45a7eb0e70ef749e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626925"
---
# <a name="encoding-binary-objects-with-bytestream-encoder"></a><span data-ttu-id="db91a-102">Kodowanie obiektów binarnych za pomocą kodera elementu ByteStream</span><span class="sxs-lookup"><span data-stu-id="db91a-102">Encoding Binary Objects with ByteStream Encoder</span></span>
<span data-ttu-id="db91a-103">Wysyłanie i odbieranie nieprzetworzone dane binarne za pomocą programu Windows Communication Foundation (WCF) została skonfigurowana przy użyciu <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="db91a-103">Sending and receiving raw binary data with Windows Communication Foundation (WCF) is configured using <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>.</span></span>  
  
## <a name="byte-stream-message-encoder-architecture"></a><span data-ttu-id="db91a-104">Architektura kodera komunikatów Stream bajtów</span><span class="sxs-lookup"><span data-stu-id="db91a-104">Byte Stream Message Encoder Architecture</span></span>  
 <span data-ttu-id="db91a-105">Koder komunikatu binarnego używany przez usługę WCF nie ma żadnych funkcji do przetwarzania, sprawdzanie poprawności lub Identyfikowanie podstawowych danych binarnych w komunikacie.</span><span class="sxs-lookup"><span data-stu-id="db91a-105">The binary message encoder used by WCF has no facility for processing, validating, or identifying the underlying binary data in the message.</span></span> <span data-ttu-id="db91a-106">Pakiet danych jest zakodowany w formacie XML, wysyłane, odebrano i zdekodowane.</span><span class="sxs-lookup"><span data-stu-id="db91a-106">The data package is encoded into XML, sent, received, and decoded.</span></span> <span data-ttu-id="db91a-107">Koder przetwarza dane po przekazywany do transportu i przed wysłaniem wiadomości do kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="db91a-107">The encoder processes the data after being passed to the transport and before the message is sent to the message queue.</span></span> <span data-ttu-id="db91a-108">Funkcjonalnie kodera binarnego jest zawijany dane wiadomości w `<binary>` elementy do wysyłania i usuwa elementy po otrzymaniu komunikatu.</span><span class="sxs-lookup"><span data-stu-id="db91a-108">Functionally, the binary encoder wraps the message data in `<binary>` elements for sending and removes the elements after the message is received.</span></span>  
  
## <a name="using-the-byte-stream-message-encoder"></a><span data-ttu-id="db91a-109">Przy użyciu kodera komunikatów Stream bajtów</span><span class="sxs-lookup"><span data-stu-id="db91a-109">Using the Byte Stream Message Encoder</span></span>  
 <span data-ttu-id="db91a-110">Poniższy przykład zawiera kontrakt usługi, która implementuje koder komunikatów strumienia bajtów.</span><span class="sxs-lookup"><span data-stu-id="db91a-110">The following example shows a service contract that implements the byte stream message encoder.</span></span>  
  
```csharp  
[OperationContract]  
Void Myfunction(Stream stream);  
```  
  
 <span data-ttu-id="db91a-111">Poniższy przykład pokazuje usługi wywoływana.</span><span class="sxs-lookup"><span data-stu-id="db91a-111">The following example shows the service being invoked.</span></span>  
  
```csharp  
proxy.MyFunction(stream);  
```  
  
 <span data-ttu-id="db91a-112">W przypadku usługi, który implementuje infrastrukturze komunikatu (na przykład router), komunikat jest przetwarzany bez sprawdzania, sprawdzanie poprawności lub inny sposób interakcji z wiadomością, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="db91a-112">In the case of using a service that implements a message infrastructure (such as a router), the message is processed without inspecting, validating, or otherwise interacting with the message, as shown in the following example.</span></span>  
  
```csharp  
[OperationContract]  
void ProcessMessage(Message message) ;  
```  
  
## <a name="scenarios"></a><span data-ttu-id="db91a-113">Scenariusze</span><span class="sxs-lookup"><span data-stu-id="db91a-113">Scenarios</span></span>  
 <span data-ttu-id="db91a-114">Koder Stream bajt jest przydatne w następujących scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="db91a-114">The Byte Stream Encoder is useful in the following scenarios.</span></span>  
  
- <span data-ttu-id="db91a-115">Przenoszenie obrazu JPEG między komputerami przy użyciu usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="db91a-115">Transferring a JPEG image between computers using WCF.</span></span> <span data-ttu-id="db91a-116">W tym scenariuszu obrazu zostaną dostarczone za pomocą transportu ze źródła zewnętrznego, a dane wysłane będzie pierwotne bajtów, które składają się na obrazie.</span><span class="sxs-lookup"><span data-stu-id="db91a-116">In this scenario, the image will arrive through the transport from an outside source, and the data sent will be the raw bytes that make up the image.</span></span> <span data-ttu-id="db91a-117">Usługa będzie odbierać dane binarne i wyświetlić obraz.</span><span class="sxs-lookup"><span data-stu-id="db91a-117">A service will receive the binary data and display the image.</span></span>  
  
- <span data-ttu-id="db91a-118">Odczytywanie informacji poza kolejki komunikatów i przetwarza go.</span><span class="sxs-lookup"><span data-stu-id="db91a-118">Reading information out of a message queue and processing it.</span></span> <span data-ttu-id="db91a-119">Komunikat będzie odczytywać menedżera kolejki komunikatów i przekazywane kanał kolejki wiadomości do obsłużenia.</span><span class="sxs-lookup"><span data-stu-id="db91a-119">The message will be read from a message queue manager, and passed up the message queue channel to be handled.</span></span> <span data-ttu-id="db91a-120">Kanał wiadomości w kolejce będzie pełnił rolę menedżera kolejki w stosie kanału WCF.</span><span class="sxs-lookup"><span data-stu-id="db91a-120">The message queue channel will act as a queue manager in the WCF channel stack.</span></span>  
  
 <span data-ttu-id="db91a-121">W przypadku wysyłania komunikatu za pośrednictwem kanału kolejki komunikatów, nadawca nie ma kontroli nad bajtów odebranych przez menedżera kolejki.</span><span class="sxs-lookup"><span data-stu-id="db91a-121">In the case of sending a message over a message queue channel, the sender has no control over the bytes received from the queue manager.</span></span> <span data-ttu-id="db91a-122">Odbieranie proces ma możliwość odczytywania bajtów raw, wiadomości będą odbierane nieprawidłowo sformatowane, a nie będą przetwarzane; zakłada się, że proces odbierania możliwości tłumaczenia odebranych bajtów do miał format.</span><span class="sxs-lookup"><span data-stu-id="db91a-122">If the receiving process has no capability to read raw bytes, the message will be received as badly formatted and will not be processed; it is assumed that the receiving process will have the capability of translating the received bytes back into a usable format.</span></span>
