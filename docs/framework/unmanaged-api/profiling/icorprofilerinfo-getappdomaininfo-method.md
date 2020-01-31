---
title: ICorProfilerInfo::GetAppDomainInfo — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetAppDomainInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetAppDomainInfo
helpviewer_keywords:
- ICorProfilerInfo::GetAppDomainInfo method [.NET Framework profiling]
- GetAppDomainInfo method [.NET Framework profiling]
ms.assetid: a6bf5a04-e03e-44f0-917a-96f6a6d3cc96
topic_type:
- apiref
ms.openlocfilehash: 0407b7057753f7fdee6ea6b1d05144b135b6378a
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864105"
---
# <a name="icorprofilerinfogetappdomaininfo-method"></a><span data-ttu-id="4d7b6-102">ICorProfilerInfo::GetAppDomainInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="4d7b6-102">ICorProfilerInfo::GetAppDomainInfo Method</span></span>
<span data-ttu-id="4d7b6-103">Akceptuje identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4d7b6-103">Accepts an application domain ID.</span></span> <span data-ttu-id="4d7b6-104">Zwraca nazwę domeny aplikacji i identyfikator procesu, który go zawiera.</span><span class="sxs-lookup"><span data-stu-id="4d7b6-104">Returns an application domain name and the ID of the process that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d7b6-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4d7b6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomainInfo(  
    [in]  AppDomainID appDomainId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] ProcessID   *pProcessId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d7b6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4d7b6-106">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="4d7b6-107">podczas Identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4d7b6-107">[in] The ID of the application domain.</span></span>  
  
 `cchName`  
 <span data-ttu-id="4d7b6-108">podczas Długość (w znakach) `szName` buforu powrotu.</span><span class="sxs-lookup"><span data-stu-id="4d7b6-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="4d7b6-109">określoną Wskaźnik do łącznej długości znaku nazwy domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4d7b6-109">[out] A pointer to the total character length of the application domain name.</span></span>  
  
 `szName`  
 <span data-ttu-id="4d7b6-110">określoną Bufor znaków udostępniany przez obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="4d7b6-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="4d7b6-111">Gdy metoda zwraca, `szName` będzie zawierać pełną lub częściową nazwę domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4d7b6-111">When the method returns, `szName` will contain the full or partial application domain name.</span></span>  
  
 `pProcessId`  
 <span data-ttu-id="4d7b6-112">określoną Wskaźnik do identyfikatora procesu, który zawiera domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4d7b6-112">[out] A pointer to the ID of the process that contains the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d7b6-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4d7b6-113">Remarks</span></span>  
 <span data-ttu-id="4d7b6-114">Po powrocie tej metody należy sprawdzić, czy bufor `szName` był wystarczająco duży, aby zawierał pełną nazwę domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4d7b6-114">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the application domain.</span></span> <span data-ttu-id="4d7b6-115">W tym celu należy porównać wartość, która `pcchName` wskazuje na wartość parametru `cchName`.</span><span class="sxs-lookup"><span data-stu-id="4d7b6-115">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="4d7b6-116">Jeśli `pcchName` wskazuje wartość, która jest większa niż `cchName`, Przydziel większy bufor `szName`, zaktualizuj `cchName` przy użyciu nowego, większego rozmiaru i ponownie wywołaj `GetAppDomainInfo`.</span><span class="sxs-lookup"><span data-stu-id="4d7b6-116">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAppDomainInfo` again.</span></span>  
  
 <span data-ttu-id="4d7b6-117">Alternatywnie można najpierw wywołać `GetAppDomainInfo` z buforem `szName` o zerowej długości, aby uzyskać prawidłowy rozmiar buforu.</span><span class="sxs-lookup"><span data-stu-id="4d7b6-117">Alternatively, you can first call `GetAppDomainInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="4d7b6-118">Następnie można ustawić rozmiar buforu na wartość zwróconą w `pcchName` i ponownie wywołać `GetAppDomainInfo`.</span><span class="sxs-lookup"><span data-stu-id="4d7b6-118">You can then set the buffer size to the value returned in `pcchName` and call `GetAppDomainInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d7b6-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4d7b6-119">Requirements</span></span>  
 <span data-ttu-id="4d7b6-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d7b6-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d7b6-121">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4d7b6-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4d7b6-122">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4d7b6-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d7b6-123">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d7b6-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d7b6-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4d7b6-124">See also</span></span>

- [<span data-ttu-id="4d7b6-125">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="4d7b6-125">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="4d7b6-126">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="4d7b6-126">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="4d7b6-127">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="4d7b6-127">Profiling</span></span>](index.md)
