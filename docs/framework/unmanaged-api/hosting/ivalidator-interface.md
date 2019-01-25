---
title: IValidator — Interfejs
ms.date: 03/30/2017
api_name:
- IValidator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IValidator
helpviewer_keywords:
- IValidator interface [.NET Framework hosting]
ms.assetid: b297e3b0-20f9-478f-b707-5e2eecb2b5b2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f307ad5689602b030c609a51f6834bdbb0ec4f8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54717718"
---
# <a name="ivalidator-interface"></a><span data-ttu-id="82e49-102">IValidator — Interfejs</span><span class="sxs-lookup"><span data-stu-id="82e49-102">IValidator Interface</span></span>
<span data-ttu-id="82e49-103">Udostępnia metody sprawdzania poprawności przenośnego pliku wykonywalnego obrazów (PE) i raportowanie błędów sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="82e49-103">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="82e49-104">Metody</span><span class="sxs-lookup"><span data-stu-id="82e49-104">Methods</span></span>  
  
|<span data-ttu-id="82e49-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="82e49-105">Method</span></span>|<span data-ttu-id="82e49-106">Opis</span><span class="sxs-lookup"><span data-stu-id="82e49-106">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="82e49-107">Sprawdzanie poprawności</span><span class="sxs-lookup"><span data-stu-id="82e49-107">Validate</span></span>|<span data-ttu-id="82e49-108">Weryfikuje określony plik PE lub Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="82e49-108">Validates the specified PE or Microsoft intermediate language (MSIL) file.</span></span>|  
|<span data-ttu-id="82e49-109">FormatEventInfo</span><span class="sxs-lookup"><span data-stu-id="82e49-109">FormatEventInfo</span></span>|<span data-ttu-id="82e49-110">Pobiera komunikat o błędzie odpowiadający błąd sprawdzania poprawności określonej.</span><span class="sxs-lookup"><span data-stu-id="82e49-110">Gets the error message corresponding to the specified validation error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="82e49-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="82e49-111">Requirements</span></span>  
 <span data-ttu-id="82e49-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82e49-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82e49-113">**Nagłówek:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="82e49-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="82e49-114">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="82e49-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="82e49-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82e49-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82e49-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="82e49-116">See also</span></span>
- [<span data-ttu-id="82e49-117">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="82e49-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="82e49-118">CorRuntimeHost, klasa coclass</span><span class="sxs-lookup"><span data-stu-id="82e49-118">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
