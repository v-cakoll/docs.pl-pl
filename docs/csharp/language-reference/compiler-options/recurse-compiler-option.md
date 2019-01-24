---
title: -recurse (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /recurse
helpviewer_keywords:
- /recurse compiler option [C#]
- recurse compiler option [C#]
- -recurse compiler option [C#]
ms.assetid: 4e8212e5-04e3-45b1-8a42-41bc50e683b0
ms.openlocfilehash: a4a55090cf465d0eac05303392ba7500dd96ee90
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54679373"
---
# <a name="-recurse-c-compiler-options"></a>-recurse (opcje kompilatora C#)
Recurse — opcja pozwala na kompilowanie plików kodu źródłowego we wszystkich katalogach podrzędnych albo określonego katalogu (dir) lub w katalogu projektu.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a>Argumenty  
 `dir` (opcjonalnie)  
 Katalog, w którym chcesz rozpocząć wyszukiwanie. Jeśli nie zostanie określony, wyszukiwanie rozpoczyna się w katalogu projektu.  
  
 `file`  
 Pliki do wyszukania. Symbole wieloznaczne są dozwolone.  
  
## <a name="remarks"></a>Uwagi  
 **-Recurse** opcja pozwala na kompilowanie plików kodu źródłowego we wszystkich katalogach podrzędnych określonego katalogu (`dir`) lub w katalogu projektu.  
  
 Można używać symboli wieloznacznych w nazwach plików do kompilacji wszystkie odpowiednie pliki w katalogu projektu bez użycia **-recurse**.  
  
 Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można zmienić programowo.  
  
## <a name="example"></a>Przykład  
 Kompiluje wszystkie pliki C# w bieżącym katalogu:  
  
```console  
csc *.cs  
```  
  
 Kompiluje, wszystkie pliki C# w katalogu dir1\dir2 i katalogi poniżej i generuje dir2.dll:  
  
```console  
csc -target:library -out:dir2.dll -recurse:dir1\dir2\*.cs  
```  
  
## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
