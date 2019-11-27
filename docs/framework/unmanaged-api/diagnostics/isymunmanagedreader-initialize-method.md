---
title: ISymUnmanagedReader::Initialize — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.Initialize
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::Initialize
helpviewer_keywords:
- ISymUnmanagedReader::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 8f0dd2fe-7df7-464e-91f4-5518c586bb5f
topic_type:
- apiref
ms.openlocfilehash: ca34d1d84d6f9960d021c35566f8412df321464d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429738"
---
# <a name="isymunmanagedreaderinitialize-method"></a><span data-ttu-id="47b75-102">ISymUnmanagedReader::Initialize — Metoda</span><span class="sxs-lookup"><span data-stu-id="47b75-102">ISymUnmanagedReader::Initialize Method</span></span>
<span data-ttu-id="47b75-103">Inicjuje czytnik symboli z interfejsem importera metadanych, z którym zostanie skojarzony ten czytnik, wraz z nazwą pliku modułu.</span><span class="sxs-lookup"><span data-stu-id="47b75-103">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="47b75-104">Tę metodę można wywołać tylko raz i muszą one zostać wywołane przed innymi metodami czytnika.</span><span class="sxs-lookup"><span data-stu-id="47b75-104">This method can be called only once, and must be called before any other reader methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47b75-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="47b75-105">Syntax</span></span>  
  
```cpp  
HRESULT Initialize (  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *filename,  
    [in]  const WCHAR  *searchPath,  
    [in]  IStream      *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="47b75-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="47b75-106">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="47b75-107">podczas Interfejs programu do importowania metadanych, z którym ten czytnik zostanie skojarzony.</span><span class="sxs-lookup"><span data-stu-id="47b75-107">[in] The metadata importer interface with which this reader will be associated.</span></span>  
  
 `filename`  
 <span data-ttu-id="47b75-108">podczas Nazwa pliku modułu.</span><span class="sxs-lookup"><span data-stu-id="47b75-108">[in] The file name of the module.</span></span> <span data-ttu-id="47b75-109">Zamiast tego można użyć parametru `pIStream`.</span><span class="sxs-lookup"><span data-stu-id="47b75-109">You can use the `pIStream` parameter instead.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="47b75-110">podczas Ścieżka do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="47b75-110">[in] The path to search.</span></span> <span data-ttu-id="47b75-111">Ten parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="47b75-111">This parameter is optional.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="47b75-112">podczas Strumień pliku używany jako alternatywa dla parametru filename.</span><span class="sxs-lookup"><span data-stu-id="47b75-112">[in] The file stream, used as an alternative to the filename parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="47b75-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="47b75-113">Return Value</span></span>  
 <span data-ttu-id="47b75-114">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="47b75-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47b75-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="47b75-115">Remarks</span></span>  
 <span data-ttu-id="47b75-116">Należy określić tylko jeden z `filename` lub `pIStream` parametrów, nie obu.</span><span class="sxs-lookup"><span data-stu-id="47b75-116">You need to specify only one of the `filename` or the `pIStream` parameters, not both.</span></span> <span data-ttu-id="47b75-117">Parametr `searchPath` jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="47b75-117">The `searchPath` parameter is optional.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47b75-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="47b75-118">Requirements</span></span>  
 <span data-ttu-id="47b75-119">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="47b75-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47b75-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="47b75-120">See also</span></span>

- [<span data-ttu-id="47b75-121">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="47b75-121">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
