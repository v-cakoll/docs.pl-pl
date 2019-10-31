---
title: CorFlags.exe (Narzędzie konwersji CorFlags)
ms.date: 03/30/2017
helpviewer_keywords:
- CorFlags conversion tool
- CorFlags.exe
- portable executable files, CorFlags section
ms.assetid: ef900f8f-71ca-4dde-9b8c-95ddb0d7d89c
ms.openlocfilehash: e1251b6660db45f3af4f6e57114b1b10da18bd0a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129860"
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
|:------------|-----------------|  
|`-32BIT[REQ]+`|Ustawia flagę 32BITREQUIRED.|  
|`-32BIT[REQ]-`|Czyści flagę 32BITREQUIRED.|  
|`-32BITPREF+`|Ustawia flagę 32BITPREFERRED. Aplikacja działa jako proces 32-bitowy nawet na platformach 64-bitowych. Należy ustawić tą flagę tylko dla plików EXE. Jeśli flaga jest ustawiona dla biblioteki DLL, nie można załadować biblioteki DLL w procesach 64-bitowych i zostanie zgłoszony wyjątek <xref:System.BadImageFormatException>. Plik EXE z tą flagą może być załadowany do procesu 64-bitowego.<br /><br /> Nowość w .NET Framework 4,5.|  
|`-32BITPREF-`|Czyści flagę 32BITPREFERRED.<br /><br /> Nowość w .NET Framework 4,5.|  
|`-?`|Wyświetla składnię polecenia i opcje narzędzia.|  
|`-Force`|Wymusza aktualizację, nawet jeśli jest to zestaw z silną nazwą. **Ważne:**  W przypadku aktualizowania zestawu o silnej nazwie należy podpisać go ponownie przed wykonaniem kodu.|  
|`-help`|Wyświetla składnię polecenia i opcje narzędzia.|  
|`-ILONLY+`|Ustawia flagę ILONLY.|  
|`-ILONLY-`|Czyści flagę ILONLY.|  
|`-nologo`|Pomija wyświetlanie transparentu startowego firmy Microsoft.|  
|`-RevertCLRHeader`|Przywraca wersję nagłówka do CLR 2.0.|  
|`-UpgradeCLRHeader`|Uaktualnienia wersję nagłówka CLR do 2.5. **Uwaga:**  Zestawy muszą mieć wersję nagłówka CLR równą 2,5 lub większą do uruchomienia natywnie.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli nie określono opcji, narzędzie konwersji CorFlags wyświetla flagi dla określonego zestawu.  
  
## <a name="see-also"></a>Zobacz także

- [Narzędzia](index.md)
- [Aplikacje 64-bitowe](../64-bit-apps.md)
- [Wiersze polecenia](developer-command-prompt-for-vs.md)
