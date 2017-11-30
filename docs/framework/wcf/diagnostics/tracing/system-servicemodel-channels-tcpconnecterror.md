---
title: System.ServiceModel.Channels.TcpConnectError
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 22d93797-072e-405d-a3e0-5c519ddf290b
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2e17a4c51332317bb5b77d2ab23c936999b2706e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelstcpconnecterror"></a><span data-ttu-id="0b3b2-102">System.ServiceModel.Channels.TcpConnectError</span><span class="sxs-lookup"><span data-stu-id="0b3b2-102">System.ServiceModel.Channels.TcpConnectError</span></span>
<span data-ttu-id="0b3b2-103">Nie można wykonać operacji nawiązywania połączeń TCP.</span><span class="sxs-lookup"><span data-stu-id="0b3b2-103">The TCP connect operation failed.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0b3b2-104">Opis</span><span class="sxs-lookup"><span data-stu-id="0b3b2-104">Description</span></span>  
 <span data-ttu-id="0b3b2-105">To ostrzeżenie śledzenia poziomu oznacza błąd do nawiązania połączenia z punktem końcowym protokołu TCP.</span><span class="sxs-lookup"><span data-stu-id="0b3b2-105">This warning level trace indicates a failure to connect to a TCP endpoint.</span></span> <span data-ttu-id="0b3b2-106">Może to się zdarzyć, jeśli zdalny punkt końcowy nie odpowiada na danego adresu IP i portu.</span><span class="sxs-lookup"><span data-stu-id="0b3b2-106">This could happen if the remote endpoint is not responding at a given IP address and port.</span></span> <span data-ttu-id="0b3b2-107">Ślad można zignorować, jeśli kolejne próbuje połączyć się powieść adresów (np. adresy IPv4 lub IPv6, lub inne adresy IP reprezentujący nazwę danego hosta) innych prawidłowymi adresami IP.</span><span class="sxs-lookup"><span data-stu-id="0b3b2-107">This trace can be ignored if subsequent attempts to connect to other valid IP addresses (such as IPv4 or IPv6 addresses, or other IP addresses representing a given hostname) succeed.</span></span> <span data-ttu-id="0b3b2-108">Wyjątek w obrębie tego śledzenia mogą zawierać dodatkowe informacje o tym błędzie.</span><span class="sxs-lookup"><span data-stu-id="0b3b2-108">The exception within this trace can reveal additional information about the error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b3b2-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0b3b2-109">See Also</span></span>  
 [<span data-ttu-id="0b3b2-110">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="0b3b2-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="0b3b2-111">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="0b3b2-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="0b3b2-112">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="0b3b2-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
