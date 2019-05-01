---
title: Powiązania elementu WS-MetadataExchange
ms.date: 03/30/2017
ms.assetid: 10f8de5d-b81d-4ea7-b37e-7f2c00c39714
ms.openlocfilehash: 03e6e6d5ee7e69b397acd0f51b8037f02c1804ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61795479"
---
# <a name="ws-metadataexchange-bindings"></a><span data-ttu-id="0006e-102">Powiązania elementu WS-MetadataExchange</span><span class="sxs-lookup"><span data-stu-id="0006e-102">WS-MetadataExchange Bindings</span></span>
<span data-ttu-id="0006e-103">W tym temacie opisano, jak domyślne powiązania wymiany metadanych są tworzone dla różnych transportu.</span><span class="sxs-lookup"><span data-stu-id="0006e-103">This topic describes how the default metadata exchange bindings are constructed for various transports.</span></span>  
  
## <a name="the-default-bindings"></a><span data-ttu-id="0006e-104">Domyślne powiązania</span><span class="sxs-lookup"><span data-stu-id="0006e-104">The Default Bindings</span></span>  
  
|<span data-ttu-id="0006e-105">Domyślna nazwa powiązania</span><span class="sxs-lookup"><span data-stu-id="0006e-105">Default Binding Name</span></span>|<span data-ttu-id="0006e-106">Jak jest konstruowany powiązania</span><span class="sxs-lookup"><span data-stu-id="0006e-106">How the binding is constructed</span></span>|  
|--------------------------|------------------------------------|  
|<span data-ttu-id="0006e-107">mexHttpBinding</span><span class="sxs-lookup"><span data-stu-id="0006e-107">mexHttpBinding</span></span>|<span data-ttu-id="0006e-108">A <xref:System.ServiceModel.WSHttpBinding> z wyłączonymi zabezpieczeniami na poziomie transportu.</span><span class="sxs-lookup"><span data-stu-id="0006e-108">A <xref:System.ServiceModel.WSHttpBinding> with transport-level security disabled.</span></span>|  
|<span data-ttu-id="0006e-109">mexHttpsBinding</span><span class="sxs-lookup"><span data-stu-id="0006e-109">mexHttpsBinding</span></span>|<span data-ttu-id="0006e-110">A <xref:System.ServiceModel.WSHttpBinding> , która obsługuje zabezpieczenia na poziomie transportu.</span><span class="sxs-lookup"><span data-stu-id="0006e-110">A <xref:System.ServiceModel.WSHttpBinding> that supports transport-level security.</span></span>|  
|<span data-ttu-id="0006e-111">mexNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="0006e-111">mexNamedPipeBinding</span></span>|<span data-ttu-id="0006e-112">A <xref:System.ServiceModel.Channels.CustomBinding> z <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> przy użyciu wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="0006e-112">A  <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> using the default values.</span></span>|  
|<span data-ttu-id="0006e-113">mexTcpBinding</span><span class="sxs-lookup"><span data-stu-id="0006e-113">mexTcpBinding</span></span>|<span data-ttu-id="0006e-114">A <xref:System.ServiceModel.Channels.CustomBinding> z <xref:System.ServiceModel.Channels.TcpTransportBindingElement> przy użyciu wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="0006e-114">A <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.TcpTransportBindingElement> using default values.</span></span>|
