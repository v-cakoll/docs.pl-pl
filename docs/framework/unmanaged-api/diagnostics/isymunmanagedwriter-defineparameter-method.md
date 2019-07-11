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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d5b82415635980f5bd4e13e87a0a03ec5b7032bb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777325"
---
# <a name="isymunmanagedwriterdefineparameter-method"></a><span data-ttu-id="77385-102">ISymUnmanagedWriter::DefineParameter — Metoda</span><span class="sxs-lookup"><span data-stu-id="77385-102">ISymUnmanagedWriter::DefineParameter Method</span></span>
<span data-ttu-id="77385-103">Definiuje pojedynczy parametr w bieżącej metodzie.</span><span class="sxs-lookup"><span data-stu-id="77385-103">Defines a single parameter in the current method.</span></span> <span data-ttu-id="77385-104">Typ parametru jest pobierana z parametru pozycji (kolejny) w podpisie metody.</span><span class="sxs-lookup"><span data-stu-id="77385-104">The parameter type is taken from the parameter's position (sequence) within the method's signature.</span></span>  
  
 <span data-ttu-id="77385-105">Parametry są definiowane w metadanych dla danej metody, nie trzeba je ponownie zdefiniować za pomocą tej metody.</span><span class="sxs-lookup"><span data-stu-id="77385-105">If parameters are defined in the metadata for a given method, you do not have to define them again by using this method.</span></span> <span data-ttu-id="77385-106">Czytelnicy symbol musi sprawdzić normalne metadane parametrów przed sprawdzeniem magazynu symboli.</span><span class="sxs-lookup"><span data-stu-id="77385-106">The symbol readers must check the normal metadata for the parameters before checking the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77385-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="77385-107">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="77385-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="77385-108">Parameters</span></span>  
 `name`  
 <span data-ttu-id="77385-109">[in] Nazwa parametru.</span><span class="sxs-lookup"><span data-stu-id="77385-109">[in] The parameter name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="77385-110">[in] Atrybuty parametru.</span><span class="sxs-lookup"><span data-stu-id="77385-110">[in] The parameter attributes.</span></span>  
  
 `sequence`  
 <span data-ttu-id="77385-111">[in] Podpis parametru.</span><span class="sxs-lookup"><span data-stu-id="77385-111">[in] The parameter signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="77385-112">[in] Typ adresu.</span><span class="sxs-lookup"><span data-stu-id="77385-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="77385-113">[in] Pierwszy adres specyfikację parametru.</span><span class="sxs-lookup"><span data-stu-id="77385-113">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="77385-114">[in] Drugi adres specyfikację parametru.</span><span class="sxs-lookup"><span data-stu-id="77385-114">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="77385-115">[in] Trzeci adres specyfikację parametru.</span><span class="sxs-lookup"><span data-stu-id="77385-115">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="77385-116">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="77385-116">Return Value</span></span>  
 <span data-ttu-id="77385-117">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="77385-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77385-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="77385-118">Requirements</span></span>  
 <span data-ttu-id="77385-119">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="77385-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77385-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="77385-120">See also</span></span>

- [<span data-ttu-id="77385-121">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="77385-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
