---
title: CLRRuntimeHost — Klasa coclass
ms.date: 03/30/2017
api_name:
- CLRRuntimeHost Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CLRRuntimeHost
helpviewer_keywords:
- CLRRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 2ac9cbf5-8a2d-4e4f-8831-0dad8ef0a897
topic_type:
- apiref
ms.openlocfilehash: 40766ce5837053493f2e3f1f25fe7d1d63ec695f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616805"
---
# <a name="clrruntimehost-coclass"></a><span data-ttu-id="d7014-102">CLRRuntimeHost — Klasa coclass</span><span class="sxs-lookup"><span data-stu-id="d7014-102">CLRRuntimeHost Coclass</span></span>
<span data-ttu-id="d7014-103">Udostępnia interfejsy umożliwiające zarządzanie wykonywaniem kodu przez środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="d7014-103">Provides interfaces for managing code execution by the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7014-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d7014-104">Syntax</span></span>  
  
```cpp  
coclass CLRRuntimeHost {  
    [default] interface  ICLRRuntimeHost;  
    interface            ICLRValidator;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="d7014-105">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="d7014-105">Interfaces</span></span>  
  
|<span data-ttu-id="d7014-106">Interfejs</span><span class="sxs-lookup"><span data-stu-id="d7014-106">Interface</span></span>|<span data-ttu-id="d7014-107">Opis</span><span class="sxs-lookup"><span data-stu-id="d7014-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="d7014-108">ICLRRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="d7014-108">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)|<span data-ttu-id="d7014-109">Zapewnia metody kontrolowania wykonywania aplikacji przez środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="d7014-109">Provides methods for controlling the execution of applications by the runtime.</span></span>|  
|[<span data-ttu-id="d7014-110">ICLRValidator, interfejs</span><span class="sxs-lookup"><span data-stu-id="d7014-110">ICLRValidator Interface</span></span>](iclrvalidator-interface.md)|<span data-ttu-id="d7014-111">Zapewnia metody weryfikacji przenośnych obrazów wykonywalnych i szczegółowe raportowanie błędów walidacji.</span><span class="sxs-lookup"><span data-stu-id="d7014-111">Provides methods for validation of portable executable images and for detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d7014-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d7014-112">Requirements</span></span>  
 <span data-ttu-id="d7014-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7014-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7014-114">**Nagłówek:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="d7014-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="d7014-115">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d7014-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d7014-116">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7014-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7014-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d7014-117">See also</span></span>

- [<span data-ttu-id="d7014-118">Współklasy hostingu</span><span class="sxs-lookup"><span data-stu-id="d7014-118">Hosting Coclasses</span></span>](hosting-coclasses.md)
