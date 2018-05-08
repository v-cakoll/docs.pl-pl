---
title: Storeadm.exe (Narzędzie wydzielonej pamięci masowej)
ms.date: 03/30/2017
helpviewer_keywords:
- Storeadm.exe
- listing stores for current user
- Isolated Storage tool
- stores, current user
- removing stores
ms.assetid: b81202b8-d91d-4b23-9c53-4a112f74a44a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3c9b8d0680a50d9945bef0d03d10e45750fc49a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="storeadmexe-isolated-storage-tool"></a>Storeadm.exe (Narzędzie wydzielonej pamięci masowej)
Narzędzie Isolated Storage obsługujące izolowane magazyny wyświetla lub usuwa wszystkie istniejące magazyny bieżącego użytkownika.  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, należy użyć wiersza polecenia dewelopera (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```  
storeadm [/list][/machine][/remove][/roaming][/quiet]  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/h**[**elp**]|Wyświetla składnię polecenia i opcje narzędzia.|  
|**/ list**|Wyświetla wszystkie istniejące magazyny bieżącego użytkownika. W tym magazyny dla wszystkich aplikacji lub zespołów wykonanych przez tego użytkownika.|  
|**/ Machine**|Wybiera magazyn komputera. Użyj tej opcji z **/list** lub **lub usuwanie** opcję, aby określić stosowanie akcji w magazynie komputera.<br /><br /> Nowość w programie .NET Framework 2.0|  
|**/quiet**|Określa tryb cichy; pomija informacyjne dane wyjściowe, tak aby były wyświetlane tylko komunikaty o błędach.|  
|**/ Remove**|Trwale usuwa wszystkie istniejące magazyny bieżącego użytkownika.|  
|**/ mobilnego**|Wybiera mobilny magazyn. Użyj tej opcji z **/list** lub **lub usuwanie** opcji, aby określić stosowanie akcji mobilnego magazynu.|  
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|  
  
## <a name="remarks"></a>Uwagi  
 Uruchamianie Storeadm.exe z wiersza polecenia bez określenia opcji wyświetla składnię i opcje narzędzia.  
  
 **/List** i **lub usuwanie** opcje są zazwyczaj używane pojedynczo; jednak jeśli nie określono co najmniej dwie opcje one zostanie wykonany w kolejności, w jakiej występują w wierszu polecenia.  
  
 Aplikacje można zapisać do jednego z dwóch magazynów użytkownika lub do magazynu komputera:  
  
-   Lokalny magazyn istnieje w lokalizacji, która może nie są przekazywane (w systemie Windows 2000 lub nowszym), nawet jeśli roaming danych użytkownika jest włączone dla użytkownika.  
  
-   Mobilny magazyn istnieje w lokalizacji, która jest w stanie korzystać z roamingu, ale tylko zrobić po włączeniu roamingu dla użytkownika za pośrednictwem administracji systemu Windows NT.  
  
-   Magazyn komputera jest wspólny dla wszystkich użytkowników komputera i jest przechowywany we wspólnym katalogu na tym komputerze.  
  
    > [!NOTE]
    >  Magazyn komputera jest nowy w programie .NET Framework w wersji 2.0.  
  
 To, czy roaming jest faktycznie włączony dla użytkownika, nie wpływa na administrację Storeadm.exe. Uruchomienie narzędzia bez żadnych opcji zastosuje wszystkie akcje do magazynu lokalnego. Uruchomienie narzędzia z **/ mobilnego** opcja dotyczy wszystkich akcji w magazynie, który jest w stanie korzystać z roamingu. Uruchomienie narzędzia z **/maszyny** opcja dotyczy wszystkich akcji w magazynie komputera.  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia](../../../docs/framework/tools/index.md)  
 [Wydzielona pamięć masowa](../../../docs/standard/io/isolated-storage.md)  
 [Wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
