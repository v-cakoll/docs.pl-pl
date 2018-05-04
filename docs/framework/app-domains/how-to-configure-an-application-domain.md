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
ms.openlocfilehash: ab5a4c5f06e7b1789b9252820374ab1b0aca75be
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-configure-an-application-domain"></a>Porady: konfigurowanie domeny aplikacji
Środowisko uruchomieniowe języka wspólnego można udostępnić informacje o konfiguracji dla nowej domeny aplikacji, przy użyciu <xref:System.AppDomainSetup> klasy. Podczas tworzenia domeny aplikacji, najważniejsze właściwości to <xref:System.AppDomainSetup.ApplicationBase%2A>. Druga **AppDomainSetup** właściwości są używane głównie przez hosty w czasie wykonywania, aby skonfigurować domenę określonej aplikacji.  
  
 **ApplicationBase** właściwość definiuje katalogu głównego aplikacji. Gdy środowiska uruchomieniowego musi spełnić żądania typu, sondy go do zestawu zawierającego typ w katalogu określonym przez **ApplicationBase** właściwości.  
  
> [!NOTE]
>  Nowa domena aplikacji dziedziczy tylko **ApplicationBase** właściwości twórcy.  
  
 Poniższy przykład tworzy wystąpienie **AppDomainSetup** klasy, używa tej klasy w celu utworzenia nowej domeny aplikacji, zapisuje te informacje w konsoli i następnie zwalnia domeny aplikacji.  
  
## <a name="example"></a>Przykład  
 [!code-cpp[ADApplicationBase#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADApplicationBase/CPP/source2.cpp#2)]
 [!code-csharp[ADApplicationBase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADApplicationBase/CS/source2.cs#2)]
 [!code-vb[ADApplicationBase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADApplicationBase/VB/source2.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie za pomocą domeny aplikacji](application-domains.md#programming-with-application-domains)  
 [Używanie domen aplikacji](../../../docs/framework/app-domains/use.md)
