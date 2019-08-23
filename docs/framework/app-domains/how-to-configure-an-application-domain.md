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
ms.openlocfilehash: bb7223d2356ebec54ddd64dee514f1c8785e2d17
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921570"
---
# <a name="how-to-configure-an-application-domain"></a>Instrukcje: Konfigurowanie domeny aplikacji
Możesz dostarczyć środowisko uruchomieniowe języka wspólnego z informacjami o konfiguracji dla nowej domeny aplikacji przy użyciu <xref:System.AppDomainSetup> klasy. W przypadku tworzenia własnych domen aplikacji najważniejszym właściwość jest <xref:System.AppDomainSetup.ApplicationBase%2A>. Inne właściwości **AppDomainSetup** są używane głównie przez hosty środowiska uruchomieniowego w celu skonfigurowania konkretnej domeny aplikacji.  
  
 Właściwość **ApplicationBase** definiuje katalog główny aplikacji. Gdy środowisko uruchomieniowe musi spełniać żądanie typu, sondy dla zestawu zawierającego typ w katalogu określonym przez właściwość **ApplicationBase** .  
  
> [!NOTE]
> Nowa domena aplikacji dziedziczy tylko właściwość **ApplicationBase** twórcy.  
  
 Poniższy przykład tworzy wystąpienie klasy **AppDomainSetup** , używa tej klasy do tworzenia nowej domeny aplikacji, zapisuje informacje w konsoli, a następnie zwalnia domenę aplikacji.  
  
## <a name="example"></a>Przykład  
 [!code-cpp[ADApplicationBase#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADApplicationBase/CPP/source2.cpp#2)]
 [!code-csharp[ADApplicationBase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADApplicationBase/CS/source2.cs#2)]
 [!code-vb[ADApplicationBase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADApplicationBase/VB/source2.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- [Programowanie przy użyciu domen aplikacji](application-domains.md#programming-with-application-domains)
- [Używanie domen aplikacji](../../../docs/framework/app-domains/use.md)
