---
title: /out (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 53b77dec53be1d97c5f2526cb117933a2b8fe046
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="out-visual-basic"></a>/out (Visual Basic)
Określa nazwę pliku wyjściowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
/out:filename  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`filename`|Wymagany. Nazwa pliku wyjściowego, który tworzy kompilatora. Jeśli nazwa pliku zawiera spację, nazwę należy ująć w cudzysłów ("").|  
  
## <a name="remarks"></a>Uwagi  
 Określ pełną nazwę i rozszerzenie pliku do utworzenia. Jeśli nie chcesz, plik .exe przyjmuje nazwy z kodu źródłowego pliku zawierającego `Sub Main` procedury i pliku dll pobiera jego nazwa pierwszego pliku kodu źródłowego.  
  
 Określ nazwę pliku bez rozszerzenia .exe lub dll, kompilator automatycznie dodaje rozszerzenia, w zależności od wartości określonej dla `/target` — opcja kompilatora.  
  
|Aby ustawić/out w programie Visual Studio zintegrowane środowisko deweloperskie|  
|---|  
|1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**. <br />2.  Kliknij przycisk **aplikacji** kartę.<br />3.  Zmodyfikuj wartość w **nazwy zestawu** pole.|  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `T2.vb` i tworzy plik wyjściowy `T2.exe`.  
  
```  
vbc t2.vb /out:t3.exe  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/ TARGET (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
