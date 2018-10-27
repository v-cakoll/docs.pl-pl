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
ms.openlocfilehash: 0d9341b90f876306ff2e964141c2c729d1cf0e5f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50193830"
---
# <a name="retrieving-setup-information-from-an-application-domain"></a><span data-ttu-id="a110d-102">Pobieranie informacji o instalacji z domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="a110d-102">Retrieving Setup Information from an Application Domain</span></span>
<span data-ttu-id="a110d-103">Każde wystąpienie domeny aplikacji składa się z obie te właściwości i <xref:System.AppDomainSetup> informacji.</span><span class="sxs-lookup"><span data-stu-id="a110d-103">Each instance of an application domain consists of both properties and <xref:System.AppDomainSetup> information.</span></span> <span data-ttu-id="a110d-104">Można pobrać informacji o instalacji z domeny aplikacji za pomocą <xref:System.AppDomain?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="a110d-104">You can retrieve setup information from an application domain using the <xref:System.AppDomain?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="a110d-105">Ta klasa udostępnia kilka elementów członkowskich, które pobierają informacje o konfiguracji dotyczące domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a110d-105">This class provides several members that retrieve configuration information about an application domain.</span></span>  
  
 <span data-ttu-id="a110d-106">Możesz także zbadać **AppDomainSetup** obiektu dla domeny aplikacji, można uzyskać informacji o instalacji, który został przekazany do domeny, podczas jej tworzenia.</span><span class="sxs-lookup"><span data-stu-id="a110d-106">You can also query the **AppDomainSetup** object for the application domain to obtain setup information that was passed to the domain when it was created.</span></span>  
  
 <span data-ttu-id="a110d-107">Poniższy przykład tworzy nową domenę aplikacji, a następnie drukuje kilka wartości elementów członkowskich do konsoli.</span><span class="sxs-lookup"><span data-stu-id="a110d-107">The following example creates a new application domain and then prints several member values to the console.</span></span>  
  
 [!code-cpp[AppDomain_Setup#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source2.cpp#2)]
 [!code-csharp[AppDomain_Setup#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source2.cs#2)]
 [!code-vb[AppDomain_Setup#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source2.vb#2)]  
  
 <span data-ttu-id="a110d-108">Poniższy przykład ustawia i pobiera, informacje o konfiguracji domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a110d-108">The following example sets, and then retrieves, setup information for an application domain.</span></span> <span data-ttu-id="a110d-109">Należy pamiętać, że `AppDomain.SetupInformation.ApplicationBase` pobiera informacje o konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a110d-109">Note that `AppDomain.SetupInformation.ApplicationBase` gets the configuration information.</span></span>  
  
 [!code-cpp[AppDomain_Setup#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source3.cpp#3)]
 [!code-csharp[AppDomain_Setup#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source3.cs#3)]
 [!code-vb[AppDomain_Setup#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="a110d-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a110d-110">See Also</span></span>  
- [<span data-ttu-id="a110d-111">Programowanie z domenami aplikacji</span><span class="sxs-lookup"><span data-stu-id="a110d-111">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)  
- [<span data-ttu-id="a110d-112">Używanie domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="a110d-112">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
