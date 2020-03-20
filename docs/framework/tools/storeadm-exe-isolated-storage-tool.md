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
ms.openlocfilehash: 46e846eaf92835fb2a9130b85ed20749934ca5a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75715712"
---
# <a name="storeadmexe-isolated-storage-tool"></a>Storeadm.exe (Narzędzie wydzielonej pamięci masowej)
Narzędzie Isolated Storage obsługujące izolowane magazyny wyświetla lub usuwa wszystkie istniejące magazyny bieżącego użytkownika.  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, użyj wiersza polecenia dewelopera dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [Wiersze poleceń](developer-command-prompt-for-vs.md).  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```console  
storeadm [/list][/machine][/remove][/roaming][/quiet]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/h**[**elp**]|Wyświetla składnię polecenia i opcje narzędzia.|  
|**/lista**|Wyświetla wszystkie istniejące magazyny bieżącego użytkownika. W tym magazyny dla wszystkich aplikacji lub zespołów wykonanych przez tego użytkownika.|  
|**/maszyna**|Wybiera magazyn komputera. Użyj tej opcji z **/list** lub **/remove** opcji, aby określić, że akcja powinna mieć zastosowanie do magazynu komputera.<br /><br /> Nowość w programie .NET Framework 2.0|  
|**/cichy**|Określa tryb cichy; pomija informacyjne dane wyjściowe, tak aby były wyświetlane tylko komunikaty o błędach.|  
|**/usuń**|Trwale usuwa wszystkie istniejące magazyny bieżącego użytkownika.|  
|**/roaming**|Wybiera mobilny magazyn. Użyj tej opcji z **/list** lub **/remove** opcje, aby określić, że akcja powinna mieć zastosowanie do magazynu mobilnego.|  
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|  
  
## <a name="remarks"></a>Uwagi  
 Uruchamianie Storeadm.exe z wiersza polecenia bez określenia opcji wyświetla składnię i opcje narzędzia.  
  
 Opcje **/list** i **/remove** są zwykle używane po jednym naraz; jednak jeśli określono dwie lub więcej opcji, zostaną one wykonane w kolejności, w jakiej pojawiają się w wierszu polecenia.  
  
 Aplikacje można zapisać do jednego z dwóch magazynów użytkownika lub do magazynu komputera:  
  
- Lokalny magazyn istnieje w lokalizacji, która jest gwarantowana, aby nie wędrować (w systemie Windows 2000 i nowszych), nawet jeśli roaming danych użytkownika jest włączony dla użytkownika.  
  
- Sklep mobilny istnieje w lokalizacji, która może się przemieszczać, ale może to zrobić tylko wtedy, gdy roaming jest włączony dla użytkownika za pośrednictwem administracji systemu Windows NT.  
  
- Magazyn komputera jest wspólny dla wszystkich użytkowników komputera i jest przechowywany we wspólnym katalogu na tym komputerze.  
  
    > [!NOTE]
    > Magazyn komputera jest nowy w programie .NET Framework w wersji 2.0.  
  
 To, czy roaming jest faktycznie włączony dla użytkownika, nie wpływa na administrację Storeadm.exe. Uruchomienie narzędzia bez żadnych opcji zastosuje wszystkie akcje do magazynu lokalnego. Uruchomienie narzędzia z opcją **/roaming** stosuje wszystkie akcje do magazynu, który jest w stanie wędrować. Uruchamianie narzędzia za pomocą opcji **/machine** powoduje zastosowanie wszystkich akcji do magazynu maszyn.  
  
## <a name="see-also"></a>Zobacz też

- [narzędzia](index.md)
- [Izolowany magazyn](../../standard/io/isolated-storage.md)
- [Wiersz polecenia](developer-command-prompt-for-vs.md)
