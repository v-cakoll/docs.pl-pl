---
title: -pdb (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /pdb
helpviewer_keywords:
- -pdb compiler option [C#]
- pdb compiler option [C#]
- /pdb compiler option [C#]
ms.assetid: e9d0f96a-5b75-45d6-9765-92538dd5f823
caps.latest.revision: "8"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 108244d7de49c2ff4df1ac7202e77958743b32df
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="pdb-c-compiler-options"></a>/pdb (opcje kompilatora C#)
**/PDB** — opcja kompilatora Określa nazwę i lokalizację pliku symboli debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```console  
/pdb:filename  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Nazwa i lokalizacja pliku symboli debugowania.  
  
## <a name="remarks"></a>Uwagi  
 Po określeniu [/Debug (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/debug-compiler-option.md), kompilator utworzy plik PDB w tym samym katalogu, gdy kompilator spowoduje utworzenie pliku wyjściowego (.exe lub .dll) przy użyciu nazwy pliku, która jest taka sama jak nazwa pliku wyjściowego.  
  
 **/ PDB** można określić innych niż domyślna nazwa pliku i lokalizację pliku PDB.  
  
 Tej opcji kompilatora nie można ustawić w środowisku programowania Visual Studio i nie można go zmienić programowo.  
  
## <a name="example"></a>Przykład  
 Kompiluj `t.cs` i Utwórz plik PDB o nazwie tt.pdb:  
  
```console  
csc /debug /pdb:tt t.cs  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
