---
title: ISymENCUnmanagedMethod::GetFileNameFromOffset — Metoda
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetFileNameFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetFileNameFromOffset
helpviewer_keywords:
- GetFileNameFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetFileNameFromOffset method [.NET Framework debugging]
ms.assetid: 00e2e194-12f5-436e-a997-2b9d3e844d4f
topic_type:
- apiref
ms.openlocfilehash: 857410187edf1c712865626a3327dd4c92cc211f
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441932"
---
# <a name="isymencunmanagedmethodgetfilenamefromoffset-method"></a><span data-ttu-id="91c23-102">ISymENCUnmanagedMethod::GetFileNameFromOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="91c23-102">ISymENCUnmanagedMethod::GetFileNameFromOffset Method</span></span>
<span data-ttu-id="91c23-103">Pobiera nazwę pliku dla wiersza skojarzonego z przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="91c23-103">Gets the file name for the line associated with an offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91c23-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="91c23-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFileNameFromOffset(  
    [in]  ULONG32  dwOffset,  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
       length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91c23-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="91c23-105">Parameters</span></span>  
 `dwOffset`  
 <span data-ttu-id="91c23-106">podczas A `ULONG32` , który zawiera przesunięcie.</span><span class="sxs-lookup"><span data-stu-id="91c23-106">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `cchName`  
 <span data-ttu-id="91c23-107">podczas `ULONG32`Wskazuje rozmiar `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="91c23-107">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="91c23-108">określoną Wskaźnik do obiektu, `ULONG32` który odbiera rozmiar (w znakach) bufora wymaganego do przechowywania nazw plików.</span><span class="sxs-lookup"><span data-stu-id="91c23-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the file names.</span></span>  
  
 `szName`  
 <span data-ttu-id="91c23-109">określoną Bufor zawierający nazwy plików.</span><span class="sxs-lookup"><span data-stu-id="91c23-109">[out] The buffer that contains the file names.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="91c23-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="91c23-110">Return Value</span></span>  
 <span data-ttu-id="91c23-111">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="91c23-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91c23-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="91c23-112">Requirements</span></span>  
 <span data-ttu-id="91c23-113">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="91c23-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91c23-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="91c23-114">See also</span></span>

- [<span data-ttu-id="91c23-115">ISymENCUnmanagedMethod — Interfejs</span><span class="sxs-lookup"><span data-stu-id="91c23-115">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)
