---
title: Wdrażanie aplikacji WCF za pomocą technologii ClickOnce
ms.date: 03/30/2017
ms.assetid: 1a11feee-2a47-4d3e-a28a-ad69d5ff93e0
ms.openlocfilehash: b520931751bbba00d440b46657962ad3f1e41cd3
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802236"
---
# <a name="deploying-wcf-applications-with-clickonce"></a><span data-ttu-id="6deea-102">Wdrażanie aplikacji WCF za pomocą technologii ClickOnce</span><span class="sxs-lookup"><span data-stu-id="6deea-102">Deploying WCF Applications with ClickOnce</span></span>
<span data-ttu-id="6deea-103">Aplikacje klienckie korzystające z Windows Communication Foundation (WCF) można wdrożyć przy użyciu technologii ClickOnce.</span><span class="sxs-lookup"><span data-stu-id="6deea-103">Client applications using Windows Communication Foundation (WCF) may be deployed using ClickOnce technology.</span></span> <span data-ttu-id="6deea-104">Ta technologia pozwala im wykorzystać ochronę zabezpieczeń środowiska uruchomieniowego zapewnianą przez zabezpieczenia dostępu kodu, pod warunkiem, że są podpisane cyfrowo za pomocą zaufanego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="6deea-104">This technology allows them to take advantage of the runtime security protections provided by Code Access Security, provided that they are digitally signed with a trusted certificate.</span></span> <span data-ttu-id="6deea-105">Certyfikat używany do podpisywania aplikacji ClickOnce musi znajdować się w magazynie zaufanych wydawców, a zasady zabezpieczeń lokalnych na komputerze klienckim muszą być skonfigurowane tak, aby przyznać pełne uprawnienia zaufania do aplikacji podpisanych za pomocą certyfikatu wydawcy.</span><span class="sxs-lookup"><span data-stu-id="6deea-105">The certificate used to sign the ClickOnce application must reside in the Trusted Publisher store, and the local security policy on the client machine must be configured to grant Full Trust permissions to applications signed with the publisher's certificate.</span></span>  
  
 <span data-ttu-id="6deea-106">Aby uzyskać informacje na temat konfigurowania aplikacji ClickOnce i zaufanych wydawców, zobacz [Konfigurowanie zaufanych wydawców ClickOnce](https://docs.microsoft.com/previous-versions/dotnet/articles/ms996418(v=msdn.10)).</span><span class="sxs-lookup"><span data-stu-id="6deea-106">For information on configuring ClickOnce applications and trusted publishers, see [Configuring ClickOnce Trusted Publishers](https://docs.microsoft.com/previous-versions/dotnet/articles/ms996418(v=msdn.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6deea-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6deea-107">See also</span></span>

- [<span data-ttu-id="6deea-108">Przegląd wdrażania zaufanych aplikacji</span><span class="sxs-lookup"><span data-stu-id="6deea-108">Trusted Application Deployment Overview</span></span>](/visualstudio/deployment/trusted-application-deployment-overview)
- <span data-ttu-id="6deea-109">[Wdrożenie ClickOnce dla aplikacji Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/wh45kb66(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="6deea-109">[ClickOnce Deployment for Windows Forms Applications](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/wh45kb66(v=vs.90))</span></span>
