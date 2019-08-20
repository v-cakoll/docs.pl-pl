---
title: -rekursywnie (C# opcje kompilatora)
ms.date: 07/20/2015
f1_keywords:
- /recurse
helpviewer_keywords:
- /recurse compiler option [C#]
- recurse compiler option [C#]
- -recurse compiler option [C#]
ms.assetid: 4e8212e5-04e3-45b1-8a42-41bc50e683b0
ms.openlocfilehash: c82e3019e1a1e3ba45a7000312b54b9d7f64a2db
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606739"
---
# <a name="-recurse-c-compiler-options"></a>-rekursywnie (C# opcje kompilatora)
Opcja-rekursywnie umożliwia skompilowanie plików kodu źródłowego we wszystkich katalogach podrzędnych określonego katalogu (dir) lub katalogu projektu.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a>Argumenty  
 `dir`obowiązkowe  
 Katalog, w którym ma zostać rozpoczęte wyszukiwanie. Jeśli ta wartość nie jest określona, wyszukiwanie rozpoczyna się w katalogu projektu.  
  
 `file`  
 Pliki do wyszukania. Symbole wieloznaczne są dozwolone.  
  
## <a name="remarks"></a>Uwagi  
 Opcja **-** rekursywnie umożliwia skompilowanie plików kodu źródłowego we wszystkich katalogach podrzędnych określonego katalogu (`dir`) lub katalogu projektu.  
  
 W nazwie pliku można użyć symboli wieloznacznych, aby skompilować wszystkie zgodne pliki w katalogu projektu bez użycia opcji **-** rekursywnie.  
  
 Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można jej zmienić programowo.  
  
## <a name="example"></a>Przykład  
 Kompiluje wszystkie C# pliki w bieżącym katalogu:  
  
```console  
csc *.cs  
```  
  
 Kompiluje wszystkie pliki w C# katalogu dir1\dir2 i wszystkie znajdujące się w nim katalogi i generuje dir2. dll:  
  
```console  
csc -target:library -out:dir2.dll -recurse:dir1\dir2\*.cs  
```  
  
## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](./index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
