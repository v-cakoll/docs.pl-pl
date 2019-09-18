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
ms.openlocfilehash: 06883646982aa6bd642dc4fce7881a289dad5901
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053189"
---
# <a name="how-to-configure-an-application-domain"></a><span data-ttu-id="26464-102">Instrukcje: Konfigurowanie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="26464-102">How to: Configure an Application Domain</span></span>
<span data-ttu-id="26464-103">Możesz dostarczyć środowisko uruchomieniowe języka wspólnego z informacjami o konfiguracji dla nowej domeny aplikacji przy użyciu <xref:System.AppDomainSetup> klasy.</span><span class="sxs-lookup"><span data-stu-id="26464-103">You can provide the common language runtime with configuration information for a new application domain using the <xref:System.AppDomainSetup> class.</span></span> <span data-ttu-id="26464-104">W przypadku tworzenia własnych domen aplikacji najważniejszym właściwość jest <xref:System.AppDomainSetup.ApplicationBase%2A>.</span><span class="sxs-lookup"><span data-stu-id="26464-104">When creating your own application domains, the most important property is <xref:System.AppDomainSetup.ApplicationBase%2A>.</span></span> <span data-ttu-id="26464-105">Inne właściwości **AppDomainSetup** są używane głównie przez hosty środowiska uruchomieniowego w celu skonfigurowania konkretnej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="26464-105">The other **AppDomainSetup** properties are used mainly by runtime hosts to configure a particular application domain.</span></span>  
  
 <span data-ttu-id="26464-106">Właściwość **ApplicationBase** definiuje katalog główny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="26464-106">The **ApplicationBase** property defines the root directory of the application.</span></span> <span data-ttu-id="26464-107">Gdy środowisko uruchomieniowe musi spełniać żądanie typu, sondy dla zestawu zawierającego typ w katalogu określonym przez właściwość **ApplicationBase** .</span><span class="sxs-lookup"><span data-stu-id="26464-107">When the runtime needs to satisfy a type request, it probes for the assembly containing the type in the directory specified by the **ApplicationBase** property.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="26464-108">Nowa domena aplikacji dziedziczy tylko właściwość **ApplicationBase** twórcy.</span><span class="sxs-lookup"><span data-stu-id="26464-108">A new application domain inherits only the **ApplicationBase** property of the creator.</span></span>  
  
 <span data-ttu-id="26464-109">Poniższy przykład tworzy wystąpienie klasy **AppDomainSetup** , używa tej klasy do tworzenia nowej domeny aplikacji, zapisuje informacje w konsoli, a następnie zwalnia domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="26464-109">The following example creates an instance of the **AppDomainSetup** class, uses this class to create a new application domain, writes the information to console, and then unloads the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26464-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="26464-110">Example</span></span>  
 [!code-cpp[ADApplicationBase#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADApplicationBase/CPP/source2.cpp#2)]
 [!code-csharp[ADApplicationBase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADApplicationBase/CS/source2.cs#2)]
 [!code-vb[ADApplicationBase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADApplicationBase/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="26464-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="26464-111">See also</span></span>

- [<span data-ttu-id="26464-112">Programowanie przy użyciu domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="26464-112">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="26464-113">Używanie domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="26464-113">Using Application Domains</span></span>](use.md)
