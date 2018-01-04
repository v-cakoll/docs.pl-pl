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
ms.workload: dotnet
ms.openlocfilehash: 890a8b31339715a4dac8fd2c6e76cc11cda0ee4e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-an-application-domain"></a><span data-ttu-id="1c815-102">Porady: konfigurowanie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="1c815-102">How to: Configure an Application Domain</span></span>
<span data-ttu-id="1c815-103">Środowisko uruchomieniowe języka wspólnego można udostępnić informacje o konfiguracji dla nowej domeny aplikacji, przy użyciu <xref:System.AppDomainSetup> klasy.</span><span class="sxs-lookup"><span data-stu-id="1c815-103">You can provide the common language runtime with configuration information for a new application domain using the <xref:System.AppDomainSetup> class.</span></span> <span data-ttu-id="1c815-104">Podczas tworzenia domeny aplikacji, najważniejsze właściwości to <xref:System.AppDomainSetup.ApplicationBase%2A>.</span><span class="sxs-lookup"><span data-stu-id="1c815-104">When creating your own application domains, the most important property is <xref:System.AppDomainSetup.ApplicationBase%2A>.</span></span> <span data-ttu-id="1c815-105">Druga **AppDomainSetup** właściwości są używane głównie przez hosty w czasie wykonywania, aby skonfigurować domenę określonej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1c815-105">The other **AppDomainSetup** properties are used mainly by runtime hosts to configure a particular application domain.</span></span>  
  
 <span data-ttu-id="1c815-106">**ApplicationBase** właściwość definiuje katalogu głównego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1c815-106">The **ApplicationBase** property defines the root directory of the application.</span></span> <span data-ttu-id="1c815-107">Gdy środowiska uruchomieniowego musi spełnić żądania typu, sondy go do zestawu zawierającego typ w katalogu określonym przez **ApplicationBase** właściwości.</span><span class="sxs-lookup"><span data-stu-id="1c815-107">When the runtime needs to satisfy a type request, it probes for the assembly containing the type in the directory specified by the **ApplicationBase** property.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1c815-108">Nowa domena aplikacji dziedziczy tylko **ApplicationBase** właściwości twórcy.</span><span class="sxs-lookup"><span data-stu-id="1c815-108">A new application domain inherits only the **ApplicationBase** property of the creator.</span></span>  
  
 <span data-ttu-id="1c815-109">Poniższy przykład tworzy wystąpienie **AppDomainSetup** klasy, używa tej klasy w celu utworzenia nowej domeny aplikacji, zapisuje te informacje w konsoli i następnie zwalnia domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1c815-109">The following example creates an instance of the **AppDomainSetup** class, uses this class to create a new application domain, writes the information to console, and then unloads the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c815-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="1c815-110">Example</span></span>  
 [!code-cpp[ADApplicationBase#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADApplicationBase/CPP/source2.cpp#2)]
 [!code-csharp[ADApplicationBase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADApplicationBase/CS/source2.cs#2)]
 [!code-vb[ADApplicationBase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADApplicationBase/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="1c815-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1c815-111">See Also</span></span>  
 [<span data-ttu-id="1c815-112">Programowanie za pomocą domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="1c815-112">Programming with Application Domains</span></span>](http://msdn.microsoft.com/en-us/bd36055b-56bd-43eb-b4d8-820c37172131)  
 [<span data-ttu-id="1c815-113">Używanie domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="1c815-113">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
