---
title: ImportTypes — Metoda
ms.date: 03/30/2017
api_name:
- IALink.ImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportTypes
helpviewer_keywords:
- ImportTypes method
ms.assetid: 351d4b4c-c939-486d-9471-51914a55f471
topic_type:
- apiref
ms.openlocfilehash: 76d2b163f959111923bffb1348890f6fbb29828e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445678"
---
# <a name="importtypes-method"></a><span data-ttu-id="04a24-102">ImportTypes — Metoda</span><span class="sxs-lookup"><span data-stu-id="04a24-102">ImportTypes Method</span></span>
<span data-ttu-id="04a24-103">Inicjuje importowanie typów z każdego zakresu zaimportowanego za pomocą [metody ImportFile —](importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="04a24-103">Initiates the importing of types from each scope imported via [ImportFile Method](importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04a24-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="04a24-104">Syntax</span></span>  
  
```cpp  
HRESULT ImportTypes(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="04a24-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="04a24-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="04a24-106">Identyfikator zestawu do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="04a24-106">ID of the assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="04a24-107">Identyfikator pliku do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="04a24-107">ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="04a24-108">Zakres od zera do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="04a24-108">Zero-based scope to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="04a24-109">Odbiera dojście modułu wyliczającego dla typów w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="04a24-109">Receives enumerator handle for the types in this scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="04a24-110">Opcjonalnie odbiera Interfejs [interfejsu IMetaDataImport](../metadata/imetadataimport-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="04a24-110">Optionally receives [IMetaDataImport Interface](../metadata/imetadataimport-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="04a24-111">Opcjonalnie otrzymuje liczbę typów we wskazanym zakresie.</span><span class="sxs-lookup"><span data-stu-id="04a24-111">Optionally receives count of types in the indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="04a24-112">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="04a24-112">Return Value</span></span>  
 <span data-ttu-id="04a24-113">Zwraca S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="04a24-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04a24-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="04a24-114">Requirements</span></span>  
 <span data-ttu-id="04a24-115">Wymaga Alink. h</span><span class="sxs-lookup"><span data-stu-id="04a24-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04a24-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="04a24-116">See also</span></span>

- [<span data-ttu-id="04a24-117">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="04a24-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="04a24-118">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="04a24-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="04a24-119">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="04a24-119">ALink API</span></span>](index.md)
