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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 23752cb259accb1df6093a4b1d90a2541fd771d4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ws-metadataexchange-bindings"></a><span data-ttu-id="4918d-102">Powiązania elementu WS-MetadataExchange</span><span class="sxs-lookup"><span data-stu-id="4918d-102">WS-MetadataExchange Bindings</span></span>
<span data-ttu-id="4918d-103">W tym temacie opisano sposób powiązania wymiany metadanych domyślne są wykonane dla różnych transportu.</span><span class="sxs-lookup"><span data-stu-id="4918d-103">This topic describes how the default metadata exchange bindings are constructed for various transports.</span></span>  
  
## <a name="the-default-bindings"></a><span data-ttu-id="4918d-104">Powiązania domyślnego</span><span class="sxs-lookup"><span data-stu-id="4918d-104">The Default Bindings</span></span>  
  
|<span data-ttu-id="4918d-105">Domyślna nazwa powiązania</span><span class="sxs-lookup"><span data-stu-id="4918d-105">Default Binding Name</span></span>|<span data-ttu-id="4918d-106">Sposób powiązania jest tworzony</span><span class="sxs-lookup"><span data-stu-id="4918d-106">How the binding is constructed</span></span>|  
|--------------------------|------------------------------------|  
|<span data-ttu-id="4918d-107">MexHttpBinding</span><span class="sxs-lookup"><span data-stu-id="4918d-107">MexHttpBinding</span></span>|<span data-ttu-id="4918d-108">A <xref:System.ServiceModel.WSHttpBinding> z zabezpieczeniami na poziomie transportu wyłączone.</span><span class="sxs-lookup"><span data-stu-id="4918d-108">A <xref:System.ServiceModel.WSHttpBinding> with transport-level security disabled.</span></span>|  
|<span data-ttu-id="4918d-109">MexHttpsBinding</span><span class="sxs-lookup"><span data-stu-id="4918d-109">MexHttpsBinding</span></span>|<span data-ttu-id="4918d-110">A <xref:System.ServiceModel.WSHttpBinding> obsługującego zabezpieczenia na poziomie transportu.</span><span class="sxs-lookup"><span data-stu-id="4918d-110">A <xref:System.ServiceModel.WSHttpBinding> that supports transport-level security.</span></span>|  
|<span data-ttu-id="4918d-111">MexNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="4918d-111">MexNamedPipeBinding</span></span>|<span data-ttu-id="4918d-112">A <xref:System.ServiceModel.Channels.CustomBinding> z <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> przy użyciu wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="4918d-112">A  <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> using the default values.</span></span>|  
|<span data-ttu-id="4918d-113">MexTcpBinding</span><span class="sxs-lookup"><span data-stu-id="4918d-113">MexTcpBinding</span></span>|<span data-ttu-id="4918d-114">A <xref:System.ServiceModel.Channels.CustomBinding> z <xref:System.ServiceModel.Channels.TcpTransportBindingElement> przy użyciu wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="4918d-114">A <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.TcpTransportBindingElement> using default values.</span></span>|
