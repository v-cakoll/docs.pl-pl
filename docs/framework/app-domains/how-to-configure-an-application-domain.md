---
title: 'Porady: konfigurowanie domeny aplikacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, configuring
- ApplicationBase property
ms.assetid: 07ea8438-7a34-49f0-a7e8-3d6ff7e4a482
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ab5a4c5f06e7b1789b9252820374ab1b0aca75be
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743410"
---
# <a name="how-to-configure-an-application-domain"></a><span data-ttu-id="aaf35-102">Porady: konfigurowanie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="aaf35-102">How to: Configure an Application Domain</span></span>
<span data-ttu-id="aaf35-103">Środowisko uruchomieniowe języka wspólnego można udostępnić informacje o konfiguracji dla nowej domeny aplikacji, przy użyciu <xref:System.AppDomainSetup> klasy.</span><span class="sxs-lookup"><span data-stu-id="aaf35-103">You can provide the common language runtime with configuration information for a new application domain using the <xref:System.AppDomainSetup> class.</span></span> <span data-ttu-id="aaf35-104">Podczas tworzenia domeny aplikacji, najważniejsze właściwości to <xref:System.AppDomainSetup.ApplicationBase%2A>.</span><span class="sxs-lookup"><span data-stu-id="aaf35-104">When creating your own application domains, the most important property is <xref:System.AppDomainSetup.ApplicationBase%2A>.</span></span> <span data-ttu-id="aaf35-105">Druga **AppDomainSetup** właściwości są używane głównie przez hosty w czasie wykonywania, aby skonfigurować domenę określonej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aaf35-105">The other **AppDomainSetup** properties are used mainly by runtime hosts to configure a particular application domain.</span></span>  
  
 <span data-ttu-id="aaf35-106">**ApplicationBase** właściwość definiuje katalogu głównego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aaf35-106">The **ApplicationBase** property defines the root directory of the application.</span></span> <span data-ttu-id="aaf35-107">Gdy środowiska uruchomieniowego musi spełnić żądania typu, sondy go do zestawu zawierającego typ w katalogu określonym przez **ApplicationBase** właściwości.</span><span class="sxs-lookup"><span data-stu-id="aaf35-107">When the runtime needs to satisfy a type request, it probes for the assembly containing the type in the directory specified by the **ApplicationBase** property.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aaf35-108">Nowa domena aplikacji dziedziczy tylko **ApplicationBase** właściwości twórcy.</span><span class="sxs-lookup"><span data-stu-id="aaf35-108">A new application domain inherits only the **ApplicationBase** property of the creator.</span></span>  
  
 <span data-ttu-id="aaf35-109">Poniższy przykład tworzy wystąpienie **AppDomainSetup** klasy, używa tej klasy w celu utworzenia nowej domeny aplikacji, zapisuje te informacje w konsoli i następnie zwalnia domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aaf35-109">The following example creates an instance of the **AppDomainSetup** class, uses this class to create a new application domain, writes the information to console, and then unloads the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aaf35-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="aaf35-110">Example</span></span>  
 [!code-cpp[ADApplicationBase#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADApplicationBase/CPP/source2.cpp#2)]
 [!code-csharp[ADApplicationBase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADApplicationBase/CS/source2.cs#2)]
 [!code-vb[ADApplicationBase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADApplicationBase/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="aaf35-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aaf35-111">See Also</span></span>  
 [<span data-ttu-id="aaf35-112">Programowanie za pomocą domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="aaf35-112">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)  
 [<span data-ttu-id="aaf35-113">Używanie domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="aaf35-113">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
