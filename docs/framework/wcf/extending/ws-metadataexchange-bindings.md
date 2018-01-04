---
title: "Powiązania elementu WS-MetadataExchange"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10f8de5d-b81d-4ea7-b37e-7f2c00c39714
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8d305f3bf34b3b14da566fa792552e24e695ef33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ws-metadataexchange-bindings"></a><span data-ttu-id="23b66-102">Powiązania elementu WS-MetadataExchange</span><span class="sxs-lookup"><span data-stu-id="23b66-102">WS-MetadataExchange Bindings</span></span>
<span data-ttu-id="23b66-103">W tym temacie opisano sposób powiązania wymiany metadanych domyślne są wykonane dla różnych transportu.</span><span class="sxs-lookup"><span data-stu-id="23b66-103">This topic describes how the default metadata exchange bindings are constructed for various transports.</span></span>  
  
## <a name="the-default-bindings"></a><span data-ttu-id="23b66-104">Powiązania domyślnego</span><span class="sxs-lookup"><span data-stu-id="23b66-104">The Default Bindings</span></span>  
  
|<span data-ttu-id="23b66-105">Domyślna nazwa powiązania</span><span class="sxs-lookup"><span data-stu-id="23b66-105">Default Binding Name</span></span>|<span data-ttu-id="23b66-106">Sposób powiązania jest tworzony</span><span class="sxs-lookup"><span data-stu-id="23b66-106">How the binding is constructed</span></span>|  
|--------------------------|------------------------------------|  
|<span data-ttu-id="23b66-107">MexHttpBinding</span><span class="sxs-lookup"><span data-stu-id="23b66-107">MexHttpBinding</span></span>|<span data-ttu-id="23b66-108">A <xref:System.ServiceModel.WSHttpBinding> z zabezpieczeniami na poziomie transportu wyłączone.</span><span class="sxs-lookup"><span data-stu-id="23b66-108">A <xref:System.ServiceModel.WSHttpBinding> with transport-level security disabled.</span></span>|  
|<span data-ttu-id="23b66-109">MexHttpsBinding</span><span class="sxs-lookup"><span data-stu-id="23b66-109">MexHttpsBinding</span></span>|<span data-ttu-id="23b66-110">A <xref:System.ServiceModel.WSHttpBinding> obsługującego zabezpieczenia na poziomie transportu.</span><span class="sxs-lookup"><span data-stu-id="23b66-110">A <xref:System.ServiceModel.WSHttpBinding> that supports transport-level security.</span></span>|  
|<span data-ttu-id="23b66-111">MexNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="23b66-111">MexNamedPipeBinding</span></span>|<span data-ttu-id="23b66-112">A <xref:System.ServiceModel.Channels.CustomBinding> z <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> przy użyciu wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="23b66-112">A  <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> using the default values.</span></span>|  
|<span data-ttu-id="23b66-113">MexTcpBinding</span><span class="sxs-lookup"><span data-stu-id="23b66-113">MexTcpBinding</span></span>|<span data-ttu-id="23b66-114">A <xref:System.ServiceModel.Channels.CustomBinding> z <xref:System.ServiceModel.Channels.TcpTransportBindingElement> przy użyciu wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="23b66-114">A <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.TcpTransportBindingElement> using default values.</span></span>|
