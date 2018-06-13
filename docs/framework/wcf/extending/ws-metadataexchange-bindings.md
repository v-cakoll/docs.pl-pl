---
title: Powiązania elementu WS-MetadataExchange
ms.date: 03/30/2017
ms.assetid: 10f8de5d-b81d-4ea7-b37e-7f2c00c39714
ms.openlocfilehash: 384e5bb05ba4263f245f6901b84e2388ea19bd73
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488627"
---
# <a name="ws-metadataexchange-bindings"></a><span data-ttu-id="46d2f-102">Powiązania elementu WS-MetadataExchange</span><span class="sxs-lookup"><span data-stu-id="46d2f-102">WS-MetadataExchange Bindings</span></span>
<span data-ttu-id="46d2f-103">W tym temacie opisano sposób powiązania wymiany metadanych domyślne są wykonane dla różnych transportu.</span><span class="sxs-lookup"><span data-stu-id="46d2f-103">This topic describes how the default metadata exchange bindings are constructed for various transports.</span></span>  
  
## <a name="the-default-bindings"></a><span data-ttu-id="46d2f-104">Powiązania domyślnego</span><span class="sxs-lookup"><span data-stu-id="46d2f-104">The Default Bindings</span></span>  
  
|<span data-ttu-id="46d2f-105">Domyślna nazwa powiązania</span><span class="sxs-lookup"><span data-stu-id="46d2f-105">Default Binding Name</span></span>|<span data-ttu-id="46d2f-106">Sposób powiązania jest tworzony</span><span class="sxs-lookup"><span data-stu-id="46d2f-106">How the binding is constructed</span></span>|  
|--------------------------|------------------------------------|  
|<span data-ttu-id="46d2f-107">MexHttpBinding</span><span class="sxs-lookup"><span data-stu-id="46d2f-107">MexHttpBinding</span></span>|<span data-ttu-id="46d2f-108">A <xref:System.ServiceModel.WSHttpBinding> z zabezpieczeniami na poziomie transportu wyłączone.</span><span class="sxs-lookup"><span data-stu-id="46d2f-108">A <xref:System.ServiceModel.WSHttpBinding> with transport-level security disabled.</span></span>|  
|<span data-ttu-id="46d2f-109">MexHttpsBinding</span><span class="sxs-lookup"><span data-stu-id="46d2f-109">MexHttpsBinding</span></span>|<span data-ttu-id="46d2f-110">A <xref:System.ServiceModel.WSHttpBinding> obsługującego zabezpieczenia na poziomie transportu.</span><span class="sxs-lookup"><span data-stu-id="46d2f-110">A <xref:System.ServiceModel.WSHttpBinding> that supports transport-level security.</span></span>|  
|<span data-ttu-id="46d2f-111">MexNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="46d2f-111">MexNamedPipeBinding</span></span>|<span data-ttu-id="46d2f-112">A <xref:System.ServiceModel.Channels.CustomBinding> z <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> przy użyciu wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="46d2f-112">A  <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> using the default values.</span></span>|  
|<span data-ttu-id="46d2f-113">MexTcpBinding</span><span class="sxs-lookup"><span data-stu-id="46d2f-113">MexTcpBinding</span></span>|<span data-ttu-id="46d2f-114">A <xref:System.ServiceModel.Channels.CustomBinding> z <xref:System.ServiceModel.Channels.TcpTransportBindingElement> przy użyciu wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="46d2f-114">A <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.TcpTransportBindingElement> using default values.</span></span>|
