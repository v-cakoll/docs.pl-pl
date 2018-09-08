---
title: Wdrażanie aplikacji WCF za pomocą technologii ClickOnce
ms.date: 03/30/2017
ms.assetid: 1a11feee-2a47-4d3e-a28a-ad69d5ff93e0
ms.openlocfilehash: d733c6f523393737418c6394707c1d4e6e9c1710
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44222217"
---
# <a name="deploying-wcf-applications-with-clickonce"></a><span data-ttu-id="e01c9-102">Wdrażanie aplikacji WCF za pomocą technologii ClickOnce</span><span class="sxs-lookup"><span data-stu-id="e01c9-102">Deploying WCF Applications with ClickOnce</span></span>
<span data-ttu-id="e01c9-103">Można wdrażać aplikacji klienckich za pomocą usługi Windows Communication Foundation (WCF) przy użyciu technologii ClickOnce.</span><span class="sxs-lookup"><span data-stu-id="e01c9-103">Client applications using Windows Communication Foundation (WCF) may be deployed using ClickOnce technology.</span></span> <span data-ttu-id="e01c9-104">Ta technologia umożliwia korzystanie z zalet środowiska uruchomieniowego zabezpieczenia udostępniane przez zabezpieczeń dostępu kodu, pod warunkiem, że są podpisane cyfrowo za pomocą zaufanego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="e01c9-104">This technology allows them to take advantage of the runtime security protections provided by Code Access Security, provided that they are digitally signed with a trusted certificate.</span></span> <span data-ttu-id="e01c9-105">Certyfikat użyty do podpisania aplikacji ClickOnce musi znajdować się w magazynie zaufanego wydawcy, a zasady zabezpieczeń lokalnych na komputerze klienckim musi być skonfigurowany tak, aby udzielić uprawnień pełnego zaufania aplikacjom podpisanym za pomocą certyfikatu wydawcy.</span><span class="sxs-lookup"><span data-stu-id="e01c9-105">The certificate used to sign the ClickOnce application must reside in the Trusted Publisher store, and the local security policy on the client machine must be configured to grant Full Trust permissions to applications signed with the publisher's certificate.</span></span>  
  
 <span data-ttu-id="e01c9-106">Aby uzyskać informacje na temat konfigurowania aplikacji ClickOnce i zaufanych wydawców, zobacz [Konfigurowanie zaufanych wydawców ClickOnce](https://go.microsoft.com/fwlink/?LinkId=94774).</span><span class="sxs-lookup"><span data-stu-id="e01c9-106">For information on configuring ClickOnce applications and trusted publishers, see [Configuring ClickOnce Trusted Publishers](https://go.microsoft.com/fwlink/?LinkId=94774).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e01c9-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e01c9-107">See Also</span></span>  
 [<span data-ttu-id="e01c9-108">Przegląd wdrażania zaufanych aplikacji</span><span class="sxs-lookup"><span data-stu-id="e01c9-108">Trusted Application Deployment Overview</span></span>](https://go.microsoft.com/fwlink/?LinkId=94775)  
 [<span data-ttu-id="e01c9-109">Wdrożenie rozwiązania ClickOnce dla Windows Forms aplikacji</span><span class="sxs-lookup"><span data-stu-id="e01c9-109">ClickOnce Deployment for Windows Forms Applications</span></span>](https://go.microsoft.com/fwlink/?LinkId=94776)
