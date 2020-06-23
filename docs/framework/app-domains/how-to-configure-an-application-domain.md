---
title: 'Instrukcje: Konfigurowanie domeny aplikacji'
description: Skonfiguruj domenę aplikacji w programie .NET. Środowisko CLR z informacjami o konfiguracji dla nowej domeny aplikacji można dostarczyć przy użyciu klasy AppDomainSetup.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, configuring
- ApplicationBase property
ms.assetid: 07ea8438-7a34-49f0-a7e8-3d6ff7e4a482
ms.openlocfilehash: 27afcf161bec74143fafb5dceb20597de73e23d4
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104859"
---
# <a name="how-to-configure-an-application-domain"></a>Instrukcje: Konfigurowanie domeny aplikacji
Możesz dostarczyć środowisko uruchomieniowe języka wspólnego z informacjami o konfiguracji dla nowej domeny aplikacji przy użyciu <xref:System.AppDomainSetup> klasy. W przypadku tworzenia własnych domen aplikacji najważniejszym właściwość jest <xref:System.AppDomainSetup.ApplicationBase%2A> . Inne właściwości **AppDomainSetup** są używane głównie przez hosty środowiska uruchomieniowego w celu skonfigurowania konkretnej domeny aplikacji.  
  
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
