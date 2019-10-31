---
title: ECustomDumpFlavor — Wyliczenie
ms.date: 03/30/2017
api_name:
- ECustomDumpFlavor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ECustomDumpFlavor
helpviewer_keywords:
- ECustomDumpFlavor enumeration [.NET Framework hosting]
ms.assetid: b39b3320-fac7-41f1-9a03-ab6fb0cd89c7
topic_type:
- apiref
ms.openlocfilehash: 057794fe524a0ee01f6f090ca7e11a4a4b523047
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124931"
---
# <a name="ecustomdumpflavor-enumeration"></a><span data-ttu-id="e3121-102">ECustomDumpFlavor — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="e3121-102">ECustomDumpFlavor Enumeration</span></span>
<span data-ttu-id="e3121-103">Zawiera wartości wskazujące, które elementy mają być uwzględnione w niestandardowym podzestawie zrzutu sterty podczas raportowania błędów.</span><span class="sxs-lookup"><span data-stu-id="e3121-103">Contains values that indicate which items to include in a custom subset of a heap dump when reporting errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3121-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e3121-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    DUMP_FLAVOR_Mini            = 1,  
    DUMP_FLAVOR_NonHeapCLRState = 2  
} ECustomDumpFlavor;  
```  
  
## <a name="members"></a><span data-ttu-id="e3121-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e3121-105">Members</span></span>  
  
|<span data-ttu-id="e3121-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="e3121-106">Member</span></span>|<span data-ttu-id="e3121-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e3121-107">Description</span></span>|  
|------------|-----------------|  
|`DUMP_FLAVOR_Mini`|<span data-ttu-id="e3121-108">Określa, że niestandardowy zrzut sterty powinien rozpoczynać się jako minizrzutu i dołączać dodatkowe dane określone przez wystąpienia [CustomDumpItem —](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) przesłane do tej samej metody.</span><span class="sxs-lookup"><span data-stu-id="e3121-108">Specifies that the custom heap dump should start as a minidump and include extra data specified by any [CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) instances passed to the same method.</span></span>|  
|`DUMP_FLAVOR_NonHeapCLRState`|<span data-ttu-id="e3121-109">Określa, że zrzut sterty niestandardowej ma zbierać wszystkie dane stanu czasu wykonywania, które nie były przydzielane dynamicznie.</span><span class="sxs-lookup"><span data-stu-id="e3121-109">Specifies that the custom heap dump should gather all run-time state data that was not dynamically allocated.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3121-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e3121-110">Remarks</span></span>  
 <span data-ttu-id="e3121-111">Parametr typu `ECustomDumpFlavor` jest przesyłany do metody [ICLRErrorReportingManager:: BeginCustomDump —](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e3121-111">A parameter of type `ECustomDumpFlavor` is passed to the [ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3121-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e3121-112">Requirements</span></span>  
 <span data-ttu-id="e3121-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3121-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3121-114">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e3121-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e3121-115">**Biblioteka:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e3121-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e3121-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3121-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3121-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e3121-117">See also</span></span>

- [<span data-ttu-id="e3121-118">ECustomDumpItemKind, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="e3121-118">ECustomDumpItemKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)
- [<span data-ttu-id="e3121-119">ICLRErrorReportingManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e3121-119">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="e3121-120">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="e3121-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
