---
title: -out (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
ms.openlocfilehash: 5dcf9dc5cc0987e965aba7fd2b8821252e19a655
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58815995"
---
# <a name="-out-visual-basic"></a>-out (Visual Basic)
Określa nazwę pliku wyjściowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
-out:filename  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`filename`|Wymagana. Nazwa pliku wyjściowego, kompilator tworzy. Jeśli nazwa pliku zawiera spację, nazwę należy ująć w znaki cudzysłowu ("").|  
  
## <a name="remarks"></a>Uwagi  
 Podaj pełną nazwę i rozszerzenie pliku do utworzenia. Jeśli tego nie zrobisz, plik .exe przyjmuje nazwy z kodu źródłowego pliku zawierającego `Sub Main` procedury i plik .dll pobiera jego nazwę pierwszego pliku kodu źródłowego.  
  
 Jeśli określisz nazwę pliku bez rozszerzenia .exe lub .dll, kompilator automatycznie dodaje rozszerzenia, w zależności od wartości określonej dla `-target` — opcja kompilatora.  
  
|Aby ustawić - out w programie Visual Studio zintegrowanego środowiska programistycznego|  
|---|  
|1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**. <br />2.  Kliknij przycisk **aplikacji** kartę.<br />3.  Zmodyfikuj wartość w **nazwy zestawu** pole.|  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `T2.vb` i tworzy plik wyjściowy `T2.exe`.  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
