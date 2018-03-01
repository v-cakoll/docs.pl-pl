---
title: -recurse (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /recurse
helpviewer_keywords:
- /recurse compiler option [C#]
- recurse compiler option [C#]
- -recurse compiler option [C#]
ms.assetid: 4e8212e5-04e3-45b1-8a42-41bc50e683b0
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b50454112bc7aee6c3e0f8fe674e8727ca9e49be
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="-recurse-c-compiler-options"></a>-recurse (opcje kompilatora C#)
Recurse — opcja umożliwia skompilować plików kodu źródłowego we wszystkich katalogach podrzędnych albo określonego katalogu (dir) lub w katalogu projektu.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a>Argumenty  
 `dir`(opcjonalnie)  
 Katalog, w którym ma rozpocząć wyszukiwanie. Jeśli nie zostanie określony, wyszukiwanie rozpoczyna się w katalogu projektu.  
  
 `file`  
 Pliki do wyszukania. Symbole wieloznaczne są dozwolone.  
  
## <a name="remarks"></a>Uwagi  
 **-Recurse** opcja umożliwia skompilować plików kodu źródłowego we wszystkich katalogach podrzędnych określonego katalogu (`dir`) lub w katalogu projektu.  
  
 Symbole wieloznaczne w nazwie pliku służy do Kompiluj wszystkie zgodne pliki w katalogu projektu bez użycia **-recurse**.  
  
 Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można zmienić programowo.  
  
## <a name="example"></a>Przykład  
 Kompiluje wszystkie pliki C# w bieżącym katalogu:  
  
```console  
csc *.cs  
```  
  
 Kompiluje wszystkie pliki C# w katalogu dir1\dir2 i wszystkie jego katalogów i generuje dir2.dll:  
  
```console  
csc -target:library -out:dir2.dll -recurse:dir1\dir2\*.cs  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
