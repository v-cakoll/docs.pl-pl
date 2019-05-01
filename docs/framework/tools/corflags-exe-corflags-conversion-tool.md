---
title: CorFlags.exe (Narzędzie konwersji CorFlags)
ms.date: 03/30/2017
helpviewer_keywords:
- CorFlags conversion tool
- CorFlags.exe
- portable executable files, CorFlags section
ms.assetid: ef900f8f-71ca-4dde-9b8c-95ddb0d7d89c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ee801a5af214e2306e6f1667b5e4ee067683fdb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61779980"
---
# <a name="corflagsexe-corflags-conversion-tool"></a>CorFlags.exe (Narzędzie konwersji CorFlags)
Narzędzie do konwersji CorFlags pozwala na konfigurowanie sekcji CorFlags w nagłówku przenośnego obrazu wykonywalnego.  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, należy użyć wiersz polecenia programisty dla programu Visual Studio (lub wiersza polecenia programu Visual Studio Windows 7). Aby uzyskać więcej informacji, zobacz [wiersz polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```  
CorFlags.exe assembly [options]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Wymagany parametr|Opis|  
|------------------------|-----------------|  
|`assembly`|Nazwa zestawu, dla którego chcesz skonfigurować CorFlags.|  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/32BIT[REQ]+**|Ustawia flagę 32BITREQUIRED.|  
|**/32BIT[REQ]-**|Czyści flagę 32BITREQUIRED.|  
|**/32BITPREF+**|Ustawia flagę 32BITPREFERRED. Aplikacja działa jako proces 32-bitowy nawet na platformach 64-bitowych. Należy ustawić tą flagę tylko dla plików EXE. Jeśli flaga jest ustawiona dla biblioteki dll, nie uda się jej załadować w procesach 64-bitowych i <xref:System.BadImageFormatException> wyjątku. Plik EXE z tą flagą może być załadowany do procesu 64-bitowego.<br /><br /> Nowość w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].|  
|**/32BITPREF-**|Czyści flagę 32BITPREFERRED.<br /><br /> Nowość w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].|  
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|  
|**/Force**|Wymusza aktualizację, nawet jeśli jest to zestaw z silną nazwą. **Ważne:**  Jeżeli zestaw o silnej nazwie zostanie zaktualizowany, należy podpisać go ponownie przed wykonaniem jego kodu.|  
|**/help**|Wyświetla składnię polecenia i opcje narzędzia.|  
|**/ILONLY+**|Ustawia flagę ILONLY.|  
|**/ILONLY-**|Czyści flagę ILONLY.|  
|**/nologo**|Pomija wyświetlanie transparentu startowego firmy Microsoft.|  
|**/RevertCLRHeader**|Przywraca wersję nagłówka do CLR 2.0.|  
|**/UpgradeCLRHeader**|Uaktualnienia wersję nagłówka CLR do 2.5. **Uwaga:**  Aby zestaw mógł być uruchomiony natywnie, musi mieć wersję nagłówka CLR 2.5 lub wyższą.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli nie określono opcji, narzędzie konwersji CorFlags wyświetla flagi dla określonego zestawu.  
  
## <a name="see-also"></a>Zobacz także

- [Narzędzia](../../../docs/framework/tools/index.md)
- [Aplikacje 64-bitowe](../../../docs/framework/64-bit-apps.md)
- [Wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
