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
ms.openlocfilehash: 6f34a9aac31fe50974a6f88416d0a00cd72aca8e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54511933"
---
# <a name="iclrvalidator-interface"></a><span data-ttu-id="2d51c-102">ICLRValidator — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2d51c-102">ICLRValidator Interface</span></span>
<span data-ttu-id="2d51c-103">Udostępnia metody sprawdzania poprawności przenośnego pliku wykonywalnego obrazów (PE) i raportowanie błędów sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="2d51c-103">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2d51c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2d51c-104">Methods</span></span>  
  
|<span data-ttu-id="2d51c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2d51c-105">Method</span></span>|<span data-ttu-id="2d51c-106">Opis</span><span class="sxs-lookup"><span data-stu-id="2d51c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2d51c-107">FormatEventInfo, metoda</span><span class="sxs-lookup"><span data-stu-id="2d51c-107">FormatEventInfo Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-formateventinfo-method.md)|<span data-ttu-id="2d51c-108">Pobiera szczegółowy komunikat o błędzie sprawdzania poprawności określonej.</span><span class="sxs-lookup"><span data-stu-id="2d51c-108">Gets a detailed message about the specified validation error.</span></span>|  
|[<span data-ttu-id="2d51c-109">Validate, metoda</span><span class="sxs-lookup"><span data-stu-id="2d51c-109">Validate Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md)|<span data-ttu-id="2d51c-110">Sprawdza poprawność przenośny plik wykonywalny lub języka Microsoft intermediate language (MSIL) w określonym pliku.</span><span class="sxs-lookup"><span data-stu-id="2d51c-110">Validates the portable executable or Microsoft intermediate language (MSIL) in the specified file.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2d51c-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2d51c-111">Requirements</span></span>  
 <span data-ttu-id="2d51c-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d51c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d51c-113">**Nagłówek:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="2d51c-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="2d51c-114">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2d51c-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2d51c-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d51c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d51c-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2d51c-116">See also</span></span>
- [<span data-ttu-id="2d51c-117">ICLRErrorReportingManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="2d51c-117">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="2d51c-118">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="2d51c-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="2d51c-119">CLRRuntimeHost, klasa coclass</span><span class="sxs-lookup"><span data-stu-id="2d51c-119">CLRRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/clrruntimehost-coclass.md)
