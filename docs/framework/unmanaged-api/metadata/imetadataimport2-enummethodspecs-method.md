---
title: IMetaDataImport2::EnumMethodSpecs — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumMethodSpecs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumMethodSpecs
helpviewer_keywords:
- IMetaDataImport2::EnumMethodSpecs method [.NET Framework metadata]
- EnumMethodSpecs method [.NET Framework metadata]
ms.assetid: b3fc1e6c-bcb6-4915-baf8-7dc0a31b8724
topic_type:
- apiref
ms.openlocfilehash: 4a1de144163ec2b4952bd16b59fb1c92b706631b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428300"
---
# <a name="imetadataimport2enummethodspecs-method"></a><span data-ttu-id="25b9f-102">IMetaDataImport2::EnumMethodSpecs — Metoda</span><span class="sxs-lookup"><span data-stu-id="25b9f-102">IMetaDataImport2::EnumMethodSpecs Method</span></span>
<span data-ttu-id="25b9f-103">Pobiera moduł wyliczający dla tablicy tokenów elementu MethodSpec skojarzonych z określonym tokenem MethodDef lub MemberRef.</span><span class="sxs-lookup"><span data-stu-id="25b9f-103">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25b9f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="25b9f-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodSpecs (  
    [in, out] HCORENUM      *phEnum,   
    [in]      mdToken       tk,  
    [out]     mdMethodSpec  rMethodSpecs[],  
    [in]      ULONG         cMax,  
    [out]     ULONG         *pcMethodSpecs  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="25b9f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="25b9f-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="25b9f-106">[in. out] Wskaźnik do modułu wyliczającego dla `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="25b9f-106">[in, out] A pointer to the enumerator for `rMethodSpecs`.</span></span>  
  
 `tk`  
 <span data-ttu-id="25b9f-107">podczas Token elementu MemberRef lub MethodDef reprezentujący metodę, której tokeny elementu MethodSpec mają zostać wyliczone.</span><span class="sxs-lookup"><span data-stu-id="25b9f-107">[in] The MemberRef or MethodDef token that represents the method whose MethodSpec tokens are to be enumerated.</span></span> <span data-ttu-id="25b9f-108">Jeśli wartość `tk` jest równa 0 (zero), wszystkie tokeny elementu MethodSpec w zakresie zostaną wyliczone.</span><span class="sxs-lookup"><span data-stu-id="25b9f-108">If the value of `tk` is 0 (zero), all MethodSpec tokens in the scope will be enumerated.</span></span>  
  
 `rMethodSpecs`  
 <span data-ttu-id="25b9f-109">określoną Tablica tokenów elementu MethodSpec do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="25b9f-109">[out] The array of MethodSpec tokens to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="25b9f-110">podczas Żądana Maksymalna liczba tokenów do umieszczenia w `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="25b9f-110">[in] The requested maximum number of tokens to place in `rMethodSpecs`.</span></span>  
  
 `pcMethodSpecs`  
 <span data-ttu-id="25b9f-111">określoną Zwrócona liczba tokenów umieszczonych w `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="25b9f-111">[out] The returned number of tokens placed in `rMethodSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="25b9f-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="25b9f-112">Return Value</span></span>  
  
|<span data-ttu-id="25b9f-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="25b9f-113">HRESULT</span></span>|<span data-ttu-id="25b9f-114">Opis</span><span class="sxs-lookup"><span data-stu-id="25b9f-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="25b9f-115">`EnumMethodSpecs` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="25b9f-115">`EnumMethodSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="25b9f-116">`phEnum` nie ma elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="25b9f-116">`phEnum` has no member elements.</span></span> <span data-ttu-id="25b9f-117">W tym przypadku `pcMethodSpecs` jest ustawiona na 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="25b9f-117">In this case, `pcMethodSpecs` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="25b9f-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="25b9f-118">Requirements</span></span>  
 <span data-ttu-id="25b9f-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25b9f-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25b9f-120">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="25b9f-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="25b9f-121">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="25b9f-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="25b9f-122">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25b9f-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25b9f-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="25b9f-123">See also</span></span>

- [<span data-ttu-id="25b9f-124">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="25b9f-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="25b9f-125">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="25b9f-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
