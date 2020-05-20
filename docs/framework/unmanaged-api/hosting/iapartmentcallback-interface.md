---
title: IApartmentCallback — Interfejs
ms.date: 03/30/2017
api_name:
- IApartmentCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IApartmentCallback
helpviewer_keywords:
- IApartmentCallback interface [.NET Framework hosting]
ms.assetid: 57c33c58-bf0b-4533-b569-e6a682d02cba
topic_type:
- apiref
ms.openlocfilehash: fbf501d906ecc0bf55719fa33d1af2d4db1cc2ef
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617100"
---
# <a name="iapartmentcallback-interface"></a><span data-ttu-id="f1b7a-102">IApartmentCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f1b7a-102">IApartmentCallback Interface</span></span>
<span data-ttu-id="f1b7a-103">Zapewnia metody tworzenia wywołań zwrotnych w obrębie apartamentu.</span><span class="sxs-lookup"><span data-stu-id="f1b7a-103">Provides methods for making callbacks within an apartment.</span></span> <span data-ttu-id="f1b7a-104">*Apartament* jest kontenerem logicznym w ramach procesu dla obiektów, które mają takie same wymagania dotyczące dostępu do wątków.</span><span class="sxs-lookup"><span data-stu-id="f1b7a-104">An *apartment* is a logical container within a process for objects that share the same thread access requirements.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f1b7a-105">Metody</span><span class="sxs-lookup"><span data-stu-id="f1b7a-105">Methods</span></span>  
  
|<span data-ttu-id="f1b7a-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="f1b7a-106">Method</span></span>|<span data-ttu-id="f1b7a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f1b7a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f1b7a-108">DoCallback, metoda</span><span class="sxs-lookup"><span data-stu-id="f1b7a-108">DoCallback Method</span></span>](iapartmentcallback-docallback-method.md)|<span data-ttu-id="f1b7a-109">Wykonuje określoną funkcję w obrębie apartamentu.</span><span class="sxs-lookup"><span data-stu-id="f1b7a-109">Executes the specified function within an apartment.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f1b7a-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f1b7a-110">Requirements</span></span>  
 <span data-ttu-id="f1b7a-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1b7a-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1b7a-112">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f1b7a-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f1b7a-113">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f1b7a-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f1b7a-114">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1b7a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1b7a-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f1b7a-115">See also</span></span>

- [<span data-ttu-id="f1b7a-116">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f1b7a-116">Hosting Interfaces</span></span>](hosting-interfaces.md)
