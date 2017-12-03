---
title: "Instrukcje: Używanie elementu ChannelFactory"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d48f01b5-582b-4c8b-b547-8adddae7e371
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 37ad5181ad140c3ef3ea8ba5b3774fd44310dca7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-use-the-channelfactory"></a>Instrukcje: Używanie elementu ChannelFactory
Ogólnego <xref:System.ServiceModel.ChannelFactory%601> klasa jest używana w zaawansowanych scenariuszach, które wymagają utworzenia fabryki kanałów, który może służyć do tworzenia więcej niż jeden kanał.  
  
### <a name="to-create-and-use-the-channelfactory-class"></a>Tworzenie i używanie klasy ChannelFactory  
  
1.  Tworzenie i uruchamianie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Projektowanie i Implementowanie usług](../../../../docs/framework/wcf/designing-and-implementing-services.md), [Konfigurowanie usług](../../../../docs/framework/wcf/configuring-services.md), i [usług hostingu](../../../../docs/framework/wcf/hosting-services.md).  
  
2.  Użyj [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do generowania kontraktu (interfejs) dla klienta.  
  
3.  W kodzie klienta, użyj <xref:System.ServiceModel.ChannelFactory%601> klasę, aby utworzyć wiele odbiorników punktu końcowego.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[c_HowToUseChannelFactory#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtousechannelfactory/cs/source.cs#1)]
 [!code-vb[c_HowToUseChannelFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtousechannelfactory/vb/source.vb#1)]
