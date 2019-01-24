---
title: -pdb (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /pdb
helpviewer_keywords:
- -pdb compiler option [C#]
- pdb compiler option [C#]
- /pdb compiler option [C#]
ms.assetid: e9d0f96a-5b75-45d6-9765-92538dd5f823
ms.openlocfilehash: b0a566931ac76a3adb191f423a497bc446e280c8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54575505"
---
# <a name="-pdb-c-compiler-options"></a>-pdb (opcje kompilatora C#)
**- Pdb** — opcja kompilatora Określa nazwę i lokalizację pliku symboli debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-pdb:filename  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Nazwa i lokalizacja pliku symboli debugowania.  
  
## <a name="remarks"></a>Uwagi  
 Po określeniu [-debug (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/debug-compiler-option.md), kompilator utworzy plik .pdb w tym samym katalogu, gdzie kompilator utworzy plik wyjściowy (.exe lub .dll) przy użyciu nazwy pliku, która jest taka sama jak nazwa pliku wyjściowego.  
  
 **-pdb** służy do określania plików innych niż domyślne nazwę i lokalizację pliku .pdb.  
  
 Nie można ustawić tę opcję kompilatora w środowisku programowania Visual Studio i nie można go zmienić programowo.  
  
## <a name="example"></a>Przykład  
 Skompilować `t.cs` i tworzenie pliku .pdb o nazwie tt.pdb:  
  
```console  
csc -debug -pdb:tt t.cs  
```  
  
## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
