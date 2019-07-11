---
title: CorPEKind — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorPEKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPEKind
helpviewer_keywords:
- CorPEKind enumeration [.NET Framework metadata]
ms.assetid: 22dc6dea-b1b9-4982-a730-a022d586b117
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0bfe30567bcd8e22a82d401e00b0a6ee50407def
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781673"
---
# <a name="corpekind-enumeration"></a><span data-ttu-id="bf43f-102">CorPEKind — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="bf43f-102">CorPEKind Enumeration</span></span>
<span data-ttu-id="bf43f-103">Zawiera wartości, które opisują plików przenośnych plików wykonywalnych (PE), ponieważ zwrócony z wywołania do [IMetaDataImport2::GetPEKind](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md).</span><span class="sxs-lookup"><span data-stu-id="bf43f-103">Contains values that describe a portable executable (PE) file, as returned from a call to [IMetaDataImport2::GetPEKind](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf43f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bf43f-104">Syntax</span></span>  
  
```cpp  
typedef enum CorPEKind {  
  
    peNot           = 0x00000000,  
    peILonly        = 0x00000001,  
    pe32BitRequired = 0x00000002,  
    pe32Plus        = 0x00000004,  
    pe32Unmanaged   = 0x00000008,  
    pe32BitPreferred= 0x00000010  
  
} CorPEKind;  
```  
  
## <a name="members"></a><span data-ttu-id="bf43f-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="bf43f-105">Members</span></span>  
  
|<span data-ttu-id="bf43f-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="bf43f-106">Member</span></span>|<span data-ttu-id="bf43f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="bf43f-107">Description</span></span>|  
|------------|-----------------|  
|`peNot`|<span data-ttu-id="bf43f-108">Wskazuje, że nie jest plikiem PE.</span><span class="sxs-lookup"><span data-stu-id="bf43f-108">Indicates that this is not a PE file.</span></span>|  
|`peILOnly`|<span data-ttu-id="bf43f-109">Wskazuje, że ten plik PE zawiera tylko kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="bf43f-109">Indicates that this PE file contains only managed code.</span></span>|  
|`pe32BitRequired`|<span data-ttu-id="bf43f-110">Wskazuje, że ten plik PE wywołań Win32.</span><span class="sxs-lookup"><span data-stu-id="bf43f-110">Indicates that this PE file makes Win32 calls.</span></span>|  
|`pe32Plus`|<span data-ttu-id="bf43f-111">Wskazuje, że ten plik PE jest uruchamiany na platformie 64-bitowej.</span><span class="sxs-lookup"><span data-stu-id="bf43f-111">Indicates that this PE file runs on a 64-bit platform.</span></span>|  
|`pe32Unmanaged`|<span data-ttu-id="bf43f-112">Wskazuje, że ten plik PE jest kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="bf43f-112">Indicates that this PE file is native code.</span></span>|  
|<span data-ttu-id="bf43f-113">pe32BitPreferred</span><span class="sxs-lookup"><span data-stu-id="bf43f-113">pe32BitPreferred</span></span>|<span data-ttu-id="bf43f-114">Wskazuje, czy ten plik PE jest niezależny od platformy i preferuje do załadowania w środowisku 32-bitowych.</span><span class="sxs-lookup"><span data-stu-id="bf43f-114">Indicates that this PE file is platform-neutral and prefers to be loaded in a 32-bit environment.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf43f-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bf43f-115">Remarks</span></span>  
 <span data-ttu-id="bf43f-116">Te wartości można używane w kombinacji bitowe.</span><span class="sxs-lookup"><span data-stu-id="bf43f-116">These values can be used in bitwise combinations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf43f-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bf43f-117">Requirements</span></span>  
 <span data-ttu-id="bf43f-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf43f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf43f-119">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="bf43f-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="bf43f-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf43f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf43f-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bf43f-121">See also</span></span>

- [<span data-ttu-id="bf43f-122">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="bf43f-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
