---
title: IMetaDataImport::GetUserString — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetUserString
helpviewer_keywords:
- IMetaDataImport::GetUserString method [.NET Framework metadata]
- GetUserString method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 0fd3bb47-58b5-4083-b241-b9719df7a285
topic_type:
- apiref
ms.openlocfilehash: 358ca84f32e1b233116605bf5486cc9a01b42e67
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503510"
---
# <a name="imetadataimportgetuserstring-method"></a><span data-ttu-id="4a032-102">IMetaDataImport::GetUserString — Metoda</span><span class="sxs-lookup"><span data-stu-id="4a032-102">IMetaDataImport::GetUserString Method</span></span>
<span data-ttu-id="4a032-103">Pobiera ciąg literału reprezentowanego przez określony token metadanych.</span><span class="sxs-lookup"><span data-stu-id="4a032-103">Gets the literal string represented by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a032-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4a032-104">Syntax</span></span>  
  
```cpp  
HRESULT GetUserString (  
   [in]   mdString    stk,  
   [out]  LPWSTR      szString,  
   [in]   ULONG       cchString,  
   [out]  ULONG       *pchString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a032-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4a032-105">Parameters</span></span>  
 `stk`  
 <span data-ttu-id="4a032-106">podczas Token ciągu, dla którego ma zostać zwrócony skojarzony ciąg.</span><span class="sxs-lookup"><span data-stu-id="4a032-106">[in] The String token to return the associated string for.</span></span>  
  
 `szString`  
 <span data-ttu-id="4a032-107">określoną Kopia żądanego ciągu.</span><span class="sxs-lookup"><span data-stu-id="4a032-107">[out] A copy of the requested string.</span></span>  
  
 `cchString`  
 <span data-ttu-id="4a032-108">podczas Maksymalny rozmiar w postaci dwubajtowej żądanej wartości `szString` .</span><span class="sxs-lookup"><span data-stu-id="4a032-108">[in] The maximum size in wide characters of the requested `szString`.</span></span>  
  
 `pchString`  
 <span data-ttu-id="4a032-109">określoną Rozmiar znaków dwubajtowych zwracanych `szString` .</span><span class="sxs-lookup"><span data-stu-id="4a032-109">[out] The size in wide characters of the returned `szString`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a032-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4a032-110">Requirements</span></span>  
 <span data-ttu-id="4a032-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a032-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a032-112">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4a032-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4a032-113">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4a032-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4a032-114">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a032-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a032-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4a032-115">See also</span></span>

- [<span data-ttu-id="4a032-116">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="4a032-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="4a032-117">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="4a032-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
