---
title: -pdb (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /pdb
helpviewer_keywords:
- -pdb compiler option [C#]
- pdb compiler option [C#]
- /pdb compiler option [C#]
ms.assetid: e9d0f96a-5b75-45d6-9765-92538dd5f823
ms.openlocfilehash: 3081f4716e8cd858d789db6050e635af941aa05c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602576"
---
# <a name="-pdb-c-compiler-options"></a>-pdb (Opcje kompilatora C#)
Opcja kompilatora **-pdb** określa nazwę i lokalizację pliku symboli debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-pdb:filename  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Nazwa i lokalizacja pliku symboli debugowania.  
  
## <a name="remarks"></a>Uwagi  
 Po [określeniu -debug (C# Opcje kompilatora),](./debug-compiler-option.md)kompilator utworzy plik .pdb w tym samym katalogu, w którym kompilator utworzy plik wyjściowy (.exe lub .dll) o nazwie pliku, która jest taka sama jak nazwa pliku wyjściowego.  
  
 **-pdb** umożliwia określenie niedomyślnej nazwy pliku i lokalizacji pliku pdb.  
  
 Nie można ustawić tej opcji kompilatora w środowisku programistycznym programu Visual Studio ani nie można jej programowo zmienić.  
  
## <a name="example"></a>Przykład  
 Skompiluj `t.cs` i utwórz plik pdb o nazwie tt.pdb:  
  
```console  
csc -debug -pdb:tt t.cs  
```  
  
## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora Języka C#](./index.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
