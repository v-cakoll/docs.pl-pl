---
title: IMetaDataImport2 — Interfejs
ms.date: 03/30/2017
api_name:
- IMetaDataImport2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2
helpviewer_keywords:
- IMetaDataImport2 interface [.NET Framework metadata]
ms.assetid: d39b2b87-ba53-4771-ae53-952a68452511
topic_type:
- apiref
ms.openlocfilehash: fe9e87618291218a41e52f80198ce9068c9c56e2
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490399"
---
# <a name="imetadataimport2-interface"></a><span data-ttu-id="1b1b1-102">IMetaDataImport2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1b1b1-102">IMetaDataImport2 Interface</span></span>
<span data-ttu-id="1b1b1-103">Rozszerza interfejs [IMetaDataImport](imetadataimport-interface.md) w celu zapewnienia możliwości pracy z typami ogólnymi.</span><span class="sxs-lookup"><span data-stu-id="1b1b1-103">Extends the [IMetaDataImport](imetadataimport-interface.md) interface to provide the capability of working with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1b1b1-104">Metody</span><span class="sxs-lookup"><span data-stu-id="1b1b1-104">Methods</span></span>  
  
|<span data-ttu-id="1b1b1-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="1b1b1-105">Method</span></span>|<span data-ttu-id="1b1b1-106">Opis</span><span class="sxs-lookup"><span data-stu-id="1b1b1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1b1b1-107">EnumGenericParamConstraints — Metoda</span><span class="sxs-lookup"><span data-stu-id="1b1b1-107">EnumGenericParamConstraints Method</span></span>](imetadataimport2-enumgenericparamconstraints-method.md)|<span data-ttu-id="1b1b1-108">Pobiera moduł wyliczający dla tablicy ograniczeń parametrów ogólnych skojarzonych z parametrem ogólnym reprezentowanym przez określony token.</span><span class="sxs-lookup"><span data-stu-id="1b1b1-108">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="1b1b1-109">EnumGenericParams — Metoda</span><span class="sxs-lookup"><span data-stu-id="1b1b1-109">EnumGenericParams Method</span></span>](imetadataimport2-enumgenericparams-method.md)|<span data-ttu-id="1b1b1-110">Pobiera moduł wyliczający dla tablicy tokenów parametrów ogólnych skojarzonych z określonym tokenem TypeDef lub MethodDef.</span><span class="sxs-lookup"><span data-stu-id="1b1b1-110">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>|  
|[<span data-ttu-id="1b1b1-111">EnumMethodSpecs — Metoda</span><span class="sxs-lookup"><span data-stu-id="1b1b1-111">EnumMethodSpecs Method</span></span>](imetadataimport2-enummethodspecs-method.md)|<span data-ttu-id="1b1b1-112">Pobiera moduł wyliczający dla tablicy tokenów elementu MethodSpec skojarzonych z określonym tokenem MethodDef lub MemberRef.</span><span class="sxs-lookup"><span data-stu-id="1b1b1-112">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>|  
|[<span data-ttu-id="1b1b1-113">GetGenericParamConstraintProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="1b1b1-113">GetGenericParamConstraintProps Method</span></span>](imetadataimport2-getgenericparamconstraintprops-method.md)|<span data-ttu-id="1b1b1-114">Pobiera metadane skojarzone z ograniczeniem parametru generycznego reprezentowane przez określony token ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="1b1b1-114">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span></span>|  
|[<span data-ttu-id="1b1b1-115">GetGenericParamProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="1b1b1-115">GetGenericParamProps Method</span></span>](imetadataimport2-getgenericparamprops-method.md)|<span data-ttu-id="1b1b1-116">Pobiera metadane skojarzone z parametrem ogólnym reprezentowanym przez określony token.</span><span class="sxs-lookup"><span data-stu-id="1b1b1-116">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="1b1b1-117">GetMethodSpecProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="1b1b1-117">GetMethodSpecProps Method</span></span>](imetadataimport2-getmethodspecprops-method.md)|<span data-ttu-id="1b1b1-118">Pobiera sygnaturę metadanych metody przywoływanej przez określony token elementu MethodSpec.</span><span class="sxs-lookup"><span data-stu-id="1b1b1-118">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>|  
|[<span data-ttu-id="1b1b1-119">GetPEKind — Metoda</span><span class="sxs-lookup"><span data-stu-id="1b1b1-119">GetPEKind Method</span></span>](imetadataimport2-getpekind-method.md)|<span data-ttu-id="1b1b1-120">Pobiera wartość identyfikującą charakter kodu w przenośnym pliku wykonywalnym (PE), zazwyczaj plik DLL lub EXE, zdefiniowany w bieżącym zakresie metadanych</span><span class="sxs-lookup"><span data-stu-id="1b1b1-120">Gets a value identifying the nature of the code in a portable executable (PE) file, typically a DLL or EXE file, defined in the current metadata scope</span></span>|  
|[<span data-ttu-id="1b1b1-121">GetVersionString — Metoda</span><span class="sxs-lookup"><span data-stu-id="1b1b1-121">GetVersionString Method</span></span>](imetadataimport2-getversionstring-method.md)|<span data-ttu-id="1b1b1-122">Pobiera numer wersji środowiska uruchomieniowego, który został użyty do skompilowania zestawu.</span><span class="sxs-lookup"><span data-stu-id="1b1b1-122">Gets the version number of the runtime that was used to build the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1b1b1-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1b1b1-123">Requirements</span></span>  
 <span data-ttu-id="1b1b1-124">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b1b1-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b1b1-125">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="1b1b1-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1b1b1-126">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1b1b1-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1b1b1-127">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b1b1-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b1b1-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1b1b1-128">See also</span></span>

- <xref:System.Reflection.PortableExecutableKinds>
- [<span data-ttu-id="1b1b1-129">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="1b1b1-129">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="1b1b1-130">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1b1b1-130">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
