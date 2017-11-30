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
# <a name="ws-metadataexchange-bindings"></a>Powiązania elementu WS-MetadataExchange
W tym temacie opisano sposób powiązania wymiany metadanych domyślne są wykonane dla różnych transportu.  
  
## <a name="the-default-bindings"></a>Powiązania domyślnego  
  
|Domyślna nazwa powiązania|Sposób powiązania jest tworzony|  
|--------------------------|------------------------------------|  
|MexHttpBinding|A <xref:System.ServiceModel.WSHttpBinding> z zabezpieczeniami na poziomie transportu wyłączone.|  
|MexHttpsBinding|A <xref:System.ServiceModel.WSHttpBinding> obsługującego zabezpieczenia na poziomie transportu.|  
|MexNamedPipeBinding|A <xref:System.ServiceModel.Channels.CustomBinding> z <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> przy użyciu wartości domyślnych.|  
|MexTcpBinding|A <xref:System.ServiceModel.Channels.CustomBinding> z <xref:System.ServiceModel.Channels.TcpTransportBindingElement> przy użyciu wartości domyślnych.|
