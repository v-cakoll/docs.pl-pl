---
title: Pobieranie informacji o instalacji z domeny aplikacji
description: Pobierz informacje o instalacji z domeny aplikacji w programie .NET przy użyciu klasy System. AppDomain lub obiektu AppDomainSetup.
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
ms.openlocfilehash: 06bf6b5901736b87852492f48a9d8972490b8304
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903470"
---
# <a name="retrieving-setup-information-from-an-application-domain"></a>Pobieranie informacji o instalacji z domeny aplikacji
Każde wystąpienie domeny aplikacji składa się z właściwości i <xref:System.AppDomainSetup> informacji. Informacje o instalacji z domeny aplikacji można pobrać przy użyciu <xref:System.AppDomain?displayProperty=nameWithType> klasy. Ta klasa udostępnia kilku członkom, którzy pobierają informacje o konfiguracji domeny aplikacji.  
  
 Można także zbadać obiekt **AppDomainSetup** dla domeny aplikacji, aby uzyskać informacje o konfiguracji, które zostały przesłane do domeny podczas tworzenia.  
  
 Poniższy przykład tworzy nową domenę aplikacji, a następnie drukuje kilka wartości elementów członkowskich w konsoli.  
  
 [!code-cpp[AppDomain_Setup#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source2.cpp#2)]
 [!code-csharp[AppDomain_Setup#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source2.cs#2)]
 [!code-vb[AppDomain_Setup#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source2.vb#2)]  
  
 Poniższy przykład ustawia, a następnie pobiera informacje o konfiguracji dla domeny aplikacji. Należy pamiętać, że `AppDomain.SetupInformation.ApplicationBase` Pobiera informacje o konfiguracji.  
  
 [!code-cpp[AppDomain_Setup#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source3.cpp#3)]
 [!code-csharp[AppDomain_Setup#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source3.cs#3)]
 [!code-vb[AppDomain_Setup#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source3.vb#3)]  
  
## <a name="see-also"></a>Zobacz też

- [Programowanie przy użyciu domen aplikacji](application-domains.md#programming-with-application-domains)
- [Używanie domeny aplikacji](use.md)
