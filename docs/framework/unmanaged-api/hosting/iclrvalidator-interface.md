---
title: ICLRValidator — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRValidator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRValidator
helpviewer_keywords:
- ICLRValidator interface [.NET Framework hosting]
ms.assetid: 2edd0a10-77fb-4173-91eb-f2970cc364d0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 05287d3674e55a87cfe359fc08f74fa46000d79f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59075850"
---
# <a name="iclrvalidator-interface"></a><span data-ttu-id="cff31-102">ICLRValidator — Interfejs</span><span class="sxs-lookup"><span data-stu-id="cff31-102">ICLRValidator Interface</span></span>
<span data-ttu-id="cff31-103">Udostępnia metody sprawdzania poprawności przenośnego pliku wykonywalnego obrazów (PE) i raportowanie błędów sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="cff31-103">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cff31-104">Metody</span><span class="sxs-lookup"><span data-stu-id="cff31-104">Methods</span></span>  
  
|<span data-ttu-id="cff31-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="cff31-105">Method</span></span>|<span data-ttu-id="cff31-106">Opis</span><span class="sxs-lookup"><span data-stu-id="cff31-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cff31-107">FormatEventInfo, metoda</span><span class="sxs-lookup"><span data-stu-id="cff31-107">FormatEventInfo Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-formateventinfo-method.md)|<span data-ttu-id="cff31-108">Pobiera szczegółowy komunikat o błędzie sprawdzania poprawności określonej.</span><span class="sxs-lookup"><span data-stu-id="cff31-108">Gets a detailed message about the specified validation error.</span></span>|  
|[<span data-ttu-id="cff31-109">Validate, metoda</span><span class="sxs-lookup"><span data-stu-id="cff31-109">Validate Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md)|<span data-ttu-id="cff31-110">Sprawdza poprawność przenośny plik wykonywalny lub języka Microsoft intermediate language (MSIL) w określonym pliku.</span><span class="sxs-lookup"><span data-stu-id="cff31-110">Validates the portable executable or Microsoft intermediate language (MSIL) in the specified file.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cff31-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cff31-111">Requirements</span></span>  
 <span data-ttu-id="cff31-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cff31-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cff31-113">**Nagłówek:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="cff31-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="cff31-114">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cff31-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="cff31-115">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="cff31-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cff31-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cff31-116">See also</span></span>

- [<span data-ttu-id="cff31-117">ICLRErrorReportingManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="cff31-117">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="cff31-118">Hosting — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="cff31-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="cff31-119">CLRRuntimeHost — Klasa coclass</span><span class="sxs-lookup"><span data-stu-id="cff31-119">CLRRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/clrruntimehost-coclass.md)
