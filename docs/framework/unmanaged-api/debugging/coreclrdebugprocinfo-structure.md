---
title: "CoreClrDebugProcInfo — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CoreClrDebugProcInfo
api_location: mscordbi_macx86.dll
api_type: COM
f1_keywords: CoreClrDebugProcInfo
helpviewer_keywords:
- remote debugging API [Silverlight]
- CoreClrDebugProcInfo structure
- Silverlight, remote debugging
ms.assetid: 4ddc37da-5c94-4beb-b61c-b54071c0e749
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 53616fb8e947d2a301dcfcb4e3870a9a9dc36ec1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="coreclrdebugprocinfo-structure"></a>CoreClrDebugProcInfo — Struktura
Reprezentuje proces, który jest uruchomiony na komputerze zdalnym.  
  
## <a name="syntax"></a>Składnia  
  
```  
struct  CoreClrDebugProcInfo {  
    DWORD m_dwPID;  
    DWORD m_dwInternalID;  
    WCHAR m_wszName[256];  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`m_dwPID`|Identyfikator procesu przypisane systemu operacyjnego.|  
|`m_dwInternalID`|Identyfikator procesu, który jest przypisany przez serwer proxy debugowania zdalnego uruchomiona na komputerze docelowym. Ten identyfikator jest odtwarzana częściej niż identyfikator systemu operacyjnego.|  
|`m_wszName`|Wiersza polecenia procesu. Ten element członkowski może zostać obcięty.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CoreClrRemoteDebuggingInterfaces.h  
  
 **Biblioteka:** mscordbi_macx86.dll  
  
 **Wersje programu .NET framework:** 3.5 z dodatkiem SP1
