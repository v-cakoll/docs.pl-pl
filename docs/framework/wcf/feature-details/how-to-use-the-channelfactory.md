---
title: 'Instrukcje: Używanie elementu ChannelFactory'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d48f01b5-582b-4c8b-b547-8adddae7e371
ms.openlocfilehash: 4bb2053fb50931756e79d5346a3f14d2acbe04f6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595313"
---
# <a name="how-to-use-the-channelfactory"></a>Instrukcje: Używanie elementu ChannelFactory
Klasa generyczna <xref:System.ServiceModel.ChannelFactory%601> jest używana w zaawansowanych scenariuszach, które wymagają utworzenia fabryki kanałów, której można użyć do utworzenia więcej niż jednego kanału.  
  
### <a name="to-create-and-use-the-channelfactory-class"></a>Aby utworzyć i użyć klasy ChannelFactory  
  
1. Kompiluj i uruchamiaj usługę Windows Communication Foundation (WCF). Aby uzyskać więcej informacji, zobacz [projektowanie i implementowanie usług](../designing-and-implementing-services.md), [Konfigurowanie usług](../configuring-services.md)i [usług hostingowych](../hosting-services.md).  
  
2. Użyj [Narzędzia do przesyłania metadanych modelu ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) w celu wygenerowania kontraktu (interfejsu) dla klienta.  
  
3. W kodzie klienta Użyj <xref:System.ServiceModel.ChannelFactory%601> klasy, aby utworzyć odbiorniki wielu punktów końcowych.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[c_HowToUseChannelFactory#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtousechannelfactory/cs/source.cs#1)]
 [!code-vb[c_HowToUseChannelFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtousechannelfactory/vb/source.vb#1)]
