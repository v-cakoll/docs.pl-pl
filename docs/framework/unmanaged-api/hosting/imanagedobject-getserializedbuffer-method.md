---
title: IManagedObject::GetSerializedBuffer — Metoda
ms.date: 03/30/2017
api_name:
- IManagedObject.GetSerializedBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetSerializedBuffer
helpviewer_keywords:
- IManagedObject::GetSerializedBuffer method [.NET Framework hosting]
- GetSerializedBuffer method [.NET Framework hosting]
ms.assetid: c17105bb-b49f-434e-8f9b-77f8c85b9220
topic_type:
- apiref
ms.openlocfilehash: c68ec0b41bb38afc7cefaf47df718fffcf42d250
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842433"
---
# <a name="imanagedobjectgetserializedbuffer-method"></a><span data-ttu-id="42861-102">IManagedObject::GetSerializedBuffer — Metoda</span><span class="sxs-lookup"><span data-stu-id="42861-102">IManagedObject::GetSerializedBuffer Method</span></span>
<span data-ttu-id="42861-103">Pobiera ciąg reprezentujący ten obiekt zarządzany.</span><span class="sxs-lookup"><span data-stu-id="42861-103">Gets the string representation of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42861-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="42861-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSerializedBuffer (  
    [out] BSTR *pBSTR  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42861-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="42861-105">Parameters</span></span>  
 `pBSTR`  
 <span data-ttu-id="42861-106">określoną Wskaźnik do ciągu, który jest serializowanym obiektem.</span><span class="sxs-lookup"><span data-stu-id="42861-106">[out] A pointer to a string that is the serialized object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42861-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="42861-107">Remarks</span></span>  
 <span data-ttu-id="42861-108">`GetSerializedBuffer`Metoda serializować obiekt, aby można go było zorganizować dla klienta.</span><span class="sxs-lookup"><span data-stu-id="42861-108">The `GetSerializedBuffer` method serializes the object so it can be marshaled to the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42861-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="42861-109">Requirements</span></span>  
 <span data-ttu-id="42861-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42861-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42861-111">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="42861-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="42861-112">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="42861-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="42861-113">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42861-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42861-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="42861-114">See also</span></span>

- [<span data-ttu-id="42861-115">IManagedObject, interfejs</span><span class="sxs-lookup"><span data-stu-id="42861-115">IManagedObject Interface</span></span>](imanagedobject-interface.md)
