---
title: Przestarzałe klasy coclass i interfejsy hostingu środowiska CLR
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 1
- .NET Framework 1.1, hosting interfaces
- hosting interfaces [.NET Framework], version 1
- .NET Framework 1.0, hosting interfaces
ms.assetid: 7b3d2755-cbab-4160-bc69-eb85791e38c7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1f6c20a69894c95086dbd813601ac8811ab4f337
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61985702"
---
# <a name="deprecated-clr-hosting-interfaces-and-coclasses"></a><span data-ttu-id="a7ea2-102">Przestarzałe klasy coclass i interfejsy hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="a7ea2-102">Deprecated CLR Hosting Interfaces and Coclasses</span></span>
<span data-ttu-id="a7ea2-103">W tej sekcji opisano interfejsy, które niezarządzanych hostów można użyć do integracji środowisko uruchomieniowe języka wspólnego (CLR) w wersjach programu .NET Framework 1.0 i 1.1 w swoich aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="a7ea2-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) in the .NET Framework versions 1.0 and 1.1 into their applications.</span></span> <span data-ttu-id="a7ea2-104">Te interfejsy dostarczać metody do hosta skonfigurować i załadowania środowiska uruchomieniowego do procesu.</span><span class="sxs-lookup"><span data-stu-id="a7ea2-104">These interfaces provide methods for a host to configure and load the runtime into a process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a7ea2-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="a7ea2-105">In This Section</span></span>  
 <span data-ttu-id="a7ea2-106">IAppDomainSetup</span><span class="sxs-lookup"><span data-stu-id="a7ea2-106">IAppDomainSetup</span></span>  
 <span data-ttu-id="a7ea2-107">Udostępnia metody dla hosta skonfigurować <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="a7ea2-107">Provides methods for the host to configure an <xref:System.AppDomain>.</span></span>  
  
 [<span data-ttu-id="a7ea2-108">ICeeFileGen, klasa</span><span class="sxs-lookup"><span data-stu-id="a7ea2-108">ICeeFileGen Class</span></span>](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md)  
 <span data-ttu-id="a7ea2-109">(Przestarzałe) Zawiera funkcje do tworzenia natywnych przenośny plik wykonywalny (PE).</span><span class="sxs-lookup"><span data-stu-id="a7ea2-109">(Deprecated) Provides functionality for creating a native portable executable (PE) file.</span></span>  
  
 [<span data-ttu-id="a7ea2-110">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="a7ea2-110">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 <span data-ttu-id="a7ea2-111">Udostępnia metody dla hosta skonfigurować ustawienia środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="a7ea2-111">Provides methods for the host to configure CLR settings.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a7ea2-112">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="a7ea2-112">Related Sections</span></span>  
 [<span data-ttu-id="a7ea2-113">Interfejsy hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="a7ea2-113">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 <span data-ttu-id="a7ea2-114">Zawiera tematy, które opisują hostingu dostarczanych z .NET Framework w wersji 2.0 i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="a7ea2-114">Contains topics that describe the hosting interfaces provided with the .NET Framework version 2.0 and later versions.</span></span>
