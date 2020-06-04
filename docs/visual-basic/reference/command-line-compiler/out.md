---
title: -out
ms.date: 07/20/2015
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
ms.openlocfilehash: 75f3ee7f24112f911803732ccb8d39eeafa95e3d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400516"
---
# <a name="-out-visual-basic"></a>-out (Visual Basic)
Określa nazwę pliku wyjściowego.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`filename`|Wymagany. Nazwa pliku wyjściowego tworzonego przez kompilator. Jeśli nazwa pliku zawiera spację, należy ująć ją w cudzysłów ("").|  
  
## <a name="remarks"></a>Uwagi  
 Określ pełną nazwę i rozszerzenie pliku do utworzenia. W przeciwnym razie plik. exe przyjmuje swoją nazwę z pliku kodu źródłowego zawierającego `Sub Main` procedurę, a plik. dll przyjmuje jego nazwę z pierwszego pliku kodu źródłowego.  
  
 Jeśli określisz nazwę pliku bez rozszerzenia exe lub dll, kompilator automatycznie doda rozszerzenie dla Ciebie, w zależności od wartości określonej dla `-target` opcji kompilatora.  
  
|Aby skonfigurować w zintegrowanym środowisku programistycznym programu Visual Studio|  
|---|  
|1. zaznaczono projekt w **Eksplorator rozwiązań**. W menu **projekt** kliknij polecenie **Właściwości**. <br />2. Kliknij kartę **aplikacja** .<br />3. Zmodyfikuj wartość w polu **Nazwa zestawu** .|  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `T2.vb` i tworzy plik wyjściowy `T2.exe` .  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a>Zobacz też

- [Kompilator wiersza polecenia Visual Basic](index.md)
- [-Target (Visual Basic)](target.md)
- [Przykłady kompilacji — wiersze poleceń](sample-compilation-command-lines.md)
