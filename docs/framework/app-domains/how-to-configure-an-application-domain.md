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
ms.openlocfilehash: ca28984fa4a328e33d8d9bf79641cc451160f5ea
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119906"
---
# <a name="how-to-configure-an-application-domain"></a>Porady: konfigurowanie domeny aplikacji
Możesz dostarczyć środowisko uruchomieniowe języka wspólnego z informacjami o konfiguracji dla nowej domeny aplikacji przy użyciu <xref:System.AppDomainSetup> klasy. W przypadku tworzenia własnych domen aplikacji najważniejszym właściwość jest <xref:System.AppDomainSetup.ApplicationBase%2A>. Inne właściwości **AppDomainSetup** są używane głównie przez hosty środowiska uruchomieniowego w celu skonfigurowania konkretnej domeny aplikacji.  
  
 Właściwość **ApplicationBase** definiuje katalog główny aplikacji. Gdy środowisko uruchomieniowe musi spełniać żądanie typu, sondy dla zestawu zawierającego typ w katalogu określonym przez właściwość **ApplicationBase** .  
  
> [!NOTE]
> Nowa domena aplikacji dziedziczy tylko właściwość **ApplicationBase** twórcy.  
  
 Poniższy przykład tworzy wystąpienie klasy **AppDomainSetup** , używa tej klasy do tworzenia nowej domeny aplikacji, zapisuje informacje w konsoli, a następnie zwalnia domenę aplikacji.  
  
## <a name="example"></a>Przykład  
 [!code-cpp[ADApplicationBase#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADApplicationBase/CPP/source2.cpp#2)]
 [!code-csharp[ADApplicationBase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADApplicationBase/CS/source2.cs#2)]
 [!code-vb[ADApplicationBase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADApplicationBase/VB/source2.vb#2)]  
  
## <a name="see-also"></a>Zobacz też

- [Programowanie przy użyciu domen aplikacji](application-domains.md#programming-with-application-domains)
- [Używanie domeny aplikacji](use.md)
