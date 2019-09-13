---
title: Interpretowanie śledzenia sieci
ms.date: 03/30/2017
helpviewer_keywords:
- TraceMode attribute
- hexidecimal data, network tracing output
- network tracing, analyzing
- protocolonly
- text, network tracing output
- includehex
ms.assetid: ad22b4b8-00af-4778-9cca-cb609ce1f8ff
ms.openlocfilehash: 09f77a60255accc3e4b1c4fa5ea3d7526444e4cb
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894724"
---
# <a name="interpreting-network-tracing"></a><span data-ttu-id="b6351-102">Interpretowanie śledzenia sieci</span><span class="sxs-lookup"><span data-stu-id="b6351-102">Interpreting Network Tracing</span></span>
<span data-ttu-id="b6351-103">Po włączeniu śledzenia sieci można użyć funkcji śledzenia do przechwytywania wywołań aplikacji do różnych <xref:System.Net> elementów członkowskich klasy.</span><span class="sxs-lookup"><span data-stu-id="b6351-103">When network tracing is enabled, you can use tracing to capture calls your application makes to various <xref:System.Net> class members.</span></span> <span data-ttu-id="b6351-104">Dane wyjściowe tych wywołań mogą wyglądać podobnie jak w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="b6351-104">The output from these calls may be similar to the following examples.</span></span>  
  
```output
[588]   (4357)   Entering Socket#33574638::Send()  
[588]   (4387)   Exiting Socket#33574638::Send()-> 61#61
```  
  
 <span data-ttu-id="b6351-105">W poprzednim przykładzie [588] jest unikatowym identyfikatorem bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="b6351-105">In the preceding example, [588] is the current thread's unique identifier.</span></span> <span data-ttu-id="b6351-106">(4357) i (4387) to sygnatury czasowe określające liczbę milisekund, które upłynęły od momentu uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b6351-106">(4357) and (4387) are timestamps denoting the number of milliseconds that have elapsed since the application started.</span></span> <span data-ttu-id="b6351-107">Dane po znaczniku czasu pokazują aplikację wprowadzającą i opuszczają metodę **Socket. Send**.</span><span class="sxs-lookup"><span data-stu-id="b6351-107">The data following the timestamp shows the application entering and exiting the method **Socket.Send**.</span></span> <span data-ttu-id="b6351-108">Obiekt wykonujący metodę **send** ma 33574638 jako unikatowy identyfikator.</span><span class="sxs-lookup"><span data-stu-id="b6351-108">The object executing the **Send** method has 33574638 as its unique identifier.</span></span> <span data-ttu-id="b6351-109">Ślad wyjścia metody zawiera wartość zwracaną (61 w poprzednim przykładzie).</span><span class="sxs-lookup"><span data-stu-id="b6351-109">The method exit trace includes the return value (61 in the preceding example).</span></span>  
  
 <span data-ttu-id="b6351-110">Ślady sieci mogą przechwytywać ruch sieciowy, który jest wysyłany z lub odbierany przez aplikację przy użyciu protokołów na poziomie aplikacji, takich jak protokół HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="b6351-110">Network traces can capture network traffic that is sent from or received by your application using application-level protocols such as Hypertext Transfer Protocol (HTTP).</span></span> <span data-ttu-id="b6351-111">Te dane można przechwytywać jako tekst i, opcjonalnie, dane szesnastkowe.</span><span class="sxs-lookup"><span data-stu-id="b6351-111">This data can be captured as text and, optionally, hexadecimal data.</span></span> <span data-ttu-id="b6351-112">Dane szesnastkowe są dostępne po określeniu **includehex** jako wartości atrybutu **TraceMode** .</span><span class="sxs-lookup"><span data-stu-id="b6351-112">Hexadecimal data is available when you specify **includehex** as the value of the **tracemode** attribute.</span></span> <span data-ttu-id="b6351-113">(Aby uzyskać szczegółowe informacje na temat tego atrybutu [, zobacz How to: Skonfiguruj śledzenie](../../../docs/framework/network-programming/how-to-configure-network-tracing.md)sieci). Poniższy przykład śledzenia został wygenerowany przy użyciu **includehex**.</span><span class="sxs-lookup"><span data-stu-id="b6351-113">(For detailed information about this attribute, see [How to: Configure Network Tracing](../../../docs/framework/network-programming/how-to-configure-network-tracing.md).) The following example trace was generated using **includehex**.</span></span>  
  
 `[1692]   (1142)   00000000 : 47 45 54 20 2F 77 70 61-64 2E 64 61 74 20 48 54 : GET /wpad.dat HT`  
  
 `[1692]   (1142)   00000010 : 54 50 2F 31 2E 31 0D 0A-48 6F 73 74 3A 20 69 74 : TP/1.1..Host: it`  
  
 `[1692]   (1142)   00000020 : 67 70 72 6F 78 79 0D 0A-43 6F 6E 6E 65 63 74 69 : gproxy..Connecti`  
  
 `[1692]   (1142)   00000030 : 6F 6E 3A 20 43 6C 6F 73-65 0D 0A 0D 0A     : on: Close....`  
  
 <span data-ttu-id="b6351-114">Aby pominąć dane szesnastkowe, określ **protocolonly** jako wartość atrybutu **TraceMode** .</span><span class="sxs-lookup"><span data-stu-id="b6351-114">To omit hexadecimal data, specify **protocolonly** as the value for the **tracemode** attribute.</span></span> <span data-ttu-id="b6351-115">Poniższy przykład pokazuje ślad, gdy **protocolonly** jest określony.</span><span class="sxs-lookup"><span data-stu-id="b6351-115">The following example shows the trace when **protocolonly** is specified.</span></span>  
  
 `[2444]   (594)   Data from ConnectStream#33574638::WriteHeaders<<GET /wpad.dat HTTP/1.1`  
  
 `Host: itgproxy`  
  
 `Connection: Close`  
  
## <a name="see-also"></a><span data-ttu-id="b6351-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b6351-116">See also</span></span>

- [<span data-ttu-id="b6351-117">Włączanie śledzenia sieci</span><span class="sxs-lookup"><span data-stu-id="b6351-117">Enabling Network Tracing</span></span>](../../../docs/framework/network-programming/enabling-network-tracing.md)
- [<span data-ttu-id="b6351-118">Instrukcje: Konfigurowanie śledzenia sieci</span><span class="sxs-lookup"><span data-stu-id="b6351-118">How to: Configure Network Tracing</span></span>](../../../docs/framework/network-programming/how-to-configure-network-tracing.md)
- [<span data-ttu-id="b6351-119">Śledzenie sieci w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b6351-119">Network Tracing in the .NET Framework</span></span>](../../../docs/framework/network-programming/network-tracing.md)
