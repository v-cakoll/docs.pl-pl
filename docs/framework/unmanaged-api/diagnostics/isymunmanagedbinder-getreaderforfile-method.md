---
title: ISymUnmanagedBinder::GetReaderForFile — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder.GetReaderForFile
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder::GetReaderForFile
helpviewer_keywords:
- ISymUnmanagedBinder::GetReaderForFile method [.NET Framework debugging]
- GetReaderForFile method [.NET Framework debugging]
ms.assetid: 46c06258-831e-47c8-a50a-8650af6b637e
topic_type:
- apiref
ms.openlocfilehash: 94cda16466ea5a3d35a478a2ae80281e9414f719
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449360"
---
# <a name="isymunmanagedbindergetreaderforfile-method"></a><span data-ttu-id="ef712-102">ISymUnmanagedBinder::GetReaderForFile — Metoda</span><span class="sxs-lookup"><span data-stu-id="ef712-102">ISymUnmanagedBinder::GetReaderForFile Method</span></span>
<span data-ttu-id="ef712-103">Podanym interfejsem metadanych i nazwą pliku zwraca poprawny interfejs [ISymUnmanagedReader](isymunmanagedreader-interface.md) , który odczytuje symbole debugowania skojarzone z modułem.</span><span class="sxs-lookup"><span data-stu-id="ef712-103">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="ef712-104">Ta metoda spowoduje otwarcie pliku bazy danych programu (PDB) tylko wtedy, gdy znajduje się obok pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="ef712-104">This method will open the program database (PDB) file only if it is next to the executable file.</span></span> <span data-ttu-id="ef712-105">Ta zmiana została wprowadzona ze względów bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="ef712-105">This change has been made for security purposes.</span></span> <span data-ttu-id="ef712-106">Jeśli potrzebujesz bardziej szczegółowego wyszukiwania pliku PDB, użyj metody [ISymUnmanagedBinder2:: GetReaderForFile2 —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ef712-106">If you need a more extensive search for the PDB file, use the [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef712-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="ef712-107">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderForFile(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [out, retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef712-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="ef712-108">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="ef712-109">podczas Wskaźnik do interfejsu importowania metadanych.</span><span class="sxs-lookup"><span data-stu-id="ef712-109">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="ef712-110">podczas Wskaźnik do nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="ef712-110">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="ef712-111">podczas Wskaźnik do ścieżki wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="ef712-111">[in] A pointer to the search path.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="ef712-112">określoną Wskaźnik, który jest ustawiony na zwracany Interfejs [ISymUnmanagedReader](isymunmanagedreader-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="ef712-112">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ef712-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ef712-113">Return Value</span></span>  
 <span data-ttu-id="ef712-114">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="ef712-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef712-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ef712-115">Requirements</span></span>  
 <span data-ttu-id="ef712-116">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="ef712-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef712-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ef712-117">See also</span></span>

- [<span data-ttu-id="ef712-118">ISymUnmanagedBinder, interfejs</span><span class="sxs-lookup"><span data-stu-id="ef712-118">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
- [<span data-ttu-id="ef712-119">GetReaderForFile2, metoda</span><span class="sxs-lookup"><span data-stu-id="ef712-119">GetReaderForFile2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)
