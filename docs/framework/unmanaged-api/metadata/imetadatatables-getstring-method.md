---
title: IMetaDataTables::GetString — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetString
helpviewer_keywords:
- IMetaDataTables::GetString method [.NET Framework metadata]
- GetString method, IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 895c35cf-b95d-4e3b-93b5-cfc1cf9044fc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3ed3501930b94eae59cf38355f8255ecf4165bcc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449585"
---
# <a name="imetadatatablesgetstring-method"></a><span data-ttu-id="e1fd0-102">IMetaDataTables::GetString — Metoda</span><span class="sxs-lookup"><span data-stu-id="e1fd0-102">IMetaDataTables::GetString Method</span></span>
<span data-ttu-id="e1fd0-103">Pobiera ciąg pod określonym indeksem z kolumną tabeli w bieżącym zakresie odwołania.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-103">Gets the string at the specified index from the table column in the current reference scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1fd0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e1fd0-104">Syntax</span></span>  
  
```  
HRESULT GetString (   
    [in]  ULONG       ixString,  
    [out] const char  **ppString  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e1fd0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e1fd0-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="e1fd0-106">[in] Indeks, w którym należy uruchomić wyszukać następnej wartości.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-106">[in] The index at which to start to search for the next value.</span></span>  
  
 `ppString`  
 <span data-ttu-id="e1fd0-107">[out] Wskaźnik na wskaźnik do wartości zwracany ciąg.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-107">[out] A pointer to a pointer to the returned string value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1fd0-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e1fd0-108">Requirements</span></span>  
 <span data-ttu-id="e1fd0-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1fd0-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1fd0-110">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e1fd0-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e1fd0-111">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e1fd0-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e1fd0-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1fd0-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1fd0-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e1fd0-113">See Also</span></span>  
 [<span data-ttu-id="e1fd0-114">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="e1fd0-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="e1fd0-115">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="e1fd0-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
