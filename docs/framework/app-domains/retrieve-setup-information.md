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
ms.openlocfilehash: 80c9fe6de0fca86497ffe84cd8dadf0eb8cef6c5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59108956"
---
# <a name="retrieving-setup-information-from-an-application-domain"></a>Pobieranie informacji o instalacji z domeny aplikacji
Każde wystąpienie domeny aplikacji składa się z obie te właściwości i <xref:System.AppDomainSetup> informacji. Można pobrać informacji o instalacji z domeny aplikacji za pomocą <xref:System.AppDomain?displayProperty=nameWithType> klasy. Ta klasa udostępnia kilka elementów członkowskich, które pobierają informacje o konfiguracji dotyczące domeny aplikacji.  
  
 Możesz także zbadać **AppDomainSetup** obiektu dla domeny aplikacji, można uzyskać informacji o instalacji, który został przekazany do domeny, podczas jej tworzenia.  
  
 Poniższy przykład tworzy nową domenę aplikacji, a następnie drukuje kilka wartości elementów członkowskich do konsoli.  
  
 [!code-cpp[AppDomain_Setup#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source2.cpp#2)]
 [!code-csharp[AppDomain_Setup#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source2.cs#2)]
 [!code-vb[AppDomain_Setup#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source2.vb#2)]  
  
 Poniższy przykład ustawia i pobiera, informacje o konfiguracji domeny aplikacji. Należy pamiętać, że `AppDomain.SetupInformation.ApplicationBase` pobiera informacje o konfiguracji.  
  
 [!code-cpp[AppDomain_Setup#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source3.cpp#3)]
 [!code-csharp[AppDomain_Setup#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source3.cs#3)]
 [!code-vb[AppDomain_Setup#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source3.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- [Programowanie z domenami aplikacji](application-domains.md#programming-with-application-domains)
- [Używanie domen aplikacji](../../../docs/framework/app-domains/use.md)
