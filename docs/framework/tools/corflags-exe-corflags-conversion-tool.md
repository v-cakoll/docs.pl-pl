---
title: "CorFlags.exe (Narzędzie konwersji CorFlags)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CorFlags conversion tool
- CorFlags.exe
- portable executable files, CorFlags section
ms.assetid: ef900f8f-71ca-4dde-9b8c-95ddb0d7d89c
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ca3e9dbe5578623ccc67898c6f08213c31ad8e23
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="corflagsexe-corflags-conversion-tool"></a>CorFlags.exe (Narzędzie konwersji CorFlags)
Narzędzie do konwersji CorFlags pozwala na konfigurowanie sekcji CorFlags w nagłówku przenośnego obrazu wykonywalnego.  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, należy użyć wiersza polecenia dewelopera (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```  
CorFlags.exe assembly [options]  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Wymagany parametr|Opis|  
|------------------------|-----------------|  
|`assembly`|Nazwa zestawu, dla którego chcesz skonfigurować CorFlags.|  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/ 32-BITOWE [WYMAGANE] +**|Ustawia flagę 32BITREQUIRED.|  
|**/ 32-BITOWE [WYMAGANE]-**|Czyści flagę 32BITREQUIRED.|  
|**/32BITPREF+**|Ustawia flagę 32BITPREFERRED. Aplikacja działa jako proces 32-bitowy nawet na platformach 64-bitowych. Należy ustawić tą flagę tylko dla plików EXE. Jeśli flaga jest ustawiona na bibliotekę DLL, biblioteki DLL nie udało się załadować w 64-bitowych procesów i <xref:System.BadImageFormatException> wyjątku. Plik EXE z tą flagą może być załadowany do procesu 64-bitowego.<br /><br /> Nowość w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].|  
|**/32BITPREF-**|Czyści flagę 32BITPREFERRED.<br /><br /> Nowość w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].|  
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|  
|**/ Force**|Wymusza aktualizację, nawet jeśli jest to zestaw z silną nazwą. **Ważne:** po zaktualizowaniu zestawu z silną nazwą, musisz zarejestrować go ponownie przed wykonaniem jego kodu.|  
|**/ Help**|Wyświetla składnię polecenia i opcje narzędzia.|  
|**/ILONLY+**|Ustawia flagę ILONLY.|  
|**/ILONLY-**|Czyści flagę ILONLY.|  
|**/ nologo**|Pomija wyświetlanie transparentu startowego firmy Microsoft.|  
|**/ RevertCLRHeader**|Przywraca wersję nagłówka do CLR 2.0.|  
|**/ UpgradeCLRHeader**|Uaktualnienia wersję nagłówka CLR do 2.5. **Uwaga:** zestawy muszą mieć CLR nagłówkiem w wersji 2.5 lub nowszej do działania.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli nie określono opcji, narzędzie konwersji CorFlags wyświetla flagi dla określonego zestawu.  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia](../../../docs/framework/tools/index.md)  
 [64-bit — aplikacje](../../../docs/framework/64-bit-apps.md)  
 [Wiersz polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
