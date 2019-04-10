---
title: 'Instrukcje: Konfigurowanie domeny aplikacji'
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
ms.openlocfilehash: fe0c7ecf1b0daf0e9ea56ec590083fe1ccd2d693
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225082"
---
# <a name="how-to-configure-an-application-domain"></a>Instrukcje: Konfigurowanie domeny aplikacji
Środowisko uruchomieniowe języka wspólnego może udostępniać informacje o konfiguracji dla nowej domeny aplikacji, za pomocą <xref:System.AppDomainSetup> klasy. Podczas tworzenia domen aplikacji, najważniejsze właściwości to <xref:System.AppDomainSetup.ApplicationBase%2A>. Druga **AppDomainSetup** właściwości są używane głównie przez hosty środowiska uruchomieniowego, aby skonfigurować domeny określonej aplikacji.  
  
 **ApplicationBase** właściwość definiuje katalogu głównego aplikacji. Gdy środowisko wykonawcze musi spełnić żądanie typu, sondy jej zestawu zawierającego typ w katalogu określonym przez **ApplicationBase** właściwości.  
  
> [!NOTE]
>  Nowa domena aplikacji dziedziczy tylko **ApplicationBase** właściwość twórcy.  
  
 Poniższy przykład tworzy wystąpienie **AppDomainSetup** klasa, używa tej klasy w celu utworzenia nowej domeny aplikacji, zapisuje te informacje w konsoli i następnie zwalnia domeny aplikacji.  
  
## <a name="example"></a>Przykład  
 [!code-cpp[ADApplicationBase#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADApplicationBase/CPP/source2.cpp#2)]
 [!code-csharp[ADApplicationBase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADApplicationBase/CS/source2.cs#2)]
 [!code-vb[ADApplicationBase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADApplicationBase/VB/source2.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- [Programowanie za pomocą domen aplikacji](application-domains.md#programming-with-application-domains)
- [Używanie domeny aplikacji](../../../docs/framework/app-domains/use.md)
