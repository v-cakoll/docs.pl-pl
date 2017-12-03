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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 46110c965e40ce1fc9297014b198e1a95598a23c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelchannelstcpconnecterror"></a><span data-ttu-id="1ca80-102">System.ServiceModel.Channels.TcpConnectError</span><span class="sxs-lookup"><span data-stu-id="1ca80-102">System.ServiceModel.Channels.TcpConnectError</span></span>
<span data-ttu-id="1ca80-103">Nie można wykonać operacji nawiązywania połączeń TCP.</span><span class="sxs-lookup"><span data-stu-id="1ca80-103">The TCP connect operation failed.</span></span>  
  
## <a name="description"></a><span data-ttu-id="1ca80-104">Opis</span><span class="sxs-lookup"><span data-stu-id="1ca80-104">Description</span></span>  
 <span data-ttu-id="1ca80-105">To ostrzeżenie śledzenia poziomu oznacza błąd do nawiązania połączenia z punktem końcowym protokołu TCP.</span><span class="sxs-lookup"><span data-stu-id="1ca80-105">This warning level trace indicates a failure to connect to a TCP endpoint.</span></span> <span data-ttu-id="1ca80-106">Może to się zdarzyć, jeśli zdalny punkt końcowy nie odpowiada na danego adresu IP i portu.</span><span class="sxs-lookup"><span data-stu-id="1ca80-106">This could happen if the remote endpoint is not responding at a given IP address and port.</span></span> <span data-ttu-id="1ca80-107">Ślad można zignorować, jeśli kolejne próbuje połączyć się powieść adresów (np. adresy IPv4 lub IPv6, lub inne adresy IP reprezentujący nazwę danego hosta) innych prawidłowymi adresami IP.</span><span class="sxs-lookup"><span data-stu-id="1ca80-107">This trace can be ignored if subsequent attempts to connect to other valid IP addresses (such as IPv4 or IPv6 addresses, or other IP addresses representing a given hostname) succeed.</span></span> <span data-ttu-id="1ca80-108">Wyjątek w obrębie tego śledzenia mogą zawierać dodatkowe informacje o tym błędzie.</span><span class="sxs-lookup"><span data-stu-id="1ca80-108">The exception within this trace can reveal additional information about the error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ca80-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1ca80-109">See Also</span></span>  
 [<span data-ttu-id="1ca80-110">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="1ca80-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="1ca80-111">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="1ca80-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="1ca80-112">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="1ca80-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
