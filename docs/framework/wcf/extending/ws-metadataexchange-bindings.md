---
title: Powiązania elementu WS-MetadataExchange
ms.date: 03/30/2017
ms.assetid: 10f8de5d-b81d-4ea7-b37e-7f2c00c39714
ms.openlocfilehash: 03e6e6d5ee7e69b397acd0f51b8037f02c1804ec
ms.sourcegitcommit: 0888d7b24f475c346a3f444de8d83ec1ca7cd234
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2018
ms.locfileid: "53767351"
---
# <a name="ws-metadataexchange-bindings"></a><span data-ttu-id="33f73-102">Powiązania elementu WS-MetadataExchange</span><span class="sxs-lookup"><span data-stu-id="33f73-102">WS-MetadataExchange Bindings</span></span>
<span data-ttu-id="33f73-103">W tym temacie opisano, jak domyślne powiązania wymiany metadanych są tworzone dla różnych transportu.</span><span class="sxs-lookup"><span data-stu-id="33f73-103">This topic describes how the default metadata exchange bindings are constructed for various transports.</span></span>  
  
## <a name="the-default-bindings"></a><span data-ttu-id="33f73-104">Domyślne powiązania</span><span class="sxs-lookup"><span data-stu-id="33f73-104">The Default Bindings</span></span>  
  
|<span data-ttu-id="33f73-105">Domyślna nazwa powiązania</span><span class="sxs-lookup"><span data-stu-id="33f73-105">Default Binding Name</span></span>|<span data-ttu-id="33f73-106">Jak jest konstruowany powiązania</span><span class="sxs-lookup"><span data-stu-id="33f73-106">How the binding is constructed</span></span>|  
|--------------------------|------------------------------------|  
|<span data-ttu-id="33f73-107">mexHttpBinding</span><span class="sxs-lookup"><span data-stu-id="33f73-107">mexHttpBinding</span></span>|<span data-ttu-id="33f73-108">A <xref:System.ServiceModel.WSHttpBinding> z wyłączonymi zabezpieczeniami na poziomie transportu.</span><span class="sxs-lookup"><span data-stu-id="33f73-108">A <xref:System.ServiceModel.WSHttpBinding> with transport-level security disabled.</span></span>|  
|<span data-ttu-id="33f73-109">mexHttpsBinding</span><span class="sxs-lookup"><span data-stu-id="33f73-109">mexHttpsBinding</span></span>|<span data-ttu-id="33f73-110">A <xref:System.ServiceModel.WSHttpBinding> , która obsługuje zabezpieczenia na poziomie transportu.</span><span class="sxs-lookup"><span data-stu-id="33f73-110">A <xref:System.ServiceModel.WSHttpBinding> that supports transport-level security.</span></span>|  
|<span data-ttu-id="33f73-111">mexNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="33f73-111">mexNamedPipeBinding</span></span>|<span data-ttu-id="33f73-112">A <xref:System.ServiceModel.Channels.CustomBinding> z <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> przy użyciu wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="33f73-112">A  <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> using the default values.</span></span>|  
|<span data-ttu-id="33f73-113">mexTcpBinding</span><span class="sxs-lookup"><span data-stu-id="33f73-113">mexTcpBinding</span></span>|<span data-ttu-id="33f73-114">A <xref:System.ServiceModel.Channels.CustomBinding> z <xref:System.ServiceModel.Channels.TcpTransportBindingElement> przy użyciu wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="33f73-114">A <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.TcpTransportBindingElement> using default values.</span></span>|
