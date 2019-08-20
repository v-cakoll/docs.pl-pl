---
title: -PDB (C# opcje kompilatora)
ms.date: 07/20/2015
f1_keywords:
- /pdb
helpviewer_keywords:
- -pdb compiler option [C#]
- pdb compiler option [C#]
- /pdb compiler option [C#]
ms.assetid: e9d0f96a-5b75-45d6-9765-92538dd5f823
ms.openlocfilehash: 3081f4716e8cd858d789db6050e635af941aa05c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602576"
---
# <a name="-pdb-c-compiler-options"></a>-PDB (C# opcje kompilatora)
**-PDB —** opcja kompilatora określa nazwę i lokalizację pliku symboli debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-pdb:filename  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Nazwa i lokalizacja pliku symboli debugowania.  
  
## <a name="remarks"></a>Uwagi  
 Gdy określisz polecenie [-DebugC# (opcje kompilatora)](./debug-compiler-option.md), kompilator utworzy plik. pdb w tym samym katalogu, w którym kompilator utworzy plik wyjściowy (. exe lub. dll) z nazwą pliku, która jest taka sama jak nazwa pliku wyjściowego.  
  
 **-PDB** umożliwia określenie niedomyślnej nazwy pliku i lokalizacji dla pliku. pdb.  
  
 Nie można ustawić tej opcji kompilatora w środowisku deweloperskim programu Visual Studio, ani programowo zmienić.  
  
## <a name="example"></a>Przykład  
 Kompiluj `t.cs` i Utwórz plik. pdb o nazwie TT. pdb:  
  
```console  
csc -debug -pdb:tt t.cs  
```  
  
## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](./index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
