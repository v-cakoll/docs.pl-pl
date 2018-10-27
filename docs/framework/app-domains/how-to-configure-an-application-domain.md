---
title: 'Porady: konfigurowanie domeny aplikacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, configuring
- ApplicationBase property
ms.assetid: 07ea8438-7a34-49f0-a7e8-3d6ff7e4a482
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 012f0220afa0e444d68af5998fb2492a03a371d8
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183168"
---
# <a name="how-to-configure-an-application-domain"></a>Porady: konfigurowanie domeny aplikacji
Środowisko uruchomieniowe języka wspólnego może udostępniać informacje o konfiguracji dla nowej domeny aplikacji, za pomocą <xref:System.AppDomainSetup> klasy. Podczas tworzenia domen aplikacji, najważniejsze właściwości to <xref:System.AppDomainSetup.ApplicationBase%2A>. Druga **AppDomainSetup** właściwości są używane głównie przez hosty środowiska uruchomieniowego, aby skonfigurować domeny określonej aplikacji.  
  
 **ApplicationBase** właściwość definiuje katalogu głównego aplikacji. Gdy środowisko wykonawcze musi spełnić żądanie typu, sondy jej zestawu zawierającego typ w katalogu określonym przez **ApplicationBase** właściwości.  
  
> [!NOTE]
>  Nowa domena aplikacji dziedziczy tylko **ApplicationBase** właściwość twórcy.  
  
 Poniższy przykład tworzy wystąpienie **AppDomainSetup** klasa, używa tej klasy w celu utworzenia nowej domeny aplikacji, zapisuje te informacje w konsoli i następnie zwalnia domeny aplikacji.  
  
## <a name="example"></a>Przykład  
 [!code-cpp[ADApplicationBase#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADApplicationBase/CPP/source2.cpp#2)]
 [!code-csharp[ADApplicationBase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADApplicationBase/CS/source2.cs#2)]
 [!code-vb[ADApplicationBase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADApplicationBase/VB/source2.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
- [Programowanie z domenami aplikacji](application-domains.md#programming-with-application-domains)  
- [Używanie domen aplikacji](../../../docs/framework/app-domains/use.md)
