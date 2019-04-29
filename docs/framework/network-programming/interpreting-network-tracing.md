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
ms.openlocfilehash: 00df193671255e7b40f5c4b86ee952a3e20e3a40
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61642311"
---
# <a name="interpreting-network-tracing"></a><span data-ttu-id="6a630-102">Interpretowanie śledzenia sieci</span><span class="sxs-lookup"><span data-stu-id="6a630-102">Interpreting Network Tracing</span></span>
<span data-ttu-id="6a630-103">Po włączeniu funkcji śledzenia sieci umożliwia śledzenie przechwytywania wywołania aplikacji sprawia, że do różnych <xref:System.Net> składowych klasy.</span><span class="sxs-lookup"><span data-stu-id="6a630-103">When network tracing is enabled, you can use tracing to capture calls your application makes to various <xref:System.Net> class members.</span></span> <span data-ttu-id="6a630-104">Dane wyjściowe z tych wywołań może być podobne do poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="6a630-104">The output from these calls may be similar to the following examples.</span></span>  
  
```  
[588]   (4357)   Entering Socket#33574638::Send()  
[588]   (4387)   Exiting Socket#33574638::Send()-> 61#61  
```  
  
 <span data-ttu-id="6a630-105">W powyższym przykładzie [588] to unikatowy identyfikator bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="6a630-105">In the preceding example, [588] is the current thread's unique identifier.</span></span> <span data-ttu-id="6a630-106">(4357) i (4387) są sygnatury czasowe oznaczający liczbę milisekund, które upłynęły od czasu uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6a630-106">(4357) and (4387) are timestamps denoting the number of milliseconds that have elapsed since the application started.</span></span> <span data-ttu-id="6a630-107">Dane zgodnie z sygnaturą czasową przedstawiono aplikację i wychodzą z metody **Socket.Send**.</span><span class="sxs-lookup"><span data-stu-id="6a630-107">The data following the timestamp shows the application entering and exiting the method **Socket.Send**.</span></span> <span data-ttu-id="6a630-108">Wykonywanie obiektu **wysyłania** metoda ma 33574638 jako unikatowego identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="6a630-108">The object executing the **Send** method has 33574638 as its unique identifier.</span></span> <span data-ttu-id="6a630-109">Śledzenia zakończenia metody zawiera wartość zwracaną (61 w powyższym przykładzie).</span><span class="sxs-lookup"><span data-stu-id="6a630-109">The method exit trace includes the return value (61 in the preceding example).</span></span>  
  
 <span data-ttu-id="6a630-110">Danych śledzenia sieci można przechwytywać ruch sieciowy, który jest wysłanych lub odebranych przez aplikację za pomocą protokoły poziomu aplikacji, takich jak protokół HTTP (Hypertext Transfer).</span><span class="sxs-lookup"><span data-stu-id="6a630-110">Network traces can capture network traffic that is sent from or received by your application using application-level protocols such as Hypertext Transfer Protocol (HTTP).</span></span> <span data-ttu-id="6a630-111">Te dane mogą być przechwytywane jako tekst i, opcjonalnie, dane szesnastkowe.</span><span class="sxs-lookup"><span data-stu-id="6a630-111">This data can be captured as text and, optionally, hexadecimal data.</span></span> <span data-ttu-id="6a630-112">Dane szesnastkowe jest dostępna po określeniu **includehex** jako wartość **tryb_śledzenia** atrybutu.</span><span class="sxs-lookup"><span data-stu-id="6a630-112">Hexadecimal data is available when you specify **includehex** as the value of the **tracemode** attribute.</span></span> <span data-ttu-id="6a630-113">(Aby uzyskać szczegółowe informacje dotyczące tego atrybutu, zobacz [jak: Konfigurowanie śledzenia sieci](../../../docs/framework/network-programming/how-to-configure-network-tracing.md).) Poniższy przykład śledzenia został wygenerowany za pomocą **includehex**.</span><span class="sxs-lookup"><span data-stu-id="6a630-113">(For detailed information about this attribute, see [How to: Configure Network Tracing](../../../docs/framework/network-programming/how-to-configure-network-tracing.md).) The following example trace was generated using **includehex**.</span></span>  
  
 `[1692]   (1142)   00000000 : 47 45 54 20 2F 77 70 61-64 2E 64 61 74 20 48 54 : GET /wpad.dat HT`  
  
 `[1692]   (1142)   00000010 : 54 50 2F 31 2E 31 0D 0A-48 6F 73 74 3A 20 69 74 : TP/1.1..Host: it`  
  
 `[1692]   (1142)   00000020 : 67 70 72 6F 78 79 0D 0A-43 6F 6E 6E 65 63 74 69 : gproxy..Connecti`  
  
 `[1692]   (1142)   00000030 : 6F 6E 3A 20 43 6C 6F 73-65 0D 0A 0D 0A     : on: Close....`  
  
 <span data-ttu-id="6a630-114">Aby pominąć szesnastkowe dane, należy określić **protocolonly** jako wartość pozycji **tryb_śledzenia** atrybutu.</span><span class="sxs-lookup"><span data-stu-id="6a630-114">To omit hexadecimal data, specify **protocolonly** as the value for the **tracemode** attribute.</span></span> <span data-ttu-id="6a630-115">W poniższym przykładzie pokazano śledzenia podczas **protocolonly** jest określony.</span><span class="sxs-lookup"><span data-stu-id="6a630-115">The following example shows the trace when **protocolonly** is specified.</span></span>  
  
 `[2444]   (594)   Data from ConnectStream#33574638::WriteHeaders<<GET /wpad.dat HTTP/1.1`  
  
 `Host: itgproxy`  
  
 `Connection: Close`  
  
## <a name="see-also"></a><span data-ttu-id="6a630-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6a630-116">See also</span></span>

- [<span data-ttu-id="6a630-117">Włączanie śledzenia sieci</span><span class="sxs-lookup"><span data-stu-id="6a630-117">Enabling Network Tracing</span></span>](../../../docs/framework/network-programming/enabling-network-tracing.md)
- [<span data-ttu-id="6a630-118">Instrukcje: Konfigurowanie śledzenia sieci</span><span class="sxs-lookup"><span data-stu-id="6a630-118">How to: Configure Network Tracing</span></span>](../../../docs/framework/network-programming/how-to-configure-network-tracing.md)
- [<span data-ttu-id="6a630-119">Śledzenie sieci w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6a630-119">Network Tracing in the .NET Framework</span></span>](../../../docs/framework/network-programming/network-tracing.md)
