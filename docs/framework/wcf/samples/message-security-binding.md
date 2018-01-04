---
title: "Powiązanie zabezpieczeń komunikatów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4570ce7-864e-461b-85d8-0f7bcc53c2c8
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: f0c8b125d3fc313dca4140b871ccea8165329fda
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="message-security-binding"></a><span data-ttu-id="f866e-102">Powiązanie zabezpieczeń komunikatów</span><span class="sxs-lookup"><span data-stu-id="f866e-102">Message Security Binding</span></span>
<span data-ttu-id="f866e-103">Ta sekcja zawiera przykłady ilustrujące powiązanie zabezpieczeń komunikatów w usługach systemu Windows w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f866e-103">This section contains samples that demonstrate message security binding in Windows Services in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f866e-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="f866e-104">In This Section</span></span>  
 [<span data-ttu-id="f866e-105">Zabezpieczenia komunikatów z anonimowością</span><span class="sxs-lookup"><span data-stu-id="f866e-105">Message Security Anonymous</span></span>](../../../../docs/framework/wcf/samples/message-security-anonymous.md)  
 <span data-ttu-id="f866e-106">W tym przykładzie pokazano, jak wdrożyć [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikacji używającej zabezpieczenia na poziomie komunikatu bez uwierzytelniania klienta, ale który wymaga uwierzytelniania serwera za pomocą certyfikatu X.509 serwera.</span><span class="sxs-lookup"><span data-stu-id="f866e-106">This sample demonstrates how to implement a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] application that uses message-level security with no client authentication but that requires server authentication using the server's X.509 certificate.</span></span>  
  
 [<span data-ttu-id="f866e-107">Certyfikat zabezpieczeń komunikatów</span><span class="sxs-lookup"><span data-stu-id="f866e-107">Message Security Certificate</span></span>](../../../../docs/framework/wcf/samples/message-security-certificate.md)  
 <span data-ttu-id="f866e-108">W tym przykładzie pokazano, jak wdrożyć aplikację, która używa WS-Security z X.509 v3 certyfikatu uwierzytelniania klienta i wymaga przy użyciu serwera X.509 v3 certyfikatu uwierzytelniania serwera.</span><span class="sxs-lookup"><span data-stu-id="f866e-108">This sample demonstrates how to implement an application that uses WS-Security with X.509 v3 certificate authentication for the client and requires server authentication using the server's X.509 v3 certificate.</span></span>  
  
 [<span data-ttu-id="f866e-109">Nazwa użytkownika zabezpieczeń komunikatów</span><span class="sxs-lookup"><span data-stu-id="f866e-109">Message Security User Name</span></span>](../../../../docs/framework/wcf/samples/message-security-user-name.md)  
 <span data-ttu-id="f866e-110">W tym przykładzie pokazano, jak wdrożyć aplikację, która używa WS-Security przy użyciu uwierzytelniania nazwa użytkownika dla klienta i wymaga uwierzytelniania serwera przy użyciu certyfikatu X.509v3 serwera.</span><span class="sxs-lookup"><span data-stu-id="f866e-110">This sample demonstrates how to implement an application that uses WS-Security with username authentication for the client and requires server authentication using the server's X.509v3 certificate.</span></span>  
  
 [<span data-ttu-id="f866e-111">Zabezpieczenia komunikatów — Windows</span><span class="sxs-lookup"><span data-stu-id="f866e-111">Message Security Windows</span></span>](../../../../docs/framework/wcf/samples/message-security-windows.md)  
 <span data-ttu-id="f866e-112">W tym przykładzie pokazano, jak skonfigurować <xref:System.ServiceModel.WSHttpBinding> powiązania w celu użycia zabezpieczenia na poziomie komunikatu z uwierzytelnianiem systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="f866e-112">This sample demonstrates how to configure a <xref:System.ServiceModel.WSHttpBinding> binding to use message-level security with Windows authentication.</span></span>
