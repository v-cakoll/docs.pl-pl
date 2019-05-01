---
title: 'Instrukcje: używanie elementu ChannelFactory'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d48f01b5-582b-4c8b-b547-8adddae7e371
ms.openlocfilehash: 7d542a3dcae514e75194b49c23a8dec5dd7e8c3b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62047259"
---
# <a name="how-to-use-the-channelfactory"></a>Instrukcje: używanie elementu ChannelFactory
Ogólny <xref:System.ServiceModel.ChannelFactory%601> klasa jest używana w zaawansowanych scenariuszach, które wymagają utworzenia fabryki kanałów, który może służyć do utworzenia kanału więcej niż jeden.  
  
### <a name="to-create-and-use-the-channelfactory-class"></a>Tworzenie i używanie klasy ChannelFactory  
  
1. Skompiluj i uruchom usługę Windows Communication Foundation (WCF). Aby uzyskać więcej informacji, zobacz [projektowanie i Implementowanie usług](../../../../docs/framework/wcf/designing-and-implementing-services.md), [Konfigurowanie usług](../../../../docs/framework/wcf/configuring-services.md), i [usług obsługującego](../../../../docs/framework/wcf/hosting-services.md).  
  
2. Użyj [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do generowania kontraktu (interfejs) dla klienta.  
  
3. W kodzie klienta użyć <xref:System.ServiceModel.ChannelFactory%601> klasy, aby utworzyć wiele odbiorników punktu końcowego.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[c_HowToUseChannelFactory#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtousechannelfactory/cs/source.cs#1)]
 [!code-vb[c_HowToUseChannelFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtousechannelfactory/vb/source.vb#1)]
