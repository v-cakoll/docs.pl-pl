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
# <a name="ws-metadataexchange-bindings"></a>Powiązania elementu WS-MetadataExchange
W tym temacie opisano, jak domyślne powiązania wymiany metadanych są tworzone dla różnych transportu.  
  
## <a name="the-default-bindings"></a>Domyślne powiązania  
  
|Domyślna nazwa powiązania|Jak jest konstruowany powiązania|  
|--------------------------|------------------------------------|  
|mexHttpBinding|A <xref:System.ServiceModel.WSHttpBinding> z wyłączonymi zabezpieczeniami na poziomie transportu.|  
|mexHttpsBinding|A <xref:System.ServiceModel.WSHttpBinding> , która obsługuje zabezpieczenia na poziomie transportu.|  
|mexNamedPipeBinding|A <xref:System.ServiceModel.Channels.CustomBinding> z <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> przy użyciu wartości domyślnych.|  
|mexTcpBinding|A <xref:System.ServiceModel.Channels.CustomBinding> z <xref:System.ServiceModel.Channels.TcpTransportBindingElement> przy użyciu wartości domyślnych.|
