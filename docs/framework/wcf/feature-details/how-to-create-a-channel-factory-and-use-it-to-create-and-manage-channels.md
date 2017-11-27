---
title: "Instrukcje: Tworzenie fabryki kanałów i używanie jej do tworzenia kanałów oraz zarządzania nimi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 018dcc30-9f61-419e-af8e-412a85e8d282
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cb2e8384fca96149babb5df01e25a1b890db6ad3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-channel-factory-and-use-it-to-create-and-manage-channels"></a><span data-ttu-id="e4f9e-102">Instrukcje: Tworzenie fabryki kanałów i używanie jej do tworzenia kanałów oraz zarządzania nimi</span><span class="sxs-lookup"><span data-stu-id="e4f9e-102">How to: Create a Channel Factory and Use it to Create and Manage Channels</span></span>
<span data-ttu-id="e4f9e-103"><xref:System.ServiceModel.DuplexChannelFactory%601> Klasa umożliwia tworzenie i zarządzanie nimi kanałach dupleksowych różnych typów używanych przez klientów do wysyłania i odbierania wiadomości do i z punktów końcowych usługi.</span><span class="sxs-lookup"><span data-stu-id="e4f9e-103">The <xref:System.ServiceModel.DuplexChannelFactory%601> class provides the means to create and manage duplex channels of different types that clients use to send and receive messages to and from service endpoints.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4f9e-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="e4f9e-104">Example</span></span>  
 <span data-ttu-id="e4f9e-105">Poniższy kod przedstawia sposób utworzyć fabryki kanałów i użyć go do tworzenia i zarządzania kanałów.</span><span class="sxs-lookup"><span data-stu-id="e4f9e-105">The following code shows how to create a channel factory and use it to create and manage channels.</span></span>  
  
 [!code-csharp[S_CustomAuthentication#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_customauthentication/cs/instance.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e4f9e-106">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e4f9e-106">See Also</span></span>  
 <xref:System.ServiceModel.DuplexChannelFactory%601>
