---
title: "Wdrażanie aplikacji WCF za pomocą technologii ClickOnce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a11feee-2a47-4d3e-a28a-ad69d5ff93e0
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0e87e01c39c5f50ff3f4d4e9479a68e19cceb90f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="deploying-wcf-applications-with-clickonce"></a><span data-ttu-id="edf8d-102">Wdrażanie aplikacji WCF za pomocą technologii ClickOnce</span><span class="sxs-lookup"><span data-stu-id="edf8d-102">Deploying WCF Applications with ClickOnce</span></span>
<span data-ttu-id="edf8d-103">Aplikacje klienckie przy użyciu [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] można wdrożyć przy użyciu technologii ClickOnce.</span><span class="sxs-lookup"><span data-stu-id="edf8d-103">Client applications using [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] may be deployed using ClickOnce technology.</span></span> <span data-ttu-id="edf8d-104">Ta technologia umożliwia im to wykorzystać środowiska uruchomieniowego ochrony zabezpieczeń dostarczone przez zabezpieczenia dostępu kodu, pod warunkiem, że są podpisane cyfrowo przy użyciu zaufanego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="edf8d-104">This technology allows them to take advantage of the runtime security protections provided by Code Access Security, provided that they are digitally signed with a trusted certificate.</span></span> <span data-ttu-id="edf8d-105">Certyfikat używany do podpisywania aplikacji ClickOnce musi znajdować się w magazynie zaufanego wydawcy i zasady zabezpieczeń lokalnych na komputerze klienckim należy skonfigurować tak, aby udzielić uprawnień pełne zaufanie do wydawcy certyfikat podpisywania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="edf8d-105">The certificate used to sign the ClickOnce application must reside in the Trusted Publisher store, and the local security policy on the client machine must be configured to grant Full Trust permissions to applications signed with the publisher's certificate.</span></span>  
  
 <span data-ttu-id="edf8d-106">Aby uzyskać informacje na temat konfigurowania aplikacji ClickOnce i zaufanych wydawców, zobacz [Konfigurowanie zaufanych wydawców ClickOnce](http://go.microsoft.com/fwlink/?LinkId=94774).</span><span class="sxs-lookup"><span data-stu-id="edf8d-106">For information on configuring ClickOnce applications and trusted publishers, see [Configuring ClickOnce Trusted Publishers](http://go.microsoft.com/fwlink/?LinkId=94774).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edf8d-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="edf8d-107">See Also</span></span>  
 [<span data-ttu-id="edf8d-108">Przegląd wdrażania zaufanych aplikacji</span><span class="sxs-lookup"><span data-stu-id="edf8d-108">Trusted Application Deployment Overview</span></span>](http://go.microsoft.com/fwlink/?LinkId=94775)  
 [<span data-ttu-id="edf8d-109">Wdrożenie ClickOnce dla systemu Windows formularzy aplikacji</span><span class="sxs-lookup"><span data-stu-id="edf8d-109">ClickOnce Deployment for Windows Forms Applications</span></span>](http://go.microsoft.com/fwlink/?LinkId=94776)
