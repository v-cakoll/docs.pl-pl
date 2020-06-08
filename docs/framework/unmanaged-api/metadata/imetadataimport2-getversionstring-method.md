---
title: IMetaDataImport2::GetVersionString — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetVersionString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetVersionString
helpviewer_keywords:
- GetVersionString method, IMetaDataImport2 interface [.NET Framework metadata]
- IMetaDataImport2::GetVersionString method [.NET Framework metadata]
ms.assetid: 308183ee-fd44-4432-9d86-ef00d181b49b
topic_type:
- apiref
ms.openlocfilehash: 84cf5ac9eab5749d3bdc63670fe5c31bfb62abcd
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490410"
---
# <a name="imetadataimport2getversionstring-method"></a><span data-ttu-id="2312f-102">IMetaDataImport2::GetVersionString — Metoda</span><span class="sxs-lookup"><span data-stu-id="2312f-102">IMetaDataImport2::GetVersionString Method</span></span>
<span data-ttu-id="2312f-103">Pobiera numer wersji środowiska uruchomieniowego, który został użyty do skompilowania zestawu.</span><span class="sxs-lookup"><span data-stu-id="2312f-103">Gets the version number of the runtime that was used to build the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2312f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2312f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionString (  
   [out] LPWSTR      pwzBuf,  
   [in]  DWORD       ccBufSize,  
   [out] DWORD       *pccBufSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2312f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2312f-105">Parameters</span></span>  
 `pwzBuf`  
 <span data-ttu-id="2312f-106">określoną Tablica do przechowywania ciągu, który określa wersję.</span><span class="sxs-lookup"><span data-stu-id="2312f-106">[out] An array to store the string that specifies the version.</span></span>  
  
 `ccBufSize`  
 <span data-ttu-id="2312f-107">podczas Rozmiar, w postaci dwubajtowej `pwzBuf` tablicy.</span><span class="sxs-lookup"><span data-stu-id="2312f-107">[in] The size, in wide characters, of the `pwzBuf` array.</span></span>  
  
 `pccBufSize`  
 <span data-ttu-id="2312f-108">określoną Liczba znaków dwubajtowych, łącznie z terminatorem wartości null, zwracana w `pwzBuf` tablicy.</span><span class="sxs-lookup"><span data-stu-id="2312f-108">[out] The number of wide characters, including a null terminator, returned in the `pwzBuf` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2312f-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2312f-109">Remarks</span></span>  
 <span data-ttu-id="2312f-110">`GetVersionString`Metoda pobiera wbudowaną wersję bieżącego zakresu metadanych.</span><span class="sxs-lookup"><span data-stu-id="2312f-110">The `GetVersionString` method gets the built-for version of the current metadata scope.</span></span> <span data-ttu-id="2312f-111">Jeśli zakres nigdy nie został zapisany, nie będzie miał wbudowanej wersji i zostanie zwrócony pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="2312f-111">If the scope has never been saved, it will not have a built-for version, and an empty string will be returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2312f-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2312f-112">Requirements</span></span>  
 <span data-ttu-id="2312f-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2312f-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2312f-114">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2312f-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2312f-115">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2312f-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2312f-116">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2312f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2312f-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2312f-117">See also</span></span>

- [<span data-ttu-id="2312f-118">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="2312f-118">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="2312f-119">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2312f-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
