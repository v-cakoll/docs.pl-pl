---
title: Pobieranie informacji o instalacji z domeny aplikacji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- AppDomainSetup object
- retrieving setup information
- application domains, retrieving setup information
ms.assetid: 5cdb12ae-1e37-4a62-8ec7-93d6dcc6e8d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6fab54080a529a9b5a93c06a4f249a9c14ecd7af
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743891"
---
# <a name="retrieving-setup-information-from-an-application-domain"></a>Pobieranie informacji o instalacji z domeny aplikacji
Każde wystąpienie domeny aplikacji składa się z obu właściwości i <xref:System.AppDomainSetup> informacji. Można pobrać informacji konfiguracyjnych z domeny aplikacji przy użyciu <xref:System.AppDomain?displayProperty=nameWithType> klasy. Ta klasa udostępnia kilka elementów członkowskich, które służą do pobierania informacji konfiguracyjnych dotyczących domeny aplikacji.  
  
 Możesz także zbadać **AppDomainSetup** obiektu uzyskać informacje dotyczące Instalatora, który został przekazany do domeny, podczas tworzenia domeny aplikacji.  
  
 Poniższy przykład tworzy nową domenę aplikacji i następnie drukuje kilka wartości elementów członkowskich do konsoli.  
  
 [!code-cpp[AppDomain_Setup#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source2.cpp#2)]
 [!code-csharp[AppDomain_Setup#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source2.cs#2)]
 [!code-vb[AppDomain_Setup#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source2.vb#2)]  
  
 Następujące przykładowe zestawy, a następnie pobiera, informacje o konfiguracji domeny aplikacji. Należy pamiętać, że `AppDomain.SetupInformation.ApplicationBase` pobiera informacje o konfiguracji.  
  
 [!code-cpp[AppDomain_Setup#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source3.cpp#3)]
 [!code-csharp[AppDomain_Setup#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source3.cs#3)]
 [!code-vb[AppDomain_Setup#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source3.vb#3)]  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie za pomocą domeny aplikacji](application-domains.md#programming-with-application-domains)  
 [Używanie domen aplikacji](../../../docs/framework/app-domains/use.md)
