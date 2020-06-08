---
title: Interpretowanie śledzenia sieci
description: Dowiedz się, jak używać funkcji śledzenia do przechwytywania wywołań wysyłanych przez aplikację do różnych elementów członkowskich klasy System.Net w .NET Framework.
ms.date: 03/30/2017
helpviewer_keywords:
- TraceMode attribute
- hexidecimal data, network tracing output
- network tracing, analyzing
- protocolonly
- text, network tracing output
- includehex
ms.assetid: ad22b4b8-00af-4778-9cca-cb609ce1f8ff
ms.openlocfilehash: 7a17e4ba14d8c5fe136667c4eb5bc5b2fd7a8242
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502369"
---
# <a name="interpreting-network-tracing"></a><span data-ttu-id="ed5a4-103">Interpretowanie śledzenia sieci</span><span class="sxs-lookup"><span data-stu-id="ed5a4-103">Interpreting Network Tracing</span></span>
<span data-ttu-id="ed5a4-104">Po włączeniu śledzenia sieci można użyć funkcji śledzenia do przechwytywania wywołań aplikacji do różnych <xref:System.Net> elementów członkowskich klasy.</span><span class="sxs-lookup"><span data-stu-id="ed5a4-104">When network tracing is enabled, you can use tracing to capture calls your application makes to various <xref:System.Net> class members.</span></span> <span data-ttu-id="ed5a4-105">Dane wyjściowe tych wywołań mogą wyglądać podobnie jak w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="ed5a4-105">The output from these calls may be similar to the following examples.</span></span>  
  
```output
[588]   (4357)   Entering Socket#33574638::Send()  
[588]   (4387)   Exiting Socket#33574638::Send()-> 61#61
```  
  
 <span data-ttu-id="ed5a4-106">W poprzednim przykładzie [588] jest unikatowym identyfikatorem bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="ed5a4-106">In the preceding example, [588] is the current thread's unique identifier.</span></span> <span data-ttu-id="ed5a4-107">(4357) i (4387) to sygnatury czasowe określające liczbę milisekund, które upłynęły od momentu uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ed5a4-107">(4357) and (4387) are timestamps denoting the number of milliseconds that have elapsed since the application started.</span></span> <span data-ttu-id="ed5a4-108">Dane po znaczniku czasu pokazują aplikację wprowadzającą i opuszczają metodę **Socket. Send**.</span><span class="sxs-lookup"><span data-stu-id="ed5a4-108">The data following the timestamp shows the application entering and exiting the method **Socket.Send**.</span></span> <span data-ttu-id="ed5a4-109">Obiekt wykonujący metodę **send** ma 33574638 jako unikatowy identyfikator.</span><span class="sxs-lookup"><span data-stu-id="ed5a4-109">The object executing the **Send** method has 33574638 as its unique identifier.</span></span> <span data-ttu-id="ed5a4-110">Ślad wyjścia metody zawiera wartość zwracaną (61 w poprzednim przykładzie).</span><span class="sxs-lookup"><span data-stu-id="ed5a4-110">The method exit trace includes the return value (61 in the preceding example).</span></span>  
  
 <span data-ttu-id="ed5a4-111">Ślady sieci mogą przechwytywać ruch sieciowy, który jest wysyłany z lub odbierany przez aplikację przy użyciu protokołów na poziomie aplikacji, takich jak protokół HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="ed5a4-111">Network traces can capture network traffic that is sent from or received by your application using application-level protocols such as Hypertext Transfer Protocol (HTTP).</span></span> <span data-ttu-id="ed5a4-112">Te dane można przechwytywać jako tekst i, opcjonalnie, dane szesnastkowe.</span><span class="sxs-lookup"><span data-stu-id="ed5a4-112">This data can be captured as text and, optionally, hexadecimal data.</span></span> <span data-ttu-id="ed5a4-113">Dane szesnastkowe są dostępne po określeniu **includehex** jako wartości atrybutu **TraceMode** .</span><span class="sxs-lookup"><span data-stu-id="ed5a4-113">Hexadecimal data is available when you specify **includehex** as the value of the **tracemode** attribute.</span></span> <span data-ttu-id="ed5a4-114">(Aby uzyskać szczegółowe informacje na temat tego atrybutu, zobacz [How to: Configure Network Tracing](how-to-configure-network-tracing.md).) Poniższy przykład śledzenia został wygenerowany przy użyciu **includehex**.</span><span class="sxs-lookup"><span data-stu-id="ed5a4-114">(For detailed information about this attribute, see [How to: Configure Network Tracing](how-to-configure-network-tracing.md).) The following example trace was generated using **includehex**.</span></span>  
  
 `[1692]   (1142)   00000000 : 47 45 54 20 2F 77 70 61-64 2E 64 61 74 20 48 54 : GET /wpad.dat HT`  
  
 `[1692]   (1142)   00000010 : 54 50 2F 31 2E 31 0D 0A-48 6F 73 74 3A 20 69 74 : TP/1.1..Host: it`  
  
 `[1692]   (1142)   00000020 : 67 70 72 6F 78 79 0D 0A-43 6F 6E 6E 65 63 74 69 : gproxy..Connecti`  
  
 `[1692]   (1142)   00000030 : 6F 6E 3A 20 43 6C 6F 73-65 0D 0A 0D 0A     : on: Close....`  
  
 <span data-ttu-id="ed5a4-115">Aby pominąć dane szesnastkowe, określ **protocolonly** jako wartość atrybutu **TraceMode** .</span><span class="sxs-lookup"><span data-stu-id="ed5a4-115">To omit hexadecimal data, specify **protocolonly** as the value for the **tracemode** attribute.</span></span> <span data-ttu-id="ed5a4-116">Poniższy przykład pokazuje ślad, gdy **protocolonly** jest określony.</span><span class="sxs-lookup"><span data-stu-id="ed5a4-116">The following example shows the trace when **protocolonly** is specified.</span></span>  
  
 `[2444]   (594)   Data from ConnectStream#33574638::WriteHeaders<<GET /wpad.dat HTTP/1.1`  
  
 `Host: itgproxy`  
  
 `Connection: Close`  
  
## <a name="see-also"></a><span data-ttu-id="ed5a4-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ed5a4-117">See also</span></span>

- [<span data-ttu-id="ed5a4-118">Włączanie śledzenia sieci</span><span class="sxs-lookup"><span data-stu-id="ed5a4-118">Enabling Network Tracing</span></span>](enabling-network-tracing.md)
- [<span data-ttu-id="ed5a4-119">Instrukcje: konfigurowanie śledzenia sieci</span><span class="sxs-lookup"><span data-stu-id="ed5a4-119">How to: Configure Network Tracing</span></span>](how-to-configure-network-tracing.md)
- [<span data-ttu-id="ed5a4-120">Śledzenie sieci w .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ed5a4-120">Network Tracing in the .NET Framework</span></span>](network-tracing.md)
