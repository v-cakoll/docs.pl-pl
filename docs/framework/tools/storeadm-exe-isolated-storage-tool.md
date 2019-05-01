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
ms.openlocfilehash: 906d9d4dfd1c1082a4b49b7143f590967dcc7fd0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61919378"
---
# <a name="storeadmexe-isolated-storage-tool"></a>Storeadm.exe (Narzędzie wydzielonej pamięci masowej)
Narzędzie Isolated Storage obsługujące izolowane magazyny wyświetla lub usuwa wszystkie istniejące magazyny bieżącego użytkownika.  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, należy użyć wiersz polecenia programisty dla programu Visual Studio (lub wiersza polecenia programu Visual Studio Windows 7). Aby uzyskać więcej informacji, zobacz [wiersz polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```  
storeadm [/list][/machine][/remove][/roaming][/quiet]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/ h**[**elp**]|Wyświetla składnię polecenia i opcje narzędzia.|  
|**/ list**|Wyświetla wszystkie istniejące magazyny bieżącego użytkownika. W tym magazyny dla wszystkich aplikacji lub zespołów wykonanych przez tego użytkownika.|  
|**/ machine**|Wybiera magazyn komputera. Użyj tej opcji z **/list** lub **/usunąć** opcję, aby określić, czy akcja ma mieć zastosowanie do magazynu komputera.<br /><br /> Nowość w programie .NET Framework 2.0|  
|**/quiet**|Określa tryb cichy; pomija informacyjne dane wyjściowe, tak aby były wyświetlane tylko komunikaty o błędach.|  
|**/remove**|Trwale usuwa wszystkie istniejące magazyny bieżącego użytkownika.|  
|**/ roaming**|Wybiera mobilny magazyn. Użyj tej opcji z **/list** lub **/usunąć** opcji, aby określić, czy akcja ma mieć zastosowanie do mobilnego magazynu.|  
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|  
  
## <a name="remarks"></a>Uwagi  
 Uruchamianie Storeadm.exe z wiersza polecenia bez określenia opcji wyświetla składnię i opcje narzędzia.  
  
 **/List** i **/usunąć** opcje są zwykle używane pojedynczo; Jednakże, jeśli nie określono dwie lub więcej opcji one wykonywane w kolejności, w jakiej są wyświetlane w wierszu polecenia.  
  
 Aplikacje można zapisać do jednego z dwóch magazynów użytkownika lub do magazynu komputera:  
  
- Magazyn lokalny istnieje w lokalizacji, która może się nie korzystać z roamingu (w systemie operacyjnym Windows 2000 i nowszych), nawet jeśli roaming danych jest włączone dla danego użytkownika.  
  
- Mobilny magazyn istnieje w lokalizacji, która jest w stanie korzystać z roamingu, ale tylko w przypadku, gdy roaming jest włączony dla użytkownika za pośrednictwem administracji systemu Windows NT.  
  
- Magazyn komputera jest wspólny dla wszystkich użytkowników komputera i jest przechowywany we wspólnym katalogu na tym komputerze.  
  
    > [!NOTE]
    >  Magazyn komputera jest nowy w programie .NET Framework w wersji 2.0.  
  
 To, czy roaming jest faktycznie włączony dla użytkownika, nie wpływa na administrację Storeadm.exe. Uruchomienie narzędzia bez żadnych opcji zastosuje wszystkie akcje do magazynu lokalnego. Uruchomienie narzędzia z **/ roaming** opcji zastosuje wszystkie akcje do magazynu który może korzystać z roamingu. Uruchomienie narzędzia z **/machine** opcji zastosuje wszystkie akcje do magazynu komputera.  
  
## <a name="see-also"></a>Zobacz także

- [Narzędzia](../../../docs/framework/tools/index.md)
- [Wydzielona pamięć masowa](../../../docs/standard/io/isolated-storage.md)
- [Wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
