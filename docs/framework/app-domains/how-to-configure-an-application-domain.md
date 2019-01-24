---
title: 'Instrukcje: Konfigurowanie domeny aplikacji'
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
ms.openlocfilehash: 8989d7695f44b0cd2e8b0ce3ec8bd74a6e802102
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54534569"
---
# <a name="how-to-configure-an-application-domain"></a><span data-ttu-id="22fbd-102">Instrukcje: Konfigurowanie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="22fbd-102">How to: Configure an Application Domain</span></span>
<span data-ttu-id="22fbd-103">Środowisko uruchomieniowe języka wspólnego może udostępniać informacje o konfiguracji dla nowej domeny aplikacji, za pomocą <xref:System.AppDomainSetup> klasy.</span><span class="sxs-lookup"><span data-stu-id="22fbd-103">You can provide the common language runtime with configuration information for a new application domain using the <xref:System.AppDomainSetup> class.</span></span> <span data-ttu-id="22fbd-104">Podczas tworzenia domen aplikacji, najważniejsze właściwości to <xref:System.AppDomainSetup.ApplicationBase%2A>.</span><span class="sxs-lookup"><span data-stu-id="22fbd-104">When creating your own application domains, the most important property is <xref:System.AppDomainSetup.ApplicationBase%2A>.</span></span> <span data-ttu-id="22fbd-105">Druga **AppDomainSetup** właściwości są używane głównie przez hosty środowiska uruchomieniowego, aby skonfigurować domeny określonej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="22fbd-105">The other **AppDomainSetup** properties are used mainly by runtime hosts to configure a particular application domain.</span></span>  
  
 <span data-ttu-id="22fbd-106">**ApplicationBase** właściwość definiuje katalogu głównego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="22fbd-106">The **ApplicationBase** property defines the root directory of the application.</span></span> <span data-ttu-id="22fbd-107">Gdy środowisko wykonawcze musi spełnić żądanie typu, sondy jej zestawu zawierającego typ w katalogu określonym przez **ApplicationBase** właściwości.</span><span class="sxs-lookup"><span data-stu-id="22fbd-107">When the runtime needs to satisfy a type request, it probes for the assembly containing the type in the directory specified by the **ApplicationBase** property.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="22fbd-108">Nowa domena aplikacji dziedziczy tylko **ApplicationBase** właściwość twórcy.</span><span class="sxs-lookup"><span data-stu-id="22fbd-108">A new application domain inherits only the **ApplicationBase** property of the creator.</span></span>  
  
 <span data-ttu-id="22fbd-109">Poniższy przykład tworzy wystąpienie **AppDomainSetup** klasa, używa tej klasy w celu utworzenia nowej domeny aplikacji, zapisuje te informacje w konsoli i następnie zwalnia domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="22fbd-109">The following example creates an instance of the **AppDomainSetup** class, uses this class to create a new application domain, writes the information to console, and then unloads the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22fbd-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="22fbd-110">Example</span></span>  
 [!code-cpp[ADApplicationBase#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADApplicationBase/CPP/source2.cpp#2)]
 [!code-csharp[ADApplicationBase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADApplicationBase/CS/source2.cs#2)]
 [!code-vb[ADApplicationBase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADApplicationBase/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="22fbd-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="22fbd-111">See also</span></span>
- [<span data-ttu-id="22fbd-112">Programowanie z domenami aplikacji</span><span class="sxs-lookup"><span data-stu-id="22fbd-112">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="22fbd-113">Używanie domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="22fbd-113">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
