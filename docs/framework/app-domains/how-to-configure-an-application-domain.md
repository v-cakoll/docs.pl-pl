---
title: 'Porady: konfigurowanie domeny aplikacji'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, configuring
- ApplicationBase property
ms.assetid: 07ea8438-7a34-49f0-a7e8-3d6ff7e4a482
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 79a05be9b3ddb9ca8aaabe13165efc5d851125a5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 [Programowanie za pomocą domeny aplikacji](http://msdn.microsoft.com/en-us/bd36055b-56bd-43eb-b4d8-820c37172131)  
 [Używanie domeny aplikacji](../../../docs/framework/app-domains/use.md)
