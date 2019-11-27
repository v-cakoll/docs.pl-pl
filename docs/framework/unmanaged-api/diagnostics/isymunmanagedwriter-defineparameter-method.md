---
title: ISymUnmanagedWriter::DefineParameter — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineParameter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineParameter
helpviewer_keywords:
- DefineParameter method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineParameter method [.NET Framework debugging]
ms.assetid: a8e3dd32-6a44-4371-9a74-f417b11998c8
topic_type:
- apiref
ms.openlocfilehash: bc1b65de026a674a3dff183050a5a205fd7052c9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427995"
---
# <a name="isymunmanagedwriterdefineparameter-method"></a><span data-ttu-id="74442-102">ISymUnmanagedWriter::DefineParameter — Metoda</span><span class="sxs-lookup"><span data-stu-id="74442-102">ISymUnmanagedWriter::DefineParameter Method</span></span>
<span data-ttu-id="74442-103">Definiuje pojedynczy parametr w bieżącej metodzie.</span><span class="sxs-lookup"><span data-stu-id="74442-103">Defines a single parameter in the current method.</span></span> <span data-ttu-id="74442-104">Typ parametru jest pobierany z pozycji parametru (Sequence) w podpisie metody.</span><span class="sxs-lookup"><span data-stu-id="74442-104">The parameter type is taken from the parameter's position (sequence) within the method's signature.</span></span>  
  
 <span data-ttu-id="74442-105">Jeśli parametry są zdefiniowane w metadanych dla danej metody, nie trzeba ich definiować ponownie przy użyciu tej metody.</span><span class="sxs-lookup"><span data-stu-id="74442-105">If parameters are defined in the metadata for a given method, you do not have to define them again by using this method.</span></span> <span data-ttu-id="74442-106">Czytelnicy symboli muszą sprawdzić normalne metadane parametrów przed sprawdzeniem magazynu symboli.</span><span class="sxs-lookup"><span data-stu-id="74442-106">The symbol readers must check the normal metadata for the parameters before checking the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74442-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="74442-107">Syntax</span></span>  
  
```cpp  
HRESULT DefineParameter(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      sequence,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74442-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="74442-108">Parameters</span></span>  
 `name`  
 <span data-ttu-id="74442-109">podczas Nazwa parametru.</span><span class="sxs-lookup"><span data-stu-id="74442-109">[in] The parameter name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="74442-110">podczas Atrybuty parametru.</span><span class="sxs-lookup"><span data-stu-id="74442-110">[in] The parameter attributes.</span></span>  
  
 `sequence`  
 <span data-ttu-id="74442-111">podczas Sygnatura parametru.</span><span class="sxs-lookup"><span data-stu-id="74442-111">[in] The parameter signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="74442-112">podczas Typ adresu.</span><span class="sxs-lookup"><span data-stu-id="74442-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="74442-113">podczas Pierwszy adres dla specyfikacji parametru.</span><span class="sxs-lookup"><span data-stu-id="74442-113">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="74442-114">podczas Drugi adres dla specyfikacji parametru.</span><span class="sxs-lookup"><span data-stu-id="74442-114">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="74442-115">podczas Trzeci adres dla specyfikacji parametru.</span><span class="sxs-lookup"><span data-stu-id="74442-115">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="74442-116">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="74442-116">Return Value</span></span>  
 <span data-ttu-id="74442-117">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="74442-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74442-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="74442-118">Requirements</span></span>  
 <span data-ttu-id="74442-119">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="74442-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74442-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="74442-120">See also</span></span>

- [<span data-ttu-id="74442-121">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="74442-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
