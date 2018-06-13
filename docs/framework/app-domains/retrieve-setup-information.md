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
# <a name="retrieving-setup-information-from-an-application-domain"></a><span data-ttu-id="ea512-102">Pobieranie informacji o instalacji z domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="ea512-102">Retrieving Setup Information from an Application Domain</span></span>
<span data-ttu-id="ea512-103">Każde wystąpienie domeny aplikacji składa się z obu właściwości i <xref:System.AppDomainSetup> informacji.</span><span class="sxs-lookup"><span data-stu-id="ea512-103">Each instance of an application domain consists of both properties and <xref:System.AppDomainSetup> information.</span></span> <span data-ttu-id="ea512-104">Można pobrać informacji konfiguracyjnych z domeny aplikacji przy użyciu <xref:System.AppDomain?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="ea512-104">You can retrieve setup information from an application domain using the <xref:System.AppDomain?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="ea512-105">Ta klasa udostępnia kilka elementów członkowskich, które służą do pobierania informacji konfiguracyjnych dotyczących domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ea512-105">This class provides several members that retrieve configuration information about an application domain.</span></span>  
  
 <span data-ttu-id="ea512-106">Możesz także zbadać **AppDomainSetup** obiektu uzyskać informacje dotyczące Instalatora, który został przekazany do domeny, podczas tworzenia domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ea512-106">You can also query the **AppDomainSetup** object for the application domain to obtain setup information that was passed to the domain when it was created.</span></span>  
  
 <span data-ttu-id="ea512-107">Poniższy przykład tworzy nową domenę aplikacji i następnie drukuje kilka wartości elementów członkowskich do konsoli.</span><span class="sxs-lookup"><span data-stu-id="ea512-107">The following example creates a new application domain and then prints several member values to the console.</span></span>  
  
 [!code-cpp[AppDomain_Setup#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source2.cpp#2)]
 [!code-csharp[AppDomain_Setup#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source2.cs#2)]
 [!code-vb[AppDomain_Setup#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source2.vb#2)]  
  
 <span data-ttu-id="ea512-108">Następujące przykładowe zestawy, a następnie pobiera, informacje o konfiguracji domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ea512-108">The following example sets, and then retrieves, setup information for an application domain.</span></span> <span data-ttu-id="ea512-109">Należy pamiętać, że `AppDomain.SetupInformation.ApplicationBase` pobiera informacje o konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ea512-109">Note that `AppDomain.SetupInformation.ApplicationBase` gets the configuration information.</span></span>  
  
 [!code-cpp[AppDomain_Setup#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source3.cpp#3)]
 [!code-csharp[AppDomain_Setup#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source3.cs#3)]
 [!code-vb[AppDomain_Setup#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="ea512-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ea512-110">See Also</span></span>  
 [<span data-ttu-id="ea512-111">Programowanie za pomocą domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="ea512-111">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)  
 [<span data-ttu-id="ea512-112">Używanie domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="ea512-112">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
