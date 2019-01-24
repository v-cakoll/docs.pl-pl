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
ms.openlocfilehash: 0c5b43258b3ce501d1302c31a70f51341d3a84d4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54588041"
---
# <a name="retrieving-setup-information-from-an-application-domain"></a><span data-ttu-id="38f38-102">Pobieranie informacji o instalacji z domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="38f38-102">Retrieving Setup Information from an Application Domain</span></span>
<span data-ttu-id="38f38-103">Każde wystąpienie domeny aplikacji składa się z obie te właściwości i <xref:System.AppDomainSetup> informacji.</span><span class="sxs-lookup"><span data-stu-id="38f38-103">Each instance of an application domain consists of both properties and <xref:System.AppDomainSetup> information.</span></span> <span data-ttu-id="38f38-104">Można pobrać informacji o instalacji z domeny aplikacji za pomocą <xref:System.AppDomain?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="38f38-104">You can retrieve setup information from an application domain using the <xref:System.AppDomain?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="38f38-105">Ta klasa udostępnia kilka elementów członkowskich, które pobierają informacje o konfiguracji dotyczące domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="38f38-105">This class provides several members that retrieve configuration information about an application domain.</span></span>  
  
 <span data-ttu-id="38f38-106">Możesz także zbadać **AppDomainSetup** obiektu dla domeny aplikacji, można uzyskać informacji o instalacji, który został przekazany do domeny, podczas jej tworzenia.</span><span class="sxs-lookup"><span data-stu-id="38f38-106">You can also query the **AppDomainSetup** object for the application domain to obtain setup information that was passed to the domain when it was created.</span></span>  
  
 <span data-ttu-id="38f38-107">Poniższy przykład tworzy nową domenę aplikacji, a następnie drukuje kilka wartości elementów członkowskich do konsoli.</span><span class="sxs-lookup"><span data-stu-id="38f38-107">The following example creates a new application domain and then prints several member values to the console.</span></span>  
  
 [!code-cpp[AppDomain_Setup#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source2.cpp#2)]
 [!code-csharp[AppDomain_Setup#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source2.cs#2)]
 [!code-vb[AppDomain_Setup#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source2.vb#2)]  
  
 <span data-ttu-id="38f38-108">Poniższy przykład ustawia i pobiera, informacje o konfiguracji domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="38f38-108">The following example sets, and then retrieves, setup information for an application domain.</span></span> <span data-ttu-id="38f38-109">Należy pamiętać, że `AppDomain.SetupInformation.ApplicationBase` pobiera informacje o konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="38f38-109">Note that `AppDomain.SetupInformation.ApplicationBase` gets the configuration information.</span></span>  
  
 [!code-cpp[AppDomain_Setup#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source3.cpp#3)]
 [!code-csharp[AppDomain_Setup#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source3.cs#3)]
 [!code-vb[AppDomain_Setup#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="38f38-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="38f38-110">See also</span></span>
- [<span data-ttu-id="38f38-111">Programowanie z domenami aplikacji</span><span class="sxs-lookup"><span data-stu-id="38f38-111">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="38f38-112">Używanie domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="38f38-112">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
