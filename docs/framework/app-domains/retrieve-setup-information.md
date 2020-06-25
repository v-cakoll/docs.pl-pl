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
ms.openlocfilehash: 3b7fdd302ac11caa423815483a4add38264f0910
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325667"
---
# <a name="retrieve-setup-information-from-an-application-domain"></a><span data-ttu-id="db261-103">Pobieranie informacji o instalacji z domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="db261-103">Retrieve setup information from an application domain</span></span>

<span data-ttu-id="db261-104">Każde wystąpienie domeny aplikacji składa się z właściwości i <xref:System.AppDomainSetup> informacji.</span><span class="sxs-lookup"><span data-stu-id="db261-104">Each instance of an application domain consists of both properties and <xref:System.AppDomainSetup> information.</span></span> <span data-ttu-id="db261-105">Informacje o instalacji z domeny aplikacji można pobrać przy użyciu <xref:System.AppDomain?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="db261-105">You can retrieve setup information from an application domain using the <xref:System.AppDomain?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="db261-106">Ta klasa udostępnia kilku członkom, którzy pobierają informacje o konfiguracji domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="db261-106">This class provides several members that retrieve configuration information about an application domain.</span></span>  
  
 <span data-ttu-id="db261-107">Można także zbadać obiekt **AppDomainSetup** dla domeny aplikacji, aby uzyskać informacje o konfiguracji, które zostały przesłane do domeny podczas tworzenia.</span><span class="sxs-lookup"><span data-stu-id="db261-107">You can also query the **AppDomainSetup** object for the application domain to obtain setup information that was passed to the domain when it was created.</span></span>  
  
 <span data-ttu-id="db261-108">Poniższy przykład tworzy nową domenę aplikacji, a następnie drukuje kilka wartości elementów członkowskich w konsoli.</span><span class="sxs-lookup"><span data-stu-id="db261-108">The following example creates a new application domain and then prints several member values to the console.</span></span>  
  
 [!code-cpp[AppDomain_Setup#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source2.cpp#2)]
 [!code-csharp[AppDomain_Setup#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source2.cs#2)]
 [!code-vb[AppDomain_Setup#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source2.vb#2)]  
  
 <span data-ttu-id="db261-109">Poniższy przykład ustawia, a następnie pobiera informacje o konfiguracji dla domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="db261-109">The following example sets, and then retrieves, setup information for an application domain.</span></span> <span data-ttu-id="db261-110">`AppDomain.SetupInformation.ApplicationBase`Pobiera informacje o konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="db261-110">`AppDomain.SetupInformation.ApplicationBase` gets the configuration information.</span></span>  
  
 [!code-cpp[AppDomain_Setup#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source3.cpp#3)]
 [!code-csharp[AppDomain_Setup#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source3.cs#3)]
 [!code-vb[AppDomain_Setup#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="db261-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="db261-111">See also</span></span>

- [<span data-ttu-id="db261-112">Programowanie przy użyciu domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="db261-112">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="db261-113">Używanie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="db261-113">Using Application Domains</span></span>](use.md)
