---
title: ICorPublishAppDomain::GetName — Metoda
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomain.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomain::GetName
helpviewer_keywords:
- GetName method, ICorPublishAppDomain interface [.NET Framework debugging]
- ICorPublishAppDomain::GetName method [.NET Framework debugging]
ms.assetid: 6ef8ac9b-9803-4b65-8b13-25f3e0b1bc6b
topic_type:
- apiref
ms.openlocfilehash: 2f91891164f1f80617cab10347eb4a7a08762c10
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140351"
---
# <a name="icorpublishappdomaingetname-method"></a><span data-ttu-id="36ec2-102">ICorPublishAppDomain::GetName — Metoda</span><span class="sxs-lookup"><span data-stu-id="36ec2-102">ICorPublishAppDomain::GetName Method</span></span>
<span data-ttu-id="36ec2-103">Pobiera nazwę domeny aplikacji reprezentowanej przez ten [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span><span class="sxs-lookup"><span data-stu-id="36ec2-103">Gets the name of the application domain that is represented by this [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36ec2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="36ec2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32   cchName,   
    [out] ULONG32   *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR       *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="36ec2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="36ec2-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="36ec2-106">podczas Rozmiar tablicy `szName`.</span><span class="sxs-lookup"><span data-stu-id="36ec2-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="36ec2-107">określoną Wskaźnik do liczby znaków dwubajtowych, w tym znak null, zwracany w tablicy `szName`.</span><span class="sxs-lookup"><span data-stu-id="36ec2-107">[out] A pointer to the number of wide characters, including the null character, returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="36ec2-108">określoną Tablica, w której ma zostać przechowana nazwa.</span><span class="sxs-lookup"><span data-stu-id="36ec2-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36ec2-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="36ec2-109">Remarks</span></span>  
 <span data-ttu-id="36ec2-110">Jeśli `szName` ma wartość różną od null, Metoda `GetName` kopiuje do `szName`znaki `cchName` (w tym terminator wartości null).</span><span class="sxs-lookup"><span data-stu-id="36ec2-110">If `szName` is non-null, the `GetName` method copies up to `cchName` characters (including the null terminator) into `szName`.</span></span> <span data-ttu-id="36ec2-111">Jeśli w `pcchName`jest zwracana wartość inna niż null, rzeczywista liczba znaków w nazwie (łącznie z terminatorem wartości null) jest przechowywana w tablicy `szName`.</span><span class="sxs-lookup"><span data-stu-id="36ec2-111">If a non-null is returned in `pcchName`, the actual number of characters in the name (including the null terminator) is stored in the `szName` array.</span></span>  
  
 <span data-ttu-id="36ec2-112">Metoda `GetName` zwraca wartość HRESULT S_OK, niezależnie od liczby skopiowanych znaków.</span><span class="sxs-lookup"><span data-stu-id="36ec2-112">The `GetName` method returns an S_OK HRESULT regardless of how many characters were copied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36ec2-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="36ec2-113">Requirements</span></span>  
 <span data-ttu-id="36ec2-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36ec2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36ec2-115">**Nagłówek:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="36ec2-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="36ec2-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="36ec2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36ec2-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36ec2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36ec2-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="36ec2-118">See also</span></span>

- [<span data-ttu-id="36ec2-119">ICorPublishAppDomain, interfejs</span><span class="sxs-lookup"><span data-stu-id="36ec2-119">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)
