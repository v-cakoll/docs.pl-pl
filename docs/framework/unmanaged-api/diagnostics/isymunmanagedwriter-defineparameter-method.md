---
title: "ISymUnmanagedWriter::DefineParameter — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.DefineParameter
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::DefineParameter
helpviewer_keywords:
- DefineParameter method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineParameter method [.NET Framework debugging]
ms.assetid: a8e3dd32-6a44-4371-9a74-f417b11998c8
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7fe62a8f6b48d1a9931cc0310811d7fc42f7029b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriterdefineparameter-method"></a><span data-ttu-id="33e44-102">ISymUnmanagedWriter::DefineParameter — Metoda</span><span class="sxs-lookup"><span data-stu-id="33e44-102">ISymUnmanagedWriter::DefineParameter Method</span></span>
<span data-ttu-id="33e44-103">Określa pojedynczy parametr w bieżącej metodzie.</span><span class="sxs-lookup"><span data-stu-id="33e44-103">Defines a single parameter in the current method.</span></span> <span data-ttu-id="33e44-104">Typ parametru jest pobierana z parametru pozycji (sekwencji) w podpisie metody.</span><span class="sxs-lookup"><span data-stu-id="33e44-104">The parameter type is taken from the parameter's position (sequence) within the method's signature.</span></span>  
  
 <span data-ttu-id="33e44-105">Parametry są definiowane w metadanych dla danej metody, nie trzeba definiować ich ponownie za pomocą tej metody.</span><span class="sxs-lookup"><span data-stu-id="33e44-105">If parameters are defined in the metadata for a given method, you do not have to define them again by using this method.</span></span> <span data-ttu-id="33e44-106">Czytniki symbol musi sprawdzić normalne metadane parametrów przed zaewidencjonowaniem magazynu symboli.</span><span class="sxs-lookup"><span data-stu-id="33e44-106">The symbol readers must check the normal metadata for the parameters before checking the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33e44-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="33e44-107">Syntax</span></span>  
  
```  
HRESULT DefineParameter(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      sequence,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="33e44-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="33e44-108">Parameters</span></span>  
 `name`  
 <span data-ttu-id="33e44-109">[in] Nazwa parametru.</span><span class="sxs-lookup"><span data-stu-id="33e44-109">[in] The parameter name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="33e44-110">[in] Atrybuty parametrów.</span><span class="sxs-lookup"><span data-stu-id="33e44-110">[in] The parameter attributes.</span></span>  
  
 `sequence`  
 <span data-ttu-id="33e44-111">[in] Sygnatura parametru.</span><span class="sxs-lookup"><span data-stu-id="33e44-111">[in] The parameter signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="33e44-112">[in] Typ adresu.</span><span class="sxs-lookup"><span data-stu-id="33e44-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="33e44-113">[in] Pierwszy adres Specyfikacja parametru.</span><span class="sxs-lookup"><span data-stu-id="33e44-113">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="33e44-114">[in] Drugi adres Specyfikacja parametru.</span><span class="sxs-lookup"><span data-stu-id="33e44-114">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="33e44-115">[in] Trzeci adres Specyfikacja parametru.</span><span class="sxs-lookup"><span data-stu-id="33e44-115">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="33e44-116">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="33e44-116">Return Value</span></span>  
 <span data-ttu-id="33e44-117">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="33e44-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33e44-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="33e44-118">Requirements</span></span>  
 <span data-ttu-id="33e44-119">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="33e44-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33e44-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="33e44-120">See Also</span></span>  
 [<span data-ttu-id="33e44-121">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="33e44-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
