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
ms.openlocfilehash: 7528283765c2b6f4a9d5e84015526a95938a6281
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
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
 Po określeniu [-debug (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/debug-compiler-option.md), kompilator utworzy plik PDB w tym samym katalogu, gdy kompilator spowoduje utworzenie pliku wyjściowego (.exe lub .dll) przy użyciu nazwy pliku, która jest taka sama jak nazwa pliku wyjściowego.  
  
 **-pdb** pozwala określić nazwę pliku innych niż domyślne i lokalizację pliku PDB.  
  
 Tej opcji kompilatora nie można ustawić w środowisku programowania Visual Studio i nie można go zmienić programowo.  
  
## <a name="example"></a>Przykład  
 Kompiluj `t.cs` i Utwórz plik PDB o nazwie tt.pdb:  
  
```console  
csc -debug -pdb:tt t.cs  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
