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
ms.openlocfilehash: b420fb451bf1bb2078a4419a648a1407c39ad178
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044738"
---
# <a name="corflagsexe-corflags-conversion-tool"></a>CorFlags.exe (Narzędzie konwersji CorFlags)
Narzędzie do konwersji CorFlags pozwala na konfigurowanie sekcji CorFlags w nagłówku przenośnego obrazu wykonywalnego.  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, użyj wiersz polecenia dla deweloperów dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [wiersza polecenia](developer-command-prompt-for-vs.md).  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```console  
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
|**/32BITPREF +**|Ustawia flagę 32BITPREFERRED. Aplikacja działa jako proces 32-bitowy nawet na platformach 64-bitowych. Należy ustawić tą flagę tylko dla plików EXE. Jeśli flaga jest ustawiona dla biblioteki DLL, nie można załadować biblioteki DLL w procesach 64-bitowych i <xref:System.BadImageFormatException> zgłaszany jest wyjątek. Plik EXE z tą flagą może być załadowany do procesu 64-bitowego.<br /><br /> Nowość w .NET Framework 4,5.|  
|**/32BITPREF-**|Czyści flagę 32BITPREFERRED.<br /><br /> Nowość w .NET Framework 4,5.|  
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|  
|**/Force**|Wymusza aktualizację, nawet jeśli jest to zestaw z silną nazwą. **Ważne:**  Jeżeli zestaw o silnej nazwie zostanie zaktualizowany, należy podpisać go ponownie przed wykonaniem jego kodu.|  
|**/help**|Wyświetla składnię polecenia i opcje narzędzia.|  
|**/ILONLY +**|Ustawia flagę ILONLY.|  
|**ILONLY**|Czyści flagę ILONLY.|  
|**/nologo**|Pomija wyświetlanie transparentu startowego firmy Microsoft.|  
|**/RevertCLRHeader**|Przywraca wersję nagłówka do CLR 2.0.|  
|**/UpgradeCLRHeader**|Uaktualnienia wersję nagłówka CLR do 2.5. **Uwaga:**  Aby zestaw mógł być uruchomiony natywnie, musi mieć wersję nagłówka CLR 2.5 lub wyższą.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli nie określono opcji, narzędzie konwersji CorFlags wyświetla flagi dla określonego zestawu.  
  
## <a name="see-also"></a>Zobacz także

- [Narzędzia](index.md)
- [Aplikacje 64-bitowe](../64-bit-apps.md)
- [Wiersze polecenia](developer-command-prompt-for-vs.md)
