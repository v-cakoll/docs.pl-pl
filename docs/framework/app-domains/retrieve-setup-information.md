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
ms.openlocfilehash: 4d06a8a3ccfa35af283323478ee44a7da63d896d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119735"
---
# <a name="retrieving-setup-information-from-an-application-domain"></a><span data-ttu-id="8ecc6-102">Pobieranie informacji o instalacji z domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="8ecc6-102">Retrieving Setup Information from an Application Domain</span></span>
<span data-ttu-id="8ecc6-103">Każde wystąpienie domeny aplikacji składa się z właściwości i <xref:System.AppDomainSetup> informacji.</span><span class="sxs-lookup"><span data-stu-id="8ecc6-103">Each instance of an application domain consists of both properties and <xref:System.AppDomainSetup> information.</span></span> <span data-ttu-id="8ecc6-104">Informacje o instalacji z domeny aplikacji można pobrać przy użyciu klasy <xref:System.AppDomain?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8ecc6-104">You can retrieve setup information from an application domain using the <xref:System.AppDomain?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="8ecc6-105">Ta klasa udostępnia kilku członkom, którzy pobierają informacje o konfiguracji domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8ecc6-105">This class provides several members that retrieve configuration information about an application domain.</span></span>  
  
 <span data-ttu-id="8ecc6-106">Można także zbadać obiekt **AppDomainSetup** dla domeny aplikacji, aby uzyskać informacje o konfiguracji, które zostały przesłane do domeny podczas tworzenia.</span><span class="sxs-lookup"><span data-stu-id="8ecc6-106">You can also query the **AppDomainSetup** object for the application domain to obtain setup information that was passed to the domain when it was created.</span></span>  
  
 <span data-ttu-id="8ecc6-107">Poniższy przykład tworzy nową domenę aplikacji, a następnie drukuje kilka wartości elementów członkowskich w konsoli.</span><span class="sxs-lookup"><span data-stu-id="8ecc6-107">The following example creates a new application domain and then prints several member values to the console.</span></span>  
  
 [!code-cpp[AppDomain_Setup#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source2.cpp#2)]
 [!code-csharp[AppDomain_Setup#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source2.cs#2)]
 [!code-vb[AppDomain_Setup#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source2.vb#2)]  
  
 <span data-ttu-id="8ecc6-108">Poniższy przykład ustawia, a następnie pobiera informacje o konfiguracji dla domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8ecc6-108">The following example sets, and then retrieves, setup information for an application domain.</span></span> <span data-ttu-id="8ecc6-109">Należy pamiętać, że `AppDomain.SetupInformation.ApplicationBase` pobiera informacje o konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8ecc6-109">Note that `AppDomain.SetupInformation.ApplicationBase` gets the configuration information.</span></span>  
  
 [!code-cpp[AppDomain_Setup#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source3.cpp#3)]
 [!code-csharp[AppDomain_Setup#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source3.cs#3)]
 [!code-vb[AppDomain_Setup#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="8ecc6-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8ecc6-110">See also</span></span>

- [<span data-ttu-id="8ecc6-111">Programowanie przy użyciu domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="8ecc6-111">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="8ecc6-112">Używanie domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="8ecc6-112">Using Application Domains</span></span>](use.md)
